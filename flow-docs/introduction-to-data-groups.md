---
title: Microsoft Flow のデータ グループ | Microsoft Docs
description: Microsoft PowerApps と Microsoft Flow のデータ グループの概要
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
ms.date: 10/26/2016
ms.author: deonhe
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: ba064461c34ce73faa712964791643ef67fca089
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690148"
---
# <a name="learn-all-about-data-groups"></a>データ グループのすべて
## <a name="what-is-a-data-group"></a>データ グループとは
データ グループは、[データ損失防止 (DLP) ポリシー](prevent-data-loss.md)内のサービスを分類する簡単な方法です。 **Business data only** (ビジネス データのみ) グループと **No business data allowed** (ビジネス データ禁止) グループという 2 つのデータ グループを利用できます。 どのサービスをどのデータ グループに配置するかは組織が自由に決定できます。 サービスを分類する最良の方法は、組織に与える影響に基づいてグループにサービスを配置することです。 既定では、すべてのサービスが **No business data allowed** (ビジネス データ禁止) グループに配置されます。 管理センターから DLP ポリシーのプロパティを作成または変更するとき、データ グループでサービスを管理します。

## <a name="how-data-is-shared-between-data-groups"></a>データ グループ間でデータが共有されるしくみ
グループの異なるサービス間ではデータを共有できません。 たとえば、**Business data only** (ビジネス データのみ) グループに SharePoint と Salesforce を配置し、**No business data allowed** (ビジネス データ禁止) グループに Facebook と Twitter を配置した場合、SharePoint と Facebook の間でデータを移動させるフローを作成することはできません。 グループの異なるサービス間ではデータを共有することはできませんが、特定のグループ内のサービス間ではデータを共有できます。 そのため、前の例に戻ると、SharePoint と Salesforce は同じデータ グループに配置されたため、エンド ユーザーが作成したフローでは、SharePoint と Salesforce の間でデータを共有できます。 同様に、エンド ユーザーは Facebook と Twitter の間でデータを共有するフローや PowerApps を作成できます。 要点は、特定のグループ内のサービスがデータを共有できて、グループの異なるサービスはデータを共有できないということです。  

また、1 つのデータ グループを *既定* のグループとして指定する必要かがあります。 最初は、**No business data allowed** (ビジネス データ禁止) グループが*既定*のグループであり、すべてのサービスがそのデータ グループに配置されます。 監理者は既定のデータ グループを **Business data only** (ビジネス データのみ) グループに変更できます。 **注** フローに追加された新しいサービスは指定の *既定* グループに配置されます。 そのため、**No business data allowed** (ビジネス データ禁止) を既定のグループにすることが推奨されます。ビジネス データを新しいサービスと共有した場合の影響を組織が判断してから **Business data only** (ビジネス データのみ) グループにサービスを手動で追加します。

## <a name="add-services-to-a-data-group"></a>サービスをデータ グループに追加する
このチュートリアルでは、データ損失防止 (DLP) ポリシーの **Business data only** (ビジネス データのみ) データ グループに SharePoint と Salesforce を追加します。 

1. DLP ポリシーの **Business data only** (ビジネス データのみ) グループ ボックスの内側にある **[+ 追加]** リンクを選択します。    
   ![イメージを追加する](./media/introduction-to-data-groups/add-to-data-group-1.png)  
2. SharePoint と Salesforce を選択し、**[サービスの追加]** を選択して両方のサービスを Business data only (ビジネス データのみ) グループに追加します。    
   ![サービス イメージを追加する](./media/introduction-to-data-groups/add-to-data-group-2.png)  
3. 一番上にあるメニューから **[ポリシーの保存]** を選択します。  
   ![ポリシーを保存する](./media/introduction-to-data-groups/add-to-data-group-4.png) 
4. SharePoint と Salesforce の両方が Business data only (ビジネス データのみ) グループに入っています。  
   ![更新されたビジネス データ グループ](./media/introduction-to-data-groups/add-to-data-group-3.png)   

このチュートリアルでは、DLP ポリシーの **Business data only** (ビジネス データのみ) データ グループに SharePoint と Salesforce を追加しました。 DLP ポリシーの環境に属する人物が SharePoint または Salesforce と **No business data allowed** (ビジネス データ禁止) データ グループのサービスの間でデータを共有するアプリを作成した場合、そのアプリの実行は許可されません。

## <a name="remove-services-from-a-data-group"></a>データ グループからサービスを削除する
すべてのサービスは利用できるデータ グループの 1 つに属する必要があるため、特定のグループからサービスを削除するには、そのサービスを別のグループに追加し、ポリシーを保存します。  

## <a name="change-the-default-data-group"></a>既定のデータ グループを変更する
このチュートリアルでは、**No business data allowed** (ビジネス データ禁止) から **Business data only** (ビジネス データのみ) グループに既定のデータ グループを変更します。  

**重要** フローに追加された新しいサービスは指定の *既定* グループに配置されます。 このような理由から、**No business data allowed** (ビジネス データ禁止) を既定のグループにしておき、**Business data only** (ビジネス データのみ) グループにサービスを手動で追加する方法が推奨されます。

1. 既定のデータ グループとして指定するデータ グループの右上隅にある **[...]** を選択します。    
   ![既定のグループを変更する](./media/introduction-to-data-groups/default-data-group-0.png)  
2. **[Set as default group]** (既定のグループとして設定する) を選択します:  
   ![既定のグループを変更する](./media/introduction-to-data-groups/default-data-group-1.png)   
3. 一番上にあるメニューから **[ポリシーの保存]** を選択します。  
   ![既定のグループを変更する](./media/introduction-to-data-groups/add-to-data-group-4.png) 
4. これでこのデータ グループが既定のデータ グループとして指定されます。  
   ![既定のグループを変更する](./media/introduction-to-data-groups/default-data-group-2.png)   

## <a name="next-steps"></a>次のステップ
* [データ損失防止 (DLP) ポリシーの詳細](prevent-data-loss.md)
* [環境の詳細](environments-overview-admin.md)   

