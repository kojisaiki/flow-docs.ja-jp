---
title: 管理者に関する環境の概要 | Microsoft Docs
description: Microsoft Flow での環境の使用、作成、管理
services: ''
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2017
ms.author: sunayv
ms.openlocfilehash: cf1a618b9e0ed76147eb4ede2aed42111c66b4a5
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "31007980"
---
# <a name="using-environments-within-microsoft-flow"></a>Microsoft Flow 内の環境の使用

## <a name="benefits"></a>利点

環境には次の利点があります。

* **データのローカリティ**: 環境は複数の異なるリージョンに作成でき、その地理的な場所にバインドされます。 環境内にフローを作成すると、そのフローはその地理的な場所のすべてのデータセンターにルーティングされます。 これには、パフォーマンス上の利点もあります。

    ユーザーがヨーロッパにいる場合は、ヨーロッパ リージョンに環境を作成して使います。 ユーザーが米国にいる場合は、米国に環境を作成して使います。 

    > [!IMPORTANT]
    > 環境を削除した場合、その環境内のすべてのフローも削除されます。 これは、接続、ゲートウェイ、PowerApps など、その環境で作成するすべての項目に適用されます。
* **データ損失の防止**: 管理者としては、内部の場所 (給与情報を含む *OneDrive for Business* や SharePoint リストなど) からデータを取得し、そのデータを公開の場所 (*Twitter* など) に投稿するようなフローは望ましくありません。 Microsoft Flow の展開内のデータを共有できるサービスを制御するには、データ損失防止を使います。

    たとえば、*SharePoint* と *OneDrive for Business* サービスを、ビジネス データのみのポリシーに追加することができます。 この環境に作成されるすべてのフローは、*SharePoint* サービスと *OneDrive for Business* サービスを使うことができます。 しかし、ビジネス データのみのポリシーに含まれていない他のサービスとデータを共有することはできません。

  > [!NOTE]
  > データ損失防止は、P2 ライセンスなど、いくつかのライセンス SKU で使用できます。

* **すべてのリソースの分離境界**: どのフロー、ゲートウェイ、接続、カスタム コネクタなども、固有の環境に存在します。 他の環境には存在しません。
* **Common Data Service**: サービスにデータを挿入するフローを作成する場合は、このサービスを使います。

  * Excel ファイルにデータを挿入し、OneDrive などのクラウド ストレージ アカウントに Excel ファイルを格納します。
  * SQL Database を作成してから、そこにデータを格納します。
  * Common Data Service を使用してデータを格納します。

    すべての環境は、Common Data Service のフロー用に最大で 1 個のデータベースを持つことができます。 Common Data Service にアクセスするには、ライセンスを購入する必要があります。Common Data Service は無料ライセンスには含まれません。

## <a name="limitations"></a>制限事項

環境には多くの利点がありますが、新たな制限も生じます。 環境が分離境界であるという事実は、"*異なる*" 環境のリソースを参照するリソースは持てないことを意味します。 たとえば、ある環境でカスタム コネクタを作成し、そのカスタム コネクタを使うフローを別の環境に作成することはできません。

## <a name="use-the-default-environment"></a>既定の環境を使用する

**既定**の環境はすべてのユーザーによって共有され、すべてのユーザーは**既定**の環境内にフローを作成できます。

> [!TIP]
> プレビュー ユーザーの場合は、既存のすべてのフローが既定の環境に存在します。 "*プレビュー ユーザー*" とは、一般提供 (GA) リリース前に Microsoft Flow を使用していたユーザーのことです。

## <a name="the-admin-center"></a>管理センター

管理者は、管理センターを使って環境の作成と管理を行います。 管理センターを開くには 2 つの方法があります。

### <a name="option-1-select-settings"></a>オプション 1: 設定を選択する

