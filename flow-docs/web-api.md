---
title: フローが Common Data Service for Apps に格納され、豊富な Web API を使用するようになりました
description: フローが Common Data Service for Apps に格納され、豊富な Web API を使用するようになりました。
author: stepsic-microsoft-com
ms.reviewer: deonhe
ms.date: 03/05/2019
ms.topic: article
ms.prod: ''
ms.service: business-applications
ms.technology: ''
ms.author: stepsic
audience: Power user
ms.openlocfilehash: 111fb191c6963e02d7bf54b419fd7088ce7605fc
ms.sourcegitcommit: 9ecf4956320d465a3bf618b79a9023b729d33c89
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57463031"
---
# <a name="microsoft-flow-web-api"></a>Microsoft Flow Web API

今後、すべてのフローは Common Data Service (CDS) for Apps に格納され、[豊富な Web API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/perform-operations-web-api) が利用されます。

このコンテンツでは、Microsoft Flow の **[ソリューション]** タブに含まれるフローの管理について説明しています。 現在、**[マイ フロー]** 以下のフローはこのような API ではサポートされていません。

## <a name="compose-http-requests"></a>HTTP 要求を作成する

要求の作成を始めるには、まず URL を構築する必要があります。 Microsoft Flow Web API のベース URL の形式は `https://{Organization ID}.{Regional Subdomain}.dynamics.com/api/data/v9.1/` です。 次の 2 つのパラメーターがあります。

- **[組織 ID]** は、フローを格納する環境の一意の名前です。 Microsoft Flow の右上にある環境スイッチャーに組織 ID が表示されます。 **[組織 ID]** は **[環境 ID]** (フローの URL に表示される GUID) とは異なります。

     ![環境スイッチャー](media/web-api/get-organization-id.png "環境スイッチャー")

- **[Regional Subdomain]\(リージョンサブのドメイン\)** は、環境の場所によって変わります。 Microsoft Flow にサインインすると、Web ページの URL でご自分の環境のリージョンを確認できます。 そのリージョン名を使用して、次の表で対応するサブドメインを見つけてください。

     ![フローの URL](media/web-api/get-region-name.png "フローの URL")

     | Region (リージョン)         | サブドメイン   |
     | -------------- | ----------- |
     | 米国  | crm         |
     | 南米  | crm2        |
     | カナダ         | crm3        |
     | ヨーロッパ         | crm4        |
     | アジア太平洋   | crm5        |
     | オーストラリア      | crm6        |
     | 日本          | crm7        |
     | インド          | crm8        |
     | 米国政府  | crm9        |
     | イギリス | crm11       |

