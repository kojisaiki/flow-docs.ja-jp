---
title: "API コネクタの概要 | Microsoft Docs"
description: "ISV および SaaS サービスの所有者は、コネクタを作成し、Microsoft の認定を受けることができます。"
services: 
suite: flow
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 62f8f8d0af72292a61324d75bd46f53d559b46a3
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="api-connector-overview-microsoft-flow"></a>API コネクタの概要 (Microsoft Flow)
**API コネクタ**は OpenAPI (Swagger) を利用した REST API のラッパーであり、基になっているサービスが [Microsoft Flow](https://flow.microsoft.com)、[PowerApps](https://powerapps.microsoft.com)、[Logic Apps](https://docs.microsoft.com/azure/logic-apps/) とやり取りすることを可能にします。 コネクタを使用することで、ユーザーは、アカウントを接続し、あらかじめ作成されている**トリガー**と**アクション**のセットを利用して、独自のアプリとワークフローを作成できます。

**独立系ソフトウェア ベンダー (ISV)** や **SaaS サービス所有者**は、コネクタを作成して、広範なビジネス シナリオや生産性シナリオをユーザーに提供できます。 コネクタを使うと、統合の限定されている設定を超えて、サービスが適用、発見、使用される範囲を拡大できます。

## <a name="requirements"></a>要件
コネクタを作成して提供するには、サービスが次の要件を満たしている必要があります。

* Microsoft Flow、PowerApps、Logic Apps にふさわしいビジネス ユーザー シナリオ
* 安定した REST API で公開されているサービス

## <a name="build-your-connector"></a>コネクタを作成する
API コネクタ作成の最初のステップは、完全に機能するカスタム コネクタを作成することです。 カスタム コネクタは API コネクタとまったく同じように動作しますが、使用できるのは作成者と、作成者のテナント内の特定のユーザーに制限されます。

コネクタを作成するには複数の手順があります。

![API コネクタの作成手順](./media/api-connectors-overview/authoring-steps.png)

API コネクタを開発する方法について[詳しくはこちら](api-connector-dev.md)をご覧ください。

## <a name="submit-for-certification"></a>認定を申請する
コネクタを作成した後は、その認定を申請します。 サード パーティ認定プロセスの一環として、Microsoft は公開する前にコネクタをレビューします。

このプロセスでは、Microsoft Flow および PowerApps でのコネクタの機能が検証され、技術およびコンテンツのコンプライアンスが確認されます。

認定と公開のためにコネクタを提出するプロセスについて[詳しくはこちら](api-connector-submission.md)をご覧ください。

## <a name="get-support"></a>サポートを受ける
オンボーディングと開発のサポートについては、[condevhelp@microsoft.com](mailto:condevhelp@microsoft.com) にメールでお問い合わせください。このアカウントは常に監視および管理されています。 開発者の問い合わせや問題は、適切なチームに迅速に引き渡されます。

