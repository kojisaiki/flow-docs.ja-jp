---
title: 企業の開発者、ISV、パートナーのための Microsoft Flow | Microsoft Docs
description: Microsoft Flow のソリューションの開発について説明します。
services: ''
suite: flow
documentationcenter: na
author: mgblythe
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/31/2018
ms.author: mblythe
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: f510d387b594bb11306f8bc2530573b775e5f08e
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690401"
---
# <a name="microsoft-flow-for-enterprise-developers-isvs-and-partners"></a>企業の開発者、ISV、パートナーのための Microsoft Flow

開発者は Microsoft Flow を拡張することで組織や顧客により強力なソリューションを提供できます。

## <a name="microsoft-flow-for-enterprise-developers"></a>企業の開発者のための Microsoft Flow

企業の開発者として組織が堅牢なカスタム ソリューションを作成できるように Microsoft Flow で支援します。

- **カスタム コネクタの作成**: カスタム コネクタを作成し、Microsoft Flow を介して組織のデータと Web サービスに接続します。 [詳細については、こちらをご覧ください](https://docs.microsoft.com/connectors/custom-connectors/)

- **Azure Functions の作成**: Azure Functions を作成し、カスタム サーバー側ロジックでアプリを拡張します。 [詳細については、こちらをご覧ください](https://docs.microsoft.com/azure/azure-functions/functions-flow-scenario)

- **Microsoft Flow の組み込み**: Microsoft Flow を Web サイトのエクスペリエンスに組み込んで統合されたソリューションを作成し、組織で既に使用されているワークフローやプロセスを目に見えるようにします。 [詳細については、こちらをご覧ください](embed-flow-dev.md)

## <a name="microsoft-flow-for-isvs-and-microsoft-partners"></a>ISV および Microsoft パートナーのための Microsoft Flow

Microsoft パートナーまたは独立系ソフトウェア ベンダー (ISV) は、製品を拡張してお客様のデータやビジネス プロセスと連携することでお客様への普及を促し、ビジネス プロセスをアプリケーションの一部として自動化するためにワークフローを追加およびカスタマイズします。 以下の 7 つの手順を完了すると、アプリケーションが 200 を超えるさまざまなサービスに接続できる信頼性の高いクラウド規模のワークフロー エンジンを利用できるようになります。

| フェーズ | 手順 | 必要なタイミング |
| --- | --- | --- |
| 開発 | 1.データに対するカスタム コネクタを作成する | 独自の ISV データを PowerApps または Microsoft Flow に公開したい場合 |
| 開発 | 2.Azure Active Directory (Azure AD) でユーザーを認証するためのサポートをアプリケーションに追加する | Microsoft AppSource に Microsoft Flow の UI またはリストを埋め込みたい場合 | 
| 開発 | 3.Web ベースの iframe を使用して Microsoft Flow の UI をアプリケーションに埋め込む | アプリケーションにフローの作成または管理を追加したい場合 | 
| 開発 | 4.フロー テンプレートを作成および公開する | お客様のフローを事前に作成したい場合 | 
| 開発 | 5.プログラムでフローを展開するためのアプリケーション ロジックを追加する | お客様のために事前に作成したフローを自動的に展開したい場合 | 
| 配布 | 6.Microsoft クラウド ソリューション プロバイダー プログラムを通じてお客様に Microsoft Flow のライセンスを付与する | お客様が Office 365 または Dynamics 365 のライセンスを持っていない場合 |
| 配布 | 7.Microsoft AppSource にソリューションを表示する | ISV ソリューションの可視性を高めるために推奨 |

### <a name="1-connecting-to-your-apis-or-enabling-customers-to-connect-to-your-apis"></a>1.API への接続、またはお客様による API への接続の有効化

ISV として、お客様にフローを使用してアクセスしていただきたい独自のデータを所有することが多くあります。 カスタム コネクタを使用するとあらゆるデータに対するアクセスを公開することができます。 [詳細については、こちらをご覧ください](https://docs.microsoft.com/connectors/custom-connectors/)

作成後は、お客様が次の 2 つの方法でコネクタを使用できるようになります。
- コネクタは、REST API または PowerShell を介して、お客様のテナントに展開できます。
- カスタム コネクタをすべてのユーザーがパブリックに利用できるようにするには、コネクタを証明のために送信します。 [詳細については、こちらをご覧ください](https://docs.microsoft.com/connectors/custom-connectors/submit-certification)

### <a name="2-authentication"></a>2.認証 

REST API を呼び出し、認証済みの UI を埋め込むには、アプリケーションで Azure AD のフェデレーション シングル サインオンを使用してエンド ユーザーとお客様を認証する必要があります。 AAD フェデレーション SSO を有効にする方法については、[こちらを参照してください](https://identity.microsoft.com/)。 認証されていないアクセス、または Azure AD 以外の ID プロバイダーを使用したアクセスはサポートしていません。 

### <a name="3-embedding-ui-components"></a>3.UI コンポーネントの埋め込み

アプリ内に Microsoft Flow を埋め込んで、ご利用のアプリと Microsoft Flow がサポートする他のすべてのサービスをコンテキスト内で深く統合することができます。 [詳細については、こちらをご覧ください](embed-flow-dev.md)

### <a name="4-create-and-publish-flow-templates"></a>4.フロー テンプレートを作成および公開する

コネクタを作成した後は、サービスの使用方法を示すテンプレートを公開する必要があります。 これらのテンプレートは、ユーザーがサービスについて理解し、その後で独自のワークフローに拡張できる例として使用されます。 [詳細については、こちらをご覧ください](../publish-a-template.md)

### <a name="5-deployment"></a>5.デプロイ

エンドユーザーが自動的にフローを使用できるようにアクセス権を付与するには、フローをユーザーの Azure AD テナントにデプロイします。 REST API または PowerShell を使用してデプロイするデプロイ パッケージを使用します。 [詳細については、こちらをご覧ください](https://docs.microsoft.com/powerapps/export-import-packages)

### <a name="6-licensing"></a>6.ライセンス

お客様が既に Office 365 または Dynamics 365 を所有していて、ユーザーが Azure AD でログインする ID がそのライセンスと関連付けられている場合、それ以上のライセンス要件はありません。 ただし、お客様が Office 365 または Dynamics 365 を使用しない場合は、アプリケーションに埋め込まれたコンポーネントを利用するライセンスが与えられるように、Microsoft Flow の使用権を代わりに取得する必要があります。

お客様の代わりにライセンスを取得するための [Microsoft クラウド ソリューション プロバイダー](https://partner.microsoft.com/cloud-solution-provider) プログラムを提供しています。 Microsoft Flow には 2 種類の[価格プラン](https://flow.microsoft.com/pricing/)があります。プランと機能の詳細をご確認ください。

### <a name="7-list-on-appsource"></a>7.AppSource に登録

Microsoft Flow をアプリケーションに統合すると、AppSource に表示されます。 AppSource を使用して顧客が体験できるアプリを開発して AppSource に公開すると、ビジネスの新しい潜在顧客を開拓できます。 [詳細については、こちらをご覧ください](dev-appsource-test-drive.md)
