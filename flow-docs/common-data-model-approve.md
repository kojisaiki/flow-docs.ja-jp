---
title: "Common Data Service を使用した承認ループの作成 | Microsoft Docs"
description: "Dropbox に追加されたファイルをレビュー担当者が承認または却下できるように連携するエンティティ、フロー、アプリを作成します。"
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/22/2016
ms.author: stepsic
ms.openlocfilehash: f56b109cc0263c8464d6d7475421ab32af8888d5
ms.sourcegitcommit: f3261717768177e03e825c0dd2e3ba736dc9b94d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="build-an-approval-loop-by-using-microsoft-flow-and-the-microsoft-common-data-service"></a>Microsoft Flow と Microsoft Common Data Service を使用した承認ループの作成
Common Data Service を使用すると、フローから独立しているデータベースに情報が格納されるフローを作成できます。 その最も良い例が、承認に関するものです。 承認の状態をエンティティに格納すると、フローはそれを基盤にして動作することができます。

この例では、ユーザーが Dropbox にファイルを追加したときに開始される承認プロセスを作成します。 ファイルが追加されると、それに関する情報がアプリに表示されます。ここで、レビュー担当者が変更を承認または却下できます。 レビュー担当者が変更を承認または却下すると、通知メールが送信され、却下されたファイルは Dropbox から削除されます。

このセクションの手順に従うと、以下のものが作成されます。

* **カスタム エンティティ**Dropbox に追加された各ファイルに関する情報と、ファイルの状態が承認済み、却下、保留中のいずれであるかが含まれます。
* **フロー**。このフローにより、Dropbox にファイルが追加されたときにカスタム エンティティに情報が追加され、ファイルが承認または却下されたときにメールが送信され、却下されたファイルが削除されます。 これらの手順は、このようなフローを一から作成する方法を示していますが、同様のフローをテンプレートから作成することもできます。
* Dropbox に追加されたファイルをレビュー担当者が承認または却下できる**アプリ**。 PowerApps を使用すると、カスタム エンティティのフィールドに基づいて自動的にこのアプリが生成されます。

**前提条件**