Online Management API の [[インスタンスの取得]](https://docs.microsoft.com/rest/api/admin.services.crm.dynamics.com/instances/getinstances) メソッドを使用して、利用できるインスタンスの一覧をプログラムで取得することもできます。

Web API に対する各要求で、`Accept` および `Content-type` ヘッダーを `application/json` に設定する必要があります。

最後に、`Authorization` ヘッダーに Azure AD ベアラー トークンを設定します。 CDS for Apps の Azure AD ベアラー トークンを取得する方法については、[こちら](https://docs.microsoft.com/dynamics365/customer-engagement/developer/authenticate-users)を参照してください。 たとえば、次の要求があります。

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows
Accept: application/json
Authorization: Bearer ey...
```

この応答には、その環境内からのフローの一覧が含まれています。

```http
{
    "@odata.context": "https://org00000000.crm0.dynamics.com/api/data/v9.1/$metadata#workflows",
    "value": [{
        "@odata.etag": "W/\"12116760\"",
        "category": 5,
        "statecode": 0,
        "workflowidunique": "00000000-0000-0000-0000-000000000001",
        "workflowid" : "00000000-0000-0000-0000-000000000002",
        "createdon": "2018-11-15T19:45:51Z",
        "_ownerid_value": "00000000-0000-0000-0000-000000000003",
        "modifiedon": "2018-11-15T19:45:51Z",
        "ismanaged": false,
        "name": "Sample flow",
        "_modifiedby_value": "00000000-0000-0000-0000-000000000003",
        "_createdby_value": "00000000-0000-0000-0000-000000000003",
        "type": 1,
        "description": "This flow updates some data in CDS for Apps.",
        "clientdata": "{\"properties\":{\"connectionReferences\":{\"shared_commondataservice\":{\"source\":\"NotSpecified\",\"id\":\"/providers/Microsoft.PowerApps/apis/shared_commondataservice\",\"tier\":\"NotSpecified\"}},\"definition\":{...}},\"schemaVersion\":\"1.0.0.0\"}"
    }]
}
```

## <a name="list-flows"></a>フローを一覧表示する

上記のように、`workflows` に対して `GET` を呼び出すことでワークフローの一覧を取得できます。 各ワークフローには多くのプロパティがありますが、関連性の高いものは次のとおりです。

| プロパティ名     | 説明                                              |
| ----------------- | -------------------------------------------------------- |
| category          | フローのカテゴリ。 次の種類があります。0 - クラシック CDS for Apps ワークフロー、1 - クラシック CDS for Apps ダイアログ、2 - ビジネス ルール、3 - クラシック CDS for Apps アクション、4 - ビジネス プロセス フロー、5 - 自動化されたインスタント フローまたはスケジュールされたフロー。 |
| statecode         | フローの状態。 状態は **0** - オフ、または **1** - オンです。|
| workflowuniqueid  | フローのこのインストールの一意識別子。 |
| workflowid        | すべてのインポート全体でのフローの一意識別子。 |
| createdon         | フローが作成された日付。 |
| _ownerid_value    | フローを所有するユーザーまたはチームの一意識別子。 これは、CDS for Apps での systemusers エンティティの ID です。 |
| modifiedon        | フローの最終更新日時。 |
| ismanaged         | フローがマネージド ソリューションを介してインストールされたかどうかを示します。 |
| name              | フローに付けた表示名。 |
| _modifiedby_value | フローを最後に更新したユーザー。 これは、CDS for Apps での systemusers エンティティの ID です。 |
| _createdby_value  | フローを作成したユーザー。 これは、CDS for Apps での systemusers エンティティの ID です。 |
| type              | フローが実行中のフローか、追加のフローを作成するために使用できるテンプレートかを示します。 1 - フロー、2 - アクティブ化、または 3 - テンプレート。 |
| 説明       | ユーザーが指定したフローの説明。 |
| clientdata        | connectionReferences とフローの定義を含むオブジェクトの文字列エンコードされた JSON。 |

特定のプロパティを要求する、フローの一覧をフィルター処理するなどの操作も実行できます。詳細については、[データのクエリを実行するための CDS for Apps API ドキュメント](https://docs.microsoft.com/dynamics365/customer-engagement/developer/webapi/query-data-web-api)に関するページを参照してください。 たとえば、このクエリからは、現在有効な自動フロー、インスタント フロー、またはスケジュールされたフローのみが返されます。

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows?$filter=category eq 5 and statecode eq 1
Accept: application/json
Authorization: Bearer ey...
```

## <a name="create-a-flow"></a>フローを作成する

フローを作成するには、`workflows` コレクションに対して `POST` を呼び出します。 自動フロー、インスタント フロー、およびスケジュールされたフローの必須のプロパティは、category、name、type、primaryentity、および clientdata です。 このような種類のフローの primaryentity には `none` を使用します。

description と statecode を指定することもできます。

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
        "category": 5,
        "statecode": 0,
        "name": "Sample flow name",
        "type": 1,
        "description": "This flow reads some data from CDS for Apps.",
        "primaryentity":"none",
        "clientdata": "{\"properties\":{\"connectionReferences\":{\"shared_commondataservice\":{\"connectionName\":\"shared-commondataser-00000000-0000-0000-0000-000000000004\",\"source\":\"Invoker\",\"id\":\"/providers/Microsoft.PowerApps/apis/shared_commondataservice\"}},\"definition\":{\"$schema\": \"https:\/\/schema.management.azure.com\/providers\/Microsoft.Logic\/schemas\/2016-06-01\/workflowdefinition.json#\",\"contentVersion\": \"1.0.0.0\",\"parameters\": {\"$connections\": {\"defaultValue\": {},\"type\": \"Object\"},\"$authentication\": {\"defaultValue\": {},\"type\": \"SecureObject\"}},\"triggers\": {\"Recurrence\": {\"recurrence\": {\"frequency\": \"Minute\",\"interval\": 1},\"type\": \"Recurrence\"}},\"actions\": {\"List_records\": {\"runAfter\": {},\"metadata\": {\"flowSystemMetadata\": {\"swaggerOperationId\": \"GetItems_V2\"}},\"type\": \"ApiConnection\",\"inputs\": {\"host\": {\"api\": {\"runtimeUrl\": \"https:\/\/firstrelease-001.azure-apim.net\/apim\/commondataservice\"},\"connection\": {\"name\": \"@parameters('$connections')['shared_commondataservice']['connectionId']\"}},\"method\": \"get\",\"path\": \"\/v2\/datasets\/@{encodeURIComponent(encodeURIComponent('default.cds'))}\/tables\/@{encodeURIComponent(encodeURIComponent('accounts'))}\/items\",\"queries\": {\"$top\": 1},\"authentication\": \"@parameters('$authentication')\"}}},\"outputs\": {}}},\"schemaVersion\":\"1.0.0.0\"}"
}
```

最も重要なセクションは、フローが使用する connectionReferences が含まれている `clientdata` と、フローの [definition](https://docs.microsoft.com/azure/logic-apps/logic-apps-workflow-definition-language) です。 connectionReferences は、フローが使用する各接続へのマッピングです。

次の 3 つのプロパティがあります。

| プロパティ名  | 説明                                                 |
| -------------- | ----------------------------------------------------------- |
| connectionName | 接続を特定します。 **Connections** ページに移動し、接続の URL からコピーすることで、connectionName を確認することができます。 |
| source         | `Embedded` または `Invoker` です。 `Invoker` はインスタント フロー (ユーザーがボタンを選択してフローを実行したフロー) の場合にのみ有効であり、エンド ユーザーが接続を提供することを示します。 この場合、connectionName は設計時にのみ使用されます。 接続が `Embedded` の場合は、指定した connectionName が常に使用されることを意味します。 |
| id             | コネクタの識別子。 id は常に `/providers/Microsoft.PowerApps/apis/` で始まり、次にコネクタ名が含まれます。これは、接続の URL からコピーするか、**[コネクタ]** ページからコネクタを選択してコピーして取得できます。 |

`POST` 要求を実行すると、新しいフローの `workflowid` を含む `OData-EntityId` ヘッダーを受け取ります。

## <a name="update-a-flow"></a>フローを更新する

ワークフローに対して `PATCH` を呼び出し、フローの更新、有効化、または無効化を行うことができます。 このような呼び出しには `workflowid` プロパティを使用します。 たとえば、次の呼び出しを使用するとフローの説明と所有者を更新できます。

```http
PATCH https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows(00000000-0000-0000-0000-000000000002)
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "description" : "This flow will ensure consistency across systems.",
    "ownerid@odata.bind": "systemusers(00000000-0000-0000-0000-000000000005)",
}
```

> [!NOTE]
> 所有者を変更する構文には `odata.bind` 形式を使用します。 つまり、\_ownerid_value フィールドに直接パッチを適用する代わりに、`@odata.bind` をプロパティ名に追加してから `systemusers()` を使用して ID をラップします。

もう 1 つの例を挙げると、次の呼び出しを使用してフローを有効にすることができます。

```http
PATCH https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows(00000000-0000-0000-0000-000000000002)
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "statecode" : 1
}
```

### <a name="delete-a-flow"></a>フローを削除する

単純な `DELETE` の呼び出しを使用してフローを削除します。

```http
DELETE https://org00000000.crm0.dynamics.com/api/data/v9.1/workflows(00000000-0000-0000-0000-000000000002)
Accept: application/json
Authorization: Bearer ey...
```

> [!NOTE]
> 有効なフローを削除することはできません。 まずフローをオフにする必要があります (前の「**フローを更新する**」を参照してください)。そうしないと、エラー `Cannot delete an active workflow definition.` が表示されます。

## <a name="get-all-users-with-whom-a-flow-is-shared"></a>フローが共有されているすべてのユーザーを取得する

アクセス権を持つユーザーを一覧表示するには、CDS for Apps の*関数*を使用します。 この関数は、`Target` の 1 つのパラメーターを受け取ります。

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/RetrieveSharedPrincipalsAndAccess(Target=@tid)?@tid={'@odata.id':'workflows(00000000-0000-0000-0000-000000000002)'}
Accept: application/json
Authorization: Bearer ey...
```

