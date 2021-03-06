---
title: Microsoft Flow での GDPR データ主体のエクスポート要求 | Microsoft Docs
description: Microsoft Flow を使用して GPDR データ主体のエクスポート要求に応答する方法を説明します。
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
ms.date: 4/24/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: e0f9b8e5b345b4dbc226cff2f42850bb126c09b3
ms.sourcegitcommit: 44bc9de9f06b64615731ceb60a4f46cfcd45b167
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727138"
---
# <a name="responding-to-gdpr-data-subject-export-requests-for-microsoft-flow"></a>Microsoft Flow に対する GDPR データ主体のエクスポート要求への応答

Microsoft は、パートナーによる一般データ保護規則 (GDPR) への対応への協力の一環として、準備の参考となるようにこのドキュメントを作成しました。 このドキュメントでは、GDPR に対する Microsoft の対応について説明するだけでなく、Microsoft Flow を使用するときに GDPR コンプライアンスをサポートするために実行できる手順の例を示します。

## <a name="manage-export-requests"></a>エクスポート要求の管理

"*データ ポータビリティの権利*" では、データ主体は別のデータ コントローラーに送信できる電子形式 (つまり、"構造化された、一般的に使用される、マシンが読み取り可能で相互運用可能な形式") で、個人データのコピーを要求できます。

Microsoft Flow では、特定のユーザーの個人データを検索およびエクスポートするために、次のエクスペリエンスが用意されています。

