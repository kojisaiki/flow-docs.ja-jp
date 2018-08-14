---
title: Microsoft Flow と Web サイトおよびアプリを統合する | Microsoft Docs
description: Microsoft Flow エクスペリエンスを Web サイトまたはアプリに埋め込みます。
services: ''
suite: flow
documentationcenter: na
author: bbarath
manager: erikre
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/09/2017
ms.author: barathb
ms.openlocfilehash: 1dee6ba5cfd41edb1218e7246ce329265b9ce1d2
ms.sourcegitcommit: 77aae180d972373d1f251fa6a5c8f484f08ffc15
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39719961"
---
# <a name="integrate-microsoft-flow-with-websites-and-apps"></a>Microsoft Flow と Web サイトおよびアプリを統合する
アプリまたは Web サイトに Microsoft Flow を埋め込むと、ユーザーは簡単に個人的なタスクや仕事のタスクを自動化できるようになります。

ユーザーは、フローを作成するために、**Microsoft アカウント**か、**Azure Active Directory** の職場または学校アカウントが必要です。 Microsoft Flow は、システムで使用されている ID をどれでもサポートするホワイトラベル ソリューションなどをサポートしていません (既に Microsoft アカウントまたは AAD を使用している場合を除く)。

## <a name="prerequisites"></a>前提条件
* サービスを Microsoft Flow に接続する[カスタム コネクタを作成する](register-custom-api.md)。
* 作成した API を使用する [1 つ以上のテンプレートを作成して発行する](../publish-a-template.md)。

## <a name="show-templates-for-your-scenarios"></a>シナリオに応じたテンプレートの表示
開始するには、Web サイトにフロー テンプレートが直接表示されるように、次のコードを追加します。

```html
<iframe src="https://flow.microsoft.com/{locale}/widgets/templates/?q={search term}
&pagesize={number of templates}&destination={destination}"></iframe>
```

**注**: ページでコードを見やすいように改行を追加してあります。

| パラメーター | 説明 |
| --- | --- |
| locale |テンプレート ビューを表す 4 文字の言語と地域コード。 たとえば、`en-us` は英語 (米国) を表し、`de-de` はドイツ語を表します。 |
| search term |ビューに表示するテンプレートの検索語句。 たとえば、Wunderlist のテンプレートを表示するには、`wunderlist` を検索します。 |
| number of templates |ビューに表示するテンプレートの数。 |
| destination |ユーザーがテンプレートをクリックしたときに開くページ。 テンプレートの詳細を表示するには `details` を指定し、Microsoft Flow デザイナーを開くには `new` を指定します。 |
| parameters.{name} |フローに渡す追加のコンテキスト。 |

destination パラメーターが `new` の場合は、ユーザーがテンプレートをクリックしたときに Microsoft Flow が開くため、デザイナーでフローを作成できます。 アプリの内部から完全に利用したい場合は、次のセクションを参照してください。

### <a name="passing-additional-parameters-to-the-flow"></a>フローに追加のパラメーターを渡す
ユーザーが Web サイトやアプリで特定のコンテキストにいる場合は、そのコンテキストをフローに渡すことができます。 たとえば、ユーザーが Wunderlist で特定のリストを表示している間に、"*リストに項目が追加されたときに通知を受け取る*" テンプレートを開くとします。 次の手順に従うと、リスト ID を "*パラメーター*" としてフローに渡すことができます。

1. フロー テンプレートを発行する前に、そのテンプレートでパラメーターを定義します。 パラメーターは、`@{parameters('parameter_name')}` のような形式にします。
2. iframe src でパラメーターを渡します。たとえば、**listName** というパラメーターがある場合は、`&parameters.listName={the name of the list}` を追加します。

### <a name="full-sample"></a>完全なサンプル
ドイツにおける Wunderlist に関する上位 4 つのテンプレートを表示し、**myCoolList** のユーザーを開始するには、次のとおりです。

```html
<iframe src="https://flow.microsoft.com/de-de/widgets/templates/?q=wunderlist
&pagesize=4&destination=details&parameters.listName=myCoolList"></iframe>
```

## <a name="embed-the-management-of-flows"></a>フローの管理の埋め込み
認証済みの Flow SDK を使用すると、ユーザーは Web サイトまたはアプリから直接フローを作成して管理することができます (Microsoft Flow ポータルに移動する必要はありません)。 認証済み SDK を使用するには、ユーザーが Microsoft アカウントまたは Azure Active Directory にサインインする必要があります。

> [!NOTE]
> アプリケーションで Microsoft Flow を使用するすべてのユーザーが Microsoft Flow ユーザーになります。 Microsoft Flow ブランドを非表示にする方法はありません。
> 
> 

### <a name="include-the-javascript-for-the-authenticated-sdk"></a>認証済み SDK の JavaScript を含める
この例に従って、HTML コードに SDK を含めてください。 また、SDK をダウンロードして圧縮し、製品とパッケージ化することもできます。

```javascript
<script src="https://flow.microsoft.com/content/msflowsdk-1.1.js" async defer></script>
```

### <a name="create-a-container-to-contain-the-view"></a>ビューを含めるコンテナーを作成する
次の HTML div を追加します。

```html
<div id="flowDiv" class="flowContainer"></div>
```

状況に適切なサイズで表示されるように、このコンテナーのスタイルを設定することをお勧めします。

```html
<head>
    <style>
        .flowContainer iframe {
            width: 400px;
            height: 1000px;
            border: none;
            overflow: hidden;
    }
    </style>
</head>
```

iframe は幅が 320 ピクセル未満の場合に正しく表示されないため、幅が 1200 ピクセルを超えるコンテンツは書き込まれません。 高さは任意の値でかまいません。

### <a name="authentication-against-the-sdk"></a>SDK に対する認証
ユーザーが既に作成したフローを一覧表示し、さらにテンプレートからフローを作成するには、AAD の authToken を指定します。

```javascript
<script>
    window.msFlowSdkLoaded = function() {
        var sdk = new MsFlowSdk({
            hostName:'https:/flow.microsoft.com'
        });
        var widget = sdk.renderWidget('flows', {
            container: 'flowDiv'
            environmentId: '[environmentId]'    // find environment id from browser URL when you 
                                                // click on 'my flows'
                                                //ex: https://flow.microsoft.com/manage/environments/[environmentId]/flows
        });
        widget.callbacks.GET_ACCESS_TOKEN = function(requestParam, widgetDoneCallback)
       {
            var authCallback = function(token) {
                widgetDoneCallback(null, {
                    token: token // Get AAD access token from your backend system
                });
            };
        }
    }
</script>
```

次の API 呼び出しを行って、`environmentId` を検索できます。ユーザーがアクセスできる環境の一覧が返されます。

```http
GET https://management.azure.com/providers/Microsoft.ProcessSimple/environments
?api-version=2016-11-01 
```

返される JSON 応答の環境一覧から、環境を選択できます。 `properties.isDefault=true` プロパティをチェックして、既定のユーザー環境を探すことができます。

この例では、`requestParam` は次のように定義されます。

```javascript
export interface IRpcRequestParam {
    callInfo: IRpcCallInfo,
    data?: any;
}
```

次に、`widgetDoneCallback` はホストがトークンを持つようになったら呼び出す必要のあるコールバック関数です。 これを行うのは、トークンの取得は非同期プロセスである可能性があるためです。 この関数を呼び出すときに渡す必要のあるパラメーターは、`(errorResult: any, successResult: any)` です。 successResult はコールバックの種類によって異なります。 `GetAccessToken` の場合、種類は次のとおりです。

```javascript
export interface IGetAccessTokenResult {
    token: string;
}
```
