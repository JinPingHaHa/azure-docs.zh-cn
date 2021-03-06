---
title: 快速入门：使用 C# 向必应实体搜索 REST API 发送搜索请求
titlesuffix: Azure Cognitive Services
description: 使用本快速入门，通过 C# 向必应实体搜索 REST API 发送请求，并接收 JSON 响应。
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: bing-entity-search
ms.topic: quickstart
ms.date: 02/01/2019
ms.author: aahi
ms.openlocfilehash: b61db97cec77fc724933c2b4e7d3fa7f7afc0ab6
ms.sourcegitcommit: 90cec6cccf303ad4767a343ce00befba020a10f6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55884947"
---
# <a name="quickstart-send-a-search-request-to-the-bing-entity-search-rest-api-using-c"></a>快速入门：使用 C# 向必应实体搜索 REST API 发送搜索请求

使用本快速入门对必应实体搜索 API 进行你的第一次调用并查看 JSON 响应。 这个简单的 C# 应用程序会向该 API 发送一个新闻搜索查询并显示响应。 [GitHub](https://github.com/Azure-Samples/cognitive-services-REST-api-samples/blob/master/dotnet/Search/BingEntitySearchv7.cs) 上提供了此应用程序的源代码。

虽然此应用程序是使用 C# 编写的，但 API 是一种 RESTful Web 服务，与大多数编程语言兼容。


## <a name="prerequisites"></a>先决条件

* 任何版本的 [Visual Studio 2017](https://www.visualstudio.com/downloads/)。
* [Json.NET](https://www.newtonsoft.com/json) 框架，可以 NuGet 包的形式提供。
* 如果使用的是 Linux/MacOS，则可使用 [Mono](http://www.mono-project.com/) 运行此应用程序。


[!INCLUDE [cognitive-services-bing-news-search-signup-requirements](../../../../includes/cognitive-services-bing-entity-search-signup-requirements.md)]

## <a name="create-and-initialize-a-project"></a>创建并初始化项目

1. 在 Visual Studio 中创建一个新的 C# 控制台解决方案。 然后将以下命名空间添加到主代码文件。
    
    ```csharp
    using System;
    using System.Net.Http;
    using System.Text;
    ```

2. 创建一个新类，并为 API 终结点、订阅密钥和你要搜索的查询添加变量。

    ```csharp
    namespace EntitySearchSample
    {
        class Program
        {
            static string host = "https://api.cognitive.microsoft.com";
            static string path = "/bing/v7.0/entities";
    
            static string market = "en-US";
    
            // NOTE: Replace this example key with a valid subscription key.
            static string key = "ENTER YOUR KEY HERE";
    
            static string query = "italian restaurant near me";
        //...
        }
    }
    ```

## <a name="send-a-request-and-get-the-api-response"></a>发送请求并获取 API 响应

1. 在该类中创建一个名为 `Search()` 的函数。 创建一个新的 `HttpClient` 对象，并将你的订阅密钥添加到 `Ocp-Apim-Subscription-Key` 标头。

    1. 通过将主机和路径进行组合来构造你的请求的 URI。 然后，添加你的市场，并对你的查询进行 URL 编码。
    2. 等待 `client.GetAsync()` 获得 HTTP 响应，然后通过等待 `ReadAsStringAsync()` 来存储 JSON 响应。
    3. 将字符串输出到控制台。

    ```csharp
    async static void Search()
    {
        //...
        HttpClient client = new HttpClient();
        client.DefaultRequestHeaders.Add("Ocp-Apim-Subscription-Key", key);

        string uri = host + path + "?mkt=" + market + "&q=" + System.Net.WebUtility.UrlEncode(query);

        HttpResponseMessage response = await client.GetAsync(uri);

        string contentString = await response.Content.ReadAsStringAsync();
        Console.WriteLine(JsonPrettyPrint(contentString));
    }
    ```

2. 在应用程序的 main 方法中调用 `Search()` 函数。
    
    ```csharp
    static void Main(string[] args)
    {
        Search();
        Console.ReadLine();
    }
    ```


## <a name="example-json-response"></a>示例 JSON 响应

在 JSON 中返回成功的响应，如以下示例所示： 

```json
{
  "_type": "SearchResponse",
  "queryContext": {
    "originalQuery": "italian restaurant near me",
    "askUserForLocation": true
  },
  "places": {
    "value": [
      {
        "_type": "LocalBusiness",
        "webSearchUrl": "https://www.bing.com/search?q=sinful+bakery&filters=local...",
        "name": "Liberty's Delightful Sinful Bakery & Cafe",
        "url": "https://www.contoso.com/",
        "entityPresentationInfo": {
          "entityScenario": "ListItem",
          "entityTypeHints": [
            "Place",
            "LocalBusiness"
          ]
        },
        "address": {
          "addressLocality": "Seattle",
          "addressRegion": "WA",
          "postalCode": "98112",
          "addressCountry": "US",
          "neighborhood": "Madison Park"
        },
        "telephone": "(800) 555-1212"
      },

      . . .
      {
        "_type": "Restaurant",
        "webSearchUrl": "https://www.bing.com/search?q=Pickles+and+Preserves...",
        "name": "Munson's Pickles and Preserves Farm",
        "url": "http://www.princi.com/",
        "entityPresentationInfo": {
          "entityScenario": "ListItem",
          "entityTypeHints": [
            "Place",
            "LocalBusiness",
            "Restaurant"
          ]
        },
        "address": {
          "addressLocality": "Seattle",
          "addressRegion": "WA",
          "postalCode": "98101",
          "addressCountry": "US",
          "neighborhood": "Capitol Hill"
        },
        "telephone": "(800) 555-1212"
      },
      
      . . .
    ]
  }
}
```

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [构建单页 Web 应用](../tutorial-bing-entities-search-single-page-app.md)

* [什么是必应实体搜索 API？](../overview.md )
* [必应实体搜索 API 参考](https://docs.microsoft.com/rest/api/cognitiveservices/bing-entities-api-v7-reference)
