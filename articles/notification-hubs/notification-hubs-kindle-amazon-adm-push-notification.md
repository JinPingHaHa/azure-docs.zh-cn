---
title: 使用 Azure 通知中心向 Kindle 应用推送通知 | Microsoft Docs
description: 在本教程中，将了解如何使用 Azure 通知中心将推送通知发送到 Kindle 应用程序。
services: notification-hubs
documentationcenter: ''
author: jwargo
manager: patniko
editor: spelluru
ms.assetid: 346fc8e5-294b-4e4f-9f27-7a82d9626e93
ms.service: notification-hubs
ms.workload: mobile
ms.tgt_pltfrm: mobile-kindle
ms.devlang: Java
ms.topic: tutorial
ms.custom: mvc
ms.date: 01/04/2019
ms.author: jowargo
ms.openlocfilehash: c9e582aa530e484cfe6c11f491be748bf4f33ecb
ms.sourcegitcommit: 9b6492fdcac18aa872ed771192a420d1d9551a33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2019
ms.locfileid: "54452561"
---
# <a name="get-started-with-notification-hubs-for-kindle-apps"></a>通知中心入门（Kindle 应用）

[!INCLUDE [notification-hubs-selector-get-started](../../includes/notification-hubs-selector-get-started.md)]

本教程演示如何使用 Azure 通知中心将推送通知发送到 Kindle 应用程序。 你将创建一个空白 Kindle 应用，它使用 Amazon Device Messaging (ADM) 接收推送通知。

在本教程中，你创建/更新代码来执行以下任务：

> [!div class="checklist"]
> * 向开发人员门户添加新应用程序
> * 创建 API 密钥
> * 将凭据添加到中心
> * 设置应用程序
> * 创建 ADM 消息处理程序
> * 将 API 密钥添加到应用
> * 运行应用
> * 发送测试通知

## <a name="prerequisites"></a>先决条件

