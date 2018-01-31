---
title: "カスタム コネクタで Azure Active Directory を使用する | Microsoft Docs"
description: "Azure Active Directory 認証を使用する Azure Resource Manager 用のカスタム コネクタを作成する方法について説明します。"
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
ms.date: 05/03/2016
ms.author: deonhe
ms.openlocfilehash: 791a44a681ef70ead495bf46623657b2b75cfb65
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2018
---
# <a name="use-azure-active-directory-with-a-custom-connector-in-microsoft-flow"></a>Microsoft Flow で Azure Active Directory とカスタム コネクタを使用する
Azure Resource Manager (ARM) を使うと、Azure でソリューションのコンポーネント (データベース、仮想マシン、Web アプリなど) を管理できます。 このチュートリアルでは、Azure Active Directory で認証を有効にし、ARM API の 1 つをカスタム コネクタとして登録して、Microsoft Flow でそれに接続する方法を示します。 これは、フローの一部として Azure リソースを管理する場合に便利です。 ARM について詳しくは、「[Azure Resource Manager の概要](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)」をご覧ください。

## <a name="prerequisites"></a>前提条件
* [Azure のサブスクリプション](https://azure.microsoft.com/free/)。
* [Microsoft Flow アカウント](https://flow.microsoft.com)。
* このチュートリアルで使う[サンプルの OpenAPI ファイル](https://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json)。

## <a name="enable-authentication-in-azure-active-directory"></a>Azure Active Directory で認証を有効にする
最初に、ARM API エンドポイントを呼び出すときに認証を実行する Azure Active Directory (AAD) アプリケーションを作成する必要があります。

1. [Azure Portal](https://portal.azure.com) にサインインします。  Azure Active Directory テナントが 1 つ以上ある場合、右上隅でユーザー名に確認し、正しいディレクトリにログインしていることを確認します。
   
    ![ユーザー名](./media/customapi-azure-resource-manager-tutorial/current-user.png)
2. 左側のメニューの **[その他のサービス]** をクリックします。  **[フィルター]** テキスト ボックスに **Azure Active Directory** と入力し、**[Azure Active Directory]** をクリックします。
   
    ![Azure Active Directory](./media/customapi-azure-resource-manager-tutorial/azureaad.png)
   
    [Azure Active Directory] ブレードが開きます。   
3. Azure Active Directory ブレードのメニューで、**アプリの登録** をクリックします。
   
    ![アプリを登録する](./media/customapi-azure-resource-manager-tutorial/azureapplication.png)
4. 登録済みのアプリケーションの一覧で **[追加]** をクリックします。
   
    ![[追加] ボタン](./media/customapi-azure-resource-manager-tutorial/add-app-btn.png)   
5. アプリケーション名を入力し、**[Web アプリ/API]** は選択されたままにし、**[サインオン URL]** に `https://login.windows.net` と入力します。  **[作成]** をクリックします。  
   
    ![新しいアプリのフォーム](./media/customapi-azure-resource-manager-tutorial/newapplication.png)
6. 一覧内の新しいアプリケーションをクリックします。
   
    ![一覧内の新しいアプリ](./media/customapi-azure-resource-manager-tutorial/newapplication2.png)
   
    [登録済みのアプリ] ブレードが開きます。  **[アプリケーション ID]** を書き留めておきます。  これは後で使用します。
7. [設定] ブレードも開いているはずです。  開いていない場合、**[設定]** ボタンをクリックします。
   
    ![[設定] ボタン](./media/customapi-azure-resource-manager-tutorial/settings-btn.png)
8. 設定 ブレードで、**返信 URL** をクリックします。 URL の一覧から `https://msmanaged-na.consent.azure-apim.net/redirect` を追加し、**[保存]** をクリックします。
   
    ![返信 URL](./media/customapi-azure-resource-manager-tutorial/reply-urls.png)
9. 設定 ブレードに戻り、**必要なアクセス許可** をクリックします。  必要なアクセス許可 ブレードで **追加** をクリックします。
   
    ![必要なアクセス許可](./media/customapi-azure-resource-manager-tutorial/permissions.png)
   
    [API アクセスの追加] ブレードが開きます。
10. **[API を選択します]** をクリックします。 開いたブレードで、Azure Service Management API のオプションをクリックし、**[選択]** をクリックします。
    
    ![API を選択する](./media/customapi-azure-resource-manager-tutorial/permissions2.png)
11. **[アクセス許可の選択]** をクリックします。  [*デリゲートされたアクセス許可*] の下の **[Access Azure Service Management as organization users]** \(Azure Service Management に組織ユーザーとしてアクセスする)、**[選択]** を順にクリックします。
    
    ![デリゲートされたアクセス許可](./media/customapi-azure-resource-manager-tutorial/permissions3.png)
12. API アクセスの追加 ブレードで **完了** をクリックします。
13. 設定 ブレードに戻り、**キー** をクリックします。  キー ブレードが開いたら、キーの説明を入力し、有効期間を選択して **保存** をクリックします。  新しいキーが表示されます。  後で必要になるので、キーの値を書き留めておきます。  これで Azure Portal を閉じることができます。
    
    ![キーを作成する](./media/customapi-azure-resource-manager-tutorial/configurekeys.png)

## <a name="add-the-connection-in-microsoft-flow"></a>Microsoft Flow で接続を作成する
AAD アプリケーションを構成したので、カスタム コネクタを追加します。

1. [Microsoft Flow Web アプリ](https://flow.microsoft.com/)のページの右上隅の (歯車型の) **[設定]** ボタンをクリックします。  次に、**[custom connectors (カスタム コネクタ)]** をクリックします。
   
    ![カスタム コネクタを検索する](./media/customapi-azure-resource-manager-tutorial/finding-custom-apis.png)  
2. **[Create custom connector (カスタム コネクタの作成)]** をクリックします。  
   
    API のプロパティを求められます。  
   
   | プロパティ | 説明 |
   | --- | --- |
   | Name (名前) |ページ上部の **[無題]** をクリックし、フローに名前を付けます。 |
   | OpenAPI ファイル |[ARM OpenAPI ファイルのサンプル](https://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json)を参照します。 |
   | API アイコンのアップロード |**[アイコンのアップロード]** をクリックし、アイコンの画像ファイルを選択します。 サイズが 1 MB 未満の PNG または JPG 画像を使用できます。 |
   | 説明 |カスタム コネクタの説明を入力します (任意)。 |
   
    ![カスタム コネクタの作成](./media/customapi-azure-resource-manager-tutorial/create-custom-api.png)  
   
    **[続行]** を選択します。
3. OpenAPI ファイルは認証に AAD アプリケーションを使用するため、次の画面では、Flow にアプリケーションに関する情報を入力する必要があります。  **[クライアント ID]** には、先ほど書き留めておいた AAD の**アプリケーション ID** を入力します。  [クライアント シークレット] には、**キー**を使用します。  最後に、**[リソース URL]** には `https://management.core.windows.net/` を入力します。
   
   > [!IMPORTANT]
   > 末尾のスラッシュも含め、リソース URL は上のとおり正確に入力します。
   > 
   > 
   
    ![OAuth 設定](./media/customapi-azure-resource-manager-tutorial/oauth-settings.png)
   
    セキュリティ情報を入力したら、ページ上部のフロー名の横のチェック マーク **[&#x2713;]** をクリックし、カスタム コネクタを作成します。
4. これでカスタム コネクタが **[custom connectors (カスタム コネクタ)]** の下に列挙されるようになります。
   
    ![利用可能な API](./media/customapi-azure-resource-manager-tutorial/list-custom-apis.png)  
5. これでカスタム コネクタが登録されたので、アプリとフローで使用されるように、カスタム コネクタに接続を作成する必要があります。  カスタム コネクタ名の横の **[+]** をクリックし、サインオン画面を完了します。

> [!NOTE]
> サンプルの OpenAPI には、ARM の一連の操作は完全には定義しておらず、現在[すべてのサブスクリプションを列挙する](https://msdn.microsoft.com/library/azure/dn790531.aspx)ことのみが含まれています。  この OpenAPI を編集することも、[オンライン OpenAPI エディター](http://editor.swagger.io/)を使用して別 OpenAPI を作成することもできます。
> 
> この手順は、AAD を使用して認証されたすべての RESTful API へのアクセスに使用できます。
> 
> 

## <a name="next-steps"></a>次のステップ
フローの作成方法の詳細については、「[Microsoft Flow を使用した作成の開始](get-started-logic-flow.md)」を参照してください。

カスタム コネクタについて質問したりコメントしたりする場合は、[コミュニティに参加](https://aka.ms/flow-community)してください。