`Target` パラメーターは、`@odata.id` という単一のプロパティを持つ JSON のような文字列です。 上記の例のワークフロー ID を置き換えます。 戻り値は次のとおりです。

```http
{
    "@odata.context": "https://org00000000.crm0.dynamics.com/api/data/v9.1/$metadata#Microsoft.Dynamics.CRM.RetrieveSharedPrincipalsAndAccessResponse",
    "PrincipalAccesses": [
        {
            "AccessMask": "ReadAccess",
            "Principal": {
                "@odata.type": "#Microsoft.Dynamics.CRM.systemuser",
                "ownerid": "00000000-0000-0000-0000-000000000005"
            }
        }
    ]
}
```

## <a name="share-or-unshare-a-flow"></a>フローの共有または共有解除

`GrantAccess` アクションを使用してフローを共有することができます。

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/GrantAccess
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "Target" : {
        "@odata.type": "Microsoft.Dynamics.CRM.workflow",
        "workflowid" : "00000000-0000-0000-0000-000000000002"
    },
    "PrincipalAccess": {
        "Principal": {
            "@odata.type" : "Microsoft.Dynamics.CRM.systemuser",
            "ownerid" : "00000000-0000-0000-0000-000000000005"
        },
        "AccessMask": "ReadAccess"
    }
}
```

`AccessMask` パラメーターは、さまざまなアクセス許可レベルに対して次の値を持つフィールドです。

| Name (名前)         | 説明                                          |
| ------------ | ---------------------------------------------------- |
| None         | アクセス権がありません。                                           |
| ReadAccess   | フローを読み取る権利。                          |
| WriteAccess  | フローを更新する権利。                        |
| DeleteAccess | フローを削除する権利。                        |
| ShareAccess  | フローを共有する権利。                         |
| AssignAccess | フローの所有者を変更する権利。           |

コンマを使用して複数のアクセス許可を組み合わせることができます。たとえば、`ReadAccess,WriteAccess` を渡すことで、フローの読み取りと更新の両方を実行できます。

`RevokeAccess` アクションを使用してフローの*共有を解除*することができます。 次に例を示します。

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/RevokeAccess
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "Target" : {
        "@odata.type": "Microsoft.Dynamics.CRM.workflow",
        "workflowid" : "00000000-0000-0000-0000-000000000002"
    },
    "Revokee": {
        "@odata.type" : "Microsoft.Dynamics.CRM.systemuser",
        "ownerid" : "00000000-0000-0000-0000-000000000005"
    }
}
```

