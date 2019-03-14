---
title: ワークフロー プロセスの管理に関するベスト プラクティス | MicrosoftDocs
description: 推奨されるワークフローの使用方法について説明します
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 34e34c33-003a-494f-858c-3d34aacb308c
caps.latest.revision: 10
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: c0a59a625f4d43d125bde6ddf6edd5da5b6f6430
ms.sourcegitcommit: 9ecf4956320d465a3bf618b79a9023b729d33c89
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57462788"
---
# <a name="best-practices-for-workflow-processes"></a>ワークフロー プロセスのベスト プラクティス

このトピックには、ワークフロー プロセスを作成して管理するためのベスト プラクティスについて説明します。  
  
<a name="BKMK_AvoidInfiniteLoops"></a>   
## <a name="avoid-infinite-loops"></a>無限ループを回避する  
 ワークフロー内に無限ループを開始するロジックが作成されてしまい、サーバーのリソースが消費されて、パフォーマンスが影響を受ける可能性があります。 無限ループが発生する可能性のある典型的な状況は、属性が更新されたら開始するよう構成されたワークフローがあり、ワークフローのロジック内でその属性が更新された場合です。 更新アクションが、レコードを更新するのと同じワークフローをトリガーし、そのワークフローを繰り返しトリガーします。  
  
 作成するワークフローには、無限ループを検出して停止するロジックが含まれます。 ワークフロー プロセスが特定のレコードに対して所定の回数を超えて実行された場合、次のエラーが発生してプロセスが失敗します: **このワークフロー ジョブは、それを開始したワークフローに無限ループが含まれているため、取り消されました。ワークフローの論理を修正して、やり直してください)**。 回数の制限は 16 です。  
  
<a name="BKMK_UseWorkflowTemplates"></a>   
## <a name="use-workflow-templates"></a>ワークフロー テンプレートを使用する  
 類似のワークフローが存在し、同じパターンに従うワークフローをさらに作成する可能性がある場合は、ワークフローをワークフロー テンプレートとして保存します。 これにより、次に類似のワークフローを作成する必要が生じた際には、すべての条件とアクションを最初から入力しなくて済むよう、テンプレートを使用してワークフローを作成します。  
  
 **[プロセスの作成]** ダイアログ ボックスで、**[New process from an existing template (select from list)]\(既存のテンプレートから新規プロセス (一覧から選択)\)** を選択します。  
  
<a name="BKMK_UseChildWorkflows"></a>   
## <a name="use-child-workflows"></a>子ワークフローを使用する  
 異なるワークフローまたは条件付き分岐で同じロジックを適用する場合は、ワークフローまたは条件付き分岐ごとにそのロジックを手動でレプリケートする必要がないよう、そのロジックを子ワークフローとして定義します。 これにより、ワークフローを簡単に管理できるようになります。 同じロジックを適用できる可能性のある多数のワークフローを調べる代わりに、1 つのワークフローを更新するだけで済みます。  
  
## <a name="automatically-delete-completed-workflow-jobs"></a>完了したワークフロー ジョブを自動的に削除する
バックグラウンド (非同期) のワークフローでは、ワークフロー定義で **[完了したワークフロー ジョブを自動的に削除する (ディスク容量の確保)]** オプションをオンにすることをお勧めします。 このチェック ボックスをオンにすると、領域を節約するために、システムで成功した実行のワークフロー ログを削除できます。 失敗したワークフロー実行のログは、トラブルシューティングのために常に保存されます。  

![ワークフロー ジョブの保持](media/workflow-job-retention.png)

<a name="BKMK_AutoDeleteCompletedWorkflowJobs"></a>   
## <a name="keep-logs-for-workflow-jobs-that-encountered-errors"></a>エラーが発生しているワークフロー ジョブのログを保持する  
バックグラウンドで実行されない (同期の) ワークフローでは、ワークフロー定義で **[エラーが発生したワークフロー ジョブのログを保持する]** オプションをオンにすることをお勧めします。 このオプションをオンにすると、失敗したワークフロー実行のログをトラブルシューティングのために保存することができます。 成功した同期ワークフロー実行のログは、領域を節約するために常に削除されます。   

![失敗したワークフローのログを保持するオプション](media/keep-logs-for-workflows.png)

## <a name="limit-the-number-of-workflows-that-update-the-same-entity"></a>同じエンティティを更新するワークフローの数を制限する
同じエンティティを更新する複数のワークフローを実行すると、リソース ロックの問題が発生する可能性があります。 営業案件が更新されるたびに関連するアカウントへの更新をトリガーする、複数のワークフローが実行されているとします。 これらのワークフローの複数のインスタンスが実行されて、同じアカウント レコードを同時に更新しようとすると、リソース ロックの問題が発生する可能性があります。 ワークフローのエラーが発生し、"**SQL タイムアウト: リソース _リソース名_ のロックを取得できません**" などのエラー メッセージが記録されます。 

  
<a name="BKMK_DocumentChangesUsingNotes"></a>   
## <a name="use-notes-to-keep-track-of-changes"></a>メモを使用して変更を追跡する  
 ワークフローを編集する際には、[メモ] タブを使用し、実行した内容とその理由を入力してください。 これにより、その変更について他のユーザーが理解できます。  
  
## <a name="next-steps"></a>次のステップ  
 [ワークフロー プロセスの概要](workflow-processes.md)   
 [ワークフロー プロセスの構成](configure-workflow-steps.md)   
 [ワークフロー プロセスの監視と管理](monitor-manage-processes.md)
   
