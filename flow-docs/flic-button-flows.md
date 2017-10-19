---
title: "Flic ボタンでフローを開始する | Microsoft Docs"
description: "Shortcut Labs 社が提供する Flic と呼ばれる物理ボタンを使用してボタン フローを簡単に開始することができます。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/19/2017
ms.author: deonhe
ms.openlocfilehash: 518834103c1a17ef2f5af218eae43ccab4e5fda2
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="run-your-flows-by-pressing-a-flic-smart-button-preview"></a>Flic スマート ボタン (プレビュー) を押してフローを実行する
Shortcut Labs 社が提供する物理ボタン (Flic と呼ばれる) を押してフローをトリガーします。 たとえば、Flic を押すことで、作業時間の追跡、予定表のブロック、イベントへの来訪者のカウント、または地理的な場所の保存を行うことができます。

> [!IMPORTANT]
> フローを作成する前に、[Android](https://play.google.com/store/apps/details?id=io.flic.app) または [iOS](https://itunes.apple.com/us/app/flic-app/id977593793?ls=1&mt=8) 用の Flic モバイル アプリを使用して Flic のすべてのプロパティを構成します。
> 
> 

## <a name="prerequisites"></a>前提条件
Flics を Microsoft Flow と一緒に使用するためには次の前提条件を満たしておく必要があります。

* [Microsoft Flow](https://flow.microsoft.com) のアクセス権を持っている
* [Android](https://play.google.com/store/apps/details?id=io.flic.app) または [iOS](https://itunes.apple.com/us/app/flic-app/id977593793?ls=1&mt=8) 用の Flic モバイル アプリをダウンロード済みであり、このアプリを使用して 1 つまたは複数の Flic をペアリングしている。

## <a name="configure-flic-properties"></a>Flic のプロパティを構成する
Flic のモバイル アプリを使用して Flic のイベントをプログラミングします。 対象のイベントは次のとおりです。

* クリック (1 回の短押し)
* ダブルクリック (2 回の短押し)
* 押したまま (1 回の長押し)

このスクリーン ショットは、Flic 構成プロセスがどのようなものかを示すサンプルです。

![Flic を構成する](./media/flic-button-flows/configure-flic-actions.png)

Flic イベントを Microsoft Flow にリンクしたら、その Flic を、目的のフロー用のトリガーとして選択することができます。 このチュートリアルでは後でトリガーを選択します。

## <a name="create-a-flow-thats-triggered-by-a-flic"></a>Flic によってトリガーされるフローを作成する
このチュートリアルでは、コンサルタントが各クライアントで費やした時間を記録するフローを作成します。 コンサルタントはクライアントに到着したときに Flic を 1 回押し、クライアントを離れる直前にもう一度押します。 Flic を押すたびに、Flic が接続されているフローが実行されます。 フローにより、現在の時刻が Google スプレッドシートに保存され、電子メール通知が送信されます。 電子メールには、フロー実行に関する詳細情報が含まれています。

注: Flic モバイル アプリを使用してペアリングが行われていることを確認し、Microsoft Flow をトリガーするために 1 回以上の**クリック**操作を構成します。 このスクリーン ショットでは、Microsoft Flow をトリガーするために**クリック**操作を構成しています。 このチュートリアルでは後で、Flic が 1 回押された (クリックされた) ときにトリガーされるようにフローを構成します。

   ![Flic の構成](./media/flic-button-flows/flic-configured-for-flow.png)

それではフローの作成を開始しましょう。

### <a name="start-with-a-template"></a>テンプレートで開始する
1. [Microsoft Flow](https://flow.microsoft.com) にサインインします。
   
    ![サインイン](./media/flic-button-flows/sign-into-flow.png)
2. 検索ボックスに「**flic**」と入力し、検索アイコンを選択します。
   
    ![Flic を検索する](./media/flic-button-flows/search-flic.png)
3. **Flic スマート ボタンを使用して作業時間を追跡**テンプレートを選択します。
   
    ![テンプレートを選択する](./media/flic-button-flows/flic-templates.png)

### <a name="create-a-spreadsheet-in-google-sheets"></a>Google スプレッドシートでスプレッドシートを作成する
1. テンプレートの詳細を確認します。このテンプレートでは Google スプレッドシートのスプレッドシートが必要です。
   
   ![テンプレートの詳細を確認する](./media/flic-button-flows/flic-template-details.png)
2. Google スプレッドシートで、**ClickType** および **TimeStamp** という名前の列を含むスプレッドシートを作成します。
   
      ヒント: Google スプレッドシート内の列に名前を付けるには、列の上部に列名を入力します。 シートはスクリーン ショットのように表示されます。
   
   ![Google スプレッドシート](./media/flic-button-flows/flic-google-sheet.png)
   
   注: このシートはこのチュートリアルの後の方で使用します。

### <a name="add-the-flic-trigger-to-your-flow"></a>Flic トリガーをフローに追加する
1. テンプレートのサービスにサインインし、[**続行**] を選択します。
   
     [**続行**] は、テンプレート用の必要なすべてのサービスにサインインした後で有効になります。
   
    ![資格情報を入力する](./media/flic-button-flows/flic-template-services-sign-in.png)
2. [検索] ボックスに「**flic**」と入力し、[**Flic - When a Flic is pressed**]\(Flic - Flic を押したとき\) トリガーを選択します。
   
    ![Flic トリガーを検索する](./media/flic-button-flows/flic-search-trigger.png)
3. [**Flic - When a Flic is pressed**]\(Flic - Flic を押したとき\) カードの **Flic ボタン** リストから、使用する Flic を選択します。
4. **イベント** リストから**クリック**を選択して、Flic を 1 回押したときにフローがトリガーされるように指定します。
   
    ![Flic 操作を選択する](./media/flic-button-flows/select-flic.png)
   
   必要に応じて、**任意**を選択すると、各 Flic イベント (クリック、ダブルクリック、または押したままにする) でフローをトリガーするように指定できます。
   
   **ダブルクリック**を選択すると、Flic を 2 回短押したときにフローがトリガーされます。 **押したまま**を選択すると、Flic の長押しでフローがトリガーされます。
   
   他のフローを作成し、それらのフローを、**イベント** リストにある他のイベントを使用してトリガーすることができます。 たとえば、**ダブルクリック** イベントを使用すると、クライアントを離れた時刻を記録することができます。

### <a name="configure-the-sheet"></a>シートを構成する
   [**行の挿入**] カード: 

1. [**ファイル**] リストから、先ほど作成したスプレッドシートを選択します。
2. [**ワークシート**] リストからシートを選択します。
   
   注: シートを選択すると、[**行の挿入**] カードに 2 つのボックスが追加で表示されます。 これらのボックスは、先ほど作成したシート内の 2 つの列を表します。
3. [**ClickType**] ボックスを選択し、[**Click type**]/(クリックの種類/) トークンを選択します。
4. [**Timestamp**] ボックスを選択し、[**Click time**]/(クリック時刻/) トークンを選択します。
   
    ![Google スプレッドシート データを構成する](./media/flic-button-flows/flick-insert-row-card.png)

### <a name="confirm-the-email-settings-are-correct"></a>電子メールの設定が正しいことを確認する
1. [**メール通知を受け取る**] カードが次のスクリーンショットのようになることを確認します。
   
    ![メール通知を確認する](./media/flic-button-flows/email-settings.png)

### <a name="save-your-flow-and-test-it"></a>フローを保存してテストする
1. フローに名前を付けて保存する
   
    ![フローを保存する](./media/flic-button-flows/save.png)

フォローした場合は、Flic を 1 回押すとフローがトリガーされます。 フローはクリックの種類と現在の時刻をシートに記録し、電子メールをユーザーに送信します。

1. Flic を 1 回押します。
2. Google スプレッドシートでワークシートを開きます。 [**ClickType**] 列に "click" が、[**Timestamp**] 列に時刻が表示されているのを確認できるはずです。
   
    ![実行結果を表示する](./media/flic-button-flows/flic-google-sheet-after-run.png)
3. Microsoft Flow の Web サイトまたは Microsoft Flow モバイル アプリで実行結果を確認することもできます。 テストの実行を示すスクリーン ショットを次に示します。
   
    ![フローを保存する](./media/flic-button-flows/flic-test-run-results-portal.png)
4. フローを実行したときに受信した通知メールの本文は次のようになります。
   
    ![フローを保存する](./media/flic-button-flows/flic-email-body.png)

(任意) Flic を押したときに場所 (緯度と経度) が自動的に記録されるようにフローの機能拡張を検討します。

## <a name="more-information"></a>詳細情報
* [ボタン フローを共有する](share-buttons.md)
* ボタン フローの実行時に [ボタン トリガー トークン](introduction-to-button-trigger-tokens.md) を使用して現在のデータを送信する方法について説明します。
* [Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリをインストールします。

