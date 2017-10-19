---
title: "管理者に関する環境の概要 | Microsoft Docs"
description: "Microsoft Flow での環境の使用、作成、管理"
services: 
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/27/2016
ms.author: sunayv
ms.openlocfilehash: f1c50e5d16d5b9fbbd3e6db3128947b0554e9a85
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="using-environments-within-microsoft-flow"></a>Microsoft Flow 内の環境の使用
## <a name="benefits"></a>利点
環境は Microsoft Flow の新機能で、次のような利点があります。 

* **データのローカリティ**: 環境は複数の異なるリージョンに作成でき、その地理的な場所にバインドされます。 環境内にフローを作成すると、そのフローはその地理的な場所のすべてのデータセンターにルーティングされます。 これには、パフォーマンス上の利点もあります。 
  
    ユーザーがヨーロッパにいる場合は、ヨーロッパ リージョンに環境を作成し、使用します。 ユーザーが米国にいる場合は、米国に環境を作成し、使用します。 
  
    環境を削除した場合、その環境内のすべてのフローも削除されます。 これは、接続、ゲートウェイ、PowerApps など、その環境で作成するすべての項目に適用されます。
* **データ損失の防止**: 管理者としては、内部の場所 (*OneDrive for Business* など) からデータを取得し、そのデータを公開の場所 (*Twitter* など) に投稿するようなフローは望ましくありません。 データ損失防止を使用すると、ビジネス データのみのポリシーで、どのサービスを使用できるかを制御できます。 
  
    たとえば、*SharePoint* と *OneDrive for Business* サービスをビジネス データのみのポリシーに追加できます。 この環境に作成したすべてのフローは、*SharePoint* と *OneDrive for Business* サービスを使用できます。 追加したサービスのみを利用できます。 
  
  > [!NOTE]
  > データ損失防止は、P2 ライセンスなど、いくつかのライセンス SKU で使用できます。 
  > 
  > 
* **すべてのリソースの分離境界**: どのフロー、ゲートウェイ、接続、カスタム コネクタなども、固有の環境に存在します。 他の環境には存在しません。 
* **Common Data Service**: どこかにデータを挿入するフローを作成するとします。 次のようなオプションがあります。
  
  * Excel ファイルにデータを挿入し、OneDrive などのクラウド ストレージ アカウントに Excel ファイルを格納します。
  * 独自の SQL Database を作成して、そこにデータを格納します。
  * Common Data Service を使用してデータを格納します。
    
    すべての環境は、Common Data Service のフロー用に、0 個または 1 個のデータベース ストレージを持つことができます。 Common Data Service にアクセスするには、ライセンスを購入する必要があります。無料のライセンスには含まれません。

## <a name="limitations"></a>制限事項
環境には多くの利点がありますが、新たな制限も生じます。 環境が分離境界であるという事実は、複数の環境に "*わたって*" 他のリソースを参照するリソースを持てないことを意味します。 たとえば、1 つの環境でカスタム コネクタを作成し、そのカスタム コネクタと、別の環境内のゲートウェイの両方を使用するフローを作成することはできません。

そのため、必要な場合にだけ環境を作成することが重要です。 環境を作成しすぎると、組織全体のユーザーがリソースを共有することが非常に困難になります。

## <a name="use-the-default-environment"></a>既定の環境を使用する
**既定**の環境はすべてのユーザーが使用でき、すべてのユーザーによって共有されます。 すべてのユーザーがこの環境にフローを作成できます。

> [!TIP]
> プレビュー ユーザーの場合は、既存のすべてのフローが既定の環境に存在します。 "*プレビュー ユーザー*" とは、一般提供 (GA) リリース前に Microsoft Flow を使用していたユーザーのことです。 
> 
> 

## <a name="use-the-administrator-center"></a>管理センターの使用
管理者は、管理センターを使用して、環境の作成、作成した環境へのユーザーの追加などのタスクを行います。 管理センターを開く方法は 2 とおりあります。

