---
title: データ損失防止 (DLP) ポリシーの概要 | Microsoft Docs
description: Microsoft Flow のデータ損失防止ポリシーの概要について説明します。
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
ms.date: 02/28/2018
ms.author: deonhe
ms.openlocfilehash: 7dbf6296383551d82d22682121210f1cd339b65e
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "29563088"
---
# <a name="data-loss-prevention-dlp-policies"></a>データ損失防止 (DLP) ポリシー

このドキュメントでは、定義したコネクタ一覧で組織のデータを共有から保護するデータ損失防止ポリシーについて説明します。

## <a name="whats-a-data-loss-prevention-policy"></a>データ損失防止ポリシーとは

組織のデータはその成功に不可欠です。 意思決定のためにデータをすぐに使用できる必要がありますが、アクセス権のないユーザーと共有されないように保護する必要があります。 このデータを保護するため、Microsoft Flow では、ビジネス データにアクセスして共有できるコンシューマー コネクタを定義するポリシーを作成して適用できます。 データを共有する方法を定義するこれらのポリシーは、データ損失防止 (DLP) ポリシーと呼ばれます。

## <a name="why-create-a-dlp-policy"></a>DLP ポリシーを作成する理由

DLP ポリシーを作成して、ビジネス データにアクセスして共有できるコンシューマー コネクタを明確に定義します。 たとえば、Microsoft Flow を使っている組織は、SharePoint のビジネス データが Twitter フィードに自動的に発行されるのを望まない場合があります。 これを防ぐには、SharePoint データがツイートのソースとして使用されるのをブロックする DLP ポリシーを作成します。

## <a name="benefits-of-a-dlp-policy"></a>DLP ポリシーの利点

* 組織全体でデータが一貫した方法で管理されることを保証します。
* 重要なビジネス データが誤ってソーシャル メディア サイトなどのコネクタに発行されるのを防ぎます。

## <a name="managing-dlp-policies"></a>DLP ポリシーの管理

### <a name="prerequisites-for-managing-dlp-policies"></a>DLP ポリシー管理の前提条件

* 環境管理者またはテナント管理者のアクセス許可。

    アクセス許可の詳細については、[環境に関する記事](environments-overview-admin.md)をご覧ください。
* [Microsoft Flow P2 ライセンス](billing-questions.md)。

## <a name="create-a-dlp-policy"></a>DLP ポリシーを作成する

### <a name="prerequisites-for-creating-dlp-policies"></a>DLP ポリシー作成の前提条件

DLP ポリシーを作成するには、少なくとも 1 つの環境へのアクセス許可が必要です。

会社の SharePoint サイトのデータが Twitter に発行されるのを防ぐ DLP ポリシーを作成するには、次の手順のようにします。

