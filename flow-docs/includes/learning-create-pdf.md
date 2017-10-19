このトピックでは、Contoso Flooring 社が Microsoft Flow を使用して、ドキュメントを標準形式に変換してから SharePoint Online に保存する処理を自動的に行い、クラウドへの安全な保管を実現する方法について説明します。 新しいファイルが OneDrive for Business フォルダーに追加されたときを検出し、そのファイルを PDF に変換し、SharePoint Online フォルダーに格納するフローを作成します。 

## <a name="prerequisites"></a>前提条件
このシナリオでは、PDF 変換サービスである **Muhimbi** のアカウントが必要です。 Muhimbi アカウントをまだお持ちでない場合は、[30 日間無料試用版](http://www.muhimbi.com/Products/PDF-Converter-for-SharePoint/Products-PDF-Converter-for-SharePoint-Free-Trial.aspx)にサインアップできます。 そのページの指示に従って SharePoint Online サイトからアプリをデプロイします。 

## <a name="create-the-source-and-target-folders"></a>ソース フォルダーとターゲット フォルダーの作成
まず、OneDrive for Business と SharePoint Online 上にソース フォルダーとターゲット フォルダーを作成する必要があります。 

1. OneDrive for Business では、**[ファイル]** で、"**完了ドキュメント**" という名前のフォルダーを作成します。 
   
    ![](./media/learning-create-pdf/onedrive-folder.png)
2. SharePoint Online では、**[共有ドキュメント]** で、"**PDF – 完了ファイル**" とい名前のフォルダーを作成します。 
   
    ![](./media/learning-create-pdf/sharepoint-folder.png)

## <a name="create-the-flow"></a>フローを作成する
1. Microsoft Flow で、**[自分のフロー]**、**[一から作成]** の順に選択します。 
   
    ![](./media/learning-create-pdf/create-blank-flow.png)
2. **[多数のコネクタやトリガーを検索する]** を選択します。
3. **[OneDrive]** を検索し、**[OneDrive for Business]** を選択し、トリガー **[OneDrive for Business - ファイルが作成されたとき]** を選択します。 **[フォルダー]** で、フォルダー アイコンを選択し、前の手順で作成した **[完了ドキュメント]** を選択します。 
   
    ![](./media/learning-create-pdf/onedrive-trigger.png)
4. **[新しいステップ]** を選択し、**[アクションの追加]** を選択します。 
   
    ![](./media/learning-create-pdf/new-action.png)
5. **[Muhimbi]** を検索し、**[Muhimbi PDF]** コネクタを選択し、アクション **[Muhimbi PDF – ドキュメントの変換]** を選択します。
   
    ![](./media/learning-create-pdf/muhimbi-action.png)
6. この時点で、Muhimbi に対する認証を実行するように Microsoft Flow から求められる場合があります。 Microsoft Flow で Muhimbi サービスを使用するためには、**SharePoint テナント ID** を使用して Muhimbi を登録する必要があります。 
   
   1. テナント ID を確認するには、SharePoint Online の **[設定]** 歯車アイコンを選択し、**[サイト設定]** を選択します。
   2. **[サイト コレクションの管理]** で、**[Site collection app permissions]\(サイト コレクションのアプリ アクセス許可\)** を選択します。 テナント ID は、任意のアプリ リストで "**@**" 記号に続く識別子です。 
      
       ![](./media/learning-create-pdf/tenant-id.png)
7. **[ドキュメントの変換]** アクションで、次の値を設定します。
   
   * **ソース ファイル名**: 動的なコンテンツ リストから、**[ファイル名]** を選択します。
   * **ソース ファイルのコンテンツ**: 動的なコンテンツ リストから、**[ファイルのコンテンツ]** を選択します。
   * **出力形式**: ドロップダウン リストから **[PDF]** を選択します。
     
     ![](./media/learning-create-pdf/muhimbi-configuration.png)

これまでに、次の手順を使用してフローを構成しました。 

1. 特定の OneDrive for Business フォルダーに新しいファイルが追加されるたびに、フローをトリガーする。 
2. Muhimbi サービスによって、そのファイルを PDF に変換する。 

最後の手順として、チームがアクセスできる SharePoint Online フォルダーに PDF ドキュメントを移動するアクションを追加する。  

1. **[新しいステップ]** を選択し、**[アクションの追加]** を選択します。  **SharePoint** を検索し、**[SharePoint – ファイルの作成]** アクションを選択します。 
   
    ![](./media/learning-create-pdf/sharepoint-create-file.png)
2. **[ファイルの作成]** アクションで、次の値を設定します。
   
   * **サイトのアドレス**: SharePoint サイトの URL です。  
   * **フォルダー パス**: フォルダー アイコンを選択し、**[PDF - 完了ファイル]** フォルダーに移動します。
   * **ファイル名**: **[ドキュメントの変換]** の動的なコンテンツ リストから **[基本ファイル名]** を選択し、"**.pdf**" を追加して、この拡張子でファイルが SharePoint に保存されるようにします。 
   * **ファイルのコンテンツ**: **[ドキュメントの変換]** の動的なコンテンツ リストから、**[Processed file content]\(処理対象のファイルのコンテンツ\)** を選択します。
3. 作業内容を保存するページの上部で、**[フローの作成]** を選択します。
   
    ![](./media/learning-create-pdf/sharepoint-configure-file.png)

## <a name="test-the-flow"></a>フローのテスト
1. フローをテストするには、OneDrive for Business の **[完了ドキュメント]** フォルダーに新しいファイルを追加します。 
2. フローで、**[自分のフロー]** を選択し、実行履歴を表示する新しいフローを選択します。 既定では、フローは 5 分ごとに実行するように構成されます。 
3. フローが実行された後で、ファイルが PDF に変換され、SharePoint の **[PDF – 完了ファイル]** フォルダーに保存されていることを確認します。 
   
    ![](./media/learning-create-pdf/test-the-flow.png)

