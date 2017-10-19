---
title: "データ損失防止 (DLP) ポリシーの概要 | Microsoft Docs"
description: "Microsoft Flow のデータ損失防止ポリシーの概要について説明します。"
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
ms.date: 01/24/2016
ms.author: deonhe
ms.openlocfilehash: 29eaa9299e09c641538ab8f9dfbc9954bca66a3b
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="data-loss-prevention-dlp-policies"></a>データ損失防止 (DLP) ポリシー
## <a name="what-is-a-data-loss-prevention-policy"></a>データ損失防止ポリシーとは
組織のデータはその成功に不可欠です。 意思決定のためにデータをすぐに使用できる必要がありますが、アクセス権のないユーザーと共有されないように保護する必要があります。 このデータを保護するため、Microsoft Flow (単に Flow) では、共有できるコンシューマー サービス/コネクタ固有のビジネス データを定義するポリシーを作成して適用できます。 データを共有する方法を定義するこれらのポリシーは、データ損失防止 (DLP) ポリシーと呼ばれます。

## <a name="why-create-a-dlp-policy"></a>DLP ポリシーを作成する理由
DLP ポリシーは、共有できるコンシューマー サービス ビジネス データを明確に定義するために作成します。 たとえば、Flow を使用している組織は、SharePoint に保存されているビジネス データが Twitter フィードに自動的に発行されるのを望まない場合があります。 これを防ぐには、SharePoint データがツイートのソースとして使用されるのをブロックする DLP ポリシーを作成できます。

## <a name="benefits-of-a-dlp-policy"></a>DLP ポリシーの利点
* 組織全体でデータが一貫した方法で管理されることを保証します。  
* 重要なビジネス データが誤ってソーシャル メディア サイトなどのサービスに発行されるのを防ぎます。   

## <a name="managing-dlp-policies"></a>DLP ポリシーの管理
**前提条件**  
DLP ポリシーを作成、編集、削除するには、次のものが必要です。 

* 環境管理者またはテナント管理者のアクセス許可。 アクセス許可について詳しくは、[環境に関するトピック](environments-overview-admin.md)をご覧ください。  
* [Flow P2 ライセンス](billing-questions.md)。  

## <a name="create-a-dlp-policy"></a>DLP ポリシーを作成する
**前提条件**  
DLP ポリシーを作成するのには、少なくとも 1 つの環境へのアクセス許可が必要です。  

会社の SharePoint に保存されているデータが Twitter に発行されるのを防ぐ DLP ポリシーを作成するには、次の手順のようにします。  

1. データ ポリシー タブで **[New policy]** (新しいポリシー) リンクを選びます。  
   ![サインイン](./media/prevent-data-loss/create-policy-1.png)    
2. 表示されるページの上部にある **[Data Policy Name]** (データ ポリシー名) に「 *Secure Data Access for Contoso* 」と入力します。   
   ![サインイン](./media/prevent-data-loss/create-policy-2.png)  
3. **[Applies to]** (適用対象) タブで[環境](environments-overview-admin.md)を選びます。  
   **注:** 環境管理者は、1 つの環境のみに適用されるポリシーを作成できます。 テナント管理者は、すべての環境、1 つまたは複数の選択した環境、または選択した環境を除くすべての環境に適用されるポリシーを作成できます。  
   ![サインイン](./media/prevent-data-loss/create-policy-3.png)  
4. **[Data groups]** (データ グループ) タブを選びます。  
   ![サインイン](./media/prevent-data-loss/create-policy-4.png)  
5. **[Business data only]** (ビジネス データのみ) グループ ボックスの内側にある **[+ 追加]** リンクを選びます。    
   ![サインイン](./media/prevent-data-loss/create-policy-5.png)  
6. **[Add services]** (サービスの追加) ページで、**[SharePoint]** サービスと **[Salesforce]** サービスを選びます。  
   ![サインイン](./media/prevent-data-loss/create-policy-6.png)  
7. **[Add services]** (サービスの追加) ボタンを選んで、ビジネス データの共有を許可するサービスを追加します。    
   ![サインイン](./media/prevent-data-loss/create-policy-7.png)  
8. **[Save Policy]** (ポリシーの保存) を選びます。  
   ![サインイン](./media/prevent-data-loss/create-policy-8.png)  
9. しばらくすると、新しい DLP ポリシーがデータ損失防止ポリシーの一覧に表示されます。  
   ![サインイン](./media/prevent-data-loss/create-policy-9.png)  
10. **省略可能** 新しい DLP ポリシーが使用できるようになったことを知らせる電子メールや他の通知をチームに送ります。

