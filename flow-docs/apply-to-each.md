---
title: Apply to each アクションを使用して項目の配列をループ処理する | Microsoft Docs
description: Microsoft Flow を使って項目の配列をループ処理し、複数の条件を調べ、それらの条件に基づいてアクションを実行します。
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
ms.date: 03/16/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 914fe6d84bb63e1f3e184794d34fbfd58ad30963
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690171"
---
# <a name="use-the-apply-to-each-action-in-microsoft-flow-to-process-a-list-of-items-periodically"></a>Microsoft Flow の Apply to each アクションを使用して項目の一覧を定期的に処理する
受信トレイに新しいメールが到着したときなど、多くのトリガーはイベントに基づいてフローをすぐに開始できます。 このようなトリガーは便利ですが、定義されているスケジュールでデータ ソースを照会し、データ ソース内の項目のプロパティに基づいて特定のアクションを行うようなフローを実行したいこともあります。 そのような処理のために、スケジュール (1 日 1 回など) に従ってフローを開始し、**Apply to each** などのループ アクションを使って項目の一覧を処理することができます。 たとえば、**Apply to each** を使うと、データベースのレコードや、Microsoft SharePoint の項目の一覧を更新できます。

このチュートリアルでは、15 分ごとに実行して以下の処理を行うフローを作成します。

1. Office 365 Outlook 受信トレイにある最新の未読メッセージを 10 件取得します。
2. 10 件の各メッセージを調べて、件名に**meet now** (会議の開始) が含まれるかどうかを確認します。
3. 上司からのメールかどうか、または高重要度で送信されたかどうかを確認します。
4. 件名に**meet now** (会議の開始) が含まれる、上司からのメールまたは高重要度で送信されたメールについて、プッシュ通知を送信し、既読としてマークします。

次の図は、このチュートリアルで作成するフローの詳細です。

![作成するフローの概要](./media/apply-to-each/foreach-flow-visio.png)

## <a name="prerequisites"></a>前提条件
このチュートリアルの手順を正しく実行するための要件を次に示します。

