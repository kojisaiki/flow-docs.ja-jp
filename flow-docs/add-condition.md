---
title: "フローへの条件の追加 | Microsoft Docs"
description: "条件が true の場合にのみフローが 1 つ以上のタスクを実行することを指定します。"
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
ms.date: 10/17/2017
ms.author: stepsic
ms.openlocfilehash: 135b3509a9412f7674a1e9cb2ada86ebd2bb9f4f
ms.sourcegitcommit: 122870842a07183ab3b90e07d99b60d822d6c5ae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="add-a-condition-to-a-flow"></a>フローへの条件の追加

条件が true の場合にのみフローが 1 つ以上のタスクを実行することを指定します。 たとえば、キーワードを含むツイートが 10 回以上リツイートされた場合のみ電子メールを受け取るように指定します。

## <a name="prerequisites"></a>前提条件

* テンプレートから[フローを作成する](get-started-logic-template.md) - このチュートリアルでは、例として[こちらのテンプレートを使用](https://flow.microsoft.com/galleries/public/templates/e78571e5c70e4806a18eeacba5a897c8/)します

## <a name="add-a-condition"></a>条件の追加

1. [Microsoft Flow](https://flow.microsoft.com) で、上部のナビゲーション バーの **[自分のフロー]** を選択します。

    まだサインインしていない場合は、サインインしなければならない場合があります。

1. フローの一覧で、作成したフローのいずれかを選択します。

    このチュートリアルでは、Twitter トリガーと SharePoint アクションを使用した例を取り上げます。

1. **[フローの編集]** を選択します。

1. 最後のアクションの下部にある **[新しいステップ]** をクリックします。

1. **[条件の追加]** を選択します。

    ![条件ボタン](./media/add-condition/add-condition.png)

1. **[条件]** カードの左側のボックスで空の領域を選択します。

    **[動的なコンテンツ]** 一覧が表示されます。

1. **[Retweet count (リツイート数)]** を選択してボックスに追加します。

1. **[条件]** カードの真ん中のボックスで、**[次の値以上]** を選択します。

1. 右側のボックスに「**10**」を入力します。

    ![パラメーターが設定されている [オブジェクト名] ボックス](./media/add-condition/specify-condition.png)

1. 条件で使用するアクションのヘッダーを選択し (**[項目の作成]** など)、**[はいの場合]** というテキストの下にドラッグします。

    カーソルを放すと、アクションはそのボックスに移動します。

    ![アクションをドラッグ](./media/add-condition/drag-action.png)

1. 必要に応じてアクションを構成します。

1. フローを保存します。

## <a name="edit-in-advanced-mode"></a>詳細設定モードでの編集

**[詳細設定モードで編集]** を選択して、さらに詳細な条件を記述することもできます。 *ワークフロー定義言語*のすべての式を詳細設定モードで使用することができます。 使用可能なすべての式は[こちら](https://msdn.microsoft.com/library/azure/mt643789.aspx)をご覧ください。

## <a name="next-steps"></a>次のステップ

詳細設定モードで条件に[式を使用する](use-expressions-in-conditions.md)方法について説明します。
