---
title: 全員が承認する必要のある承認フローを作成する | Microsoft Docs
description: 要求を承認するには全員の承認が必要な承認フロー、つまり 1 人でも拒否すれば要求が拒否される承認フローを作成します。
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
ms.date: 02/27/2018
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 141eb19018e080191bf0fe2ba6f47f0739d347d7
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689711"
---
# <a name="create-an-approval-flow-that-requires-everyone-to-approve"></a>全員が承認する必要のある承認フローを作成する

このチュートリアルでは、休暇申請が承認されるためには全員 (割り当てられているすべての承認者) が同意する必要があり、どの承認者でも要求全体を拒否できる、承認ワークフローを作成する方法を示します。

この種の承認ワークフローは、休暇申請の承認に従業員のマネージャーとマネージャーのマネージャーの両方の同意を必要とする組織で役に立ちます。 ただし、いずれかのマネージャーは、他のユーザーの入力がなくても要求を拒否できます。

> [!NOTE]
> このチュートリアルは休暇承認シナリオですが、この種類の承認フローは、要求を承認するために複数の承認者が必要な任意の状況で使えます。
>
>

## <a name="prerequisites"></a>前提条件

* [Microsoft Flow](https://flow.microsoft.com)、Microsoft Office 365 Outlook、Microsoft Office 365 ユーザーへのアクセス。
* SharePoint [リスト](https://support.office.com/article/SharePoint-lists-I-An-introduction-f11cd5fe-bc87-4f9e-9bfe-bbd87a22a194)。

    このチュートリアルでは、休暇申請に使う SharePoint リストを作成してあるものとします。 SharePoint リストの詳細を示す例については、[並列承認](parallel-modern-approvals.md)に関するチュートリアルをご覧ください。
* フロー作成の基本をよく理解している。

    [アクション、トリガー](multi-step-logic-flow.md#add-another-action)、および[条件](add-condition.md)の追加方法を確認することができます。 次の手順では、これらのアクションの実行方法がわかっていることを前提とします。

> [!NOTE]
> このチュートリアルでは、SharePoint と Office 365 Outlook を使いますが、Zendesk、Salesforce、Gmail、Microsoft Flow がサポートする [200 以上のサービス](https://flow.microsoft.com/connectors/)など、その他のサービスを使うこともできます。
>
>

## <a name="create-the-flow"></a>フローを作成する

> [!NOTE]
> 以前に SharePoint または Office 365 への接続を作成しており、サインインを求められた場合は、表示される指示に従います。
>
>

このチュートリアルではトークンを使います。 トークンの一覧を表示するには、いずれかの入力コントロールをタップまたはクリックし、表示される **[動的なコンテンツ]** の一覧でトークンを検索します。

[Microsoft Flow](https://flow.microsoft.com) にサインインし、以下の手順でフローを作成します。

1. 画面の右上で **[自分のフロー]** > **[一から作成]** を選びます。
1. **[SharePoint - When an item is created or modified]\(SharePoint - 項目が作成または変更されたとき\)** トリガーを追加します。
1. 休暇申請リストをホストする SharePoint サイトの **[サイトのアドレス]** を入力し、**[リスト名]** リストを選びます。
1. **[Office 365 ユーザー - 上司を取得する V2]** アクションを追加し、**[ユーザー (UPN)]** ボックスを選んで、**[Created By Email]\(作成者の電子メール\)** トークンを追加します。

    **[Created By Email]\(作成者の電子メール\)** トークンは、**[動的なコンテンツ]** の一覧の **[When an item is created or modified]\(項目が作成または変更されたとき\)** カテゴリにあります。 このトークンは、SharePoint で項目を作成したユーザーのマネージャーに関するデータへのアクセスを動的に提供します。

1. 別の **[Office 365 ユーザー - 上司を取得する V2]** アクションを追加し、**[メール]** トークンを **[ユーザー (UPN)]** ボックスに追加します。

    **[メール]** トークンは、**[動的なコンテンツ]** の一覧の **[上司を取得する V2 2]** カテゴリにあります。 このトークンは、マネージャーのマネージャーのメール アドレスへのアクセスを動的に提供します。

    **[上司を取得する V2 2]** カードの名前は、"階層の上司をスキップする" のようなわかりやすい名前に変更できます。
1. **[Start an approval]\(承認を開始する\)** アクションを追加し、**[Approval type]\(承認の種類\)** の一覧から **[割り当て済みリストのすべてのユーザー]** を選びます。

   > [!IMPORTANT]
   > いずれかの承認者が拒否した場合、承認要求はすべての承認者について拒否されたものと見なされます。
   >
   >
1. 次の表を参考にして、**[Start an approval]\(承認を開始する\)** カードを設定します。

   | フィールド | 説明 |
   | --- | --- |
   |  Approval type (承認の種類) |**[割り当て済みリストの任意のユーザー]** を使って、どの承認者でも要求を承認または拒否できることを示します。 </p>**[割り当て済みリストのすべてのユーザー]** を使って、全員が同意した場合にのみ要求は承認され、1 人でも拒否すると要求は拒否されることを示します。 |
   |  タイトル |承認要求のタイトルです。 |
   |  割り当て先 |承認者のメール アドレスです。 |
   |  詳細 |**[割り当て先]** フィールドに列記されている承認者に送信する追加情報です。 |
   |  アイテム リンク |承認項目の URL です。 この例では、これは SharePoint 内の項目へのリンクです。 |
   |  アイテム リンクの説明 |**[アイテム リンク]** の説明です。 |

   > [!TIP]
   > **[Start an approval\(承認を開始する\)]** アクションでは、**応答**や**応答の概要**など、複数のトークンが提供されます。 これらのトークンをフローで使って、承認要求フロー実行結果の充実したレポートを提供します。
   >
   >

    **[Start an approval]\(承認を開始する\)** カードは、承認者に送信される承認要求のテンプレートです。 組織にとって便利なようにこれを構成します。 次に例を示します。

    ![承認を開始する](media/all-assigned-must-approve/start-an-approval-card.png)

1. **[Office 365 Outlook - 電子メールを送信]** アクションを追加し、要求の結果のメールを送信するように構成します。

    **[電子メールを送信]** カードの例を次に示します。

    ![電子メールを送信](media/all-assigned-must-approve/send-an-email-card.png)

> [!NOTE]
> **[Start an approval\(承認を開始する\)]** アクションの後のすべてのアクションは、**[Start an approval\(承認を開始する\)]** カードの **[Approval type\(承認の種類\)]** の一覧での選択に基づいて実行されます。 次の表は、選択に基づく動作の一覧です。
>
>

| Approval type (承認の種類) | 動作 |
| --- | --- |
| 割り当て済みリストの任意のユーザー |**[Start an approval\(承認を開始する\)]** アクションに続くアクションは、承認者の誰か 1 人が決定した後で実行されます。 |
| 割り当て済みリストのすべてのユーザー |**[Start an approval\(承認を開始する\)]** アクションに続くアクションは、1 人の承認者が要求を拒否するか、またはすべての承認者が要求を承認した後で実行されます。 |

画面の上部にある **[フロー名]** にフローの名前を入力し、**[フローの作成]** を選んで保存します。

以上でフローが完成しました。 ここまで実行していれば、フローは次の図のようになります。

![フローの全体像の図](media/all-assigned-must-approve/overall-flow.png)

SharePoint リストに項目が追加されるか項目が変更されるたびに、フローがトリガーされ、**[Start an approval]\(承認を開始する\)** カードの **[割り当て先]** に列記されているすべての承認者に承認要求が送信されます。 フローは、Microsoft Flow モバイル アプリおよびメールで承認要求を送信します。 SharePoint の項目を作成したユーザーは、要求の承認または拒否が明確に示された結果の概要をメールで受け取ります。

各承認者に送信される承認要求の例を次に示します。

![承認要求](media/all-assigned-must-approve/approval-request.png)

フロー実行後の応答および応答概要の例を次に示します。

![応答トークン](media/all-assigned-must-approve/response-output.png)

## <a name="learn-more-about-approvals"></a>承認に関する詳細

* [1 人の承認者による最新の承認](modern-approvals.md)
* [シーケンシャルな最新の承認](sequential-modern-approvals.md)
* [並列の最新の承認](parallel-modern-approvals.md)
* [承認と Microsoft Common Data Service](common-data-model-approve.md)
* [外出先で要求を承認する](mobile-approvals.md)
