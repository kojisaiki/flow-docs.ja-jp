---
title: ワークフローからカスタム アクションを呼び出す | MicrosoftDocs
description: ワークフローからカスタム アクションを呼び出す方法について説明します
ms.custom: ''
ms.date: 11/22/2018
ms.reviewer: ''
ms.service: flow
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 1fd5d39e-3dc8-4d1a-8b4b-ccaa303f4bbb
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 938410cf4484f8bed6509beee1d36c8cb3718e6f
ms.sourcegitcommit: 9ecf4956320d465a3bf618b79a9023b729d33c89
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57462972"
---
# <a name="invoke-custom-actions-from-a-workflow"></a>ワークフローからカスタム アクションを呼び出す

ワークフローには、ビジネス シナリオをサポートするさまざまな機能があります。 レコードに対する基本的なデータ操作アクション (作成、更新、削除など) をワークフローの中から呼び出すことによって、かなりのビジネス シナリオが解決されます。 しかしながら、ワークフロー内から直接呼び出されるカスタム アクションの力をワークフローの機能と結合する場合、コードを記述する必要なく、まったく新しい範囲のビジネス シナリオがアプリケーションに追加されます。  
  
 それでは、カスタム アクションがワークフローから呼び出されるシナリオを見てみましょう。 特定の営業案件の割引が 20% を超えたときにマネージャーの承認を要求するカスタム アクションを呼び出します。  
  
<a name="action"></a>   
## <a name="dynamics-365-customer-engagement-example-create-a-custom-action-using-the-opportunity-entity"></a>Dynamics 365 カスタマー エンゲージメントの例: 営業案件エンティティを利用してカスタム アクションを作成する
  
1. [ソリューション エクスプローラー](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer)で、**[プロセス]** を選択します。  
  
2.  ナビゲーション バーで、**[新規]** を選択します。 プロセスに名前を付け、**[アクション]** カテゴリを選択します。  
  
 割引の承認を要求するために、**[承認プロセス]** という名称のカスタム アクションを使用します。 新しいメッセージを作成し、マネージャーの承認に対する要求を送信する目的で、下の画像のように、**[備考]** という入力パラメーターと **[メールを送信する]** 手順を追加しました。  
  
 ![手順の追加 - メールの送信](media/enable-custom-action-approval-proces-sadd-email.png "手順の追加 - メールの送信")  
  
 メール メッセージを構成するには、**[プロパティの設定]** を選択します。 フォームが開いたら、**[フォーム アシスタント]** を使用し、備考やその他の情報を追加します。スクリーンショットで強調表示されている箇所をご覧ください。 備考を追加するには、メッセージ内でそれを表示する箇所にカーソルを置き、**[フォーム アシスタント]** の **[検索]** で最初のドロップダウン リストから **[引数]** を選択し、2 つ目のドロップダウン リストから **[備考]** を選択し、**[OK]** を選択します。  
  
 ![メールの設定](media/enable-custom-action-approval-process-setup-email.png "メールの設定")  
  
 ワークフローからアクションを呼び出すには、それを有効にする必要があります。 アクションを有効にしたら、**[プロパティの表示]** を選択し、そのプロパティを表示できます。  
  
 ![カスタム アクションを有効にする - 承認プロセス](media/enable-custom-action-approval-process-activate-action.png "カスタム アクションを有効にする - 承認プロセス")  
  
<a name="workflow"></a>   
## <a name="invoke-a-custom-action-from-a-workflow"></a>ワークフローからカスタム アクションを呼び出す  
  
1. [ソリューション エクスプローラー](/powerapps/maker/model-driven-apps/advanced-navigation#solution-explorer)で、**[プロセス]** を選択します。   
  
2.  ナビゲーション バーで、**[新規]** を選択します。 プロセスに名前を付け、**[ワークフロー]** カテゴリを選択します。  
  
 20% を超える営業案件の割引に対してマネージャーの承認が必要になったとき、**[承認プロセス]** カスタム アクションを呼び出すワークフローを作成しました。  
  
 ![ワークフローからアクション プロパティを設定する](media/enable-custom-action-from-workflow.png "ワークフローからアクション プロパティを設定する")  
  
 **[プロパティの設定]** を選択することでアクションの入力プロパティを設定できます。 備考に営業案件に関連するアカウントの名前を追加しました。 **[フォーム アシスタント]** の **[検索]** で最初のドロップダウン リストから **[アクション]** を選択し、2 つ目のドロップダウン リストから **[アカウント名]** を選択し、**[OK]** を選択します。 **[ターゲット]** プロパティは必須であり、自動的にデータが入力されます。 **[ターゲット]** プロパティの **{Opportunity(Opportunity)}** は、呼び出し元ワークフローが実行されているものと同じ営業案件です。 あるいは、検索を利用し、ターゲット プロパティに固有の営業案件を選択できます。  
  
 ![承認プロセス アクションに入力パラメーターを設定する](media/enable-customaction-workflow-set-properties.png "承認プロセス アクションに入力パラメーターを設定する")  
  



