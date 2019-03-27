---
title: 'サンプル: 業務プロセス フローの使用 (Dynamics 365 Customer Engagement の開発者ガイド) | Microsoft Docs'
description: このサンプルでは、エンティティ レコードのビジネス プロセス フロー インスタンスを取得する、ビジネス プロセス フロー インスタンスのアクティブなパスとそのプロセス ステージを取得する、およびアクティブなステージを変更するなどの業務プロセス フローをプログラムで操作する方法を説明します。
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.service: flow
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
ms.assetid: 7d378504-b4b2-4a09-838c-69ee094072ef
caps.latest.revision: 15
author: msftman
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: 6f3543b666e471d1f7fa0fe24fc718e50d35aec8
ms.sourcegitcommit: 24da014ea8db8e59f097c4622d1e2cca9a4d1709
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58352966"
---
# <a name="sample-work-with-business-process-flows"></a>サンプル: 業務プロセス フローの使用

このサンプルでは、エンティティ レコードのビジネス プロセス フロー インスタンスを取得する、ビジネス プロセス フロー インスタンスのアクティブなパスとそのプロセス ステージを取得する、およびアクティブなステージを変更するなどの業務プロセス フローをプログラムで操作する方法を説明します。 これらの概念については、「[Work with business process flows using code](business-process-flows-code.md)」 (コードを使用して業務プロセス フローを操作する) を参照してください  

 このサンプルをダウンロードするには、「[サンプル: 業務プロセス フローの使用](https://go.microsoft.com/fwlink/p/?LinkId=846108)」をご覧ください。  

<a name="BKMK_Prerequisites"></a>   
## <a name="prerequisites"></a>前提条件  
 サンプルを実行するには、次が必要です。  

1. Common Data Service 環境にアクセスできる。  

2. このサンプルで使用されている潜在顧客、営業案件、およびワークフロー エンティティと業務プロセス フロー定義エンティティ レコードへの適切なアクセス許可を持つ。  

3. サンプルを実行するために Visual Studio 2015 以降がある。  

4. サンプル プロジェクトをダウンロードし、サンプル プロジェクトで使用されている NuGet パッケージを復元するためのインターネット接続がある。  

<a name="BKMK_WhatThisSampleDoes"></a>   
## <a name="what-this-sample-does"></a>このサンプルで実行すること  

1.  サンプル潜在顧客レコードを作成します。 これにより、潜在顧客レコードに "Lead To Opportunity Sales Process\(潜在顧客から営業案件への営業プロセス\)" 業務プロセス フローのインスタンスが自動的に作成されます。  

2.  潜在顧客レコードを営業案件レコードに変換します。  


4.  `RetrieveProcessInstances` メッセージを使用して、"営業案件" レコードに関連付けられている業務プロセス フロー インスタンスを取得します。 返されたコレクションの先頭のレコードは、アクティブな業務プロセス フロー インスタンスで、この例では "Lead To Opportunity Sales Process\(潜在顧客から営業案件への営業プロセス\)" になります。  

5.  `RetrieveActivePath` メッセージを使用して、"Lead To Opportunity Sales Process\(潜在顧客から営業案件への営業プロセス\)" インスタンスのアクティブなパスとプロセス ステージを取得します。  

6.  "Lead To Opportunity Sales Process\(潜在顧客から営業案件への営業プロセス\)" インスタンスの現在アクティブなステージを取得し、次のステージに移動するかどうかをユーザーに確認します。 移動を確認したら、"Lead To Opportunity Sales Process\(潜在顧客から営業案件への営業プロセス\)" インスタンスのアクティブなステージとして、アクティブなパスに次のステージを設定します。  

7.  最後に、サンプルの実行中に作成されたレコードを削除するかどうかをユーザーに確認します。  

     サンプルの出力を次に示します。  

    ![サンプル出力](media/work-with-bpf-sample-output.png "サンプル出力")  

<a name="BKMK_runSample"></a>   
## <a name="run-the-sample"></a>サンプルを実行する  

1. WorkWithBPF Visual Studio サンプル プロジェクトを[ダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=846108)し、コンピューター上のフォルダーに抽出します。  

2. 抽出したフォルダー内の `WorkWithBPF.sln` ファイルを見つけて、Visual Studio で開きます。  

3. サンプル プロジェクトでは、サンプルを実行する前に復元する必要がある NuGet パッケージが使用されています。 Visual Studio で NuGet パッケージの自動復元が有効になっていることを確認します。 詳細情報: [NuGet パッケージの復元の有効化と無効化](https://go.microsoft.com/fwlink/?linkid=846106)  

    または、**[プロジェクト]** > **[NuGet パッケージの管理]** を選択し、**[復元]** を選択して、サンプルで使用されているパッケージを手動で復元します。  

4. F5 キーを押すか、**[デバッグ]** > **[デバッグ開始]** を選択します。  

5. これまでどのサンプルも実行したことがない場合は、コードを実行するために情報を入力する必要があります。実行したことがある場合は、以前に設定したいずれかのインスタンスの番号を入力します。  


   |                                 プロンプト                                  |                                                                                             説明                                                                                             |
   |-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      Enter a Dynamics 365 server name and port\(Dynamics 365 のサーバー名とポートを入力してください\) [crm.dynamics.com]       | Dynamics 365 サーバーの名前を入力します。 既定値は、北米で Dynamics 365 (オンライン) (crm.dynamics.com) です。<br /><br /> 例: <br />crm5.dynamics.com |
   | Is this organization provisioned in Microsoft online services\(この組織は Microsoft Online Services でプロビジョニングされましたか\) (y/n) [n] |                                                 Microsoft Online Services でプロビジョニングされた組織の場合は、**y** を入力します。 それ以外の場合は、**n** を入力します。                                                  |
   |                          Enter domain\username\(ドメイン\ユーザー名を入力してください\)                          |                                                                                    お使いの Microsoft アカウントを入力します。                                                                                     |
   |                             Enter password\(パスワードを入力してください\)                              |                      パスワードを入力します。 ウィンドウに文字が "\*" と表示されます。 パスワードは、後で再利用するために Microsoft 資格情報マネージャーで安全に保存されます。                       |
   |                Specify an organization number\(組織番号を指定してください\) (1-n) [1]                 |                      所属する表示された組織の一覧から、対応する番号を入力します。 既定値は 1 で、一覧の先頭の組織を示します。                       |


6. サンプルでは、「[このサンプルで実行すること](#what-this-sample-does)」で説明されている操作が実行され、追加のオプションの入力が求められる場合があります。  

7. サンプルが完了したら、Enter キーを押してコンソール ウィンドウを閉じます。  

