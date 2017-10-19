---
title: "フローでの承認待ち | Microsoft Docs"
description: "フローでは、外部イベントが発生するのを待ってから、アクションを実行できます。たとえば、ユーザーが変更を承認または拒否してから、意思決定の通知を送信することができます。"
services: 
suite: flow
documentationcenter: na
author: merwanhade
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/24/2016
ms.author: merwanhade
ms.openlocfilehash: a26566486cf6310dc1c33ef226bfc37b30a5ad16
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="wait-for-approval-in-microsoft-flow"></a>Microsoft Flow での承認待ち
<iframe width="560" height="315" src="https://www.youtube.com/embed/W6oxcYRtW-8?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

SharePoint で項目を作成した場合に、承認電子メールを担当者に送信し、その項目が承認されたか拒否されたかが、その担当者から通知されるフローを作成します。 このチュートリアルに厳密に従うために、ここではトリガー アクションとしてシンプルな SharePoint リストを作成しますが、Dropbox、OneDrive などの別のデータ ソースを使用することもできます。

**前提条件**

* **[Title]** 列が含まれる **Project Tracker** という名前のシンプルな SharePoint Online リストを作成し、**[Assigned To]** という名前のユーザー列またはグループ列を追加します。
  
   ![Project Tracker SPO リストのイメージ](./media/wait-for-approvals/project-tracker.png)

## <a name="add-an-event-to-trigger-the-flow"></a>フローをトリガーするイベントの追加
1. [flow.microsoft.com](https://flow.microsoft.com) で、上部のナビゲーション バーの **[自分のフロー]** を選択し、**[Create new flow (新しいフローの作成])** を選択します。
   
    ![新しいフローの作成のイメージ](./media/wait-for-approvals/create-a-new-flow.png)
2. **[How would you like to start? (どのように開始しますか)]** ボックスに、「**new item**」と入力するか貼り付け、**[SharePoint Online - when a new item is created (SharePoint Online - 新しい項目が作成されたとき)]** を選択します。
   
    ![SPO トリガーのイメージ](./media/wait-for-approvals/send-approval-email-select-2.png)
3. メッセージが表示されたら、SharePoint Online にサインインします。
4. **[Site url (サイトの URL)]** で、リストが含まれるサイトの URL を入力するか貼り付けます。
   
    ![SPO サイト URL のイメージ](./media/wait-for-approvals/SPO-site-url.png)
5. **[List name (リスト名)]** で、**[Project Tracker]** などのリストを選択します。
   
    ![SPO リスト名のイメージ](./media/wait-for-approvals/SPO-list-name.png)

## <a name="add-the-resulting-action"></a>結果アクションの追加
1. **+** ボタンを選択し、**[アクションの追加]** を選択します。
   
    ![アクションの追加のイメージ](./media/wait-for-approvals/add-an-action.png)
2. **[What would you like to do next? (次に何を実行しますか)]** ボックスに、「**電子メールの送信**」と入力するか貼り付け、**[Office 365 Outlook - 承認の電子メールを送信します]** を選択します。
   
    ![承認の電子メールの送信のイメージ](./media/wait-for-approvals/send-approval-mail.png)
3. メッセージが表示されたら、Office 365 Outlook にサインインします。
4. **[To (宛先)]** フィールドを選択し、**[Assigned to EMail (担当者の電子メール)]** を選択します。
   
    **[Assigned To]** 列のユーザーが、電子メールを受け取って、項目を承認または拒否します。 フローをテストするために項目を作成する場合は、このフィールドに自身を指定します。 このようにして自分で項目を承認または拒否し、さらにその通知メールも受け取ります。
   
    **注**: **[Subject (件名)]** フィールドと **[User Options (ユーザー オプション)]** フィールドは、ニーズに合わせてカスタマイズできます。
   
    ![承認の電子メールの送信先フィールドのイメージ](./media/wait-for-approvals/send-approval-email-to.png)

## <a name="add-a-condition"></a>条件の追加
1. **+** ボタンを選択し、**[条件の追加]** を選択します。
   
    ![条件追加のイメージ](./media/wait-for-approvals/add-a-condition.png)
2. **[オブジェクト名]** フィールドで、**[SelectedOption]** を選択します。
3. **[値]** フィールドに、「**Approve**」と入力するか貼り付けます。
   
    ![条件カードのイメージ](./media/wait-for-approvals/condition-card-2.png)
4. **[はいの場合]** 領域で **[アクションの追加]** を選択します。
   
    ![はいの場合のアクションの追加のイメージ](./media/wait-for-approvals/yes-add-an-action.png)
5. **[What would you like to do next? (次に何を実行しますか)]** ボックスに、「**電子メールの送信**」と入力するか貼り付け、**[Office 365 Outlook - 電子メールの送信]** を選択します。
   
    ![はいの場合の電子メールの送信のイメージ](./media/wait-for-approvals/yes-send-email.png)
6. **[Subject (件名)]** ボックスで、件名を指定します。
   
    たとえば、**[Assigned To DisplayName (担当者の表示名)]** を選択し、「**has approved**」と入力して前後にスペースを挿入します。次に、**[Title]** を選択します。
7. **[Body (本文)]** ボックスで、電子メールの本文を指定します (「**プロジェクトの次のフェーズに進む準備ができました。**」など)。
8. **[To (宛先)]** フィールドに、受信者 (**[Created by EMail (電子メールの作成者)]** など) を入力します。
   
    SharePoint リストに項目を作成したユーザーに、プロジェクトが承認されたか拒否されたかが通知されます。
   
    ![はいの場合の電子メールの送信のイメージ](./media/wait-for-approvals/if-yes-send-email-card-3.png)
9. **[いいえの場合]** 領域では、直前の 5 つの手順を繰り返します。ただし、**[Subject (件名)]** と **[Body (本文)]** には、プロジェクトが拒否された旨を入力します。
   
     ![いいえの場合の電子メールの送信のイメージ](./media/wait-for-approvals/no-send-email-2.png)

## <a name="finish-and-test-your-flow"></a>フローの完了およびテスト
1. フローに名前を付けて、**[Create flow (フローの作成)]** を選択します。
   
     ![フロー作成のイメージ](./media/wait-for-approvals/create-flow.png)
2. SharePoint リストに項目を作成します。
   
    承認メールは、指定した受信者に送信されます。 受信者がその電子メールで **[承認]** または **[却下]** を選択すると、電子メールで返信が届きます。 