`RevokeAccess` を使用すると、`AccessMask` で付与されているすべてのアクセス許可が削除されます。

## <a name="export-flows"></a>フローをエクスポートする

フローを .zip ファイルにエクスポートするには、`ExportSolution` アクションを使用します。 まず、目的のフローを[ソリューション](https://flow.microsoft.com/blog/solutions-in-microsoft-flow/)に追加します。

ソリューションにフローが追加されたら、次のアクションを呼び出します。

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/ExportSolution
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "SolutionName" : "Awesome solution 1",
    "Managed": false
}
```

`ExportSolution` を使用すると、base 64 でエンコードされた文字列が `ExportSoutionFile` プロパティで返されます。

```http
{
    "@odata.context": "https://org00000000.crm0.dynamics.com/api/data/v9.1/$metadata#Microsoft.Dynamics.CRM.ExportSolutionResponse",
    "ExportSolutionFile": "UEsDBBQAAgAI..."
}
```

このファイルをソース管理に保存したり、必要なバージョン管理や配布システムを使用したりすることができます。

## <a name="import-flows"></a>フローをインポートする

ソリューションをインポートするには、`ImportSolution` アクションを呼び出します。

| プロパティ名                    | 説明                               |
| -------------------------------- | ----------------------------------------- |
| OverwriteUnmanagedCustomizations | CDS for Apps にこのようなフローの既存のインスタンスがある場合、インポートするには、このフラグを `true` に設定する必要があります。 それ以外の場合は上書きされません。 |
| PublishWorkflows                 | インポート時にクラシック CDS for Apps ワークフローをアクティブ化するかどうかを示します。 この設定は他の種類のフローには適用されません。 |
| ImportJobId                      | インポート ジョブを追跡するために新しい一意の GUID を指定します。 |
| CustomizationFile                | ソリューションを含む base 64 でエンコードされた zip ファイル。 |

```http
POST https://org00000000.crm0.dynamics.com/api/data/v9.1/ImportSolution
Accept: application/json
Authorization: Bearer ey...
Content-type: application/json
{
    "OverwriteUnmanagedCustomizations": false,
    "PublishWorkflows" : true,
    "ImportJobId" : "00000000-0000-0000-0000-000000000006",
    "CustomizationFile" : "UEsDBBQAAgAI..."
}
```

インポートは長時間かかる操作なので、ImportSolution アクションに対する応答は `204 No content` になります。 進行状況を追跡するには、`importjobs` オブジェクトに対して `GET` を呼び出し、元の `ImportSolution` アクションに含めた `ImportJobId` を指定します。

```http
GET https://org00000000.crm0.dynamics.com/api/data/v9.1/importjobs(00000000-0000-0000-0000-000000000006)
Accept: application/json
Authorization: Bearer ey...
```

この呼び出しで、`progress` (完了の割合)、`startedon`、`completedon` (インポートが完了した場合) などのインポート操作の状態が返されます。

インポートが正常に完了したら、`connectionNames` は対象の環境で異なる可能性があるため (仮に接続が存在する場合)、フローの接続を設定する必要があります。 対象の環境で新しい接続を設定する場合は、フローの所有者がそれらを Microsoft Flow Designer で作成する必要があります。 新しい環境で接続が既に設定されている場合は、接続の名前を使用してフローの `clientData` に対する `PATCH` を実行できます。
