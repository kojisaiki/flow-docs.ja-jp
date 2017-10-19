---
title: "課金と使用状況の測定に関する質問 | Microsoft Docs"
description: "Microsoft Flow の課金と使用状況の測定についてよく寄せられる質問とその回答"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: aftowen
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/21/2016
ms.author: deonhe
ms.openlocfilehash: b627c008e1483360f35b6de579e2c0da32e60c93
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="billing-and-metering-questions"></a>課金と使用状況の測定に関する質問
この記事では、Microsoft Flow の課金と使用状況の測定についてよく寄せられる質問とその回答を紹介します。

## <a name="where-can-i-find-out-what-pricing-plans-are-available"></a>利用できる価格プランはどこで確認できますか
[価格に関するページ](https://flow.microsoft.com/pricing/)を参照してください。

## <a name="where-can-i-find-out-what-my-plan-is"></a>現在のプランはどこで確認できますか
[価格に関するページ](https://flow.microsoft.com/pricing/)を参照してください。

## <a name="how-do-i-switch-plans"></a>プランの切り替え方法を教えてください
上部のナビゲーション メニューで、[**学習**] をクリックまたはタップして、[**価格**] をクリックまたはタップします。

![[学習]、[Pricing (価格)] の順に選択](./media/billing-questions/learn-pricing.png)

## <a name="how-do-i-know-how-much-ive-used"></a>使用量を確認する方法を教えてください
[**アクティビティ**] をクリックまたはタップすると、実行のログが通知および失敗と共に表示されます。

![[アクティビティ] リンク](./media/billing-questions/activity-link.png)

無料プランまたは試用プランをご利用の場合、上部のナビゲーション バーの歯車アイコンをクリックまたはタップすると、プランに対する現在の使用状況が表示されます。   

![[設定] ボタン](./media/billing-questions/settings.png)

無料プランまたは試用プランをご利用でない場合は、組織内のすべてのユーザー間で実行がプールされます。 組織全体で使用可能なクォータと使用状況を公開できる機能に取り組んでいます。

## <a name="what-happens-if-my-usage-exceeds-the-limits"></a>使用量が制限を超えた場合はどうなりますか
Microsoft Flow が実行を調整し始める場合があります。

## <a name="where-can-i-find-more-information-regarding-the-usage-limits"></a>使用量の制限に関する詳細情報はどこで見つけられますか
[価格に関するページ](https://flow.microsoft.com/pricing/)の 「**FAQ**」セクションを参照してください。

## <a name="what-happens-if-i-try-to-execute-runs-too-frequently"></a>実行の試行頻度が高すぎるとどうなりますか
プランに応じて、フローの実行頻度が決定されます。 たとえば、無料プランの場合、フローを実行できるのは 15 分ごとになります。 前回の実行から 15 分が経過しないうちにフローがトリガーされた場合、フローは 15 分が経過するまでキューに入れられます。 新しいデータの確認は実行とは見なされません。

## <a name="what-counts-as-a-run"></a>実行と見なされるものを教えてください
自動トリガーによるか手動での開始かにかかわらず、フローはトリガーされるたびに、1 つの実行と見なされます。

## <a name="are-there-differences-between-microsoft-accounts-and-work-or-school-accounts-for-billing"></a>Microsoft アカウントと職場または学校アカウントの間では、課金について違いがありますか
はい。 Microsoft アカウント (@outlook.com や @gmail.com で終わるアカウントなど) でサインインした場合、利用できるのは無料プランのみになります。 有料プランの機能を利用するには、職場または学校の電子メール ID でサインインします。

## <a name="im-trying-to-upgrade-but-im-told-my-account-isnt-eligible"></a>アップグレードを試していますが、アカウントが適切ではないと表示されます
アップグレードするには、職場または学校アカウントを使用するか、[こちら](https://powerbi.microsoft.com/documentation/powerbi-admin-signing-up-for-power-bi-with-a-new-office-365-trial/)の Power BI の記事の手順に従って、Office 365 試用版を作成します。

## <a name="why-did-i-run-out-of-runs-when-my-flow-only-ran-a-few-times"></a>自分のフローが数回しか実行されていないときに実行が制限に達してしまうのはなぜですか
特定のフローは、予想よりも頻繁に実行される場合があります。 たとえば、上司から電子メールが届くたびにプッシュ通知を送信するフローを作成することができます。 そのフローはメールが届くたびに実行されなければなりません。メールが上司からのものかどうかを確認する必要があるからです。 このアクションは実行と見なされます。

この問題は、必要なフィルターをすべてトリガー内に含めることで回避できます。 上記の例では、[**詳細オプション**] メニューを展開し、[**送信元**] フィールドに上司のメール アドレスを指定します。

## <a name="other-limits-and-caveats"></a>その他の制限と注意事項
* 各アカウントには次の制限があります。
  * 50 個のフロー
  * 15 個のカスタム コネクタ
  * API あたり 20 個、合計で 100 個の接続。
* ゲートウェイは、既定の環境でのみインストールできます。   
* Twitter など、特定の外部のコネクタは、接続のスロットルを実装してサービスの品質を制御できます。 スロットルを有効にすると、フローは失敗します。 このスロットルの詳細をレビューするには、フローの実行履歴にある失敗した実行を確認します。

