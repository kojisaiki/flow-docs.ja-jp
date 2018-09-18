---
title: 他のユーザーとボタンを共有します。 | Microsoft Docs
description: 他のユーザーも同じボタンを使用して時間を節約できるように、ボタンを共有します。
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/21/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 77b46d10ec3856054dcc8e1734b327bac9a01596
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690341"
---
# <a name="share-button-flows-in-microsoft-flow"></a>Microsoft Flow でボタン フローを共有する
Microsoft Flow モバイル アプリでは、[ボタン フロー](introduction-to-button-flows.md) (ボタン) を組織内の他のユーザーまたはグループと共有できます。 ボタンを共有すると、共有するユーザーまたはグループが自分のボタンを実行する場合と同じようにボタンを実行できます。 他のユーザーが共有したボタンへの[リンクを共有する](share-buttons.md#re-share-a-button)こともできます。 いつでもボタンの[共有を停止](share-buttons.md#stop-sharing-a-button)できます。

> このドキュメントで使用されるスクリーンショットは、Android デバイスから取得されています。 iPhone を使用している場合、画像の表示が異なる可能性がありますが、機能は同じです。
> 
> 

[次の手順](share-buttons.md#use-shared-buttons)に従って、他のユーザーと共有されているボタンを使用します。

## <a name="prerequisites"></a>前提条件
ボタンを共有するには、次のものが必要です。

* [Microsoft Flow](https://flow.microsoft.com) へのアクセス権を持つアカウント
* 共有するフロー。
* [Android](https://aka.ms/flowmobiledocsandroid)、[iOS](https://aka.ms/flowmobiledocsios)、または [Windows Phone](https://aka.ms/flowmobilewindows) 用の Microsoft Flow モバイル アプリがインストールされたモバイル デバイス。
* ボタンを共有する組織内のグループまたはユーザー。

## <a name="share-a-button"></a>ボタンを共有する
Microsoft Flow モバイル アプリの **[ボタン]** タブからボタンを共有できます。

1. 共有するボタンの横にある小さなアイコンをタップします。
   
    ![ボタンの共有](./media/share-buttons/share-button-flows-buttons-tab.png)
2. **[Button users]** (ボタンのユーザー) ページで **[Invite others]** (他のユーザーを招待) をタップします。
   
    ![ボタンの共有](./media/share-buttons/share-button-flows-button-users.png)
3. ボタンを共有するグループまたはユーザーを検索して選択します。
   
    ![ボタンの共有](./media/share-buttons/share-button-flows-invite-others-select.png)
4. **[Invite others]** (他のユーザーを招待) ページで **[送信]** をタップします。
   
    ![ボタンの共有](./media/share-buttons/share-button-flows-invite-others-send.png)
5. そのページで、ボタンを共有する操作が正常に完了したことを示す **[完了]** をタップします。
   
    ![ボタンの共有](./media/share-buttons/share-button-flows-invite-others-done.png)

## <a name="require-users-to-use-their-own-connections"></a>ユーザーに自分の接続を使用するよう要求する
> [!NOTE]
> ボタンを共有する場合、ボタンを共有したユーザーに、ボタンで使用されるすべての接続の使用を許可することができます。 また、そのユーザーに自分の接続を使用するよう要求することもできます。 接続の使用を他のユーザーに許可する場合、他のユーザーはその接続で資格情報にアクセスしたり、他のフローで再利用したりすることはできません。
> 
> 

以下の手順に従って、ボタンを共有したユーザーに自分の接続を使用するよう要求します。

1. ボタンを共有した直後に表示される画面で **[接続の管理]** を選択します。
2. 管理するボタンの **[編集]** を選択します。
3. **[ユーザーによって指定されました]** または自分のメール アドレスを選択します。
   
    この選択内容によって、共有ボタンで誰の接続を使用する必要があるかが示されます。
   
    ![ボタンの共有](./media/share-buttons/share-button-select-connection-provided-by-user.png)
   
    選択内容はいつでも表示または変更できます。 これを行うには、**[フロー]** タブ、共有したフロー、**[ユーザーと接続]**、**[接続]** タブ、管理するボタンの **[編集]** の順に選択します。
   
    ![ボタンの共有](./media/share-buttons/share-button-flows-conn-provided-by-user.png)

## <a name="view-the-list-of-button-users"></a>ボタンのユーザーの一覧を表示する
**[ボタン]** タブから次の手順を実行することで、ボタンが共有されているすべてのグループまたはユーザーを表示することができます。

1. 該当するボタンの横にある小さなアイコンをタップします。
2. **[ボタンのユーザー]** ページに、ボタンが共有されているすべてのグループまたはユーザーが表示されます。
   
    ![ボタンのユーザーを表示する](./media/share-buttons/share-button-flows-button-users-list.png)

## <a name="stop-sharing-a-button"></a>ボタンの共有を停止する
ボタンの共有を停止するには、**[ボタンのユーザー]** タブで次の手順を実行します。

1. 今後は共有したくないボタンの横にある小さなアイコンをタップします。
2. **[ボタンのユーザー]** ページで、ボタンの共有を停止するユーザーまたはグループをタップします。
   
    ![ボタンの共有を停止する](./media/share-buttons/share-button-flows-remove-user-list.png)
3. ユーザーのページが表示されたら、**[ユーザーの削除]** をタップします。
   
    ![ボタンの共有を停止する](./media/share-buttons/share-button-flows-remove-user.png)
4. 削除の操作が完了するまで待ちます。 **[Button users]** (ボタンのユーザー) ページが更新され、削除したユーザーまたはグループが一覧に含まれていないことを確認します。
   
    ![ボタンの共有を停止する](./media/share-buttons/share-button-flows-remove-user-result.png)

## <a name="monitor-the-run-history"></a>実行履歴を監視する
すべての実行履歴は、ボタンの共有相手により開始された実行も含めて、Microsoft Flow モバイル アプリのボタンの作成者の **[アクティビティ]** タブにのみ表示されます。

## <a name="use-shared-buttons"></a>共有ボタンを使用する
他のユーザーから共有されたボタンを実行するには、**[ボタンの追加]** ページから **[ボタン]** タブにボタンを追加する必要があります。

1. **[ボタン]** タブの **[GET MORE (さらに表示)]** (または表示されている場合は **[新しいボタンが使用可能です]** バナー) をタップします。
   
    ![自分が新しいボタンの共有相手になった場合](./media/share-buttons/share-button-flows-banner.png)
2. 使用するボタンをタップします。
   
    タップされたボタンは、Microsoft Flow アプリの **[ボタン]** タブにすぐに追加されます。 追加されると、**[ボタン]** タブに表示されている他のボタンと同様に、そのタブからボタンを使用できます。
   
    ![自分が新しいボタンの共有相手になった場合](./media/share-buttons/share-button-flows-buttons-shared-with-me.png)

## <a name="re-share-a-button"></a>ボタンを再共有する
共有されているボタンへのリンクを共有することができます。

1. 共有するボタンの横にある **[...]** を選択します。
2. **[ボタン リンクの共有]** を選択します。
   
    ![ボタン リンクを再共有する](./media/share-buttons/re-share-button.png)
3. ボタンを共有するために使用したいアプリを選択してから、手順に従って共有するユーザーにボタンを送信します。

## <a name="stop-using-a-shared-button"></a>共有ボタンの使用を停止する
自分が共有相手になっていたボタンが不要になった場合は、次の手順を使用して **[ボタン]** タブからそのボタンを削除します。

1. **[ボタン]** タブで、不要になったボタンの横にある **[...]** をタップします。
   
    ![ボタンを削除する](./media/share-buttons/share-button-flows-added-shared-button.png)
2. 表示されるメニューで **[削除]** をタップします。

これだけです。 そのボタンは、Microsoft Flow アプリの **[ボタン]** タブに表示されなくなります。

> [!NOTE]
> 共有ボタンを削除したあとで、削除したボタンを再度追加する必要がある場合は、**[ボタン]** タブで **[GET MORE (さらに表示)]** を選択します。
> 
> 

