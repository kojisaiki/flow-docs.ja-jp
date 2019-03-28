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
ms.date: 01/31/2019
ms.author: barathb
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: 47d44b2c97275add492153d85138b7d11b554530
ms.sourcegitcommit: 3c7822c7207cfa51d0274e9647ef02e5ea1d999f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2019
ms.locfileid: "58321412"
---
# <a name="integrate-microsoft-flow-with-websites-and-apps"></a>Microsoft Flow と Web サイトおよびアプリを統合する

"*フロー ウィジェット*" を使用してアプリまたは Web サイトに Microsoft Flow を埋め込むと、ユーザーは簡単に個人的なタスクや仕事のタスクを自動化できるようになります。

フロー ウィジェットは、ホスト ドキュメント内にある iFrame です。 このドキュメントは Microsoft Flow デザイナー内のページを指します。 フロー ウィジェットによって Microsoft Flow の特定の機能がサードパーティ製アプリケーションに統合されます。

ウィジェットはシンプルにすることができます。 たとえば、ホストと iFrame の間で通信せずにテンプレートの一覧をレンダリングするようなウィジェットです。 ウィジェットは複雑にすることもできます。 たとえば、テンプレートからフローをプロビジョニングし、ホストとウィジェットの間の双方向通信によってフローをトリガーするようなウィジェットです。

## <a name="prerequisites"></a>前提条件

- **Microsoft アカウント**または
- 職場または学校アカウント

## <a name="use-the-unauthenticated-widget"></a>認証されていないウィジェットを使用する
認証されていないテンプレートを使用するには、iFrame でホスト アプリケーションに直接それを埋め込みます。 JS SDK やアクセス トークンは必要ありません。 

### <a name="show-templates-for-your-scenarios"></a>シナリオに応じたテンプレートの表示
開始するには、次のコードを追加し、Web サイトに Microsoft Flow テンプレートを表示します。

```html
<iframe src="https://flow.microsoft.com/{locale}/widgets/templates/?q={search term}
&pagesize={number of templates}&destination={destination}"></iframe>
```

| パラメーター | 説明 |
| --- | --- |
| locale |テンプレート ビューを表す 4 文字の言語と地域コード。 たとえば、`en-us` は英語 (米国) を表し、`de-de` はドイツ語を表します。 |
| search term |ビューに表示するテンプレートの検索語句。 たとえば、Wunderlist のテンプレートを表示するには、`wunderlist` を検索します。 |
| number of templates |ビューに表示するテンプレートの数。 |
| destination |ユーザーがテンプレートを選択したときに開くページ。 テンプレートの詳細を表示するには `details` を入力し、Microsoft Flow デザイナーを開くには `new` を入力します。 |
| parameters.{name} |フローに渡す追加のコンテキスト。 |
| templateCategory | フィルター処理で所与のテンプレート カテゴリに絞り込む                     | 

宛先パラメーターが `new` の場合、ユーザーがテンプレートを開くと、Microsoft Flow デザイナーが開きます。 ユーザーはデザイナーでフローを作成できます。 ウィジェットのすべての機能を利用する場合、次のセクションをご覧ください。

### <a name="passing-additional-parameters-to-the-flow-template"></a>フロー テンプレートに追加のパラメーターを渡す

ユーザーが Web サイトやアプリで特定のコンテキストにいる場合、そのコンテキストをフローに渡すことができます。 たとえば、ユーザーが Wunderlist で特定のリストを表示している間に、"*リストに項目が追加されたときに通知を受け取る*" テンプレートを開くとします。 次の手順でリスト ID を "*パラメーター*" としてフローに渡します。

1. フロー テンプレートを発行する前に、そのテンプレートでパラメーターを定義します。 パラメーターは、`@{parameters('parameter_name')}` のような形式にします。
1. iframe src でパラメーターを渡します。たとえば、**listName** というパラメーターがある場合は、`&parameters.listName={the name of the list}` を追加します。

### <a name="full-sample"></a>完全なサンプル

ドイツの Wunderlist テンプレートを上位 4 つ表示し、**myCoolList** のユーザーを開始するには、次のコードを使用します。

