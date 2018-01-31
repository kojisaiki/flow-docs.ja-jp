---
title: "Web API 用のカスタム コネクタを作成する | Microsoft Docs"
description: "Microsoft Flow 用に Azure Active Directory 認証を使用して、ASP.NET Web API を作成する方法を学習します。"
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
ms.date: 12/06/2016
ms.author: sunayv
ms.openlocfilehash: fef904b02d4b0f028edba236b73e19155b6f4919
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2018
---
# <a name="build-a-custom-connector-for-a-web-api-in-microsoft-flow"></a>Microsoft Flow で Web API 用のカスタム コネクタを作成する
このチュートリアルでは、ASP.NET Web API の作成を開始し、それを Azure Web Apps にホストし、Azure Active Directory 認証を有効にして、Microsoft Flow に ASP.NET Web API を登録する方法を説明します。 API を登録した後は、それに接続して、フローから呼び出すことができます。 

## <a name="prerequisites"></a>前提条件
* [Azure のサブスクリプション](https://azure.microsoft.com/free/)。
* [PowerApps のアカウント](https://powerapps.microsoft.com)。
* [Visual Studio](https://www.visualstudio.com/vs/) 2013 以降。

## <a name="create-an-aspnet-web-api-and-deploy-it-to-azure"></a>ASP.NET Web API を作成し Azure にデプロイする
1. Visual Studio で、**[ファイル]** > **[新しいプロジェクト]** をクリックし、新しい C# ASP.NET Web アプリケーションを作成します。
   
    ![新しい Web アプリ](./media/customapi-web-api-tutorial/newwebapp.png)
2. **[Web API]** テンプレートを選択します。  **[クラウド内のホスト]** はオンのままにします。  **[認証の変更]** をクリックします。
   
    ![新しい Web プロジェクト テンプレート](./media/customapi-web-api-tutorial/new-web-api.png)
3. **[No Authentication]**\(認証なし)、**[OK]** の順にクリックします。
   
    ![認証なし](./media/customapi-web-api-tutorial/noauth.png)
4. **[新しい ASP.NET プロジェクト]** ダイアログで **[OK]** をクリックします。  [Microsoft Azure Web App の構成] ダイアログが表示されます。
   
    ![Microsoft Azure Web App の構成](./media/customapi-web-api-tutorial/azure-publishing.png)]
   
    Azure アカウントを選択し、**[Web アプリ名]** を入力 (するか既定のままに) し、Azure **サブスクリプション**を選択します。  \**[App Service プラン]** \(サブスクリプション内の一連の Web Apps) を選択または作成します。  \**[リソース グループ]** \(サブスクリプション内の Azure リソースのグループ) を選択または作成します。  Web App を展開するリージョンを選択します。  Web API で必要な場合、Azure の **[データベース サーバー]** を選択するか作成します。  最後に、**[OK]** をクリックします。
5. Web API を作成します。
   
   > [!NOTE]
   > Web API 用のコードをまだ準備していない場合は、チュートリアル [「Getting Started with ASP.NET Web API 2 (C#)」](https://www.asp.net/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api) (ASP.NET Web API 2 の概要 (C#)) をご覧ください。
   > 
   > 
6. Web API を PowerApps に接続するには、その動作が記述された [Swagger](http://swagger.io/) ファイルが必要です。  [オンライン エディター](http://editor.swagger.io/)を使用して独自の OpenAPI を記述することもできますが、このチュートリアルでは [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle/blob/master/README.md) というオープン ソース ツールを使用します。  **ツール** > **NuGet パッケージ マネージャー** > **パッケージ マネージャー コンソール** の順にクリックして、Visual Studio プロジェクトに Swashbuckle NuGet パッケージをインストールし、パッケージ マネージャー コンソール に `Install-Package Swashbuckle` のコマンドを入力します。
   
    ![Install-Package Swashbuckle](./media/customapi-web-api-tutorial/swashbuckle-console.png)
   
   > [!TIP]
   > Swashbuckle のインストール後に Web API アプリケーションを実行すると、URL `http://<your root URL>/swagger/docs/v1` に OpenAPI ファイルが生成されます。  生成されたユーザー インターフェイスは `http://<your root URL>/swagger` にもあります。
   > 
   > 
7. Web API の準備ができたら Azure に発行します。 Visual Studio から発行するには、ソリューション エクスプ ローラーで Web プロジェクトを右クリックし、**発行...** をクリックし、発行 ダイアログ ボックスのプロンプトの指示に従います。
8. `https://<azure-webapp-url>/swagger/docs/v1` に移動して OpenAPI JSON を取得します。  内容を JSON ファイルとして保存します。  ブラウザーによっては、空のテキスト ファイルにテキストをコピーして貼り付ける必要があります。   
   
   > [!IMPORTANT]
   > 操作 ID が重複する OpenAPI ドキュメントは無効です。 サンプル C# テンプレートを使用している場合、操作 ID `Values_Get` は、2 回繰り返されます。 これは、1 つのインスタンスを `Value_Get` に変更し再発行することで、修正することができます。
   > 
   > このチュートリアルから[サンプルの OpenAPI](https://pwrappssamples.blob.core.windows.net/samples/webAPI.json) をダウンロードすることも可能です。 (`//` で開始される) コメントは、使用前に必ず削除するようにしてください。
   > 
   > 

## <a name="set-up-azure-active-directory-authentication"></a>Azure Active Directory 認証を設定する
これから Azure に 2 つの Azure Active Directory (AAD) アプリケーションを作成します。  これを行う方法の例については、[Azure Resource Manager のチュートリアル](customapi-azure-resource-manager-tutorial.md#enable-authentication-in-azure-active-directory)をご覧ください。

> [!IMPORTANT]
> いずれのアプリも同じディレクトリに配置する必要があります。
> 
> 

### <a name="first-aad-application-securing-the-web-api"></a>1 番目の AAD アプリケーション: Web API をセキュリティで保護する
1 番目の AAD アプリケーションは、Web API をセキュリティで保護するために使用します。 **webAPI** と名前を付けます。  次の値を使用して、前述のリンクのチュートリアル (「Azure Active Directory で認証を有効にする」セクションのみ) の手順に従います。

* サインオン URL: `https://login.windows.net`
* 返信 URL: `https://<your-root-url>/.auth/login/aad/callback`
* クライアント キーは必要ありません。
* すべてのアクセス許可は委任する必要はありません。
* **重要** アプリケーション ID を書き留めておきます。  これは後で使用します。

### <a name="second-aad-application-securing-the-custom-connector-and-delegated-access"></a>2 番目の AAD アプリケーション: カスタム コネクタをセキュリティで保護し、委任されたアクセス許可を取得する
2 番目の AAD アプリケーションは、カスタム コネクタの登録をセキュリティで保護し、1 番目のアプリケーションで保護された Web API に委任されたアクセスを取得します。 これを **webAPI-customAPI** と命名します。

* サインオン URL: `https://login.windows.net`
* 返信 URL: `https://msmanaged-na.consent.azure-apim.net/redirect`
* Web API に委任されたアクセスを取得するためにアクセス許可を追加します。
* このアプリケーション用に後でアプリケーション ID が必要となるので、それを書き留めておきます。
* クライアント キーを生成し、それを安全な場所に保存します。 このキーは後で使用します。

## <a name="add-authentication-to-your-azure-web-app"></a>Azure Web アプリに認証を追加する
1. [Azure Portal](https://portal.azure.com) にサインインし、最初のセクションで展開した Web アプリを検索します。
2. **[設定]** をクリックして、**[認証/承認]** を選択します。
3. **[App Service 認証]** をオンにし、**[Azure Active Directory]** を選択します。  次のブレードで、**[Express]** を選択します。  
4. **[既存の AD アプリを選択する]** をクリックし、前に作成した **webAPI** AAD アプリケーションを選択します。

これで Web アプリケーションの認証に AAD を使用できます。

## <a name="add-the-custom-connector-to-microsoft-flow"></a>Microsoft Flow にカスタム コネクタを追加する
1. OpenAPI を変更し、`securityDefintions` オブジェクトと Web アプリケーションに使用する AAD 認証を追加します。 OpenAPI の **host** プロパティのセクションは次のようになります。

```javascript
// File header should be above here...

"host": "<your-root-url>",
"schemes": [
    "https"         //Make sure this is https!
],
"securityDefinitions": {
    "AAD": {
        "type": "oauth2",
        "flow": "accessCode",
        "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
        "tokenUrl" : "https://login.windows.net/common/oauth2/token",
        "scopes": {}
    }
},

// The rest of the OpenAPI follows...
```

1. [Microsoft Flow](https://flow.powerapps.com) を参照し、「[Microsoft Flow でカスタム コネクタを登録して使用する](register-custom-api.md)」の説明に従ってカスタム コネクタを追加します。
2. OpenAPI をアップロードすると、Web API に AAD 認証を使用していることがウィザードによって自動的に検出されます。
3. カスタム コネクタに AAD 認証を構成します。  
   
   * **クライアント ID**: *webAPI-CustomAPI のクライアント ID*
   * **シークレット**: *webAPI CustomAPI のクライアント キー*
   * **ログイン URL**: `https://login.windows.net`
   * **ResourceUri**: *webAPI のクライアント ID*
4. **[作成]** をクリックして、カスタム コネクタへの接続を作成します。

## <a name="next-steps"></a>次のステップ
[Azure Resource Manager カスタム コネクタのチュートリアル](customapi-azure-resource-manager-tutorial.md)をご覧ください。

