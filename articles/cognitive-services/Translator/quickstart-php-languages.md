---
title: 快速入门：获取支持的语言，PHP - 文本翻译 API
titleSuffix: Azure Cognitive Services
description: 在本快速入门中，你将使用文本翻译 API 和 PHP 获取翻译、音译和字典查找支持的语言列表以及示例。
services: cognitive-services
author: erhopf
manager: nitinme
ms.service: cognitive-services
ms.subservice: translator-text
ms.topic: quickstart
ms.date: 02/08/2019
ms.author: erhopf
ms.openlocfilehash: 1b91c5801a64581098250468c2cd1df448a7a7b1
ms.sourcegitcommit: 943af92555ba640288464c11d84e01da948db5c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2019
ms.locfileid: "55976583"
---
# <a name="quickstart-get-supported-languages-with-the-translator-text-rest-api-php"></a>快速入门：通过文本翻译 REST API (PHP) 获取受支持的语言

在该快速入门中，你将使用文本翻译 API 获取翻译、音译和字典查找支持的语言列表以及示例。

## <a name="prerequisites"></a>先决条件

需要 [PHP 5.6.x](http://php.net/downloads.php) 运行此代码。

## <a name="languages-request"></a>语言请求

以下代码使用 [Languages](./reference/v3-0-languages.md) 方法获取翻译、音译和字典查找支持的语言列表和示例。

1. 在你喜欢使用的代码编辑器中新建一个 PHP 项目。
2. 添加以下提供的代码。
3. 运行该程序。

```php
<?php
// NOTE: Be sure to uncomment the following line in your php.ini file.
// ;extension=php_openssl.dll
$host = "https://api.cognitive.microsofttranslator.com";
$path = "/languages?api-version=3.0";
$output_path = "output.txt";
function GetLanguages ($host, $path) {
    $headers = "Content-type: text/xml\r\n";
    // NOTE: Use the key 'http' even if you are making an HTTPS request. See:
    // http://php.net/manual/en/function.stream-context-create.php
    $options = array (
        'http' => array (
            'header' => $headers,
            'method' => 'GET'
        )
    );
    $context  = stream_context_create ($options);
    $result = file_get_contents ($host . $path, false, $context);
    return $result;
}
$result = GetLanguages ($host, $path);
// Note: We convert result, which is JSON, to and from an object so we can pretty-print it.
// We want to avoid escaping any Unicode characters that result contains. See:
// http://php.net/manual/en/function.json-encode.php
$json = json_encode(json_decode($result), JSON_UNESCAPED_UNICODE | JSON_PRETTY_PRINT);
// Write the output to file.
$out = fopen($output_path, 'w');
fwrite($out, $json);
fclose($out);
?>
```

## <a name="languages-response"></a>语言响应

成功的响应以 JSON 格式返回，如以下示例所示：

```json
{
  "translation": {
    "af": {
      "name": "Afrikaans",
      "nativeName": "Afrikaans",
      "dir": "ltr"
    },
    "ar": {
      "name": "Arabic",
      "nativeName": "العربية",
      "dir": "rtl"
    },
...
  },
  "transliteration": {
    "ar": {
      "name": "Arabic",
      "nativeName": "العربية",
      "scripts": [
        {
          "code": "Arab",
          "name": "Arabic",
          "nativeName": "العربية",
          "dir": "rtl",
          "toScripts": [
            {
              "code": "Latn",
              "name": "Latin",
              "nativeName": "اللاتينية",
              "dir": "ltr"
            }
          ]
        },
        {
          "code": "Latn",
          "name": "Latin",
          "nativeName": "اللاتينية",
          "dir": "ltr",
          "toScripts": [
            {
              "code": "Arab",
              "name": "Arabic",
              "nativeName": "العربية",
              "dir": "rtl"
            }
          ]
        }
      ]
    },
...
  },
  "dictionary": {
    "af": {
      "name": "Afrikaans",
      "nativeName": "Afrikaans",
      "dir": "ltr",
      "translations": [
        {
          "name": "English",
          "nativeName": "English",
          "dir": "ltr",
          "code": "en"
        }
      ]
    },
    "ar": {
      "name": "Arabic",
      "nativeName": "العربية",
      "dir": "rtl",
      "translations": [
        {
          "name": "English",
          "nativeName": "English",
          "dir": "ltr",
          "code": "en"
        }
      ]
    },
...
  }
}
```

## <a name="next-steps"></a>后续步骤

浏览此快速入门的示例代码和其他内容，包括翻译和音译，以及 GitHub 上的其他示例文本翻译项目。

> [!div class="nextstepaction"]
> [浏览 GitHub 上的 PHP 示例](https://aka.ms/TranslatorGitHub?type=&language=php)