1. [flow.microsoft.com](https://flow.microsoft.com) にサインインします。
1. 設定の歯車アイコンを選び、一覧から **[管理センター]** を選びます。

   ![設定と管理者ポータル](./media/environments-overview-admin/settings.png)
1. 管理センターが開きます。

### <a name="option-2-open-adminflowmicrosoftcom"></a>オプション 2: admin.flow.microsoft.com を開く

[admin.flow.microsoft.com](https://admin.flow.microsoft.com) に移動し、職場アカウントでサインインします。

## <a name="create-an-environment"></a>環境を作成する

1. [Microsoft Flow 管理センター](https://admin.flow.microsoft.com)で **[Environments (環境)]** を選択します。 既存の環境がすべて表示されます。![環境](./media/environments-overview-admin/environments-list.png)
2. **[新しい環境]** を選び、必要な情報を指定します。


   |     プロパティ     |                                                 説明                                                 |
   |------------------|-------------------------------------------------------------------------------------------------------------|
   | 環境名 |              「`Human Resources`」や「`Europe flows`」など、環境の名前を入力します。              |
   |      Region (リージョン)      | 環境をホストする場所を選択します。 最高のパフォーマンスを得るには、ユーザーに最も近いリージョンを使用します。 |
   | 環境の種類 |                  ライセンスに基づいて、環境の種類 ([Production]\(運用\) または [試用版])。                   |

     ![環境設定](./media/environments-overview-admin/new-environment-dialog.png)
3. **[環境の作成]** をクリックします。
4. **[データベースの作成]** と **[スキップ]** の 2 つのオプションが表示されます。
5. **[データベースの作成]** を選ぶと、データベースの **[通貨]** と **[言語]** の指定を求められます。 さらに、サンプル アプリとデータの展開を選ぶこともできます。

   ![データベース構成の設定](./media/environments-overview-admin/create-database-dialog2.png)


次に、ユーザーを環境に追加できます。

## <a name="manage-your-existing-environments"></a>既存の環境を管理する

1. [Microsoft Flow 管理センター](https://admin.flow.microsoft.com)で **[Environments (環境)]** を選択します。

   ![環境のメニュー項目](./media/environments-overview-admin/select-environments.png)
1. 環境を選択してプロパティを開きます。
1. 環境の作成者や地理的な場所など、環境に関する追加情報を見るには、**[詳細]** タブを使います。

   ![[詳細] タブ](./media/environments-overview-admin/open-environment.png)
1. **[Security]** (セキュリティ) を選択します。

    前のステップで **[データベースの作成]** を選ばなかった場合は、**[環境ロール]** として **[環境管理者]** と **[環境作成者]** の 2 つのオプションが表示されます。

    ![管理者ロール](./media/environments-overview-admin/environment-roles.png)

    **作成者**は、フロー、データ接続、ゲートウェイなどの新しいリソースを環境に作成できます。

   > [!NOTE]
   > 環境内のリソースを "*編集する*" には、ユーザーは**作成者**である必要はありません。 各作成者は、環境作成者ではないユーザーにアクセス許可を付与することにより、自分のリソースを編集できるユーザーを決定します。
   > 
   > 

    **管理者**は、データ損失防止ポリシーを作成できるほか、環境の作成、環境へのユーザーの追加、管理者/作成者権限の割り当てなどの他の管理タスクを実行できます。

   1. **[環境作成者]** ロールを選んだ後、**[ユーザー]** を選びます。![作成者ロール](./media/environments-overview-admin/add-environment-maker.png)
   1. **作成者**ロールに与える名前、メール アドレス、またはユーザー グループを入力します。
   1. **[保存]** を選択します。

1. **[セキュリティ]** で **[ユーザー ロール]** を選択します。

    ![ユーザー ロール](./media/environments-overview-admin/security-user-roles.png)

    既存のロールが一覧表示されます。ロールを編集または削除するためのオプションも表示されます。

    **[新しいロール]** を選択して、新しいロールを作成します。
1. **[セキュリティ]** で **[Permission Sets (アクセス許可セット)]** を選択します。

    ![アクセス許可セット](./media/environments-overview-admin/security-permission-set.png)

    ロールを編集または削除するための既存のアクセス許可セットとオプションがすべて表示されます。

    **[新しいアクセス許可セット]** を選び、新しいアクセス許可セットを作成します。
1. データを保存するために **[データベースの作成]** を選んだ場合、このデータベースは Common Data Service の一部です。 **[セキュリティ]** タブをクリックすると、ロール ベースのセキュリティを適用できる**Dynamics 365 インスタンス管理センター**に移動するように求められます。
![Dynamics のセキュリティ設定](./media/environments-overview-admin/Security-Link-D365.png)

1. 環境/インスタンス内のユーザーの一覧からユーザーを選びます。
  ![Dynamics のセキュリティ設定](./media/environments-overview-admin/D365-Select-User.png)

1. ユーザーにロールを割り当てます。

   ![ユーザーにロールを割り当てる](./media/environments-overview-admin/D365-Assign-Role.png)

> [!NOTE]
> これらの環境ロールをユーザーまたはグループに割り当てても、データベース (ある場合) へのアクセス権が自動的に与えられることはないので、データベース所有者が別途アクセス権を付与する必要があります。 
>
>

### <a name="database-security"></a>データベース セキュリティ
データベース スキーマを作成および変更できるかどうか、および環境でプロビジョニングされているデータベース内に格納されたデータに接続できるかどうかは、データベースのユーザー ロールとアクセス許可セットによって制御されます。 環境のデータベースのユーザー ロールとアクセス許可セットは、**[セキュリティ]** タブの **[ユーザー ロール]** および **[アクセス許可セット]** セクションから管理できます。 

   ![ユーザーにロールを割り当てる](./media/environments-overview-admin/D365-Assign-Role.png)

## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="can-i-move-a-flow-between-environments"></a>環境間でフローを移動できますか。

はい、ある環境からフローをエクスポートして、別の環境にインポートできます。

### <a name="which-license-includes-the-common-data-service"></a>どのライセンスに Common Data Service が含まれていますか。

Common Data Service を使用してデータベースを作成する権限は、Microsoft PowerApps Plan 2 のみに含まれています。 ただし、すべての有料プラン (Microsoft Flow Plan 1 と 2、Microsoft PowerApps プラン 1 と 2) には、Common Data Service を使用する権限が含まれています。

[Microsoft Flow の価格](https://flow.microsoft.com/pricing/)に関するページにアクセスして、適切なプランを選んでください。

課金に関してよく寄せられる質問に対する回答については、[課金についての質問](billing-questions.md)に関するドキュメントをご覧ください。

### <a name="can-the-common-data-service-be-used-outside-of-an-environment"></a>環境の外部で Common Data Service を使用できますか。

できません。 Common Data Service には環境が必要です。 詳細は、[こちらを](common-data-model-intro.md)参照してください。

### <a name="what-regions-include-microsoft-flow"></a>Microsoft Flow にはどのようなリージョンが含まれますか。

Microsoft Flow は、Office 365 でサポートされているほとんどのリージョンをサポートしています。詳しくは、[リージョンの概要](regions-overview.md)に関するページをご覧ください。

### <a name="whats-needed-to-create-my-own-custom-environment"></a>独自のカスタム環境を作成するには何が必要ですか。

Microsoft Flow Plan 2 ライセンスを持つすべてのユーザーは、独自の環境を作成できます。 Microsoft Flow のすべてのユーザーは、Plan 2 管理者によって作成された環境を使用できますが、独自の環境を作成することはできません。
