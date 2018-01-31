---
title: "Microsoft Flow で webhook を使用する | Microsoft Docs"
description: "Microsoft Flow で webhook とやりとりするフローを作成する方法について説明します"
services: 
suite: flow
documentationcenter: 
author: msftman
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/08/2017
ms.author: deonhe
ms.openlocfilehash: cf899063ed6244e85d7eb0759efc9421cbdaa327
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2018
---
# <a name="use-webhooks-with-microsoft-flow"></a>Microsoft Flow で webhook を使用する
[webhook](http://www.webhooks.org/) は、イベント通知を提供する単純な HTTP コールバックです。  Microsoft Flow では、webhook を利用してフローをトリガーできます。  このチュートリアルでは、webhook によってトリガーされるフローを作成する方法を示します。

> [!NOTE]
> webhook で通知を送信できるサービスの例として GitHub を利用しますが、ここで紹介する手法は webhook を使用するあらゆるサービスに応用できます。
> 
> 

## <a name="prerequisites"></a>前提条件
このチュートリアルを完了するために必要な要素:

* [webhook](http://www.webhooks.org/) に関する基本的な理解。
* [OpenAPI 仕様](http://swagger.io/specification/) (Swagger) の基本的な理解。
* [GitHub](https://www.github.com) アカウント。
* このチュートリアルの[サンプルの OpenAPI JSON](https://pwrappssamples.blob.core.windows.net/samples/githubWebhookSample.json)。
* または、OpenAPI ファイルを記述しない場合は、[トリガー UI](customapi-webhooks.md#creating-webhook-triggers-from-the-ui) を使って webhook トリガーを定義できます。

## <a name="the-openapi-file"></a>OpenAPI ファイル
webhook は Microsoft Flow に一種の[カスタム コネクタ](register-custom-api.md)として実装されます。そのため、OpenAPI JSON ファイルを与え、webhook の形を定義する必要があります。  OpenAPI には、webhook ワーク作成のために重要な 3 つの定義が含まれています。

1. webhook を作成する
2. API (ここでは、GitHub) から入ってくるフック要求を定義する
3. webhook を削除する

### <a name="creating-the-webhook"></a>webhook を作成する
webhook は GitHub 側で `/repos/{owner}/{repo}/hooks` に対する HTTP POST により作成されます。  OpenAPI に定義されているトリガーで新しいフローが作成されるとき、あるいはトリガーが変更されるとき、Microsoft Flow はこの URL に投稿する必要があります。  下のサンプルでは、GitHub に投稿される要求のスキーマが `post` プロパティに含まれています。

```json
"/repos/{owner}/{repo}/hooks": {
    "x-ms-notification-content": {
    "description": "Details for Webhook",
    "schema": {
        "$ref": "#/definitions/WebhookPushResponse"
    }
    },
    "post": {
    "description": "Creates a Github webhook",
    "summary": "Triggers when a PUSH event occurs",
    "operationId": "webhook-trigger",
    "x-ms-trigger": "single",
    "parameters": [
        {
        "name": "owner",
        "in": "path",
        "description": "Name of the owner of targetted repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "repo",
        "in": "path",
        "description": "Name of the repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "Request body of webhook",
        "in": "body",
        "description": "This is the request body of the Webhook",
        "schema": {
            "$ref": "#/definitions/WebhookRequestBody"
        }
        }
    ],
    "responses": {
        "201": {
        "description": "Created",
        "schema": {
            "$ref": "#/definitions/WebhookCreationResponse"
        }
        }
    }
    }
},
```

> [!IMPORTANT]
> `"x-ms-trigger": "single"` プロパティは、フロー デザイナーの利用可能トリガー リストにこの webhook を表示するように Microsoft Flow に通知するスキーマ拡張機能です。そのため、これを必ず含めてください。
> 
> 

### <a name="defining-the-incoming-hook-request-from-the-api"></a>API から入ってくるフック要求を定義する
上のサンプルのように、入ってくるフック要求 (GitHub から Microsoft Flow への通知) の形はカスタム `x-ms-notification-content` プロパティで定義されます。  要求のコンテンツ全体を含める必要はありません。フローで使用する部分だけで十分です。

### <a name="deleting-the-webhook"></a>webhook を削除する
webhook の削除方法を Microsoft Flow に通知する定義を OpenAPI に含めることはとても重要です。  フローのトリガーを更新したり、フローを削除したりするたびに、Microsoft Flow は webhook の削除を試行します。

```json
"/repos/{owner}/{repo}/hooks/{hook_Id}": {
    "delete": {
    "description": "Deletes a Github webhook",
    "operationId": "DeleteTrigger",
    "parameters": [
        {
        "name": "owner",
        "in": "path",
        "description": "Name of the owner of targetted repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "repo",
        "in": "path",
        "description": "Name of the repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "hook_Id",
        "in": "path",
        "description": "ID of the Hook being deleted",
        "required": true,
        "type": "string"
        }
    ]
    }
},
```

> [!IMPORTANT]
> Microsoft Flow が webhook を削除できるように、webhook の作成時、API で 201 応答に `Location` HTTP ヘッダーを含める**必要があります**。  `Location` ヘッダーには、HTTP DELETE と共に使用する webhook のパスを含める必要があります。  たとえば、GitHub の応答に付属する `Location` の形式は `https://api.github.com/repos/<user name>/<repo name>/hooks/<hook ID>` です。
> 
> 

## <a name="authentication"></a>認証
Microsoft Flow に webhook 要求を送信する API には、通常、何らかの形式の認証が与えられます。GitHub も例外ではありません。  数種類の認証がサポートされています。  このチュートリアルでは、GitHub の個人アクセス トークンを使用します。

1. [GitHub](https://www.github.com) に移動し、サインインしていない場合はサインインします。
2. 右上にある自分の**プロフィール写真**をクリックし、メニューの **[設定]** をクリックします。
   
    ![設定](./media/customapi-webhooks/github-settings.png)
3. 左のメニューの **[開発者向け設定]** で、**[個人用アクセス トークン]** をクリックします。
   
    ![個人用アクセス トークン](./media/customapi-webhooks/personal-access-tokens.png)
4. **[新しいトークンを生成する]** ボタンをクリックします。
   
    ![新しいトークンを生成する](./media/customapi-webhooks/generate-new-token.png)
5. **[トークンの説明]** ボックスに説明を入力します。
6. **[admin:repo_hook]** チェック ボックスをオンにします。
   
    ![admin:repo_hook](./media/customapi-webhooks/repo-hook.png)
7. **[トークンの生成]** ボタンをクリックします。
8. 新しいトークンをメモします。
   
    ![新しいトークン](./media/customapi-webhooks/new-token.png)
   
   > [!IMPORTANT]
   > このトークンに再びアクセスすることはできません。 コピーしてメモ帳などに貼り付け、チュートリアルの後半で使用します。
   > 
   > 

## <a name="adding-the-webhook-to-microsoft-flow"></a>webhook を Microsoft Flow に追加する
これで、webhook をカスタム コネクタとして Microsoft Flow に追加するために必要なすべての要素が揃いました。

1. [Microsoft Flow Web ポータル](https://flow.microsoft.com)に移動し、サインインしていない場合はサインインします。
2. **[設定]** アイコンをクリックし、**[Custom Connectors (カスタム コネクタ)]** をクリックします。
   
    ![カスタム コネクタ](./media/customapi-webhooks/custom-apis.png)
3. **[Create custom connector (カスタム コネクタの作成)]** ボタンをクリックします。
4. **[Import OpenAPI (OpenAPI のインポート)]** ボックスのファイル フォルダー アイコンをクリックし、サンプルの OpenAPI ファイルを選択します。
5. **[一般情報]** セクションの **[更新]** をクリックし、アイコンとして使用する画像ファイルを選択します。
6. **[続行]** をクリックします。
   
    ![OpenAPI をインポートする](./media/customapi-webhooks/import-swagger.png)
7. 次の画面で、セキュリティ設定を構成します。  **[認証の種類]** で **[基本認証]** を選択します。
8. **[基本認証]** セクションで、ラベル フィールドにテキストを入力します。**ユーザー名**と**パスワード**です。  これはフローでトリガーが使用されるときに表示されるラベルです。
   
    ![基本認証](./media/customapi-webhooks/basic-auth.png)
9. ページ上部でフローに名前を付け、**[Create connector (コネクタの作成)]** をクリックします。
   
    ![API の作成](./media/customapi-webhooks/create-api.png)

新しいカスタム コネクタがカスタム コネクタ ページの一覧に表示されるはずです。

## <a name="creating-webhook-triggers-from-the-ui"></a>UI からの webhook トリガーの作成
1. 基準 OpenAPI ファイルをアップロード/作成した後、カスタム コネクタ ウィザードの **[定義]** タブに移動します。
2. 左側のウィンドウで **[+ 新しいトリガー]** をクリックし、トリガーの説明を入力します。 この例では、リポジトリに対してプル要求が行われたときに起動されるトリガーを作成します。
   
    ![トリガーの作成 - 1](./media/customapi-webhooks/create-new-trigger-1.png)
3. 次に、webhook トリガーを作成する要求を定義します。 これは、サンプルの "*webhook トリガー作成*" 要求をインポートすることによって行うことができます。 webhook の作成については、[Github の API リファレンス](https://developer.github.com/v3/repos/hooks/#create-a-hook)をご覧ください。 
4. Microsoft Flow は標準の ```content-type``` とセキュリティ ヘッダーを自動的に追加するので、サンプルからインポートするときに定義する必要はありません。 
   
    ![トリガーの作成 - 2](./media/customapi-webhooks/create-new-trigger-2.png)
5. webhook 作成要求をインポートした後、サンプルの応答からインポートして webhook の応答を定義します。 プル要求イベントについては、[Github の API リファレンス](https://developer.github.com/v3/activity/events/types/#pullrequestevent)をご覧ください。 
   
    **注**: 応答をすべて貼り付ける必要はありません。 必要なフィールドのみを定義する必要があります。
   この例では、PR の URL と、PR を行ったユーザーの情報のみを抽出します。
   
    ![トリガーの作成 - 3](./media/customapi-webhooks/create-new-trigger-3.png)
6. 最後の手順では、webhook 作成要求のパラメーターで、Github が設定するために Microsoft Flow がコールバック URL を設定する必要がある値を選択します。 この場合、これは ```config``` オブジェクトの URL プロパティです。
   
    ![トリガーの作成 - 4](./media/customapi-webhooks/create-new-trigger-4.png)

## <a name="using-the-webhook-as-a-trigger"></a>トリガーとして webhook を使用する
すべての構成が完了したので、フローで webhook を使用できます。  GitHub リポジトリが git プッシュを受信するたびに Microsoft Flow モバイル アプリにプッシュ通知を送信するフローを作成します。

1. [Microsoft Flow Web ポータル](https://flow.microsoft.com)で、ページの上部にある **[自分のフロー]** をクリックします。
2. **[一から作成]** をクリックします。
3. Microsoft Flow のデザイナーで、前に登録したカスタム コネクタを検索します。
   
    ![新しいトリガー](./media/customapi-webhooks/new-trigger.png)
   
    一覧で、トリガーとして使用する項目をクリックします。
4. このカスタム コネクタを使用するのは初めてとなるため、これに接続する必要があります。  **接続名**の場合、わかりやすい名前を入力します。  **ユーザー名**の場合、GitHub ユーザー名を使用します。  **パスワード**の場合、先に作成した**個人用アクセス トークン**を使用します。
   
    ![新しい接続](./media/customapi-webhooks/new-connection.png)
   
    **[作成]** をクリックします。
5. 次に、監視するリポジトリに関する情報を Microsoft Flow に指定します。  OpenAPI ファイルの **WebhookRequestBody** オブジェクトのフィールドを認識できます。  **所有者**と**リポジトリ**に関しては、監視する GitHub リポジトリの所有者名とリポジトリ名を入力します。
   
    ![リポジトリ情報](./media/customapi-webhooks/repo-info.png)
   
   > [!IMPORTANT]
   > この例では、[Visual Studio コード](https://code.visualstudio.com)のリポジトリを使用しています。 自分のアカウントに権限が与えられているリポジトリを使用してください。  自分のリポジトリを作成すると簡単です。
   > 
   > 
6. **[+ 新しいステップ]** をクリックし、**[アクションの追加]** をクリックします。
7. **[プッシュ通知]** アクションを見つけて選択します。
   
    ![プッシュ通知](./media/customapi-webhooks/push-notification.png)
8. **[テキスト]** フィールドにテキストを入力します。  OpenAPI ファイルの **WebhookPushResponse** オブジェクトでは使用できるパラメーターのリストが定義されていることに注意してください。
   
    ![プッシュ通知の詳細](./media/customapi-webhooks/push-details.png)
9. ページ上部でフローに名前を付け、**[フローの作成]** をクリックします。
   
    ![フロー名](./media/customapi-webhooks/flow-name.png)

## <a name="verification-and-troubleshooting"></a>検証とトラブルシューティング
すべてが正しく設定されていることを確認するには、**[自分のフロー]** をクリックし、新しいフローの隣にある**情報アイコン**をクリックし、実行履歴を表示します。  webhook 作成で "Succeeded" (成功) の実行が 1 つ以上表示されているはずです。  GitHub 側で webhook が作成されたことを示します。  実行に失敗した場合、実行詳細に移動し、失敗した理由を確認できます。  失敗の原因が "404 Not Found" 応答の場合、使用したリポジトリで webhook を作成する権限が GitHub アカウントに与えられていない可能性があります。

## <a name="summary"></a>概要
すべてが正しく構成されると、選択した GitHub リポジトリで git プッシュが発生したとき、Microsoft Flow モバイル アプリにプッシュ通知が送信されます。  上記のプロセスを利用すれば、あらゆる webhook 対応サービスをフローのトリガーとして使用できます。

## <a name="next-steps"></a>次のステップ
* [カスタム コネクタを登録します](register-custom-api.md)。
* [ASP.NET Web API を使用します](customapi-web-api-tutorial.md)。
* [Azure Resource Manager API を登録します](customapi-azure-resource-manager-tutorial.md)。

