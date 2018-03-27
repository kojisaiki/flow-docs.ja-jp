---
title: よく寄せられる質問 | Microsoft Docs
description: Microsoft Flow に関するいくつかの一般的な質問に回答します。
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/15/2017
ms.author: stepsic
ms.openlocfilehash: 99a66520b5a922b4945c9d3c94c7a5c053df98ee
ms.sourcegitcommit: a0435b92fa7f5dedff3b0ff806836c7a07309fd2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="frequently-asked-questions"></a>よく寄せられる質問
## <a name="audience-and-strategy"></a>対象ユーザーと戦略
### <a name="what-is-microsoft-flow"></a>Microsoft Flow とは何ですか。
Microsoft Flow とは、時間のかかるビジネス タスクやプロセスを、さまざまなアプリケーションやサービスに自動化するワークフローを構築する、基幹業務ユーザーを対象としたクラウド ベースのサービスです。

### <a name="who-is-the-intended-audience-for-microsoft-flow"></a>Microsoft Flow の対象ユーザーは誰ですか。
Microsoft Flow は次の 2 種類のユーザーを明確な対象としています。

* IT とパートナーシップを組み、ビジネス ソリューションの責任をビジネス自体につなげる企業組織内の基幹業務 “シチズン インテグレーター”。
* IT や統合の専門家たちが、Azure Logic Apps などのより高度な統合ツールに専門知識を活用できるよう、基幹業務パートナーには独自のソリューションを構築できる力を与えたい IT の意思決定者。

