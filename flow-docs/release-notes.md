---
title: リリース ノート | Microsoft Docs
description: Microsoft Flow リリースの一般的な問題と新機能
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/12/2018
ms.author: stepsic
ms.openlocfilehash: 4d88b0baee16fb0aeea24e2f2c84806595f21662
ms.sourcegitcommit: 753d52fa29d04f2eb774f7bec29b8d5793ccbb93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="release-notes"></a>リリース ノート
## <a name="top-questions"></a>よくある質問
1. フローでエラーが発生しました。 解決するにはどうすればよいですか。
   
   1. 障害を特定します。 最初に Web ポータルの上部にある通知アイコンを選ぶか、モバイル アプリで **[Activity]** (アクティビティ) タブを選びます。 フローが表示され、選択できるようになります。
   2. これでフローの詳細を調べられるようになりました。 赤い感嘆符アイコンの付いたステップを探すと、フローのエラー メッセージが表示されているはずです。
   3. エラー メッセージに応じて、フローを**編集**して修正できます。 [フローの一般的なエラーの解決方法については、こちらを参照してください](fix-flow-failures.md)。
2. 高度な条件または式はどのようにして使えばよいですか。
   
   * [条件の追加に関する記事](add-condition.md)をご覧ください。
   * フローに複数のケースが必要な場合は、既存の条件から **[条件の追加]** をクリックまたはタップします。
   * 高度な式を作成するには、[Logic Apps の関数](https://docs.microsoft.com/rest/api/logic/definition-language)を参照してください。
3. Office 365 ではライセンスはどのように機能しますか?
   
   * Office 365 ユーザーの場合は、Microsoft Flow for Office 365 プランでフル アクセスを取得します。 詳細については、[Microsoft Flow の料金プラン](https://flow.microsoft.com/pricing/)をご覧ください。
   * 管理者の場合は、Office 365 などで [Microsoft Flow ライセンス](organization-q-and-a.md)に関する情報をご覧ください。

## <a name="known-issues-and-resolutions"></a>既知の問題と解決策
1. [マイ サイト] にある、種類が *カスタム リスト* 以外の SharePoint リストがサポートされていません。 この問題を回避するには、標準的な SharePoint サイトにカスタム リストを作成します。
2. SharePoint リストの分類フィールドにフローを書き込むことはできません。 この問題が修正されるまでは、単純な文字列フィールドを使用することをお勧めします。
3. 選択したフォルダー内で入れ子になったフォルダーの中に追加されるファイルに対しては、ファイル トリガーが起動されません。

## <a name="whats-new"></a>新機能

### <a name="release-2018-02-09"></a>2018 年 2 月 9 日リリース

- **ゲートウェイの高可用性** - オンプレミス データ ゲートウェイで可用性の高いクラスターを作り、1 台のコンピューターが停止しても接続が維持されるようにします。
- **Apply to each の改善** - Flow プラン 1 または Flow プラン 2 によって、最大 100,000 個の項目が 1 回の実行で処理され、Apply to each ループで 50 件のアクションが並列処理されます。 

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/gateway-ha-increased-apply-to-each/)。

### <a name="release-2018-01-29"></a>2018 年 1 月 29 日リリース

- **Microsoft Teams 内の Flow** - Teams から、フローを作成して管理し、送受信した承認を見直し、Teams デスクトップ アプリまたは teams.microsoft.com で直接フローを起動できます。[詳細についてはここをお読みください](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/)。
- **共同編集通知** - 自分が所有しているフローが共同作業者によって変更されると、メール通知が届き、変更者と変更されたフローが伝えられます。
- **新しい式** - 新しい式セットが 2 つ追加されました。1 つは URL を解析するための式セットで、もう 1 つは JSON オブジェクトと連動する式セットです。
- **3 つの新しいコネクタ** - 今週は新しい Plumsail コネクタが 2 つあります。Plumsail SP と Plumsail Forms です。また、新しい kintone コネクタがあります。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/shared-notifications-and-expressions/)。

### <a name="release-2018-01-17"></a>2018 年 1 月 17 日リリース

- **Office 365 プロファイル情報** - ユーザーのプロファイルと写真を操作する新しいアクションを Office 365 ユーザー コネクタに追加しました。
- **文字列変数を増やす** - ループ内の文字列を増やし、テーブルやその他の一覧をビルドできます。
- **Infobip コネクタ** - Infobip は、音声通話や受信 SMS のトリガーなど、企業レベルの通信を可能にするサービスです。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/o365-profile-infobip/)。

### <a name="release-2017-12-20"></a>2017 年 12 月 20 日リリース

すべての Microsoft Flow リージョンで Microsoft Flow Analytics を利用できるようになり、環境内で実行されているフローの正常性を詳細に知ることができます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/announcing-microsoft-flow-analytics/)。


### <a name="release-2017-12-14"></a>2017 年 12 月 14 日リリース

- **Outlook Connector の機能強化** - ".eml" ファイルとしてのメールの保存、予定表の招待への自動応答、メール スレッドで言及されたときのフローのトリガーを行うことができるようになりました。
- **接続の機能強化** - Microsoft Flow はユーザーが最近使った接続を記憶し、新しく追加されたすべてのコネクタを表示します。
- **5 つの新しいコネクタ** - Azure Container Instances、Azure Kusto、Metatask、Microsoft To-Do、Plumsail Documents が追加されました。
- **HTTP の機能強化** - HTTP のアクションがチャンク エンコードをサポートするようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/outlook-connector-more/)。

### <a name="release-2017-12-05"></a>2017 年 12 月 5 日リリース

すべてのリージョンで、Microsoft Flow の起動パネルを利用できるようになりました。 このパネルでは、SharePoint のリストまたはドキュメント ライブラリ内でフローを実行するときに、フローに値を追加することができます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/introducing-flow-launch-panel-in-sharepoint-lists-and-libraries/)。


### <a name="release-2017-11-28"></a>2017 年 11 月 28 日リリース

