---
title: スケジュールに従ったフローの実行 | Microsoft Docs
description: 毎日、毎時間などのスケジュールに従ってフローを実行して、定期的なタスクを自動化します。
services: ''
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/14/2017
ms.author: stepsic
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: af18e8caae8e74bb12d274c6e5cb0d94a0e0471b
ms.sourcegitcommit: b684b379e6007d3bd00948525156e7fbd39bf96c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57665016"
---
# <a name="run-flows-on-a-schedule"></a>スケジュールに従ったフローの実行
1 つ以上のタスクを実行するフローを作成します (例: メールによるレポートの送信)。

* 1 日、1 時間、または 1 分につき 1 回実行する
* 指定した日付に実行する
* 指定した日数、時間、分の経過後に実行する

## <a name="create-a-recurring-flow"></a>定期的なフローの作成
1. [Microsoft Flow](https://flow.microsoft.com) にサインインし、上部のナビゲーション バーの **[マイ フロー]** を選択します。
   
    ![[マイ フロー] オプション](./media/run-scheduled-tasks/create-flow.png)
2. **[一から作成]** を選択します。
   
    ![ゼロからフローを作成](./media/run-scheduled-tasks/create-from-blank.png)
3. **[すべてのコネクタとトリガーを検索する]** ボックスに、「**繰り返し**」と入力し、**[スケジュール - 繰り返し]** を選択します。
   
    ![繰り返しのトリガーを検索](./media/run-scheduled-tasks/select-recurrence.png)
4. **[Recurrence (繰り返し)]** ダイアログ ボックスで、フローを実行する頻度を指定します。
   
    たとえば、2 週間に 1 回フローを実行するには、**[間隔]** で **[2]** を指定し、**[頻度]** で **[週]** を指定します。
   
    ![定期的な実行の指定](./media/run-scheduled-tasks/specify-recurrence.png)

## <a name="specify-advanced-options"></a>詳細なオプションを指定する
1. 前のセクションの手順を実行し、**[詳細オプションを表示する]** を選択します。
   
    **注**: このオプションは、**[間隔]** と **[頻度]** に設定された値に基づいて変更されます。 表示されている画面が、下図と異なる場合は **[間隔]** と **[頻度]** が下図と同じ値に設定されていることを確認してください。
2. **[タイム ゾーン]** を選択し、**[開始時刻]** を指定する際にローカル タイム ゾーン、協定世界時 (UTC) などを反映するようにします。
3. **[開始時刻]** を次の形式で指定します。
   <br>YYYY-MM-DDTHH:MM:SSZ
4. **[頻度]** で **[日]** を指定した場合は、フローを実行する時刻を指定します。
5. **[頻度]** で **[週]** を指定した場合は、フローを実行する曜日 (1 日または複数の曜日) とフローを実行する時刻 (1 回または複数の実行時刻) を指定します。
   
    たとえば、図のオプションのように、2018 年 1 月 1 日、月曜日の正午 (太平洋標準時) になったらすぐにフローを開始し、このフローを 2 週間に 1 回、火曜日の午後 5:30 (太平洋標準時) に実行するように設定します。
   
    ![詳細なオプションを指定する](./media/run-scheduled-tasks/advanced-options.png)
6. [ゼロからのフロー作成](get-started-logic-flow.md)に関する記事に従って、フローで実行するアクションを追加します。

## <a name="delay-a-flow"></a>フローの延期
1. [Microsoft Flow](https://flow.microsoft.com) にサインインし、上部のナビゲーション バーの **[マイ フロー]** を選択します。
   
    ![ゼロからフローを作成](./media/run-scheduled-tasks/create-flow.png)
2. **[一から作成]** を選択します。
   
    ![ゼロからフローを作成](./media/run-scheduled-tasks/create-from-blank.png)
3. [ゼロからのフロー作成](get-started-logic-flow.md)に関する記事に従って、イベントを指定します。
4. **[新しいステップ]** を選択し、**[アクションの追加]** を選択します。
   
    ![フローにアクションを追加するオプション](./media/run-scheduled-tasks/add-action.png)
5. アクションの一覧で、次のいずれかの操作を行います。
   
   * **[遅延]** を選択し、**[カウント]** を指定して、秒、分、時間などの **[単位]** を指定する。
   * **[延期期限]** を選択し、日付を次の形式で指定します。<br>YYYY-MM-DDTHH:MM:SSZ
     
     ![遅延の追加](./media/run-scheduled-tasks/add-delay.png)
     ![時間の単位で遅延を指定](./media/run-scheduled-tasks/delay.png)
     ![延期期限を指定](./media/run-scheduled-tasks/delay-until.png)

## <a name="learn-more"></a>詳細については、こちらをご覧ください

[詳細オプション](https://docs.microsoft.com/azure/connectors/connectors-native-recurrence)とその構成方法の詳細をご覧ください。

