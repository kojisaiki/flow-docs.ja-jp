---
title: 承認ワークフローの自動化の簡略化  | Microsoft Docs
description: SharePoint、Dynamics CRM、Salesforce、One Drive for Business、Zendesk、または WordPress と統合される承認ワークフローを自動化します。
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/20/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 0d948cdf5bce01aa5c18955645774dbcf455ba1b
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690858"
---
# <a name="create-and-test-an-approval-workflow-with-microsoft-flow"></a>Microsoft Flow を使用して承認ワークフローを作成してテストする

Microsoft Flow では、SharePoint、Dynamics CRM、Salesforce、OneDrive for Business、Zendesk、WordPress など、複数のサービスにわたり文書やプロセスの承認を管理できます。

承認ワークフローを作成するには、**[承認 - 承認を開始]** アクションを任意のフローに追加します。 このアクションを追加すると、フローでドキュメントまたはプロセスの承認を管理できるようになります。 たとえば、請求書、作業指示書または販売見積りを承認する、ドキュメントの承認フローを作成できます。 また、休暇申請、超過作業時間、出張計画を承認する、プロセスの承認フローを作成することもできます。

承認者は、受信トレイ、Microsoft Flow Web サイトの[承認センター](https://flow.microsoft.com/manage/approvals/received/)、または Microsoft Flow アプリから要求に対応できます。

## <a name="create-an-approval-flow"></a>承認フローを作成する
ここで、作成し、テストするフローの概要を次に示します。

   ![フローの概要](./media/modern-approvals/create-flow-overview.png)

フローでは次の手順を実行します。

1. 誰かが SharePoint Online リストで休暇申請を作成したときに開始されます。
2. 休暇申請を承認センターに追加し、それを承認者に電子メールで送信します。
3. 休暇を申請したユーザーに、承認者の決定内容を含む電子メールを送信します。
4. SharePoint Online リストを決定コメントによって更新します。

## <a name="prerequisites"></a>前提条件
このチュートリアルを完了するには、以下にアクセスする必要があります。

[!INCLUDE [prerequisites-for-modern-approvals](includes/prerequisites-for-modern-approvals.md)]

SharePoint Online リストで次の列を作成します。

   ![SharePoint Online リストの列。](./media/modern-approvals/sharepoint-list-fields.png)

SharePoint Online リストの名前と URL をメモします。 後で **[SharePoint - 項目が作成されたとき]** トリガーを構成するときに、この項目が必要になります。

## <a name="create-your-flow-from-the-blank-template"></a>空白のテンプレートからフローを作成する
[!INCLUDE [sign-in-and-create-flow-from-blank-template](includes/sign-in-and-create-flow-from-blank-template.md)]

## <a name="add-a-trigger"></a>トリガーの追加

[!INCLUDE [add-trigger-when-sharepoint-item-created](includes/add-trigger-when-sharepoint-item-created.md)]

**[サイト アドレス]** と **[リスト名]** は、このチュートリアルで先に示された項目です。

![SharePoint 情報](./media/modern-approvals/select-sharepoint-site-info.png)

## <a name="add-a-profile-action"></a>プロファイル アクションの追加

1. **[新しいステップ]** を選択し、**[アクションの追加]** を選択します。
   
    ![新しいステップ](./media/modern-approvals/select-sharepoint-add-action.png)
2. **[アクションの選択]** 検索ボックスに「**プロファイル**」と入力します。
   
    ![プロファイルの検索](./media/modern-approvals/search-for-profile.png)
3. 検索して、**[Office 365 ユーザー - 私のプロファイルの取得]** アクションを選択します。
   
    ![Office ユーザーの選択](./media/modern-approvals/select-my-profile.png)
4. フローの名前を指定し、**[フローの作成]** を選択してこれまでに行った作業を保存します。
   
    ![フローの保存](./media/modern-approvals/save.png)

## <a name="add-an-approval-action"></a>承認アクションの追加

[!INCLUDE [add-an-approval-action](includes/add-an-approval-action.md)]

> [!NOTE]
> このアクションを実行すると、**[担当者]** ボックス内の電子メール アドレスに承認要求が送信されます。
>
>

## <a name="add-a-condition"></a>条件の追加

[!INCLUDE [add-approval-condition-response](includes/add-approval-condition-response.md)]

## <a name="add-an-email-action-for-approvals"></a>承認に電子メール アクションを追加する

休暇申請が承認された場合に電子メールを送信するには、次のステップに従います。

[!INCLUDE [add-action-to-send-email-when-vacation-approved](includes/add-action-to-send-email-when-vacation-approved.md)]

   ![承認された電子メールのテンプレートを構成する](./media/sequential-modern-approvals/yes-email-config.png)

## <a name="add-an-update-action-for-approved-requests"></a>承認された要求の更新アクションを追加する

[!INCLUDE [add-action-to-update-sharepoint-with-approval](includes/add-action-to-update-sharepoint-with-approval.md)]

> [!NOTE]
> **[サイト アドレス]**、**[リスト名]**、**[ID]**、および **[タイトル]** は必須です。
>
>

![アイテムの更新の構成](./media/modern-approvals/configure-update-item.png)

## <a name="add-an-email-action-for-rejections"></a>却下に電子メール アクションを追加する

[!INCLUDE [add-action-to-send-email-when-vacation-rejected](includes/add-action-to-send-email-when-vacation-rejected.md)]

![却下された要求を構成する](./media/modern-approvals/configure-rejected-email.png)

## <a name="add-update-action-for-rejected-requests"></a>却下された要求に更新アクションを追加する

[!INCLUDE [add-action-to-update-sharepoint-with-rejection](includes/add-action-to-update-sharepoint-with-rejection.md)]

   > [!NOTE]
   > **[サイト アドレス]**、**[リスト名]**、**[ID]**、および **[タイトル]** は必須です。
   >
   >

![アイテムの更新カード](./media/modern-approvals/configure-update-item-no.png)

1. **[フローの更新]** を選択して、行った作業を保存します。
   
    ![更新アクションを選択する](./media/modern-approvals/update.png)

ステップに従っている場合、フローは次のスクリーン ショットのようになります。

![フローの概要](./media/modern-approvals/completed-flow.png)

これでフローが作成されました。テストしてみましょう。

## <a name="request-an-approval"></a>承認の要求

[!INCLUDE [request-vacation-approval](includes/request-vacation-approval.md)]

これでフローの作成およびテストが終了したので、フローの使い方を他のユーザーに知らせてください。

## <a name="learn-more"></a>詳細については、こちらをご覧ください

* [承認待ちの要求](approve-reject-requests.md)を表示し、管理する
* [シーケンシャル承認フロー](sequential-modern-approvals.md)を作成する
* [並列承認フローを作成する](parallel-modern-approvals.md)
* [Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリをインストールします。