- **管理されたメタデータ** - 管理されたメタデータ (分類とも呼ばれます) 型を使う SharePoint の列のデータを読み取ったり書き込んだりできます 。
- **配列への追加** - 新しい [配列変数に追加] アクションを使って、配列の末尾に項目を追加できます。
- **Tago** - Tago へのコネクタが新しく追加されました。外部データを提供する電子デバイスを簡単に接続し、コンテキスト分析を使ってより賢明な意思決定を下すことができます。
- **iPhone X** - iPhone X の全画面表示を使い、画像のアップロードの速度が向上した、新しいバージョンの Microsoft Flow アプリです。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/managed-metadata-tago/)。

### <a name="release-2017-11-09"></a>2017 年 11 月 9 日リリース

- **OneDrive for Business の統合** - [OneDrive for Business 内のフロー ボタン](https://flow.microsoft.com/blog/microsoft-flow-integration-in-one-drive-for-business-and-new-connector-actions/)を使って、選んだファイルまたはフォルダーに対するフローを作成またはトリガーできるようになりました。
- **プランナーのトリガー** - 新しいタスクが作成されたとき、自分にタスクが割り当てられたとき、またはタスクが完了したときに、フローを開始します。
- **SharePoint の添付ファイル** - SharePoint リスト項目の添付ファイルを処理 (添付ファイルの一覧表示、ダウンロード、追加、削除) します。
- **フロー管理コネクタ** - 環境内の他のフローの管理を自動化するフローを作成します (たとえば、アクセス許可をフローに自動的に追加します)。
- **4 つの新しいコネクタ** - Azure Custom Vision Service、D&B Optimizer、Enadoc、Derdak SIGNL4 が追加されました。 
- **新しいコネクタ アクション** - SQL クエリの実行、メール トリガーの取得の高速化、Azure AD での HTTP の任意のメソッドの使用など。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/planner-triggers-connector-improvements/)。

### <a name="release-2017-11-02"></a>2017 年 11 月 2 日リリース

- **監査ログ** - Microsoft Flow 監査イベントを、すべてのテナントの Office 365 セキュリティ/コンプライアンス センターで使用できるようになりました。
- **フロー ウィジェットの修正** - ウィジェットにボタンが読み込まれなくなる Flow モバイル アプリの問題を修正しました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/security-and-compliance-center/)。

### <a name="release-2017-10-19"></a>2017 年 10 月 19 日リリース

- **入れ子になった Apply to each** - 他の Apply to each コンテナー アクションに Apply to each アクションを追加し、フィルター処理や選択ができます。
- **日付と時刻のアクション** - ローカル時刻の取得、および時間の追加、減算、書式設定のための新しいアクション。
- **4 つの新しいコネクタ** - Content Moderator、Docparser、Microsoft Kaizala、Pitney Bowes Data Validation が追加されました。
- **接続エクスペリエンスの向上** - 接続が切れたときの Flow ポータルでの通知と、より充実した接続の詳細情報。
- **外出先コレクション** - [外出先で作業する](https://flow.microsoft.com/collections/onthego/)ための新しいテンプレート コレクション。
- **メール アドレスのボタン入力** - ユーザーがボタンを実行したときに、ユーザーからメール アドレスを収集します。
- **ファイルのボタン入力** - ユーザーがボタンを実行したときに、写真などのアップロードされたファイルをユーザーから取得します。
- **最初の実行と自動サインイン** - 自動サインインなど、モバイル アプリでの最初の実行エクスペリエンスが向上しました。
- **Microsoft Forms トリガーの高速化** - Forms でこれまでよりはるかに速くフローをトリガーできます (これまでは 1 時間に 1 回)。
- **セッション間でのボタン入力** - 携帯電話でトリガーされたボタンが、以前の入力を記憶しています。
- **モバイル アクティビティ フィード** - より詳細な実行の概要とトラブルシューティングの詳細を含めるように、アクティビティのフィードが強化されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/nested-apply-to-each/)。

### <a name="release-2017-10-03"></a>2017 年 10 月 3 日リリース

- **全員の承認が必要** - 承認要求を受け取ったすべてのユーザーによる承認を必要とします。
- **新しい OneDrive for Business アクション** - OneDrive for Business に格納されたファイルの PDF 生成および他の 4 つの新しいアクション。
- **Apache Impala コネクタ** - Apache Impala (incubating) はオープン ソースであり、Apache Hadoop のネイティブの分析データベースです。
- **フローの説明の追加** - フローを共有するときに同僚がフローの概要を理解できるように、フローの説明を追加します。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/all-must-approve-and-onedrive/)。

### <a name="release-2017-09-25---q3-update-for-microsoft-flow"></a>2017 年 9 月 25 日リリース - Microsoft Flow の第 3 四半期更新プログラム

- **最初のリリースでの SharePoint のより深い統合** - レビュー フロー用の新しい "標準" 送信と、初期リリース テナントのフローを実行するときに入力を収集するためのフロー パネルがあります。
- **Dynamics 365 for Customer Engagement** - フローが Dynamics 365 for Customer Engagement の UI に統合されました。
- **Microsoft セキュリティ センター** - フローが Microsoft セキュリティ センターに一覧表示され、HIPAA、ISO、SOC などの認定が示されます。
- **使用状況の分析** - すべてのフローには、基本的な使用状況分析機能を備えた Power BI ダッシュボードが埋め込まれています。
- **初期リリースでの監査ログ** - 初期リリース テナントのすべてのフロー管理イベントが、Office 365 セキュリティ/コンプライアンス センターに記録されます。
- **6 つの新しいコネクタ** - LinkedIn、Office 365 Groups、Skype for Business、Adobe Sign、Bizzy、Azure Log Analytics Data Collection が追加されました。
- **SQL トリガー** - SQL テーブルで新しい行が追加されると、または行が更新されると、フローが実行されます。
- **オンプレミスのカスタム コネクタ** - カスタム コネクタは、オンプレミスのデータ ゲートウェイを使って、ネットワーク上の内部エンドポイントに接続できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/q3-2017-update/)。

### <a name="release-2017-09-21"></a>2017 年 9 月 21 日リリース

