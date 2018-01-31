---
title: "Microsoft Flow でのカスタム コネクタ用の OpenAPI 拡張 | Microsoft Docs"
description: "Microsoft Flow で使用する OpenAPI に必要なスキーマ拡張を示します"
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: sunaysv
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/19/2017
ms.author: sunayv
ms.openlocfilehash: b8fdc04c16701c876d84e9761a48093fa5fb195c
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2018
---
# <a name="openapi-extensions-for-custom-connectors-in-microsoft-flow"></a>Microsoft Flow でのカスタム コネクタ用の OpenAPI 拡張
## <a name="introduction"></a>概要
Microsoft Flow、Azure Logic Apps、または Microsoft PowerApps のカスタム コネクタを作成するには、API の操作とパラメーターが記述された、言語に依存しない、コンピューターが読み取れるドキュメントである OpenAPI の定義ファイルを指定する必要があります。 OpenAPI のすぐに使用可能な機能と共に、Logic Apps と Flow のカスタム コネクタを作成する際にこれらの OpenAPI 拡張機能を含めることもできます。

* `summary`
* `x-ms-summary`
* `description`
* `x-ms-visibility`
* `x-ms-dynamic-values`
* `x-ms-dynamic-schema`

これらの拡張機能の詳細を以下に示します。

<a name="summary"></a>

## <a name="summary"></a>概要
アクション (操作) のタイトルを指定します。 </br>
適用対象: 操作 </br>
推奨: `summary` の*文頭を大文字*にします。 </br>
例: "When an event is added to calendar" または "Send an email"

![各操作の "summary"](./media/custom-connector-openapi-extensions/summary.png)

``` json
"actions" {
  "Send_an_email": {
    /// Other action properties here...
    "summary": "Send an email",
    /// Other action properties here...
  }
},
```

## <a name="x-ms-summary"></a>x-ms-summary
エンティティのタイトルを指定します。 </br>
適用対象: パラメーター、応答スキーマ </br>
推奨: `x-ms-summary` の*タイトルの各単語の先頭を大文字*にします。 </br>
例: "Calendar ID"、"Subject"、"Event Description" など

![各エンティティの "x-ms-summary"](./media/custom-connector-openapi-extensions/x-ms-summary.png)

``` json
"actions" {
  "Send_an_email": {
    /// Other action properties here...
    "parameters": [ 
      {
        /// Other parameters here...
        "x-ms-summary": "Subject",
        /// Other parameters here...
      }
    ]
  }
},
```
<a name="description"></a>

## <a name="description"></a>説明
操作の機能、またはエンティティの形式と機能についての詳細な説明を指定します。 </br>
適用対象: 操作、パラメーター、応答スキーマ </br>
推奨: `description` の*文頭を大文字*にします。 </br>
例: "This operation triggers when a new event is added to the calendar"、"Specify the subject of the mail." など

![各操作またはエンティティの "description"](./media/custom-connector-openapi-extensions/description.png)

``` json
"actions" {
  "Send_an_email": {
     "description": "Specify the subject of the mail",
     /// Other action properties here...
  }
},
```

<a name="visibility"></a>

## <a name="x-ms-visibility"></a>x-ms-visibility
ユーザーに対するエンティティの可視性を指定します。 </br>
使用可能な値: `important`、`advanced`、および `internal` </br>
適用対象: 操作、パラメーター、スキーマ

* `important` 操作とパラメーターは常に、最初にユーザーに表示されます。
* `advanced` 操作とパラメーターは追加メニューで非表示になります。
* `internal` 操作とパラメーターはユーザーに対して非表示になります。

> [!NOTE]
> `internal` および `required` であるパラメーターの場合、その既定値を指定する**必要**があります。
> 
> 

例: **[詳細]** メニューと **[詳細オプションの表示]** メニューでは、`advanced` 操作とパラメーターは非表示になります。

![操作とパラメーターを表示または非表示にする場合の "x-ms-visibility"](./media/custom-connector-openapi-extensions/x-ms-visibility.png)

``` json
"actions" {
  "Send_an_email": {
     /// Other action properties here...
     "parameters:": [
         {
           "name": "Subject",
           "type": "string",
           "description": "Specify the subject of the mail",
           "x-ms-summary": "Subject",
           "x-ms-visibility": "important",
           /// Other parameter properties here
         }
     ]
     /// Other action properties here...
  }
},
```

