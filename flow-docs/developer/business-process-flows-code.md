---
title: コードを使用して業務プロセス フローを操作する | MicrosoftDocs
description: 業務プロセス フローをプログラミングによって操作して、さらに効率的かつ合理的な業務プロセスを作成する方法を説明します。
ms.custom: ''
ms.date: 07/09/2018
ms.reviewer: ''
ms.service: flow
ms.topic: article
ms.assetid: 67d8cf80-9f77-4804-97a1-cf9f61417e83
author: msftman
ms.author: deonhe
manager: kvivek
search.app:
- Flow
search.audienceType:
- developer
ms.openlocfilehash: 4fcbca859d167e82229aa60f96f5122912e5cca3
ms.sourcegitcommit: c7c9add30d5bf1ab6bd5b55b802fd28618b38411
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362980"
---
# <a name="work-with-business-process-flows-using-code"></a>コードを使用して業務プロセス フローを操作する

"*業務プロセス フロー*" によって、さらに効率的で合理的な、販売、サービス、その他の業務プロセスを作成できます。 また、エンティティ フォームの一番上に特別なコントロールが配置されて、業務プロセスが視覚化されます。 ユーザーに対して、販売、マーケティング、サービスのプロセスの完了までさまざまなステージが示されます。 各プロセスは複数のステージとステップをサポートします。 ステップの追加または削除、ステージの順序の変更、業務プロセス フローへの新しいエンティティの追加を行うことができます。  
  
さまざまな業務プロセス フロー インスタンスは、同じエンティティ レコードに対して同時に実行できます。 ユーザーは、同時実行の業務プロセス インスタンスを切り替えて、プロセスの現在のステージの作業を再開できます。 

このトピックでは、業務プロセス フローをプログラミングによって操作する方法を説明します。

> [!NOTE]
> 業務プロセス フローを操作するためにコードを記述する必要はありません。 UI を使用した業務プロセス フローの作成と管理について詳しくは、「[Business process flows overview](../business-process-flows-overview.md)」 (業務プロセス フローの概要) を参照してください。  

<a name="PrereqsBPF"></a>   
## <a name="prerequisites-for-business-process-flow"></a>業務プロセス フローの前提条件 

カスタム エンティティおよび UI フォームを更新したエンティティを業務プロセス フローに含めることができます。 更新された UI エンティティは、<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsAIRUpdated> プロパティが `true` に設定されます。 

業務プロセス フローに対してエンティティを有効にするには、<xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsBusinessProcessEnabled> プロパティを `true` に設定します。

> [!IMPORTANT]
>  業務プロセス フローに対するエンティティの有効化は一方向のプロセスです。 元に戻すことはできません。

   
<a name="DefineBPF"></a>   
## <a name="define-business-process-flow"></a>業務プロセス フローを定義する
  
ビジュアル業務プロセス フロー デザイナーを使用して、業務プロセス フローを定義します。 詳細情報: [業務プロセス フローを作成する](../create-business-process-flow.md)

既定では、業務プロセス フロー レコードが `Draft` 状態で作成されます。  

業務プロセス フローの定義は <xref:Microsoft.Dynamics.CRM.workflow> エンティティに格納され、業務プロセス フローのステージ情報は <xref:Microsoft.Dynamics.CRM.processstage> エンティティに格納されます。
  
<a name="ActivateBPF"></a>   
## <a name="activate-business-process-flow"></a>業務プロセス フローをアクティブ化する  
 プロセス フローを使用するには、前もってアクティブ化する必要があります。 アクティブ化するには、`Workflow` エンティティの `prvActivateBusinessProcessFlow` 権限を持っている必要があります。 <xref:Microsoft.Xrm.Sdk.Messages.UpdateRequest> メッセージを使用して、`Workflow` エンティティ レコードの状態を `Activated` に設定します。 詳細情報: [[更新] を使用して特化された操作を実行する](/dynamics365/customer-engagement/developer/org-service/perform-specialized-operations-using-update) 

 > [!NOTE]
 > 業務プロセス フロー デザイナーを使用して、業務プロセス フローをアクティブ化することもできます。 

