---
title: Microsoft Flow のリージョンの概要 | Microsoft Docs
description: Microsoft Flow のリージョンに関する質問と回答の概要
services: ''
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/28/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 32301a87c33e5586280d822df8f6c381dbbf96a9
ms.sourcegitcommit: 3d0aecc89ed12b58f4b424c1c5a0654350f07d08
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "57885163"
---
# <a name="faq-for-regions-in-microsoft-flow"></a>Microsoft Flow のリージョンに関する FAQ
このドキュメントでは、Microsoft Flow についてよく寄せられる質問の一覧を示します。

## <a name="how-do-i-find-out-where-my-flow-is-deployed"></a>自分のフローがデプロイされる場所を確認する方法
フローは、[環境](environments-overview-admin.md)をホストする[リージョン](https://azure.microsoft.com/regions/)にデプロイされます。 たとえば、環境がヨーロッパ リージョンで作成されている場合、フローはヨーロッパのデータ センターに保存されます。

管理者は Microsoft Flow [管理センター](https://admin.flow.microsoft.com)にサインインすると、リージョンを識別できます。 **[環境]** タブには、既存のすべての環境とそのリージョンが一覧表示されます。

![環境を表示する](media/regions-overview/environments-list.png)

## <a name="what-regions-are-available"></a>どのリージョンを利用できますか。
* 米国
* ヨーロッパ
* アジア
* オーストラリア
* インド
* 日本
* カナダ
* 南米
* イギリス

## <a name="what-features-are-specific-to-a-given-region"></a>特定のリージョンに固有の機能はどれですか。
環境は複数の異なるリージョンに作成でき、その地理的な場所にバインドされます。 環境にフローを作成すると、そのフローはその地理的な場所のデータセンターにデプロイされます。 これは、共通データ モデル、フロー、接続、ゲートウェイ、アプリ、カスタム コネクタなど、その環境で作成するすべての項目に適用されます。

最適なパフォーマンスのためには、ユーザーに最も近いリージョンに環境を作成します。 たとえば、ユーザーがヨーロッパにいる場合は、ヨーロッパ リージョンに環境を作成します。 ユーザーが米国にいる場合は、米国リージョンに環境を作成します。

## <a name="gateways"></a>ゲートウェイ
ゲートウェイには次の制限があります。

* インド リージョンでは利用できません。
* 既定の環境でのみサポートされ、カスタム環境ではサポートされていません。

## <a name="is-microsoft-flow-available-in-national-clouds"></a>Microsoft Flow は、各国のクラウドで使用できますか。
いいえ、Microsoft Flow は、各国のクラウドでは使用できません。 各国のクラウドに対するサポートは、2018 年に開始される予定です。

## <a name="what-outbound-ip-addresses-are-used-in-each-region"></a>各リージョンではどのような送信 IP アドレスが使われますか。
「[制限事項と構成](limits-and-config.md)」を参照してください。

