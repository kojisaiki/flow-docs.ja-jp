---
title: オンプレミス データ ゲートウェイについて | Microsoft Docs
description: オンプレミス データ ゲートウェイに関する参考、インストール、トラブルシューティング情報
services: ''
suite: flow
documentationcenter: na
author: MSFTMan
manager: KFile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/15/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 95081295bfe0fd6c904876aaf70974575a7986c1
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690907"
---
# <a name="understand-on-premises-data-gateways-for-microsoft-flow"></a>Microsoft Flow のオンプレミス データ ゲートウェイについて
オンプレミス データ ゲートウェイと Microsoft Flow を利用し、Microsoft SQL Server などのオンプレミス データ ソースに安全に接続します。

## <a name="installation-and-configuration"></a>インストールと構成
### <a name="prerequisites"></a>前提条件
最小:

* [.NET Framework 4.6](https://www.microsoft.com/download/details.aspx?id=48130)
* 64 ビット版の Windows 7 または Windows Server 2008 R2 (またはそれ以降)

推奨:

* 8 コア CPU
* 8 GB メモリ
* 64 ビット版の Windows Server 2012 R2 (またはそれ以降)

関連する考慮事項:

* ゲートウェイをドメイン コントローラーにインストールすることはできません。
* ゲートウェイは、電源オフ、スリープ状態、またはインターネット未接続状態の可能性があるコンピューター (ノート PC など) にインストールしないでください。
* ワイヤレス ネットワーク経由では、ゲートウェイのパフォーマンスが低下する可能性があります。

## <a name="install-a-gateway"></a>ゲートウェイのインストール
> [!IMPORTANT]
> Microsoft SharePoint データ ゲートウェイは、HTTP トラフィックと HTTPS トラフィックの両方をサポートするようになりました。
> 
> 

1. [インストーラーをダウンロード](https://go.microsoft.com/fwlink/?LinkID=820931)し、実行します。
   
    ![インストーラーの実行](./media/gateway-reference/run-installer.png)
2. インストール ウィザードの最初の画面で、**[次へ]** を選択し、ノート PC へのゲートウェイのインストールに関する通知を確認します。
   
    ![通知画面](./media/gateway-reference/laptop-reminder.png)
3. インストール場所を選択します。
4. 使用条件とプライバシーに関する声明に同意します。
5. **[インストール]** を選択します。
   
    ![場所画面](./media/gateway-reference/location.png)
6. **[ユーザー アカウント制御]** ダイアログ ボックスで、**[はい]** を選択して続行します。
7. **[オンプレミス データ ゲートウェイ]** 画面で、ゲートウェイのサインインで使用するアカウントのメール アドレスを入力し、**[サインイン]** を選択し、サインイン プロセスを完了します。
   
    ![サインイン](./media/gateway-reference/sign-in.png)

## <a name="register-new-gateway-or-take-over-existing-gateway"></a>新しいゲートウェイを登録するか、既存のゲートウェイを継承する
1. **[このコンピューターに新しいゲートウェイを登録します]** または **[既存のゲートウェイを移行、復元、または置き換えます]** を選択し、**[次へ]** を選択します。
   
    ![新規または既存の選択](./media/gateway-reference/new-existing.png)
2. 新しいゲートウェイを構成するには、**[New on-premises data gateway name]\(新しいオンプレミス データ ゲートウェイの名前\)** ボックスに名前を入力し、**[回復キー]** ボックスに回復キーを入力し、**[回復キーの確認]** ボックスに同じ回復キーを入力します。 **[構成]** を選択し、**[閉じる]** を選択します。
   
    ![新しいゲートウェイの構成](./media/gateway-reference/configure-new.png)
3. 8 文字以上を含む回復キーを指定し、安全な場所に保存しておきます。 このキーは、ゲートウェイを移行、復元、または置き換える場合に必要になります。
4. 既存のゲートウェイを移行、復元、または置き換えるには、ゲートウェイの名前と回復キーを指定し、**[構成]** を選択して、追加の指示に従います。
   
    ![既存のゲートウェイの回復](./media/gateway-reference/recover-existing.png)

## <a name="restart-the-gateway"></a>ゲートウェイの再起動
このゲートウェイは Windows サービスとして実行されるため、その他の Windows サービスと同様、複数の方法で開始および停止できます。 たとえば、ゲートウェイが実行されているコンピューター上で、管理者特権のアクセス許可を使用してコマンド プロンプトを開き、次のコマンドのいずれかを実行できます。

* サービスを停止するには、次のコマンドを実行します。

```batchfile
    net stop PBIEgwService
```

* サービスを開始するには、次のコマンドを実行します。

```batchfile
    net start PBIEgwService
```

## <a name="configure-a-firewall-or-proxy"></a>ファイアウォールまたはプロキシの構成
ゲートウェイのプロキシ情報を指定する方法については、[プロキシ設定の構成](https://powerbi.microsoft.com/documentation/powerbi-gateway-proxy/)に関するページを参照してください。

PowerShell プロンプトから次のコマンドを実行することで、ファイアウォール (またはプロキシ) が接続をブロックしている可能性があるかどうかを確認できます。 このコマンドにより、Azure Service Bus への接続性がテストされます。 このコマンドは、ネットワーク接続をテストするだけで、クラウド サーバー サービスやゲートウェイとは関係ありません。 コンピューターがインターネットに接続されているかどうかを確認する際に役立ちます。

```powershell
Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350
```

結果は次の出力のようになります。 **TcpTestSucceeded** が *true* ではない場合は、ファイアウォールによってブロックされている可能性があります。

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

すべてを網羅する場合は、**ComputerName** と **Port** の値を、このトピックの「**ポートの構成**」に記載されている値に置き換えます。

ファイアウォールが Azure Service Bus から Azure データ センターへの接続をブロックしている場合もあります。 そのような場合は、これらのデータ センターでお住まいの地域の [IP アドレス](https://www.microsoft.com/download/details.aspx?id=41653)すべてをホワイトリストに指定 (ブロック解除) します。

## <a name="configure-ports"></a>ポートの構成
このゲートウェイは、Azure Service Bus に対する送信接続を作成します。 通信は、送信ポート TCP 443 (既定)、5671、5672、9350 ～ 9354 で行われます。 このゲートウェイには受信ポートが必要ありません。

ハイブリッド ソリューションの詳細については、[こちら](https://azure.microsoft.com/documentation/articles/service-bus-fundamentals-hybrid-solutions/)を参照してください。

| ドメイン名 | 送信ポート | 説明 |
| --- | --- | --- |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671 ～ 5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443、9350 ～ 9354 |TCP を経由する Service Bus Relay 上のリスナー (Access Control のトークン取得には 443 が必要) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| *.msftncsi.com |443 |ゲートウェイに到達できない場合にインターネット接続をテストするために使用されます。 |

ドメインではなく IP アドレスをホワイトリストに指定する必要がある場合は、[Microsoft Azure Datacenter IP Ranges の一覧](https://www.microsoft.com/download/details.aspx?id=41653)をダウンロードして使用できます。 場合によっては、Azure Service Bus の接続が完全修飾ドメイン名ではなく IP アドレスで行われる可能性があります。

## <a name="sign-in-account"></a>サインイン アカウント
ユーザーは、職場または学校アカウントでサインインします。 これは組織のアカウントです。 Office 365 サービスにサインアップしても、勤務先メール アドレスを指定しなかった場合は、nancy@contoso.onmicrosoft.com のようになります。 クラウド サービス内では、お使いのアカウントが Azure Active Directory (AAD) のテナント内に保存されます。 ほとんどの場合、AAD アカウントの UPN はメール アドレスと一致します。

## <a name="windows-service-account"></a>Windows サービス アカウント
オンプレミス データ ゲートウェイは、Windows サービスのログオン資格情報に *NT SERVICE\PBIEgwService* を使用するよう構成されています。 既定では、この資格情報に、サービスとしてログオンする権限があります。 これは、ゲートウェイのインストール先コンピューターとの関連で存在します。

これは、オンプレミスのデータ ソースへの接続に使用するアカウントでも、クラウド サービスへのサインインに使用する職場または学校アカウントでもありません。

## <a name="tenant-level-administration"></a>テナント レベルの管理

現時点では、テナント管理者は他のユーザーがインストールして構成したすべてのゲートウェイを 1 箇所から管理することはできません。  テナント管理者には、組織内のユーザーがインストールするすべてのゲートウェイに対して自分を管理者として追加するようユーザーに求めることをお勧めします。 このようにすれば、[ゲートウェイ設定] ページまたは [PowerShell コマンド](https://docs.microsoft.com/power-bi/service-gateway-high-availability-clusters#powershell-support-for-gateway-clusters)を使って組織内のすべてのゲートウェイを管理できます。

## <a name="frequently-asked-questions"></a>よく寄せられる質問
### <a name="general-questions"></a>一般的な質問
**質問:** ゲートウェイではどのデータ ソースがサポートされていますか。
**回答:**

* SQL Server
* SharePoint
* Oracle
* Informix
* ファイル システム
* DB2

**質問:** SQL Azure など、クラウド内のデータ ソースにはゲートウェイが必要ですか。
**回答:** いいえ。 ゲートウェイは、オンプレミスのデータ ソースのみに接続します。

**質問:** 実際の Windows サービスはどのように呼ばれていますか。
**回答:** [サービス] では、このゲートウェイは **Power BI Enterprise Gateway サービス**という名前で表示されます。

**質問:** クラウドからゲートウェイへの受信接続はありますか。
**回答:** いいえ。 ゲートウェイは、Azure Service Bus への送信接続を使用します。

**質問:** 送信接続をブロックしたらどうなりますか。 何を開く必要がありますか。
**回答:** ゲートウェイで使用する[ポート](gateway-reference.md#configure-ports)とホストを確認してください。

**質問:** ゲートウェイをデータ ソースと同じコンピューターにインストールする必要がありますか。
**回答:** いいえ。 ゲートウェイは、指定された接続情報を使用してデータ ソースに接続します。 この意味では、ゲートウェイをクライアント アプリケーションと考えてください。 ゲートウェイで必要なのは、指定されたサーバー名に接続できることだけです。

**質問:** ゲートウェイからデータ ソースに対してクエリを実行するための待ち時間はどのくらいですか。 最適なアーキテクチャは何ですか。
**回答:** ネットワーク待ち時間を短縮するには、できる限りデータ ソースの近くにゲートウェイをインストールしてください。 実際のデータ ソース上にゲートウェイをインストールできると、発生する待ち時間は最小限に抑えられます。 データ センターについても検討してください。 たとえば、サービスで米国西部のデータ センターを使用していて、SQL Server を Azure VM でホストしている場合は、この Azure VM も米国西部に配置することをお勧めします。 そうすることで、待ち時間が最小限に抑えられ、Azure VM での送信料金が回避されます。

**質問:** ネットワーク帯域幅に関する要件はありますか。
**回答:** ネットワーク接続に十分なスループットを確保することをお勧めします。 環境はどれも異なるため、送信されるデータの量によって結果に影響があります。 ExpressRoute を使用すると、オンプレミスと Azure データ センター間にある程度のスループットを保証できるようになります。

サードパーティ製のツール [Azure Speed Test アプリ](http://azurespeedtest.azurewebsites.net/)を使用すると、スループットを計ることができます。

**質問:** ゲートウェイ Windows サービスを Azure Active Directory アカウントで実行できますか。
**回答:** いいえ。 Windows サービスには、有効な Windows アカウントが必要です。 既定では、サービスの SID *NT SERVICE\PBIEgwService* を使用して実行されます。

**質問:** 結果はどのようにクラウドに送信されますか。
**回答:** 結果は Azure Service Bus を利用して送信されます。 詳細については、「[ゲートウェイのしくみ](gateway-reference.md#how-the-gateway-works)」を参照してください。

**質問:** 資格情報はどこに保存されていますか。
**回答:** データ ソース用に入力した資格情報は、暗号化され、ゲートウェイ クラウド サービスに保存されます。 資格情報は、オンプレミスのゲートウェイで暗号化が解除されます。

### <a name="high-availabilitydisaster-recovery"></a>高可用性と障害復旧
**質問:** ゲートウェイで高可用性のシナリオを実現するためのプランはありますか。
**回答:** はい、高可用性は[利用できるようになっています](https://flow.microsoft.com/blog/gateway-ha-increased-apply-to-each)。

**質問:** 障害復旧にはどのオプションを使用できますか。
**回答:** ゲートウェイの復元または移動には、回復キーを使用できます。

**質問:** 回復キーの利点は何ですか。
**回答:** ゲートウェイの設定を移行したり、回復したりできます。

### <a name="troubleshooting-questions"></a>トラブルシューティングに関する質問
**質問:** ゲートウェイ ログはどこにありますか。
**回答:** このトピックの後半にある「[ツール](gateway-reference.md#tools)」を参照してください。

**質問:** オンプレミスのデータ ソースにどのようなクエリが送信されているかを確認する方法を教えてください。
**回答:** クエリ トレースを有効にすることができます。このトレースには、送信されるクエリが含まれます。 トラブルシューティングが完了したら、忘れずに元の値に戻してください。 クエリ トレースを有効な状態にしておくと、ログの容量が大きくなります。

クエリをトレースするためにデータ ソースに用意されているツールを確認することもできます。 たとえば、SQL Server と Analysis Services に拡張イベントまたは SQL Profiler を使用できます。

## <a name="how-the-gateway-works"></a>ゲートウェイのしくみ
![しくみ](./media/gateway-reference/gateway-arch.png)

オンプレミスのデータ ソースに接続されている要素をユーザーが操作すると、次のようになります。

1. クラウド サービスによって、クエリが作成され、データ ソース用に暗号化された資格情報と共に、ゲートウェイで処理するためにキューに送信されます。
2. ゲートウェイ クラウド サービスは、クエリを分析し、要求を [Azure Service Bus](https://azure.microsoft.com/documentation/services/service-bus/) にプッシュします。
3. オンプレミス データ ゲートウェイは、Azure Service Bus へのポーリングを実行して保留中の要求があるかどうかを確認します。
4. ゲートウェイは、クエリを取得して、資格情報の暗号化を解除し、その資格情報を使用してデータ ソースに接続します。
5. ゲートウェイは、クエリを実行するためにデータ ソースに送信します。
6. 結果は、データ ソースからゲートウェイに返され、さらにクラウド サービスに送信されます。 その後、その結果がサービスで使用されます。

## <a name="troubleshooting"></a>トラブルシューティング
### <a name="update-to-the-latest-version"></a>最新バージョンに更新する
多くの問題は、ゲートウェイのバージョンが最新でない場合に発生します。 最新のバージョンを使用していることを確認してください。  ゲートウェイを最近更新していない場合、最新版をインストールし、インストール後に問題が解消されるか確認してください。

#### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>エラー: ユーザーをグループに追加できませんでした。  (-2147463168   PBIEgwService   Performance Log Users   )
ドメイン コントロールにゲートウェイをインストールしようとすると、このエラーが発生することがあります。ドメイン コントロールへのインストールはサポートされていません。 ゲートウェイは、ドメイン コントローラーではないコンピューター上にインストールする必要があります。

## <a name="tools"></a>ツール
### <a name="collecting-logs-from-the-gateway-configurator"></a>ゲートウェイ構成ウィザードからのログ収集
ゲートウェイのログをいくつか収集することができます。 必ず最初にログを確認してください。

1. インストーラーのログ
   
    %localappdata%\Temp\On-premises_data_gateway_*.log
2. 構成のログ
   
    %localappdata%\Microsoft\on-premises data gateway\GatewayConfigurator*.log
3. エンタープライズ ゲートウェイ サービスのログ
   
    C:\Users\PBIEgwService\AppData\Local\Microsoft\on-premises data gateway\Gateway*.log
4. イベント ログ

**On-premises data gateway service** のイベント ログは、**[アプリケーションとサービス ログ]** に表示されています。

![イベント ログ](./media/gateway-reference/event-logs.png)

### <a name="fiddler-trace"></a>Fiddler のトレース
[Fiddler](http://www.telerik.com/fiddler) は、HTTP トラフィックを監視する Telerik 提供の無償ツールです。  クライアント コンピューターから、Power BI サービスとのやりとりを確認できます。 これにより、エラーやその他の関連情報が表示される場合もあります。