<a name="BPFEntity"></a>   
## <a name="business-process-flow-entity"></a>業務プロセス フローのエンティティ 
 対応する `Workflow` エンティティ レコードの状態を変更するか、業務プロセス フロー デザイナーを使用して、業務プロセス フロー定義をアクティブ化すると、"*\<activesolutionprefix>*_*\<uniquename>*" (uniquename はユーザーが指定する名前から導出される) という名前のカスタム エンティティが自動的に作成され、アクティブ化された業務プロセス フロー インスタンスが格納されます。  
  
 たとえば、業務プロセス フロー定義の名前として "My Custom BPF" を指定し、アクティブ ソリューションのために既定の発行者 (新規) を使用している場合、プロセスのインスタンスを格納するために作成されたカスタム エンティティの名前は "new_mycustombpf" になります。  
  
 `uniquename` の値が業務プロセス フロー定義に対して存在しない場合、たとえば業務プロセス フローが以前のバージョンのソリューションからインポートされた場合は、カスタム エンティティの既定名が"`\<activesolutionprefix>_bpf_<GUID_BPF_Definition>`: になります。  
  
> [!IMPORTANT]
>  サンプルの業務プロセス フロー レコードは、システム エンティティを使用して、対応する業務プロセス フロー インスタンス レコードを格納します。  
>   
>  ただし、新しく作成するすべての業務プロセス フロー定義は、前述したようにカスタム エンティティを使用してインスタンス レコードを格納します。 

業務プロセス フローのエンティティの名前を取得するには、次のいずれかの方法を使用します。

- **UI を使用**: カスタマイズの UI を使用して、業務プロセス フローのエンティティを一覧から選択します。

    ![](media/bpf-entity-name.png)
- **Web API を使用**: 次の要求を使用します。

    **要求**

    ```
    GET [Organization URI]/api/data/v9.0/workflows?$filter=name eq 'My Custom BPF'&$select=uniquename HTTP/1.1
    ```

    **応答**
    ```
    {  
    "@odata.context":"[Organization URI]/api/data/v9.0/$metadata#workflows(uniquename)",
    "value":[  
         {  
             "@odata.etag":"W/\"1084677\"",
             "uniquename":"new_mycustombpf",
             "workflowid":"2669927e-8ad6-4f95-8a9a-f1008af6956f"
         }
      ]
    }
    ```
- **組織サービスを使用**: 次のコード サンプルを使用します。

    ```c#
    QueryExpression query = new QueryExpression
    {
        EntityName = "workflow",
        ColumnSet = new ColumnSet("uniquename"),
        Criteria = new FilterExpression
        {
            Conditions =
            {
                new ConditionExpression
                {
                    AttributeName = "name",
                    Operator = ConditionOperator.Equal,
                    Values = { "My Custom BPF" }
                }
            }
        }
    };
    Workflow Bpf = (Workflow)_serviceProxy.RetrieveMultiple(query).Entities[0]; 
    ```
> [!NOTE]
> <xref:Microsoft.Xrm.Sdk.Metadata.EntityMetadata.IsBPFEntity> プロパティは、業務プロセス フローのエンティティに対しては `true` となります。 インスタンス内の業務プロセス フロー エンティティをすべて取得するには、次の Web API 要求を実行します。
> ```http
> GET [Organization URI]/api/data/v9.0/EntityDefinitions?$select=SchemaName,LogicalName,DisplayName&$filter=IsBPFEntity eq true HTTP/1.1
> ```

<a name="BPFSecurity"></a>   
## <a name="manage-security-for-business-process-flows"></a>業務プロセス フローのセキュリティを管理する

業務プロセス フローをアクティブにしたときに、業務プロセス フローのインスタンスを格納するためのカスタム エンティティが自動的に作成されますが、このエンティティは Customer Engagement の他のカスタム エンティティと同様に標準のセキュリティ モデルに従います。 つまり、そのエンティティに付与された特権に基づいて、実行時に業務プロセス フローのユーザーに付与される許可が定義されます。

