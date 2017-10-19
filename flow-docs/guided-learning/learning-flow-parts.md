---
title: "Microsoft Flow の構成要素 | Microsoft Docs"
description: "Microsoft Flow のさまざまな要素とそれらの関連性を確認します。 テンプレートを使って、またはゼロから新しいフローを作成します。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: 9U8jMRO-Jv0
courseduration: 9m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 6a7fe2d56c7bc3b2253b675ce26f3f29042a7a71
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="building-blocks-of-microsoft-flow"></a>Microsoft Flow の構成要素
Microsoft Flow の基本について理解できたところで、**Microsoft Flow ツアー**に進みましょう。 テンプレートからフローを作成する方法とゼロからフローを作成する方法を簡単に説明します。

## <a name="check-out-the-templates"></a>テンプレートを見る
flow.microsoft.com で、ページの一番上にある **[テンプレート]** リンクをクリックすると、いくつかのテンプレートが表示されます。自分の Web サービスでそれらのテンプレートをすぐに利用できます。 これらのアプリを試し、**Microsoft Flow で何ができるか**、ビジネスにどのように役立つかを理解してください。

![Flow のテンプレート](./media/learning-flow-parts/template-list.png)

テンプレート フローはそれぞれ、特定の目的のために設計されています。たとえば、何かが発生したときに通知を受け取る、サービス間で新しいファイルをコピーする、SharePoint 承認を追跡するなどです。 これらのテンプレートは**すぐに使用できます**。  必要な作業は、**テンプレートを構成**し、フローを自分のアカウントに追加することだけです。 **[このテンプレートを使用]** をクリックし、必要なサービスにサインインし、続くフォームに記入します。  たとえば、これはテンプレートから作成したフローですが、SharePoint リストが変更されたときに電子メール通知を送信します。 

![Flow のテンプレートの例](./media/learning-flow-parts/example-template.png)

テンプレートは数百種類用意されています。**Microsoft Flow for web** または **Microsoft Flow for mobile** で検索できます。

![Flow for web と Flow for mobile](./media/learning-flow-parts/flow-web-mobile.png)

## <a name="create-a-flow-from-scratch"></a>ゼロからフローを作成する
テンプレートからフローを作成する方法について紹介しましたが、自動化する作業に適したテンプレートが見つからない場合はどうすればよいでしょうか。 **フローはゼロから作成する**ことができます。  ゼロからフローを作成する場合は、空のキャンバスから始め、**サービス、トリガー、アクション**を追加してフローを構築します。  

![空のフロー](./media/learning-flow-parts/flow-from-blank.png)

## <a name="building-blocks-of-a-flow"></a>フローの構成要素
フローの作成にテンプレートを使う場合も使わない場合も、フローには、フローチャートと同様に、特定の方法で連携する**構成要素**が含まれます。

* **サービス**は、フロー内のデータの情報源であり、宛先です。
* **トリガー**は、フローを開始するイベントです。
* **アクション**は、フローで遂行されるタスクです。
* **条件**は、フロー内の if/then ロジックの分岐を可能にします。
* **ループ**は、アクションを複数回繰り返すための機能です。

### <a name="services"></a>サービス
Microsoft Flow はさまざまな**アプリケーションとサービス**に接続できます。  たとえば、**Twitter**、**Github**、**Wunderlist**、**Office 365**、**Google Docs** などがあります。これらのサービスは Microsoft Flow にデータを提供する**情報源**であり、Microsoft Flow が行った作業の**宛先**です。  **flow.microsoft.com** の一番上にある **[サービス]** リンクをクリックすると、サービスの完全一覧が表示されます。

![Flow コネクタ](./media/learning-flow-parts/flow-connectors.png)

### <a name="triggers"></a>トリガー
すべてのフローが**トリガー**で開始します。  さまざまな種類のトリガーがあります。  その中には接続している Web サービスのイベントが含まれます。"**特定のユーザーがツイートを送信したとき**" や "**ファイルが Dropbox アカウントに保存されたとき**" などです。  ほかには組み込みのトリガーがあります。"**繰り返しスケジュールでフローを実行する**" や "**Web 要求に応えてフローを実行する**" などです。  最後に、手動のトリガーがあります。たとえば、**Microsoft Flow または Microsoft PowerApps** のボタンをクリックしてフローを起動します。  トリガーは、多くの場合、フロー内のアクションに、**発生したイベントに関する情報を渡します**。

![フローのトリガー](./media/learning-flow-parts/flow-triggers.png)  

### <a name="actions"></a>アクション
**アクション**は、フローがトリガーされた後に実際に**発生する**ことを表します。  たとえば、"**通知**" や情報源から宛先に "**データまたはファイルをコピーすること**" です。その他のアクションとしては、たとえば、"**ソーシャル メディアに投稿する**" や "**一定期間遅らせる**" などがあります。  アクションを利用し、他のアクションで使用する**データをサービスから取得する**こともできます。

![フローのアクション](./media/learning-flow-parts/flow-actions.png) 

### <a name="conditions"></a>条件
**条件**を利用することで、フローに意思決定を追加できます。  条件が評価されるとき、フローは "**はい**" パスと "**いいえ**" パスに分岐します。   たとえば、**Dropbox** に投稿した休暇の写真を **OneDrive** にコピーする場合、ファイル名に *vacation* という言葉が含まれているかどうかを確認し、含まれている場合、そのファイルを **OneDrive** にコピーするが、含まれていない場合、何もしないことを選択する条件を [**Dropbox new file**] \(新しいファイルを Dropbox に入れる) トリガーの後に作成します。

![フローの条件](./media/learning-flow-parts/flow-condition.png) 

### <a name="loops"></a>ループ
**ループ**を利用することで、あるアクションを複数回実行できます。あるアクションを繰り返し発生させたり、一群のアイテムの中でアイテムごとに 1 回だけ実行したりします。

## <a name="next-lesson"></a>次のレッスン
このトピックでは、Microsoft Flow の概要を説明しました。  **テンプレート**を閲覧し、**ゼロからのフロー作成**について考察しました。  アプリとサービス、フローを開始する**トリガー**、フロー内で行動を起こす**アクション**、決定を行う**条件**、フロー内で繰り返す**ループ**に接続することでフローを構築します。  **Microsoft Flow を知るための簡単な方法はテンプレートから始めて**、既に使用しているアプリとサービスにそれを結び付けることです。 

次に、このガイド付き学習コースでこれまで学習した内容をおさらいします。