- **フロー履歴のダウンロード** - フローの実行履歴を Excel で開く CSV ファイルとしてダウンロードします。
- **高度な定期実行** - 定期的なスケジュールを作成してフローをトリガーします (たとえば、平日にのみトリガーする)。
- **IntelliSense** - 式を入力すると、IntelliSense がパラメーターの候補を表示します。
- **4 つの新しいコネクタ** - Azure AD HTTP サービス、Amazon Redshift、Azure Event Grid Publish、FlowForma 用のコネクタが追加されました。
- **リンクの共有** - OneDrive ファイルまたは Azure Storage Blob の共有できるリンクを生成する新しいアクション。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/download-history-recurrence/)。


### <a name="release-2017-08-25"></a>2017 年 8 月 25 日リリース
* **SharePoint 用のドキュメント プロパティおよびその他** - [SharePoint ドキュメント ライブラリのプロパティの読み取りおよび設定](https://flow.microsoft.com/blog/support-for-sharepoint-document-library-properties/)を行い、SharePoint アイテムへのリンクなど追加のフィールドを使用できます。
* **フロー コレクション** - フロー コレクションは、ロールごと、または縦方向で整理された一連のテンプレート コレクションです。
* **ボタンの再共有** - ボタンを同僚と共有すると、同僚はそのボタンを他のユーザーと再共有することができます。
* **ボタンからのリストの収集** - ユーザーがボタンをタップしたときに、選択対象とするオプションのドロップダウン リストを定義できます。
* **7 つの新しいコネクタ** - AWeber、Azure Log Analytics、Azure Tables、DocFusion365、Azure Event Grid、Azure Event Hubs、StaffHub。 
* **Slack および MySQL の機能強化** - Slack でのチャネルの作成または結合がサポートされ、MySQL のデータベースへの書き込みを行うことができます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/button-updates-seven-connectors/)。

### <a name="release-2017-08-02"></a>2017 年 8 月 2 日リリース
* **個人、選択肢、参照フィールドに書き込む** - SharePoint の作成項目と更新項目[で](https://flow.microsoft.com/blog/setting-sharepoint-s-person-choice-and-lookup-fields/)個人、選択肢、参照フィールドを設定できるようになりました。
* **その他のアクション設定** - トリガーやアクションの実行で制御できる項目が増えました。たとえば、再試行ポリシーや改ページを構成できます。
* **4 つの新しいコネクタ** - Azure File Storage、Elastic Forms、Plivo、Video Indexer を利用できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/four-connector-action-settings/)。

### <a name="release-2017-07-27---q2-update-for-microsoft-flow"></a>2017 年 7 月 27 日リリース - Microsoft Flow の第 2 四半期更新プログラム
* **インポートとエクスポート** - 環境間で、あるいはテストから本稼働にフロー ソリューションをエクスポートしたり、インポートしたりできます。 
* **アクションで式を使用する** - アクションに式を入力し、使い方についてインライン ヘルプを表示できます。
* **拡大し、Azure Logic Apps になる** - フローを Azure Logic App リソースとして保存します。このリソースは Visual Studio や Azure Portal を介して展開できます。
* **管理上、見える範囲** - Microsoft Flow の利用状況をテナントにダウンロードすれば、どこでどのようにフローが使用されているのかを正確に把握できます。
* **Dynamics 365 のフロー** - Dynamics 365 for Operations & Financials, Business Edition 内でフローを使用します。
* **もっと簡単にシナリオを見つける** - コネクタでできることをすべて参照し、フロー作成のための出発点としてトリガーを使用します。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/q2-2017-update/)。

### <a name="release-2017-07-13"></a>2017 年 7 月 13 日リリース
* **テンプレート公開機能の強化** - 作成したフローとそのカテゴリを一般ギャラリーに公開します。
* **Outlook 予定表のイベントを取得する** - 予定表の 2 つの時刻の間にあるすべてのイベントを返す新しいアクションです。
* **新しいモバイル機能** - モバイル アプリでフローを必要に応じて実行し、失敗した実行を再提出します。
* **カスタム コネクタの動的ドロップダウン** - 動的ドロップダウン、ポーリング トリガーを作成し、カスタム コネクタをテストします。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/publishing-and-custom-connectors/)。

### <a name="release-2017-06-28"></a>2017 年 6 月 28 日リリース
* **言語設定の更新** - [設定] メニューによって、Microsoft Flow で使用する言語とリージョンの両方をカスタマイズできます。
* **5 つの新しいコネクタ** - Adobe Creative Cloud、Bing Maps、Bing Search、JotForm、および Freshservice に対するサポートを追加しました。
* **タイムアウトの構成** - 承認など、実行時間の長いアクションの "タイムアウト" 設定を事前に変更することで、フローが継続します。
* **Outlook にコメントを追加し、承認を求める** - 承認要求を受け取ったら、Outlook を終了せずにコメントを記入できます。
* **カスタム コネクタのブランドの色** - 背景に使用されるカスタム コネクタの色を入力できるようになりました。
* **チーム フローについて名前を付けて保存する** - チーム フローなど、任意のフローのコピーを作成します。
* **フローの削除に関する情報** - フローを削除する場合、そのフローで保留中のすべての実行が一覧表示されます。
* **[コネクタ] ページのフィルター処理** - [コネクタ] ページで希望するコネクタを検索し、コネクタの種類によってフィルター処理します。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/language-settings-3-connectors/)。

### <a name="release-2017-06-19"></a>2017 年 6 月 19 日リリース
送信済みであるすべての保留中の承認要求の状態を表示できるようになりました。 さらに、モバイル デバイスから直接、保留中のすべての承認を参照して操作することができます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/sent-requests-flow-mobile/)。

### <a name="release-2017-06-15"></a>2017 年 6 月 15 日リリース
* **コンテンツの変換** - HTML コンテンツをプレーン テキストに変換できる新しいコネクタ。HTML で書式設定された電子メールを処理するのに便利です。
* **3 つの新しいデータベース コネクタ** - MySQL、PostgreSQL、および Teradata の読み取り専用のサポートを追加しました。 これらのコネクタは、オンプレミスのデータ ゲートウェイ経由で接続されます。
* **その他の 3 つのコネクタ** - Azure Application Insights、Calendly、Teamwork Projects に接続します。
* **エラー処理のために視覚化を向上** - エラー発生後に実行される手順が赤い点線の矢印で表示され、容易に識別できるようになりました。
* **実行の詳細を示すウィンドウ** - フローが失敗した場合に、フローを修正するための有効な手順を含む新しいウィンドウが右側に表示されます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/seven-connectors-and-html/)。