カスタム業務プロセス フロー エンティティのスコープは組織です。 このエンティティに対する通常の作成、取得、更新、削除の特権によって、ユーザーが自分に割り当てられたロールに基づいて持つことになるアクセス許可が定義されます。 既定の設定では、業務プロセス フローのカスタム エンティティが作成されるときにアクセス許可が付与されるセキュリティ ロールは**システム管理者**と**システム カスタマイザー**のみであるため、新しい業務プロセス フローのエンティティ (この例では **My Custom BPF**) にその他のセキュリティ ロールが必要な場合は明示的にアクセス許可を与える必要があります。

![](media/bpf-privileges.png)

<a name="ManageBPF"></a>   
## <a name="create-retrieve-update-and-delete-business-process-flow-entity-records-process-instances"></a>業務プロセス フローのエンティティ レコード (プロセス インスタンス) の作成、取得、更新、削除  
 業務プロセス フロー定義をアクティブにしたときに自動的に作成されるカスタム エンティティに、その業務プロセス フロー定義に対応するすべてのプロセス インスタンスが格納されます。 このカスタム エンティティは、Web API と CRM 2011 エンドポイントを使用する、標準的なプログラミングによるレコード (プロセス インスタンス) の作成と管理をサポートしています。

> [!IMPORTANT]
> エンティティ レコードのプロセス インスタンスを別のインスタンスに切り替えることは、UI (クライアント) で行うか、このセクションで示す情報を使用してプログラミングで行うことだけがサポートされています。 `SetProcess` メッセージ (<xref href="Microsoft.Dynamics.CRM.SetProcess?text=SetProcess Action" /> または <xref:Microsoft.Crm.Sdk.Messages.SetProcessRequest>) を使用してプログラミングでターゲット エンティティ レコードのプロセスを切り替える (別の業務フローをアクティブなプロセス インスタンスとして設定する) ことはできなくなりました。 

 複数のエンティティにまたがる業務プロセス フローがあるとします。名前は "My Custom BPF" で、3 つのステージがあります。S1:Account、S2:Account、および S3:Contact です。 

 ![](media/sample-bpf.png)
 
### <a name="retrieve-all-the-records-instances-for-a-business-process-flow-entity"></a>1 つの業務プロセス フロー エンティティに対応するレコード (インスタンス) をすべて取得する
 業務プロセス フロー エンティティの名前が "new_mycustombpf" の場合に、この業務プロセス フロー エンティティに対応するレコード (プロセス インスタンス) をすべて取得するには次のクエリを使用します。  
  
```http
GET [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
```

この時点では、インスタンスが存在しないため、応答でインスタンスを取得できません。 このトピックの後半では、業務プロセス フロー定義のインスタンスを作成した後で、この要求を実行します。

