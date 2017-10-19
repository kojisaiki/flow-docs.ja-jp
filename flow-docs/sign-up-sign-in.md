---
title: "サインアップおよびサインイン | Microsoft Docs"
description: "Microsoft Flow にサインアップおよびサインインして、このプロセスに関する問題のトラブルシューティングを行います。"
services: 
suite: flow
documentationcenter: na
author: anjlic
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/04/2017
ms.author: anjlic
ms.openlocfilehash: a7ebed9be4753bbd3a416271464fe908db00e8bb
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="sign-up-and-sign-in-for-microsoft-flow"></a>Microsoft Flow でのサインアップおよびサインイン
<iframe width="560" height="315" src="https://www.youtube.com/embed/cRkmSZrctLc?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

個人用に Microsoft Flow の使用を開始するのは簡単です。 フローを作成する前に、任意の電子メール アドレスを使用してサインアップします。 そのアドレスでオンラインの Microsoft 製品を使用したことがない場合は、少し時間を取って登録する必要があります。

## <a name="sign-up-free"></a>無料サインアップ
他のオンライン Microsoft 製品を使用したことがない場合、サインアップが必要になります。

1. [Flow.microsoft.com](https://flow.microsoft.com) で、右上隅の **[無料でサインアップ]** をクリックまたはタップします。
2. 電子メール アドレスを入力します。
3. 右矢印をクリックまたはタップします。
   
    ![サインアップ リンク](./media/sign-up-sign-in/signup.png)

## <a name="sign-in"></a>サインイン
仕事または個人で他のオンライン Microsoft 製品を使用したことがある場合、サインインするだけでかまいません。

1. [flow.microsoft.com](https://flow.microsoft.com) で、右上隅の **[サインイン]** をクリックまたはタップします。
   
    ![サインイン リンク](./media/sign-up-sign-in/signin.png)
2. 電子メール アドレスを入力します。
3. [サインイン] ページで、電子メール アドレスとパスワードを入力します。

## <a name="using-paid-features"></a>有料機能の使用
どなたでもサインアップして Microsoft Flow の無料プランをご利用いただけます。 所属する組織で Office 365 または Dynamics 365 を購入しているようであれば、Microsoft Flow のその他の機能を使用できる可能性があります。 有料の機能を使用したい場合は、90 日間無料試用版を開始するか、Microsoft Flow Plan 1 または Plan 2 をご購入いただくこともできます。 支払いの詳細については、[こちら](billing-questions.md)をご覧ください。

管理については、[組織の Q&A のフロー](organization-q-and-a.md)に関するページをご覧ください。

## <a name="troubleshooting"></a>トラブルシューティング
ほとんどの場合、このトピックで説明した簡単なプロセスで Microsoft Flow に登録できますが、 場合によっては、登録できないこともあります。この表では、サインアップできない場合の最も一般的な原因と、その回避策について説明します。

| 症状/エラー メッセージ | 原因と回避策 |
| --- | --- |
| **Microsoft アカウントが作成されていない** <br> サインアップ中に電子メール アドレスを入力した後、次のようなメッセージが届きます。<br><br> *その Microsoft アカウントは存在しません。別のアカウントを入力するか、新しいアカウントを取得してください。* |Microsoft アカウントが作成されていない電子メール アドレスでサインアップしました。 そのページの **[今すぐサインアップ]** リンクを選択すると、お使いの電子メール アドレスに対応する新しい Microsoft アカウントを作成できます。 既存の電子メール アドレスを使用して Microsoft アカウントを作成できます。 |
| **.gov または .mil の電子メール アドレス**<br>サインアップ時に次のようなメッセージが表示される。<br><br>*Microsoft Flow unavailable: Microsoft Flow is not available for users with .gov or .mil email addresses at this time. (Microsoft Flow を使用できません: 現在、Microsoft Flow は、電子メール アドレスに .gov または .mil が含まれるユーザーが使用することはできません。)Use another work email address or check back later. (他の勤務先の電子メール アドレスを使用するか、後でもう一度ご確認ください。)* |現在、.gov または .mil のアドレスで Microsoft Flow にサインアップすることはできません。 その代わり、*@outlook.com* アドレスなど、任意の Microsoft アカウント電子メール アドレスを使ってサインインできます。 |
| **セルフ サービス サインアップが無効になっている**<br><br>サインアップ時に次のようなメッセージが表示される。<br>*We can't finish signing you up. (サインアップを完了できません。)Your IT department has turned off signup for Microsoft Flow. (IT 部門によって Microsoft Flow のサインアップが無効になっています。)Contact them to complete signup. (サインアップを完了するには、IT 部門に連絡してください。)* <br>または<br> *We can't finish signing you up. (サインアップを完了できません。)It looks like Microsoft Flow isn't currently available for your work or school. (現在、Microsoft Flow は職場または学校で使用できなくなっている可能性があります。)* |**[サインイン]** ではなく **[サインアップ]** を選択しました。 ホーム ページ上部の **[サインイン]** を選択すると、Microsoft Flow にアクセスできるようになります。 |
| **電子メール アドレスが Office 365 ID ではない**<br><br>サインアップ時に次のようなメッセージが表示される。<br>*We can't find you at contoso.com. (contoso.com で見つかりません。)Do you use a different ID at work or school? (勤務先または学校で別の ID を使用していますか?)Try signing in with that, and if it doesn't work, contact your IT department. (その ID でサインインしようとして、うまくいかない場合は、IT 部門に問い合わせください。)* |ユーザーの組織では ID を使用して、Office 365 やその他の Microsoft サービスにサインインしていますが、その ID がユーザーの電子メール アドレスと異なります。 たとえば、電子メール アドレスが Nancy.Smith@contoso.com で、ID が nancys@contoso.com である場合もあります。サインアップを完了するには、Office 365 やその他の Microsoft サービスにサインインするために組織によって割り当てられた ID を使用します。 |

## <a name="next-steps"></a>次のステップ
* [テンプレートの使用を開始します](get-started-logic-template.md)。テンプレートは、設定済みの事前に構築されたフローです。
* 既にプロセスが決まっており、そのプロセスに合ったテンプレートが見つからない場合は、[ゼロからフローを作成](get-started-logic-flow.md)してください。

