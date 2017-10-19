---
title: "Microsoft Flow の概要 | Microsoft Docs"
description: "Microsoft Flow と、それを使ってできることについて説明します。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: kZs7lqgp4LU
courseduration: 5m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 63ecfabc6b91f3a12fffd6986187b6bbd254b6da
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="guided-learning-for-microsoft-flow"></a>Microsoft Flow のガイド付き学習
Microsoft Flow の**ガイド付き学習**にようこそ。 この自分のペースで進められるオンライン コースでは、Microsoft Flow について順番に説明します。Microsoft Flow に関する知識を積み上げることができます。

この**ガイド付き学習**コースには現在、「概要」セクションが用意されています。数週間後にコンテンツが追加される予定です。 このコースは、理解しやすい分量にわけて説明するように作られています。概念、詳細、例の順に学習する論理的な流れになっています。 図もふんだんに盛り込まれており、学習に役立ちます。

Microsoft Flow の**初心者**の場合、このコースで Microsoft Flow を学習できます。**上級者**の場合、理解が深まり、足りないところが補われます。 このコースが役立つことを望んでいます。今後も、コンテンツが追加されるのでご期待ください。

このガイド付き学習コースは、現在も**開発作業中**です。  コースの内容や、**学習したい他のトピック**について、**ご意見をお送りください**。

## <a name="what-is-microsoft-flow"></a>Microsoft Flow とは何ですか。
Microsoft Flow とは、オンライン **ワークフロー サービス**であり、最もよく使用されているアプリおよびサービス間のワークフローを自動化することにより、仕事を無駄なく効率的に行えるようになります。  Microsoft Flow は 100 を超えるサービスに接続でき、すべてはサインアップするとすぐに使うことができます。 Microsoft Flow には、外出先でワークフローを追跡するのに役立つモバイル アプリケーションや企業で使う管理環境もあり、Microsoft Flow を独自のアプリケーションに埋め込むことも可能です。

このコースでは、Microsoft Flow の概要と概念を説明した後、フローを構築して管理し、管理者として環境内のフローを制御する方法を示します。 Contoso Flooring Company という架空の会社で使うための情報とシナリオを提供します。  ユーザーのビジネスやユーザーのクライアントのビジネスでこのシナリオがどのように役に立つかを紹介します。

![フローの概念スケッチ](./media/learning-introducing-flow/flow-conceptual.png)

Microsoft Flow は**インターネット上のアプリケーション**に限定されません。  SharePoint や SQL Server など、**オンプレミス データ**をフローに含めることができます。

## <a name="what-you-can-do-with-microsoft-flow"></a>Microsoft Flow でできること
 Microsoft Flow を使うと、お気に入りのアプリケーションとサービスの間の**自動化されたワークフロー**を作成し、ファイルの同期、通知の受信、データ収集などを行うことができます。  [Microsoft Flow で利用できるアプリケーションとサービスの一覧](https://flow.microsoft.com/services/)は継続的に拡大しています。  Microsoft Flow で自動化できるタスクの例:

* 重要な通知または電子メールに瞬時に受信して応答する。
* 新しい潜在顧客を記録し、追跡し、フォローアップする。
* サービス間でのファイルのコピーを行う。
* ビジネスに関するデータを収集してチームに通知する。
* 承認を自動化する。

Microsoft Flow の一般的な用途は、**通知を受信する**ことです。 たとえば、営業のリードが Dynamics 365 または Sales Force に追加されるたびに、即座に、リードについてのメールを受け取ったり、携帯電話のモバイル アプリでプッシュ通知を受信したりできます。 **新しい営業リード**をフォローアップする優れた方法です。

また、Microsoft Flow を使ってファイルをコピーすることもできます。 たとえば、DropBox のフォルダーにファイルが追加されるたびに、SharePoint のフォルダーに自動的にコピーし、ファイルがあることを**チームに通知**できます。

ビジネスについてのユーザーの声を知りたい場合は、特定のハッシュタグでツイートが投稿されると**トリガー**する**フローを作成**できます。 フローはツイートの詳細をコピーし、SQL データベースや SharePoint リストだけでなく OneDrive でホストされている Excel ファイルに保存することもできます。 どれでも好みのものを選べます。 収集したデータを使って、そのデータを Power BI に接続し、傾向を把握し、データに関する質問をする**アクション**を作成できます。

最後に、Flow の最も一般的な使い方の 1 つは、**承認を自動化**することです。 たとえば、SharePoint リストを使って会社の承認を追跡している場合、承認ワークフローをトリガーできます。

詳しくは、**テンプレートのランディング** ページで**テンプレート**の一覧をご覧ください (これについては次のセクションで説明します)。 その一覧に表示されていないフローのすばらしいアイデアをお持ちですか?  問題ありません。  自分だけのフローを作成できます。また、それをコミュニティで紹介することもできます。

## <a name="creating-and-administering-flows"></a>フローを作成し、管理する
フローの作成および管理を行うには、Web アプリを使用することも、[Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリを使用することもできます。 いずれのプラットフォームを選択した場合でも、問題の診断やデータの同期などを簡単に実行できます。

* どこからでもフローのオン/オフを切り替える。
* フローが失敗したタイミングを確認する。
* 詳細な実行履歴レポートを確認する。
* 通知タイプ別に実行を表示する/絞り込む。

## <a name="next-lesson"></a>次のレッスン
これで Microsoft Flow の概要が理解できたので、次はフローの構成要素を確認します。