1. [Microsoft Flow 管理センター](https://admin.flow.microsoft.com) (管理センター) にサインインします。

1. [データ ポリシー] タブを選び、**[新しいポリシー]** リンクを選びます。

    ![サインイン](./media/prevent-data-loss/create-policy-1.png)
1. **[データ グループ]** タブを選びます。

1. ページの上部にある **[データ ポリシー名]** ラベルに、DLP ポリシーの名前として「*Secure Data Access for Contoso*」と入力します。

    ![サインイン](./media/prevent-data-loss/create-policy-2.png)

1. **[環境]** タブで[環境](environments-overview-admin.md)を選びます。

    > [!NOTE]
    > 環境管理者は、1 つの環境のみに適用されるポリシーを作成できます。 テナント管理者は、環境の任意の組み合わせに適用されるポリシーを作成できます。
    >
    >

    ![環境の選択](./media/prevent-data-loss/create-policy-3.png)

1. **[Data groups]** (データ グループ) タブを選びます。

    ![データ ソースの選択](./media/prevent-data-loss/create-policy-4.png)

1. **[Business data only]\(ビジネス データのみ\)** グループ ボックスの内部にある **[追加]** リンクを選びます。

    ![追加の選択](./media/prevent-data-loss/create-policy-5.png)

1. **[コネクタの追加]** ページで、**[SharePoint]** コネクタと **[Salesforce]** コネクタを選びます。

   ![コネクタの選択](./media/prevent-data-loss/create-policy-6.png)

1. **[コネクタの追加]** ボタンを選んで、ビジネス データを共有できるコネクタを追加します。

1. 画面右上隅の **[ポリシーの保存]** を選びます。

1. しばらくすると、新しい DLP ポリシーがデータ損失防止ポリシーの一覧に表示されます。

    ![DLP リスト](./media/prevent-data-loss/create-policy-9.png)

1. **省略可能** 新しい DLP ポリシーが使用できるようになったことを知らせる電子メールや他の通知をチームに送ります。

以上で、SharePoint と Saleforce 間でのデータ共有をアプリに許可し、他のサービスとのデータ共有をブロックする DLP ポリシーが作成されました。

> [!NOTE]
> 1 つのデータ グループにサービスを追加すると、他のデータ グループからそのサービスが自動的に削除されます。 たとえば、Twitter が現在、**ビジネス データのみ**データ グループに読み込まれているとき、ビジネス データを Twitter と共有しない場合、Twitter サービスを**ビジネス データ禁止**データ グループに追加します。 ビジネス データのみデータ グループから Twitter が削除されます。
>
>

## <a name="data-sharing-violations"></a>データ共有の違反

これまでに説明したような DLP ポリシーを作成した場合、ユーザーが Salesforce (**ビジネス データのみ**のデータ グループ) と Twitter (**ビジネス データが許可されない**データ グループ) の間でデータを共有するフローを作成すると、データ損失防止ポリシーに一致しないためにフローが**中断**されることがユーザーに通知されます。

![フローの作成](./media/prevent-data-loss/10.png)

ユーザーから中断されたフローについての問い合わせがあった場合は、次のことを検討します。

1. この例では、SharePoint と Twitter の間でビジネス データを共有するビジネス上の正当な理由がある場合は、DLP ポリシーを編集できます。

1. DLP ポリシーに準拠するようにフローを編集するよう、ユーザーに依頼します。

1. これら 2 つのエンティティ間でのデータ共有について決定が下されるまでフローを中断した状態のままにするよう、ユーザーに求めます。

## <a name="find-a-dlp-policy"></a>DLP ポリシーを検索する

### <a name="admins"></a>管理者

管理者は、管理センターの検索機能を使って、特定の DLP ポリシーを検索できます。

> [!NOTE]
> 管理者は、組織内のユーザーがフローを作成する前にポリシーを認識できるように、すべての DLP ポリシーを公開する必要があります。
>
>

### <a name="makers"></a>作成者

管理者権限がないユーザーが組織の DLP ポリシーについて詳しく知りたい場合は、管理者に問い合わせてください。 詳細については、[作成者環境に関する記事](environments-overview-maker.md)もご覧ください。

> [!NOTE]
> DLP ポリシーを編集または削除できるのは管理者だけです。
>
>

## <a name="edit-a-dlp-policy"></a>DLP ポリシーを編集する

1. [管理センター](https://admin.flow.microsoft.com)を起動します。

1. 管理センターの左側にある **[Data polices]** (データ ポリシー) リンクを選びます。

    ![データ ポリシーの選択](./media/prevent-data-loss/2.png)

1. 既存の DLP ポリシーの一覧を検索し、編集するポリシーの横にある編集ボタンを選びます。

1. ポリシーに必要な変更を行います。 たとえば、環境や、データ グループのサービスを変更できます。

1. **[ポリシーの保存]** を選んで、変更を保存します。

> [!NOTE]
> 環境管理者は、テナント管理者によって作成された DLP ポリシーを見ることはできますが、編集することはできません。
>
>

## <a name="delete-a-dlp-policy"></a>DLP ポリシーを削除する

1. [管理センター](https://admin.flow.microsoft.com)を起動します。

1. 左側にある **[Data polices]\(データ ポリシー\)** タブを選びます。

    ![データ ポリシー タブの選択](./media/prevent-data-loss/2.png)

1. 既存の DLP ポリシーの一覧を検索し、削除するポリシーの横にある削除ボタンを選びます。

    ![削除ボタンの選択](./media/prevent-data-loss/3-delete.png)

1. **[Delete]** (削除) ボタンを選んで、ポリシーの削除を確定します。

    ![ポリシー削除の確認](./media/prevent-data-loss/4.png)

## <a name="dlp-policy-permissions"></a>DLP ポリシーのアクセス許可

DLP ポリシーを作成および変更できるのは、テナント管理者と環境管理者だけです。 アクセス許可の詳細については、[環境](environments-overview-admin.md)に関する記事をご覧ください。

## <a name="next-steps"></a>次のステップ

* [環境の詳細](environments-overview-admin.md)
* [Microsoft Flow の詳細](getting-started.md)
* [管理センターの詳細](admin-center-introduction.md)
* [データ統合の詳細](https://docs.microsoft.com/common-data-service/entity-reference/dynamics-365-integration)
