---
title: "Microsoft Flow の作成時に環境を切り替える | Microsoft Docs"
description: "Microsoft Flow を作成するときにさまざまな環境を使用する方法"
services: 
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/27/2016
ms.author: sunayv
ms.openlocfilehash: bcbb566c20291da14881d771c538dd89689b6b1d
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2017
---
# <a name="choosing-an-environment"></a>環境を選択する
Microsoft Flow は、さまざまな環境で作業できるほか、環境の切り替えも簡単に行うことができます。 この記事では、環境に関する次のトピックを取り上げます。

* 環境の機能の概要
* 環境を切り替える
* 適切な環境でフローを作成する方法

## <a name="environments-overview"></a>環境の概要
環境では、フロー、接続、ゲートウェイなどのリソースの分離境界を提供しています。 フローを作成する際は、フローをホストする環境と、そのフローで使用するリソースを選択します。 シナリオに応じて異なる環境を使用できます。

いくつかの例を示します。

* Microsoft Common Data Service への接続を使用するフローの作成。 このシナリオでは、フローと Microsoft Common Data Service は同一の環境に存在します。 このため、すべてのデータは環境 (分離境界) 内で分離されます。
* 人事部門向けのフローの作成。 人事部門のユーザーのみがそのフローにアクセスできるようにする必要があります。 たとえば、販売グループがそのフローを使用できないようにします。 このシナリオでは、人事部門のユーザーのみがアクセス許可を持つ別の環境を使用して、フローとフローで使用されるリソース (ゲートウェイや接続など) をホストすることができます。
* フローを使用して SharePoint のデータを表示する、ヨーロッパのユーザーがいる場合。 このシナリオでは、フローと SharePoint 接続をホストする環境をヨーロッパに作成します。 このヨーロッパの環境では、すべてのリソースがヨーロッパに存在するため (データのローカリティ)、ヨーロッパのユーザーは最高のパフォーマンスを得られます。

環境は、Microsoft Flow の管理者によって作成されます。 このような管理者は、異なる環境にアクセスできるユーザーも制御します。

このトピックでは、異なる環境間で移動する方法を示します。 環境の作成と管理の方法の詳細については、[環境の管理](environments-overview-admin.md)に関するページを参照してください。

## <a name="switching-environments"></a>環境を切り替える
Microsoft Flow では、非常に簡単に環境を切り替えることができます。 切り替えを行うと、その特定の環境のすべての項目が表示されます。他の環境の項目は表示されません。

次に例を示します。

*Human Resources* 環境に *NewEmployee* という名前のフローを作成します。 [flow.microsoft.com](http://flow.microsoft.com) で、*Sales* 環境を開きます。 *NewEmployee* フローは表示されません。 *NewEmployee* フローを表示するには、*Human Resources* 環境を開きます。 これは、接続、ゲートウェイ、PowerApps など、その環境で作成するすべての項目に適用されますので注意してください。

1. [flow.microsoft.com](http://flow.microsoft.com) を開きます。
2. 右上隅に、ユーザーの名前と現在の環境が表示されます。  
   ![](./media/environments-overview-maker/default-environment.png)
   
    画像では通知に注目してください。 これらの通知は、この既定の環境のフローに固有です。
3. 自分の名前を選択します。 ドロップダウン リストには、ユーザーが使用できるすべての環境が一覧表示されます。 現在の環境が選択されています。  
   ![](./media/environments-overview-maker/all-environments.png)
4. 別の環境に切り替えるには、一覧でその環境を選択します。  
   ![](./media/environments-overview-maker/select-europe.png)
5. Microsoft Flow は、新しい環境に自動的に切り替わります。  
   ![](./media/environments-overview-maker/europe-environment.png)
   
    画像で通知が表示されなくなったことに注目してください。 新しい Europe 環境には通知がありません。

## <a name="create-flows-in-the-right-environment"></a>適切な環境でのフローの作成
フローを作成する前に、フローを作成する環境を選択していることを必ず確認してください。 選択していない場合は、フローを削除して、正しい環境で再作成することになります。

フローを作成する環境を選択する際は、次のことを考慮してください。

* ゲートウェイは既定の環境に作成されます。 ゲートウェイは他の環境に作成できないため、オンプレミスのデータに接続する場合は既定の環境を使用する必要があります。
* フローで使用できるのは、同じ環境内にある接続とリソースのみです。 別の環境のリソースを使用することはできません。 たとえば、カスタム コネクタを使うフローを作成しているものとします。 このカスタム コネクタは、フローと同じ環境に存在する必要があります。
* Microsoft Common Data Service データベースが関連付けられている環境は常に 1 つだけです。 つまり、Microsoft Common Data Service のデータを使用する場合は、そのデータベースと同じ環境を選択する必要があります。
* リソースの編集が可能な環境がすべて表示されます。 ただし、すべての環境で新しいリソースを作成できるという意味ではありません。 このため、一部の環境では新しいフローを作成できない場合があります。 管理者に依頼して "**作成者**" として環境に追加してもらうか、別の環境を選んでフローを作成する必要があります (既定の環境にはいつでもフローを作成できます)。

## <a name="what-you-did"></a>結果
上記の手順を使用すると、使用するためのアクセス許可を持っている複数の環境を切り替えます。 これで、フローの作成を開始できます。

## <a name="next-steps"></a>次のステップ
[テンプレートからフローを作成する](get-started-logic-template.md)  
[フローを作成する](get-started-logic-flow.md)  
[管理者に関する環境の概要](environments-overview-admin.md)

