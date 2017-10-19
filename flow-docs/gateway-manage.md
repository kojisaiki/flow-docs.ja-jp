---
title: "オンプレミス データ ゲートウェイについて | Microsoft Docs"
description: "Microsoft Flow でオンプレミス データ ゲートウェイを表示してインストールします。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/15/2017
ms.author: deonhe
ms.openlocfilehash: 41f5d40ca2ad5fcce3a7967beef7104dd532b1d8
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
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
> Microsoft SharePoint データ ゲートウェイは、HTTP トラフィックをサポートしますが、HTTPS トラフィックはサポートしません。
> 
> 

## <a name="prerequisites"></a>前提条件
* Microsoft Flow への[サインアップ](sign-up-sign-in.md)で使用したユーザー名とパスワード。
* ゲートウェイでの管理アクセス許可。
  
  これらのアクセス許可は、インストールするゲートウェイごとに既定で付与されます。また、他のゲートウェイの管理者から、そのゲートウェイに対するこのアクセス許可が付与される場合もあります。
* ゲートウェイをサポートするライセンス。 詳しくは、[料金ページ](https://flow.microsoft.com/pricing/)の「接続」セクションをご覧ください。
* ゲートウェイとオンプレミスの接続は、[既定の環境](environments-overview-maker.md)でのみ作成することができます。

## <a name="view-your-gateways"></a>ゲートウェイを表示する
[Microsoft Flow Web サイト](https://flow.microsoft.com)の右上隅にある歯車アイコンをクリックまたはタップし、[**ゲートウェイ**] をクリックまたはタップします。

![管理対象のゲートウェイ][1]

**注**: ゲートウェイへのアクセス権限を作成した場合、または PowerApps でゲートウェイへのアクセス権限が付与されている場合、Microsoft Flow の [**ゲートウェイ**] 一覧にそのゲートウェイが表示されます。

## <a name="install-a-gateway"></a>ゲートウェイのインストール
1. [ゲートウェイ インストール ウィザード](http://go.microsoft.com/fwlink/?LinkID=820580&clcid=0x409)をダウンロードします。
   
    このウィザードは、[Microsoft Flow Web サイト](https://flow.microsoft.com)の右上隅にある歯車をクリックまたはタップして、[**ゲートウェイ**] をクリックまたはタップし、[**ゲートウェイの作成**] をクリックまたはタップしてダウンロードすることもできます。
   
    ![ゲートウェイのインストール][2]
2. このウィザードを実行し、Microsoft Flow にサインインしたときと同じ資格情報を入力します。
   
    ゲートウェイは、登録と構成に成功すると、Microsoft Flow の [**ゲートウェイ**] 一覧に表示されます。

詳細については、[ゲートウェイの概要](gateway-reference.md)に関するページを参照してください。

<!-- Image references -->
[1]: ./media/manage-gateway/view-gateways.png
[2]: ./media/manage-gateway/list-gateways.png
