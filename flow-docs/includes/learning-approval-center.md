前のトピックでは、SharePoint リストを使用して簡単に Twitter フィードを強化する方法について説明しました。 このトピックでは、承認を使用して、よりビジネス向けのシナリオを構築する方法について説明します。 ここでは、SharePoint リストにアクセスする権限を持つ全員がツイートを作成できます。また、ソーシャル メディア チームはそれらのツイートを承認または却下することができます。 チームは、アカウントと、顧客に送信されるコンテンツの制御を維持します。 

## <a name="create-an-approval-request-flow"></a>承認要求フローを作成する
1. **Microsoft Flow** ホームページで、**[承認]**、**[承認フローの作成]** の順に選択し、下にスクロールして **[承認後にリスト アイテムを Twitter に投稿する]** テンプレートを選択します。 
   
    ![テンプレートを選択する](./media/learning-approval-center/create-approval.png)
2. **[SharePoint]**、**[承認]**、および **[Twitter]** のアカウントの資格情報を確認し、**[続行]** を選択します。 
   
    ![資格情報を選択する](./media/learning-approval-center/verify-credentials.png)

既定で、このテンプレートは、新しい項目が特定のリストに作成されるたびに承認プロセスを開始し、項目が承認されると、ツイートを Twitter に投稿します。 このトピックでは、このプロセスを変更します。具体的には、承認応答を使用して SharePoint リストを更新し、承認されたかどうかを示し、提案されたツイートに対して承認者が追加したコメントがあれば追加する、という手順を追加します。 

1. 前に作成した **ContosoTweets** SharePoint リストに、新しい 2 つの列を追加します。
   
   1. プラス記号 **+** を選択し、**[はい/いいえ]** を選択します
   2. 「**ApprovalStatus**」と入力し、**[作成]** を選択します
   3. プラス記号 **+** を選択し、**[1 行テキスト]** を選択します
   4. 「**ApproverComments**」と入力し、**[保存]** を選択します。
      
      ![列を追加する](./media/learning-approval-center/new-columns.png)
2. **Microsoft Flow** に戻り、**[新しい項目が作成されたとき]** アクションに次の値を入力します。
   
   * **サイトのアドレス**: チームの SharePoint URL
   * **リスト名**: ContosoTweets
     
     ![サイトとリスト](./media/learning-approval-center/site-address.png)
3. **[Start an approval]\(承認を開始する\)** アクションで **[編集]** を選択してすべてのフィールドを表示します。 
   
    ![フィールドの編集](./media/learning-approval-center/edit-all-fields.png)
4. **[タイトル]** に「**New tweet for**」と入力し、動的コンテンツ リストから **[タイトル]** を選択します。 
   
    ![タイトル](./media/learning-approval-center/tweet-title.png)
5. **[割り当て先]** に自分の名前またはテスト ユーザー名を入力します。 
   
    ![割り当て先](./media/learning-approval-center/tweet-assigned-to.png)
6. **[詳細]** で、既定の項目を削除し、動的コンテンツ リストから **[TweetContent]**、**[TweetDate]**、および **[Created by DisplayName]** を **on** および **by** という単語で接続して追加します。 
   
    ![詳細](./media/learning-approval-center/tweet-details.png)
7. **[アイテム リンク]** で、SharePoint リストの URL をコピーして貼り付け、**[アイテム リンクの説明]** に「**Contoso ツイート リスト**」と入力します。 
   
    ![アイテム リンク](./media/learning-approval-center/tweet-item-link.png)
8. **[条件]** アクションで、**[はいの場合]** ボックスにマウスを移動してプラス記号 **+** を選択し、**[アクションの追加]** を選択します。 
   
    ![アクションを追加する](./media/learning-approval-center/add-an-action.png)
9. **項目の更新**を検索し、**SharePoint** コネクタを選択し、**[SharePoint - 項目の更新]** アクションを選択します。
   
    ![SharePoint の項目の更新](./media/learning-approval-center/update-item.png)
10. **[サイトのアドレス]** と **[リスト名]** にサイトの URL と **ContosoTweets** リストをもう一度入力し、**[ID]** に動的コンテンツ リストから **[ID]** を入力します。 
    
     ![サイト、リスト、ID](./media/learning-approval-center/address-list-id.png)
11. **[タイトル]** フィールドを選択し、動的コンテンツ リストで**タイトル**を探します。 **[新しい項目が作成されたとき]** アクションから **[タイトル]** 項目を追加します。 
    
     ![新しいタイトル](./media/learning-approval-center/add-title.png)
12. **[ApprovalStatus]** を選択し、値を **[はい]** に設定し、**[ApproverComments]** を選択し、値を動的コンテンツ リストの **[コメント]** に設定します。 
    
     ![状態とコメント](./media/learning-approval-center/approver-status.png)
13. **[いいえの場合、何もしない]** ボックスの一番下近くにある **[アクションの追加]** を選択します。
    
     ![アクションを追加しない](./media/learning-approval-center/add-a-no-action.png)
14. **[はいの場合]** 構成で使用した手順と同じ手順で、**[SharePoint - 項目の更新]** アクションを作成し、**[ApprovalStatus]** 設定を **[いいえ]** に設定する点を除き、同じ値でフィールドを構成します。ただし、 
    
     ![状態 = いいえ](./media/learning-approval-center/status-no.png)
15. **[ツイートの投稿]** アクションを選択し、**[編集]** を選択し、**[ツイート テキスト]** を動的コンテンツ リストの **[TweetContent]** に設定します。  ページの上部で、**[フローの作成]** を選択して作業内容を保存します。 
    
     ![投稿と保存](./media/learning-approval-center/post-tweet.png)

これは、Microsoft Flow でチームの生産性を向上する方法のごく一例です。 チームがアイデア、関連するニュース、または製品のガイダンスを投稿できるだけでなく、顧客に送信されるツイートを管理者が制御できます。

次のトピックでは、提案されたツイートに対して承認者が新しい要求を受け取ったときはどうなるかについて見てみましょう。 

