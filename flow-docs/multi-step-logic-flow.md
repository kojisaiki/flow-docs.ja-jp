---
title: 詳細オプションと複数のアクションの追加 | Microsoft Docs
description: フローを拡張して、詳細オプションを追加し (たとえば、電子メールの優先度を高く設定し)、同じイベントに対して他のアクションを追加します。
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/20/2017
ms.author: stepsic
ms.openlocfilehash: f6c936cbf5a2bd481adb52ec9b01545fb9ba7b0b
ms.sourcegitcommit: f0202f74ba9a2282a670a1751462f598a5ea0ce5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="add-multiple-actions-and-advanced-options-to-a-flow"></a>フローへの複数のアクションと詳細オプションの追加
同じトリガーに対して 1 つ以上の詳細オプションと複数のアクションを追加して、フローをカスタマイズします。 たとえば、電子メール メッセージを高い優先度で送信する詳細オプションを追加します。 SharePoint リストに項目が追加されたときに電子メールを送信するほか、同じ情報を含むファイルを Dropbox に作成します。

## <a name="prerequisites"></a>前提条件
* [フローを作成する](get-started-logic-flow.md)

## <a name="add-another-action"></a>他のアクションの追加
この手順では、フローの途中にアクションを追加します。 このアクションでは、ファイルを Dropbox に保存し、アイテムをリストにアーカイブします。

1. [flow.microsoft.com](https://flow.microsoft.com) で、上部のナビゲーション バーの **[自分のフロー]** を選択します。
2. フローの一覧で、編集するフローを選択します。
3. **[新しいステップ]** を選択し、**[アクションの追加]** を選択します。
   
    ![折りたたまれている追加](./media/multi-step-logic-flow/add-action.png)
4. 使用できるアクションの一覧で "**ファイルの作成**" を検索し、**[Dropbox - ファイルの作成]** を選択します。
   
    ![ファイルの作成を検索する](./media/multi-step-logic-flow/create-file-search.png)
5. メッセージが表示されたら、Dropbox の資格情報を指定します。
6. **[フォルダーのパス]** ボックスの右側にあるフォルダー アイコンを選択します。
7. 検索して、新しいファイルを配置するフォルダーを選択します。
   
    ![ファイルの作成を検索する](./media/multi-step-logic-flow/create-file-folder.png)
8. 新しいファイルの名前を **[ファイル名]** ボックスに入力します。 ファイル名に ".txt" などの拡張機能を追加するようにしてください。 ここでは、ファイルの一意性を確保するためにファイルの名前に **TweetId** を使用します。 **TweetId** トークンを探すには、**[もっと見る]** を選択する必要がある場合があります。
9. **[ファイルのコンテンツ]** ボックスに入力して、ファイルに含めるテキストを追加します。 また、**[ファイルのコンテンツ]** ボックスにトークンを追加することもできます。
   
    ![ファイル名とコンテンツ](./media/multi-step-logic-flow/create-file-name-and-contents.png)
   
   > [!IMPORTANT]
   > ファイルに既存のファイル名 (選択したフォルダー内) に一致する名前を付けた場合、既存のファイルは上書きされます。
   > 
   > 
10. 画面の上部にあるメニューで **[フローの更新]** を選択します。
11. 指定したキーワードを含むツイートを送信します。
    
     ファイルが 1 分以内に Dropbox アカウントに作成されます。

## <a name="reorder-or-delete-an-action"></a>アクションの並べ替えまたは削除
* Dropbox にファイルが作成された後に電子メールを受信するには、電子メール アクションの上にあるタイトル バーをドラッグして、Dropbox アクションを移動します。 トリガー (**新しいツイートの投稿時**) と電子メール アクションの間の矢印の上で、Dropbox アクションを放します。 (カーソルはアクションが正しく配置されているかどうかを示します。)
  
  > [!NOTE]
  > ステップの出力を使用している場合、そのステップの前に、別のステップを移動することはできません。
  > 
  > 
  
    ![メニューの削除](./media/multi-step-logic-flow/draggingaction.png)
* アクションを削除するには、削除するアクションのタイトル バーの右端にある省略記号 ([...]) を選択し、**[削除]**、**[OK]** の順に選択します。
  
    ![メニューの削除](./media/multi-step-logic-flow/deletemenu.png)
  
     **注:** フローの任意の場所からアクションの出力を使用している場合、そのアクションは削除できません。 先にフィールドからその出力を削除すると、アクションを削除できます。

## <a name="add-advanced-options"></a>詳細オプションの追加
**[電子メールの送信]** アクションが含まれるフローを開始します。

1. **[電子メールの送信]** カードの下部にある **[詳細オプションの表示]** を選択します。
   
     電子メールの送信に使用する詳細オプションが表示されます。
   
    ![SharePoint のトリガー](./media/multi-step-logic-flow/advanced.png)
2. 詳細オプションを非表示にするには、**[重要度]** の一覧で **[高]** を選択して、**[詳細オプションを表示しない]** を選択します。
3. 画面の上部にあるメニューで **[フローの更新]** を選択します。
   
     このステップでは変更が保存されます。

