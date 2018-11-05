---
title: ガイド プロセスで CDS for Apps ダイアログを使用する (非推奨) | MicrosoftDocs
description: ダイアログは、プロセスからユーザーに指示するためにステップバイステップのスクリプトを使用することによって、情報を収集および処理する同期または対話型のプロセスです。
ms.custom: ''
ms.date: 10/31/2017
ms.reviewer: ''
ms.topic: article
ms.assetid: d17f8ae2-854b-4f67-a115-5a03d4f0b8ce
caps.latest.revision: 25
author: msftman
ms.author: deonhe
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: f8b2e87bdb9aed63e9f180d446349779cd37c25c
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689665"
---
# <a name="use-cds-for-apps-dialogs-for-guided-processes-deprecated"></a>ガイド プロセスで CDS for Apps ダイアログを使用する (非推奨)

[ダイアログは非推奨となっています](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#dialogs-are-deprecated)。 ダイアログを業務プロセス フローまたはキャンバス アプリに置き換える必要があります。 詳細情報: [ダイアログを業務プロセス フローまたはキャンバス アプリに置き換える](replace-dialogs.md) 

ダイアログは、プロセスからユーザーに指示するためにステップバイステップのスクリプトを使用することによって、情報を収集および処理する Common Data Service (CDS) for Apps で同期または対話型のプロセスです。 たとえば、サポート案件の解決とサポート案件のエスカレーションにおけるご自分のサービス担当者向けのガイドとして指定するダイアログを作成できます。 同様に、営業案件の見込み評価、リード スコアリングなど、営業プロセスを標準化するためのダイアログを作成できます。 詳細については、Dynamics 365 Customer Engagement の開発者ガイドの「[ガイド プロセスでダイアログを使用する](/dynamics365/customer-engagement/developer/use-dialogs-guided-processes)」を参照してください。

## <a name="differences-between-workflows-and-dialogs"></a>ワークフローとダイアログの違い

次の表では、CDS for Apps のワークフローとダイアログの違いに関する情報を示しています。  


| ワークフロー     |    ダイアログ      |
|---------------|--------------|
|                                                                                                  ユーザーが開始、または自動化することができます。                                                                                                   |                                                                                          ユーザーが開始する必要があります。                                                                                          |
|                                  非同期プロセスまたはリアルタイム プロセスで、実行を完了するためにユーザーの入力を必要としません。 非同期プロセスはバックグラウンドで実行されますが、リアルタイム プロセスは直ちに実行されます。                                   | 実行を完了するためにユーザーの入力を必要とするリアルタイム プロセスです。 これらのプロセスを実行すると、ウィザードに似たインターフェイスが表示されるため、プロセスを実行するために適切な選択を行うことができます。 |
|                                                    非同期ワークフローの実行に関する詳細を格納するエンティティは `AsyncOperation` ですが、`Process` がリアルタイム ワークフローに使用されます。                                                     |                                                       実行中のダイアログによって生成される情報を格納するエンティティは、`ProcessSession` エンティティです。                                                       |
|                  トリガーはワークフローでサポートされます。 サポートされるトリガーの一覧については、[プロセスでサポートされている種類、トリガー、エンティティ](/dynamics365/customer-engagement/developer/supported-types-triggers-entities-actions-processes)に関するページを参照してください。                   |                                                                                   トリガーはダイアログではサポートされていません。                                                                                    |
  
### <a name="see-also"></a>関連項目
[ダイアログを業務プロセス フローまたはキャンバス アプリに置き換える](replace-dialogs.md)
