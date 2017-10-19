---
title: "カスタム コネクタを登録して使用する | Microsoft Docs"
description: "OpenAPI と Postman を使用して、Microsoft Flow でカスタム コネクタを登録して使用します。"
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/09/2017
ms.author: sunayv
ms.openlocfilehash: 94d46b2948f03316162e1c1d45860ae94feb897c
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="register-and-use-custom-connectors-in-microsoft-flow"></a>Microsoft Flow でカスタム コネクタを登録して使用する
Microsoft Flow を使用すると、コーディングなしでワークフローを作成できます。 しかし、場合によっては Microsoft Flow の機能を拡張する必要がありますが、そのためには Web サービスが最適です。 フローでサービスに接続し、操作を実行して、データを取得できます。 Microsoft Flow で接続したい Web サービスがある場合は、サービスをカスタム コネクタとして登録します。 そうすることで、Microsoft Flow は、必要な認証、サポートされる操作、操作ごとのパラメーターと出力など、Web API の特性を知ることができます。

このトピックでは、カスタム コネクタを登録して使用するために必要な手順について説明します。また、Azure Cognitive Services の [Text Analytics API](https://www.microsoft.com/cognitive-services/text-analytics-api) を使います。 この API は、渡されたテキストの言語、センチメント、キー フレーズを識別します。

## <a name="prerequisites"></a>前提条件
* [Microsoft Flow アカウント](https://flow.microsoft.com)。
* JSON 形式の OpenAPI 2.0 (旧称 Swagger) ファイル、OpenAPI 定義への URL、または API の Postman Collection。 1 つもお持ちではない場合は、ガイダンスを提供します。
* (省略可能) カスタム コネクタのアイコンとして使う画像。

## <a name="steps-in-the-custom-connector-process"></a>カスタム コネクタのプロセスの手順
カスタム コネクタのプロセスには複数の手順があります。以下では、それについて簡単に説明します。 この記事では、何らかの種類の認証済みアクセスを備えた RESTful API が既にあるものと想定し、記事の残りの部分では手順 3 ～ 6 に注目します。 手順 1 と 2 の例については、「[Microsoft Flow 用にカスタム Web API を作成する](customapi-web-api-tutorial.md)」をご覧ください。

1. 選択した言語とプラットフォームで、**RESTful API を作成**します。 マイクロソフトの技術を使う場合は、次のいずれかをお勧めします (ただし、任意のプラットフォームを使うことができます)。
   
   * Azure Functions
   * Azure Web Apps
   * Azure API Apps
2. 次のいずれかの認証メカニズムを使って、**API をセキュリティで保護**します。 コネクタへの認証されていないアクセスを許可することはできますが、お勧めできません。
   
   * Azure Active Directory 詳細については、「[Microsoft Flow で Azure Active Directory とカスタム コネクタを使用する](customapi-azure-resource-manager-tutorial.md)」を参照してください。
   * Dropbox、Facebook、SalesForce などの特定のサービスに対する OAuth 2.0
   * 汎用 OAuth 2.0
   * API キー
   * 基本認証
3. Microsoft Flow が接続できるように、業界標準の 2 つの方法のどちらかで **API を記述**します。
   
   * OpenAPI ファイル
   * Postman Collection
     
     登録プロセスの一環として、手順 4 で OpenAPI ファイルを作成することもできます。
4. Microsoft Flow のウィザードを使って、**カスタム コネクタを登録**します。API の説明、セキュリティの詳細、その他の情報を指定します。
5. アプリで**カスタム コネクタを使用**します。 アプリでコネクタへの接続を作成し、API が提供する操作を呼び出します。Microsoft Flow で標準の接続を呼び出す場合と同じです。
6. Microsoft Flow の他のリソースと同じように、**カスタム コネクタを共有**します。 この手順は省略してもかまいませんが、通常は、複数のアプリ作成者の間でカスタム コネクタを共有すると役に立ちます。

## <a name="describe-your-api"></a>API を記述する
何らかの種類の認証済みアクセスを備えた API がある場合、Microsoft Flow がそれに接続できるように API を記述する方法が必要です。 そのためには、OpenAPI ファイルまたは Postman Collection を作成します。これは、次のような "*任意の*" REST API エンドポイントから行うことができます。

* パブリックに利用可能なコネクタ。 例: [Spotify](https://developer.spotify.com/)、[Uber](https://developer.uber.com/)、[Slack](https://api.slack.com/)、[Rackspace](http://docs.rackspace.com/)、その他。
* 作成して、Azure、Amazon Web Services (AWS)、Heroku、Google Cloud などのクラウド ホスティング プロバイダーに展開する API。
* API がパブリック インターネットで公開される場合、ネットワークにデプロイされたカスタム基幹業務 API。

OpenAPI 2.0 (旧称 Swagger) と Postman Collection では使う形式が異なりますが、どちらもコンピューターで読み取り可能な言語に依存しないドキュメントであり、API の操作とパラメーターを記述します。

* これらのドキュメントは、API の基になっている言語とプラットフォームに応じたさまざまなツールを使って生成できます。 OpenAPI ファイルの例については、[Text Analytics API のドキュメント](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/export?DocumentFormat=Swagger&ApiName=Azure)をご覧ください。
* API の OpenAPI ファイルがまだなく、ファイルを作成しない場合でも、Postman Collection を使ってカスタム コネクタを簡単に作成できます。 詳しくは、「[Postman Collection を作成する](postman-collection.md)」をご覧ください。
* Microsoft Flow の背後では最終的に OpenAPI が使われるので、Postman Collection は解析されて OpenAPI 定義ファイルに変換されます。

**注**: ファイルのサイズを 1 MB 未満にする必要があります。

### <a name="getting-started-with-openapi-and-postman"></a>OpenAPI と Postman の概要
* OpenAPI を初めて使う場合は、swagger.io サイトの「[Getting Started with OpenAPI](http://swagger.io/getting-started/)」(OpenAPI の概要) をご覧ください。
* Postman を初めて使う場合は、Postman のサイトから [Postman アプリ](https://www.getpostman.com/apps)をインストールしてください。
* API を Azure API Apps または Azure Functions で作成した場合は、「[Azure でホストされる API を PowerApps と Microsoft Flow にエクスポートする](https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow)」で詳細をご覧ください。

## <a name="register-your-custom-connector"></a>カスタム コネクタを登録する
OpenAPI ファイルまたは Postman Collection を使って、Microsoft Flow にカスタム コネクタを登録します。

1. [flow.microsoft.com](https://flow.microsoft.com) の上部のバーで、歯車アイコンを選択して設定メニューを開きます。 **[Custom Connectors (カスタム コネクタ)]** オプションを選びます。
   
    ![カスタム コネクタの作成](./media/register-custom-api/managecustomapi.png)  
2. **[Create custom connector (カスタム コネクタの作成)]** を選びます。
   
    ![カスタム コネクタのプロパティ](./media/register-custom-api/newcustomapi.png)
3. **[General (全般)]** タブで、カスタム コネクタの作成方法を選びます。
   
   * OpenAPI をアップロードする
   * OpenAPI URL を貼り付ける
   * Postman Collection V1 をアップロードする
     
     ![カスタム コネクタの作成方法](./media/register-custom-api/choosehowtocreate.png)
     
     カスタム コネクタのアイコンをアップロードします。 [Description (説明)]、[Host (ホスト)]、[Base URL (ベース URL)] の各フィールドは、通常、OpenAPI ファイルの情報が自動的に設定されます。 自動設定されない場合は、フィールドに情報を追加できます。 [**続行**] を選択します。
4. **[Security (セキュリティ)]** タブで、認証プロパティを入力します。
   
    ![認証の種類](./media/register-custom-api/authenticationtypes.png)
   
   * 認証の種類は、OpenAPI の `securityDefinitions` オブジェクトでの定義に基づいて自動的に設定されます。 次に示すのは OAuth2.0 の例です。
     
       ```
       "securityDefinitions": {
           "AAD": {
           "type": "oauth2",
           "flow": "accessCode",
           "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
           "tokenUrl": "https://login.windows.net/common/oauth2/token"
           "scopes": {}
           }
       },
       ```
   * OpenAPI ファイルで `securityDefintions` オブジェクトが使われていない場合は、値を追加する必要はありません。
   * Postman Collection の場合は、サポートされる認証の種類 (OAuth 2.0 や基本など) を使っている場合にのみ、認証の種類が自動的に設定されます。
   * Azure Active Directory (AAD) 認証の設定の例については、「[Microsoft Flow 用にカスタム Web API を作成する](customapi-web-api-tutorial.md#set-up-azure-active-directory-authentication)」をご覧ください。
5. **[Definitions (定義)]** タブでは、OpenAPI ファイルまたは Postman Collection で定義されているすべての操作と要求および応答の値が自動的に設定されます。 必要なすべての操作が定義されている場合は、この画面を変更せずに、登録プロセスの手順 6 に進むことができます。
   
    ![[Definition (定義)] タブ](./media/register-custom-api/definitiontab.png)
   
    既存のアクションを編集する場合、またはカスタム コネクタに新しいアクションを追加する場合は、引き続き以下をお読みください。
   
   1. OpenAPI ファイルまたは Postman Collection にまだ含まれていなかった新しいアクションを追加する場合は、左側のウィンドウで **[New action (新しいアクション)]** を選択し、**[General (全般)]** セクションで操作の名前、説明、可視性を指定します。
   2. **[Request (要求)]** セクションで、右上の **[Import from sample (サンプルからインポート)]** を選択します。 右側のフォームで、サンプルの要求に貼り付けます。 通常、API ドキュメントではサンプルの要求を使用でき、**[Verb (動詞)]**、**[Request URL (要求 URL)]**、**[Headers (ヘッダー)]**、**[Body (本文)]** の各フィールドに入力する情報を取得できます。 例については、[Text Analytics API のドキュメント](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/operations/56f30ceeeda5650db055a3c6)をご覧ください。
      
      > [!IMPORTANT]
      > ヘッダー `Content-type` は Microsoft Flow によって自動的に追加されます。このヘッダーは必ずアクションから削除してください。 **[セキュリティ]** セクションに定義されている認証ヘッダーもアクションとトリガーから削除する必要があります。 
      > 
      > 
      
      ![サンプルからのインポート](./media/register-custom-api/importfromsample.png)
   3. **[Import (インポート)]** を選択して、要求の定義を完了します。 同様の方法で応答を定義します。
6. すべての操作の定義が済んだら、**[Create (作成)]** を選択してカスタム コンテナを作成します。
7. カスタム コンテナを作成した後、**[Test (テスト)]** タブに移動して、API で定義した操作をテストします。 接続を選択し、入力パラメーターを指定して、操作をテストします。
   
    ![カスタム コネクタのテスト](./media/register-custom-api/testcustomapi.png)
   
    呼び出しが成功すると、有効な応答を受け取ります。
   
    ![コネクタのテストの応答](./media/register-custom-api/testapiresponse.png)

### <a name="quota-and-throttling"></a>クォータと調整
* カスタム コネクタの作成クォータについて詳しくは、「[最適なプランをお選びください](https://flow.microsoft.com/pricing/)」ページをご覧ください。 他のユーザーから共有されているカスタム コネクタは、このクォータに含まれません。
* カスタム コネクタで作成される接続ごとに、ユーザーは 1 分あたり最大 500 個の要求を行うことができます。

## <a name="share-your-custom-connector"></a>カスタム コネクタを共有する
カスタム コネクタが完成したので、組織の他のユーザーと共有できます。 カスタム コネクタを共有した後、カスタム コネクタを削除するとコネクタへのすべての接続が削除されますが、他のユーザーが既に依存している可能性がある点に注意してください。 組織の外部のユーザーにコネクタを提供する場合は、「[API コネクタの概要 (Microsoft Flow)](api-connector-overview.md)」をご覧ください。

1. [flow.microsoft.com](https://flow.microsoft.com) の上部のバーで、歯車アイコンを選択して設定メニューを開きます。 **[Custom connectors (カスタム コネクタ)]** オプションを選びます。
   
    ![新しい接続](./media/register-custom-api/managecustomapi.png)
2. コネクタの省略記号 [**...**] ボタンを選択し、**[プロパティの表示]** を選択します。  
   
    ![コネクタのプロパティの表示](./media/register-custom-api/view-properties.png)
3. **[共有]** を選択し、コネクタへのアクセスを許可するユーザーまたはグループを入力します。  
   
    ![カスタム コネクタの共有](./media/register-custom-api/sharecustomapi.png)
4. **[保存]** を選択します。

## <a name="next-steps"></a>次のステップ
[Postman Collection の作成方法を学習します](postman-collection.md)。

[OpenAPI のカスタム拡張機能について学習します](customapi-how-to-swagger.md)。

[ASP.NET Web API を使用します](customapi-web-api-tutorial.md)。

[Azure Resource Manager API を登録します](customapi-azure-resource-manager-tutorial.md)。

