---
title: "フローへの条件の追加 | Microsoft Docs"
description: "特定の条件が true の場合にのみフローが 1 つ以上のタスクを実行することを指定します。"
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/22/2016
ms.author: stepsic
ms.openlocfilehash: 1291b32f001be211acddbf1c83f3b1bdf03f2ac3
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="add-a-condition-to-a-flow"></a>フローへの条件の追加
特定の条件が true の場合にのみフローが 1 つ以上のタスクを実行することを指定します。 たとえば、キーワードを含むツイートが 10 回以上リツイートされた場合のみ電子メールを受け取るように指定します。

**前提条件**

* テンプレートから[フローを作成する](get-started-logic-template.md) - このチュートリアルでは、例として[こちらのテンプレートを使用](https://flow.microsoft.com/galleries/public/templates/e78571e5c70e4806a18eeacba5a897c8/)します。

## <a name="add-a-condition"></a>条件の追加
1. [flow.microsoft.com](https://flow.microsoft.com) で、上部のナビゲーション バーの **[自分のフロー]** を選択します。
2. フローの一覧で、作成したフローを選択します。 このチュートリアルでは、Twitter トリガーと SharePoint アクションを使用した例を取り上げます。
3. 最後のアクションの下部にある **[新しいステップ]** ボタンをクリックします。
4. **[条件の追加]** を選択します。
   
    ![条件ボタン](./media/add-a-condition/add-condition.png)
5. **[オブジェクト名]** の空の領域を選択し、**[動的なコンテンツの追加]** を選択して、動的なコンテンツのメニューを開きます。
6. **[Retweet count (リツイート数)]** を選択してボックスに追加します。
7. **[リレーションシップ]** ボックスで、**[次の値以上]** を選択します。
8. **[値]** ボックスに、「**10**」と入力します。
   
    ![パラメーターが設定されている [オブジェクト名] ボックス](./media/add-a-condition/specify-condition.png)
9. 条件内で必要なアクションのヘッダーをクリックし (**[Create item (アイテムの作成)]** など)、**[はいの場合]** というテキストの下にドラッグします。 カーソルを放すと、アクションはそのボックスに移動します。
   
    ![アクションをドラッグ](./media/add-a-condition/drag-action.png)
10. フローを保存します。

## <a name="edit-in-advanced-mode"></a>詳細設定モードでの編集
**[詳細設定モードで編集]** リンクを選択して、さらに詳細な条件を記述することもできます。 こちらの "*ワークフロー定義言語*" の表現をすべて使用することができます。 利用可能な関数の詳細については、[こちら](https://msdn.microsoft.com/library/azure/mt643789.aspx)を参照してください。

