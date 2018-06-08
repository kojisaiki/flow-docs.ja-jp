---
title: フローでの承認待ち | Microsoft Docs
description: フローでは、外部イベントが発生するのを待ってから、アクションを実行できます。たとえば、ユーザーが変更を承認または拒否してから、意思決定の通知を送信することができます。
services: ''
suite: flow
documentationcenter: na
author: merwanhade
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/15/2018
ms.author: merwanhade
ms.openlocfilehash: b75cacf14da7d1b339e8a2f9e35eece389c2a6f7
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "29563160"
---
# <a name="wait-for-approval-in-microsoft-flow"></a>Microsoft Flow での承認待ち

> [!VIDEO https://www.youtube.com/embed/W6oxcYRtW-8?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF]
>


SharePoint で項目を作成した場合に、承認電子メールを担当者に送信し、その項目が承認されたか拒否されたかが、その担当者から通知されるフローを作成します。 このチュートリアルに厳密に従うために、ここではトリガー アクションとしてシンプルな SharePoint リストを作成しますが、Dropbox、OneDrive などの別のデータ ソースを使用することもできます。

**前提条件**

* **Project Tracker** という名前の簡単な SharePoint リストを作成し、「**Title**」という名前の列を追加し、「**Assigned To**」という名前のユーザー列またはグループ列を追加します。

   ![Project Tracker SPO リストのイメージ](./media/wait-for-approvals/project-tracker.png)

## <a name="add-an-event-to-trigger-the-flow"></a>フローをトリガーするイベントの追加

1. [Microsoft Flow](https://flow.microsoft.com) にサインインし、上部のナビゲーション バーの **[自分のフロー]** を選んで、**[一から作成]** を選びます。

1. **[Search hundreds of connectors and triggers]\(多数のコネクタやトリガーを検索する\)** ボックスを選び、「**新しいアイテム**」と入力して、**[SharePoint - when an item is created]\(SharePoint - アイテム作成時\)** に移動します。

1. メッセージが表示されたら、SharePoint にサインインします。
1. **[サイトのアドレス]** に、リストを含む SharePoint サイトの URL を入力します。

1. **[リスト名]** で、前に作成したリストを選びます。 説明のとおりに設定してきた場合、名前は **Project Tracker** です。

    ![SPO リスト名のイメージ](./media/wait-for-approvals/SPO-list-name.png)

## <a name="add-the-resulting-action"></a>結果アクションの追加

1. **[新しいステップ]** ボタンを選んで、**[アクションの追加]** を選びます。

1. **[Search all connectors and actions]\(すべてのコネクタとアクションを検索する\)** ボックスに、「**メールの送信**」と入力するか貼り付けて、**[Office 365 Outlook - Send email with options]\(Office 365 Outlook - 電子メールとオプションの送信\)** を選びます。

1. メッセージが表示されたら、Office 365 Outlook にサインインします。

1. **[宛先]** フィールドを選び、**[Assigned to Email]\(割り当て先電子メール\)** トークンを選びます。

    **[Assigned To]\(割り当て先\)** 列のユーザーがメールを受け取って、項目を承認または拒否します。 フローをテストするために項目を作成する場合は、このフィールドに自身を指定します。 このようにして自分で項目を承認または拒否し、さらにその通知メールも受け取ります。

    > [!NOTE]
    > **[件名]** フィールドと **[ユーザー オプション]** フィールドは、ニーズに合わせてカスタマイズできます。

    ![承認の電子メールの送信先フィールドのイメージ](./media/wait-for-approvals/send-approval-email-to.png)

## <a name="add-a-condition"></a>条件の追加

1. **[新しいステップ]** ボタンを選んで、**[Add a condition]\(条件の追加\)** を選びます。

    ![条件追加のイメージ](./media/wait-for-approvals/add-a-condition.png)
1. 最初のボックスを選び、**SelectedOption** トークンを選びます。
1. 最後のボックスを選び、「**Approve**」と入力します。

    ![条件カードのイメージ](./media/wait-for-approvals/condition-card-2.png)

1. **[はいの場合]** 領域で **[アクションの追加]** を選択します。

1. **[Search all connectors and actions]\(すべてのコネクタとアクションを検索する\)** ボックスに、「**メールの送信**」と入力するか貼り付けて、**[Office 365 Outlook - 電子メールを送信]** を選びます。

1. **[宛先]** フィールドに、受信者 (**[Created by Email]\(作成者の電子メール\)** など) を入力します。

1. **[Subject (件名)]** ボックスで、件名を指定します。

    たとえば、**[Assigned To DisplayName (担当者の表示名)]** を選択し、「**has approved**」と入力して前後にスペースを挿入します。次に、**[Title]** を選択します。

1. **[Body (本文)]** ボックスで、電子メールの本文を指定します (「**プロジェクトの次のフェーズに進む準備ができました。**」など)。

    > [!NOTE]
    > SharePoint リストに項目を作成したユーザーに、プロジェクトが承認されたか拒否されたかが通知されます。

    ![はいの場合の電子メールの送信のイメージ](./media/wait-for-approvals/if-yes-send-email-card-3.png)

1. **[いいえの場合]** 領域では、直前の 5 つの手順を繰り返します。ただし、**[Subject (件名)]** と **[Body (本文)]** には、プロジェクトが拒否された旨を入力します。

     ![いいえの場合の電子メールの送信のイメージ](./media/wait-for-approvals/no-send-email-2.png)

## <a name="finish-and-test-your-flow"></a>フローの完了およびテスト

1. フローに名前を付けて、**[Create flow (フローの作成)]** を選択します。

     ![フロー作成のイメージ](./media/wait-for-approvals/create-flow.png)
1. SharePoint リストに項目を作成します。

    承認メールが指定した受信者に送信されます。 受信者がそのメールで **[承認]** または **[却下]** を選ぶと、メールで返信が届きます。

## <a name="learn-more"></a>詳細については、こちらをご覧ください

* [1 人の承認者による最新の承認のチュートリアル](modern-approvals.md)
* [シーケンシャル承認](sequential-modern-approvals.md)を作成する
* [並列承認](parallel-modern-approvals.md)を作成する
* [外出先で要求](mobile-approvals.md)を承認する
