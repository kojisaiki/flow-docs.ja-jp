---
title: 電子メールのプロパティに基づいてフローを実行する | Microsoft Docs
description: 電子メールの件名、送信者のアドレス、受信者のアドレスなどのプロパティに基づいてフローを開始します。
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/08/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 94af3389301f40aa5caaa46eda98c8b1c9be0228
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689803"
---
# <a name="trigger-a-flow-based-on-email-properties"></a>電子メールのプロパティに基づいてフローをトリガーする
次の電子メール プロパティの 1 つまたは複数が指定した条件を満たすときに実行されるフローを作成するには、**[新しい電子メールが届いたとき]** トリガーを使用します。

| プロパティ | 使用する場合 |
| --- | --- |
| フォルダー |特定のフォルダーに電子メールが届くたびにフローをトリガーします。 このプロパティは、電子メールをさまざまなフォルダーに振り分けるルールを使用している場合に役立ちます。 |
| 宛先 |電子メールの送信先アドレスに基づいてフローをトリガーします。 このプロパティは、異なる電子メール アドレスに送信された電子メールを同じ受信トレイで受信する場合に役立ちます。 |
| From (差出人) |送信者の電子メール アドレスに基づいてフローをトリガーします。 |
| Importance (重要度) |送信された電子メールの重要度に基づいてフローをトリガーします。 電子メールは高、標準、または低の重要度を指定して送信することができます。 |
| Has Attachment (添付ファイルを含む) |着信電子メール内の添付ファイルの有無に基づいてフローをトリガーします。 |
| Subject Filter (件名フィルター) |電子メールの件名に特定の語句がないかどうかを検索します。 その後、検索結果に基づく*アクション*が実行されます。 |

> [!IMPORTANT]
> 各 [Microsoft Flow プラン](https://flow.microsoft.com/pricing/)には実行クォータが含まれています。 可能なかぎり、常にフローのトリガーのプロパティを確認してください。 これにより、実行クォータが不必要に使用されることを回避できます。 条件でプロパティをチェックすると、定義したフィルター条件が満たされない場合でも、すべての実行がプランの実行クォータについてカウントされます。 

たとえば、条件で電子メールの *差出人* アドレスをチェックすると、関係する *差出人* アドレスであるかどうかに関わらず、すべての実行がプランの実行クォータについてカウントされます。
> 
> 

次のチュートリアルでは、**[新しい電子メールが届いたとき]** トリガーですべてのプロパティを照合します。 詳細については、[課金についてよく寄せられる質問](billing-questions.md#what-counts-as-a-run)と[料金](https://ms.flow.microsoft.com/pricing/)のページを参照してください。

## <a name="prerequisites"></a>前提条件
* [Microsoft Flow](https://flow.microsoft.com) へのアクセス権を持つアカウント
* Office 365 Outlook アカウント
* [Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリ
* Office、Outlook、プッシュ通知サービスへの接続

## <a name="trigger-a-flow-based-on-an-emails-subject"></a>電子メールの件名に基づいてフローをトリガーする
このチュートリアルでは、新しい電子メールの件名に「lottery」(宝くじ) という語が含まれる場合に携帯電話にプッシュ通知を送信するフローを作成します。 その後、そのような電子メールには *開封済み* のマークが付けられます。

>[!NOTE]
>このチュートリアルではプッシュ通知を送信しますが、ワークフローの必要に適したその他のアクションを自由に使用できます。 たとえば、電子メールの内容を、Google スプレッドシート、または Dropbox に格納されている Microsoft Excel ファイルなどの別のリポジトリに格納できます。

それでは開始しましょう。

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-inbox-folder](includes/sign-in-use-blank-select-email-trigger-and-inbox-folder.md)]

1. **[Subject Filter] (件名フィルター)** ボックスで、フローを使用して着信電子メールのフィルターを適用するテキストを入力します。
   
     この例では、件名に「lottery」(宝くじ) という語が含まれる電子メールに注目します。
   
    ![高度なオプション](./media/email-triggers/email-triggers-subject-text.png)

    [!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. 先ほど指定した **[件名フィルター]** に一致する電子メールが届いたときに受信するモバイル通知の詳細を入力します。
   
    ![通知の詳細](./media/email-triggers/email-triggers-4.png)

    [!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. フローに名前を付けます。 次に、ページ上部の **[フローの作成]** を選択して保存します。
   
    ![フローを保存する](./media/email-triggers/email-triggers-subject-notification.png)

おめでとうございます。 これで、件名に「lottery」(宝くじ) という語を含む電子メールを受信するたびにプッシュ通知を受信できます。

## <a name="trigger-a-flow-based-on-an-emails-sender"></a>電子メールの送信者に基づいてフローをトリガーする
このチュートリアルでは、特定の送信者 (電子メール アドレス) からの電子メールが届いた場合に携帯電話にプッシュ通知を送信するフローを作成します。 また、このフローではそのような電子メールに *開封済み* のマークが付けられます。

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-inbox-folder](includes/sign-in-use-blank-select-email-trigger-and-inbox-folder.md)]

1. 送信者の電子メール アドレスを **[差出人]** に入力します。 
   
     このアドレスから送信されたすべての電子メールに対してアクションが実行されます。
   
    ![電子メールのプロパティ](./media/email-triggers/email-triggers-from.png)

    [!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. 先ほど入力した電子メール アドレスからのメッセージが届いたときに受信するモバイル通知の詳細を入力します。
   
    ![通知の詳細](./media/email-triggers/email-triggers-sender-notification.png)

    [!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. フローの名前を指定した後、ページ上部の **[フローの作成]** を選択することによって保存します。
   
    ![フローを保存する](./media/email-triggers/email-triggers-sender-5.png)

## <a name="trigger-a-flow-when-emails-arrive-in-a-specific-folder"></a>電子メールが特定のフォルダーに届いたときにフローをトリガーする
アドレスなどの特定のプロパティに基づいて電子メールをさまざまなフォルダーに振り分けるルールを使用している場合は、この種類のフローを使用できます。

開始手順:

> [!NOTE]
> 電子メールを受信トレイ以外のフォルダーに振り分けるルールがまだ存在しない場合は、そのようなルールを作成し、テスト電子メールを送信することによって動作を確認します。
> 
> 

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-specific-folder](includes/sign-in-use-blank-select-email-trigger-and-specific-folder.md)]

1. 特定の電子メールをルーティングするフォルダーを選択します。 すべての電子メール フォルダーを表示するには、最初に **[Show Picker] (ピッカーの表示)** アイコンを選択します。これは、**[新しい電子メールが届いたとき]** カードの **[フォルダー]** ボックスの右側にあります。
   
    ![フォルダーを選択する](./media/email-triggers/email-triggers-2.png)

    [!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. 先ほど選択したフォルダーに電子メールが届いたときに受信するモバイル通知の詳細を入力します。 まだである場合は、通知サービス用の資格情報を入力します。
   
    ![通知の詳細](./media/email-triggers/email-triggers-folder-notification.png)

    [!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. フローの名前を指定した後、ページ上部の **[フローの作成]** を選択することによって保存します。
   
    ![フローを保存する](./media/email-triggers/email-triggers-7.png)

このチュートリアルで先ほど選択したフォルダーに振り分けられる電子メールを送信することによって、フローをテストします。

