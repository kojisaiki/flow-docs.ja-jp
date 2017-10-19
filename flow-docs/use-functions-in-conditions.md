---
title: "関数と条件を使用する | Microsoft Docs"
description: "次のような高度な関数を使用する "
"\"and\"\",": 
"\"\"or\"\",": 
"\"\"empty\"\",": 
"\"\"less\"\"": 
and: 
"\"\"greater\"\"": 
with: 
microsoft: 
flow: 
conditions.": 
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
ms.date: 08/01/2017
ms.author: deonhe
ms.openlocfilehash: 26f8dd2f8f9c027584bba197d301e4c8a32b0857
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="use-functions-in-conditions-to-check-multiple-values"></a>複数の値を確認する条件で関数を使用する
このチュートリアルでは、関数と**条件**を利用し、**詳細モード**で複数の値を比較する方法について学習します。

フローを作成するとき、基本モードで[**条件**](add-a-condition.md#add-a-condition)カードを使用し、単一値を別の値と簡単に比較できます。 ただし、複数の値を比較しなければならない場面もあります。 たとえば、スプレッドシートやデータベース テーブルの列の値を確認する場合です。

条件では、次の論理関数をあらゆる組み合わせで利用できます。

| 関数 | 説明 | 例 |
| --- | --- | --- |
| <a href="#use-the-and-function">and</a> |2 つの引数を受け取り、両方の値が true の場合は true を返します。<br><b>注</b>: 両方の引数をブール値にする必要があります。 |次の関数は false を返します。 <br>and(greater(1,10),equals(0,0)) |
| <a href="#use-the-or-function">or</a> |2 つの引数を受け取り、どちらかの引数が true の場合は true を返します。 <br><b>注</b>: 両方の引数をブール値にする必要があります。 |次の関数は true を返します。<br>or(greater(1,10),equals(0,0)) |
| equals |2 つの値が等しい場合に true を返します。 |たとえば、parameter1 が someValue のとき、次の関数は true を返します。<br>equals(parameters('parameter1'), 'someValue') |
| <a href="#use-the-less-function">less</a> |2 つの引数を受け取り、最初の引数が 2 番目の引数よりも小さい場合、true を返します。 <br><b>注</b>: サポートされる型は整数、浮動小数点数、文字列です。 |次の関数は true を返します。<br>less(10,100) |
| lessOrEquals |2 つの引数を受け取り、最初の引数が 2 番目の引数と等しいかそれよりも小さい場合は true を返します。 <br><b>注</b>: サポートされる型は整数、浮動小数点数、文字列です。 |次の関数は true を返します。<br>lessOrEquals(10,10) |
| <a href="#use-the-greater-function">greater</a> |2 つの引数を受け取り、最初の引数が 2 番目の引数よりも大きい場合は true を返します。 <br><b>注</b>: サポートされる型は整数、浮動小数点数、文字列です。 |次の関数は false を返します。<br>greater(10,10) |
| greaterOrEquals |2 つの引数を受け取り、最初の引数が 2 番目の引数と等しいかそれよりも大きい場合は true を返します。 <br><b>注</b>: サポートされる型は整数、浮動小数点数、文字列です。 |次の関数は false を返します。<br>greaterOrEquals(10,100) |
| <a href="#use-the-empty-function">empty</a> |オブジェクト、配列、文字列が空の場合は true を返します。 |次の関数は true を返します。<br>empty('') |
| not |2 つの引数を受け取り、引数が true の場合は true を返します。 <br><b>注</b>: 両方の引数をブール値にする必要があります。 |次の関数は true を返します。<br>not(contains('200 Success','Fail')) |
| if |式の結果が true か false の場合、特定の値を返します。 |次の関数は "yes" を返します。<br>if(equals(1, 1), 'yes', 'no') |

## <a name="prerequisites"></a>前提条件
* Microsoft Flow にアクセスできること。
* このチュートリアルの後半で説明するテーブルを含むスプレッドシート。 Microsoft Flow でアクセスできるように、Dropbox や Microsoft OneDrive などの場所にスプレッドシートを保存してください。
* Microsoft Office 365 Outlook (Office 365 Outlook を使用するとき、サポートされているあらゆる電子メール サービスをフローで利用できます。)

## <a name="use-the-or-function"></a>or 関数を使用する
ある項目の値が valueA **か** valueB の場合にアクションを行うワークフローがあります。 たとえば、スプレッドシート テーブルのタスクの状態を追跡記録します。 テーブルに *Status* という名前の列があり、*Status* 列の入力可能値は次のようになっていると想定します。

* **completed** (完了済み)
* **blocked** (ブロック済み)
* **unnecessary** (不要)
* **not started** (未開始)

スプレッドシートは、たとえば、次のようになります。

![サンプルのスプレッドシート](./media/use-functions-in-conditions/spreadsheet-table.png)

先のスプレッドシートの場合、Microsoft Flow を利用し、たとえば、*Status* 列が *completed* または *unnecessary* に設定されているすべての行を削除します。

フローを作成してみましょう。

### <a name="start-with-a-blank-flow"></a>空のフローから始める
1. [Microsoft Flow](https://flow.microsoft.com) にサインインします。
   
    ![サインイン](includes/media/modern-approvals/sign-in.png)
2. **[自分のフロー]** タブを選択します。
   
    ![自分のフローの選択](includes/media/modern-approvals/select-my-flows.png)
3. **[一から作成]** を選択します。
   
    ![一から作成する](includes/media/modern-approvals/blank-template.png)

### <a name="add-a-trigger-to-your-flow"></a>トリガーをフローに追加する
1. **[スケジュール]** を探し、**[スケジュール - 繰り返し]** トリガーを選択します。
   
    ![スケジュール トリガー](includes/media/schedule-trigger/schedule-trigger.png)
2. 一日一回実行するようにスケジュールを設定します。
   
    ![スケジュールの設定](includes/media/schedule-trigger/set-schedule.png)

### <a name="select-the-spreadsheet-and-get-all-rows"></a>スプレッドシートを選択し、すべての行を取得する
1. **[新しいステップ]**  >  **[アクションの追加]** を選択します。
   
    ![新しいステップ](includes/media/new-step/action.png)
2. **[行]** を探し、**[Excel - 行の取得]** を選択します。
   
    注: 使用しているスプレッドシートに対応する "行の取得" アクションを選択します。 たとえば、Google スプレッドシートを使用している場合、**[Google スプレッドシート - 行の取得]** を選択します。
   
    ![行を取得する](includes/media/new-step/get-excel-rows.png)
3. [**ファイル名**] ボックスのフォルダー アイコンを選択し、データが含まれるスプレッドシートを探し、選択します。
   
    ![スプレッドシートを選択する](includes/media/new-step/select-spreadsheet.png)
4. **[テーブル名]** 一覧のデータを含むテーブルを選択します。
   
    ![テーブルを選択する](includes/media/new-step/select-table.png)

### <a name="check-the-status-column-of-each-row"></a>各行の status 列を確認する
1. **[新しい手順]** > **[その他]** > **[それぞれへの適用の追加]** の順に選択します。
   
    ![テーブルを選択する](includes/media/new-step/apply-to-each.png)
2. **Value** トークンを **[以前の手順から出力を選択]** ボックスに追加します。
   
    ![テーブルを選択する](includes/media/apply-to-each/add-value-token.png)
3. **[条件の追加]** > **[詳細設定モードで編集]** の順に選択します。
4. 次の **or** 関数を追加します。 この **or** 関数はテーブル内の各行の値を確認します (関数内でアクセスされるとき、行は項目として認識されます)。 **status** 列の値が *completed* **か** *unnecessary* の場合、**or** 関数は "true" として評価します。
   
    **or** 関数は次のように表示されます。
   
    ````@or(equals(item()?['status'], 'unnecessary'), equals(item()?['status'], 'completed'))````
   
    **条件**カードは次のイメージのようになります。
   
    ![or 関数のイメージ](./media/use-functions-in-conditions/or-function.png)

### <a name="delete-matching-rows-from-the-spreadsheet"></a>一致する行をスプレッドシートから削除する
1. 条件の **[IF YES, DO NOTHING]** 分岐で **[アクションの追加]** を選択します。
2. **[行の削除]** を探し、**[Excel - 行の削除]** を選択します。
   
    ![行の削除のイメージ](includes/media/new-step/select-delete-excel-row.png)
3. **[ファイル名]** ボックスで、削除するデータが含まれるスプレッドシート ファイルを探し、選択します。
4. **[テーブル名]** 一覧で、データを含むテーブルを選択します。
5. **[行 ID]** ボックスに**行 ID** トークンを入力します。
   
    ![スプレッドシート ファイル](includes/media/new-step/delete-excel-row.png)

### <a name="name-the-flow-and-save-it"></a>フローに名前を付け、保存する
1. フローに名前を付け、**[フローの作成]** ボタンを選択します。
   
    ![フローを保存する](./media/use-functions-in-conditions/name-and-save.png)

### <a name="run-the-flow-with-the-or-function"></a>or 関数を含むフローを実行する
保存後、フローが実行されます。 このチュートリアルの前半で説明したスプレッドシートを作成すると、そのスプレッドシートは実行後、次のようになります。

![or 関数の完了](./media/use-functions-in-conditions/spreadsheet-table-after-or-function-runs.png)

Status 列が "completed" か "unnecessary" の行からデータがすべて削除されています。

## <a name="use-the-and-function"></a>and 関数を使用する
2 つの列を含むスプレッドシート テーブルがあると想定します。 列の名前は Status と Assigned です。 また、Status 列の値が "blocked" で、Assigned 列の値が "John Wonder" の場合、すべての行を削除すると想定します。  このタスクを実行するには、このチュートリアルの前述のすべての手順に従います。ただし、詳細モードで**条件**カードを編集する場合は、以下の **and** 関数を使用します。

````@and(equals(item()?['Status'], 'blocked'), equals(item()?['Assigned'], 'John Wonder'))````

**条件**カードは次のイメージのようになります。

![and 関数のイメージ](./media/use-functions-in-conditions/and-function.png)

### <a name="run-the-flow-with-the-and-function"></a>and 関数を含むフローを実行する
ここまで実行していれば、スプレッドシートは次のイメージのようになります。

![and 実行前](./media/use-functions-in-conditions/spreadsheet-table-before-and-function-runs.png)

フローの実行後、スプレッドシートは次のイメージのようになります。

![and 実行後](./media/use-functions-in-conditions/spreadsheet-table-after-and-function-runs.png)

## <a name="use-the-empty-function"></a>empty 関数を使用する
スプレッドシートに空の行が存在することに注目してください。 空の行を削除するには、**empty** 関数を利用し、Assigned 列と Status 列にテキストが入っていないすべての行を特定します。

このタスクを遂行するには、このチュートリアルで先に紹介した「**and 関数を使用する**」セクションのすべての手順を実行します。ただし、詳細モードで**条件**カードを編集するとき、下の empty 関数を使用します。

````@and(empty(item()?['Status']), empty(item()?['Assigned']))````

**条件**カードは次のイメージのようになります。

![empty 関数のイメージ](./media/use-functions-in-conditions/empty-function.png)

フローの実行後、スプレッドシートは次のイメージのようになります。

![empty 実行後](./media/use-functions-in-conditions/spreadsheet-table-after-empty-function-runs.png)

余分な行がテーブルから削除されています。

## <a name="use-the-greater-function"></a>greater 関数を使用する
同僚達のために野球のチケットを購入し、スプレッドシートを利用して同僚達からの返済を確認するとします。 全額を支払っていない同僚にメールを毎日送信するフローを簡単に作成できます。

**greater** 関数を利用し、全額を支払っていない同僚を特定します。 全額を支払っていない同僚には催促のメールを自動送信できます。

このスプレッドシートは次のようになります。

![スプレッドシートのイメージ](./media/use-functions-in-conditions/tickets-spreadsheet-table.png)

**greater** 関数が実装されていますが、この関数により、支払額が全額に達していないすべての同僚が特定されます。

````@greater(item()?['Due'], item()?['Paid'])````

## <a name="use-the-less-function"></a>less 関数を使用する
同僚のために野球のチケットを購入し、スプレッドシートを利用して同僚からの返済を確認するとします。返済は各同僚が同意した日付までとします。 支払期日到達まで 1 日未満になっても全額支払いが完了していない同僚に催促のメールを送信するフローを作成できます。

**and** 関数と **less** 関数を併用します。評価する条件が 2 つあるためです。

| 評価する条件 | 使用する関数 | 例 |
| --- | --- | --- |
| 全額が支払われたか? |greater |@greater(item()?['Due'], item()?['Paid']) |
| 期日到達まで 1 日未満になっているか? |less |@less(item()?['DueDate'], addDays(utcNow(),1)) |

## <a name="combine-the-greater-and-less-functions-in-an-and-function"></a>and 関数の中で greater 関数と less 関数を組み合わせます
**greater** 関数を利用し、全額を支払っていない同僚を特定します。**less** 関数を利用し、期日到達まで 1 日未満になっているか判定します。 次に、**[電子メールの送信]** アクションを利用し、期日到達まで 1 日未満になっても全額を支払っていない同僚に催促のメールを送信します。

このスプレッドシート テーブルは次のようになります。

![スプレッドシートのイメージ](./media/use-functions-in-conditions/spreadsheet-table-due-date.png)

**and** 関数が実装されていますが、この関数により、期日到達まで 1 日未満になっても全額を支払っていないすべての同僚が特定されます。

````@and(greater(item()?['Due'], item()?['Paid']), less(item()?['dueDate'], addDays(utcNow(),1)))````

## <a name="learn-more"></a>詳細については、こちらをご覧ください
その他の関数については[こちら](https://docs.microsoft.com/azure/logic-apps/logic-apps-workflow-definition-language#functions)をご覧ください。