## <a name="x-ms-dynamic-values"></a>x-ms-dynamic-values
ユーザーが操作の入力パラメーターを選択できるように、設定済みリストを表示します。 </br>
適用対象: パラメーター </br>
使用方法: パラメーターの定義に `x-ms-dynamic-values` オブジェクトを追加します。 例については、この [OpenAPI サンプル](https://procsi.blob.core.windows.net/blog-images/sampleDynamicSwagger.json)を参照してください。

![リストを表示する場合の "x-ms-dynamic-values"](./media/custom-connector-openapi-extensions/x-ms-dynamic-values.png)

### <a name="properties-for-x-ms-dynamic-values"></a>x-ms-dynamic-values のプロパティ
| Name (名前) | 必須または省略可能 | 説明 |
| --- | --- | --- |
| **operationID** |必須 |リストを設定するために呼び出す操作。 |
| **value-path** |必須 |パラメーター値を参照する、`value-collection` 内のオブジェクトのパス文字列。 `value-collection` が指定されていない場合、応答は配列として評価されます。 |
| **value-title** |省略可能 |値の説明を参照する、`value-collection` 内のオブジェクトのパス文字列。 `value-collection` が指定されていない場合、応答は配列として評価されます。 |
| **value-collection** |省略可能 |応答ペイロード内のオブジェクトの配列に対して評価するパス文字列。 |
| **parameters** |省略可能 |dynamic-values 操作を呼び出すのに必要な入力パラメーターをプロパティで指定するオブジェクト。 |

`x-ms-dynamic-values` でプロパティを表示する例を以下に示します。

``` json
"x-ms-dynamic-values": {
  "operationId": "PopulateDropdown",
  "value-path": "name",
  "value-title": "properties/displayName",
  "value-collection": "value",
  "parameters": {
     "staticParameter": "{value}",
     "dynamicParameter": {
        "parameter": "{value-to-pass-to-dynamicParameter}"
     }
  }
}
```

## <a name="example-all-the-openapi-extensions-up-to-this-point"></a>例: 現時点までのすべての OpenAPI 拡張機能
``` json
"/api/lists/{listID-dynamic}": {
    "get": {
        "description": "Get items from a single list - uses dynamic values and outputs dynamic schema",
        "summary": "Gets items from the selected list",
        "operationID": "GetListItems",
        "parameters": [
           {
             "name": "listID-dynamic",
             "type": "string",
             "in": "path",
             "description": "Select the list from where you want outputs",
             "required": true,
             "x-ms-summary": "Select List",
             "x-ms-dynamic-values": {
                "operationID": "GetLists",
                "value-path": "id",
                "value-title": "name"
             }
           }
        ]
    }
}
```

## <a name="x-ms-dynamic-schema"></a>x-ms-dynamic-schema
現在のパラメーターまたは応答のスキーマが動的であることを示します。 このオブジェクトでは、このフィールドの値で定義されている操作を呼び出し、動的にスキーマを検出し、ユーザー入力を収集するための適切な UI を表示または使用可能なフィールドを表示できます。 

適用対象: パラメーター、応答

使用方法: 要求パラメーターまたは応答本文の定義に `x-ms-dynamic-schema` オブジェクトを追加します。 例については、この [OpenAPI サンプル](https://procsi.blob.core.windows.net/blog-images/sampleDynamicSwagger.json)を参照してください。

この例では、ユーザーがドロップダウン リストから選択する項目に基づいて、入力フォームがどのように変わるかを示します。

![動的パラメーターの "x-ms-dynamic-schema"](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema.png)

また、この例では、ユーザーがドロップダウン リストから選択する項目に基づいて、出力がどのように変わるかを示します。 このバージョンでは、ユーザーは "Cars" を選択しています。

![選択された項目 "Cars" の "x-ms-dynamic-schema-response"](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema-output1.png)

このバージョンでは、ユーザーは "Food" を選択しています。

![選択された項目 "Food" の "x-ms-dynamic-schema-response"](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema-output2.png)

### <a name="properties-for-x-ms-dynamic-schema"></a>x-ms-dynamic-schema のプロパティ
| Name (名前) | 必須または省略可能 | 説明 |
| --- | --- | --- |
| **operationID** |必須 |スキーマをフェッチするために呼び出す操作。 |
| **parameters** |必須 |dynamic-schema 操作を呼び出すのに必要な入力パラメーターをプロパティで指定するオブジェクト。 |
| **value-path** |省略可能 |スキーマを持つプロパティを参照するパス文字列。 </br>これが指定されていない場合、応答は、ルート オブジェクトのプロパティにスキーマが含まれると見なされます。 |
|  | | |

動的パラメーターの例を以下に示します。

``` json
{
  "name": "dynamicListSchema",
  "in": "body",
  "description": "Dynamic schema for items in the selected list",
  "schema": {
    "type": "object",
    "x-ms-dynamic-schema": {
        "operationID": "GetListSchema",
        "parameters": {
          "listID": {
            "parameter": "listID-dynamic"
          }
        },
        "value-path": "items"
    }
  }
}
```

動的応答の例を以下に示します。

``` json
"DynamicResponseGetListSchema": {
   "type": "object",
   "x-ms-dynamic-schema": {
      "operationID": "GetListSchema",
      "parameters": {
         "listID": {
            "parameter": "listID-dynamic"
         }
      },
      "value-path": "items"
    }
}
```

## <a name="next-steps"></a>次のステップ
[カスタム コネクタを登録します](register-custom-api.md)。

[ASP.NET Web API を使用します](customapi-web-api-tutorial.md)。

[Azure Resource Manager API を登録します](customapi-azure-resource-manager-tutorial.md)。

