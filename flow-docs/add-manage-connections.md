---
title: "接続およびオンプレミスのデータ ゲートウェイを使用したデータへの接続について | Microsoft Docs"
description: "SharePoint、SQL Server、OneDrive for Business、Salesforce、Office 365、OneDrive、Dropbox、Twitter、Google Drive などへの接続を追加または管理する"
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/15/2017
ms.author: stepsic
ms.openlocfilehash: c0e115732e26bdeb0d7e4c3c60e1aa6c63e0ffc1
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="manage-connections-in-microsoft-flow"></a>Microsoft Flow での接続の管理
Microsoft Flow で接続を作成する場合、フローを作成しながら、データに簡単にアクセスすることができます。 Microsoft Flow には、SharePoint、SQL Server、Office 365、OneDrive for Business、Salesforce、Excel、Dropbox、Twitter など、よく使用される接続が含まれています。 接続は PowerApps と共有されるため、一方の製品で接続を作成すると、その接続は他方の製品にも表示されます。

たとえば、接続を使用すると、次のタスクを実行できます。

* SharePoint リストを更新する。
* OneDrive for Business または Dropbox アカウントの Excel ファイルからデータを取得する。
* Office 365 で電子メールを送信する。
* ツイートを送信する。

次のような複数のシナリオで、接続を作成できます。

* [テンプレートからフロー](get-started-logic-template.md)を作成する
* [ゼロからフローを](get-started-logic-flow.md)作成するか、既存のフローを更新する
* [Microsoft Flow Web サイト][1]で接続を直接作成する

このトピックでは、[Microsoft Flow Web サイト][1]で接続を管理する方法について説明します。

## <a name="add-a-connection"></a>接続を追加する
1. [Microsoft Flow Web サイト][1]で、職場または組織アカウントを使用してサインインします。
2. 右上隅近くにある歯車アイコンを選択し、[**接続**] を選択します。
   
    ![接続の選択](./media/add-manage-connections/connections-menu.png)
3. **[接続の作成]** を選択します。
4. [**利用可能な接続**] の一覧で、SharePoint など、セットアップする接続を選択します。
5. [**接続の作成**] ボタンを選択し、接続をセットアップするための資格情報を入力します。

接続がセットアップされると、[**自分の接続**] の一覧に表示されます。

## <a name="connect-to-your-data-through-an-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイを介してデータに接続する
この記事の執筆時点では、SQL Server と SharePoint Server はオンプレミス データ ゲートウェイをサポートしています。 ゲートウェイを使用する接続を作成するには、次の手順を実行します。

1. このトピックの前述の手順に従って、接続を追加します。
2. [**利用可能な接続**] の一覧で [**SQL Server**] を選択し、[**オンプレミスのデータ ゲートウェイ経由で接続**] チェック ボックスをオンにします。
   
    ![ゲートウェイの選択](./media/add-manage-connections/select-gateway.png)
   
   > [!IMPORTANT]
   > Microsoft SharePoint データ ゲートウェイは HTTP トラフィックをサポートしますが、HTTPS トラフィックはサポートしません。
   > 
   > 
3. 接続の資格情報を指定し、使用するゲートウェイを選択します。
   
    詳細については、[ゲートウェイの管理](gateway-manage.md)に関するページと[ゲートウェイの概要](gateway-reference.md)に関するページを参照してください。
   
    接続がセットアップされると、[**自分の接続**] の一覧に表示されます。

## <a name="delete-a-connection"></a>接続を削除する
1. [**自分の接続**] ページに移動し、削除する接続に対してごみ箱アイコンを選択します。
   
    ![接続の削除](./media/add-manage-connections/delete-connection.png)
2. [**OK**] を選択して、接続を削除することを確認します。
   
    ![削除の確認](./media/add-manage-connections/delete-confirmation.png)

接続を削除すると、PowerApps と Microsoft Flow の両方から削除されます。

## <a name="update-a-connection"></a>接続を更新する
アカウントの詳細またはパスワードの変更が理由で接続が動作しない場合、接続を更新することができます。

1. [**自分の接続**] ページで、更新する接続の [**パスワードの確認**] リンクを選択します。
   
    ![パスワードの確認](./media/add-manage-connections/verify-password.png)
2. メッセージが表示されたら、新しい資格情報で接続を更新します。

接続を更新すると、PowerApps と Microsoft Flow の両方で更新されます。

## <a name="troubleshoot-a-connection"></a>接続のトラブルシューティングを行う
組織のポリシーによっては、Microsoft Flow にサインインする場合と、SharePoint、Office 365、または OneDrive for Business への接続を作成する場合に同じアカウントを使用する必要がある場合があります。

たとえば、*yourname@outlook.com* を使用して Microsoft Flow にサインインしているのに、SharePoint への接続には *yourname@contoso.com* を使用すると、接続できない場合があります。*yourname@contoso.com* を使用して Microsoft Flow にサインインすると、SharePoint に接続できるようになります。

<!--Reference links in article-->
[1]: https://flow.microsoft.com
