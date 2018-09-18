---
title: 携帯電話からのフローの作成 | Microsoft Docs
description: テンプレートからフローを作成します。たとえば、指定したアドレスからメールを受け取るとプッシュ通知を送信するテンプレートから作成します
services: ''
suite: flow
documentationcenter: na
author: adiregev
manager: erikre
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/18/2016
ms.author: adiregev
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: f87320c61427957c02ff75675e4e15b938ac99f4
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44688331"
---
# <a name="create-a-flow-from-your-phone-by-using-microsoft-flow"></a>Microsoft Flow を使用した携帯電話からのフローの作成
テンプレートを使用して、携帯電話からフローを作成します。テンプレートを見つけるには、サービスの一覧から検索するか、カテゴリを参照するか、キーワードを指定します。 このトピックの手順では、マネージャーからメールを受け取るとプッシュ通知を携帯電話に送信するフローを作成します。

Microsoft Flow に慣れていない場合は、[概要を確認してください](getting-started.md)。

## <a name="prerequisites"></a>前提条件
* [Microsoft Flow のアカウント](sign-up-sign-in.md)。
* [サポートされているデバイス](getting-started.md#use-the-mobile-app)にインストールされた [Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリ。 このトピックのグラフィックは iPhone バージョンのアプリを示していますが、インターフェイスは Android デバイスまたは Windows Phone も似ています。
* このトピックで示すテンプレートを使用するには、以下も必要になります。
  
  * Office 365 の資格情報。
  * 携帯電話でプッシュ通知が有効になっていること。

## <a name="find-a-template"></a>テンプレートの検索
1. モバイル アプリを開き、画面下部にある **[Browse (参照)]** をタップします。
   
    ![[Browse (参照)] アイコン](./media/mobile-create-flow/browse-icon.png)
   
    テンプレートは、次のいずれかの方法で検索できます。
   
   * 画面上部にある検索ボックスでキーワードを指定する。
   * サービスの一覧でオプションをタップする。
   * 下へスクロールしてさまざまなカテゴリを表示して、任意のカテゴリのテンプレートをタップする。
     
       ![[Browse (参照)] タブ](./media/mobile-create-flow/browse-tab.png)
     
     このチュートリアルでは、マネージャーからメールを受け取るとプッシュ通知を送信するテンプレートを開きます。
2. サービスの一覧で、**[See sll (すべて表示)]** をタップします。
   
    ![サービスの一覧を表示](./media/mobile-create-flow/list-services.png)
3. **[Push notification (プッシュ通知)]** のアイコンをタップします。
   
    ![プッシュ通知](./media/mobile-create-flow/push-notifications.png)
4. 検索バーに「**email**」と入力し、マネージャーからメッセージを受け取るとプッシュ通知を送信するテンプレートをタップします。
   
    ![テンプレートの選択](./media/mobile-create-flow/choose-template.png)
5. 選択したテンプレートの詳細が示されている画面で、**[Use this template (このテンプレートを使用する)]** をタップします。
   
    ![テンプレートの確認](./media/mobile-create-flow/confirm-template.png)

## <a name="finish-the-flow"></a>フローの完了
1. メッセージが表示されたら、**[サインイン]** をタップし、Office 365 Outlook か Office 365 ユーザー、またはその両方の資格情報を指定します。
   
    ![Office 365 へのサインイン](./media/mobile-create-flow/office-signin.png)
   
    他のフローを作成するときと同じ接続を使用できます。
2. 右上隅で **[次へ]** をタップします。
   
    ![[次へ] をタップ](./media/mobile-create-flow/next.png)
   
    次の画面に、トリガー イベントと、その結果として実行されるすべてのアクションが表示されます。
   
    ![トリガー イベントとアクション](./media/mobile-create-flow/flow-structure.png)
   
    このテンプレートでは、新しいメールによりフローがトリガーされます。このフローでは、マネージャーのアドレスを含む情報を取得し、そのアドレスからメールを受け取るとプッシュ通知を送信します。 テンプレートの中には、カスタマイズしないと適切に動作しないものがありますが、このテンプレートはカスタマイズ不要です。
3. (省略可能) 画面上部で、フローに対して別の名前を入力します。
   
    ![フローの名前の変更](./media/mobile-create-flow/rename-flow.png)
4. 右上隅で **[Create (作成)]** をタップします。
   
    ![フローの作成](./media/mobile-create-flow/create-flow.png)
   
    フローが作成され、そのフローを一時停止または削除するまで、マネージャーからのメールがチェックされます。

## <a name="next-steps"></a>次のステップ
* [フロー アクティビティを監視](mobile-monitor-activity.md)します。
* [フローを管理](mobile-manage-flows.md)します。

