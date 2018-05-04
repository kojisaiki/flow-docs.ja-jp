---
title: GDPR データ主体の要求の概要 | Microsoft Docs
description: Microsoft Flow に対する GPDR データ主体の要求に応答する方法を説明します。
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/18/2018
ms.author: keweare
ms.openlocfilehash: 9f9513ca0239f72c36e96387fc010040936bbd02
ms.sourcegitcommit: 12fbfe22fedd780d42ef1d2febfd7a0769b4902e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="responding-to-gdpr-data-subject-requests-for-microsoft-flow"></a>Microsoft Flow に対する GDPR データ主体の要求への応答

この記事では、ユーザーと組織のために EU の一般データ保護規則 (GDPR) について説明します。 この記事では、GDPR に対する Microsoft の対応について説明するだけでなく、PowerApps、Microsoft Flow、Common Data Service for Apps を使用するときに GDPR コンプライアンスをサポートするために実行できる手順の例を示します。

## <a name="prerequisites"></a>前提条件

この記事に記載されているアクションをユーザーと管理者が実行できること。

### <a name="users"></a>ユーザー

ユーザーは、[Microsoft Flow ライセンス](https://preview.flow.microsoft.com/pricing/)のあるアクティブな Azure Active Directory アカウントを持っている必要があります。 この要件を満たしていないユーザーは、これらのアクションの実行を管理者に依頼する必要があります。

### <a name="administrators"></a>管理者

[Microsoft Flow 管理センター](https://admin.flow.microsoft.com/)または [PowerApps 管理者向け PowerShell](https://go.microsoft.com/fwlink/?linkid=871804) に、両方のアクセス許可を持つアカウントでサインインすると、この記事で説明されている管理者特権を必要とする操作を実行できます。

- PowerApps プラン 2 の有料版または無料試用版ライセンス。

    [無料試用版ライセンス](http://web.powerapps.com/trial)は 30 日で有効期限が切れます。

- [Office 365 全体管理者](https://support.office.com/article/assign-admin-roles-in-office-365-for-business-eac4d046-1afd-4f1a-85fc-8219c79e1504)または [Azure Active Directory 全体管理者](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)。

## <a name="responding-to-dsrs-for-microsoft-flow-customer-data"></a>Microsoft Flow 顧客データに対する DSR への応答

GDPR は、ユーザー (GDPR ではデータ主体と呼ばれます) に、雇用主または他の種類の機関や組織 (データ コントローラーまたは単にコントローラーと呼ばれます) によって収集された個人データを管理する権限を付与します。 GDPR での個人データは、識別された自然人または識別可能な自然人に関連するすべてのデータと、非常に幅広く定義されています。 GDPR では、個人データに対するデータ主体固有の権限が付与されます。このような権限には、個人データのコピーの取得、個人データの訂正の要求、個人データの処理の制限、個人データの削除、または別のコントローラーに移動できる電子的な形式での個人データの受け取りが含まれます。 データ主体がコントローラーに対して個人データへの操作を実行するよう正式に要求することを、データ主体の権利 (DSR) の要求と呼びます。

この記事では、コントローラーが DSR に応えて個人データを検索および処理するときに Microsoft の製品、サービス、管理ツールを使う方法について説明します。 具体的には、この記事には、Microsoft のクラウド内に存在する個人データを検索、アクセス、処理する方法が含まれています。 このガイドに記載されているプロセスの概要を次に示します。

1. 検出: 検索と探索のツールを使って、DSR の対象である可能性がある顧客データを簡単に検索します。 可能性のある応答ドキュメントが収集されると、以下の手順で説明されている 1 つ以上の DSR アクションを実行して、要求に応答できます。 または、DSR への応答に関する組織のガイドラインを要求が満たしていないと判断する場合もあります。 [Microsoft Flow DSR 検出ドキュメント](gdpr-dsr-discovery.md)

1. アクセス: Microsoft のクラウドに存在する個人データを取得し、要求された場合は、データ主体が使用可能な個人データのコピーを作成します。

1. 修正: 必要に応じて、個人データを変更するか、個人データに対して他の要求されたアクションを実施します。

    データ主体が組織に存在する自分の個人データの修正を要求している場合、管理者や組織は要求を受け入れるのが適切かどうかを判断する必要があります。  データの修正には、個人データの編集、検閲、削除などの操作が含まれることがあります。

    Azure Active Directory を使用して、Microsoft Flow ユーザーの ID を管理することができます。 企業の顧客は、特定の Microsoft サービスの特性に応じて編集機能を制限するなど、DSR 修正要求を管理することができます。  データ プロセッサとしての Microsoft は、システムによって生成されたログを修正する機能を提供していません。これらのログは実際のアクティビティを反映しており、Microsoft のサービス内でのイベントの履歴レコードを構成しているためです。  [DSR についての詳細](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-azure)。

1. 制限: さまざまなオンライン サービスに対するライセンスを削除するか、または可能な場合は目的のサービスをオフにすることで、個人データの処理を制限します。 また、Microsoft のクラウドからデータを削除して、オンプレミスの場所や別の場所にデータを保持することもできます。

    データ主体が、自分の個人データの処理を制限することを要求する場合があります。  Microsoft は、この目的のためのアプリケーション プログラミング インターフェイス (API) とユーザー インターフェイス (UI) を提供します。  これらのインターフェイスにより、企業顧客のテナント管理者は、データ エクスポートとデータ削除を組み合わせて、このような DSR を管理できます。 顧客は、(1) アカウント、システムで生成されたログ、関連付けられたログなどのユーザーの個人データの電子コピーをエクスポートした後、(2) Microsoft システム内に存在するアカウントおよび関連データを削除することができます。

1. 削除: Microsoft のクラウドに存在する個人データを完全に削除します。 [個人データの削除についての詳細](gdpr-dsr-delete.md)。

1. エクスポート: 個人データの (コンピューターが判読できる形式の) 電子コピーを、データ主体に提供します。 この記事の各セクションでは、データ コントローラーの組織が Microsoft のクラウド内の個人データに対する DSR に応答するために実行できる技術的な手順について説明します。 [個人データのエクスポートについての詳細](gdpr-dsr-export.md)。

## <a name="system-generated-logs"></a>システム生成ログ

Microsoft Flow のシステム生成ログについて詳しくは、こちらの[ガイド](https://docs.microsoft.com/powerapps/administrator/powerapps-gdpr-dsr-guide-systemlogs)をご覧ください。