> [!NOTE]
> 業務プロセス フローのエンティティの名前を取得する方法については、前のセクション「[業務プロセス フローのエンティティ](#business-process-flow-entity)」をご覧ください。
  
### <a name="create-a-business-process-flow-entity-record-process-instance"></a>業務プロセス フローのエンティティ レコード (プロセス インスタンス) を作成する 

UI を使用せずにエンティティ レコードについて別の業務プロセス フローに切り替える場合は、業務プロセス フローのエンティティ レコード (プロセス インスタンス) をプログラミングで作成します。 

業務プロセス フローのエンティティ レコードを作成するには、次の値を指定する必要があります。 
- `@odata.bind` 注釈を使用して単一の値を持つナビゲーション プロパティを設定することで、業務プロセス フローのエンティティ レコードをプライマリ エンティティ レコードに関連付けます。 業務プロセス フロー定義のプライマリ エンティティ レコードを指すナビゲーション プロパティ名を見つけるには、[CSDL $metadata ドキュメント](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations.md#csdl-metadata-document)を使用します。 
- `@odata.bind` 注釈を使用して単一の値を持つナビゲーション プロパティを設定することで、業務プロセス フローのエンティティ レコードを、業務プロセス フロー定義に指定された有効なステージに関連付けます。 業務プロセス フロー定義のステージ レコードを指すナビゲーション プロパティ名 (通常は `activestageid`) を見つけるには、[CSDL $metadata ドキュメント](/dynamics365/customer-engagement/developer/webapi/web-api-types-operations.md#csdl-metadata-document)を使用します。

    また、業務プロセス フロー定義のすべてのステージの情報を取得するには、業務プロセス フロー定義の ID が 2669927e-8ad6-4f95-8a9a-f1008af6956f であると仮定して、次の Web API 要求を使用します。

    **要求**

    ```http
    GET [Organization URI]/api/data/v9.0/processstages?$select=stagename&$filter=processid/workflowid eq 2669927e-8ad6-4f95-8a9a-f1008af6956f HTTP/1.1
    ```

    **応答**

    ```http
    {
        "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#processstages(stagename)",
        "value": [
            {
                "@odata.etag": "W/\"858240\"",
                "stagename": "S1",
                "processstageid": "9a9185f5-b75b-4bbb-9c2b-a6626683b99b"
            },
            {
                "@odata.etag": "W/\"858239\"",
                "stagename": "S3",
                "processstageid": "a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a"
            },
            {
                "@odata.etag": "W/\"858238\"",
                "stagename": "S2",
                "processstageid": "19a11fc0-3398-4214-8522-cb2a97f66e4b"
            }
        ]
    }
    ```

次に、次の要求を使用して、アカウント レコード (ID=a176be9e-9a68-e711-80e7-00155d41e206) の業務プロセス フロー定義のインスタンスと、プロセス インスタンスの最初のステージとして設定されたアクティブなステージ S1 (ID=9a9185f5-b75b-4bbb-9c2b-a6626683b99b) を作成します。

**要求**

```http
POST [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
Content-Type: application/json; charset=utf-8 
OData-MaxVersion: 4.0 
OData-Version: 4.0 
Accept: application/json 

{
    "bpf_accountid@odata.bind": "/accounts(a176be9e-9a68-e711-80e7-00155d41e206)",
    "activestageid@odata.bind": "/processstages(9a9185f5-b75b-4bbb-9c2b-a6626683b99b)"    
}
```

**応答**

```http
HTTP/1.1 204 No Content
OData-Version: 4.0
OData-EntityId: [Organization URI]/api/data/v9.0/new_mycustombpfs(cc3f721b-026e-e811-80ff-00155d513100)
```

最初のステージ "***以外***" として設定されたアクティブなステージを含む業務プロセス フロー定義のインスタンスを作成しようとする場合は、要求に `traversedpath` を含める必要があることに注意してください。 渡ったパスは、業務プロセス フロー インスタンス内のアクセスしたステージを表すプロセス ステージ ID のコンマ区切り文字列です。 次の要求は、アカウント レコード (ID=679b2464-71b5-e711-80f5-00155d513100) のインスタンスと、第 2 ステージ S2 (ID=19a11fc0-3398-4214-8522-cb2a97f66e4b) として設定されるアクティブなステージを作成します。

```http
POST [Organization URI]/api/data/v9.0/new_mycustombpfs HTTP/1.1 
Content-Type: application/json; charset=utf-8 
OData-MaxVersion: 4.0 
OData-Version: 4.0 
Accept: application/json 

{
    "bpf_accountid@odata.bind": "/accounts(679b2464-71b5-e711-80f5-00155d513100)",
    "activestageid@odata.bind": "/processstages(19a11fc0-3398-4214-8522-cb2a97f66e4b)",
    "traversedpath":"9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b"   
}
```

### <a name="update-a-business-process-flow-entity-record-process-instance"></a>業務プロセス フローのエンティティ レコード (プロセス インスタンス) を更新する

プロセス インスタンスを更新して、次のステージまたは前のステージへの移動、プロセス インスタンスの破棄、プロセス インスタンスの再アクティブ化、またはプロセス インスタンスの終了を行うことができます。 

#### <a name="stage-navigation"></a>ステージのナビゲーション

別のステージに移動するには、アクティブ ステージ ID を変えるようにプロセス インスタンス レコードを更新し、それに応じて渡ったパスを更新する必要があります。 業務プロセス フローを更新するとき、次のステージか前のステージにしか移動できないことに注意してください。

ステージのナビゲーションを実行するには、更新する業務プロセス フロー インスタンスの ID が必要になります。 業務プロセス フローのすべてのインスタンスを取得するには、前の[業務プロセス フロー エンティティのすべてのレコード (インスタンス) の取得](#retrieve-all-the-records-instances-for-a-business-process-flow-entity)に関する説明をご覧ください。

更新するプロセス インスタンスの ID が dc2ab599-306d-e811-80ff-00155d513100 と仮定し、次の要求を使用して、アクティブなステージを S1 から S2 に更新します。

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1
Content-Type: application/json
OData-MaxVersion: 4.0
OData-Version: 4.0

{
    "activestageid@odata.bind": "/processstages(19a11fc0-3398-4214-8522-cb2a97f66e4b)",
    "traversedpath": "9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b"
}
```

#### <a name="change-the-state-of-a-process-instance-abort-reactivate-or-finish"></a>プロセス インスタンスの状態を変更する: 中止、再アクティブ化、完了 

プロセス インスタンスの状態は、**[アクティブ]**、**[完了済]**、**[中止]** のいずれかとなります。 状態は、プロセス インスタンス レコードの次の属性によって判別されます。

- **statecode**: プロセス インスタンスの状態が表示されます。

    |値|ラベル|
    |-----|-----|
    |0    |アクティブ|
    |1    |非アクティブ|

- **statuscode**: プロセス インスタンスの状態に関する情報が表示されます。

    |値|ラベル|
    |-----|-----|
    |1    |アクティブ|
    |2    |完了済|
    |3    |中止|

つまり、プロセス インスタンスを**中止**するには、`statecode` と `statuscode` の値を適切に設定して次の要求を使用します。

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1   
Content-Type: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0 
  
{ 
    "statecode" : "1", 
    "statuscode": "3" 
}
```
 
> [!NOTE]
> どのステージでもプロセス インスタンスを中止できます。

同様に、プロセス インスタンスを再アクティブ化するには、上記のコードの `statecode` と `statuscode` の値をそれぞれ **0** と **1** で置き換えます。

また、プロセス インスタンスの状態を **[完了済]** (プロセス インスタンスの最後のステージのみで可能) に設定するには、前のコードの `statecode` と `statuscode` の値をそれぞれ **0** と **2** で置き換えます。

#### <a name="cross-entity-navigation"></a>エンティティ間のナビゲーション

この例のエンティティ間のナビゲーションでは、プロセス インスタンスのアクティブなステージを最後のステージ S3 (ID=a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a) に設定し、それに応じて渡ったパスを更新し、業務プロセス フロー定義のようにプライマリ エンティティ レコードとして連絡先レコードを設定します。

```http
PATCH [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1   
Content-Type: application/json   
OData-MaxVersion: 4.0   
OData-Version: 4.0 
  
{
    "activestageid@odata.bind": "/processstages(a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a)",
    "traversedpath":"9a9185f5-b75b-4bbb-9c2b-a6626683b99b,19a11fc0-3398-4214-8522-cb2a97f66e4b,a107e2fd-7543-4c1a-b6b4-b8060ecb1a1a",
    "bpf_contactid@odata.bind": "/contacts(0e3f10b0-da33-e811-80fc-00155d513100)"
}
``` 

### <a name="delete-a-business-process-flow-entity-record-process-instance"></a>業務プロセス フローのエンティティ レコード (プロセス インスタンス) を削除する

次の Web API 要求を使用します。

**要求**

```http
DELETE [Organization URI]/api/data/v9.0/new_mycustombpfs(dc2ab599-306d-e811-80ff-00155d513100) HTTP/1.1
```  

**応答**

レコードが存在する場合は、正常に削除されたことを示す状態 204 の通常の応答を受け取ります。 エンティティが見つからない場合は、状態 404 を含む応答を受け取ります。

## <a name="use-retrieveprocessinstances-and-retrieveactivepath-messages"></a>RetrieveProcessInstances および RetrieveActivePath メッセージを使用する

`RetrieveProcessInstances` メッセージ (<xref href="Microsoft.Dynamics.CRM.RetrieveProcessInstances?text=RetrieveActivePath Function" /> または <xref:Microsoft.Crm.Sdk.Messages.RetrieveProcessInstancesRequest>) を使用して、すべての業務プロセス定義にまたがって、エンティティ レコードのすべての業務プロセス フロー インスタンスを取得します。 エンティティに対して返される業務プロセス フロー インスタンスの順序は、インスタンスの `modifiedon` 属性に基づいています。 たとえば、最近変更された業務プロセス フロー インスタンスが、返されるコレクションの "*最初の*" レコードになります。 最近変更された業務プロセス フロー インスタンスは、エンティティ レコードについて UI でアクティブになっているインスタンスです。  
  
`RetrieveProcessInstances` メッセージを使用した結果として、エンティティ レコードについて返される各業務プロセス フロー インスタンス レコードには、アクティブなステージの ID が `processstageid` 属性に格納されます。これを使用して、アクティブな ステージを見つけて、前のステージや次のステージに移動することができます。 これを行うためには、最初に、業務プロセス フロー インスタンスのアクティブなパスと、プロセス フロー インスタンスにあるステージを、`RetrieveActivePath` メッセージ (<xref href="Microsoft.Dynamics.CRM.RetrieveActivePath?text=RetrieveActivePath Function" /> または <xref:Microsoft.Crm.Sdk.Messages.RetrieveActivePathRequest>) を使用して見つける必要があります。   
  
 業務プロセス フロー インスタンスのアクティブなステージとアクティブなパスの情報を得たら、その情報を使用して、アクティブなパスで前のステージまたは次のステージに移動できます。 前方向へのステージのナビゲーションは順序どおりに行う必要があります。つまり、アクティブなパスの次のステージに前進してください。   
  
 [組織サービス](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)を使用してこれら 2 つの方法とステージ ナビゲーションの使用方法を示すサンプル コード全体については、「[サンプル: 業務プロセス フローの使用](sample-work-business-process-flows.md)」をご覧ください。 

<a name="ApplyBPF"></a>   
## <a name="apply-business-process-flow-while-creating-an-entity-record"></a>エンティティ レコードの作成時に業務プロセス フローを適用する

このセクションでは、Customer Engagement で作成した新しいエンティティ レコードに業務プロセス フローを自動的に適用する際の既定の動作に関する情報を提供し、選択した業務プロセス フローを新しいエンティティ レコードに適用するためにオーバーライドする方法を説明します。

既定では、複数の業務プロセス フローが定義されたエンティティに関して、システムは次の複数ステップのロジックを使用して新しいエンティティ レコードに業務プロセス フローを適用します。
1. 業務プロセス フロー定義レコードの **Workflow.PrimaryEntity** 属性に基づいて、新しいエンティティ レコードに適用可能なすべての業務プロセス フローを識別します。
2. 現在のユーザーがアクセスできる業務プロセス フロー定義を識別します。 業務プロセス フローに対するアクセスの判別と管理の方法について詳しくは、このトピックで前に説明した「[Manage security for business process flows](#BPFSecurity)」(業務プロセス フローのセキュリティを管理する) をご覧ください。<br/>  
3. システム内のすべての業務プロセス フロー定義には、エンティティごとにグローバルな順序が付けられます。 業務プロセス フローの順序は、**Workflow.ProcessOrder** 属性に格納されます。 1 つのエンティティの業務プロセス フロー定義はこの順序に基づいて並べられ、順序の値が最も小さい定義が選択されます。
4. また、エンティティ レコードがビジネス アプリ (アプリ モジュール) から作成される場合、もう 1 段階のフィルター処理が適用され、新しいエンティティ レコードに自動的に適用される業務プロセス フローが選択されます。 ユーザーがアプリを使用するとき、ビジネス アプリに割り当てられたセキュリティ ロールによってユーザーがアクセス権を持っている関連エンティティ、業務プロセス フロー、ビューとフォームにしかアクセスできません。 
    - ビジネス アプリに業務プロセス フローが含まれない場合、手順 3 までに説明されたように業務プロセス フローが適用されます。
    - ビジネス アプリに 1 つ以上の業務プロセス フローが府k間れる場合は、アプリに存在する業務プロセス フローのみが適用できます。 このケースでは、ユーザーがビジネス アプリのコンテキストを使用しているとき、手順 3 の業務プロセス フローの一覧がフィルター処理されて、アプリ モジュール内に存在するビジネス アプリに含まれるものだけに絞り込まれ、プロセスの順序に基づいて並べ替えられます。 
    - 業務プロセス フローがエンティティのビジネス アプリで使用できない場合、またはユーザーがアクセス権を持っていない場合、業務プロセス フローは新しいエンティティ レコードに適用されません。

業務プロセス フローが新しいエンティティ レコードに自動的に適用されるという既定ロジックをオーバーライドできます。 これを行うには、新しいエンティティ レコードを作成するときにエンティティの **ProcessId** 属性を、次のいずれかの値に設定します。
- **Guid.Empty** に設定すると、新しいエンティティ レコードの業務プロセス フローの設定がスキップされます。 エンティティ レコードを一括作成しているときに、業務プロセス フローを適用したくない場合には、この方法をお勧めします。
- 特定の業務プロセス フロー エンティティに設定します (エンティティ参照として)。 このケースでは、システムは既定のロジックではなく、指定された業務プロセス フローを適用します。

新しいエンティティ レコードの作成時に **ProcessId** 属性の値を設定しないと、前述したように、システムによって既定のロジックが適用されます。

> [!NOTE]
> 新しいエンティティ レコードへの業務プロセス フローの自動的な適用の既定ロジックをオーバーライドするには、プログラミングを使用するしかありません。 UI を使用して行うことはできません。

## <a name="legacy-process-related-attributes-in-entities"></a>エンティティにおける従来のプロセス関連の属性

業務プロセス フローに対応するエンティティの従来のプロセス関連の属性 (**ProcessId**、**StageId**、**TraversedPath** など) は、既に非推奨になっています。 ターゲット エンティティ レコードに対してこのような従来のプロセス関連の属性を操作すると、業務プロセス フローの状態の一貫性を保証できません。サポートされるシナリオ "***ではありません***"。 お勧めの方法は、「[Create, retrieve, update, and delete business process flow entity records (process instances)](#create-retrieve-update-and-delete-business-process-flow-entity-records-process-instances)」(業務プロセス フロー エンティティ レコード (プロセス インスタンス) の作成、取得、更新、削除) セクションで前に説明したように業務プロセス フロー エンティティの属性を使用することです。

唯一の例外は、前の「[エンティティ レコードの作成時に業務プロセス フローを適用する](#ApplyBPF)」で説明したように、新規レコードへの業務プロセス フローの既定の適用をオーバーライドするためにエンティティ レコードの作成時に **ProcessId** 属性をプログラミングによって変更することです。

<a name="BKMK_clientSideScript"></a>   
## <a name="client-side-programmability-support-for-business-process-flows"></a>業務プロセス フローに関するクライアント側でのプログラミングのサポート  
 クライアント側のオブジェクトを使用して、フォーム スクリプト内で業務プロセス フローと対話することができます。 業務プロセス フローによってクライアント側のイベントがトリガーされるたびに、プロセスのレコードへの適用、ステージの変更、または状態の変更 (`Active`、`Finished`、または `Aborted`) が行われます。 詳しくは、[formContext.data.process (クライアント API リファレンス)](/dynamics365/customer-engagement/developer/clientapi/reference/formcontext-data-process.md) に関する記事をご覧ください。  
  
<a name="BKMK_MaxSettings"></a>   
## <a name="maximum-number-of-processes-stages-and-steps"></a>プロセス、ステージ、およびステップの最大数  
 エンティティあたりの、アクティブ化された業務プロセス フローの最大数の既定値は 10 です。 `Organization.MaximumActiveBusinessProcessFlowsAllowedPerEntity` 属性を使用して違う値を指定できます。 ただし、値を 10 よりも大きくすると、プロセスを切り替えるとき、または業務プロセス フローが割り当てられたレコードを開くときに、システムのパフォーマンスが低下する可能性があります。 これはプロセスが複数のエンティティにまたがる場合に特に目立ちます。  
  
 次の設定はカスタマイズできません。  
  
-   プロセス内のエンティティごとのステージの最大数は 30 です。  
  
-   各ステージ内のステップの最大数は 30 です。  
  
-   プロセス フローに含めることができるエンティティの最大数は 5 です。  

