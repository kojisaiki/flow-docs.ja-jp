---
title: "作成の開始 | Microsoft Docs"
description: "カスタム コネクタの作成と共有、フローの埋め込みなどを行います。"
services: 
suite: flow
documentationcenter: na
author: bbarath
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/22/2016
ms.author: barathb
ms.openlocfilehash: d22193ac40b6eb8f90abf2ae5ced91b39c2faad9
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="start-to-build-with-microsoft-flow"></a>Microsoft Flow を使用した作成の開始
数ある中でも、次のように Microsoft Flow でアプリケーションを拡張します。

* カスタム コネクタを作成して接続する
* その API を Microsoft Flow のすべてのユーザーと共有する
* アプリ内からフロー エクスペリエンスを埋め込む
* ユーザーが Microsoft Flow を自身に最適な方法で操作できるようにすべての開発者 API を活用する

## <a name="prerequisites"></a>前提条件
* [flow.microsoft.com](https://flow.microsoft.com) のアカウント

## <a name="create-a-custom-connector"></a>カスタム コネクタを作成する
Microsoft Flow を使用して自動化できるようにしたい Web サービスがある場合は、最初に、カスタム コネクタを作成する必要があります。 カスタム コネクタを登録することで、必要な認証、サポートされるトリガーとアクション、アクションごとのパラメーターと出力など、Web API の特性が Microsoft Flow に提供されます。

カスタム コネクタを登録するには、[このチュートリアル](https://powerapps.microsoft.com/tutorials/register-custom-api/)に従ってください。 登録すると、他のユーザーがテストを手伝えるように組織の内部で共有することができます。

## <a name="share-a-custom-connector-with-all-microsoft-flow-users"></a>すべての Microsoft Flow ユーザーとカスタム コネクタを共有する
カスタム コネクタを十分にテストしたら、[このブログの投稿](https://flow.microsoft.com/blog/calling-all-saas-apps-now-you-can-build-your-own-connector-for-flow-and-logic-apps/)にあるようにレビュー プロセスを開始します。

* API と認証情報を表す OpenAPI ファイル
* コネクタのアイコン
* API の説明
* テンプレートによって API がどのように他のユーザーに役立つかに関する約 10 個のアイデア

この情報の送信後に、Microsoft Flow と Microsoft PowerApps で API の関数の評価が開始されます。

## <a name="embed-the-flow-experience-in-your-website-or-app"></a>Web サイトまたはアプリにフロー エクスペリエンスを埋め込む
最後に、アプリ内から Microsoft Flow を埋め込んで、ご利用のアプリと、Microsoft Flow がサポートする他のすべてのサービスをコンテキスト内で深く統合することができます。 たとえば、次のことが可能です。

* サービスに関連するすべてのテンプレートを参照し、ユーザーがテンプレートを選択できるようにする
* ユーザーがアプリに関連付けたにフローを管理する

アプリ内に Microsoft Flow を埋め込む方法の詳細については、[こちらのチュートリアル](embed-flow-dev.md)に従ってください。

