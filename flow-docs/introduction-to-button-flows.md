---
title: ボタン フローで反復タスクを自動化および実行する方法 | Microsoft Docs
description: ボタン フローの概要を説明します。
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
ms.date: 01/30/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: cbcbce51bb950ef9154f356ce44a651f25ce55bd
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690085"
---
# <a name="introducing-button-flows"></a>ボタン フローの概要
## <a name="what-are-button-flows"></a>ボタン フローとは
ボタンを 1 回押すだけで実行したい反復作業は多く存在します。 たとえば、毎日のチーム同期への参加を促すメールを簡単に送信できれば便利です。あるいは、その日に予定されているチェックインがこれ以上ないという通知を受け取った後で、ご自分のコード ベースの新しい Visual Studio Online ビルドを開始できるかもしれません。 ボタン フローを利用すれば、モバイル デバイスのボタンをタップするだけでこのような作業を遂行できます。

**注** ボタン フローは、モバイル デバイスまたは Flow ポータルから作成できます。  
  ![概要画像](./media/introduction-to-button-flows/buttons-montage.png)  

## <a name="why-create-buttons"></a>ボタンを作成する理由
場所や時間に関係なく、モバイル デバイスから繰り返し作業を簡単に実行できるようにボタンを作成します。 ボタンの実行は時間を節約します。また、実行する作業が自動化されるため、手動で行うよりエラーが少なくなります。  

## <a name="create-a-button"></a>ボタンを作成する
### <a name="prerequisites"></a>前提条件
* Flow へのアクセス。 アクセスは管理者より提供されます。
* コネクタを利用してボタンを作成するためのアクセス許可があるアカウント。 たとえば、Dropbox にアクセスするボタンを作成するには、Dropbox アカウントが必要になります。

### <a name="from-the-portal"></a>ポータルから
このチュートリアルでは、Visual Studio Online (VSO) ビルドを開始し、そのビルドの開始を知らせる通知を送信するボタンを作成しましょう。  

1. **[表示]** ドロップダウン リストを選択し、**[ボタン]** カテゴリを選択します。 テンプレートの一覧がフィルター処理され、ボタン フローで使用できるものに絞り込まれます。  
   ![概要画像](./media/introduction-to-button-flows/create-button-1.png)   
2. テンプレートの一覧から **[Trigger a new build in VSO]** (VSO で新しいビルドをトリガーする) テンプレートを選択します。  
   ![概要画像](./media/introduction-to-button-flows/create-button-2.png)  
3. **[Trigger a new build in VSO]** (VSO で新しいビルドをトリガーする) ページで **[このテンプレートを使用]** ボタンを選択します。   
   ![概要画像](./media/introduction-to-button-flows/create-button-3.png)  
4. サインインしていない場合、この時点でサインインするように求められます。  
   ![概要画像](./media/introduction-to-button-flows/create-button-4.png)  
5. Flow にサインインすると、選択したテンプレートで使用されるコネクタにサインインするように求められます。 この例では、上の手順 2 で、**[Trigger a new build in VSO]** (VSO で新しいビルドをトリガーする) テンプレートを選択しました。そのため、まだサインインしていない場合、VSO (と使用しているその他のコネクタ) にサインインする必要があります。  
   ![概要画像](./media/introduction-to-button-flows/create-button-pre-req-1.png)    
6. VSO アカウントへのアクセス許可を Flow に与えることに同意する場合、**[承諾]** ボタンを選択します。  
   ![概要画像](./media/introduction-to-button-flows/create-button-5.png)   
   **注** 各コネクタを同様に承認する必要があります。 次の手順に進む準備ができると、このようなデザイナーが表示されるはずです。 **[続行]** ボタンを選択して先に進みます。  
   ![概要画像](./media/introduction-to-button-flows/create-button-6.png)   
7. これで、開始するビルドのプロパティを構成する準備ができました。    
   ![概要画像](./media/introduction-to-button-flows/create-button-7.png)  
8. **[新しいビルドをキューに入れる]** カードで **[アカウント名]**、**[プロジェクト名]**、**[ビルド定義 ID]**、**[ソース ブランチ]** を選択するか、入力し、任意で **[パラメーター]** を選択するか、入力します。    
   ![概要画像](./media/introduction-to-button-flows/create-button-8.png)  
9. 次に、**[Send a push notification]** (プッシュ通知を送信する) カードでプッシュ通知のプロパティを構成します。 既定では、このプッシュ通知は、ビルドの状態を表示する Web ページに HTML リンクを送信するように構成されています。  
   ![概要画像](./media/introduction-to-button-flows/create-button-9.png)  
10. **[フローの作成]** ボタンを選択し、ボタン フローを保存します: ![概要画像](./media/introduction-to-button-flows/create-button-10.png)  
11. しばらくすると、この成功メッセージが表示されるはずです。  
    ![概要画像](./media/introduction-to-button-flows/create-button-11.png)  