* 从 [Android 开发人员门户](https://go.microsoft.com/fwlink/?LinkId=389797)获取 Android SDK（假设你使用的是 Eclipse）。
* 按照[设置开发环境](https://developer.amazon.com/docs/fire-tablets/ft-set-up-your-development-environment.html)中的步骤设置 Kindle 的开发环境。

## <a name="add-a-new-app-to-the-developer-portal"></a>向开发人员门户添加新应用程序

1. 首先，请在 [Amazon 开发人员门户]中创建一个应用。

    ![][0]

2. 复制“应用程序密钥” 。

    ![][1]

3. 在门户中单击应用的名称，并单击“设备消息”选项卡。

    ![][2]

4. 单击“创建新的安全配置文件”，并创建一个新的安全配置文件（例如 **TestAdm security profile**）。 然后单击“保存”。

    ![][3]

5. 单击“安全配置文件”，查看刚创建的安全配置文件。 复制“客户端 ID”和“客户端密码”值以供稍后使用。

    ![][4]

## <a name="create-an-api-key"></a>创建 API 密钥

1. 使用管理员特权打开命令提示符。
2. 导航到 Android SDK 文件夹。
3. 输入以下命令：

    ```shell
    keytool -list -v -alias androiddebugkey -keystore ./debug.keystore
    ```

    ![][5]

4. 对于“密钥库”密码，请键入 **android**。
5. 复制 **MD5** 指纹。
6. 返回到开发人员门户，在“消息”选项卡中，单击“Android/Kindle”，输入应用包的名称（例如 **com.sample.notificationhubtest**）和 **MD5** 值，并单击“生成 API 密钥”。

## <a name="add-credentials-to-the-hub"></a>将凭据添加到中心

在门户中，将客户端密码和客户端 ID 添加到通知中心的“配置”选项卡。

## <a name="set-up-your-application"></a>设置应用程序

> [!NOTE]
> 创建应用程序时，请至少使用 API 级别 17。

将 ADM 库添加到 Eclipse 项目：

1. 若要获取 ADM 库，请 [下载 SDK]。 解压缩 SDK zip 文件。
2. 在 Eclipse 中右键单击项目，然后单击“属性”。 在左侧选择“Java 生成路径”，并选择顶部的“库”选项卡。 单击“添加外部 Jar”，并从提取了 Amazon SDK 的目录中选择文件 `\SDK\Android\DeviceMessaging\lib\amazon-device-messaging-*.jar`。
3. 下载 NotificationHubs Android SDK（链接）。
4. 解压缩该包，然后在 Eclipse 中将文件 `notification-hubs-sdk.jar` 拖放到 `libs` 文件夹中。

编辑应用程序清单以支持 ADM：

1. 在根清单元素中添加 Amazon 命名空间：

    ```xml
    xmlns:amazon="http://schemas.amazon.com/apk/res/android"
    ```

2. 在清单元素下添加权限作为第一个元素。 将 **[YOUR PACKAGE NAME]** 替换为用于创建应用的包。

    ```xml
    <permission
        android:name="[YOUR PACKAGE NAME].permission.RECEIVE_ADM_MESSAGE"
        android:protectionLevel="signature" />

    <uses-permission android:name="android.permission.INTERNET"/>

    <uses-permission android:name="[YOUR PACKAGE NAME].permission.RECEIVE_ADM_MESSAGE" />

    <!-- This permission allows your app access to receive push notifications
    from ADM. -->
    <uses-permission android:name="com.amazon.device.messaging.permission.RECEIVE" />

    <!-- ADM uses WAKE_LOCK to keep the processor from sleeping when a message is received. -->
    <uses-permission android:name="android.permission.WAKE_LOCK" />
    ```
3. 插入以下元素作为应用程序元素的第一个子级。 请记得将 **[YOUR SERVICE NAME]** 替换成在下一部分中创建的 ADM 消息处理程序的名称（包括包），并将 **[YOUR PACKAGE NAME]** 替换为创建应用时所用的包名称。

    ```xml
    <amazon:enable-feature
            android:name="com.amazon.device.messaging"
                    android:required="true"/>
    <service
        android:name="[YOUR SERVICE NAME]"
        android:exported="false" />

    <receiver
        android:name="[YOUR SERVICE NAME]$Receiver" />

        <!-- This permission ensures that only ADM can send your app registration broadcasts. -->
        android:permission="com.amazon.device.messaging.permission.SEND" >

        <!-- To interact with ADM, your app must listen for the following intents. -->
        <intent-filter>
        <action android:name="com.amazon.device.messaging.intent.REGISTRATION" />
        <action android:name="com.amazon.device.messaging.intent.RECEIVE" />

        <!-- Replace the name in the category tag with your app's package name. -->
        <category android:name="[YOUR PACKAGE NAME]" />
        </intent-filter>
    </receiver>
    ```

## <a name="create-your-adm-message-handler"></a>创建 ADM 消息处理程序

1. 创建继承自 `com.amazon.device.messaging.ADMMessageHandlerBase` 的新类并将其命名为 `MyADMMessageHandler`，如下图中所示：

    ![][6]

2. 添加以下 `import` 语句：

    ```java
    import android.app.NotificationManager;
    import android.app.PendingIntent;
    import android.content.Context;
    import android.content.Intent;
    import android.support.v4.app.NotificationCompat;
    import com.amazon.device.messaging.ADMMessageReceiver;
    import com.microsoft.windowsazure.messaging.NotificationHub
    ```

3. 在创建的类中添加以下代码。 请记得替换中心名称和连接字符串 (listen)：

    ```java
    public static final int NOTIFICATION_ID = 1;
    private NotificationManager mNotificationManager;
    NotificationCompat.Builder builder;
        private static NotificationHub hub;
    public static NotificationHub getNotificationHub(Context context) {
        Log.v("com.wa.hellokindlefire", "getNotificationHub");
        if (hub == null) {
            hub = new NotificationHub("[hub name]", "[listen connection string]", context);
        }
        return hub;
    }

    public MyADMMessageHandler() {
            super("MyADMMessageHandler");
        }

        public static class Receiver extends ADMMessageReceiver
        {
            public Receiver()
            {
                super(MyADMMessageHandler.class);
            }
        }

        private void sendNotification(String msg) {
            Context ctx = getApplicationContext();

            mNotificationManager = (NotificationManager)
                ctx.getSystemService(Context.NOTIFICATION_SERVICE);

        PendingIntent contentIntent = PendingIntent.getActivity(ctx, 0,
                new Intent(ctx, MainActivity.class), 0);

        NotificationCompat.Builder mBuilder =
                new NotificationCompat.Builder(ctx)
                .setSmallIcon(R.mipmap.ic_launcher)
                .setContentTitle("Notification Hub Demo")
                .setStyle(new NotificationCompat.BigTextStyle()
                        .bigText(msg))
                .setContentText(msg);

            mBuilder.setContentIntent(contentIntent);
            mNotificationManager.notify(NOTIFICATION_ID, mBuilder.build());
    }
    ```
4. 将以下代码添加到 `OnMessage()` 方法中：

    ```java
    String nhMessage = intent.getExtras().getString("msg");
    sendNotification(nhMessage);
    ```
5. 将以下代码添加到 `OnRegistered` 方法中：

    ```java
    try {
        getNotificationHub(getApplicationContext()).register(registrationId);
    } catch (Exception e) {
        Log.e("[your package name]", "Fail onRegister: " + e.getMessage(), e);
    }
    ```
6. 将以下代码添加到 `OnUnregistered` 方法中：

    ```java
    try {
        getNotificationHub(getApplicationContext()).unregister();
    } catch (Exception e) {
        Log.e("[your package name]", "Fail onUnregister: " + e.getMessage(), e);
    }
    ```
7. 在 `MainActivity` 方法中添加以下 import 语句：

    ```java
    import com.amazon.device.messaging.ADM;
    ```
8. 在 `OnCreate` 方法的末尾添加以下代码：

    ```java
    final ADM adm = new ADM(this);
    if (adm.getRegistrationId() == null)
    {
        adm.startRegister();
    } else {
        new AsyncTask() {
                @Override
                protected Object doInBackground(Object... params) {
                    try {                         MyADMMessageHandler.getNotificationHub(getApplicationContext()).register(adm.getRegistrationId());
                    } catch (Exception e) {
                        Log.e("com.wa.hellokindlefire", "Failed registration with hub", e);
                        return e;
                    }
                    return null;
                }
            }.execute(null, null, null);
    }
    ```

## <a name="add-your-api-key-to-your-app"></a>将 API 密钥添加到应用

1. 在 Eclipse 中，在项目的目录资产中创建名为 `api_key.txt` 的新文件。
2. 打开文件，复制在 Amazon 开发人员门户中生成的 API 密钥。

## <a name="run-the-app"></a>运行应用

1. 启动模拟器。
2. 在模拟器中，从顶部往下轻扫，单击“设置”，单击“我的帐户”并使用有效的 Amazon 帐户注册。
3. 在 Eclipse 中运行应用程序。

> [!NOTE]
> 如果出现了问题，请检查模拟器（或设备）的时间。 时间值必须准确。 若要更改 Kindle 模拟器的时间，可以从 Android SDK platform-tools 目录运行以下命令：

```shell
adb shell  date -s "yyyymmdd.hhmmss"
```

## <a name="send-a-notification-message"></a>发送通知消息

若要使用 .NET 发送消息：

```csharp
static void Main(string[] args)
{
    NotificationHubClient hub = NotificationHubClient.CreateClientFromConnectionString("[conn string]", "[hub name]");

    hub.SendAdmNativeNotificationAsync("{\"data\":{\"msg\" : \"Hello from .NET!\"}}").Wait();
}
```

![][7]

## <a name="next-steps"></a>后续步骤

本教程介绍了如何将广播通知发送到所有注册到后端的 Kindle 设备。 若要了解如何向特定的 Kindle 设备推送通知，请转到以下教程：以下教程展示了如何将通知推送到特定的 Android 设备，但可以使用同样的逻辑将通知推送到特定的 Kindle 设备。

> [!div class="nextstepaction"]
>[向特定设备推送通知](notification-hubs-aspnet-backend-android-xplat-segmented-gcm-push-notification.md)

<!-- URLs. -->
[Amazon 开发人员门户]: https://developer.amazon.com/home.html
[下载 SDK]: https://developer.amazon.com/public/resources/development-tools/sdk
[0]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-portal1.png
[1]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-portal2.png
[2]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-portal3.png
[3]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-portal4.png
[4]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-portal5.png
[5]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-cmd-window.png
[6]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-new-java-class.png
[7]: ./media/notification-hubs-kindle-get-started/notification-hub-kindle-notification.png
