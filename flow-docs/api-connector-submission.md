---
title: "API コネクタとしての認定を得るために提出する | Microsoft Docs"
description: "認定されたコネクタは、Microsoft Flow、PowerApps、Logic Apps のすべてのユーザーが使用できるようになります。"
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
ms.openlocfilehash: 33283e1f682190f6aea02cb61a31cb43b42d5289
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2018
---
# <a name="submit-your-connectors-for-microsoft-certification"></a>Microsoft の認定を得るためにコネクタを提出する
Microsoft Flow、Azure Logic Apps および Microsoft PowerApps のすべてのユーザーがカスタム コネクタをパブリックに使用できるようにするには、公開のためのレビュー、検証、および承認を行う Microsoft にコネクタを提出します。 

## <a name="certification-criteria"></a>認定条件
| 機能 | 詳細 | 必須または推奨 |
| --- | --- | --- |
| Software-as-a-Service (SaaS) アプリ |Logic Apps、Flow、および PowerApps に十分適したユーザー シナリオに対応します。 |必須 |
| 認証の種類 |API は、OAuth2、API キー、または基本認証をサポートする必要があります。 |必須 |
| サポート |顧客が支援を受けられるように、サポートの連絡先を提供する必要があります。 |必須 |
| 可用性および稼働時間 |アプリの稼働時間が 99.9% 以上である必要があります。 |推奨 |
|  | | |

さらに、Microsoft パートナーまたは独立系ソフトウェア ベンダー (ISV) でない場合は、コネクタを認定して一般公開する際に、基になるサービスを所有しているか、API を使用するための明示的権限を示す必要があります。

認定する場合、コネクタを次の 2 つのフェーズで確認します。 

1. 機能の検証
   
    カスタム コネクタは以下について評価されます。
   
   * カスタム コネクタ ウィザードの定義セクションの無効な swagger または JSON エラー
   * ウィザードのテスト セクションのランタイムおよびスキーマ検証エラー
     
     その結果、各操作は、クライアント側のすべてのエラーについて、Flow、Logic Apps および PowerApps で十分にテストされます。
2. コンテンツの検証
   
    適切に記述されたコネクタでは、各エンティティに対してわかりやすい名前と説明が使用されます。 ここでは、Swagger を評価し、各操作、入力パラメーターおよび応答属性に以下が含まれていることを確認します。
   
   * [概要](https://docs.microsoft.com/azure/logic-apps/custom-connector-openapi-extensions#summary)
   * [説明](https://docs.microsoft.com/azure/logic-apps/custom-connector-openapi-extensions#description)
   * [表示情報](https://docs.microsoft.com/azure/logic-apps/custom-connector-openapi-extensions#visibility)

## <a name="nominate-and-submit-your-connector-to-microsoft-for-certification"></a>Microsoft の認定を得るためにコネクタを指名して提出する
認定を申請するには、以下の手順に従います。

1. **指名**
   
   1. [指名を送信します](https://go.microsoft.com/fwlink/?linkid=848754)。
   2. 受信した相互機密保持契約書とパートナー契約書に署名します。 
      Microsoft で作業を続行するにはこれらの署名済み契約書が必要になります。 
      この契約書でコネクタが認定条件を満たしているかどうかを確認できます。 
   3. コネクタが承認された場合は、Microsoft からオンボードの手順をお知らせします。
2. **レビュー**
   
   1. レビューのために指名担当者に次の情報を送信します。
      
      * API が記述されている OpenAPI ファイル
      * コネクタを表すアイコン ファイル (.png または .jpg)  (アイコンには、230 ピクセルの正方形内に収まる 160 以下のピクセル ロゴが必要です。 背景が色付きの白いロゴが推奨されます)。
      * アイコンの 16 進形式のブランドの色 (アイコン ファイルの色付きの背景と一致する必要があります)。
      * 検証用のテスト アカウント
      * サポートの連絡先
   2. さらに情報が必要な場合は、ご連絡いたします。
3. **公開**
   
    コネクタの機能とコンテンツを検証した後、すべての製品とリージョンに展開するためにコネクタをステージングします。 通常、認定と展開プロセスには最大で 3 週間かかります。
   
    既定では、すべてのコネクタは "Premium" として公開されます。 
    アプリが Azure で構築されている場合、Office 365 Enterprise プランのすべてのユーザーが使用できる "Standard" コネクタとしてリストされるようにコネクタを申請できます。 
    詳細については、指名担当者にお問い合わせください。

