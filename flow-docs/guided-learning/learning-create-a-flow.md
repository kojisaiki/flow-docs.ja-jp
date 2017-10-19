---
title: "テンプレートからフローを作成する | Microsoft Docs"
description: "テンプレートを基にしてフローを作成して管理する方法を説明します。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: D46qE7FuShM
courseduration: 9m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/15/2017
ms.author: deonhe
ms.openlocfilehash: a6ef80f4d20b88ef3b3a5193048209f924c9860a
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="create-a-flow-from-a-template"></a>テンプレートからフローを作成する
Microsoft Flow のガイド付き学習にようこそ。 このレッスンでは、Microsoft Flow の環境についてさらに説明し、**最初のフローを構築**できるようにします。

Microsoft Flow は簡単に使い始めることができます。多数の**テンプレートから選択**して、既に使っているサービスにいっそう有意義な方法で接続できます。  

## <a name="microsoft-flow-templates"></a>Microsoft Flow のテンプレート
[Microsoft Flow の Web サイト](https://ms.flow.microsoft.com)で、**[テンプレート]** メニューを開いてみてください。 一覧をスクロールすると、Microsoft Flow で多くのサービスに接続できることがわかります。

![Flow Web サイト -> テンプレート一覧](./media/learning-create-a-flow/template-list.png)

## <a name="choose-a-template"></a>テンプレートの選択
メールで**添付ファイルを探す**のは時間のかかる作業ですが、このフローを使って OneDrive のフォルダーに**メールのすべての添付ファイルを格納する**と、時間を節約できます。

"**Office 365 のメールの添付ファイルを OneDrive for Business に保存する**" テンプレートを選びます。

![Office 365 のメール](./media/learning-create-a-flow/office-365-email.png)

## <a name="create-and-administer-a-flow"></a>フローを作成して管理する
これは**ワン クリック** テンプレートの 1 つであり、**フローの構築に必要な**関連する質問に答えるだけです。

テンプレートのグラフィックには、成功するためにテンプレートが**行うことと、必要とすること**についての**説明**があります。

**Office 365 Outlook** サービスと **SharePoint** サービスの**資格情報の入力**を求められます。 両方のサービスを定期的に使っている場合は、既にサインインされています。

![Office 365 のメールを保存する](./media/learning-create-a-flow/save-flow-office-description.png)

1. **[フローの作成]** を選びます。
   
    ![[フローの作成] をクリックする](./media/learning-create-a-flow/click-create-flow.png)
   
    結果が表示されます。 
   
    ![作成成功](./media/learning-create-a-flow/create-successful.png)
   
    フローによって OneDrive に**フォルダーが作成**され、仕事用メール アドレスにメールで送られてきた**すべての添付ファイル**がここに自動的に格納されます。
2. **[マイ フロー]** を開きます。
   
    ![[マイ フロー] を開く](./media/learning-create-a-flow/click-my-flows.png)
3. **作成したフロー**を選び、動作を確認します。
   
    ![フローを選ぶ](./media/learning-create-a-flow/click-the-flow.png)
4. **緑のチェック マーク**が表示されます。これは、**フローが成功した**ことを示します。 **[成功]** を選び、実行履歴と結果を確認します。
   
    ![フローの成功](./media/learning-create-a-flow/flow-successful.png)
   
    **フローのすべての部分**が正常に実行されました。 
   
    ![実行履歴](./media/learning-create-a-flow/run-history.png)

## <a name="important-concepts-in-microsoft-flow"></a>Microsoft Flow における重要な概念
フローを構築するときに知っておく必要のあることがいくつかあります。 すべてのフローには 2 つの主要部分があります。**トリガー**と、**1 つまたは複数のアクション**です。 

**トリガー**は、フローの開始アクションと考えることができます。この例での**新しいメールを受信したとき**や、SharePoint を使っている場合の**新しい項目が追加されたとき**などです。 **繰り返し**トリガーを使うと、固定スケジュールにすることもできます。繰り返しについては後で説明します。

**トリガーが呼び出された**ときに実行する**アクティビティがアクション**です。 たとえば、**ファイルの作成**は OneDrive にファイルを再作成します。

![新しいメールでのアクション](./media/learning-create-a-flow/trigger-or-action.png)

その他にも、**メール**の送信、**ツイート**の投稿、**承認**の開始など、多くのアクションがあります。
これらはすべて、後で一から独自のフローを作成すると、動作するようになります。 

## <a name="next-lesson"></a>次のレッスン
次のレッスンでは、Microsoft Flow モバイル アプリとその機能について説明します。 