おめでとうございます。ボタン フローが作成されました。 これで Flow アプリの **[ボタン]** タブから、時と場所に関係なく、このボタン フローを実行できます。 "ボタン" を押すだけで実行されます。 Microsoft Flow モバイル アプリは、[Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) で使用できます。

### <a name="from-your-mobile-device"></a>モバイル デバイスから
**注**: このチュートリアルでは Android デバイスの画面を利用しますが、iOS でも同じような画面や動作になります。

Flow アプリで次の操作を行います。

1. **[参照]** タブを選び、**[ボタン]** カテゴリにスクロールします。  
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-1.png)  
2. **[すべて表示]** リンクを選択します。 すぐに使えるボタンのテンプレートがすべて表示されます。     
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-2.png)  
3. **[Send an email to remind your team to join a meeting]** (会議出席のリマインダー メールをチームに送信する) テンプレートを選択します。    
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-3.png)  
4. ページの一番下にある **[このテンプレートを使用]** リンクを選択します。    
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-4.png)  
5. このテンプレートが使用するすべてのサービスにサインインする必要があります。    
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-5.png)  
6. すべてのサービスにサインインしたら、**[次へ]** リンクを選択します。      
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-6.png)  
7. **[作成]** リンクを選択します。 ここで、たとえば、フローを確認したり、必要な変更を行い、自分だけの電子メールを作成したりできます。        
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-7.png)  
8. しばらくすると、ボタン フローが作成されます。 **[SEE MY FLOW]** (自分のフローを見る) を選択します:   
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-8.png)  
9. **[My flows]** (マイ フロー) タブ上ですべてのフローを表示できます  
   ![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-9.png)  

おめでとうございます。ボタン フローが作成されました。 これで Flow アプリの **[ボタン]** タブから、時と場所に関係なく、このボタン フローを実行できます。 "ボタン" を押すだけで実行されます。 現在のところ、Flow アプリは Android と iOS のモバイル デバイスで利用できます。  

![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-10.png)  

## <a name="trigger-a-button-flow"></a>ボタン フローをトリガーする
ボタン フローが作成できたので、次は実行しましょう。 ボタン フローは Flow アプリからのみ実行できます。Android または iOS のモバイル デバイスに Flow がインストールされていることを確認してください。  

1. フロー アプリを起動し、ページの一番下にある **[ボタン]** タブをタップし、トリガーするボタン フローを表す *[ボタン]* をタップします。  
   ![概要画像](./media/introduction-to-button-flows/trigger-button-1.png)   
2. フローの実行中に進捗状況を確認します:  
   ![概要画像](./media/introduction-to-button-flows/trigger-button-2.png)   
3. 最後に、ページが更新され、ボタン フローの完了を示します。  
   ![概要画像](./media/introduction-to-button-flows/trigger-button-3.png)   

フローの実行はこれで終わりです。 

電子メールが送信されたことを示すプッシュ通知を受け取るはずです。  

## <a name="monitor-your-button-flow-runs"></a>ボタン フローの実行を監視する
フロー アプリの **[アクティビティ]** タブからボタン フローを監視できます。   
![概要画像](./media/introduction-to-button-flows/create-button-from-mobile-13.png)  

**注**: 任意のアクティビティをタップして実行結果を表示し、実行に関する情報を入手します。  

![概要画像](./media/introduction-to-button-flows/activity-details-1.png)  

## <a name="manage-button-flows"></a>ボタン フローを管理する
ボタンは完全に制御できます。時と場所に関係なく、ボタンを有効/無効にしたり、編集したり、削除したりできます。 モバイル アプリまたはフロー ポータルから、**[My flows]** (マイ フロー) を選択し、フローの管理を開始します。    

Flow アプリの **[My flows]** (マイ フロー) タブで:

1. 管理するフローを選択します。    
   ![概要画像](./media/introduction-to-button-flows/trigger-button-4.png)   
2. 実行する操作に基づき、いずれかのオプションをタップできます。    
   ![概要画像](./media/introduction-to-button-flows/manage-flow-1.png)  
3. **[フローの削除]** をタップすると、フローが削除されます。  

**注** フローを削除すると、すべての実行履歴が削除されます。   
![概要画像](./media/introduction-to-button-flows/manage-flow-2.png)   

1. ボタン フローの編集が完了したら **[更新]** をタップし、変更を保存します。   
   ![概要画像](./media/introduction-to-button-flows/manage-flow-3.png)   
2. **[実行履歴]** をタップすると、特定のボタン フローの全実行結果が表示されます。    
   ![概要画像](./media/introduction-to-button-flows/manage-flow-4.png)  
3. フローを無効にすると、**[ボタン]** タブで利用できなくなります。    
   ![概要画像](./media/introduction-to-button-flows/manage-flow-5.png)  

## <a name="next-steps"></a>次のステップ
* [ボタン フローを共有する](share-buttons.md)
* ボタン フローの実行時に[ボタン トリガー トークン](introduction-to-button-trigger-tokens.md)を使用してリアルタイムのデータを送信する方法について理解する
* [Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリをインストールします。

