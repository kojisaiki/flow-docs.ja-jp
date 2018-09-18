---
title: データ操作を理解する | Microsoft Docs
description: 作成、結合、選択、配列のフィルター処理、HTML テーブル作成、CSV テーブル作成など、Microsoft Flow による操作の実行について説明します。
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
ms.date: 08/02/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: c28fa7feb743db4616199246d6d517e2e1f6aff9
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690999"
---
# <a name="use-data-operations-with-microsoft-flow"></a>Microsoft Flow によるデータ操作を利用する
このチュートリアルでは、Microsoft Flow で頻繁に使用するデータ操作について説明します。作成、結合、選択、配列のフィルター処理、テーブルの作成、JSON の解析など、フロー作成時のデータ操作に使用できる操作です。

## <a name="prerequisites"></a>前提条件
* Microsoft Flow にアクセスできること。
* HTTP POST 要求と JSON 配列をフローに送信するための [PostMan](https://www.getpostman.com/postman) のようなツール。

## <a name="use-the-compose-action"></a>作成アクションを使用する
**データ操作 - 作成** (作成) アクションを使用すれば、フローの設計時、同じデータを何回も入力しなくて済みます。 たとえば、フローの設計時に ````[0,1,2,3,4,5,6,7,8,9]```` という数字の配列を数回入力する必要がある場合、作成アクションを使用し、次のように配列を保存できます。

1. **[作成]** を探し、**[データ操作 - 作成]** (作成) アクションを選択します。
   
    ![作成アクションを探し、選択する](./media/data-operations/search-select-compose.png)
2. 後で参照する配列を **[入力]** ボックスに入力します。
   
    ![作成アクションを構成する](./media/data-operations/add-array-compose.png)

> [!TIP]
> 後で簡単に参照するために、**作成**カードの名前を変更します。**作成**カードのタイトル バーのテキスト "Compose" をクリックします。
> 
> 

作成アクションの内容にアクセスする必要があるとき、**[このフローで使用されるアプリやコネクタから動的なコンテンツを追加します]** 一覧の**出力**トークンからアクセスします。これは次の手順で行います。

1. **[データ操作 - 結合]** などのアクションを追加します。
2. 作成アクションで保存したコンテンツを追加するコントロールを選択します。
   
    **[このフローで使用されるアプリやコネクタから動的なコンテンツを追加します]** が開きます。
3. **[このフローで使用されるアプリやコネクタから動的なコンテンツを追加します]** で、**[動的コンテンツ]** タブの**作成**カテゴリにある**出力**トークンを選択します。
   
    ![作成アクションの出力を使用する](./media/data-operations/use-compose-output.png)

## <a name="use-the-join-action"></a>結合アクションを使用する
**[データ操作 - 結合]** アクション (結合) を使用し、選択した区切り記号で配列を区切ります。 たとえば、メール アドレスの配列 ````["d@example.com", "k@example.com", "dal@example.com"]```` が含まれる Web 要求をフローが受け取ると想定します。 ただし、お使いのメール プログラムでは、アドレスをセミコロンで区切った単一文字列にする必要があります。 そのために、**[データ操作 - 結合]** (結合) アクションを使用し、次の手順でコンマの区切り記号をセミコロン “;“ に変更します。

1. 新しいアクションを追加し、**[結合]** を探し、**[データ操作 - 結合]** (結合) を選択します。
   
    ![結合アクションを探し、選択する](./media/data-operations/search-select-join.png)
2. **[From]\(配列\)** ボックスに配列を入力し、使用する新しい区切り記号を **[結合する配列]** ボックスに入力します。
   
    ここで、新しい区切り記号としてセミコロン (;) を使用しました。
   
    ![結合アクションを構成する](./media/data-operations/add-array-join.png)
3. フローを保存し、実行します。
4. フローの実行後、**[データ操作 - 結合]** アクションの出力は次のようになります。
   
    ![結合の出力](./media/data-operations/join-output.png)

## <a name="use-the-select-action"></a>選択アクションを使用する
**[データ操作 - 選択]** (選択) を使用し、配列内のオブジェクトのシェイプを変換します。 たとえば、配列内の各オブジェクトの要素を追加、削除、名前変更します。

> [!NOTE]
> 選択アクションで要素を追加したり、削除したりできますが、配列内のオブジェクトの数を変更することはできません。
> 
> 

たとえば、Web 要求を経由して次の形式でデータがフローに入る場合に選択アクションを使用できます。

````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]````

