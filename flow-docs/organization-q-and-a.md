---
title: "組織における Flow サインアップの Q&A | Microsoft Docs"
description: "Office 365 テナントにおける Flow のライセンス、管理、およびユーザー サインアップに関してよくある質問と回答"
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/05/2016
ms.author: stepsic
ms.openlocfilehash: f8807ca0941761018c92a385c26f427e69ededcb
ms.sourcegitcommit: 56d69fadcbc9169feb2e1a68d9e9361709084cf4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="flow-in-your-organization-qa"></a>組織における Flow の Q & A
このトピックでは、組織のユーザーが Flow を使用する方法と、管理者が Flow サービスを制御する方法について説明します。

## <a name="signing-up-for-flow"></a>Flow にサインアップする
### <a name="what-is-microsoft-flow"></a>Microsoft Flow とは何ですか。
Microsoft Flow は個人やチームを支援するパブリック クラウド サービスです。お気に入りのアプリとサービスの間のワークフローを自動化し、同期、通知の受信、データ収集などを行うことができます。 

### <a name="how-do-people-sign-up-for-flow"></a>Flow にサインアップするにはどうすればよいですか?
個人が Web ポータルから Flow にサインアップするには、2 つの方法があります。

#### <a name="option-1"></a>オプション 1
[flow.microsoft.com](https://flow.microsoft.com) にアクセスし、**[無料でサインアップ]** を選択し、[portal.office.com](https://portal.office.com/Start?sku=flow_free) または [signup.live.com](https://signup.live.com) で Flow のサインアップ プロセスを完了します。

#### <a name="option-2"></a>オプション 2
[flow.microsoft.com](https://flow.microsoft.com) にアクセスし、**[サインイン]** を選択し、職場、学校、個人のメールでサインインし、Flow の使用条件に同意します。    

組織のユーザーがオプション 2 の方法で Flow にサインアップすると、そのユーザーには Microsoft Flow Free のライセンスが自動的に割り当てられます。

詳しくは、「[Flow にサインアップする](sign-up-sign-in.md)」をご覧ください。

### <a name="can-i-block-another-person-from-signing-up-for-flow"></a>他のユーザーが Flow にサインアップすることを禁止できますか?
Microsoft Flow は完全なパブリック クラウド サービスです。世界中のすべてのユーザーが Flow にサインアップし、Flow を使って日常のタスクを自動化できます。 Microsoft Flow を使用するとき、Office 365 アカウントを用意すること、使用することは要求されません。 このため、現時点では、他のユーザーが Flow を使うのを禁止するメカニズムはありません (世界中のすべてのユーザーがメール アドレスに関係なく使用できます)。

ただし、誰かが Microsoft Flow にサインアップするとき、組織内ではサポートしないことを選択した場合、そのユーザーが会社にコストを発生させることはありません。 個人が Microsoft Flow に新規登録するとき、その関係は、Bing、Wunderlist、OneDrive、Outlook.com のような Microsoft の他のクラウド サービスと同様に、個人と Microsoft の間の関係になります。Microsoft Flow を個人で利用するとき、組織がサービスの提供者として解釈されることは決してありません。

最後になりますが、会社が Microsoft Flow 内の組織専用データの使用を制限する場合、データ損失防止 (DLP) ポリシーでそれを実行できます。

### <a name="how-can-people-gain-access-to-the-paid-features-of-microsoft-flow"></a>どうすれば Microsoft Flow の有料機能にアクセスできますか?
個人が Microsoft Flow の有料機能を利用するには、3 つの方法があります。

1. Flow Plan 1 または Flow Plan 2 の 90 日間無料評価版にサインアップする
2. Office 365 管理ポータルでユーザーに Flow ライセンスを割り当てる
3. ユーザーに割り当てられている Office 365 プランまたは Dynamics 365 プランで Flow サービスを利用できる Flow 機能を含む Office 365 プランまたは Dynamics 365 プランの一覧は [Flow の価格設定ページ](https://flow.microsoft.com/pricing/)でご覧いただけます。

### <a name="can-i-block-another-person-from-using-the-paid-features-of-flow"></a>他のユーザーが Flow の有料機能を使用することをブロックできますか?
個人は誰でも Microsoft Flow の有料機能を 90 日間無料で試すことができます。コストは発生しません。 ただし、Office 365 管理ポータルを利用すれば、組織内の永久有料ライセンスの割り当てを完全管理できます。

無料で提供されるものであり、必ずしも会社の推薦ではない、個人と Microsoft の直接関係である評価版に個人がサインアップします。

## <a name="administration-of-flow"></a>Flow の管理
### <a name="why-has-the-flow-icon-appeared-in-the-office-365-app-launcher"></a>Office 365 アプリ起動ツールに Flow アイコンが表示されているのはなぜですか?
8 月に発表したように、Microsoft Flow は Office 365 スイートの基本構成要素となりました。 この発表から 3 か月後、Microsoft Flow は、すべての既存 Office 365 SKU でサービスとして有効になりました。 世界中のユーザーが Microsoft Flow を利用できるようになったため、アプリ起動ツールに表示されています。

既定でアプリ起動ツールから Flow タイルを削除する方法については、次のセクションをご覧ください。

### <a name="how-do-i-remove-microsoft-flow-from-the-app-launcher-for-my-organization"></a>組織のアプリ起動ツールから Microsoft Flow を削除するにはどうすればよいですか?
あるユーザーに Flow Plan 1 または Flow Plan 2 のライセンスが割り当てられている場合、次の手順でそのユーザーの Flow ライセンスを削除できます。ライセンスを削除すれば、アプリ起動ツールから Flow アイコンが削除されます。

1. [[Office 365 管理ポータル]](https://portal.microsoftonline.com/) に移動します。
2. 左のナビゲーション バーで、**[ユーザー]** を選択し、**[アクティブ ユーザー]** を選択します。
3. ライセンスを削除するユーザーを見つけ、その名前を選択します。
4. ユーザーの詳細ウィンドウの **[製品ライセンス]** セクションで、**[編集]** を選択します。
5. **Microsoft Flow Plan 1** または **Microsoft Flow Plan 2** という名前のライセンスを見つけて **[オフ]** に切り替え、**[保存]** を選択します。
   
   ![](./media/organization-q-and-a/remove-license.png)

Office 365 プランや Dynamics 365 プランのライセンスでユーザーが Flow を利用できる場合、そのプランに含まれる追加機能へのアクセスを次の手順で無効にできます。

1. [[Office 365 管理ポータル]](https://portal.microsoftonline.com/) に移動します。
2. 左のナビゲーション バーで、**[ユーザー]** を選択し、**[アクティブ ユーザー]** を選択します。
3. アクセスを削除するユーザーを見つけ、その名前を選択します。
4. ユーザーの詳細ウィンドウの **[製品ライセンス]** セクションで、**[編集]** を選択します。
5. ユーザーの Office 365 または Dynamics 365 ライセンスを展開し、**Flow for Office 365** または **Flow for Dynamics 365** という名前のサービスへのアクセスを無効にし、**[保存]** を選択します。
   
   ![](./media/organization-q-and-a/remove-service-plan.png)

ライセンスの一括削除は PowerShell でも可能です。 詳しい例については、「[Remove licenses from user accounts with Office 365 PowerShell](https://technet.microsoft.com/library/dn771774.aspx)」 (Office 365 PowerShell を利用し、ユーザー アカウントからライセンスを削除する) を参照してください。   最後になりますが、ライセンス内のサービスを一括削除する方法は、「[Disable access to services with Office 365 PowerShell](https://technet.microsoft.com/library/dn771769.aspx)」 (Office 365 PowerShell を利用し、サービスへのアクセスを無効にする) でもご確認いただけます。

組織のユーザーに対して Flow のライセンスまたはサービスを削除すると、そのユーザーを対象に、次の場所から Flow アイコンが削除されます。

1. [Office.com](https://office.com)
   
   ![](./media/organization-q-and-a/office-home.png)
2. Office 365 アプリ起動ツール
   
   ![](./media/organization-q-and-a/office-waffle.png)

この場合、既定で Flow のタイルが削除されるだけです。 ユーザーは引き続き個人として Microsoft Flow の使用を選択できます。

### <a name="why-did-10000-licenses-for-microsoft-flow-show-up-in-my-office-365-tenant"></a>Office 365 テナントで Microsoft Flow の 10,000 ライセンスが表示されたのはなぜですか?
Microsoft Flow の Plan 1 または 2 を 90 日間試用できます。そのような評価版ライセンスがテナントの新しい Flow ユーザーの収容可能人数を表します。 これらのライセンスには料金が発生しません。 Office 365 管理ポータルに 10,000 の (評価版) ライセンスが表示されるとき、具体的に次の 2 つの理由が考えられます。

1. 2016 年 4 月から 2016 年 10 月までの間でテナント内の 1 名以上のユーザーが Flow に参加した場合、"Microsoft PowerApps and Logic flows" というラベルの付いた 10,000 ライセンスが表示されます。
   
    ![](./media/organization-q-and-a/licenses2.png)
2. テナント内の 1 名以上のユーザーが「[How do users sign up for PowerApps](#how-do-people-sign-up-for-flow)」 (PowerApps にサインアップする方法) セクションの試用サインアップ **Option 1** で Flow Plan 2 評価版にサインアップした場合、"Microsoft Power Apps & Flow" というラベルの付いた 10,000 ライセンスが表示されます。
   
    ![](./media/organization-q-and-a/licenses1.png)

Office 365 ポータルから追加ライセンスをユーザーに自分で割り当てることができますが、それは Microsoft Flow Plan 2 の評価版ライセンスであり、ユーザーに割り当ててから 90 日後に期限が切れることに注意してください。

### <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>無料ですか?  ライセンスの料金を請求されますか?
明示的な同意なしでは、ユーザーが組織にコストを発生させることはありません。無料ライセンスと評価版ライセンスのいずれも、組織に何の料金も発生させません。 また、クォータの実行など、クォータは試用されません。

### <a name="i-removed-the-microsoft-flow-free-license-and-users-can-still-access-flow"></a>Microsoft Flow 無料ライセンスを削除しました。ユーザーは Flow に引き続きアクセスできますか?
Microsoft Flow 無料ライセンスは、追跡目的でのみ含まれています。 最初のセクションで説明したように、他のユーザーが個人として Microsoft Flow を使用することを禁止することはできません。 そのため、Microsoft Flow 無料ライセンスは実際にはいかなる機能も付与したり削除したりすることはありません。

### <a name="why-cant-i-see-all-flow-licenses-in-the-office-365-admin-portal"></a>Office 365 管理ポータルにすべての Flow ライセンスが表示されないのはなぜですか?
Microsoft Flow は、個人または組織の一員として利用できます。 組織レベルのライセンスは Office 365 ポータルに常に表示されます。 しかしながら、個人として試用版に新規登録した場合、Office 365 の管理対象外となるため、ポータルには表示されません。

### <a name="how-does-an-individual-find-out-what-plan-they-are-on"></a>個人のプランを確認する方法はありますか?
[https://flow.microsoft.com/pricing](https://flow.microsoft.com/pricing) の Flow 価格ページでご自分のプランをご確認いただけます。 現在利用しているプランまたは試用版が表示されます。

### <a name="will-microsoft-flow-sign-up-impact-the-identities-in-my-organization"></a>Microsoft Flow サインアップは組織の ID に影響を与えますか?
組織に Office 365 環境が既にあり、組織のすべてのユーザーが Office 365 アカウントを持っている場合、ID 管理に変更はありません。

組織に Office 365 環境が既にあっても、組織に Office 365 アカウントを持っていないユーザーがいる場合は、テナントにユーザーが作成され、ユーザーの職場または学校の電子メール アドレスに基づいてライセンスが割り当てられます。 つまり、管理対象のユーザーの数は、組織のユーザーがサービスにサインアップすると増えます。

組織に電子メール ドメインに接続された Office 365 環境がない場合は、ID の管理方法について変更はありません。 ユーザーは新しいクラウド専用のユーザー ディレクトリに追加され、管理者はテナント管理者として引き継いでユーザーを管理できます。

### <a name="a-new-tenant-was-created-by-microsoft-flow-how-do-i-manage-this"></a>新しいテナントが Microsoft Flow で作成されましたが、どのように管理すればよいですか?
新しいテナントが Microsoft Flow によって作成された場合、次の手順でそのテナントを要求して管理できます。

1. 管理するテナント ドメインと一致する電子メール アドレス ドメインを使って Flow にサインアップすることで、テナントに参加します。 たとえば、Microsoft が contoso.com テナントを作成した場合は、@contoso.com で終わる電子メール アドレスでテナントに参加します。
2. ドメインの所有権を確認することによって、管理コントロールを要求します。テナントに参加した後は、ドメインの所有権を確認することによって自分自身を管理者の役割に昇格させることができます。 そのためには次のようにします。    
   
   1. [https://portal.office.com](https://portal.office.com/Start?sku=flow_free) にアクセスします。
   2. 左上のアプリ起動ツール アイコンを選んで、[管理者] を選びます。
   3. **[Become the admin]** (管理者になる) ページで説明を読み、**[Yes, I want to be the admin]** (はい、管理者になります) を選びます。  
      
       **注**: このオプションが表示されない場合、Office 365 管理者は既にいます。

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>複数のドメインがある場合、ユーザーが追加される Office 365 テナントを制御できるか
何も変更しなければ、各ユーザーの電子メール ドメインとサブドメインにテナントが作成されます。

電子メール アドレス拡張に関係なくすべてのユーザーを同じテナントに追加したい場合は、次のようにします。  

* 前もって対象のテナントを作るか、既存のテナントを使います。 そのテナントに統合する既存のすべてのドメインとサブドメインを追加します。 その後は、これらのドメインおよびサブドメインの電子メール アドレスを持つすべてのユーザーは、サインアップすると自動的に対象テナントに参加します。

**重要**: テナントが作成された後で、ユーザーをテナント間で移動する自動メカニズムはありません。 1 つの Office 365 テナントにドメインを追加する方法については、[Office 365 へのユーザーとドメインの追加に関する記事](https://support.office.com/article/Add-your-users-and-domain-to-Office-365-ffdb2216-330d-4d73-832b-3e31bcb5b2a7)をご覧ください。

### <a name="how-can-i-restrict-my-users-ability-to-access-my-organizations-business-data"></a>ユーザーが組織のビジネス データにアクセスする機能を制限するにはどうすればよいですか?
Microsoft Flow では、下の図のように、ビジネス用のデータ ゾーンとビジネス以外のデータ ゾーンを作成できます。 このようなデータ損失防止ポリシーを導入すると、ビジネス データとビジネス以外のデータを組み合わせる Flow をユーザーは設計したり、実行したりできなくなります。 詳細については、「[データ損失防止 (DLP) ポリシー](prevent-data-loss.md)」を参照してください。

  ![](./media/organization-q-and-a/data-loss-prevention-policy.png)

