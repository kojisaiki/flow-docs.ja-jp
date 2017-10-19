---
title: "Microsoft Flow での承認依頼 | Microsoft Docs"
description: "Microsoft Flow を使用して承認ワークフローを管理する方法について説明します。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: o-pgEBW3fOI
courseduration: 14m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 049b713ed653ab5555e5f48f63e46cce7f3207ee
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="approval-requests"></a>承認依頼
**通知の受け取り**、**ファイルのコピー**、**データの収集**を支援するだけでなく、Microsoft Flow は**承認プロセスの合理化**にも役立ちます。

## <a name="vacation-scenario"></a>休暇のシナリオ
チームの**マネージャー**がメンバーに **SharePoint リスト**で**休暇申請**を作成するように求めるものとします。 このリスト アイテムに関する**承認プロセス**を作成し、新しい休暇申請が**迅速に処理**されて、申請者に**自動的に通知**されるようにします。  

## <a name="sharepoint-and-microsoft-flow"></a>SharePoint と Microsoft Flow
**SharePoint** には Microsoft Flow の**組み込み機能**があります。  **SharePoint リスト**から、**[フロー]** ドロップダウンをクリックして、**[Create a flow]** (フローの作成) をクリックします。

![フローの作成](./media/learning-approvals/new-flow.png)   

**右側のメニュー**で、次のような**テンプレート**を探します。

![承認テンプレート](./media/learning-approvals/approval-template.png)

## <a name="using-the-template"></a>テンプレートの使用
テンプレートの **SharePoint** トリガーには、リストの情報が**事前に設定**されています。  ユーザーが行う必要があるのは、**承認者**の**メール アドレス**を追加することだけです。  **元の SharePoint アイテムは変更されない**ことに注意してください。  そのため、**SharePoint - アイテムの更新**アクションを追加する必要があります。

![アイテムの更新](./media/learning-approvals/update-item.png)

*Send emailScope* に分岐**しない場合**はどうすればよいでしょう。  既定では、何も行われません。  この場合は、たとえば申請が却下されたことを伝えるメッセージを申請者に送信するアクションを追加します。 

![分岐しない場合](./media/learning-approvals/if-no.png)

## <a name="next-lesson"></a>次のレッスン
このセクションで学習した内容を確認します。