また、入ってくるデータのシェイプを変更できます。"first" を "FirstName" に変更し、"last" を "LastName" に変更し、"first" と "last" を結合 (スペースで分割) する "FamilyName" という名前の新しいメンバーを追加します。

````[ { "FirstName": "Deon", "FamilyName": "Herb", "FullName": "Deon Herb" }, { "FirstName": "K", "FamilyName": "Herb", "FullName": "K Herb" } ]````

これを行うには:

1. **[要求 / 応答 – 応答]** (要求) アクションをフローに追加します。
2. **要求**カードから **[サンプルのペイロードを使用してスキーマを生成する]** を選択します。
3. ボックスが表示されたら、ソース データ配列のサンプルを貼り付け、**[完了]** ボタンを選択します。
4. **[データ操作 - 選択]** (選択) アクションを追加し、次のイメージのように構成します。
   
    ![選択アクションを構成する](./media/data-operations/select-card.png)
   
   > [!TIP]
   > 選択アクションからは、シェイプが新しくなったオブジェクトを含む配列が出力されます。 この配列を、先に考察した**作成**など、他のアクションで利用できます。
   > 
   > 

## <a name="use-the-filter-array-action"></a>配列のフィルター処理操作を使用する
**[データ操作 - 配列のフィルター処理]** (配列のフィルター処理) を使用すると、配列内のオブジェクト数を、指定した条件に一致するサブセットまで減らすことができます。

> [!NOTE]
> 配列のフィルター処理を利用して、配列内のオブジェクトのシェイプを変更することはできません。 また、フィルター処理するテキストでは大文字と小文字が区別されます。
> 
> 

たとえば、次の配列でフィルター処理を利用できます。

````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]````

*first* が “Deon” に設定されているオブジェクトのみを含む配列が新しく作成されます。

作成してみましょう。

1. **[データ操作 - 配列のフィルター処理]** (配列のフィルター処理) アクションを探し、フローに追加します。
2. 次のイメージのように配列のフィルター処理アクションを構成します。
   
    ![配列のフィルター処理操作を構成する](./media/data-operations/add-configure-filter-array.png)
3. フローを保存し、実行します。
   
    [PostMan](https://www.getpostman.com/postman) を利用し、JSON 配列をフローに送信する Web 要求を生成できます。
4. フローを実行すると、JSON 入力は次のような配列になると想定します。
   
    ````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]````
   
    出力は次の配列のようになります (*first* が “Deon” に設定されているオブジェクトのみがアクションの出力に含まれます)。
   
    ````[ { "first": "Deon", "last": "Herb" } ]````

## <a name="use-the-create-csv-table-action"></a>CSV テーブルの作成アクションを使用する
**[データ操作 - CSV テーブルの作成]** (CSV テーブルの作成) を使用し、JSON 配列をコンマの区切り値 (CSV) テーブルに変更します。 必要に応じて、CSV 出力でヘッダーの表示を維持できます。 たとえば、**[CSV テーブルの作成]** アクションを利用し、次の配列を CSV テーブルに変換できます。

````[ { "first": "Deon", "last": "Herb" }, { "first": "K", "last": "Herb" } ]````

1. **[データ操作 - CSV テーブルの作成]** アクションを探し、追加し、次のイメージのように構成します。
   
    ![CSV テーブルの作成アクションを構成する](./media/data-operations/create-csv-table.png)
   
    注: このイメージの**本文**トークンは **[要求 / 応答 - 応答]** アクションから取られていますが、**[CSV テーブルの作成]** アクションの入力は、フローにおける前のアクションの出力から取得できます。あるいは、**[From]\(入力\)** ボックスに直接入力できます。
2. フローを保存し、実行します。
   
    フローを実行すると、**[CSV テーブルの作成]** 出力は次のイメージのようになります。
   
    ![CSV テーブル出力の作成](./media/data-operations/create-csv-table-output.png)

## <a name="use-the-create-html-table-action"></a>HTML テーブルの作成アクションを使用する
**[データ操作 - HTML テーブルの作成]** を使用し、JSON 配列入力を HTML テーブルに変更します。 必要に応じて、HTML 出力でヘッダーの表示を維持できます。

これを行うには、「[CSV テーブルの作成](#use-the-create-csv-table-action)」セクションの手順に従います。詳しい例があります。 **[データ操作 - CSV テーブルの作成]** アクションではなく、**[データ操作 - HTML テーブルの作成]** アクションを使用してください。

> [!TIP]
> HTML テーブルをメールで送信する場合、メール アクションで "IsHtml" を選択してください。
> 
> 