#### <a name="option-1-select-settings"></a>オプション 1: 設定を選択する
1. [flow.microsoft.com](https://flow.microsoft.com) にサインインします。
2. 設定の歯車アイコンを選択し、一覧から [**管理センター**] を選択します。  
   ![設定と管理者ポータル](./media/environments-overview-admin/settings.png)
3. 管理センターが開きます。

#### <a name="option-2-open-adminflowmicrosoftcom"></a>オプション 2: admin.flow.microsoft.com を開く
[admin.flow.microsoft.com](https://admin.flow.microsoft.com) に移動し、職場アカウントでサインインします。 管理センターが開きます。

## <a name="create-an-environment"></a>環境を作成する
1. [Microsoft Flow 管理センター](https://admin.flow.microsoft.com)で **[Environments (環境)]** を選択します。 既存の環境がすべて表示されます。  
   ![](./media/environments-overview-admin/environments-list.png)
2. **[New environment]** (新しい環境) を選択します。 次の情報を入力します。
   
   | プロパティ | 説明 |
   | --- | --- |
   | 環境名 |「`Human Resources`」や「`Europe flows`」など、環境の名前を入力します。 |
   | Region (リージョン) |環境をホストする場所を選択します。 最高のパフォーマンスを得るには、ユーザーに最も近いリージョンを使用します。 たとえば、フローのユーザーがロンドンにいる場合は、ヨーロッパ リージョンを選択します。 フローのユーザーがニューヨークにいる場合は、米国リージョンを選択します。 |
3. [**環境を作成する**] を選択します。 新しい環境が一覧表示されます。 

次に、ユーザーを環境に追加します。

## <a name="manage-your-existing-environments"></a>既存の環境を管理する
1. [Microsoft Flow 管理センター](https://admin.flow.microsoft.com)で **[Environments (環境)]** を選択します。  
   ![](./media/environments-overview-admin/select-environments.png)  
2. 環境を選択してプロパティを開きます。 
3. **[Details (詳細)]** に、環境の作成者、地理的な場所など、環境に関する追加情報が表示されます。  
   ![](./media/environments-overview-admin/open-environment.png)
4. **[Security]** (セキュリティ) を選択します。 **[Environment roles]** (環境の役割) のオプションは、**[Admin]** (管理者) と **[Maker]** (作成者) の 2 つです。  
   
    ![](./media/environments-overview-admin/environment-roles.png)
   
    **[Maker]** (作成者) は、環境に新しいリソースを作成できます (フロー、データ接続、ゲートウェイなど)。 
   
   > [!NOTE]
   > ユーザーは**作成者**でなくても、環境内のリソースを "*編集*" できます。また、"*新規の*" リソースを作成することもできます。 各リソース作成者は、そのリソースを編集できるユーザーを決定することも、環境作成者以外のユーザーに編集アクセス許可を付与することもできます。
   > 
   > 
   
    **管理者**は、データ損失防止ポリシーを作成できるほか、環境の作成、環境へのユーザーの追加、管理者/作成者権限の割り当てなどの管理タスクも実行できます。  
   
   1. **[Environment Maker]** (環境作成者) の役割を選択し、**[Users]** (ユーザー) を選択します。  
      ![](./media/environments-overview-admin/add-environment-maker.png)
   2. 作成者の役割に与える名前、電子メール アドレス、またはユーザー グループを入力します。 入力を始めると、IntelliSense によって文字列に一致するユーザーまたはグループが一覧表示されます。 
   3. **[Save]** (保存) を選択して、ユーザーの追加を完了します。 
5. **[セキュリティ]** で **[ユーザー ロール]** を選択します。  
    ![](./media/environments-overview-admin/security-user-roles.png)
   
    既存のロールが一覧表示されます。ロールを編集または削除するためのオプションも表示されます。 
   
    **[新しいロール]** を選択して、新しいロールを作成します。 
6. **[セキュリティ]** で **[Permission Sets (アクセス許可セット)]** を選択します。  
    ![](./media/environments-overview-admin/security-permission-set.png)
   
    既存のアクセス許可セットが一覧表示されます。ロールを編集または削除するためのオプションも表示されます。 
   
    **[New permission set (新しいアクセス許可セット)]** を選択し、新しいセットを作成します。 
7. [**データベース**] では、データを格納するかデータベースを作成できます。 このデータベースは、Common Data Service の一部です。

## <a name="commonly-asked-questions"></a>よくある質問
##### <a name="can-i-migrate-a-microsoft-flow-in-my-us-environment-to-a-europe-environment"></a>米国環境の Microsoft Flow をヨーロッパ環境に移行できますか。
いいえ、環境間でフローを移動することはできません。 別の環境にフローを作成し直してください。

##### <a name="which-license-includes-the-common-data-service"></a>どのライセンスに Common Data Service が含まれていますか。
Common Data Service を使用してデータベースを作成する権限は、Microsoft PowerApps Plan 2 のみに含まれています。 ただし、すべての有料プラン (Microsoft Flow Plan 1 と 2、Microsoft PowerApps プラン 1 と 2) には、Common Data Service を使用する権限が含まれています。

適したプランを選択するには、[Flow の価格](https://flow.microsoft.com/pricing/)を参照してください。  

[課金に関する質問](billing-questions.md)でもよく寄せられる一般的な質問をご確認いただけます。 

##### <a name="can-the-common-data-service-be-used-outside-of-an-environment"></a>環境の外部で Common Data Service を使用できますか。
できません。 Common Data Service には環境が必要です。 詳細は、[こちらを](common-data-model-intro.md)参照してください。

##### <a name="what-regions-include-microsoft-flow"></a>Microsoft Flow にはどのようなリージョンが含まれますか。
Microsoft Flow は、Office 365 でサポートされているリージョンのほとんどをサポートしています。詳細については、[リージョンの概要](regions-overview.md)に関するページを参照してください。

##### <a name="what-is-needed-to-create-my-own-custom-environment"></a>独自のカスタム環境を作成するには何が必要ですか。
Microsoft Flow Plan 2 ライセンスを持つすべてのユーザーは、既定の環境だけでなく、独自の環境を作成できます。 Office 365 や無料プランを含む、Microsoft Flow のすべてのユーザーは、Plan 2 管理者によって作成された環境を使用できますが、独自の環境を作成することはできません。 

