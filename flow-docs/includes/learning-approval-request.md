前のトピックでは、SharePoint リストに保存されているツイートの承認プロセスを構築する方法について説明しました。  このトピックでは、承認者が新しい承認要求を受け取ったときにどうなるかについて説明します。 

## <a name="create-and-process-a-request"></a>要求の作成と処理
まず、項目を SharePoint リストに追加する必要があります。追加すると、その項目の承認要求を処理できます。

1. 前のトピックで構成した SharePoint リスト **ContosoTweets** を開きます。  **[新規作成]** を選択して、新しいツイートを作成します。 
   
    ![SharePoint リスト](./media/learning-approval-request/sharepoint-list-home.png)
2. 次の値をフィールドに追加し、**[保存]** を選択します。
   
   * **タイトル** - プロモーション
   * **TweetContent** - Contoso Flooring #ohsocontoso という新しい行を確認してください
   * **TweetDate** - 今日の日付
     
     ![SharePoint の新しい項目](./media/learning-approval-request/sharepoint-new-tweet.png)
3. **[Microsoft Flow]** の **[マイ フロー]** を選択します。 
4. 前のトピックで構成した **[承認後にリスト アイテムを Twitter に投稿する]** フローを選択し、**[実行履歴]** で実行フローを選択します。
   
    ![実行履歴](./media/learning-approval-request/run-history.png)
5. **[新しい項目が作成されたとき]** トリガーを選択します。 作成したリスト項目の情報が表示されていることを確認します。
   
    ![フローのトリガー](./media/learning-approval-request/approval-flow.png)
6. **Outlook** の受信トレイで、自動承認メールを開いて **[承認]** を選択します。 
   
    ![Outlook の要求](./media/learning-approval-request/outlook-mail.png)
7. **承認センター**で要求の詳細を確認し、コメントを追加し、**[確認]** を選択します。 
   
    ![承認センター](./media/learning-approval-request/approval-center.png)
8. **SharePoint** で、**[ContosoTweets]** リストを更新し、**[ApprovalStatus]** が **[はい]** であること、入力したコメントが表示されることを確認します。 
   
    ![SharePoint の更新リスト](./media/learning-approval-request/sharepoint-list-approved.png)

このトピックでは、承認者の観点からの操作 (承認要求電子メールの受信から、承認センターで要求を処理するまで) について説明しました。

