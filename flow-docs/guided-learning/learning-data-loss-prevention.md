---
title: "データ損失防止 (DLP) ポリシーを使用する | Microsoft Docs"
description: "Microsoft Flow を使ってタスクを自動化するときに、データ損失防止ポリシーを使って、データを共有できるサービスを管理する方法を説明します。"
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: vls4RPVP5xE
courseduration: 6m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 08/16/2017
ms.author: deonhe
ms.openlocfilehash: 2e69fd07103cb16e6c91476462f39586810b4a5d
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="use-data-loss-prevention-dlp-policies"></a>データ損失防止 (DLP) ポリシーを使用する
[Microsoft Flow](https://flow.microsoft.com) でワークフローを構築する際に利用できる[サービス](https://flow.microsoft.com/services)の数が増えると、SharePoint や Salesforce のような企業サービスに保存されている企業の重要な機密データを守る必要がでてきます。 会社の機密データを Twitter や Facebook のような消費者向けサービスに公開しないためのポリシーを作成する必要があります。 Microsoft Flow を利用すれば、**データ損失防止** (DLP) ポリシーを簡単に作成できます。ユーザーがフローを作成するとき、会社のデータが共有される消費者向けサービスを厳重に管理できます。  

## <a name="terms-you-should-get-familiar-with"></a>重要な用語
| 用語 | 説明 |
| --- | --- |
| **DLP** |これは Data Loss Prevention (データ損失防止) の省略形です。 DLP ポリシーを作成し、**サービス**間のデータ共有を管理します。 |
| **サービス** |[サービス](https://flow.microsoft.com/services)とは、Salesforce、SharePoint、Twitter のようなアプリケーションのことです。 フローの作成時にこのようなサービスが利用されます。 |
| **データ グループ** |サービスの論理グループです。 データの共有を許可するサービスを同じデータ グループに配置します。 **Business data only** (ビジネス データのみ) と **No business data allowed** (ビジネス データ禁止) という 2 つのデータ グループを利用できます。 |
| **環境** |DLP は[環境](../environments-overview-admin.md)に適用されます。 環境にはユーザーが含まれます。 |
| **ユーザー** |ユーザーは DLP ポリシーが適用される環境の組織に属します。 |
| **フロー** |フローは、利用可能なサービスを組み合わせて使用するワークフロー アプリです。 |

## <a name="all-about-how-dlp-policies-work"></a>DLP ポリシーの動作の概要
DLP ポリシーとは、簡単に言えば、相互排他的な 2 つのデータ グループの 1 つに各サービスを配置するルールに名前を付けたものです。 このルールが環境に適用されます。 環境はユーザーを論理的にグループにしたものです。 ユーザーは、異なるデータ グループに配置したサービス間でデータを共有するフローを作成できません。 つまり、ユーザーが作成できるのは、**1 つ**のデータ グループ内のサービス間でデータを共有するフローだけです。 データ グループをまたいで共有することはできません。  

| **データ グループ名** | **データ グループの説明** |
| --- | --- |
| **ビジネス データのみ** |このグループのすべてのサービスが互いにデータを共有できます。 **ビジネス データ禁止**データ グループとデータを共有することはできません。 |
| **ビジネス データ禁止** |このグループのすべてのサービスが互いにデータを共有できます。 **ビジネス データのみ**データ グループとデータを共有することはできません。 |

**注**: 1 つのデータ グループにサービスを追加すると、他のデータ グループからそのサービスが自動的に削除されます。 たとえば、Twitter が現在、**ビジネス データのみ**データ グループに読み込まれているとき、ビジネス データを Twitter と共有しない場合、Twitter サービスを**ビジネス データ禁止**データ グループに追加します。 **ビジネス データのみ**データ グループから Twitter が削除されます。

## <a name="heres-what-you-need-to-create-a-dlp"></a>このような場合に DLP を作成します。
* Microsoft Flow [管理センター](https://admin.flow.microsoft.com)へのアクセス  
* 環境の監理者の役割のアカウント  
* 環境とそれに割り当てられたユーザー  

## <a name="create-a-dlp-policy"></a>DLP ポリシーを作成する
DLP ポリシーの作成方法は次のようになります。  

1. ポリシーに名前を付ける
2. ポリシーを適用する環境を選択する
3. 2 つのデータ グループのいずれかにサービスを追加する 特定のグループに配置されているサービスのみがデータを共有できます。2 つのデータ グループに配置されているサービス間でデータを共有するフローを作成すると、保存したときにフローが自動的にブロックされます。  

利用できる DLP ポリシーの詳細は[こちら](../prevent-data-loss.md)でも確認できます。  

## <a name="examples"></a>例
* SharePoint、Office 365 ユーザー、Office 365 Outlook、OneDrive for Business、Dynamics 365、SQL Server、Salesforce の間だけでビジネス データを共有できるようにフローを制限するポリシーを作成すると、次のようになります。  
  ![](./media/learning-data-loss-prevention/a-few-business-centric-services.png)  
* SharePoint データを共有するフローの作成を特定の環境に属するユーザーに対して禁止するポリシーを作成すると、次のようになります。 SharePoint が**ビジネス データのみ**データ グループの唯一のサービスになっていることに注目してください。  
  ![ビジネス データのみ](./media/learning-data-loss-prevention/sharepoint-only-no-sharing-guided-learning.png)