以上で、SharePoint と Saleforce 間でのデータ共有をアプリに許可し、他のサービスとのデータ共有をブロックする DLP ポリシーが作成されました。  

**注**: 1 つのデータ グループにサービスを追加すると、他のデータ グループからそのサービスが自動的に削除されます。 たとえば、Twitter が現在、**ビジネス データのみ**データ グループに読み込まれているとき、ビジネス データを Twitter と共有しない場合、Twitter サービスを**ビジネス データ禁止**データ グループに追加します。 ビジネス データのみデータ グループから Twitter が削除されます。  

## <a name="data-sharing-violations"></a>データ共有の違反
これまでに説明したような DLP ポリシーを作成した場合、ユーザーが Salesforce (**ビジネス データのみ**のデータ グループ) と Twitter (**ビジネス データが許可されない**データ グループ) の間でデータを共有するフローを作成すると、データ損失防止ポリシーに一致しないためにフローが**中断**されることがユーザーに通知されます。  
![フローの作成](./media/prevent-data-loss/10.png)  

ユーザーから中断されたフローについての問い合わせがあった場合は、次のことを検討します。  

1. この例では、SharePoint と Twitter の間でビジネス データを共有するビジネス上の正当な理由がある場合は、DLP ポリシーを編集できます。  
2. DLP ポリシーに準拠するようにフローを編集するよう、ユーザーに依頼します。  
3. これら 2 つのエンティティ間でのデータ共有について決定が下されるまでフローを中断した状態のままにするよう、ユーザーに求めます。  

## <a name="find-a-dlp-policy"></a>DLP ポリシーを検索する
### <a name="admins"></a>管理者
管理者は、管理センターの検索機能を使って、特定の DLP ポリシーを検索できます。  

**注** 管理者は、組織内のユーザーがフローを作成する前にポリシーを認識できるように、すべての DLP ポリシーを公開する必要があります。

### <a name="makers"></a>作成者
管理者権限がないユーザーが組織の DLP ポリシーについて詳しく知りたい場合は、管理者に問い合わせてください。 詳細については、[作成者環境に関するトピック](environments-overview-maker.md)もご覧ください。  

**注** DLP ポリシーを編集または削除できるのは管理者だけです。  

## <a name="edit-a-dlp-policy"></a>DLP ポリシーを編集する
1. https://admin.flow.microsoft.com にアクセスして管理センターを起動します。  
2. 管理センターの左側にある **[Data polices]** (データ ポリシー) リンクを選びます。  
   ![サインイン](./media/prevent-data-loss/2.png)  
3. 既存の DLP ポリシーの一覧を検索し、編集するポリシーの横にある編集ボタンを選びます。  
   ![サインイン](./media/prevent-data-loss/3.png)  
4. 必要な変更を行います。 たとえば、環境や、データ グループのサービスを変更できます。  
5. **[Save Policy]** (ポリシーの保存) を選んで、変更を保存します。  
   ![サインイン](./media/prevent-data-loss/create-policy-8.png)  

ポリシーが更新されました。 データ損失防止ポリシーの一覧で変更したポリシーを検索し、プロパティを確認することによって、ポリシーが変更されたことを確認できます。   

**注** 環境管理者は、テナント管理者によって作成された DLP ポリシーを見ることはできますが、編集することはできません。  

## <a name="delete-a-dlp-policy"></a>DLP ポリシーを削除する
1. https://admin.flow.microsoft.com にアクセスして管理センターを起動します。  
2. 管理センターの左側にある **[Data polices]** (データ ポリシー) リンクを選びます。  
   ![サインイン](./media/prevent-data-loss/2.png)  
3. 既存の DLP ポリシーの一覧を検索し、削除するポリシーの横にある削除ボタンを選びます。  
   ![サインイン](./media/prevent-data-loss/3-delete.png)  
4. **[Delete]** (削除) ボタンを選んで、ポリシーの削除を確定します。  
   ![サインイン](./media/prevent-data-loss/4.png)  

ポリシーが削除されました。 左側の **[Data Policies]** (データ ポリシー) リンクを選んでポリシーの一覧を表示して、データ損失防止ポリシーの一覧に削除したポリシーが表示されなくなったことを確認できます。   

## <a name="dlp-policy-permissions"></a>DLP ポリシーのアクセス許可
DLP ポリシーを作成および変更できるのは、テナント管理者と環境管理者だけです。 アクセス許可について詳しくは、[環境に関するトピック](environments-overview-admin.md)をご覧ください。  

## <a name="next-steps"></a>次のステップ
* [環境の詳細](environments-overview-admin.md)  
* [Microsoft Flow の詳細](getting-started.md)  
* [管理センターの詳細](introduction-to-the-admin-center.md)  

