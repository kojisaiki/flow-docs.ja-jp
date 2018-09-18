---
title: Microsoft Flow での Microsoft アカウント (MSA) に対する GDPR データ主体の検出要求 | Microsoft Docs
description: Microsoft Flow を使用して Microsoft アカウントに対する GPDR データ主体の検出要求に応答する方法を説明します。
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: KFile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 5/16/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: 9a7031780ed6582d9f881571c3d07ce8aece074d
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690729"
---
# <a name="respond-to-gdpr-data-subject-discovery-requests"></a>GDPR データ主体の検出要求に応答する 

DSR 要求への応答の最初の手順は、要求の主体である個人データを見つけることです。
Microsoft アカウント (MSA) での認証を行うユーザーの個人データを含む、Microsoft Flow リソースの概要は次のとおりです。

|リソース|目的|
|-----|-----|
|実行履歴|過去 28 日間の各フローの実行履歴を示します。 このデータには、開始時刻、終了時刻、状態、および各フローの実行に対するすべての入力/出力情報が含まれています。 [フローの実行履歴](https://flow.microsoft.com/blog/download-history-recurrence/)に関する詳細。|
|アクティビティ フィード| 実行状態、エラー、通知など、各フローのアクティビティの要約を提供します。|
|フロー|[フロー](https://docs.microsoft.com/flow/get-started-logic-flow)に対するワークフロー ロジック。|
|接続|コネクタによって使用され、API、システム、データベースなどに接続できます。 [接続](add-manage-connections.md)に関する詳細。|

