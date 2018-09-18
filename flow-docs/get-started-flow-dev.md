---
title: カスタム コネクタの作成とフローの埋め込み | Microsoft Docs
description: カスタム コネクタの作成と共有、フローの埋め込みなどを行います。
services: ''
suite: flow
documentationcenter: na
author: bbarath
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2017
ms.author: barathb
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 21f35216231193f40c1a723dda62bb3a2ad1be59
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689642"
---
# <a name="start-to-build-with-microsoft-flow"></a>Microsoft Flow を使用した作成の開始

Microsoft Flow を使用してアプリケーションを拡張する方法をいくつか次に示します。

* カスタム コネクタを作成して接続します。
* すべての Microsoft Flow ユーザーとカスタム コネクタを共有します。
* アプリ内からフロー エクスペリエンスを埋め込みます。
* ユーザーが Microsoft Flow を自身に最適な方法で操作できるようにすべてのカスタム コネクタを強調表示します。

## <a name="prerequisites"></a>前提条件

* [Microsoft Flow](https://flow.microsoft.com) アカウント。

## <a name="create-a-custom-connector"></a>カスタム コネクタを作成する

Microsoft Flow から接続したい Web サービスがある場合は、最初に、カスタム コネクタを作成する必要があります。 カスタム コネクタを登録すると、必要な認証、サポートされるトリガーとアクション、アクションごとのパラメーターと出力など、Web サービスの特性が Microsoft Flow に提供されます。

このチュートリアルで、[カスタム コネクタを登録して使用する](https://powerapps.microsoft.com/tutorials/register-custom-api/)方法を理解してください。 カスタム コネクタの登録後は、テストのために組織内で共有することができます。

## <a name="share-a-custom-connector-with-all-microsoft-flow-users"></a>すべての Microsoft Flow ユーザーとカスタム コネクタを共有する

カスタム コネクタを完全にテストしたら、[レビュー プロセス](https://flow.microsoft.com/blog/calling-all-saas-apps-now-you-can-build-your-own-connector-for-flow-and-logic-apps/)を開始して、他のすべての Microsoft Flow ユーザーと共有するために Microsoft からの承認を受けてください。

レビュー プロセスに必要なものを次に示します。

* API と認証情報を表す OpenAPI ファイル。
* コネクタのアイコン。
* コネクタの説明。
* テンプレートによってコネクタがどのように他のユーザーに役立つかに関する約 10 個のアイデア。

この情報の送信後に、Microsoft Flow と Microsoft PowerApps で API の機能の評価が開始されます。

## <a name="embed-the-flow-experience-into-your-website-or-app"></a>Web サイトまたはアプリにフロー エクスペリエンスを埋め込む

アプリ内に Microsoft Flow を[埋め込んで](developer/embed-flow-dev.md)、ご利用のアプリと Microsoft Flow がサポートする他のすべてのサービスをコンテキスト内で深く統合することができます。 たとえば、次のことが可能です。

* サービスに関連するすべてのテンプレートを参照し、ユーザーがテンプレートを選択できるようにする。
* ユーザーがアプリに関連付けたフローを管理する。

## <a name="next-steps"></a>次のステップ

Microsoft Flow をアプリに[埋め込む](developer/embed-flow-dev.md)方法を確認してください。
