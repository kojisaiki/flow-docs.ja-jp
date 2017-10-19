---
title: "最新のパラレル承認ワークフローを作成する | Microsoft Docs"
description: "最新のパラレル承認ワークフローを作成する"
services: 
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/24/2017
ms.author: deonhe
ms.openlocfilehash: b4d11da19db97ce94df3e3d5237f6c90b3514269
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="create-parallel-approval-workflows-with-microsoft-flow"></a>Microsoft Flow を使用して最新のパラレル承認ワークフローを作成する
パラレル承認ワークフローでは、請求書、発注書、休暇申請などの項目を複数のユーザーが承認する必要があります。各ユーザーの承認は、他のすべての承認者から独立しています。

このチュートリアルでは、Microsoft Flow を使用してパラレル承認ワークフローを自動化するフローを作成します。 このフローにより、従業員の休暇申請プロセス (その従業員が日常的にサポートするすべてのユーザーまたはチームからの承認を求める) が自動化されます。 従業員は [SharePoint リスト](https://support.office.com/article/Introduction-to-lists-0a1c3ace-def0-44af-b225-cfa8d92c52d7)を使用して休暇を申請します。 休暇の承認は、従業員の直属のマネージャー、販売チーム、および人事チームから得る必要があります。 各休暇申請は、決定を行う各承認者に転送されます。 このフローでは、状態の変化を示す電子メールが送信され、決定情報によって SharePoint が更新されます。

## <a name="prerequisites"></a>前提条件
[!INCLUDE [prerequisites-for-modern-approvals](includes/prerequisites-for-modern-approvals.md)]

作成する SharePoint Online リストには、次の列を含める必要があります。

   ![SharePoint リストの列](./media/parallel-modern-approvals/sharepoint-columns.png)

SharePoint Online リストの名前と URL をメモします。 これらの項目は、後で **[SharePoint - 新しい項目が作成されたとき]** トリガーを構成するために使用します。

## <a name="create-your-flow-from-the-blank-template"></a>空白のテンプレートからフローを作成する
[!INCLUDE [sign-in-and-create-flow-from-blank-template](includes/sign-in-and-create-flow-from-blank-template.md)]

## <a name="add-a-trigger"></a>トリガーの追加
[!INCLUDE [add-trigger-when-sharepoint-item-created](includes/add-trigger-when-sharepoint-item-created.md)]

   ![SharePoint 情報](includes/media/parallel-modern-approvals/select-sharepoint-site-info.png)

## <a name="get-the-manager-for-the-person-who-created-the-vacation-request"></a>休暇申請を作成した従業員のマネージャーを取得する
[!INCLUDE [add-get-manager-action](includes/add-get-manager-action.md)]

## <a name="name-and-save-your-flow"></a>フローに名前を付けて保存する
1. フローの名前を指定し、**[フローの作成]** を選択してこれまでに行った作業を保存します。
   
   ![フローの保存](./media/parallel-modern-approvals/save.png)

> [!NOTE]
> 定期的に画面上部の **[フローの更新]** を選択して変更をフローに保存します。
> 
> 

   ![更新アクションを選択する](./media/parallel-modern-approvals/update.png)

フローの保存や更新後に変更を続行するには、画面上部から **[フローの編集]** を選択してから変更を続行します。

## <a name="add-an-approval-action-for-immediate-manager"></a>直属のマネージャー用の承認アクションを追加する
[!INCLUDE [add-an-approval-action](includes/add-an-approval-action.md)]

> [!IMPORTANT]
> このアクションを実行すると、**[割り当て先ユーザー/グループ]** ボックス内の電子メール アドレスに休暇申請が送信されるため、**[Get manager] (マネージャー取得)** 一覧から取得した **[Email] (電子メール)** トークンを挿入してください。
> 
> 

## <a name="insert-a-parallel-branch-approval-action-for-the-sales-team"></a>販売チーム用のパラレル分岐承認アクションを挿入する
1. **[Get manager] (マネージャー取得)** カードと **[Start an approval] (承認を開始)** カードの間にある下向き矢印を選択します。
2. 下向き矢印を選択した後に表示されるプラス記号を選択します。
3. **[Add a parallel branch] (パラレル分岐の追加)** を選択します。
4. **[アクションの追加]** を選択します。
   
    ![マネージャーの構成を取得する](./media/parallel-modern-approvals/add-parallel-branch.png)
5. 休暇申請を販売チームに送信する **[Start an approval] (承認を開始)** アクションを検索して選択し、構成します。 **[Start an approval] (承認を開始)** アクションを追加する方法がわからない場合は、[直属のマネージャー用の承認アクションを追加するために使用したステップ](parallel-modern-approvals.md#add-an-approval-action-for-immediate-manager)を参照してください。

> [!IMPORTANT]
> **[Start an approval] (承認を開始)** アクションの **[割り当て先ユーザー/グループ]** ボックスにある販売チームの電子メール アドレスを使用します。
> 
> 

## <a name="insert-a-parallel-branch-approval-action-for-the-human-resources-team"></a>人事チーム用のパラレル分岐承認アクションを挿入する
1. [営業チーム用のパラレル分岐を追加する](parallel-modern-approvals.md#insert-a-parallel-branch-approval-action-for-the-sales-team)手順を繰り返して、休暇申請を人事に送信する **[Start an approval] (承認を開始)** アクションを追加して構成します。

> [!IMPORTANT]
> **[Start an approval] (承認を開始)** アクションの **[割り当て先ユーザー/グループ]** ボックスにある人事チームの電子メール アドレスを使用します。
> 
> 

これまでのステップに従った場合、フローは次の例のようになります。

   ![パラレル分岐が含まれるフロー](./media/parallel-modern-approvals/flow-with-parallel-branches.png)

## <a name="options-after-adding-parallel-branches"></a>パラレル分岐を追加した後のオプション
パラレル分岐にアクションを追加した後は、次の 2 種類の方法でフローにステップをさらに追加できます。

* 小さい **[Insert a new step] (新しいステップの挿入)** ボタン (分岐の空白部分、または分岐のすぐ下の領域を選択したときに表示される丸付きの + ボタン) を使用します。 このボタンを選択すると、その**特定の分岐**にステップが追加されます。 このボタンによって追加したステップは、この特定の分岐が完了した後で実行されます。
* ワークフロー全体の下部にある大きい **[新しいステップ]** ボタンを使用します。 このボタンを選択すると、**すべての分岐**が完了した後で実行されるアクションが追加されます。 このボタンによって追加したステップは、すべての分岐が完了した後に実行されます。

以下のセクションでは、小さい **[Insert a new step] (新しいステップの挿入)** を使用して、各分岐で次のステップを実行します。

* 休暇申請が承認されたか拒否されたかをチェックする条件を追加します。
* 決定を従業員に通知する電子メールを送信します。
* SharePoint 内の休暇申請を承認の決定情報によって更新します。

次に、大きい **[新しいステップ]** ボタンを使用して、休暇申請に関するすべての決定をまとめた電子メールを送信します。

引き続き、次の処理を行いましょう。

## <a name="add-a-condition-to-each-branch"></a>各分岐に条件を追加する
1. **[Start an approval] (承認を開始)** 分岐にある空白部分を選択します。
2. 小さい **[Insert a new step] (新しいステップの挿入)** ボタン (前のステップで空白部分を選択した後で表示された丸付きの + ボタン) を選択します。
3. 表示されるメニューから **[条件の追加]** を選択します。
4. **[条件]** カードの最初のチェックボックスをオンにして、動的コンテンツ一覧の **[Start an approval] (承認を開始)** カテゴリから **[Response] (応答)** トークンを選択します。
   
    ![パラレル分岐条件が含まれるフロー](./media/parallel-modern-approvals/configure-approval-condition.png)
5. 一覧 (**[条件]** カードの中ほどにある) が **[is equal to] (と等しい)** に設定されていることを確認します。
6. 最後のボックスに「**Approve**」(承認) (このテキストでは大文字と小文字が区別されます) と入力します。
7. 条件カードは、次の例のようになります。
   
    ![パラレル分岐条件が含まれるフロー](includes/media/parallel-modern-approvals/condition-card.png)
   
   > [!NOTE]
   > この条件は、**[Start an approval] (承認を開始)** アクションから従業員のマネージャーに送信される応答をチェックします。
   > 
   > 
8. **[Start an approval 2] (承認を開始 2)** (販売チームへの承認要求) と **[Start an approval 3] (承認を開始 3)** (人事チームへの承認要求) の分岐について、前のステップを繰り返します。

## <a name="add-email-actions-to-each-branch"></a>各分岐に電子メール アクションを追加する
**[条件]** 分岐の **[IF YES, DO NOTHING]** の側で、次のステップを実行します。

   注: フローでこれらのステップが使用されて電子メールが送信されるのは、要求が承認された場合です。

[!INCLUDE [add-action-to-send-email-when-vacation-approved](includes/add-action-to-send-email-when-vacation-approved.md)]

   ![事前承認済みの電子メール テンプレートを構成する](includes/media/parallel-modern-approvals/yes-email-config.png)

要求が却下されたときに電子メールを送信するには、**[条件]** 分岐の **[IF NO, DO NOTHING]** の側を使用した後、前のステップを繰り返して却下電子メール用のテンプレートを追加します。

**[Start an approval 2] (承認を開始 2)** (販売チームへの承認要求) と **[Start an approval 3] (承認を開始 3)** (人事チームへの承認要求) の分岐について、前のステップを繰り返します。

## <a name="update-the-vacation-request-with-the-decision"></a>決定によって休暇申請を更新する
決定が行われたときに SharePoint を更新するには、次の手順を実行します。

   注: 以下のステップは分岐の **[IF YES]** と **[IF NO]** の両方の側で実行してください。

[!INCLUDE [add-action-to-update-sharepoint-with-approval](includes/add-action-to-update-sharepoint-with-approval.md)]

   ![アイテムの更新の構成](./media/parallel-modern-approvals/configure-update-item.png)

**[Start an approval 2] (承認を開始 2)** と **[Start an approval 3] (承認を開始 3)** の分岐について、前のステップを繰り返します。

## <a name="complete-the-flow"></a>フローを完成させる
1. **[新しいステップ]**  >  **[アクションの追加]** を選択する
   
    ![アイテムの更新の構成](includes/media/parallel-modern-approvals/add-an-action-2-step.png)
2. 各承認の結果を要約した電子メールを送信するには、上記のステップを使用します。 この電子メールは休暇を申請した従業員に送信します。 カードは次の例のようになります。
   
   ![アイテムの更新の構成](./media/parallel-modern-approvals/final-email-card.png)

## <a name="learn-more-about-modern-approvals"></a>最新の承認に関する詳細を説明する
[最新の承認の概要](modern-approvals.md)

