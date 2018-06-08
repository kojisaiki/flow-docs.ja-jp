---
title: テンプレートからフローを作成する | Microsoft Docs
description: 複数の組み込みテンプレートのいずれかを使ってフローを作成します。
services: ''
suite: flow
documentationcenter: na
author: aftowen
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/07/2017
ms.author: anneta
ms.openlocfilehash: b755d9abe70740a97ad85aaa60b8a3f4685a7b26
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "31008382"
---
# <a name="create-a-flow-from-a-template-in-microsoft-flow"></a>Microsoft Flow でテンプレートからフローを作成する
多くの組み込みテンプレートのいずれかからフローを作成します。組み込みテンプレートでは、たとえば、Office 365 で上司からのメールを受け取ったときに Slack メッセージが送信されるようにすることができます。

**注:** プロセスを既に計画していて、そのプロセスに適したテンプレートが見つからない場合は、[ゼロからフローを作成](get-started-logic-flow.md)してください。

**前提条件**

* [flow.microsoft.com](https://flow.microsoft.com) のアカウント
* Slack アカウント
* Office 365 の資格情報

## <a name="choose-a-template"></a>テンプレートの選択
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZJK8cYdjAic?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

1. [flow.microsoft.com](https://flow.microsoft.com) で、上部のナビゲーション バーの **[テンプレート]** を選択します。
2. 検索バーに「**Slack**」と入力し、検索アイコンを選択します。
3. Slack に関連するテンプレートのみが表示されるので、**[上司からの電子メールを受信したときに Slack でメッセージを送信する]** を選択できます。
   
    ![左側のナビゲーション バーの新しいオプション](./media/get-started-logic-template/select-template.png)
4. このテンプレートが目的にかなっていることを確認し、**[このテンプレートを使用]** を選択します。
5. Office または Slack にサインインしていない場合は、**[サインイン]** を選択し、画面の指示に従います。
   
    ![テンプレートに必要な接続の一覧](./media/get-started-logic-template/confirm-connections.png)
6. 接続を確認した後、**[Continue (続行)]** を選択します。
   
    フローが表示され、各アクションがオレンジ色のタイトル バーで示されます。
   
    ![テンプレートの既定のイベントとアクション](./media/get-started-logic-template/template-default.png)

## <a name="customize-your-flow"></a>フローのカスタマイズ
1. イベントのタイトル バーを選択して展開し、カスタマイズします (たとえば、必要な電子メールにフィルターを指定します)。
2. 入力を必要とするアクションが自動的に展開されます。
   
    たとえば、**[Post message]\(メッセージの投稿\)** アクションは、*\@username* などのチャネルを入力する必要があるため展開されます。 メッセージの内容をカスタマイズすることもできます。 既定で、メッセージには件名のみが含まれていますが、その他の情報を含めることもできます。
   
    ![Slack のチャネルの指定](./media/get-started-logic-template/specify-keyword.png)
3. 画面上部でフローの名前を指定して、**[フローの作成]** を選択します。
4. 最後に、フローが完成したら、**[完了]** を選択します。
   
    ![[完了] ボタン](./media/get-started-logic-template/done.png)

これで、上司からの電子メールを受信したときに、指定した情報を含む Slack メッセージを受信します。

## <a name="next-steps"></a>次のステップ
* [実行中のフローを確認する](see-a-flow-run.md)
* [独自のテンプレートを発行する](publish-a-template.md)
* [Common Data Service のテンプレートを使用する](common-data-model-intro.md)
* [チーム フローを作成](create-team-flows.md)し、他のユーザーを招待して共同でフローを設計します。

