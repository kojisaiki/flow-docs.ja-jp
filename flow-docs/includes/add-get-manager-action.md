1. **[新しいステップ]** を選択し、**[アクションの追加]** を選択します。
   
    ![新しいステップ](media/modern-approvals/select-sharepoint-add-action.png)
2. **[アクションの選択]** 検索ボックスに **[get manager]\(マネージャー取得)** と入力します。
3. **[Office 365 Users - Get manager (V2)]\(Office 365 ユーザー - マネージャー取得 (V2))** アクションを検索して選択します。

    ![Office ユーザーの選択](media/modern-approvals/add-get-manager-action.png)
4. **[Get manager]\(マネージャー取得)** カードの **[User (UPN)]\(ユーザー (UPN)\)** ボックスに **[Created By Email]\(電子メールによって作成)** トークンを挿入します。

    このアクションを使用すると、SharePoint で休暇申請を作成した従業員のマネージャーを取得できます。

    ![マネージャーの構成を取得する](media/modern-approvals/get-manager-card.png)

