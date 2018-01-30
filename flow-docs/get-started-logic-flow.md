---
title: "フローを作成してタスクを自動化する | Microsoft Docs"
description: "フローを作成して、イベント (SharePoint リストに行を追加するなど) が発生したときに 1 つ以上のアクション (メールの送信など) を自動的に実行します。"
services: 
suite: flow
documentationcenter: na
author: aftowen
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/28/2017
ms.author: deonhe
ms.openlocfilehash: fd6ed3973ed09442108bf780f76b750deea20eeb
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="create-a-flow-in-microsoft-flow"></a>Microsoft Flow でのフローの作成
<iframe width="560" height="315" src="https://www.youtube.com/embed/Gt3CMhLAQqE?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

イベントでトリガーされた後、1 つまたは複数のタスクを自動的に実行するフローを作成します。 たとえば、指定したキーワードが含まれるツイートを誰かが送信したときにメールで通知するフローを作成するとします。 この例では、ツイートの送信がイベント、メールの送信がアクションになります。

## <a name="prerequisites"></a>前提条件
* [flow.microsoft.com](https://flow.microsoft.com) のアカウント
* Twitter アカウント
* Office 365 の資格情報

## <a name="specify-an-event-to-start-the-flow"></a>フローを開始するイベントを指定する
最初に、どのようなイベントまたは*トリガー*でフローを開始するのか選択する必要があります。

1. [flow.microsoft.com](https://flow.microsoft.com) で、上部のナビゲーション バーの **[自分のフロー]** を選択し、**[一から作成]** を選択します。
   
    ![左側のナビゲーション バーのフロー オプション](./media/get-started-logic-flow/create-logic-flow.png)
2. **[すべてのコネクタとトリガーを検索する]** ボックスに、「**Twitter**」と入力するか貼り付け、**[Twitter - 新しいツイートが表示されたとき]** を選択します。
   
    ![Twitter イベント](./media/get-started-logic-flow/twitter-search.png)
3. Twitter アカウントをまだ Microsoft Flow に関連付けていない場合は、**[Sign in to Twitter (Twitter にサインイン)]** を選択し、資格情報を入力します。
   
    ![Twitter にサインイン](./media/get-started-logic-flow/twitter-signin.png)
4. **[検索文字列]** ボックスに、検索するキーワードを入力します。
   
    ![Twitter キーワード](./media/get-started-logic-flow/twitter-keyword.png)

## <a name="specify-an-action"></a>アクションの指定
1. **[新しいステップ]** を選択し、**[アクションの追加]** を選択します。
   
    ![アクションの追加](./media/get-started-logic-flow/add-action-icon.png)
2. **[すべてのコネクタとアクションを検索する]** と表示されているボックスで、「**メールの送信**」と入力するか貼り付けて、**[Office 365 Outlook - 電子メールの送信]** を選択します。
   
    ![アクションの一覧](./media/get-started-logic-flow/send-email.png)
3. メッセージが表示されたら、サインイン ボタンを選択し、資格情報を入力します。
4. 表示されたフォームの **[To]** (宛先) ボックスに電子メール アドレスを入力するか貼り付けます。次に、表示された連絡先の一覧から名前を選択します。
   
    ![空の電子メール メッセージ](./media/get-started-logic-flow/blank-email.png)
5. **[Subject]** (件名) ボックスに「**New tweet from: (新しいツイートの送信元:)**」と入力するか貼り付け、空白を入力します。
   
    ![プレースホルダーが含まれる件名](./media/get-started-logic-flow/message-token.png)
6. トークンの一覧で、**[ツイート作成者]** トークンを選択し、そのプレースホルダーを追加します。
   
    ![パラメーターの追加](./media/get-started-logic-flow/add-parameter.png)
7. **[本文]** ボックスの中をクリックまたはタップし、**[ツイート テキスト]** トークンをクリックまたはタップしてそのプレースホルダーを追加します。
8. (任意) トークン、その他のコンテンツ、またはその両方を電子メールの本文に追加します。
9. 画面上部でフローに名前を付けて、**[フローの作成]** を選択します。
   
    ![[フローの作成] ボタンの選択](./media/get-started-logic-flow/create-button.png)
10. **[Done (完了)]** を選択してフローの一覧を更新します。
    
     ![完了ボタンを選択](./media/get-started-logic-flow/done-button.png)
11. 指定したキーワードが含まれるツイートを送信します。
    
     1 分以内に、新しいツイートについてメールで通知されます。

## <a name="manage-a-flow"></a>フローの管理
1. [flow.microsoft.com](https://flow.microsoft.com) で、上部のナビゲーション バーの **[自分のフロー]** を選択します。
2. フローの一覧で、次のいずれかを実行します。
   
   * フローを一時停止するには、**[オフ]** に切り替えます。
     
       ![フローの一時停止](./media/get-started-logic-flow/pause-flow.png)
   * フローを再開するには、**[オン]** に切り替えます。
     
       ![フローの再開](./media/get-started-logic-flow/resume-flow.png)
   * フローを編集するには、編集するフローに対応している鉛筆アイコンを選択します。
     
       ![フローの選択](./media/get-started-logic-flow/select-flow.png)
   * フローを削除するには、**[...]** アイコンを選択し、**[削除]** を選択し、表示されたメッセージ ボックスで **[削除]** を選択します。
     
       ![削除アイコン](./media/get-started-logic-flow/delete-icon.png)
   * フローの実行履歴を表示するには、**[マイ フロー]** ページからフローを選択します。ページの **[実行履歴]** セクションに履歴が表示されます。
     
       ![実行履歴](./media/get-started-logic-flow/run-history.png)
     
     実行の一覧からフロー実行を選択して、各ステップの入力と出力を表示します。

**注**: アカウントには最大 50 個のフローを作成できます。 既に 50 個ある場合は、1 つ削除してから、フローを作成してください。

## <a name="next-steps"></a>次のステップ
* フローに、さまざまな通知方法などの[ステップを追加](multi-step-logic-flow.md)します。
* アクションを毎日、特定の日付に、または一定時間 (分) 後に実行する場合は、[スケジュールに従ってタスクを実行](run-tasks-on-a-schedule.md)します。
* [フローをアプリに追加](https://powerapps.microsoft.com/tutorials/using-logic-flows/)して、アプリがクラウド内のロジックを開始できるようにします。
* [チーム フローを作成](create-team-flows.md)し、他のユーザーを招待して共同でフローを設計します。
