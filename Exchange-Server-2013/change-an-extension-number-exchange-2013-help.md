﻿---
title: '内線番号の変更: Exchange Online Help'
TOCTitle: 内線番号の変更
ms:assetid: ff22b366-3bfb-4bf7-9f11-62fba48f1caf
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Bb232208(v=EXCHG.150)
ms:contentKeyID: 50555903
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# 内線番号の変更

 

_**適用先:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

ユーザーの UM を有効にし、内線電話番号ダイヤル プランにリンクすると、ユーザーの内線番号を含む、そのユーザーの EUM プロキシ アドレスが作成されます。ボイス メールをユーザーのメールボックスに送信できるようにするには、使用する UM の内線番号を少なくとも 1 つ定義する必要があります。この内線番号は、ユーザーが Outlook Voice Access 番号を呼び出すときにも使用されます。

ユーザーの UM を有効にしたときに追加されたメインの内線番号、または後から追加された第 2 内線番号、およびユーザーの関連する EUM プロキシ アドレスは変更可能です。ユーザーの UM を有効にしたときに追加されたメインの内線番号は、プライマリ EUM プロキシ アドレスとして表示されます。追加した第 2 内線番号は、セカンダリ EUM プロキシ アドレスとして表示されます。内線番号が変更された場合、発信者は設定されたすべての新しい内線番号でユーザーにボイス メールを残すことができます。すべての音声メッセージは、同じユーザーのメールボックスに配信されます。

ユーザーのメインの内線番号および第 2 内線番号は、EAC またはシェルを使用して変更できます。メインの内線番号および第 2 内線番号は、EAC でユーザーのメールボックスの **\[電子メール アドレス\]** ページを使用して変更できます。EAC の **\[UM メールボックス\]** ページを、メインの内線番号の変更に使用することはできませんが、第 2 内線番号の変更には使用できます。第 2 内線番号を変更する場合は、まず、既存の第 2 内線番号を削除してからユーザーの正しい第 2 内線番号を追加します。

シェルで **Get-UMMailbox** コマンドレットまたは **Get-Mailbox** コマンドレットを使用して、ユーザーのメインの内線番号および第 2 内線番号を表示できます。

ボイス メールが有効なユーザーに関連する追加の管理タスクについては、「[ボイス メールが有効なユーザーの手順](voice-mail-enabled-user-procedures-exchange-2013-help.md)」を参照してください。

## 始める前に把握しておくべき情報

  - 予想所要時間:3 分。

  - この手順を実行する際には、あらかじめアクセス許可を割り当てる必要があります。必要なアクセス許可の一覧については、以下を参照してください。「[ユニファイド メッセージングのアクセス許可](unified-messaging-permissions-exchange-2013-help.md)」の「UM メールボックス」。

  - これらの手順を実行する前に、内線電話の UM ダイヤル プランが作成されていることを確認してください。詳細な手順については、「[UM ダイヤル プランを作成する](create-a-um-dial-plan-exchange-2013-help.md)」を参照してください。

  - この手順を実行する前に、UM メールボックス ポリシーが作成されていることを確認してください。詳細な手順については、「[UM メールボックス ポリシーの作成](create-a-um-mailbox-policy-exchange-2013-help.md)」を参照してください。

  - これらの手順を実行する際には、前もってユーザーのメールボックスで UM が有効に設定され、メールボックスが内線電話ダイヤル プランにリンクされていることを確認してください。詳細な手順については、「[ボイス メール用にユーザーを有効にする](enable-a-user-for-voice-mail-exchange-2013-help.md)」を参照してください。

  - これらの手順を実行する際には、前もってユーザーに割り当てる内線番号に UM ダイヤル プランで設定された正しい数の数字が含まれていることを確認してください。

  - このトピックの手順で使用可能なキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md)」を参照してください。


> [!TIP]
> 問題がある場合は、Exchange のフォーラムで質問してください。 次のフォーラムにアクセスしてください。<A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>、 <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>、 または <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>。.



## 必要な作業

## EAC を使用してメインの内線番号または第 2 内線番号を変更する

1.  EAC で、**\[受信者\]** \> **\[メールボックス\]**に移動します。

2.  リスト ビューで、内線番号を変更するメールボックスを選択し、**\[編集\]**![編集アイコン](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "編集アイコン") をクリックします。

3.  **\[ユーザー メールボックス\]** ページの **\[電子メール アドレス\]** の下で、変更する内線番号を選択し、**\[編集\]**![編集アイコン](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "編集アイコン") をクリックします。メインの内線番号は、太字の文字と数字で一覧に表示されます。

4.  **\[電子メール アドレス\]** ページで、**\[アドレス/内線番号\]** ボックスにユーザーの新しい内線番号を入力します。新しい UM ダイヤル プランを選択する場合は、**\[参照\]** をクリックします。

5.  **\[保存\]** をクリックします。

## シェルを使用してメインの内線番号または第 2 内線番号を変更する

この例では、"Tony Smith" という UM が有効なユーザーの内線番号を "22222" に変更します。


> [!NOTE]
> シェルを使用して内線番号を変更する際には、事前に変更する EUM プロキシ アドレスの位置を特定する必要があります。位置を決定するには、<STRONG>$mbx.EmailAddresses</STRONG> コマンドを使用します。最初の EUM プロキシ アドレスは既定の (メインの) 内線番号で、リスト内の 0 になります。



    $mbx=Get-Mailbox tony.smith
    $mbx.EmailAddresses.Item(0)="eum:22222;phone-context=MyDialPlan.contoso.com"
    Set-Mailbox tony.smith -EmailAddresses $mbx.EmailAddresses

