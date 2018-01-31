---
title: "API コネクタを開発する | Microsoft Docs"
description: "API を記述し、認証の種類を指定し、トリガーとアクションを作成して、テストします。"
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
ms.openlocfilehash: 8731e8a90a62bac4a05068386d23d2449952860b
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2018
---
# <a name="develop-an-api-connector-microsoft-flow"></a>API コネクタを開発する (Microsoft Flow)
コネクタを作成するには複数の手順があります。 最初に、[Microsoft Flow](https://flow.microsoft.com/) でページの右上にある **[設定]** ボタン (歯車アイコン) をクリックまたはタップします。 次に、**[Custom Connectors (カスタム コネクタ)]** をクリックまたはタップします。

![API コネクタの検索](./media/api-connectors-dev/finding-custom-apis.png)

## <a name="describe-your-api"></a>API を記述する
API コネクタを記述するには、HTTP API のインターフェイスを定義するための [OpenAPI 標準](https://swagger.io/)を使います。 既存の OpenAPI ファイルを使って作成を始めることも、OpenAPI ファイルを自動的に生成する [Postman Collection](https://www.getpostman.com/docs/collections) をインポートすることもできます。 

![API の定義の図](./media/api-connectors-dev/build-your-api-updated.png)

いずれかの API 記述で始めた場合、ウィザードのメタデータ フィールドは自動的に設定されます。 これらはいつでも編集できます。  

## <a name="build-security"></a>セキュリティを構築する
サービスでサポートされる認証の種類を選択し、追加の詳細を指定して、サービスとクライアントの間を ID が適切に流れるようにします。 

![セキュリティの図](./media/api-connectors-dev/security.png)

コネクタのセキュリティについて[詳しくはこちら](register-custom-api.md)をご覧ください。

## <a name="build-triggers-and-actions"></a>トリガーとアクションを作成する
1. コネクタのトリガーとアクションを作成するには、**[定義]** タブに切り替えます。 
   
    ![定義の図](./media/api-connectors-dev/definition.png)
2. ウィザードでは、新しい操作を追加したり、既存の操作のスキーマや応答を編集したりできます。 各操作の **[全般]** プロパティでは、コネクタのエンド ユーザー エクスペリエンスを制御できます。 各操作の種類について詳しくは、次のリンクをご覧ください。
   
   * [トリガー](customapi-webhooks.md) (PowerApps では表示されません)
   * [アクション](register-custom-api.md)
     
     Microsoft Flow の高度な機能の実装については、「[Microsoft Flow でのカスタム コネクタ用の OpenAPI 拡張](https://flow.microsoft.com/documentation/customapi-how-to-swagger/)」をご覧ください。 
3. 最後に、**[Create connector (コネクタの作成)]** をクリックまたはタップして、API コネクタを登録します。

ウィザードでは使用できない追加機能については、[condevhelp@microsoft.com](mailto:condevhelp@microsoft.com) にお問い合わせください。

## <a name="test-the-connector"></a>コネクタをテストする
提出する前に、以下の 1 つまたは複数の方法で API コネクタをテストします。 

* API コネクタの[テスト ウィザード](https://flow.microsoft.com/blog/new-updates-custom-api/)を使います。各操作を呼び出して、機能と応答スキーマを確認できます。
* Microsoft Flow のデザイナーでは、API コネクタを使ってフローを視覚的に構築できます。 このテスト方法では、ユーザー インターフェイスの機能とコネクタの機能を確認できます。
* PowerApps Studio では、数式バーを使って各操作を呼び出し、画面上のコントロールに応答をバインドできます。

このトピックでは概要を説明しました。詳細については、「[Microsoft Flow でカスタム コネクタを登録して使用する](register-custom-api.md)」をご覧ください。

