---
title: "フローからツイートを投稿する | Microsoft Docs"
description: "SharePoint リストのデータに基づいてツイートを投稿する方法を説明します。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: y1iDal8XPAo
courseduration: 15m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: 4015377204edfde289cf04835b2660288d0690e1
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="post-tweets-from-a-flow"></a>フローによるツイートの投稿
このフローでは、**Contoso Flooring** のマーケティング チームが自分たちの **Twitter の投稿**と投稿の日付を保存する場所として **SharePoint** リストを作成します。 このリストから、コンテンツを自動ツイートするフローを作成します。 

## <a name="connect-microsoft-flow-services"></a>Microsoft Flow サービスへの接続
このトピックでは、**SharePoint** と **Twitter** のサービスを使用します。 初めてのサービスを使用する場合は、まずその新しいサービスに接続する必要があります。 

1. Microsoft Flow では、**歯車アイコン**を選択し、**[接続]** を選択します。
   
    ![接続の取得](./media/learning-push-notifications/2-get-connection.png) 
2. **[+ 接続の作成]** を選択します。
   
    ![接続の作成](./media/learning-push-notifications/3-create-connection.png) 
3. リストを下にスクロールし、Twitter を見つけて、**[+]** を選択します。
   
    ![プラス記号をクリック](./media/learning-push-notifications/4-click-plus.png)
4. Twitter アカウントを承認には、ユーザー名またはメール アドレスと、パスワードを入力し、**[Authorize app]\(アプリの承認\)** を選択します。
   
    ![ID とパスワードの作成](./media/learning-push-notifications/5-create-id-pswd.png)
5. 接続を確認するには、**歯車アイコン**、**[接続]** の順に選択します。
   
    ![自分の接続](./media/learning-push-notifications/6-my-connections.png)
   
    新しい Twitter 接続と、作成済みのその他の接続が表示されるはずです。 
   
    ![Twitter 接続](./media/learning-push-notifications/7-twitter-connection.png)

## <a name="build-a-sharepoint-list"></a>SharePoint リストの作成
最初に、Contoso Flooring 用に新しい SharePoint Online リストを作成します。 

1. SharePoint Online で、**[新規]**、**[リスト]** の順に選択します。
   
    ![新しいリストの作成](./media/learning-push-notifications/1-new-list.png)
2. リストに "**Contoso ツイート** "という名前を付けます。 
3. **[サイト ナビゲーションに表示]** チェックボックスをオフにして、**[作成]** をクリックします。
   
    ![リストの作成](./media/learning-push-notifications/2-name-create-list.png)
   
    **[作成]** を選択すると、新しいリストが表示されます。
4. 既定では、リストには "**タイトル**" という列が 1 つあるだけです。 列を追加し、"**ツイートのコンテンツ**" という名前を付けます。 ツイートした内容はここに表示されます。 
   
   1. プラス記号を選択し、**[その他]** を選択します。
      
       ![リストの作成](./media/learning-push-notifications/3-add-more-column-types.png)
   2. **[複数行テキスト]** を選択し、**[OK]** を選択します。
      
       ![リストの作成](./media/learning-push-notifications/4-add-column.png)
5. ツイートの日時を示す列を追加し、"**ツイートの日付**" という名前を付けます。
   
   1. "**ツイートのコンテンツ**" の場合と同様に、**[その他]** を選択します。
      
       ![日付と時刻の列](./media/learning-push-notifications/5-date-time-col.png)
   2. 下にスクロールして **[日付と時刻の形式]** を見つけます。 **[日付と時刻]** を選択します。これにより日付と時刻の両方が含められます。
      
       ![日付と時刻](./media/learning-push-notifications/6-date-time-must-do.png)
   3. **[OK]** を選択します。 SharePoint サイトに "**Contoso ツイート**" リストが表示されます。このリストには新しい項目を追加できます。

## <a name="build-the-flow"></a>フローの作成
リストが作成されたので、フローを作成できます。

### <a name="choose-a-trigger"></a>トリガーの選択
1. Microsoft Flow で、**[自分のフロー]** に進み、**[一から作成]** を選択します。
   
    ![一から作成](./media/learning-push-notifications/8-create-from-blank.png)
2. **[項目が作成されたとき]** を選択します。
   
    ![トリガーの追加](./media/learning-push-notifications/9-add-trigger.png)
   
    ツイートのコンテンツを含む新しい行が追加されたときに実行されるトリガーを設定します。
3. SharePoint サイトを選択し、前に設定した "**Contoso ツイート**" リストを選択します。
   
    ![作成された新しい項目](./media/learning-push-notifications/11-set-trigger.png)

これがトリガーの対象になります。

### <a name="add-an-action-to-delay-posting"></a>投稿を延期するアクションの追加
1. **[+ 新しいステップ]** を選択し、**[アクションの追加]** を選択します。 
   
    ![ステップとアクションの追加](./media/learning-push-notifications/12-add-step-and-action.png)
2. **[スケジュール]** サービスで、**[延期期限]** を選択します。 
   
    ![延期期限](./media/learning-push-notifications/13-delay-until-schedule.png)  
3. 延期の値を設定します。
   
   1. **[タイムスタンプ]** フィールドをクリックまたはタップします。 
   2. 動的なコンテンツ ボックスが開いたら、一番下までスクロールし、SharePoint リストの次の 3 つの列を確認します:**タイトル**、**ツイートの日付**、**ツイートのコンテンツ**。
   3. **[ツイートの日付]** を選択します。 
      
       ![延期期限タイムスタンプ](./media/learning-push-notifications/14-delay-until-timestamp.png)
      
       これで、SharePoint リストに誰かが何かを追加した場合、**[ツイートの日付]** 列で設定した日付と時刻までアクションは延期されます。
      
       ![動的なタイムスタンプ](./media/learning-push-notifications/15-dynamic-timestamp.png)

### <a name="add-an-action-to-post-a-tweet"></a>ツイートを投稿するアクションの追加
今度は、**[ツイートの日付]** 列で指定した日付と時刻に、フローによって実行される別のアクションを追加します。

1. **[+ 新しいステップ]**、**[アクションの追加]** の順に選択し、**[Twitter]** を検索します。
   
    ![ツイートの追加](./media/learning-push-notifications/16-add-tweet.png) 
2. アクション **[Twitter - ツイートの投稿]** を選択します。
   
    ![ツイートの投稿](./media/learning-push-notifications/17-post-tweet.png) 
3. **[ツイートのテキスト]** フィールドをクリックまたはタップし、動的コンテンツ ボックスで、**[ツイートのコンテンツ]** を選択します。 作成したシーケンスを次に示します。 
   
    ![コンテンツのツイート日](./media/learning-push-notifications/18-tweet-date-content.png)
4. **[フローの作成]** を選択します。
   
    ![フローの作成](./media/learning-push-notifications/19-tiny-create.png) 
5. **[完了]** を選択します。
   
    ![[完了] をクリック](./media/learning-push-notifications/19-click-done.png)
   
    これで、フローが完成しました。
   
    ![フローの実行](./media/learning-push-notifications/20-flow-is-done.png)
   
    SharePoint リストに新しい項目が作成されると、フローは、設定済みの日付まで投稿を延期します。 その日付がきたら、リスト内の **[ツイートのコンテンツ]** 列にあるテキストを Twitter に投稿します。

## <a name="next-lesson"></a>次のレッスン
次のレッスンでは、**[繰り返し]** と呼ばれるトリガーを使用し、**スケジュールに従ってフローを実行**する方法について学習します。

