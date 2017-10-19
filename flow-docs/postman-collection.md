---
title: "Postman でカスタム コネクタを記述する | Microsoft Docs"
description: "カスタム コネクタを登録するための Postman Collection を作成します。"
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/28/2017
ms.author: sunayv
ms.openlocfilehash: fe98999ea307367c7f3b032974fef9be6ca3f388
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="describe-a-custom-connector-with-postman"></a>Postman でカスタム コネクタを記述する
[Postman](https://www.getpostman.com/) は、速く簡単に API を開発するためのツールです。 このチュートリアルでは、Postman Collection の作成方法を見ていただきます。Postman Collection を使うと、Microsoft Flow の[カスタム コネクタ](register-custom-api.md)を簡単に作成できます。

## <a name="prerequisites"></a>前提条件
* [Postman アプリ](https://www.getpostman.com/apps)をインストールします

## <a name="create-a-postman-collection"></a>Postman Collection を作成する
Azure Cognitive Services の [Text Analytics API](https://www.microsoft.com/cognitive-services/text-analytics-api) 用の Postman Collection を作成します。 この API は、渡されたテキストの言語、センチメント、キー フレーズを識別します。

1. Postman Collection を作成するときは、最初に要求を作成します。 要求を作成するときは、HTTP 動詞、要求 URL、クエリ パラメーターまたはパス パラメーター、ヘッダー、および本文を設定できます。 詳細については、Postman のドキュメントの「[Sending Requests](https://www.getpostman.com/docs/requests)」(要求の送信) をご覧ください。 Detect Language API エンドポイントに対して、次のように値を設定します。
   
    ![Postman 要求](./media/postman-collection/request.png)
   
    使用するパラメーターと値の詳細:
   
   | パラメーター | 値 |
   | --- | --- |
   | Verb |POST |
   | 要求 URL |https://westus.api.cognitive.microsoft.com/text/analytics/v2.0/languages |
   | パラメーター |numberOfLanguagesToDetect |
   | 認証 |"No Auth" |
   | ヘッダー |Ocp-Apim-Subscription-Key = <your subscription key> <br/>Content-Type = application/json |
   | 本文 |<code>{<br/>&nbsp;&nbsp;&nbsp;"documents": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": "1",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Hello World"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}<code> |
2. **[Send (送信)]** をクリックして要求を行い、応答を受け取ります。
3. **[Save (保存)]** をクリックして、Postman コレクションに要求を保存します。
   
    ![Postman の応答](./media/postman-collection/request-response-save.png)
4. **[Save Request (要求の保存)]** ダイアログ ボックスで、**[Request name (要求の名前)]** と **[Request description (要求の説明)]** を入力します。 これらの値は、カスタム コネクタで使用します。
   
    ![Postman によるコレクションの保存](./media/postman-collection/save-request-note.png)
   
    要求に対する応答を保存することもできます。 現在、カスタム コネクタは要求ごとに 1 つの応答のみをサポートしています。 要求ごとに複数の応答を保存すると、最初の 1 つだけが使われます。
   
    ![Postman による応答の保存](./media/postman-collection/save-response.png)
5. 他の要求と応答を作成して保存し、Postman Collection の作成を続けます。
6. すべての要求と応答の Postman Collection の作成が完了したら、コレクションをエクスポートします。
   
    ![Postman のエクスポート](./media/postman-collection/export.png)
7. エクスポートの形式として、**[Collection v1 (コレクション v1)]** を選びます。
   
    ![Postman のエクスポート](./media/postman-collection/export2.png)

この Postman Collection を使って、Microsoft Flow でカスタム コネクタを作成できるようになります。

> [!IMPORTANT]
> Postman Collection からカスタム コネクタを作成する場合は、アクションとトリガーからヘッダー `Content-type` を必ず削除してください。このヘッダーは Microsoft Flow によって自動的に追加されます。 認証ヘッダー (たとえば、 `Ocp-Apim-Subscription-Key`) は **[セキュリティ]** セクションに定義し、アクションとトリガーからは削除する必要があります。 
> 
> 

詳しくは、「[Microsoft Flow でカスタム コネクタを登録して使用する](register-custom-api.md)」をご覧ください。