### <a name="release-2017-06-04"></a>2017 年 6 月 4 日リリース
* **Windows Phone 用のバージョンの一般公開** - [ Windows Phone 用の Microsoft Flow モバイル アプリがリリースされ一般公開されました](https://flow.microsoft.com/blog/announcing-flow-windows-phone-app/)。
* **フローの失敗に関する電子メール** - フローが失敗すると、電子メールによる通知が届きます。 このような失敗に関する電子メールは、週に 1 回だけ送信されます。ユーザー側でメールの配信のオンまたはオフを設定できます。
* **テーブルに対するアクションを選択する** - 新しい [アクションの選択] を使用することで、テーブルに含める列セットを変更することができます。
* **Microsoft Forms コネクタ** - Microsoft Forms が Office 365 Education に新たに組み込まれました。これにより、教師および生徒は、迅速かつ容易に独自のクイズを作成し、調査、アンケート、登録などを行うことができます。
* **Office 365 Enterprise K1 プラン** - PowerApps と Microsoft Flow が特定のクォータで Office 365 Enterprise K1 プランに含められました。
* **HTTP ヘッダーの設定がより簡単に** - [アクションの選択] と同様に、アクションに対するテキスト ボックスに入力するだけで、ヘッダー名とヘッダー値を指定できます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/microsoft-forms-tables-flow-failures/)。

### <a name="release-2017-05-23"></a>2017 年 5 月 23 日リリース
* **Microsoft Teams コネクタ** - [Microsoft Teams](https://flow.microsoft.com/blog/introducing-the-microsoft-teams-connector-for-flow/) は、Office 365 のチャットベースのワークスペースです。複数の人々、会話、コンテンツをまとめる機能があり、チームに必要なツールも用意されているため、共同作業が簡単になり、より多くの成果を達成できるようになります。
* **iOS と Android のウィジェット** - Microsoft Flow ウィジェットは、ホーム画面から直接、簡単にすばやくボタンをトリガーできるようになるボタン ショートカットです。
* **"エラー処理" 手順の作成** - アクションが失敗した後に実行する 1 つまたは複数の手順を定義します。 たとえば、Dynamics 365 でレコードを作成するフローに失敗した場合に、すぐに通知を取得することができます。
* **整数および浮動小数点の変数** - 特定のロジック セットを実行する回数をカウントするために、フロー実行内のカウンターを初期化し、インクリメントまたはデクリメントします。
* **フローの詳細ページ** - **[マイ フロー]** 一覧からフローを選択すると、アクセス権を持つユーザー、実行履歴など、そのフローの詳細情報が表示されたページが開きます。
* **管理者のフロー実行クォータ** - 管理者は、通常の会社の実行クォータと比較して、組織全体のフロー実行の使用状況を監視し、クォータの内訳を取得して、クォータに影響しているライセンスを把握できるようになりました。
* **HTTP 要求トリガーの改善** - 要求トリガーにさまざまな HTTP メソッドを使用し、パス セグメントを追加できます。
* **2 つのパートナー コネクタ** - Microsoft Flow は、電子メール解析サービスの Parserr、およびオフラインフォーム サービスの Cognito Forms に接続できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/error-handling/)。

### <a name="release-2017-05-12"></a>2017 年 5 月 12 日リリース
* **SharePoint ドキュメント ライブラリの統合** - ドキュメント ライブラリの任意のファイルを選択して、フローを開始できます。たとえば、承認を得るためにマネージャーに送信したり、[さらに多くのこと](https://flow.microsoft.com/blog/flow-in-spo-document-libraries/)を実行できます。
* **Microsoft Planner コネクタ** - Microsoft Planner を使うと、よりよい結果を得るためにチーム、タスク、ドキュメント、会話を簡単にまとめることができます。
* **ライセンスの管理ビュー** - 管理者は、Microsoft Flow と PowerApps のすべてのライセンス (試用版と有料版) を Microsoft Flow 管理センターで表示できます。
* **PowerApps Community プラン** - PowerApps Community プランは、PowerApps、Microsoft Flow、Common Data Service の調査、学習、スキル向上のための個人向け無料プランです。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/planner-community-and-licenses/)。

### <a name="release-2017-05-09"></a>2017 年 5 月 9 日リリース
* **Azure AD コネクタ** - ユーザーの作成やグループへの追加など、管理者の操作を Microsoft Flow から実行するための新しいコネクタがあります。
* **Office 365 Outlook の機能強化** - 共有メールボックスでフローをトリガーしたり、フローで共有メールボックスにメールを送信したりできます。 自動返信を設定したり読んだりすることもできます。
* **カナダでの提供** - カナダでフローを作成できるようになりました。
* **カスタム API Webhook の作成** - カスタム コネクタの開発者は、Webhook でカスタム API にトリガーを追加できるようになりました。
* **管理センターでのフロー所有者の管理** - 環境の管理者は、Microsoft Flow 管理センターでフローの所有者を管理できます。
* **コネクタのドキュメントの参照** - [docs.microsoft.com にコネクタの完全なリファレンス](https://docs.microsoft.com/Connectors/)が公開されました。
* **2 つのパートナー サービス** - Nexmo と Paylocity という 2 つの新しいパートナー サービスがリリースされました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/canada-mailboxes-aad)。

### <a name="release-2017-04-27"></a>2017 年 4 月 27 日リリース
* **並列ステップでのフロー構築** - 並列実行によりフローを作成します。2 つ以上のステップを同時に実行できることになります。
* **新しく 5 つのサービスをサポート** - 新しい 5 つのサービスとは、承認、ベンチマーク電子メール、カプセル CRM、LiveChat、Outlook Customer Manager です。
* **操作の再試行を監視** - Microsoft Flow はサービスでエラーがある場合に再試行します。 自動再試行の回数と、その詳細を確認できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/parallel-actions/)。

