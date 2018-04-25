---
title: データのフィルターとコピー | Microsoft Docs
description: Microsoft Flow を使用して、データをフィルターし、ソースからターゲットにコピーする方法を学習します
services: ''
suite: flow
documentationcenter: na
author: MSFTMan
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/21/2017
ms.author: deonhe
ms.openlocfilehash: 7c182328c341043ffc155a679f39bcbc2130a0bc
ms.sourcegitcommit: d00c10759d4afb54517a0b1032f8d0a509006d5b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="filter-and-copy-data-with-microsoft-flow"></a>Microsoft Flow を使用するデータのフィルターとコピー
このチュートリアルでは、新しい項目または変更された項目のソースを監視し、それらの変更をターゲットにコピーするフローを作成する方法を示します。 ユーザーがある場所にデータを入力する場合に、チームで別の場所または形式のデータが必要な場合、このようなフローを作成できます。

このチュートリアルで Microsoft SharePoint[ リスト](https://support.office.com/article/SharePoint-lists-I-An-introduction-f11cd5fe-bc87-4f9e-9bfe-bbd87a22a194) (ソース) から [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) テーブル (ターゲット) にデータをコピーする場合、Microsoft Flow でサポートされる [150 を超えるサービス](https://flow.microsoft.com/connectors/)のどのサービス間でもデータをコピーできます。

> [!IMPORTANT]
> 双方向の同期がサポートされていないため、ターゲットで行われた変更内容はソースにコピーされません。 双方向の同期を設定しようとしている場合は、ソースとターゲット間で変更内容が無限に送信される無限ループを作成します。
> 
> 

## <a name="prerequisites"></a>前提条件
* データのソースとターゲットへのアクセス権がある。 このチュートリアルには、ソースとターゲットを作成する手順は含まれていません。
* [Microsoft Flow](https://flow.microsoft.com) のアクセス権を持っている
* データの格納方法の基本を理解している。
* フロー作成の基本をよく理解している。 [アクション、トリガー](multi-step-logic-flow.md#add-another-action)、および[条件](add-condition.md)の追加方法を確認することができます。 次の手順では、これらのアクションの実行方法がわかっていることを前提とします。

> [!TIP]
> ソースとターゲット内の列名がすべて一致する必要はありませんが、項目を挿入または更新する際にすべての*必須*列にデータを指定する必要があります。 Microsoft Flow で自動的に必須フィールドが識別されます。
> 
> 

## <a name="quick-overview-of-the-steps"></a>手順の概要
Microsoft Flow に慣れている場合は、以下の簡単な手順を使用して、データをデータ ソースから別の場所にコピーできます。

1. 監視するソースと、変更データのコピー先を特定します。 両方にアクセスできることを確認します。
2. ソースとターゲット内の項目を一意に識別する 1 つ以上の列を特定します。 次の例では、**タイトル**列を使用しますが、任意の列 (複数可) を使用することができます。
3. ソースの変更を監視するトリガーを設定します。
4. ターゲットを検索して、変更された項目が存在するかどうかを判断します。
5. 次のように**条件**を使用します。
   * 新しい項目または変更された項目がターゲットに存在しない場合は、作成します。
   * 新しい項目または変更された項目がターゲットに存在する場合は、更新します。
6. フローをトリガーし、新しい項目または変更された項目がソースからターゲットにコピーされていることを確認します。

> [!NOTE]
> 以前に SharePoint または Azure SQL Database への接続を作成しており、サインインを求められた場合は、表示される指示に従います。
> 
> 

フローの詳しい作成手順を以下に示します。

## <a name="monitor-the-source-for-changes"></a>ソースの変更を監視する
1. [Microsoft Flow](https://flow.microsoft.com) にサインインし、**[マイ フロー]** > **[一から作成]** の順に選択します。
2. **SharePoint** を検索し、トリガーのリストから **[SharePoint - 項目が作成または変更されたとき]** トリガーを選択します。
3. **サイト アドレス**を入力してから、**[項目が作成またはされたとき]** カードで **[リスト名]** を選択します。
   
    フローで新しい項目または更新された項目を監視する、SharePoint リストの **[サイト アドレス]** と **[リスト名]** を指定します。
   
    ![SharePoint のトリガーを構成する](media/odata-filters/configure-sharepoint-trigger.png)

## <a name="search-the-destination-for-the-new-or-changed-item"></a>ターゲットで新しい項目または変更された項目を検索する
ここでは、**[SQL Server - 行の取得]** アクションを使用して、ターゲットで新しい項目または変更された項目を検索します。

1. **[新しいステップ]**  >  **[アクションの追加]** を選択します。
2. **[行の取得]** を検索し、**[SQL Server - 行の取得]** を選択して、**[テーブル名]** リストから監視するテーブルを選択します。
3. **[詳細オプションの表示]** を選択します。
4. **[フィルター クエリ]** ボックスに「**Title eq '**」と入力し、動的コンテンツ リストから**タイトル** トークンを選択して「**'**」と入力します。
   
    前の手順では、ソースとターゲットで行のタイトルが一致していることを前提としています。
   
    **[行の取得]** カードは次の図のようになります。
   
    ![ターゲット データベースから項目を取得してみる](media/odata-filters/configure-sql-get-rows-action.png)

## <a name="check-if-the-new-or-changed-item-was-found"></a>新しい項目または変更された項目が検出されたかどうかを確認する
**[新しいステップ]** > **[条件の追加]** を選択して、**条件**カードを開きます。

条件カードで、次のようにします。

1. 左側のボックスを選択します。
   
    **[このフローで使用されるアプリやコネクタから動的なコンテンツを追加します]** リストが開きます。
2. **[行の取得]** カテゴリから **[値]** を選択します。
   
   > [!TIP]
   > **[行の取得]** カテゴリから**値**が選択されたことを確認します。 **[項目が作成または変更されたとき]** カテゴリからは**値**を選択しないでください。
   > 
   > 
3. 中央のボックスのリストから **[と等しい]** を選択します。
4. 右側のボックスに「**0**」 (ゼロ) を入力します。
   
    **条件**カードは次のイメージのようになります。
   
    ![条件を構成する](media/odata-filters/configure-condition.png)
5. **[詳細設定モードでの編集]** を選択します。
   
    詳細設定モードが開くと、ボックスに **\@equals(body('Get_rows')?['value'], 0)** という式が表示されます。 **body('Get_items')?['value']** 関数の周りに **length()** を追加して、この式を編集します。 式全体は、**@equals(length(body('Get_rows')?['value']), 0)** のようになります。
   
    **条件**カードは次のイメージのようになります。
   
    ![条件を構成する](media/odata-filters/configure-condition-add-length.png)
   
   > [!TIP]
   > **length()** 関数を追加すると、フローで**値**リストを確認し、それに項目が含まれているかどうかを判別できます。
   > 
   > 

フローでターゲットから項目が取得された場合に考えられる結果は 2 つあります。

| 結果 | 次のステップ |
| --- | --- |
| 項目が存在する場合 |[項目を更新する](odata-filters.md#update-the-item-in-the-destination) |
| 項目が存在しない場合 |[新しい項目を作成する](odata-filters.md#create-the-item-in-the-destination) |

> [!NOTE]
> 次の**行の挿入**カードと**行の更新**カードのイメージは実際のものと異なる可能性があります。これらのカードには、フローで使用されている Azure SQL Database テーブルの列の名前が表示されるためです。
> 
> 

## <a name="create-the-item-in-the-destination"></a>ターゲットで項目を作成する
ターゲットに項目が存在しない場合は、**[SQL Server - 行の挿入]** アクションを使用して作成します。

**条件**の **If yes** 分岐では、次のようにします。

1. **[アクションの追加]** を選択し、**行の挿入**を検索して、**[SQL Server - 行の挿入]** を選択します。
   
    **行の挿入**カードが開きます。
2. **[テーブル名]** リストから、新しい項目を挿入するテーブルを選択します。
   
    **行の挿入**カードが展開され、選択したテーブルにすべてのフィールドが表示されます。 アスタリスク (*) の付いたフィールドは必須であり、行を有効にするために設定する必要があります。
3. 設定する各フィールドを選択し、データを入力します。
   
    データを手動で入力することも、**動的コンテンツ**から 1 つ以上のトークンを選択することも、フィールドにテキストとトークンを組み合わせて入力することもできます。
   
    **行の挿入**カードは次のイメージのようになります。
   
    ![条件を構成する](media/odata-filters/insert-row.png)

## <a name="update-the-item-in-the-destination"></a>ターゲットで項目を更新する
項目がターゲットに存在する場合は、変更内容でそれを更新します。

1. **条件**の **If no** 分岐に **[SQL Server - 行の更新]** アクションを追加します。
2. このドキュメントの[項目の作成](odata-filters.md#create-the-item-in-the-destination)に関するセクションの手順に従って、テーブルのフィールドを設定します。
   
    ![環境を表示する](media/odata-filters/update-row.png)
3. ページの上部にある **[フロー名]** にフローの名前を入力してから、**[フローの作成]** を選択して保存します。
   
    ![フローに名前を付ける](media/odata-filters/give-the-flow-a-name.png)

これで、SharePoint リスト (ソース) の項目が変更された場合は常に、フローがトリガーされ、Azure SQL Database (ターゲット) で新しい項目が挿入されるか、既存の項目が更新されます。

> [!NOTE]
> ソースから項目が削除された場合、フローはトリガーされません。 これが重要なシナリオである場合は、項目が不要になったことを示す別の列を追加することを検討してください。
> 
> 

## <a name="learn-more"></a>詳細については、こちらをご覧ください
フローで[データ操作](data-operations.md)を使用します。

