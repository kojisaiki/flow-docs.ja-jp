---
title: "ボタン フローを作成する | Microsoft Docs"
description: "ボタンからトリガーしたフローを作成する方法について説明します。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: s8ozmlVRV-Q
courseduration: 11m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: e72013611d6dbd21c06716805d42fbdd4eff7cfc
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="create-a-button-flow"></a>ボタン フローを作成する
このトピックでは、Contoso Flooring Company の**ボタン フローを構築する**方法について説明します。 

ボタン フローを使用すると、チームに**電子メールを送信**し、実行する**タスクについてアラームを送信**することができます。 フローの**所有権**は、**1 人の worker に割り当てる**か、**チームの複数のメンバーで共有する**ことができます。  

1. まず [Microsoft Flow Web サイト](https://ms.flow.microsoft.com)にアクセスし、サインインします。
2. サインインを完了したら、**[マイ フロー]**、**[一から作成]** の順に選択します。
   
    ![一から作成](./media/learning-create-button-flow/2-create-from-blank.png)
   
    最初に必要なものはトリガーです。 ボタン フローは使いやすいものです。 
3. リストに表示されない場合は、ページの下部で **[多数のコネクタやトリガーを検索する]** を選択し、「**ボタン**」と入力すると、ポップアップ表示されます。 
4. **[モバイル用のフロー ボタン]** を選択します。
   
    ![[検索] ボタン](./media/learning-create-button-flow/3-button-flow.png) 
5. **[モバイル用のフロー ボタン - 手動でフローをトリガーする]** を選択します。
   
    ![手動トリガーを選択する](./media/learning-create-button-flow/4-press-it.png)
6. 入力画面で **[Add input text]\(入力テキストの追加\)** を選択します。
   
    ![入力を追加する](./media/learning-create-button-flow/5-add-input.png)
7. 最初のテキスト ボックスに「**Contoso Flooring**」と入力し、2 つ目のテキスト ボックスに「**倉庫の配送電子メール**」と入力します。
   
    ![入力を追加する](./media/learning-create-button-flow/6-text-for-flow.png)
8. **[新しいステップ]** を選択します。 
   
    ![入力テキスト](./media/learning-create-button-flow/7-input-description.png)
9. **[アクションの追加]** を選択します。 
   
    ![アクションの追加](./media/learning-create-button-flow/8-add-an-action.png)
10. **[Office 365 Outlook]** コネクタを選択します。 表示されない場合は、「**outlook**」を検索します。
    
     ![Outlook の検索](./media/learning-create-button-flow/9-search-outlook.png)
11. **[Office 365 Outlook - 電子メールの送信]** を選択します。
    
     ![電子メールを送信する](./media/learning-create-button-flow/10-send-email.png)
    
     ボタンが押されると、チームのメンバーが建物内のどこにいても電子メールが Contoso Warehouse チーム全体に送信されるので、配信が到達したことを知らせることができます。
12. フィールドを展開し、Contoso Flooring に合わせて電子メールをカスタマイズします。
    
    1. **[宛先]** フィールドに、組織で使用できる電子メール アドレスを入力します。
    2. **[件名]** フィールドに「**配送品の到着**」と入力します。 
    3. 右側に **[動的なコンテンツ]** ボックスがポップアップ表示されます。 件名行に、ボタンを押した正確な日時を表示するには、**[日付]** と **[タイムスタンプ]** を選択します。 
       
        ![電子メールの日時](./media/learning-create-button-flow/11-email-date-time.png)
13. 次に、電子メールに簡単な**本文** (「**倉庫チームの皆さん、本日の配送心が到着しましたので、荷下ろし庫に来てください**」など) を入力します。
14. **[フローの作成]** を選択してフローを保存します。
    
     ![フローの作成](./media/learning-create-button-flow/12-create-flow.png)

## <a name="create-a-team-flow"></a>チーム フローを作成する
このボタン フローは、チーム フローの作成方法の一例として使用することができます。 このフローの作成者が病欠した場合はどうなるでしょうか。 作成者が会社を辞めた場合はどうなるでしょうか。 このフローを継続して使用できるようにする必要があります。 そのために、共同所有者を追加します。

1. フローの**チーム アイコン**を選択し、共同所有者を追加します。
   
    ![チーム フローを作成する](./media/learning-create-button-flow/13-create-team-flow.png) 
2. 名前、電子メール アドレス、またはユーザー グループを入力して共同所有者を追加します
   
    ![共同所有者を追加する](./media/learning-create-button-flow/14-add-co-owners.png)
3. 共同所有者を削除するには、名前の右にあるごみ箱アイコンを選択します。
   
    ![共同所有者を削除する](./media/learning-create-button-flow/15-remove-co-owners.png)
4. **[この所有者の削除]** を選択して削除を完了します。
   
    ![共同所有者を削除する](./media/learning-create-button-flow/16-agree-to-remove.png)

## <a name="summary"></a>概要
このレッスンでは、**ボタン フローの作成**方法について説明しました。 

わずかな時間で、倉庫の作業員が自分のチームに**配送品の到着**について**知らせる**機能がフローに追加されました。そのため、その場で待機して、他の作業に使用できる貴重な時間を無駄にする必要がなくなります。 

次に、作業員はそのボタンをチーム メンバーと共有し、その作業員がいない場合でも同じフローをトリガーできるようにしました。

## <a name="next-lesson"></a>次のレッスン
次のレッスンでは、**プッシュ通知**を使用するフローを作成する方法について説明します。