* [Microsoft Flow](sign-up-sign-in.md) と [PowerApps](https://powerapps.microsoft.com/tutorials/signup-for-powerapps/) にサインアップする。
* 「[Manage your connections (接続の管理)](https://powerapps.microsoft.com/tutorials/add-manage-connections/)」の説明に従って Dropbox および Office 365 Outlook への接続を作成する。

## <a name="build-the-entity"></a>エンティティを作成する
1. [powerapps.com](https://web.powerapps.com) にサインインします。
2. 既定で左側のナビゲーション バーが表示されない場合は、左上隅にある 3 本の横線のアイコンをクリックまたはタップします。
   
    ![左側のナビゲーション バーを開く](./media/common-data-model-approve/hamburger-icon.png)
3. 左側のナビゲーション バーで、**[管理]**、**[エンティティ]** の順にクリックまたはタップします。
   
    ![エンティティを管理する](./media/common-data-model-approve/manage-entities.png)
4. メッセージが表示されたら、**[自分のデータベースを作成]** クリックまたはタップします。
   
    ![データベースを作成する](./media/common-data-model-approve/create-database.png)
5. 右上隅の近くで、**[新しいエンティティ]** をクリックまたはタップします。
   
    ![エンティティを作成する](./media/common-data-model-approve/new-entity.png)
   
    ブラウザー ウィンドウが最大化されていない場合は、このボタンが別の場所に表示されることがあります。
6. **[エンティティ名]** で、名前を指定します。名前にはスペースを含めず、データベース内の他のエンティティと異なる名前にします。
   
    この例に正確に従うには、「**ReviewDropboxFiles**」と指定します。
   
    ![エンティティ名を指定する](./media/common-data-model-approve/entity-name.png)
7. **[表示名]** で、わかりやすい名前を指定します。
   
    ![表示名を指定する](./media/common-data-model-approve/display-name.png)
8. **[次へ]** をクリックまたはタップします。
   
    ![[次へ] ボタン](./media/common-data-model-approve/next-button.png)

## <a name="add-fields-to-the-entity"></a>エンティティにフィールドを追加する
1. 右上隅の近くで、**[フィールドの追加]** をクリックまたはタップします。
   
    ![フィールドを追加する](./media/common-data-model-approve/add-field.png)
2. フィールドの一覧の下部に表示される空白行で、**Approver** フィールドのプロパティを設定します  (これらのプロパティを設定しているときは、Tab キーを押して次の列に切り替えます)。
   
   * **[表示名]** 列に「**Approver**」と入力します。
   * **[名前]** 列に「**ApproverEmail**」と入力します。
   * **[種類]** 列で **[Email]** オプションをクリックまたはタップします。
   * **[必須]** 列でチェック ボックスをオンにします。
     
     ![Approver フィールド](./media/common-data-model-approve/approver-field.png)
3. 次の行で、**Status** フィールドのプロパティを設定します。
   
   * **[表示名]** 列に「**Status**」と入力します。
   * **[名前]** 列に「**Status**」と入力します。
   * **[種類]** 列で **[Text]** オプションをクリックまたはタップします。
   * **[プロパティ]** 列は、既定値のままにします。
   * **[必須]** 列でチェック ボックスをオンにします。
     
     ![Status フィールド](./media/common-data-model-approve/status-field.png)
4. 次の行で、**FileID** フィールドのプロパティを設定します。
   
   * **[表示名]** 列に「**File identifier**」と入力します。
   * **[名前]** 列に「**FileID**」と入力します。
   * **[種類]** 列で **[Text]** オプションをクリックまたはタップします。
   * **[プロパティ]** 列は、既定値のままにします。
   * **[一意]** 列でチェック ボックスをオンにします。
   * **[必須]** 列でチェック ボックスをオンにします。
     
     ![FileID フィールド](./media/common-data-model-approve/fileid-field.png)
5. **FileID** フィールドの右端にある省略記号 (...) をクリックまたはタップし、**[タイトル フィールドとして設定]** をクリックまたはタップします。
   
    ![タイトル フィールドを設定する](./media/common-data-model-approve/set-title-field.png)
6. 左下隅の近くの **[作成]** をクリックまたはタップします。
   
    ![エンティティを作成する](./media/common-data-model-approve/create-button.png)
7. (省略可能) エンティティの一覧が再表示されたら、ブラウザー ウィンドウを最大化し (まだ最大化していない場合)、**[種類]** 列ヘッダーをクリックまたはタップします。 一覧は、作成したばかりのエンティティなど、カスタム エンティティが先頭に表示されるように並べ替えられます。

## <a name="sign-in-and-create-a-flow"></a>サインインしてフローを作成する
1. [Microsoft Flow ポータル](https://flow.microsoft.com)を開きます。
2. ブラウザー ウィンドウをまだ最大化していない場合は最大化し、右上隅の近くの **[サインイン]** をクリックまたはタップします。
   
    ![Microsoft Flow の [サインイン] ボタン](./media/common-data-model-approve/signin-flow.png)
3. 右上のメニューで、powerapps.com でデータベースを作成した環境を選択します。
   
    **注**: 同じ環境を選択しなかった場合は、エンティティが表示されません。
4. 左上隅の近くの **[自分のフロー]** をクリックまたはタップします。
   
    ![[自分のフロー] ボタン](./media/common-data-model-approve/myflows-button.png)
5. 右上隅の近くの **[一から作成]** をクリックまたはタップします。
   
    ![一から作成ボタン](./media/common-data-model-approve/create-flow.png)

## <a name="start-when-a-file-is-added"></a>ファイルが追加されたときに開始する
1. **[他のトリガーを検索してください]** と表示されているボックスに「**Dropbox**」と入力するか貼り付けて、**[Dropbox - ファイルが作成されたとき]** をクリックまたはタップします。
   
    ![トリガーを作成する](./media/common-data-model-approve/create-trigger.png)
2. **[フォルダー]** でフォルダー アイコンをクリックまたはタップし、ファイルが追加されるフォルダーを参照します。
   
    ![フォルダーを選択する](./media/common-data-model-approve/folder-icon.png)

## <a name="add-data-to-the-entity"></a>エンティティにデータを追加する
1. **[新しいステップ]** をクリックまたはタップし、**[アクションの追加]** をクリックまたはタップします。
   
    ![アクションを追加する](./media/common-data-model-approve/add-action.png)
2. **[他のアクションを検索してください]** と表示されているボックスに「**Common Data Service**」と入力するか貼り付けて、**[Common Data Service - Create object (Common Data Service - オブジェクトの作成)]** をクリックまたはタップします。
   
    ![Common Data Service のオブジェクトを作成する](./media/common-data-model-approve/cdm-create-object.png)
3. **[The entity (エンティティ)]** で「**Review**」と入力するか貼り付けて、**[Review Dropbox files]** をクリックまたはタップします。
   
    ![エンティティを選択する](./media/common-data-model-approve/choose-entity-flow.png)
4. **[Title (タイトル)]** で、ボックス内をクリックまたはタップし、パラメーター トークンの一覧で **[ファイル名]** をクリックまたはタップして、そのトークンをフィールドに追加します。
   
    ![ファイル名トークンを追加する](./media/common-data-model-approve/add-filename-token.png)
5. **[Approver (承認者)]** で、ファイルのレビュー担当者の電子メール アドレスを入力するか貼り付けます。
   
    **注**: フローのテストをより簡単にするには、自分のアドレスを指定してください。 フローを実際に使用する準備ができたときに、後でアドレスを変更できます。
   
    ![承認者を追加する](./media/common-data-model-approve/add-approver.png)
6. **[Status (状態)]** で「**Pending**」と入力するか貼り付けます。
   
    ![既定の状態を追加する](./media/common-data-model-approve/add-default-status.png)
7. **[File Identifier (ファイル識別子)]** で、ボックス内をクリックまたはタップし、パラメーター トークンの一覧で **[ファイル識別子]** をクリックまたはタップして、そのトークンをフィールドに追加します。
   
    ![ファイル識別子トークンを追加する](./media/common-data-model-approve/add-file-identifier.png)

## <a name="check-whether-the-file-has-been-reviewed"></a>ファイルがレビューされたかどうかを確認する
1. **[Create object (オブジェクトの作成)]** アクションで、**[新しいステップ]**、**[さらに追加]**、**[Do Until の追加]** の順にクリックまたはタップします。
   
    ![Do Until を追加する](./media/common-data-model-approve/add-do-until.png)
2. **[Do until]** アクションの左上隅で、**[値の選択]** と表示されているボックス内をクリックまたはタップします。
   
    ![値を選択する](./media/common-data-model-approve/choose-value.png)
   
    **注**: ブラウザー ウィンドウが最大化されていない場合は、**[値の選択]** と表示されている上部のボックス内をクリックまたはタップします。
3. **[Create object (オブジェクトの作成) からの出力]** で **[Status]** をクリックまたはタップし、このパラメーター トークンをフィールドに追加します。
   
    ![Status トークンを追加する](./media/common-data-model-approve/add-status.png)
4. **[Do until]** アクションの中央近くにある一覧を開き、**[次の値に等しくない]** をクリックまたはタップします。
   
    ![次の値に等しくないを指定する](./media/common-data-model-approve/is-not-equal.png)
5. **[Do until]** アクションの右上隅で、**[値の選択]** と表示されているボックスに「**Pending**」と入力するか貼り付けます。
   
    ![監視する状態を指定する](./media/common-data-model-approve/do-until-not-pending.png)
   
    **注**: ブラウザー ウィンドウが最大化されていない場合は、**[値の選択]** と表示されている下部のボックス内をクリックまたはタップします。
6. **[Do until]** アクションの下部にある **[アクションの追加]** をクリックまたはタップします。
   
    ![do until 内でアクションを追加する](./media/common-data-model-approve/add-action-in-dountil.png)
7. **[他のアクションを検索してください]** と表示されているボックスに「**Common**」と入力し、**[Common Data Service - Get object (Common Data Service - オブジェクトの取得)]** をクリックまたはタップします。
   
    ![オブジェクトを取得する](./media/common-data-model-approve/get-object.png)
8. **[The namespace (名前空間)]** でデータベースをクリックまたはタップします。
9. **[The entity (エンティティ)]** で「**Review**」と入力するか貼り付けて、**[Review Dropbox files]** をクリックまたはタップします。
   
    ![エンティティを選択する](./media/common-data-model-approve/choose-entity-flow.png)
10. **[Object id (オブジェクト ID)]** で、ボックス内をクリックまたはタップし、**[ファイル識別子]** パラメーター トークンをクリックまたはタップして、それをフィールドに追加します。
    
     ![オブジェクト識別子を追加する](./media/common-data-model-approve/add-object-id.png)

## <a name="check-whether-the-item-has-been-approved"></a>項目が承認されたかどうかを確認する
1. **[Do Until]** アクションで、**[新しいステップ]**、**[条件の追加]** の順にクリックまたはタップします。
   
    ![条件を追加する](./media/common-data-model-approve/add-condition.png)
2. 条件の左上隅で、**[値の選択]** と表示されているボックス内をクリックまたはタップします。
   
    ![条件の左上隅](./media/common-data-model-approve/condition-upper-left.png)
   
    **注**: ブラウザー ウィンドウが最大化されていない場合は、**[値の選択]** と表示されている上部のボックス内をクリックまたはタップします。
3. **[Get object (オブジェクトの取得) からの出力]** で **[Status]** パラメーター トークンをクリックまたはタップし、フィールドに追加します。
   
    ![条件に状態を追加する](./media/common-data-model-approve/add-status-to-condition.png)
4. 条件の右上隅で、**[値の選択]** と表示されているボックスに「**Approved**」を入力するか貼り付けます。
   
    ![状態が承認済みに設定されているかどうかを確認する](./media/common-data-model-approve/status-equals-approved.png)
   
    **注**: ブラウザー ウィンドウが最大化されていない場合は、**[値の選択]** と表示されている下部のボックスに「**Approved**」を入力するか貼り付けます。

## <a name="send-notification-mail"></a>通知メールを送信する
1. **[はいの場合、何もしない]** で、**[アクションの追加]** をクリックまたはタップします。
   
    ![はいの場合のアクションを追加する](./media/common-data-model-approve/if-yes-action.png)
2. **[他のアクションを検索してください]** と表示されているボックスで、「**メールの送信**」を入力するか貼り付けて、**[Office 365 Outlook - 電子メールの送信]** をクリックまたはタップします。
   
    ![はいの場合、メールを送信する](./media/common-data-model-approve/if-yes-send-mail.png)
3. **[To (宛先)]** に、項目が承諾されたときに通知するユーザーのアドレスを入力するか貼り付けます。
   
    **注**: フローのテストをより簡単にするには、自分のアドレスを指定してください。 フローを実際に使用する準備ができたら、変更することができます。
   
    ![承認の受信者](./media/common-data-model-approve/approval-recipient.png)
4. **[Subject (件名)]** で、ボックス内をクリックまたはタップし、**[ファイル名]** パラメーター トークンをクリックまたはタップして、それをフィールドに追加します。
   
    ![電子メールの件名としてファイル名を指定する](./media/common-data-model-approve/subject-is-file-name.png)
5. **[Body (本文)]** で、「**項目が承認されました。**」と入力するか貼り付けます。
   
    ![承認メールの本文](./media/common-data-model-approve/approval-body.png)
6. **[いいえの場合、何もしない]** で、この手順の 1. ～ 5. の手順を繰り返します。ただし、電子メール メッセージの本文には「**項目が却下されました。**」と指定します。
   
    ![却下メールの本文](./media/common-data-model-approve/rejection-body.png)

## <a name="delete-rejected-files"></a>却下されたファイルを削除する
1. 却下メールのフィールドの下で、**[アクションの追加]** をクリックまたはタップします。
   
    ![削除アクションを追加する](./media/common-data-model-approve/add-delete-action.png)
2. **[他のアクションを検索してください]** と表示されているボックスで「**Dropbox**」と入力するか貼り付けて、**[Dropbox - ファイルの削除]** をクリックまたはタップします。
   
    ![Dropbox からファイルを削除する](./media/common-data-model-approve/dropbox-delete-file.png)
3. **[ファイル]** で、ボックス内をクリックまたはタップし、**[File identifier]** パラメーター トークンをクリックまたはタップして、それをフィールドに追加します。
   
    ![削除するファイルを識別する](./media/common-data-model-approve/identify-file-delete.png)

## <a name="save-the-flow"></a>フローを保存する
1. 画面の上部で、作成しているフローの名前を入力するか貼り付けて、**[フローの作成]** をクリックまたはタップします。
   
    ![フローを保存する](./media/common-data-model-approve/save-flow.png)
2. **[閉じる]** をクリックまたはタップし、**[完了]** をクリックまたはタップします。
3. Dropbox では、指定したフォルダーに少なくとも 2 つのファイルを追加します。1 つは承認をテストするためのファイル、もう 1 つは却下をテストするためのファイルです。

## <a name="build-the-app"></a>アプリをビルドする
1. [powerapps.com](https://web.powerapps.com) にサインインし、左側のナビゲーション バーの下部の **[新しいアプリ]** をクリックまたはタップします。
   
    ![ブラウザーでアプリを作成する](./media/common-data-model-approve/new-app-button.png)
2. 表示されるダイアログ ボックスで、Windows 用の PowerApps Studio と Web 用の PowerApps Studio のいずれかを開くオプションをクリックまたはタップします。
3. Windows 用の PowerApps Studio を開いた場合は、左側のナビゲーション バーの **[New (新規)]** をクリックまたはタップします。
4. **[Create an app from your data (データからアプリを作成する)]** で、**[Common Data Service]** タイルの **[Phone レイアウト]** をクリックまたはタップします。
   
    ![アプリを作成する](./media/common-data-model-approve/afd-cdm.png)
5. **[Search (検索)]** ボックスに「**Review**」と入力するか貼り付けます。
   
    ![エンティティを検索する](./media/common-data-model-approve/search-entities.png)
6. **[Choose an entity (エンティティの選択)]** で **[Review Dropbox Files]** をクリックまたはタップします。
   
    ![エンティティを選択する](./media/common-data-model-approve/choose-entity.png)
7. 右下隅の近くの **[Connect (接続)]** をクリックまたはタップします。
   
    ![[Connect (接続)] ボタン](./media/common-data-model-approve/connect-button.png)
8. 紹介ツアーの開始画面が表示されたら、ツアーを実行して PowerApps の概要を理解します (または、**[Skip (スキップ)]** をクリックまたはタップします)。
   
    ![紹介ツアー](./media/common-data-model-approve/quick-tour.png)
   
    ツアーは後でいつでも実行できます。実行するには、左上隅の疑問符アイコンをクリックまたはタップし、**[Take the intro tour (紹介ツアーを見る)]** をクリックまたはタップします。
9. (省略可能) 画面の下部にあるスライダーをドラッグして拡大すると、アプリが見やすくなります。
   
    ![ズーム コントロール](./media/common-data-model-approve/zoom-control.png)

## <a name="customize-the-app"></a>アプリをカスタマイズする
1. 右側のナビゲーション バーで、ヘッダーと説明が含まれているレイアウトをクリックまたはタップします。
   
    ![[Connect (接続)] ボタン](./media/common-data-model-approve/choose-layout.png)
2. **[BrowseScreen]** で検索バーのすぐ下をクリックまたはタップし、より大きなテキスト ボックス コントロールを選択します。
   
    ![ヘッダーを選択する](./media/common-data-model-approve/select-header.png)
3. 右側のウィンドウの下側の一覧で、下向き矢印をクリックまたはタップして一覧を開きます。
   
    ![ドロップダウンを開く](./media/common-data-model-approve/open-dropdown.png)
4. 下側の一覧で **[Title (タイトル)]** をクリックまたはタップし、追加されたファイルのファイル名を表示します。
   
    ![見出しデータを設定する](./media/common-data-model-approve/set-heading.png)
5. 右側のウィンドウで上側の一覧を開き、**[Status (状態)]** をクリックまたはタップして、各ファイルの状態を表示します。
   
    ![本文データを設定する](./media/common-data-model-approve/set-body.png)

## <a name="test-the-overall-solution"></a>ソリューション全体をテストする
1. PowerApps で左上隅の再生ボタンをクリックまたはタップし、プレビュー モードを開きます。
   
    ![プレビュー モードを開く](./media/common-data-model-approve/open-preview.png)
2. 一覧の最初のファイルの矢印をクリックまたはタップし、そのファイルの詳細を表示します。
   
    ![詳細画面を開く](./media/common-data-model-approve/open-details.png)
3. 右上隅の鉛筆アイコンをクリックまたはタップし、ファイルの詳細を変更します。
   
    ![編集画面を開く](./media/common-data-model-approve/edit-record.png)
4. **[Status (状態)]** ボックスに「**Approved**」と入力するか貼り付けます。
   
    ![ファイルを承認する](./media/common-data-model-approve/change-status.png)
5. 右上隅のチェック マーク アイコンをクリックまたはタップして変更を保存し、詳細画面に戻ります。
   
    ![変更を保存する](./media/common-data-model-approve/save-record.png)
   
    数分後に、ファイルが承認されたことを示す電子メールを受信します。
6. 右上隅の戻るボタンをクリックまたはタップして、参照画面に戻ります。
   
    ![参照画面に戻る](./media/common-data-model-approve/back-arrow.png)
7. 一覧のもう 1 つのファイルの矢印をクリックまたはタップし、そのファイルの詳細を表示します。
   
    ![詳細画面を開く](./media/common-data-model-approve/open-details.png)
8. 右上隅の鉛筆アイコンをクリックまたはタップし、ファイルの詳細を変更します。
   
    ![編集画面を開く](./media/common-data-model-approve/edit-record.png)
9. **[Status (状態)]** ボックスに「**Rejected**」と入力するか貼り付けます (または、**Aproved** や **Approoved** など、**Approved** 以外の任意の文字列)。
   
    ![ファイルを却下する](./media/common-data-model-approve/reject-file.png)
10. 右上隅のチェック マーク アイコンをクリックまたはタップして変更を保存し、詳細画面に戻ります。
    
     ![変更を保存する](./media/common-data-model-approve/save-record.png)
    
     数分後に、ファイルが却下されたことを示す電子メールを受信し、ファイルが Dropbox から削除されます。

