---
title: "API コネクタに関してよくあるご質問 | Microsoft Docs"
description: "要件、トリガー、その他の部分についての質問にお答えします。"
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
ms.date: 09/19/2017
ms.author: astay
ms.openlocfilehash: 1715700fa6a94bb35733865556a2c9be0ba3ce9f
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="api-connector-faq-microsoft-flow"></a>API コネクタについてよく寄せられる質問 (Microsoft Flow)
## <a name="requirements"></a>要件
**Q:** REST API を使用せずにコネクタを作成できますか? </br>
**A:** いいえ。コネクタを作成するには、サービスのための安定した HTTP REST API をサポートする必要があります。 

**Q:** コネクタを作成する際にどのようなツールを使用できますか? </br>
**A:** Azure には、API としてサービスを公開するために使用できる機能やサービスがあります。これには、ホスト用の Azure App Service や API Management などが含まれます。

**Q:** どのような種類の認証がサポートされていますか? </br>
**A:** サポートされている次の認証標準を使用することができます。

* [OAuth 2.0](https://oauth.net/2/)。[Azure Active Directory](https://azure.microsoft.com/develop/identity/) または、Dropbox、GitHub、および SalesForce などの特定のサービスが含まれます。
* 汎用 OAuth 2.0
* [基本認証](https://swagger.io/docs/specification/authentication/basic-authentication/)
* [API キー](https://swagger.io/docs/specification/authentication/api-keys/)

## <a name="triggers"></a>トリガー
**Q:** Webhook を使用しないでトリガーを作成できますか? </br>
**A:** いいえ。Azure Logic Apps と Microsoft Flow のカスタム コネクタでサポートされるのは、Webhook ベースのトリガーのみです。 他の実装パターンが必要な場合は、API の詳細を添えて [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com) にお問い合わせください。

## <a name="certification"></a>認定
**Q**: Microsoft パートナーや独立系ソフトウェア ベンダー (ISV) でない場合でも コネクタを作成できますか? </br>
**A**: はい。組織内部で使用するコネクタを登録することができます。ただし、コネクタを認定して一般公開する場合は、基になるサービスを所有しているか、API を使用するための明示的権限を示す必要があります。

## <a name="other"></a>その他
**Q:** API で動的ホストを使用します。 OpenAPI でこれらを実装するにはどうすればよいですか? </br>
**A:** カスタム コネクタでは動的ホストはサポートされません。 代わりに、開発とテストには静的ホストを使用してください。 コネクタを認定する場合は、Microsoft 連絡先担当者に動的実装についてお問い合わせください。

**Q:** Postman Collection V2 はサポートされていますか? </br>
**A:** いいえ。現在サポートされているのは Postman Collection V1 のみです。

**Q:** OpenAPI 3.0 はサポートされていますか? </br>
**A:** いいえ。現在サポートされているのは OpenAPI 2.0 のみです。

