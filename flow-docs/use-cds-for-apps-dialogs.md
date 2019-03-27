---
title: ガイド プロセスで Common Data Service ダイアログを使用する (非推奨) | Microsoft Docs
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
ms.openlocfilehash: 90bdbc0ecf9b778ec6da3e4cac2b32b44e361fb0
ms.sourcegitcommit: 24da014ea8db8e59f097c4622d1e2cca9a4d1709
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58352920"
---
# <a name="use-common-data-service-dialogs-for-guided-processes-deprecated"></a>ガイド プロセスで Common Data Service ダイアログを使用する (非推奨)

[ダイアログは非推奨となっています](/dynamics365/get-started/whats-new/customer-engagement/important-changes-coming#dialogs-are-deprecated)。 ダイアログを業務プロセス フローまたはキャンバス アプリに置き換える必要があります。 詳細情報: [ダイアログを業務プロセス フローまたはキャンバス アプリに置き換える](replace-dialogs.md) 

ダイアログは、プロセスからユーザーに指示するためにステップバイステップのスクリプトを使用することによって、情報を収集および処理する Common Data Service で同期または対話型のプロセスです。 たとえば、サポート案件の解決とサポート案件のエスカレーションにおけるご自分のサービス担当者向けのガイドとして指定するダイアログを作成できます。 同様に、営業案件の見込み評価、リード スコアリングなど、営業プロセスを標準化するためのダイアログを作成できます。 詳細については、Dynamics 365 Customer Engagement の開発者ガイドの「[ガイド プロセスでダイアログを使用する](/dynamics365/customer-engagement/developer/use-dialogs-guided-processes)」を参照してください。

## <a name="differences-between-workflows-and-dialogs"></a>ワークフローとダイアログの違い

次の表では、Common Data Service のワークフローとダイアログの違いに関する情報を示しています。  


| ワークフロー     |    ダイアログ      |
|---------------|--------------|
|                                                                                                  ユーザーが開始、または自動化することができます。                                                                                                   |                                                                                          ユーザーが開始する必要があります。                                                                                          |
|                                  非同期プロセスまたはリアルタイム プロセスで、実行を完了するためにユーザーの入力を必要としません。 非同期プロセスはバックグラウンドで実行されますが、リアルタイム プロセスは直ちに実行されます。                                   | 実行を完了するためにユーザーの入力を必要とするリアルタイム プロセスです。 これらのプロセスを実行すると、ウィザードに似たインターフェイスが表示されるため、プロセスを実行するために適切な選択を行うことができます。 |
|                                                    非同期ワークフローの実行に関する詳細を格納するエンティティは `AsyncOperation` ですが、`Process` がリアルタイム ワークフローに使用されます。                                                     |                                                       実行中のダイアログによって生成される情報を格納するエンティティは、`ProcessSession` エンティティです。                                                       |
|                  トリガーはワークフローでサポートされます。 サポートされるトリガーの一覧については、[プロセスでサポートされている種類、トリガー、エンティティ](/dynamics365/customer-engagement/developer/supported-types-triggers-entities-actions-processes)に関するページを参照してください。                   |                                                                                   トリガーはダイアログではサポートされていません。                                                                                    |
  
### <a name="see-also"></a>関連項目
[ダイアログを業務プロセス フローまたはキャンバス アプリに置き換える](replace-dialogs.md)