```html
<iframe src="https://flow.microsoft.com/de-de/widgets/templates/?q=wunderlist
&pagesize=4&destination=details&parameters.listName=myCoolList"></iframe>
```

## <a name="use-the-authenticated-flow-widgets"></a>認証済みのフロー ウィジェットを使用する

次の表は、ユーザー認証アクセス トークンを使用し、ウィジェットの全機能をサポートする Microsoft Flow ウィジェットの一覧です。 Microsoft Flow の Javascript Software 開発者キット (JS SDK) を使用し、ウィジェットを埋め込み、必要なユーザー アクセス トークンを提供する必要があります。

| ウィジェットの種類    | サポートされている機能                                                                                                                  | 
|----------------|------------------------------------------------------------------------------------------------------------------------------------| 
| フロー          | 個人フローと共有フローについて、タブにフローの一覧を表示します。 既存のフローを編集するか、テンプレートまたは白紙から新しいフローを作成します。 | 
| FlowCreation   | ホスト アプリケーションから提供されるテンプレート ID からフローを作成します。                                                                | 
| ランタイム        | ホスト アプリケーションから提供される手動またはハイブリッドトリガーのフローをトリガーします。                                                        | 
| ApprovalCenter | 承認要求と送信済み承認を埋め込みます。                                                                                        | 
| テンプレート      | テンプレートの一覧を表示します。 ユーザーは 1 つ選択し、新しいフローを作成します。                                                                         | 

認証済みの Flow SDK を使用すると、ユーザーは Web サイトまたはアプリから直接フローを作成して管理できます (Microsoft Flow に移動する必要はありません)。 認証済み SDK を使用するには、ユーザーをその Microsoft Account または Azure Active Directory でサインインする必要があります。

> [!NOTE]
> ウィジェットを使用するとき、Microsoft Flow ブランドを非表示にする方法はありません。

## <a name="widget-architecture"></a>ウィジェット アーキテクチャ

Microsoft Flow ウィジェットは、Microsoft Flow を参照する iFrame をホスト アプリケーションに埋め込むことで動作します。 Microsoft Flow ウィジェットから要求されるアクセス トークンはホストから提供されます。 Microsoft Flow の JS SDK によって、ホスト アプリケーションはウィジェットのライフサイクルを初期化し、管理できます。

![ウィジェット アーキテクチャ](../media/embed-flow-dev/Architecture.png)

### <a name="js-sdk-details"></a>JS SDK の詳細

Microsoft Flow チームから、サードパーティ製アプリケーションに Flow ウィジェットを統合する目的で JS SDK が提供されます。 Flow JS SDK は Flow サービスのパブリック リンクトして利用できます。また、この SDK によって、ホスト アプリケーションはウィジェットからのイベントを処理し、ウィジェットにアクションを送信することで Flow アプリケーションとやり取りできます。 ウィジェットのイベントとアクションはウィジェットの種類に固有です。

### <a name="widget-initialization"></a>ウィジェット初期化

Flow JS SDK 参照は、ウィジェットを初期化する前にホスト アプリケーションに追加する必要があります。

```html
<script src="https://flow.microsoft.com/Content/msflowsdk-1.1.js"></script>
```

任意のホスト名とロケール値を JSON オブジェクトに渡すことで、JS SDK インスタンスを作成します。

```javascript
var sdk = new MsFlowSdk({
    hostName:'https://flow.microsoft.com',
    locale:'en-US',
}); 
```