### <a name="release-2017-04-17---q1-update-for-microsoft-flow"></a>リリース 2017 年 4 月 17 日 - Microsoft Flow の第一四半期更新プログラム
* **最新の承認操作** - 承認者が Microsoft Flow モバイル アプリ、または Microsoft Flow Web サイトの統合承認センターから安全に承認できるワークフローを作成できます。
* **チーム フローが標準で利用可能** - チーム フローが標準で利用可能になり、複数のユーザーがフローとチーム フローを同時に所有して管理できるようになりました。
* **Microsoft Flow のコネクターの構築** - すべてのユーザーが自分の Microsoft Flow コネクターを無料で送信して、他のユーザーが使用できるようになりました。
* **"無駄を省いた" デザイナー** – 特定のテンプレートでは、新しいバージョンのデザイナーにより、フローの作成に必要なフィールドのみが表示されるようになり、操作が簡略化されます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/q1-2017-update/)。

### <a name="release-2017-04-11"></a>2017 年 4 月 11 日リリース
* **テーブルおよび一覧を構築する新しいアクション** - アイテムの一覧を処理することができる、New Create HTML Table、Create CSV Table、および Join のアクション (以前の Apply-to-each に代わるもの)。
* **任意の場所へのステップの挿入** - ドラッグ アンド ドロップをしなくても、ワークフローの任意の場所に新しいステップを挿入できるようになりました。
* **4 つの新しいサービス** - Flow では、10 から 8 の Scheduling、Act!、Inoreader、および Computer Vision API をサポートするようになりました。 Computer Vision API を使用すると、イメージを処理してテキスト コンテンツを取得したり (OCR と呼ばれる)、コンテンツに基づいてイメージに自動的にタグ付けしたりできます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/html-tables-csvs-computer-vision/)。

### <a name="release-2017-04-03"></a>2017 年 4 月 3 日リリース
* **Windows Phone ベータ版** - Windows Phone アプリのベータ プログラムで、Windows Phone にアプリのプレビューを入手できるようになりました。 [詳しくはこちら](https://flow.microsoft.com/blog/windows-phone-app-beta-is-now-available/)。
* **Muhimbi PDF** - Muhimbi PDF で Microsoft Word ファイルから PDF への変換、透かしの追加、文書のマージなどができるようになりました。 [詳しくはこちら](https://flow.microsoft.com/blog/convert-files-using-muhimbi/)。
* **物理ボタンからフローをトリガーする** - Shortcut Labs の Flic、The Button Corporation の Bttn という物理ボタン領域の 2 つの主要製品との提携を発表しました。 [詳しくはこちら](https://flow.microsoft.com/blog/physical-buttons/)。

### <a name="release-2017-03-22"></a>2017 年 3 月 22 日リリース
* **フローのコピーを作成する** - フローのコピーを作成して、下書きバージョンで作業したり、過去に作成したフローを複製したりできるようになりました。
* **2 つの新しいサービス** - タスクの作成と更新により ToDo リストを管理する Toodledo、カスタマー サービスとサポート チケットのプラットフォームを提供する Zendesk のサポートが追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/make-a-copy/)。

### <a name="release-2017-03-15"></a>2017 年 3 月 15 日リリース
* **ボタンを同僚と共有する** - 他のユーザーとフロー ボタンを共有することで、すべてのビジネス ユーザーが容易にクイック タスクを実行できるようになりました。
* **ホーム画面からボタンをトリガーする** - モバイル デバイスのホーム画面またはロック画面からのフロー ボタンへのショートカットにより、これまでよりも素早くフローをトリガーできます。
* **Microsoft Flow アプリのチーム フロー** - iOS または Android 用 Microsoft Flow アプリで、他の所有者がいるフローが表示されるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/button-sharing/)。

### <a name="release-2017-03-10"></a>2017 年 3 月 10 日リリース
* **カスタム コネクタのエクスペリエンスの向上** - Postman コレクションを使用して、カスタム コネクタの作成、動作の編集、追加、テストを行うことができるようになりました。
* **2 つの新しいサービス** - PowerApps Notifications と PivotalTracker のサポートが追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/new-updates-custom-api/)。

### <a name="release-2017-02-27"></a>2017 年 2 月 27 日リリース
* **フロー ボタンのトリガー** - フロー ボタンを Microsoft Flow Web サイトからトリガーできるようになりました。 フローの一覧を表示したら、[...] メニューを選択し、[今すぐ実行] コマンドを選択します。
* **5 つの新しいサービス** - Oracle Database、Intercom、FreshBooks、LeanKit および WebMerge のサポートが追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/trigger-flow-buttons-web/)。

### <a name="release-2017-02-21"></a>2017 年 2 月 21 日リリース
* **環境のフローを表示** - 環境の管理者は、特定の環境内のすべてのフローの詳細な一覧を表示できるほか、フローの有効化、無効化、および削除を行うことができます。
* **2 つの新しいサービス** - Azure Automation と Basecamp 2 のサポートが追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/managing-flow-resources-in-the-admin-center/)。

### <a name="release-2017-02-16"></a>2017 年 2 月 16 日リリース
* **5 つの新しいサービス** - Azure Data Lake、Bitbucket (GIT のリビジョン管理を使用するプロジェクト用の Web ベースのホスティング サービス)、Eventbrite、Infusionsoft および Pipedrive のサポートが追加されました。
* **カスタム HTTP 認証** - フロー デザイナーでは、カスタム HTTP エンドポイントで認証を使用することが可能になりました。
* **JSON メッセージの解析** - HTTP 要求のトリガーからの JSON データ、または HTTP アクションから返された JSON データを解析できます。
* **フロー実行のフィルター処理** - 実行されているフローやキャンセルされた実行の表示を含めたより具体的なオプションにより、フロー実行のフィルター処理が向上しました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/managing-flow-resources-in-the-admin-center/)。

