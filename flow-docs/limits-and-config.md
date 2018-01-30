---
title: "制限事項と構成 | Microsoft Docs"
description: "制限事項と構成"
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/02/2017
ms.author: stepsic
ms.openlocfilehash: 27e12df6ae5754f921d37992fa6759d152fd1afc
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="limits-and-configuration-in-microsoft-flow"></a>Microsoft Flow での制限事項と構成
このトピックでは、現時点でのフローに関する制限事項と構成の詳細について説明します。

## <a name="request-limits"></a>要求の制限
1 つの送信要求に対する制限は次のとおりです。

### <a name="timeout"></a>タイムアウト
| Name (名前) | 制限 |
| --- | --- |
| 要求タイムアウト |120 秒 |

### <a name="message-size"></a>メッセージ サイズ
| Name (名前) | 制限 | 備考 |
| --- | --- | --- |
| メッセージ サイズ |100 MB |100 MB を完全にサポートしていない API もあります。 |
| 式の評価の制限 |131,072 文字 |`@concat()`、`@base64()`、`string` は、この制限を超えることはできません。 |

### <a name="retry-policy"></a>再試行ポリシー
| Name (名前) | 制限 |
| --- | --- |
| 再試行回数 |4 |

## <a name="run-duration-and-retention"></a>実行の継続時間とリテンション期間
1 つのフロー実行に対する制限は次のとおりです。

| Name (名前) | 制限 | 備考 |
| --- | --- | --- |
| 実行の継続時間 |30 日 |承認などの保留ステップを含むワークフローが含まれます。 保留ステップは 30 日後にタイムアウトします。 |
| ストレージのリテンション期間 |30 日 |これは、実行の開始時点からです。 |
| 最小繰り返し間隔 |1 分 | |
| 最大繰り返し間隔 |500 日 | |

## <a name="looping-and-debatching-limits"></a>ループおよびバッチ解除の制限
1 つのフロー実行に対する制限は次のとおりです。

| Name (名前) | 制限 | 備考 |
| --- | --- | --- |
| ForEach 項目 |5,000 |必要に応じて、フィルター アクションを使って大きい配列をフィルター処理できます。 |
| Until 反復 |5,000 | |
| SplitOn 項目 |5,000 | |
| ForEach 並列処理 |1 | |

## <a name="definition-limits"></a>定義の制限
1 つのフローに対する制限は次のとおりです。

| Name (名前) | 制限 | 備考 |
| --- | --- | --- |
| ワークフローごとのアクション |250 |必要に応じて、入れ子になったワークフローを追加してこの機能を拡張できます。 |
| 許可されるアクションの入れ子の深さ |5 |必要に応じて、入れ子になったワークフローを追加してこの機能を拡張できます。 |
| 式あたりの最大文字 |8,192 | |
| `action`/`trigger` 名の制限 |80 | |
| `description` の長さの制限 |256 | |

## <a name="sharepoint-limits"></a>SharePoint に関する制限
Microsoft Flow および PowerApps で、Microsoft SharePoint を使用する方法には、[制限](https://powerapps.microsoft.com/tutorials/connection-sharepoint-online/)があります。

## <a name="ip-address-configuration"></a>IP アドレスの構成
Microsoft Flow の要求の送信元の IP アドレスは、フローを使用している[環境](environments-overview-admin.md)が置かれている[リージョン](regions-overview.md)によって異なります。 現在、フローのシナリオで使用可能な FQDN は発行されていません。

### <a name="logic-app-service"></a>Logic App サービス
フローからの呼び出しは、Azure Logic App サービスを直接通過します。 このような呼び出し例としては、HTTP や HTTP + OpenAPI などがあります。 これらの呼び出しは、以下の IP アドレスから送られてきます。

| Region (リージョン) | 送信 IP |
| --- | --- |
| アジア |168.63.200.173、13.75.89.159、23.97.68.172、13.75.94.173、40.83.127.19、52.175.33.254、52.163.93.214、52.187.65.81、52.187.65.155、13.76.133.155、52.163.228.93、52.163.230.166 |
| オーストラリア |13.75.153.66、104.210.89.222、104.210.89.244、13.75.149.4、104.210.91.55、104.210.90.241、13.73.115.153、40.115.78.70、40.115.78.237、13.73.114.207、13.77.3.139、13.70.159.205 |
| カナダ |52.233.29.92, 52.228.39.241, 52.228.39.244, 52.232.128.155, 52.229.120.45, 52.229.126.25 |
| ヨーロッパ |13.79.173.49、52.169.218.253、52.169.220.174、40.113.12.95、52.178.165.215、52.178.166.21、13.95.155.53、52.174.54.218、52.174.49.6、40.68.222.65、40.68.209.23、13.95.147.65 |
| インド |52.172.157.194、52.172.184.192、52.172.191.194、52.172.154.168、52.172.186.159、52.172.185.79、52.172.9.47、52.172.49.43、52.172.51.140、52.172.50.24、52.172.55.231、52.172.52.0 |
| 日本 |13.71.146.140、13.78.84.187、13.78.62.130、13.71.158.3、13.73.4.207、13.71.158.120、40.74.140.173、40.74.81.13、40.74.85.215、40.74.140.4、104.214.137.243、138.91.26.45 |
| 米国 |137.135.106.54、40.117.99.79、40.117.100.228、13.92.98.111、40.121.91.41、40.114.82.191、52.160.90.237、138.91.188.137、13.91.252.184、52.160.92.112、40.118.244.241、40.118.241.243 |

### <a name="services"></a>サービス
フローを介して接続されている API からの呼び出し (SQL API や SharePoint API など) は、以下で指定する IP アドレスから送られてきます。

| Region (リージョン) | 送信 IP |
| --- | --- |
| アジア |52.163.91.227、52.163.89.40、52.163.89.65、52.163.95.29、13.75.89.9、13.75.91.198、13.75.92.202、13.75.92.124 |
| オーストラリア |13.77.7.172、13.70.191.49、13.70.189.7、13.70.187.251、13.70.82.210、13.73.203.158、13.73.207.42、13.73.205.35 |
| カナダ |52.233.30.222、52.233.30.148、52.233.30.199、52.233.29.254、52.232.130.205、52.229.126.118、52.229.126.28、52.229.123.56 |
| ヨーロッパ |52.166.241.149、52.166.244.232、52.166.245.173、52.166.243.169、40.69.45.126、40.69.45.11、40.69.45.93、40.69.42.254 |
| インド |52.172.54.172、52.172.55.107、52.172.55.84、52.172.51.70、52.172.158.185、52.172.159.100、52.172.158.2、52.172.155.245 |
| 日本 |104.214.137.186、104.214.139.29、104.214.140.23、104.214.138.174、13.78.85.193、13.78.84.73、13.78.85.200、13.78.86.229 |
| 米国 |104.43.232.28、104.43.232.242、104.43.235.249、104.43.234.211、52.160.93.247、52.160.91.66、52.160.92.131、52.160.95.100、40.117.101.91、40.117.98.246、40.117.101.120、40.117.100.191 |
| 米国 (早期アクセス) |52.161.26.191、52.161.27.42、52.161.29.40、52.161.26.33、13.66.213.240、13.66.214.51、13.66.210.166、13.66.213.29 |

たとえば、Azure SQL Database の IP アドレスをホワイトリストに登録する場合は、これらのアドレスを使う必要があります。