### <a name="how-do-microsoft-flow-and-logic-apps-relate-to-each-other"></a>Microsoft Flow と Logic Apps は互いにどのように関連していますか。
Microsoft Flow では、基幹業務ユーザーがワークフローを自動化する機能を提供します。 Logic Apps は、Microsoft Flow の強力な機能のみならず、Azure Resource Manager および Azure Portal との統合、PowerShell と xPlat CLI、Visual Studio、より多くのコネクタなどの機能も提供する Azure サービスです。 [Logic Apps の詳細については、こちらを参照してください](https://azure.microsoft.com/services/app-service/logic/)。

### <a name="how-does-microsoft-flow-fit-in-microsofts-overall-business-application-platform-strategy"></a>Microsoft Flow は、マイクロソフトのビジネス アプリケーション プラットフォーム戦略全体でどのような役割を果たしますか。
Microsoft Flow は、PowerApps、Common Data Service、Dynamics 365、Office 365 などの強力で柔軟なビジネス アプリケーション プラットフォームの一部です。 Microsoft のお客様、パートナー、および ISV パートナーは、機能的な役割を果たす、または特定の地域に特化した専用のソリューションを、このプラットフォームで、自身の企業や業界専用に構築できます。 ビジネス要件を最もよく理解している基幹業務ユーザーは、データおよびプロセスを簡単に、分析、構成および合理化できるようになります。 プロフェッショナルな開発者は、自動化、分析、アプリの基幹業務を簡単に拡張して、Functions、App Service および Logic Apps などの Azure サービスを活用できます。 API コネクタ、ゲートウェイ、および Microsoft Common Data Service を使用すると、クラウドまたはオンプレミスのいずれかで、既に使用中のサービスやデータからより多くの価値を得ることができるようになります。

## <a name="functionality"></a>機能
### <a name="what-do-i-need-to-use-microsoft-flow"></a>Microsoft Flow を使用するには何が必要ですか。
Microsoft Flow の使用には、Web ブラウザーおよび電子メール アドレスのみが必要です。

### <a name="what-browsers-does-microsoft-flow-support"></a>Microsoft Flow ではどのブラウザーがサポートされていますか。
Microsoft Flow では、Microsoft Edge のほか、Chrome と Safari の最新バージョンがサポートされています。

### <a name="which-email-addresses-are-supported"></a>メール アドレスとしてサポートされているのは、どのようなものですか。
Microsoft Flow は、末尾が .gov と .mil 以外のすべてのメール アドレスをサポートしています。  

### <a name="is-microsoft-flow-available-on-premises"></a>Microsoft Flow はオンプレミスで使用できますか。
Microsoft Flow は、パブリック クラウド上のみのサービスです。 ただし、オンプレミス データ ゲートウェイを通じてオンプレミス サービスに安全に接続できます。

### <a name="what-services-can-microsoft-flow-connect-to"></a>Microsoft Flow はどのようなサービスに接続できますか。
Microsoft Flow は最初から 100 以上のデータ ソースに接続できるようになっており、それらは追加され続けています。 データ ソースとサービスの例をいくつか次に示します。

* SharePoint
* Dynamics 365
* OneDrive
* OneDrive for Business
* Google ドライブ
* Google シート
* Trello
* Twitter
* Box
* Facebook
* Salesforce.com
* Mailchimp
* 顧客 API

使用可能なすべてのコネクタの一覧は、[こちら](https://go.microsoft.com/fwlink/?LinkId=832211)を参照してください。

[オンプレミス データ ゲートウェイ](gateway-manage.md)を介して自社の IT インフラストラクチャ上のデータ ソースにアクセスできます。

### <a name="what-are-templates"></a>テンプレートとは何ですか。
テンプレートとは、よく使用される一般的なシナリオ用に事前に作成されたフローのことです。 このテンプレートを使用するのに必要なのは、テンプレート内のサービスにアクセスできることと、必要な設定を入力することだけです。

### <a name="what-data-sources-will-i-be-able-to-connect-to"></a>どのデータ ソースに接続できますか。
Office 365、Twitter、SharePoint、OneDrive、Dropbox、SQL Server など、Microsoft とサード パーティの 100 以上の標準的なサービスに接続することができます。 PowerApps 向けの Common Data Service や Salesforce などのプレミアム サービスに接続することもできます。

### <a name="how-do-i-connect-to-a-rest-api-in-my-flow"></a>フローで REST API に接続する方法を教えてください。
[カスタム コネクタ](register-custom-api.md)を作成することで、JSON を使用し、10 を超える認証方法のうち少なくとも 1 つをサポートしている任意の REST API に接続できます。

### <a name="how-do-i-connect-to-sql-server-and-other-on-premises-data-sources"></a>SQL Server やその他のオンプレミス データ ソースに接続する方法を教えてください。
[オンプレミスのデータ ゲートウェイ](gateway-manage.md)を使用すると、ローカル ネットワーク上のサービスに接続できます。

### <a name="can-i-share-the-flows-i-create"></a>作成したフローは共有できますか。
以下の方法のいずれかでフローを共有することができます。

* フローの所有者として、組織の同僚やグループを追加することができ、同僚やグループがフローを編集したり管理したりすることができるようなります。
* 手動で実行できるフローでは、組織の他のユーザーまたはグループにフローの実行のみを許可することができます。

### <a name="how-many-flows-can-i-have"></a>所有できるフローの数を教えてください。
Microsoft Flow には最大 50 のフローが付属します。 さらに必要な場合は、リクエストすることが可能です。

### <a name="where-do-i-get-started-with-microsoft-flow"></a>Microsoft Flow はどこから開始できますか。
次のリソースから開始できます。

* [ブログ](https://flow.microsoft.com)
* [YouTube チャンネル](https://youtube.com/playlist?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF)
* [トピック](getting-started.md)
* [コミュニティ](https://powerusers.microsoft.com)

### <a name="what-operating-systems-does-the-mobile-app-for-microsoft-flow-support"></a>Microsoft Flow 用のモバイル アプリがサポートする OS は何ですか。
Microsoft Flow モバイル アプリは、[Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) で使用できます。

### <a name="can-flows-be-turned-off-or-disabled"></a>フローをオフまたは無効にすることはできますか。

はい。各フローにはオン/オフ スイッチがあり、フローで要求が処理されないようにすることができます。

フローがオンに戻ったときにどのように反応するかについては、次の表を確認してください。

トリガーの種類|説明
-------|--------
ポーリング (**繰り返し**トリガーなど)|フローが再度オンになったときに、未処理/保留中のイベントがすべて処理されます。
Webhook|フローが再度オンになったときに処理されるのは、フローがオンになってから生成される新しいイベントのみです。

### <a name="what-regions-and-languages-does-microsoft-flow-support"></a>Microsoft Flow ではどのリージョンと言語がサポートされていますか。
Microsoft Flow は、42 の言語、[6 つのリージョン](regions-overview.md)で使用できます。

### <a name="how-does-microsoft-flow-compare-to-sharepoint-designer-2013"></a>Microsoft Flow と SharePoint Designer 2013 にはどのような違いがありますか。
Microsoft Flow は、承認、ドキュメントの校閲、オンボード/オフボードなど、多くの一般的なビジネス シナリオに対応する SharePoint Designer の後継サービスです。 これは、今後 SharePoint で業務を自動化させる既定のツールとなります。

### <a name="how-does-microsoft-flow-ensure-that-corporate-data-isnt-accidentally-released-to-social-media-services"></a>Microsoft Flow では企業のデータが誤ってソーシャル メディア サービスに公開されないようにするためにどのような対策が講じられていますか。
管理者は[データ損失防止ポリシー](prevent-data-loss.md)を作成して、承認されたサービスのみが Microsoft Flow で使用されるようにすることができます。

## <a name="licensing"></a>ライセンス
### <a name="will-microsoft-flow-still-have-a-free-or-trial-option"></a>Microsoft Flow の無料版または試用版のオプションはありますか。
はい。 ユーザー権限が制限された無料版を使用することも、Microsoft Flow の 90 日間試用版にサインアップすることもできます。 試用期間中は、いつでもサブスクリプションをアクティブにできます。

### <a name="what-pricing-plans-do-you-offer"></a>どのような価格プランが用意されていますか。
Microsoft Flow には、無料と有料の両方のサービス レベルが用意されています。 [価格の詳細については、こちらをご覧ください](billing-questions.md)。