### <a name="release-2017-02-06"></a>2017 年 2 月 6 日リリース
* **チーム フロー** - チーム フローを使うと、複数のユーザーが共同でフローを所有および管理でき、だれかが組織を離れた場合でも、作成したフローは引き続き実行できます。
* **カスタム コネクタの共有** - チーム フローなどのカスタム コネクタを共有し、組織内でまとめて管理できます。
* **Gmail および LUIS のサポート** - Gmail および Azure Cognitive Services の Language Understanding Intelligent Service に接続します。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/team-flows/)。

### <a name="release-2017-01-30"></a>2017 年 1 月 30 日リリース
* **フロー ボタンの入力** - フロー ボタンが実行時にユーザー入力を受け取れるようになり、フローの作成者はボタンがタップされたときに渡される情報を定義できます。
* **Outlook のタスクと HelloSign** - Outlook タスク サービスを使ってタスクを管理でき、HelloSign によりセキュリティで保護された電子署名が可能になります。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/button-user-inputs/)。

### <a name="release-2017-01-23"></a>2017 年 1 月 23 日リリース
* **サービスによる検索** - 各サービスのすべてのアクションを表示するためにトリガーまたはアクションを追加するときに、サービスごとに参照します。
* **ケースの切り替え** - 並列ロジックの複数の分岐を作成する Switch ブロックを追加します。
* **電子メール アクションの追加** - フラグ付きメールを処理する Office 365 Outlook および Outlook.com サービスの新しい機能です。
* **5 つの新しいサービス** - ローカルまたはネットワーク ファイル システムへの接続、支払いサービス ストライプ、IBM Informix、IBM DB2、および UserVoice です。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/search-by-service/)。

### <a name="release-2017-01-14"></a>2017 年 1 月 14 日リリース
* **実行の再送信** - 失敗したフローを修正して再び実行したい場合は、失敗した実行を再送信できます。
* **実行のキャンセル** - フローが動かなくなった場合、実行を明示的にキャンセルできるようになりました。
* **2 つの新しいサービス** - GoToTraining と GoToWebinar のサポートが追加されました。
* **モバイル リンク** - モバイル アプリから直接テンプレートを共有できるようになりました。Web サイトの先頭にアプリをすばやくダウンロードできるリンクが追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/managing-runs/)。

### <a name="release-2016-12-29"></a>2016 年 12 月 29 日リリース
Microsoft Flow でご利用いただけるサービスに DocuSign (電子署名とデジタル取引管理)、SurveyMonkey (Web ベース調査)、OneNote ノート作成アプリ (ビジネス アカウントのみ) が追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/final-2016-services/)。

### <a name="release-2016-12-20"></a>2016 年 12 月 20 日リリース
* **今すぐ実行** - 定期的な (繰り返し) トリガーをオンデマンドで開始できるようになりました。たとえば、レポートを毎日スケジュールしているとき、そのレポートを**今すぐ**実行することもできます。
* **6 つの新しいサービス** - MSN 天気、Medium、Google の連絡先、Buffer、Harvest、TypeForm に接続するフローを構築します。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/run-now-and-six-more-services/)。

### <a name="release-2016-12-14"></a>2016 年 12 月 14 日リリース
ボタンがトリガーされた場所、トリガーしたユーザー、時刻など、ボタン フローをトリガーするとき、貴重な情報を活用できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/button-trigger-tokens/)。

### <a name="release-2016-12-06"></a>2016 年 12 月 6 日リリース
* **ガイド付き学習の概要** - 順番が付いた一連のコースから始めます。コースは動画と文書の組になっており、Microsoft Flow の豊富で強力な機能を理解するのに役立ちます。
* **2 つの新しいサービス** - Flow では、カスタマー サポート ソリューションの Freshdesk とオンライン会議ツールの GoToMeeting を利用できるようになりました。
* **HTTP Webhook サポート** - フローを webhook のエンドポイントにできるようになりました。登録と登録解除を自動的に行います。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/guided-learning-and-two-services/)。

### <a name="release-2016-11-23"></a>2016 年 11 月 23 日リリース
* **Flow で Power BI アラートに対応** - Power BI データ アラートからフローをトリガーすることで、洞察力を行動に変えます。
* **モバイル アプリケーションの改善** - フローを、テンプレートの既存のエクスペリエンスから作成するだけでなく、一から作成できるようになりました。 フロー実行の表示時のパフォーマンスも改善されました。
* **8 つの新しいサービス** - Azure Resource Manager、Azure Queues、Chatter、Disqus、Azure Cosmos DB、Cognitive Services Face API、HipChat、Wordpress に接続できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/power-bi-and-eight-other-services/)。

### <a name="release-2016-11-15"></a>2016 年 11 月 15 日リリース
* **Microsoft Flow パートナー プログラム** - Microsoft Flow に認定パートナー プログラムが導入されました。世界中の Microsoft Flow とつながり、さまざまな会社の才能と経験を活用できます。
* **6 つの新しいサービス** - Asana、Campfire、EasyRedmine、JIRA、Redmine、Vimeo という 6 個のサービスを今週リリースします。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/partner-program-six-new-services/)。

### <a name="release-2016-10-31---general-availability"></a>2016 年 10 月 31 日リリース - 一般公開
* **価格とライセンス** - 無料プランと有料プランの両方を利用でき、Office 365 と Dynamics 365 にも含まれます。
* **Microsoft Flow 管理センター** - 新しい管理センターはエンタープライズ環境に対応します。 管理センターでは、組織内の環境を管理できます。
* **データ損失防止ポリシー** - 管理者は、データ損失防止ポリシーを作成してサービス間のデータ フローを制御できます。
* **Android での使用可能** - Microsoft Flow 携帯電話アプリは、iOS と Android の両方で使用できるようになりました。 アプリを使うと、通知を受け取り、活動を監視し、ボタンをタップしてフローを開始することができます。
* **新しいデザイナー エクスペリエンス** - ステップ間で受け渡される動的なコンテンツを検索できるようになり、必要なデータをいっそうすばやく参照できます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/announcing-ga/)。

