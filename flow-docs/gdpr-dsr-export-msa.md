---
title: Microsoft Flow での Microsoft アカウント (MSA) に対する GDPR データ主体のエクスポート要求 | Microsoft Docs
description: Microsoft Flow を使用して Microsoft アカウントに対する GPDR データ主体のエクスポート要求に応答する方法を説明します。
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 5/25/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: d03b2fff23fc313ebb7f8c12ce2835687f589516
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690769"
---
# <a name="responding-to-gdpr-data-subject-export-requests-for-microsoft-flow"></a>Microsoft Flow に対する GDPR データ主体のエクスポート要求への応答

Microsoft は、パートナーによる一般データ保護規則 (GDPR) への対応への協力の一環として、準備の参考となるようにこのドキュメントを作成しました。 このドキュメントでは、GDPR に対する Microsoft の対応について説明するだけでなく、Microsoft Flow を使用するときに GDPR コンプライアンスをサポートするために実行できる手順の例を示します。

## <a name="manage-export-requests"></a>エクスポート要求の管理

"*データ ポータビリティの権利*" では、データ主体は別のデータ コントローラーに送信できる電子形式 (つまり、"構造化された、一般的に使用される、マシンが読み取り可能で相互運用可能な形式") で、個人データのコピーを要求できます。

[Microsoft プライバシー ダッシュボード](https://account.microsoft.com/privacy/)または [Microsoft Flow](https://flow.microsoft.com/) を使用して、特定のユーザーの個人データを参照またはエクスポートします。

|個人データ|場所|
|-----------------|-------------------|
|製品とサービス アクティビティ|Microsoft プライバシー ダッシュボード|
|フロー|Microsoft Flow 作成者ポータル|
|実行履歴|Microsoft Flow 作成者ポータル|
|アクティビティ フィード|Microsoft Flow 作成者ポータル|
|接続|Microsoft Flow 作成者ポータル|

## <a name="export-product-and-service-activity"></a>製品とサービス アクティビティをエクスポートする

1. Microsoft アカウント (MSA) を使用して、[Microsoft プライバシー ダッシュボード](https://account.microsoft.com/privacy/)にサインインします。
1. **[アクティビティの履歴]** を選択します。

    ![[アクティビティの履歴]](./media/gdpr-dsr-export-msa/activityhistory.png) 使用するさまざまな Microsoft アプリケーションとサービスに対するアクティビティの履歴を参照できます。
1. **製品とサービス アクティビティ** データをエクスポートするには、**[Download your data]\(データをダウンロードする\)**、**[CREATE NEW ARCHIVE]\(新しいアーカイブを作成する\)** の順に選択します。

    ![データのダウンロード](./media/gdpr-dsr-export-msa/downloaddata.png)

1. **[App & service usage]\(アプリとサービス使用量\)**、**[アーカイブを作成]** の順に選択します。

    ![データのダウンロード](./media/gdpr-dsr-export-msa/create-archive.png)
1. 新しいアーカイブが作成されます。 **[ダウンロード]** を選択して、エクスポートした製品とサービス アクティビティ データを取得します。

    ![ダウンロード](./media/gdpr-dsr-export-msa/download.png)

## <a name="export-a-flow"></a>フローをエクスポートする

フローへのアクセス権があるエンド ユーザーは、次の手順を実行して、フローをエクスポートできます。

1. [Microsoft Flow](https://flow.microsoft.com/) にサインインします。

1. **[マイ フロー]** を選択し、エクスポートするフローを選択します。

1. **[詳細]** を選択し、**[エクスポート]** を選択します。

    ![フローのエクスポート](./media/gdpr-dsr-export/export-flow.png)

1. **[パッケージ (.zip)]** を選択します。

フローが zip 形式のパッケージとして使用可能になります。 詳しくは、[フローをエクスポートおよびインポートする方法](https://flow.microsoft.com/blog/import-export-bap-packages/)に関するブログ投稿をご覧ください。

## <a name="export-run-history"></a>実行履歴をエクスポートする

実行履歴には、フローに対するすべての実行リストが含まれます。 このデータには、トリガーとアクションに対するフローの状態、開始時刻、継続時間、および入力/出力データが含まれます。

フローへのアクセス権があるエンド ユーザーは、次の手順を実行して、このデータをエクスポートできます。

1. [Microsoft Flow](https://flow.microsoft.com/) にサインインします。
1. **[マイ フロー]** リンクを選択し、実行履歴をエクスポートするフローを選択します。
1. **[実行履歴]** ウィンドウで、**[すべて表示]** を選択します。

    ![実行履歴](./media/gdpr-dsr-export/run-history.png)

1. **[CSV のダウンロード]** を選択します。

    ![CSV のダウンロード](./media/gdpr-dsr-export/download-csv.png)

Microsoft Excel またはテキスト エディターで開いて結果を分析できるように、実行履歴が .csv ファイルとしてダウンロードされます。

## <a name="export-a-users-activity-feed"></a>ユーザーのアクティビティ フィードをエクスポートする

[Microsoft Flow](https://flow.microsoft.com/) では、アクティビティ フィードはユーザーのアクティビティ、障害、通知の履歴を示します。 ユーザーは、次の手順で自分のアクティビティ フィードを見ることができます。

1. [Microsoft Flow](http://flow.microsoft.com/) にサインインし、右上隅のベル アイコンを選択して、**[アクティビティをすべて表示]** を選択します。

    ![アクティビティ フィードの表示](./media/gdpr-dsr-export/show-activity-feed.png)

1. **[アクティビティ]** 画面で、結果をコピーし、Microsoft Word などのテキスト エディターに貼り付けます。

    ![アクティビティ フィードの表示](./media/gdpr-dsr-export/export-activity-feed.png)

## <a name="export-a-users-connections"></a>ユーザーの接続をエクスポートする

接続により、フローは API、SaaS アプリケーション、その他のサード パーティ システムに接続できます。 接続を表示するには次の手順のようにします。

1. [Microsoft Flow](http://flow.microsoft.com/) にサインインし、右上隅の歯車アイコンを選択して、**[接続]** を選択します。

    ![接続の表示](./media/gdpr-dsr-export/show-connections.png)
1. 結果をコピーし、Microsoft Word などのテキスト エディターに貼り付けます。
