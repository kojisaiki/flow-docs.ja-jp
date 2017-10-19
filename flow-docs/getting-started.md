---
title: "はじめに | Microsoft Docs"
description: "Microsoft Flow を使用して、仕事や生活をすばやく自動化する方法を紹介します"
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: hero-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/27/2017
ms.author: stepsic
ms.openlocfilehash: 4ed27b114819146f38a58e4f781a8372be9f60a1
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="get-started-with-microsoft-flow"></a>Microsoft Flow を使ってみる
<iframe width="560" height="315" src="https://www.youtube.com/embed/iMteXfAvDSE?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

ようこそ。 Microsoft Flow は、お気に入りのアプリとサービスの間のワークフローを自動化して、ファイルの同期、通知の受信、データ収集などを行うための製品です。

まずは[サインアップ](sign-up-sign-in.md)してください。既に Microsoft のアカウントをお持ちの場合は、タブレットやデスクトップ コンピューター、さらにはスマートフォンで直接[サインイン](https://flow.microsoft.com/signin)できます。

## <a name="check-out-the-home-page"></a>ホーム ページの確認
Microsoft Flow の[ホーム ページでは](https://flow.microsoft.com)、[さまざまなテンプレートが用意されている](https://flow.microsoft.com/templates)ほか、Microsoft Flow のいくつかの主要な機能について説明されています。 Microsoft Flow で何ができるか、またビジネスや普段の生活にどのように役立つかを簡単に把握することができます。

![Flow のホームページ](./media/getting-started/flowhome1.png)

![Flow のホームページ](./media/getting-started/flowhome2.png)

![Flow のホームページ](./media/getting-started/flowhome3.png)

テンプレートはそれぞれ、上司から電子メールが届いたときにテキスト メッセージを送信する、Twitter の潜在顧客を Dynamics 365 に追加する、ファイルをバックアップするなど、特定の用途に応じて設計されています。 ただし、このようなテンプレートは氷山の一角にすぎません。テンプレートの目的は、必要なプロセスに合わせて正確にカスタマイズされたフローを作成できるようにすることです。

## <a name="create-your-first-flow"></a>最初のフローの作成
役に立つフロー テンプレートを見つける必要があります。 ごく単純なテンプレートの 1 つに、[**[メールで毎日リマインダーを受け取る]**](https://flow.microsoft.com/galleries/public/templates/45a3399aa29345308f08b6db0a9c85b9/) があります。

![Flow のテンプレート](./media/getting-started/template-details.png)

このテンプレートを使用するのは非常に簡単です。まず **[続行]** を選択してください。

![接続の作成](./media/getting-started/create-connection.png)

毎日のリマインダーを送信する電子メール アドレスを入力します。 次に、リマインダーのメッセージを入力します。 最後に、**[フローの作成]** を選択し、フローが想定どおりに実行されることを確認します。

![接続の作成](./media/getting-started/configure-email-details.png)

注: フローをトリガーする条件と、そのイベントによって実行されるアクションを確認できます。 さまざまな設定を試して、フローをカスタマイズします。アクションを追加または削除することもできます。 (または、単に **[完了]** を選択します。)

他のテンプレートを探し、[このチュートリアルに従って](get-started-logic-template.md)テンプレートからフローをさらに作成する方法を詳しく確認します。

## <a name="get-creative"></a>独自のフローの作成
ここまでは、フローで何ができるかを理解し、少し操作も行いました。次は、次のデータ ソースと他の必要な情報に基づいて[フローをゼロから作成](get-started-logic-flow.md)します。

* Dropbox、OneDrive、Google ドライブなどのクラウド ストレージ アカウント内の Excel ファイル
* Google シート
* SharePoint リスト
* ユーザー定義エンティティが含まれる Salesforce または Microsoft Dynamics 365
* SQL Azure テーブル
* [Microsoft Common Data Service](common-data-model-intro.md)

![フローの構築](./media/getting-started/build-a-flow.png)

フローをゼロから作成すると、頭で考えたフロー全体がそのまま画面上で再現されます。 次のトピックで説明するさまざまな方法を使用することもできます。

* [多くのステップが含まれるフロー](multi-step-logic-flow.md)
* [スケジュールに従ってタスクを実行する](run-tasks-on-a-schedule.md)
* [承認フローを作成する](wait-for-approvals.md)
* [実行中のフローを確認する](see-a-flow-run.md)
* [テンプレートを発行する](publish-a-template.md)

## <a name="use-the-mobile-app"></a>モバイル アプリの使用
[Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリをモバイル デバイスにダウンロードします。これにより、次のことができるようになります。

* [フローのアクティビティを監視する](mobile-monitor-activity.md)。たとえば、各フローの成功、失敗、および最後に実行された時間を監視できます
* [各フローを管理する](mobile-manage-flows.md)。フローを有効または無効にしたり、イベントやアクションを確認したりできます
* [テンプレートからフローを作成する](mobile-create-flow.md)。たとえば、指定した送信者からメールを受信したときに、プッシュ通知を受け取るためのフローを作成します

## <a name="questions-ideas-were-here-to-help"></a>ご質問、 ご意見を お寄せください
マイクロソフトでは、Microsoft Flow に関する皆様のご意見をお待ちしております。また、この Microsoft Flow が皆様のお役に立つことを心より願っております。 さらに詳しいヘルプ情報が必要な場合は、こちらの詳細なチュートリアルをご覧ください。また、[コミュニティに参加](http://go.microsoft.com/fwlink/?LinkID=787467)して、質問したり、アイデアを交換したりすることもできます。 ご不明な点がありましたら、こちらの[サポート情報](http://go.microsoft.com/fwlink/?LinkID=787479)をご確認ください。