### <a name="release-2016-10-26"></a>2016 年 10 月 26 日リリース
* **ボタン フロー** - いつでもどこでもトリガーできる数えきれないほどの操作があります。 ボタン フローでは、モバイル デバイスからボタンをクリックするだけで実行できます。
* **環境の通知** - 環境は、組織のフローを格納して管理するための個別のスペースです。 環境は地理を考慮して配置されるので、環境で保持されるフロー、アプリ、ビジネス データは、環境があるリージョンに存在します。
* **6 つの新しいサービス** - Bit.ly、Cognitive Services Text Analytics、Dynamics NAV、Dynamics 365 for Financials、Instapaper、Pinterest のサポートが追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/environments-for-makers/)。

### <a name="release-2016-10-16"></a>2016 年 10 月 16 日リリース
* **カスタム コネクタでさらに多くの認証の種類がサポートされるようになりました** - カスタム コネクタで API キー認証がサポートされるようになりました。また、OAuth 2.0 仕様全体をサポートする任意のサービスに対して認証できるようになりました。
* **3 つの新しいサービスがサポートされるようになりました** - Basecamp 3、Blogger、PagerDuty のサポートが追加されました。
* **デザイナーの機能強化** - パフォーマンスが向上したほか、すべてのアクションで [...] メニューから接続を更新および修正できるようになりました。また、フローの実行を終了するための "終了" と呼ばれる新しいステップが追加されました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/early-october-updates/)。

### <a name="release-2016-09-25"></a>2016 年 9 月 25 日リリース
携帯電話でフローを作成できるようになりました。 テンプレートが豊富に取り揃えられたギャラリーを閲覧したり、サービスの一覧を検索したり、テンプレート カテゴリを選択して詳細を絞り込んだりできます。 このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/mobile-creation/)。

### <a name="release-2016-09-22"></a>2016 年 9 月 22 日リリース
* **Microsoft Graph のユーザー選択ウィンドウ** - 新しい Microsoft Graph のユーザー選択ウィンドウが Microsoft Flow UI に直接統合され、適切な連絡先またはメール アドレスを選択できるようになりました。
* **Microsoft Dynamics AX のサポート** - フローの中から、Dynamics AX Online の操作データに対する操作 (レコードの新規作成からデータの照会まで) が可能になりました。
* **パートナーによる 2 つの新しいサービス** - フローから appFigures または Insightly を使用できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/more-september-updates/)。

### <a name="release-2016-09-14"></a>2016 年 9 月 14 日リリース
* **Web サイトまたはアプリへの埋め込み** - 開発者は、Microsoft Flow を Web サイトまたはアプリに直接埋め込んで、そのユーザーが個人またはプロフェッショナル タスクを簡単に自動化できるようにしました。
* **HTTP エンドポイントとしてのフローの使用** - フロー自体を HTTP API として使用できるようになりました。 フロー内には "要求" と呼ばれるトリガーがあります。"応答" カードを追加することで、着信要求に応答できます。
* **Todoist のサポート** - Todoist を使用すると、職場や家庭のすべてのプロジェクト全体を把握することができます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/extend-web-site-application/)。

### <a name="release-2016-09-01"></a>2016 年 9 月 1 日リリース
Microsoft Flow はだれでも利用できるようになりました。当初は、Office 365 Business または Office 365 Enterprise で使用されているような、職場または学校から提供されたメール アドレスのみにプレビューを公開していました。 本日、プレビューが公式に利用可能になり、どのようなメール アドレスを使用しているかにかかわらず、すべてのユーザーが自由に使用できるようになったことをお知らせいたします。 このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/available-for-everyone/)。

### <a name="release-2016-08-31"></a>2016 年 8 月 31 日リリース
* **条件の入れ子** - 1 つの条件内に 2 番目の条件 (3 番目の条件、4 番目の条件...) を追加できるようになりました。
* **Apply to each** - "Apply to each" ループを使用すると、繰り返しの対象となるリストを制御できます。
* **Do until** - "Do until" ループを使用すると、特定の条件が満たされるまでステップを繰り返すことができます。
* **配列のフィルター処理** - リスト内のすべての項目が定義した式と一致することを確認できる 1 つのネイティブ フィルター ステップがあります。
* **文字列変数の作成** - 文字列変数を作成できるようになりました。
* **スコープ** - スコープは、複数のアクションをグループ化するための簡単な方法です。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/build-advanced-flows/)。

### <a name="release-2016-08-27"></a>2016 年 8 月 27 日リリース
* **ステップに関するコメント** - コメントにより、個々のアクションに簡単に注釈を付けることができるため、フローに必要なことを容易に思い出すことができます。
* **Smartsheet のサポート** - 今週、Smartsheet に接続するためのサポートを追加しました。 Smartsheet は、クラウド上のシートでの共同作業を容易にするサービスです。
* **フロー作成時の UI の改善** - フロー名を前面中央に配置し、保存ボタンをページの上部に移動してアクセスしやすくしました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/add-comments-smartsheet/)。

### <a name="release-2016-08-18"></a>2016 年 8 月 18 日リリース
Microsoft Flow の統合を含む、新しい SharePoint Online の最新のリスト機能をプレビューできるようになりました。 このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/microsoft-flow-integration-with-sharepoint-modern-lists-preview/)。

### <a name="release-2016-08-13"></a>2016 年 8 月 13 日リリース
* **Visual Studio Team Services** - Flow を使用して、O365 のメール、Slack、Trello、Wunderlist などのさまざまなサービスに VSTS を接続できるようになりました。
* **SharePoint の機能強化** - SharePoint リストは、単純なオブジェクト (単一行のテキスト、日付と時刻など) から複雑なオブジェクト (ユーザー、グループ、参照、選択肢など) まで、幅広いデータ型をサポートします。
* **O365 Outlook 接続のテスト** - ユーザーが新しい O365 Outlook 接続を作成するたびに、接続がテストされ、接続が使用できる状態であるかどうかが確認されます。
* **ブール型コントロール** - さらに、ブール型入力フィールドに入力する値を明確にするために、ブール型コントロールも追加されました (たとえば、[When a new email arrives (新しいメールが届いたとき)] トリガーの [Has Attachments (添付ファイルあり)])。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/visual-studio-team-services-enhancements-to-sharepoint-and-o365-outlook-and-boolean-control/)。

