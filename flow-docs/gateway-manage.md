---
title: オンプレミス データ ゲートウェイについて | Microsoft Docs
description: Microsoft Flow でオンプレミス データ ゲートウェイを表示してインストールします。
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
ms.date: 02/05/2018
ms.author: deonhe
ms.openlocfilehash: 642cf26110a09404c8bd453f894540963904ebda
ms.sourcegitcommit: 945614d737d5909c40029a61e050302d96e1619d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "29057407"
---
# <a name="manage-an-on-premises-data-gateway-in-microsoft-flow"></a>Microsoft Flow でオンプレミス データ ゲートウェイを管理する

オンプレミス データ ゲートウェイをインストールして管理すると、Microsoft Flow を介してさまざまなクラウドベースのアプリをオンプレミスのデータやアプリと安全に統合できます。

ゲートウェイでは、次の接続を通じてオンプレミスのデータに接続することができます。

* SharePoint
* SQL Server
* Oracle
* Informix
* ファイル システム
* DB2

> [!IMPORTANT]
> Microsoft SharePoint データ ゲートウェイは、HTTP トラフィックと HTTPS トラフィックの両方をサポートするようになりました。


## <a name="prerequisites"></a>前提条件

* Microsoft Flow への[サインアップ](sign-up-sign-in.md)で使用したユーザー名とパスワード。
* ゲートウェイでの管理アクセス許可。

  インストールするゲートウェイごとに、これらのアクセス許可が既定で与えられます。 また、別のゲートウェイの管理者がそのゲートウェイのこれらのアクセス許可を与えることができます。
* ゲートウェイをサポートするライセンス。 詳しくは、[料金ページ](https://flow.microsoft.com/pricing/)の「接続」セクションをご覧ください。

> [!NOTE]
> ゲートウェイとオンプレミスの接続は、[既定の環境](environments-overview-maker.md)でのみ作成することができます。



## <a name="view-your-gateways"></a>ゲートウェイを表示する

[Microsoft Flow Web サイト](https://flow.microsoft.com)の右上隅にある歯車アイコンを選択し、**[ゲートウェイ]** を選択します。

![管理対象のゲートウェイ][1]

> [!NOTE]
> ゲートウェイへのアクセス権限を作成した場合、または PowerApps でゲートウェイへのアクセス権限が付与されている場合、Microsoft Flow の **[ゲートウェイ]** 一覧にそのゲートウェイが表示されます。



## <a name="install-a-gateway"></a>ゲートウェイのインストール

1. [ゲートウェイ インストール ウィザード](https://go.microsoft.com/fwlink/?LinkID=820580&clcid=0x409)をダウンロードします。

1. このウィザードを実行し、Microsoft Flow にサインインしたときと同じ資格情報を入力します。

    ゲートウェイは、登録と構成に成功すると、Microsoft Flow の **[ゲートウェイ]** 一覧に表示されます。

詳細については、[ゲートウェイの概要](gateway-reference.md)に関するページを参照してください。

<!-- Image references -->
[1]: ./media/manage-gateway/view-gateways.png
