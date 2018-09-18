---
title: Microsoft アカウント (MSA) に対する GDPR データ主体の要求の概要 | Microsoft Docs
description: Microsoft Flow に対する GPDR データ主体の要求に応答する方法を説明します。
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: KFile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 5/16/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: 3742ac7afed24b0a1523a6038978589d293ba00b
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688492"
---
# <a name="respond-to-gdpr-data-subject-rights-dsrs-requests"></a>GDPR データ主体の権利 (DSR) の要求に応答する

この記事では、EU の一般データ保護規則 (GDPR) について説明し、Microsoft アカウント (MSA) での認証を行う Microsoft Flow ユーザー向けに GDPR コンプライアンスをサポートする手順について示します。

## <a name="prerequisites"></a>前提条件

この記事の手順を実行するには、[Microsoft Flow の無料ライセンス](https://flow.microsoft.com/pricing/)がある MSA が必要です。

>[!TIP]
> また、GDPR のコンプライアンス情報は、[Azure Active Directory アカウント](gdpr-dsr-summary.md)での認証を行うユーザーにも使用できます。
>
>

## <a name="respond-to-dsrs-for-microsoft-flow-customer-data"></a>Microsoft Flow 顧客データに対する DSR に応答する

個人データへのアクションを実行するようコントローラーに対してデータ主体で正式に要求することを、データ主体の権利 (DSR) の要求と呼びます。 GDPR では、個人データを、**識別された自然人または識別可能な自然人に関連するすべてのデータ**として定義します。 GDPR は、ユーザー (データ主体と呼ばれます) に、雇用主、機関、組織 (データ コントローラーまたは単にコントローラーと呼ばれます) によって収集された個人データを管理する権限を付与します。 これには以下の権限が含まれます。

* 個人データのコピーを取得する
* 個人データへの修正を要求する
* 個人データの処理を制限する
* 個人データを削除する
* 別のコントローラーに移動できるように、個人データを電子形式で受け取る

クラウドにあるデータに対する DSR 要求に応答するときに、コントローラーで個人データを検索および処理できるように、Microsoft では製品、サービス、ツールを提供しています。

このガイドに記載されているプロセスの概要を次に示します。

1. **検出**: 検索と探索のツールを使って、DSR 要求の対象である可能性がある顧客データを簡単に検索します。 収集したドキュメントがアクションを行うためのコントローラー ガイドラインを満たしているかどうかを判断するには、次の手順で示されている 1 つ以上の DSR アクションを実行します。 [Microsoft Flow での Microsoft アカウントに対する DSR 検出ドキュメント](gdpr-dsr-discovery-msa.md)に関する詳細。 または、DSR 要求への応答に関するコントローラーのガイドラインを要求が満たしていないと判断する場合もあります。

1. **アクセス**: Microsoft のクラウドに存在する個人データを取得し、要求された場合は、データ主体が使用できるように個人データのコピーを作成します。

1. **修正**: 必要に応じて、個人データを変更するか、個人データに対して他の要求されたアクションを実施します。

1. **制限**: さまざまなオンライン サービスに対するライセンスを削除するか、または可能な場合は目的のサービスをオフにすることで、個人データの処理を制限します。 また、Microsoft のクラウドからデータを削除して、オンプレミスの場所や別の場所にデータを保持することもできます。

1. **削除**: Microsoft のクラウドに存在する個人データを完全に削除します。 [Microsoft アカウント用の個人データの削除](gdpr-dsr-delete-msa.md)に関する詳細。 [Microsoft アカウントの削除](gdpr-dsr-accountclose-msa.md)に関する詳細。

1. **エクスポート**: 個人データの (コンピューターが判読できる形式の) 電子コピーを提供します。 [Microsoft アカウント用の個人データのエクスポートに関する詳細](gdpr-dsr-export-msa.md)。