### <a name="release-2016-08-08"></a>2016 年 8 月 8 日リリース
Microsoft Flow に統合された Microsoft Common Data Service のパブリック プレビュー。 このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/flow-and-common-data-model/)。

### <a name="release-2016-08-05"></a>2016 年 8 月 5 日リリース
* **オンプレミスの SharePoint** - SharePoint Online と同様に、定義済みのテンプレートを使用するかテンプレートを一から作成することで、オンプレミスの SharePoint のリストとドキュメント ライブラリに関するフローを作成できます。
* **デザイナーの情報バブル** - 各トリガーとアクションの機能の詳細を表示するために、フローの各ステップの上に情報バブルを追加しました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/sharepoint-on-premises-and-info-bubbles-2/)。

### <a name="release-2016-07-15"></a>2016 年 7 月 15 日リリース
* **4 つの新しいサービスの追加** - Google カレンダー、Google Tasks、YouTube、SparkPost に接続します。
* **アクションの名前変更** - アクションの名前変更により、異なるアクションを区別できるようになりました。
* **異なる期間の遅延** - 秒、分、時、または日の任意の数を選択できるようになりました。
* **使いやすいフォルダー ブラウザー** - フォルダー ブラウザーを簡略化しました。左側で選択すると、そのフォルダーが選択されるようになりました。また、右側で選択すると、そのフォルダーが開き、その内のサブフォルダーを選択できるようになります。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/new-google-services-rename-more/)。

### <a name="release-2016-07-08"></a>2016 年 7 月 8 日リリース
オンプレミスのデータ ゲートウェイを使用した、Microsoft Flow のためのオンプレミスの接続。 これにより、SQL Server に対するセキュリティで保護された接続を確立してフローと統合できます。 このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/on-premises-data-gateway/)。

### <a name="release-2016-07-02"></a>2016 年 7 月 2 日リリース
* **Google シートのサポート** - これまでの機能では Google ドライブと Excel の両方を使用することができました。今週からは Google シートのネイティブ サポートを追加しています。
* **テンプレートを使ってすばやく開始** - さらに、テンプレートから開始できるように最適化を行いました。 テンプレートに使用するアカウントをテンプレート ページで選択できるようになりました。
* **SharePoint と Office 365 の権限が失効しない** - Microsoft Flow によって Azure Active Directory ベースのサービスへのアクセスが自動的に更新されるようになったため、すべてのフローはパスワードが変更されても正しく動作します。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/more-june-updates/)。

### <a name="release-2016-06-20"></a>2016 年 6 月 20 日リリース
* **Microsoft Flow の新しいモバイル アプリの導入** - 本日、もう 1 つの主要なサービスについてお知らせします。自動化されたワークフローをいつでもどこでも管理、追跡、参照できるモバイル アプリが iOS 向けにダウンロード可能になりました (Android 向けアプリも近いうちにダウンロード可能になる予定です)。  
* **シングル サインオン** - シングル サインオンが実装されました。これにより、Office 365 のような他の Microsoft サービスと共に Microsoft Flow への認証を行うことができます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/welcome-to-flow-now-more-mobile/)。

### <a name="release-2016-06-18"></a>2016 年 6 月 18 日リリース
* **新しいメール サービス** - Microsoft Flow 内で個人または会社のメール アカウントに接続する必要なく、Microsoft Flow から直接メールを送信できるようになりました。
* **ポータルでの通知** - フローに問題が発生したときにポータルの上部に通知が表示されるようになりました。
* **ポータルのすべてのアクティビティ** - フローの Web サイトで新しい [アクティビティ] タブをクリックすることにより、すべてのフローのアクティビティを表示できるようになりました。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/mail-and-all-activity/)。

### <a name="release-2016-05-27"></a>2016 年 5 月 27 日リリース
* **サービス別のテンプレートの表示** - サポートされているすべてのサービスを (ログインせずに) 表示できるようになりました。 このページで各サービスの説明を読み、そのサービス用に提供されているテンプレートを確認できます。
* **カスタム コネクタの作成と使用** - PowerApps でカスタム コネクタを作成できるのと同様に、flow.microsoft.com で独自の API に接続することができます。
* **完成前のフローのテスト** - 開始アクションを実行した場合、フローを保存するたびに、フローの実行結果をページ内で直接確認できます。

このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/may-updates-to-microsoft-flow/)。

### <a name="release-2016-05-07"></a>2016 年 5 月 7 日リリース
Microsoft Project Online と Mailchimp の Mandrill の 2 つの新しいサービスを追加しました。 このリリースの[詳細や質問についてはこちらをご覧ください](https://flow.microsoft.com/blog/announcing-microsoft-flow-webinars/)。

### <a name="release-2016-04-27---public-preview"></a>2016 年 4 月 27 日リリース - パブリック プレビュー
[Microsoft PowerApps](https://powerapps.microsoft.com) の一環として Logic フローを使用すると、Microsoft Flow プレビュー リリースの新機能をいくつか使用できます。

* 多数のテンプレートのギャラリーを参照して、人気度、名前、または発行日順に並べ替えることができます。
* フローをカスタマイズした後、[独自のテンプレートをギャラリーに発行](publish-a-template.md)できます。
* フローのチェックと実行すべてについて、履歴を確認することができます。
* フローを保存するときに、トリガー アクションを実行するだけで、[実行中のフローを即座に確認](see-a-flow-run.md)できます。
* Flow に関する意見を交換したり[提案](https://go.microsoft.com/fwlink/?LinkID=787474)したりするための[新しいコミュニティ](https://go.microsoft.com/fwlink/?LinkID=787467)を利用できます。

## <a name="next-steps"></a>次のステップ
このリリース ノートまたは[よく寄せられる質問](frequently-asked-questions.md)に記載されていない問題がある場合は、[コミュニティに参加](https://go.microsoft.com/fwlink/?LinkID=787467)して質問するか、[サポートにお問い合わせください](http://go.microsoft.com/fwlink/?LinkID=787479)。