| Name (名前)     | 必須/省略可能 | 説明                                                    | 
|----------|-------------------|----------------------------------------------------------------| 
| `hostName` | 省略可能          | Microsoft Flow のホスト名 (例: https://flow.microsoft.com)        | 
| `locale`   | 省略可能          | ウィジェットのクライアント ロケール (渡されない場合は `en-Us`) | 


JS SDK インスタンスが作成されると、Microsoft Flow ウィジェットを初期化し、ホスト アプリケーションの親要素に埋め込むことができます。 それを行うには、次の HTML div を追加します。

```html
<div id="flowDiv" class="flowContainer"></div>
```

次に、JS SDK renderWidget() メソッドで Microsoft Flow ウィジェットを初期化します。 必ずウィジェットの種類と対応する設定を指定してください。

```javascript
var widget = sdk.renderWidget('<widgettype>', {
        container: 'flow-div',
        flowsSettings: {},
        templatesSettings: {},
        approvalSettings: {},
        widgetStyleSettings: {},
});
```

コンテナーのサンプル スタイルは次のようになります。これをホスト アプリケーションのディメンションに合わせて変更できます。

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

`renderWidget()` のパラメーターは次のようになります。 

| パラメーター        | 必須/省略可能 | 説明                                                                                 | 
|------------------|-------------------|---------------------------------------------------------------------------------------------| 
| `container`        | 必須          | ウィジェットが埋め込まれるホスト ページの DIV 要素の ID。                      | 
| `environmentId`    | 省略可能          | ウィジェットには環境 ID が必要です。ID を指定しない場合、既定の環境が使用されます。 | 
| `flowsSettings`    | 省略可能          | Microsoft Flow 設定オブジェクト                                                                        | 
| `templateSettings` | 省略可能          | テンプレート設定オブジェクト                                                                    | 
| `approvalSettings` | 省略可能          | 承認設定オブジェクト                                                                    | 

### <a name="access-tokens"></a>アクセス トークン

JS SDK `renderWidget()` の実行後、JS SDK によって iFrame が初期化され、それが Microsoft Flow ウィジェット URL を指し示します。 この URL には、クエリ文字列パラメーターのすべての設定が含まれています。 ホスト アプリケーションは、ウィジェットを初期化する前に、ユーザーの Microsoft Flow アクセス トークン (Azure Active Directory JWT と対象ユーザー https://service.flow.microsoft.com)) を取得する必要があります。 ウィジェットにより、ホストにアクセス トークンを要求する `GET_ACCESS_TOKEN` イベントが発生します。 ホストはイベントを処理し、トークンをウィジェットに渡す必要があります。

```javascript
widget.listen("GET_ACCESS_TOKEN", function(requestParam, widgetDoneCallback) {
    widgetDoneCallback(null, {
        token:  '<accesstokenFromHost>'
    });
});
```

ホスト アプリケーションは、トークンを保守し、要求されたとき、トークンと有効期限をウィジェットに渡す役割を担います。 ウィジェットを開いている時間が長くなった場合、ホストはトークンの有効期限が切れていないか確認し、必要であれば、ウィジェットに渡す前にトークンを更新する必要があります。

### <a name="detecting-if-the-widget-is-ready"></a>ウィジェットの準備状態を検出する

初期化に成功すると、ウィジェットの準備ができていることを知らせるイベントがウィジェットによって発生します。 ホストは `WIDGET_READY` イベントを待ち受け、追加のホスト コードがあればそれを実行できます。

```javascript
widget.listen("WIDGET_READY", function() {
    console.log("The flow widget is now ready.");
    // other host code on widget ready
});
 ```

## <a name="widget-settings"></a>ウィジェット設定

### <a name="flowssettings"></a>FlowsSettings 

FlowsSettings を使用し、Microsoft Flow ウィジェットの機能をカスタマイズできます。

```javascript
flowsSettings?: {
    createFromBlankTemplateId?: string;
    flowsFilter?: string;sc
    tab?: string;
};
 ```

| パラメーター | 必須/省略可能 | 説明 | 
|-----------|-------------------|-------------| 
| `createFromBlankTemplateId` | 必須 | ユーザーが Flow ウィジェットで **[一から作成]** ボタンを選択したとき、テンプレートの GUID を使用します | 
| `flowsFilter` | 省略可能 | Microsoft Flow ウィジェットは、フローを一覧表示するとき、指定されたフィルターを適用します。 たとえば、特定の SharePoint サイトを参照するフローを表示します。 <br /> ```flowFilter: "operations/any(operation: operation/sharepoint.site eq 'https://microsoft.sharepoint.com/teams/ProcessSimple' )"   ``` |                 
| `tab` | 省略可能 | Microsoft Flow ウィジェットに表示するようにアクティブ タブを初期設定します。 <br /> たとえば、 <br /> ```tab:'sharedFlows' ``` の場合、[チーム] タブが表示されます。<br /> ``` tab:'myFlows' ``` の場合、[マイ フロー] タブが表示されます。 |   

### <a name="templatessettings"></a>TemplatesSettings 

これは、Flows、FlowCreation、Templates ウィジェットなど、テンプレートからフローを作成できるすべてのウィジェットに適用されます。

```javascript
templatesSettings?: {
    defaultParams?: any;
    destination?: string;
    pageSize?: number;
    searchTerm?: string;
    templateCategory?: string;
    useServerSideProvisioning?: boolean;
    enableDietDesigner?: boolean;
};
 ```

| パラメーター |必須/省略可能 | 説明                                                                        
|-----------|-------------------|-----------------| 
|`defaultParams` | 省略可能          | テンプレートからフローを作成するときに使用するデザイン時パラメーター。例: <br /> ``` defaultParams: {'parameters.sharepoint.site': 'https://microsoft.sharepoint.com/teams/ProcessSimple', 'parameters.sharepoint.list': 'b3a5baa8-fe94-44ca-a6f0-270d9f821668'   } ```| 
| `destination` | 省略可能          | 有効な値は "new" または "details" です。 "details" に設定されると、テンプレートからフローを作成するとき、詳細ページが表示されます。     |
| `pageSize` | 省略可能          | 表示するテンプレートの数。 既定サイズ = 6 | 
| `searchTerm` | 省略可能          | 指定された検索語句に一致するテンプレートを表示します| 
| `templateCategory` | 省略可能          | 特定のカテゴリのテンプレートを表示します| 
 
### <a name="approvalcentersettings"></a>ApprovalCenterSettings

ApprovalCenter ウィジェットに適用されます。

 ```javascript
 approvalCenterSettings?: {
    approvalsFilter?: string;
    tab?: string;but
    autoNavigateToDetails?: boolean;
    showSimpleEmptyPage? boolean;
    hideLink?: boolean
};
 ```
| パラメーター | 必須/省略可能 | 説明 | 
|------------|-------------------|--------------| 
| `hideLink`| 省略可能 | `true` に設定されると、ウィジェットは送受信済みの承認リンクを非表示にします。 | 
| `autoNavigateToDetails`| 省略可能 | `true` に設定されると、承認が 1 つだけ存在するとき、ウィジェットによって承認詳細が自動的に開きます | 
| `approvalsFilter`| 省略可能 | 承認を一覧表示するとき、承認ウィジェットは指定の承認フィルターを適用します。例:  承認を一覧表示するとき、承認ウィジェットは指定の承認フィルターを適用します。例: <br/> ``` approvalsFilter: 'properties/itemlink eq \'https://microsoft.sharepoint.com/teams/ProcessSimple/_layouts/15/listform.aspx?PageType=4&ListId=737e30a6-5bc4-4e9c-bcdc-d34c5c57d938&ID=3&ContentTypeID=0x010010B708969A9C16408696FD23801531C6\'' ```  <br/> <br/>``` approvalsFilter: 'properties/itemlinkencoded eq \'{Your base64 encoded item link url} \'' ```|
| `tab`| 省略可能 | Flow ウィジェットに表示するようにアクティブ タブを既定値に設定します。 <br/> 有効な値 : "receivedApprovals"、"sentApprovals" | 
| `showSimpleEmptyPage`| 省略可能 | 承認がないとき、空のページが表示されます | 
| `hideInfoPaneCloseButton` | 省略可能 | 情報ウィンドウの [閉じる] ボタンを非表示にします (あるいは、ホストに [閉じる] ボタンが既にあります) | 

<!-- why isn't this: hideInfoPaneCloseButton listed in the approvalCenterSettings? call since other optionals are there -->

## <a name="widget-events"></a>ウィジェット イベント

Microsoft Flow ウィジェットは、ホストがウィンドウのライフサイクル イベントを待ち受けることを許可するイベントに対応しています。 Microsoft Flow ウィジェットは、2 種類のイベントに対応しています: 一方向通知イベント (Widget\_Ready など) と、ウィジェットから発生し、ホストからデータを取得するイベント (Get\_Access\_Token)。 ホストは widget.listen() メソッドを使用し、ウィジェットから発生する特定のイベントを待ち受ける必要があります。

### <a name="usage"></a>使用法

```javascript
widget.listen("<WIDGET_EVENT>", function() {
    console.log("The flow widget raised event");
});
```

### <a name="supported-events-by-widget-type"></a>サポートされるイベント (ウィジェットの種類別)

| ウィジェットのイベント      | 詳細                                                         | 
|-------------------|-----------------------------------------------------------------| 
| `WIDGET_READY`      | ウィジェットが正常にロードされた                                      | 
| `WIDGET_RENDERED`   | ウィジェットがロードされ、UI レンダリングが完了した                      | 
| `GET_ACCESS_TOKEN`  | ウィジェットが埋め込みユーザー アクセス トークンを要求する                      | 
| `GET_STRINGS`       | ウィジェットに表示される一連の UI 文字列をオーバーライドすることをホストに許可する | 

### <a name="runtime-widget"></a>ランタイム ウィジェット

| ウィジェットのイベント                    | 詳細                                     | データ                                              | 
|---------------------------------|---------------------------------------------|-----------| 
| `RUN_FLOW_STARTED`                | トリガーされ、フロー実行が開始された      |           | 
| `RUN_FLOW_COMPLETED`              | フロー実行が正常にトリガーされた             |           | 
| `RUN_FLOW_DONE_BUTTON_CLICKED`    | フロー実行でユーザーが [完了] ボタンを選択した       |           | 
| `RUN_FLOW_CANCEL_BUTTON_CLICKED`  | フロー実行でユーザーが [キャンセル] ボタンを選択した     |           | 
| `FLOW_CREATION_SUCCEEDED`         | フローが正常に作成された           |`{ flowUrl: string, flowId: string, fromTemplate: string } `|
| `WIDGET_CLOSE`                    | ホストがウィジェットを閉じると発生 |       | 

### <a name="flow-creation-widget"></a>フロー作成ウィジェット

| ウィジェットのイベント             | 詳細                                  | データ  | 
|--------------------------|------------------------------------------|-------| 
| `FLOW_CREATION_FAILED`     | フローの作成失敗                     |       | 
| `WIDGET_CLOSE`             | ホストがウィジェットを閉じると発生  |       | 
| `TEMPLATE_LOAD_FAILED`     | テンプレートのロード失敗              |       | 
| `FLOW_CREATION_SUCCEEDED`  | フローが正常に作成された        |` { flowUrl: string, flowId: string,fromTemplate?: string } `| 

### <a name="approval-widget"></a>承認ウィジェット

| ウィジェットのイベント                      | 詳細                             | 
|-----------------------------------|-------------------------------------| 
| `RECEIVED_APPROVAL_STATUS_CHANGED`  | 受信した承認ステータスが変わった  | 
| `SENT_APPROVAL_STATUS_CHANGED`      | 送信した承認ステータスが変わった      | 

**GET\_STRINGS** イベントでは、ウィジェットに表示される UI 要素の一部をカスタマイズできます。 次の文字列をカスタマイズできます。

| 文字列キー                     | ウィジェットでの使用                                                                                                                  | 
|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------| 
| `FLOW_CREATION_CREATE_BUTTON`    | フロー作成とランタイム ウィジェットの両方で [フローの作成] ボタンに表示されるテキスト                                                | 
| `FLOW_CREATION_CUSTOM_FLOW_NAME` | フロー作成ウィジェットのフロー名に使用する初期値。 allowCustomFlowName 設定が有効なときにのみ使用。 | 
| `FLOW_CREATION_HEADER`           | フロー作成とランタイム ウィジェットの両方でフローの作成時に使用するヘッダー                                                    | 
| `INVOKE_FLOW_HEADER`             | ランタイム ウィジェットでフローを呼び出すときに使用するヘッダー                                                                           | 
| `INVOKE_FLOW_RUN_FLOW_BUTTON`    | ランタイム ウィジェットでフローを呼び出す/実行するために使用されるボタンに表示されるテキスト                                                       | 

### <a name="example"></a>例

`widgetDoneCallback` を呼び出し、JSON オブジェクト、文字列キーのキーと値のペア、テキストを渡し、既定値をオーバーライドします。

```javascript
widget.listen("GET_STRINGS", function(requestParam, widgetDoneCallback) {
    widgetDoneCallback(null, {
         "FLOW_CREATION_HEADER": "<string override would go here>",
        "INVOKE_FLOW_RUN_FLOW_BUTTON":  "<string override would go here>"
    });
});
```

## <a name="widget-actions"></a>ウィジェットのアクション

ホストはウィジェットのアクションを使用し、特定のアクションまたはメッセージをウィジェットに送信します。 ウィジェット JS SDK からは、メッセージまたは JSON ペイロードをウィジェットに送信する `notify()` メソッドが提供されます。 各ウィジェット アクションでは、特定のペイロード署名がサポートされます。

### <a name="usage"></a>使用法

```javascript
widget.notify('<WIDGET_ACTION>', parameterMatchingParameterInterface)
    .then(result => console.log(result))
    .catch(error => console.log(error))
 ```

### <a name="example"></a>例 

次のコマンドをランタイム ウィジェットに送信し、フローを呼び出します 

```javascript
widget.notify('triggerFlow', { flowName: flowName, implicitData:implicitData });  
 ```

### <a name="runtime-widget"></a>ランタイム ウィジェット

| ウィジェットのアクション                               | 詳細                                                      | パラメーター インターフェイス  | 
|---------------------------------------------|--------------------------------------------------------------|----------------------| 
| `triggerFlow`                                 | フロー実行をトリガーする                                          | `{ flowName: string, implicitData?: string } `| 
| `triggerFlowByTemplate`                       | テンプレートによってフロー実行をトリガーする                              | `{ templateId: string, implicitData?: string, designTimeParameters?: Record<string, any> }` |
| `getTriggerSchema`                            | フローのトリガー スキーマを取得する                               | `{   flowName: string, }` | 
| `closeWidget`                                 | 保留中のアクティビティがあればそれをキャンセルし、WIDGET_CLOSE イベントを発生させる |                      | 

### <a name="flow-creation-widget"></a>フロー作成ウィジェット

| ウィジェットのアクション                               | 詳細                                                      | パラメーター インターフェイス  | 
|---------------------------------------------|--------------------------------------------------------------|----------------------| 
| `createFlowFromTemplate`                      | 選択したテンプレートのフローを作成する                     | `{ templateName: string, designTimeParameters?: Record<string, any> }`| 
| `createFlowFromTemplateDefinition`            | 選択したテンプレート定義のフローを作成する          | `{ templateDefinition: string }` | 
| `closeWidget`                                 | 保留中のアクティビティがあればそれをキャンセルし、WIDGET_CLOSE イベントを発生させる |                      | 

### <a name="approval-widget"></a>承認ウィジェット

| ウィジェットのアクション  | 詳細                                           | パラメーター インターフェイス  | 
|----------------|---------------------------------------------------|----------------------| 
| `closeInfoPane`  | 承認詳細を表示している情報ウィンドウを閉じる  | 該当なし                  | 

## <a name="configuring-your-client-application"></a>クライアント アプリケーションを構成する

Flow サービス スコープ (委任されたアクセス許可) でクライアント アプリケーションを構成する必要があります。 ウィジェット統合に使用される Azure Active Directory (AAD) アプリで "コード付与" 認可フローが使用される場合、AAD アプリは、Microsoft Flow でサポートされている委任されたアクセス許可で事前構成する必要があります。 これにより委任されたアクセス許可が与えられ、アプリケーションに次のことが許可されます。

-   承認を管理する
-   承認を読み取る
-   アクティビティを読み取る
-   フローを管理する
-   フローを読み取る

次の手順に従って 1 つまたは複数の委任されたアクセス許可を選択します。

1.  https://portal.azure.com に移動します。 
2.  **[Azure Active Directory]** を選択します。
3.  **[管理]** の下で **[アプリの登録]** を選択します。
4.  Flow サービス スコープに対して構成するサードパーティ製アプリケーションを入力します。
5.  **[設定]** を選択します。
      ![ウィジェット アーキテクチャ](../media/embed-flow-dev/AAD-App-Settings.png)
6. **[API アクセス]** の下で **[必要なアクセス許可]** を選択します。
7. **[追加]** を選択します。
8. **[API を選択する]** を選択します。
      ![ウィジェット アーキテクチャ](../media/embed-flow-dev/AAD-App-Select-an-API.png)
9. **[Microsoft Flow service]\(Microsoft Flow サービス\)** を見つけて選択します。 注: Microsoft Flow サービスを表示するには、テナントで少なくとも 1 人の AAD ユーザーが Flow ポータル (<https://flow.microsoft.com>) にサインインしている必要があります。
10. アプリケーションに必要な Flow スコープを選択し、**[保存]** を選択します。
      ![ウィジェット アーキテクチャ](../media/embed-flow-dev/AAD-App-DelegatedPermissions.png)

これで、JWT トークンに "scp" クレームの委任されたアクセス許可が含まれる Flow サービス トークンがアプリケーションに与えられます。

## <a name="sample-application-embedding-flow-widgets"></a>フロー ウィジェット埋め込みのサンプル アプリケーション 

リソース セクションにはサンプル JavaScript Single Page Application (SPA) があります。ホスト ページでフロー ウィジェットの埋め込みを試してみることができます。 サンプル アプリケーションを使用するには、AAD アプリケーションを登録し、暗黙的な許可フローを有効にする必要があります。

### <a name="registering-an-aad-app"></a>AAD アプリを登録する

1.  [Azure Portal](https://portal.azure.com/) にサインインします。
2.  左のナビゲーション ウィンドウで、**[Azure Active Directory]** を選択し、**[アプリの登録 (プレビュー)]**、[新規登録] の順に選択します。
3.  **[アプリケーションの登録]** ページが表示されたら、アプリケーションの名前を入力します。
4.  **[サポートされているアカウントの種類]** で、任意の組織ディレクトリで **[アカウント]** を選択します。
5.  **[リダイレクト URL]** セクションの下で、Web プラットフォームを選択し、Web サーバーに基づいてアプリケーションの URL に値を設定します。  この値を http://localhost:30662/ に構成し、サンプル アプリを実行します。
6.  **[登録]** を選択します。
7.  アプリの **[概要]** ページで、アプリケーション (クライアント) ID 値をメモします。
8.  このサンプルでは、[暗黙的な許可フロー](https://docs.microsoft.com/azure/active-directory/develop/v2-oauth2-implicit-grant-flow)を有効にする必要があります。 登録したアプリケーションの左のナビゲーション ウィンドウで、**[認証]** を選択します。
9.  **[詳細設定]** の **[暗黙の付与]** で **[ID トークン]** チェックボックスと **[アクセス トークン]** チェックボックスの両方をオンにします。 このアプリではユーザーをサインインし、Flow API を呼び出す必要があるため、ID トークンとアクセス トークンが必要になります。
10. **[保存]** を選択します。

### <a name="running-the-sample"></a>サンプルを実行する
<!-- todo where should I download from? -->
<!-- todo is this a misspelling: applicaionConfig -->
1.  サンプルをダウンロードし、それをデバイスのローカル フォルダーにコピーします。
2.  FlowSDKSample フォルダーの下で index.html ファイルを開き、`applicaionConfig` を変更し、先に登録したアプリケーション ID に `clientID` を更新します。
    ![ウィジェット アーキテクチャ](../media/embed-flow-dev/SampleApp-ApplicationConfig.png)
3.  このサンプル アプリは、Flow スコープの **Flows.Read.All** と **Flow.Manage.All** を使用するように構成されています。 **applicationConfig** オブジェクトの **flowScopes** プロパティを更新することで、追加のスコープを構成できます。
4.  次のコマンドを実行し、依存関係をインストールし、サンプル アプリを実行します。
    > \> npm install \> node server.js
5. ブラウザーを開き、「 http://localhost:30662」と入力します。
6. **[サインイン]** ボタンを選択し、AAD に認証し、フロー アクセス トークンを取得します。
7. **[アクセス トークン]** テキスト ボックスにアクセス トークンが含まれます。
    ![ウィジェット アーキテクチャ](../media/embed-flow-dev/SampleApp-AccessToken.png)
8. **[Load Flows widget]\(フロー ウィジェットを読み込む\)** または **[Load Templates widget]\(テンプレート ウィジェットを読み込む\)** を選択し、対応するウィジェットを埋め込みます。
    ![ウィジェット アーキテクチャ](../media/embed-flow-dev/SampleApp-TemplatesWidget.png)

サンプル アプリケーションの[ダウンロード リンク](https://procsi.blob.core.windows.net/docs/FlowWidgetSampleApp.zip)。

## <a name="resources"></a>リソース

### <a name="widget-test-pages"></a>ウィジェットのテスト ページ

ウィジェットの統合と設定に関する詳細は次の場所で確認できます。

- テンプレート ウィジェット: <[https://flow.microsoft.com/en-us/test/templateswidget/](https://flow.microsoft.com/en-us/test/templateswidget/)>
- FlowCreation ウィジェット: <[https://flow.microsoft.com/en-us/test/flowcreationwidget/](https://flow.microsoft.com/en-us/test/flowcreationwidget/)>
- ランタイム ウィジェット: <[https://flow.microsoft.com/en-us/test/runtimewidget/](https://flow.microsoft.com/en-us/test/runtimewidget/)>
- 承認センター ウィジェット: <[https://flow.microsoft.com/en-us/test/approvalcenterwidget/](https://flow.microsoft.com/en-us/test/approvalcenterwidget/)>
- フロー ウィジェット: <[https://flow.microsoft.com/en-us/test/managewidget/](https://flow.microsoft.com/en-us/test/managewidget/)>

### <a name="supported-widget-locales"></a>サポートされているウィジェット ロケール

頭文字で表記されているロケールが一覧にない場合、Flow では、サポートされている最寄りのロケールが使用されます。

| ロケール     | 言語                   | 
|------------|----------------------------| 
| bg-bg      | ブルガリア語 (ブルガリア)       | 
| ca-es      | カタルニア語 (スペイン)            | 
| cs-cz      | チェコ語 (チェコ共和国)     | 
| da-dk      | デンマーク語 (デンマーク)           | 
| de-de      | ドイツ語 (ドイツ)           | 
| el-gr      | ギリシャ語 (ギリシャ)             | 
| en-Us      | 英語 (米国)    | 
| es-es      | スペイン語 (カスティーヤ語)        | 
| et-ee      | エストニア語 (エストニア)         | 
| eu-es      | バスク語 (スペイン)             | 
| fi-fi      | フィンランド語 (フィンランド)          | 
| fr-fr      | フランス語 (フランス)            | 
| gl-es      | ガリシア語 (スペイン)           | 
| hi-HU      | ハンガリー語 (ハンガリー)        | 
| hi-in      | ヒンディー語 (インド)              | 
| hr-hr      | クロアチア語 (クロアチア)         | 
| id-Id      | インドネシア語 (インドネシア)     | 
| it-It      | イタリア語 (イタリア)            | 
| jp-Jp      | 日本語 (日本)           | 
| kk-kz      | カザフ語 (カザフスタン)        | 
| ko-kr      | 韓国語 (韓国)             | 
| lt-LT      | リトアニア語 (リトアニア)     | 
| lv-lv      | ラトビア語 (ラトビア)           | 
| ms-my      | マレー語 (マレーシア)           | 
| nb-no      | ノルウェー語 (ブークモール)         | 
| nl-nl      | オランダ語 (オランダ)        | 
| pl-pl      | ポーランド語 (ポーランド)            | 
| pt-br      | ポルトガル語 (ブラジル)        | 
| pt-pt      | ポルトガル語 (ポルトガル)      | 
| ro-ro      | ルーマニア語 (ルーマニア)         | 
| ru-ru      | ロシア語 (ロシア)           | 
| sk-sk      | スロバキア語 (スロバキア)          | 
| sl-si      | スロベニア語 (スロベニア)       | 
| sr-cyrl-rs | セルビア語 (キリル、セルビア) | 
| sr-latn-rs | セルビア語 (ラテン、セルビア)    | 
| sv-se      | スウェーデン語 (スウェーデン)           | 
| th-th      | タイ語 (タイ)            | 
| tr-tr      | トルコ語 (トルコ)           | 
| uk-ua      | ウクライナ語 (ウクライナ)        | 
| vi-vn      | ベトナム語 (ベトナム)      |