* [Microsoft Flow](https://flow.microsoft.com) を使うために登録されたアカウント。
* Office 365 Outlook アカウント。
* [Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリ。
* Office 365 Outlook とプッシュ通知サービスへの接続。

## <a name="create-a-flow"></a>フローを作成する
1. [Microsoft Flow](https://flow.microsoft.com) にサインインします。
2. **[マイ フロー]** タブを選び、一からフローを作成します。
   
    ![一から作成する](./media/apply-to-each/foreach-1.png)
3. 検索ボックスに「schedule」と入力し、スケジュールに関係のあるすべてのサービスとトリガーを検索します。
4. **[Schedule - Recurrence]** (スケジュール - 繰り返し) トリガーを選び、次に指定するスケジュールでフローを実行することを示します。
   
    ![繰り返しアクションのスケジュール](./media/apply-to-each/foreach-2.png)
5. 15 分ごとに実行するようにスケジュールを設定します。
   
    ![実行のスケジュール](./media/apply-to-each/foreach-3.png)
6. **[+ 新しいステップ]**、**[アクションの追加]** の順に選び、検索ボックスに「**outlook**」と入力して、Microsoft Outlook に関連するすべてのアクションを検索します。
7. **[Office 365 Outlook - 電子メールの取得]** アクションを選びます。
   
    ![電子メールの取得アクションの選択](./media/apply-to-each/foreach-4.png)
8. **[電子メールの取得]** カードが開きます。 受信トレイ フォルダーの先頭から未読のメールを 10 件選ぶように、**[電子メールの取得]** カードを構成します。 添付ファイルはフローで使われないため含めません。
   
    ![電子メール カードの構成](./media/apply-to-each/foreach-5.png)
   
   > [!NOTE]
   > ここまでで、受信トレイからメールをいくつか取得する単純なフローができました。 これらのメールは配列で返されます。**Apply to each** アクションには配列が必要であり、これがまさに必要なことにあたります。
   > 
   > 

## <a name="add-actions-and-conditions"></a>アクションと条件を追加する
1. **[+ 新しいステップ]**、**[More]** (その他) の順に選び、**[Apply to Each の追加]** アクションを選びます。
   
    ![Apply to Each の選択](./media/apply-to-each/foreach-6.png)
2. **[Apply to each]** カードの **[以前の手順から出力を選択]** ボックスに **Body** トークンを挿入します。 これにより、**Apply to each** アクションで使うメールの本文が取得されます。
   
    ![Body トークンの追加](./media/apply-to-each/foreach-7.png)
3. **[条件の追加]** を選びます。
   
    ![条件の追加](./media/apply-to-each/foreach-8.png)
4. 各メールの件名で文字列 "meet now" を検索するように、**[条件]** カードを構成します。
   
   * **[オブジェクト名]** ボックスに **Subject** トークンを挿入します。
   * **[リレーションシップ]** の一覧で **[次の値を含む]** を選びます。
   * **[値]** ボックスに「**meet now**」と入力します。
     
     ![条件の構成](./media/apply-to-each/foreach-subject-condition.png)
5. **[More]** (その他) を選び、**[IF YES, DO NOTHING]** 分岐から **[条件の追加]** を選びます。 **[条件 2]** カードが開きます。そのカードを次のように構成します。
   
   * **[オブジェクト名]** ボックスに **Importance** トークンを挿入します。
   * **[リレーションシップ]** ボックスの一覧で **[次の値に等しい]** を選びます。
   * **[値]** ボックスに「**High**」と入力します。
     
     ![条件の追加](./media/apply-to-each/foreach-importance-condition.png)
6. **[IF YES, DO NOTHING]** セクションから **[アクションの追加]** を選びます。 **[アクションを選択してください]** カードが開くので、検索条件 (**meet now** を含むメールが高重要度で送信された) が真の場合の動作を定義します。
   
    ![アクションの追加](./media/apply-to-each/foreach-9.png)
7. **通知**を検索し、**[Notifications - Send me a mobile notification]** (通知 - モバイル通知を送信する) アクションを選びます。
   
    ![通知の検索と選択](./media/apply-to-each/foreach-10.png)
8. **[Send me a mobile notification]** (モバイル通知を送信する) カードで、メールの件名に "meet now" が含まれる場合に送信されるプッシュ通知の詳細を指定して、**[アクションの追加]** を選びます。
   
    ![通知の構成](./media/apply-to-each/foreach-11.png)
9. 検索語として「**開封済み**」と入力し、**[Office 365 Outlook - 開封済みにする]** アクションを選びます。 これにより、各メールはプッシュ通知送信後に開封済みになります。
   
    ![開封済みにするアクションの追加](./media/apply-to-each/foreach-12.png)
10. **[開封済みにする]** カードの **[メッセージ ID]** ボックスに **Message Id** トークンを追加します。 **Message Id** トークンを探すには、**[もっと見る]** を選ばなければならない場合があります。 これは、開封済みとして指定するメッセージの ID を示します。
    
     ![Message Id の追加](./media/apply-to-each/foreach-13.png)
11. **[条件 2]** カードの **[IF NO, DO NOTHING]** 分岐に戻ります。
    
    * **[アクションの追加]** を選び、検索ボックスに「**上司を取得する**」と入力します。
    * 検索結果の一覧から **[Office 365 ユーザー - 上司を取得する]** アクションを選びます。
    * **[上司を取得する]** カードの **[ユーザー]** ボックスに *完全な* メール アドレスを入力します。
      
      ![上司を取得するアクションの追加と構成](./media/apply-to-each/foreach-get-manager.png)
12. **[More]** (その他) を選び、**[IF NO]** 分岐から **[条件の追加]** を選びます。 **[条件 3]** カードが開きます。メール送信者のメール アドレス (From トークン) が上司のメール アドレス (Email トークン) と同じかどうかを調べるようにカードを構成します。
    
    * **[オブジェクト名]** ボックスに **From** トークンを挿入します。
    * **[リレーションシップ]** の一覧で **[次の値を含む]** を選びます。
    * **[値]** ボックスに **Email** トークンを入力します。
      
      ![検索条件の構成](./media/apply-to-each/foreach-condition3-card.png)
13. **[条件 3]** カードの **[IF YES, DO NOTHING]** セクションから **[アクションの追加]** を選びます。 **[IF YES]** カードが開くので、検索条件 (メールが上司から送信された) が真の場合の動作を定義します。
    
     ![条件の構成](./media/apply-to-each/foreah-condition3-add-action.png)
14. **通知**を検索し、**[Notifications - Send me a mobile notification]** (通知 - モバイル通知を送信する) アクションを選びます。
    
     ![通知アクションの検索](./media/apply-to-each/foreach-10.png)
15. **[Send me a mobile notification 2]** (モバイル通知を送信する 2) カードで、メールが上司からのものである場合に送信されるプッシュ通知の詳細を指定して、**[アクションの追加]** を選びます。
    
     ![通知カードの構成](./media/apply-to-each/foreach-boss-notification.png)
16. **[Office 365 Outlook - 開封済みにする]** アクションを追加します。 これにより、各メールはプッシュ通知送信後に開封済みになります。
    
     ![開封済みにするアクションの追加](./media/apply-to-each/foreach-12.png)
17. **[開封済みにする 2]** カードに **Message Id** トークンを追加します。 **Message Id** トークンを探すには、**[もっと見る]** を選ばなければならない場合があります。 これは、開封済みとして指定するメッセージの ID を示します。
    
     ![開封済みにするアクションの構成](./media/apply-to-each/foreach-mark-as-read2.png)
18. フローの名前を指定して作成します。
    
     ![フローに名前を付けて保存](./media/apply-to-each/foreach-14.png)

以上の手順に従うと、フローは次の図のようになるはずです。

![作成されるフローの概要](./media/apply-to-each/foreach-flow-finished.png)

## <a name="run-the-flow"></a>フローを実行する
1. 件名に **meet now** が含まれる高重要度のメールを自分宛てに送信します (または、組織内のだれかにそのようなメールを送信してもらいます)。
2. メールが受信トレイにあり、未開封であることを確認します。
3. Microsoft Flow にサインインし、**[マイ フロー]** を選んで、**[今すぐ実行]** を選びます。
   
    ![今すぐ実行](./media/apply-to-each/foreach-run-1.png)
4. **[フローの実行]** を選び、フローを本当に実行することを確認します。
   
    ![実行の確認](./media/apply-to-each/foreach-run-2.png)
5. しばらくしてから、正常な実行の結果が表示されます。
   
    ![実行結果](./media/apply-to-each/foreach-run-3.png)

## <a name="view-results-of-the-run"></a>実行の結果を表示する
フローが正常に実行されたので、モバイル デバイスにプッシュ通知が送られてきているはずです。

1. モバイル デバイスで Microsoft Flow アプリを開き、**[アクティビティ]** タブを選びます。会議に関するプッシュ通知が表示されます。
   
    ![[アクティビティ] タブの選択](./media/apply-to-each/foreach-notification-1.png)
2. 通知の完全な内容を表示するには、通知を選択しなければならない場合があります。 完全な通知は次のような内容です。
   
    ![通知の詳細](./media/apply-to-each/foreach-notification-2.png)
   
   > [!NOTE]
   > プッシュ通知が届かない場合は、モバイル デバイスのデータ接続が動作していることを確認します。
   > 
   > 

