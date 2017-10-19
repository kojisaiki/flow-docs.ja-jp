---
title: "フロー実行の確認 | Microsoft Docs"
description: "フローの各ステップの入出力を終了前に表示して、そのステップが期待どおりに動作することを確認します。"
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
ms.date: 04/25/2016
ms.author: mhade
ms.openlocfilehash: 0aa39555a9e36db13ce9cb0abc400b71149a89b1
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="watch-your-flows-in-action"></a>実行中のフローの確認
<iframe width="560" height="315" src="https://www.youtube.com/embed/3wPoUCGm7Yg" frameborder="0" allowfullscreen></iframe>

フローが期待どおりに実行されることを確認するには、開始アクションを実行し、フローの各ステップによって生成された入出力を確認します。

1. フローを作成または更新します。ただし、**[Create flow (フローの作成)]** または **[Update flow (フローの更新)]** を選択した後、デザイナーは開いたままにします。
   
     たとえば、**#azure** ハッシュタグが付いたツイートが投稿されるたびに電子メールを送信する[フローを作成](get-started-logic-flow.md)します。
2. フローの開始アクションを実行します。
   
    たとえば、**#azure** ハッシュタグが含まれるツイートを送信します。
   
    開始アクションと以降の各ステップには、実行が成功したかどうかと、その所要時間が示されます。
   
    ![実行成功のイメージ](./media/see-a-flow-run/successful-flow-run.png)
3. 個別のトリガーまたはアクションを選択して、その入出力を表示します。
   
    ![カードが展開された実行成功のイメージ](./media/see-a-flow-run/successful-flow-expanded-cards.png)
4. **[Edit flow (フローの編集)]** を選択して変更します。フローが期待どおりに動作している場合は、**[Done (完了)]** を選択します。