* **Web サイト アクセス:** [PowerApps 管理センター](https://admin.powerapps.com/)または [Microsoft Flow 管理センター](https://admin.flow.microsoft.com/)にサインインします。

* **PowerShell アクセス:** [PowerApps 管理者 PowerShell コマンドレット](https://go.microsoft.com/fwlink/?linkid=871804)。

|**顧客データ**|**Web サイト アクセス**|**PowerShell アクセス**|
|-----------------|------------------|-------------------|
|システム生成ログ|[Office 365 Service Trust Portal](https://servicetrust.microsoft.com/)|
|実行履歴|Microsoft Flow 作成者ポータル||
|フロー|Microsoft Flow 作成者ポータル||
|フローのアクセス許可| Microsoft Flow 作成者ポータルおよび Microsoft Flow 管理センター||
|ユーザーの詳細||PowerApps コマンドレット|
|接続|Microsoft Flow 作成者ポータル|PowerApps コマンドレット |
|接続のアクセス許可|Microsoft Flow 作成者ポータル|PowerApps コマンドレット |
|カスタム コネクタ|Microsoft Flow 作成者ポータル|PowerApps コマンドレット |
|カスタム コネクタのアクセス許可|Microsoft Flow 作成者ポータル|PowerApps コマンドレット |
|ゲートウェイ|Microsoft Flow 作成者ポータル|オンプレミス データ ゲートウェイ PowerShell コマンドレット|
|ゲートウェイのアクセス許可|Microsoft Flow 作成者ポータル|オンプレミス データ ゲートウェイ PowerShell コマンドレット|

## <a name="export-a-flow"></a>フローをエクスポートする

エンド ユーザーまたは自分自身にフローへのアクセス権を付与した管理者は、次の手順に従ってフローをエクスポートできます。

1. [Microsoft Flow](https://flow.microsoft.com/) にサインインします。

1. **[マイ フロー]** リンクを選択し、エクスポートするフローを選択します。

1. **[詳細]** を選択し、**[エクスポート]** を選択します。

    ![フローのエクスポート](./media/gdpr-dsr-export/export-flow.png)

1. **[パッケージ (.zip)]** を選択します。

フローが zip 形式のパッケージとして使用可能になります。 詳しくは、[フローをエクスポートおよびインポートする方法](https://flow.microsoft.com/blog/import-export-bap-packages/)に関するブログ投稿をご覧ください。

## <a name="export-run-history"></a>実行履歴をエクスポートする

実行履歴には、フローで発生したすべての実行の一覧が含まれています。 このデータには、トリガーとアクションに対するフローの状態、開始時刻、継続時間、および入力/出力データが含まれます。

エンド ユーザーまたは Microsoft Flow 管理センターでフローへのアクセス権を付与した管理者は、次の手順に従ってこのデータをエクスポートできます。

1. [Microsoft Flow](https://flow.microsoft.com/) にサインインします。
1. **[マイ フロー]** リンクを選択し、実行履歴をエクスポートするフローを選択します。
1. **[実行履歴]** ウィンドウで、**[すべて表示]** を選択します。

    ![実行履歴](./media/gdpr-dsr-export/run-history.png)

1. **[CSV のダウンロード]** を選択します。

    ![CSV のダウンロード](./media/gdpr-dsr-export/download-csv.png)

Microsoft Excel またはテキスト エディターで開いて結果をさらに分析できるように、実行履歴が .csv ファイルとしてダウンロードされます。

## <a name="export-a-users-activity-feed"></a>ユーザーのアクティビティ フィードをエクスポートする

[Microsoft Flow](https://flow.microsoft.com/) では、アクティビティ フィードはユーザーのアクティビティ、障害、通知の履歴を示します。 すべてのユーザーが、次の手順で自分のアクティビティ フィードを見ることができます。

1. [Microsoft Flow](http://flow.microsoft.com/) にサインインし、右上隅のベル アイコンを選択して、**[アクティビティをすべて表示]** を選択します。

    ![アクティビティ フィードの表示](./media/gdpr-dsr-export/show-activity-feed.png)

1. **[アクティビティ]** 画面で、結果をコピーし、Microsoft Word などのドキュメント エディターに貼り付けます。

    ![アクティビティ フィードの表示](./media/gdpr-dsr-export/export-activity-feed.png)

## <a name="export-a-users-connections"></a>ユーザーの接続をエクスポートする

接続により、フローは API、SaaS アプリケーション、その他のサード パーティ システムに接続できます。 接続を表示するには次の手順のようにします。

1. [Microsoft Flow](http://flow.microsoft.com/) にサインインし、右上隅の歯車アイコンを選択して、**[接続]** を選択します。

    ![接続の表示](./media/gdpr-dsr-export/show-connections.png)
1. 結果をコピーし、Microsoft Word などのドキュメント エディターに貼り付けます。

PowerApps 管理者 PowerShell コマンドレット

```PowerShell
Add-PowerAppsAccount

#Retrieves all connections for the user 
Add-PowerAppsAccount
$userId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
Get-AdminConnection -CreateBy $userId | ConvertTo-Json |Out-File -FilePath "UserConnections.txt"
```

## <a name="export-a-list-of-a-users-connection-permissions"></a>ユーザーの接続アクセス許可の一覧をエクスポートする

ユーザーは、[PowerApps PowerShell コマンドレット](https://go.microsoft.com/fwlink/?linkid=871804)の Get-ConnectionRoleAssignment 機能を使用して、アクセスできるすべての接続に対する接続のロールの割り当てをエクスポートできます。

```PowerShell
Add-PowerAppsAccount
Get-ConnectionRoleAssignment | ConvertTo-Json | Out-File -FilePath "ConnectionPermissions.txt"
```
PowerApps 管理者 PowerShell コマンドレット

```PowerShell
Add-PowerAppsAccount

#Retrieves all connection permissions for the specified user 
Add-PowerAppsAccount
$userId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
Get-AdminConnectionRoleAssignment -PrincipalObjectId $userId | ConvertTo-Json | Out-File -FilePath "ConnectionPermissions.txt" 
```

## <a name="export-a-users-custom-connectors"></a>ユーザーのカスタム コネクタをエクスポートする

カスタム コネクタは、既製のコネクタを補完し、他の API、SaaS、およびカスタム開発システムに接続できるようにします。 カスタム コネクタの所有権を譲渡したり、カスタム コネクタを削除したりできます。

カスタム コネクタのリストをエクスポートするには、次の手順のようにします。

1. [Microsoft Flow](https://flow.microsoft.com) に移動します。
1. 設定の**歯車**アイコンを選択します。
1. **[カスタム コネクタ]** を選択します。
1. カスタム コネクタのリストをコピーし、Microsoft Word などのテキスト エディターに貼り付けます。

    ![カスタム コネクタのエクスポート](./media/gdpr-dsr-export/export-custom-connectors.png)

Microsoft Flow で提供されるエクスペリエンスだけでなく、[PowerApps PowerShell コマンドレット](https://go.microsoft.com/fwlink/?linkid=871804)の Get-Connector 機能を使って、すべてのカスタム コネクタをエクスポートすることもできます。

~~~~
Add-PowerAppsAccount
Get-Connector -FilterNonCustomConnectors | ConvertTo-Json | Out-File -FilePath "CustomConnectors.txt"
~~~~

PowerApps 管理者 PowerShell コマンドレット

```PowerShell
Add-PowerAppsAccount

#Retrieves all custom connectors for user 
Add-PowerAppsAccount
$userId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
Get-AdminConnector -CreatedBy $userId | ConvertTo-Json | Out-File -FilePath "UserCustomConnectors.txt"  
```

## <a name="export-a-users-custom-connector-permissions"></a>ユーザーのカスタム コネクタのアクセス許可をエクスポートする

ユーザーは、[PowerApps PowerShell コマンドレット](https://go.microsoft.com/fwlink/?linkid=871804)の Get-ConnectorRoleAssignment 機能を使って、作成したすべてのカスタム コネクタのアクセス許可をエクスポートできます。

```PowerShell
Add-PowerAppsAccount
Get-ConnectorRoleAssignment | ConvertTo-Json | Out-File -FilePath "CustomConnectorPermissions.txt"
```

PowerApps 管理者 PowerShell コマンドレット

```PowerShell
Add-PowerAppsAccount

#Retrieves all connection permissions for the specified user 
Add-PowerAppsAccount
$userId = "7822bb68-7c24-49ce-90ce-1ec8deab99a7"
Get-AdminConnectorRoleAssignment -PrincipalObjectId $userId | ConvertTo-Json | Out-File -FilePath "CustomConnectorPermissions.txt"   
```

## <a name="export-approval-history"></a>承認履歴をエクスポートする

Microsoft Flow の承認履歴は、ユーザーが受信または送信した承認の履歴レコードをキャプチャします。 すべてのユーザーが、次のようにして、承認履歴を表示できます。

1. [Microsoft Flow](http://flow.microsoft.com/) にサインインし、**[承認]** を選択して、**[履歴]** を選択します。

    ![承認履歴の表示](./media/gdpr-dsr-export/view-approval-history.png)

1. 一覧に、ユーザーが受け取った承認が表示されます。 ユーザーは、**[受信]** の隣の下向き矢印を選択してから、**[送信済み]** を選択することで、自分が送信した承認を表示できます

    ![受信した承認の表示](./media/gdpr-dsr-export/view-received-approvals.png)

## <a name="export-user-details"></a>ユーザーの詳細をエクスポートする
ユーザーの詳細では、ユーザーと特定のテナント間のリンクが提供されます。 管理者は、**Get AdminFlowUserDetails** コマンドレットを呼び出し、ユーザーのオブジェクト ID で渡すことで、この情報をエクスポートすることができます。

PowerApps 管理者 PowerShell コマンドレット

```PowerShell
Add-PowerAppsAccount

Get-AdminFlowUserDetails -UserId 1b6759b9-bbea-43b6-9f3e-1af6206e0e80
```

## <a name="export-gateway-settings"></a>ゲートウェイ設定をエクスポートする
オンプレミス データ ゲートウェイのデータ主体エクスポート要求への応答に関しては、[こちら](https://docs.microsoft.com/power-bi/service-gateway-onprem#tenant-level-administration)を参照してください。

