---
title: PowerApps を使用したワークフロー プロセスの監視と管理 | MicrosoftDocs
ms.custom: ''
ms.date: 05/06/2018
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
ms.assetid: a987a803-4674-4eb0-87de-caefa003b1eb
caps.latest.revision: 12
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 007caa66731870f359e8cb33ba0919390d3196cd
ms.sourcegitcommit: 9ecf4956320d465a3bf618b79a9023b729d33c89
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57462880"
---
# <a name="monitor-and-manage-workflow-processes"></a>ワークフロー プロセスの監視と管理

プロセスを監視および管理するには、プロセスを探して、状態を評価し、問題に対処するために必要なアクションがあれば実行します。  
  
<a name="BKMK_MonitorAsyncWorkflows"></a>   
## <a name="monitoring-background-workflows"></a>バックグラウンド ワークフローを監視する  
 バックグラウンド ワークフローでは、状態を追跡するためにシステム ジョブ レコードが生成されます。 これらのシステム ジョブに関する情報には、次に示すアプリケーション内のいくつかの場所でアクセスできます。  
  
 **[[設定]](/powerapps/maker/model-driven-apps/advanced-navigation#settings) > [システム ジョブ]**  
 これにはすべての種類のシステム ジョブが含まれます。 **[システム ジョブの種類]** が **[ワークフロー]** のレコードをフィルター処理する必要があります。  
  
 **ワークフロー プロセスから**  
 バックグラウンド ワークフロー定義を開いて、**[プロセス セッション]** タブに移動します。ここでは、このバックグラウンド ワークフローのシステム ジョブのみが表示されます。  
  
 **レコードから**  
 エンティティ フォームを編集して、ナビゲーションに**バックグラウンド プロセス**リレーションシップが含まれるようにできます。 こうすると、レコードのコンテキストで開始されたすべてのシステム ジョブが表示されます。  
  
> [!NOTE]
>  非同期システム ジョブ (ワークフロー) が数回連続して失敗した場合、システムはそのたびにそのジョブを実行する間隔を延ばして、管理者またはアプリ作成者が問題を調査して解決できるようにします。 再びジョブが成功するようになると、通常どおりの実行が再開されます。  
  
<a name="BKMK_ActionsOnRunningWorkflows"></a>   
### <a name="actions-on-running-background-workflows"></a>バックグラウンド ワークフローの実行に対するアクション  
 バックグラウンド ワークフローが実行しているとき、ワークフローを**取り消し**、**一時停止**、または**延期**することができます。 前に一時停止したワークフローがある場合は、**再開**できます。  
  
<a name="BKMK_MonitorSyncWorkflows"></a>   
## <a name="monitoring-real-time-workflows-and-actions"></a>リアルタイム ワークフローとアクションを監視する  
 リアルタイム ワークフローおよびアクションはすぐに発生するため、システム ジョブ レコードは使用されません。 エラーが発生すると、アプリケーション内で **[ビジネス プロセス エラー]** という見出しでユーザーに表示されます。  
  
 成功した操作のログはありません。 エラーの記録を有効にするには、プロセスの **[管理]** タブの下にある **[ワークフロー ログの保持]** 領域で **[エラーが発生したワークフロー ジョブのログを保持する]** オプションをオンにします。  
  
 特定のプロセスのエラーのログを表示するには、リアルタイム ワークフローまたはアクションの定義を開き、**[プロセス セッション]** タブに移動します。このプロセスについて記録されたエラーのみが表示されます。  
  
 任意のプロセスのすべてのエラーを表示する場合は、**[高度な検索]** に移動し、プロセス セッション エンティティに関するエラーを表示するビューを作成します。  
  
<a name="BKMK_StatusOfWorkflowProcesses"></a>   
## <a name="status-of-workflow-processes"></a>ワークフロー プロセスの状態  
 ワークフロー プロセスの一覧を表示すると、個々のプロセスには **[状態]** と **[状態の理由]** の値が 1 つ対応しています。  
  
|都道府県|状態の理由|  
|-----------|-------------------|  
|準備完了|リソースの待機中|  
|中断|待機中|  
|ロック|処理中<br /><br /> 一時停止中<br /><br /> 取り消し中|  
|完了|成功<br /><br /> 失敗<br /><br /> 取り消し済み|  

## <a name="deleting-process-log-records"></a>プロセス ログ レコードを削除する

よく実行されるバックグラウンド ワークフローまたは業務プロセス フローが組織で使用されている場合、プロセス ログ レコードの容量が大きくなり、パフォーマンスの問題を引き起こしたり、大容量のストレージを消費する可能性があります。 標準のレコード一括削除ジョブのいずれかによって十分に除去されないプロセスのログ レコードを削除するには、一括削除システム ジョブ機能を使用してカスタムのレコード一括削除ジョブを作成できます。

1. **[設定]** > **[データ管理]** > **[レコードの一括削除]** に移動します。
2. **[レコードの一括削除]** 領域で **[新規]** を選択します。 
3. **一括削除ウィザード**の開始ページで **[次へ]** を選択します。
4. **[検索対象]** リストで **[システム ジョブ]** を選択します。
5. 次の条件を使用して、プロセス ログ レコードを削除するレコード一括削除ジョブを作成します。 
 - **[システム ジョブの種類] [が次の値と等しい] [ワークフロー]**。 これによって対象がワークフローのレコードになります。 
 - **[状態] [が次の値と等しい] [完了]**。 完了したワークフローのみがジョブの実行対象になります。
 - **[状態の理由] [が次の値と等しい] [成功]**。 成功、取り消し済み、失敗のジョブを削除します。
 - **[完了日時] [が X 日よりも古い] [30]**。 [完了日時] フィールドを使用して、完了してから 30 日を超えたワークフロー プロセスのログ レコードのみを削除します。
 ![custom-bulk-record-deletion.png](media/custom-bulk-record-deletion.png)
6. **[次へ]** をクリックします。
7. 一括削除ジョブを実行する間隔を設定します。 設定した間隔で実行するようにジョブをスケジュール設定するか、[[即時] オプションを使用](#using-the-immediately-option)して 1 回限りの一括削除ジョブを作成できます。 この例では、定期的なジョブが 2018 年 5 月 21 日から 30 日間隔で実行されるように設定されます。 
![レコードの一括削除オプション](media/custom-bulk-record-delete-options.png)

### <a name="using-the-immediately-option"></a>[即時] オプションを使用する

レコードの同期一括削除をすぐに実行できるオプションがあることに注意してください。**[即時]** オプションを選択します。 この削除操作は、各レコードを削除イベント パイプラインに渡すのではなく、直接 SQL Server を実行することで行われ、システム パフォーマンスへの影響を軽減できます。 一括削除ジョブが非同期キューで処理を待機するのに比べて、これは余分なワークフロー レコードをすばやくクリーンアップする場合に適したオプションです。 

**[即時]** オプションは、次の条件を満たす場合に有効です。 
- 一括削除ジョブの対象がシステム ジョブ エンティティです。
- 検索条件が、システム ジョブの種類がワークフローと等しいという条件です。 
- 一括削除ジョブを作成するユーザーが、AsyncOperation エンティティに対するグローバル レベルの削除権限を持っています。 この権限はシステム管理者セキュリティ ロールにあります。  

同期一括削除では、完了状態の AsyncOperation レコードのみが削除されます。 1 回の呼び出しでの最大 100 万件のレコードが処理されます。 ご使用の環境で 100 万件を超えるレコードを削除する場合には、ジョブを複数回実行する必要があります。  
  
## <a name="next-steps"></a>次のステップ   
 [ワークフロー プロセスのベスト プラクティス](best-practices-workflow-processes.md) <br />

