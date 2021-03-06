﻿---
title: 'ユーザーのボイス メール: Exchange Online Help'
TOCTitle: ユーザーのボイス メール
ms:assetid: 48e1f43b-fb7e-4a52-a2cb-0fb5da6ca65f
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Aa997885(v=EXCHG.150)
ms:contentKeyID: 49896233
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# ユーザーのボイス メール

 

_**適用先:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

ユニファイド メッセージング (UM) を使用すると、Exchange 組織内のユーザーは、すべての電子メールおよび音声メッセージを 1 つのメールボックスで受信することができます。 ユニファイド メッセージング機能およびボイス メール機能は、ユーザーの生産性を向上させ、組織全体のメッセージングをより柔軟にします。

組織にユーザーを追加する際は、メールボックスを作成するか、既存のメールボックスにユーザーを接続させることができます。 ユーザーに対してメールボックスを作成するか、ユーザーを既存のメールボックスに接続させると、ユニファイド メッセージングに対してメールボックスを有効にすることが可能になり、ユーザーはボイス メール システムおよびボイス メールに備えられた機能を使用できるようになります。 ユーザーのユニファイド メッセージングを有効にすると、電子メール、ボイス メール、ファックス メッセージがすべてユーザーのメールボックスに配信されます。 Microsoft Office Outlook 2007 およびそれ以降のバージョン、Outlook Web App、Microsoft ExchangeActiveSync 対応の携帯電話、または通常の電話や携帯電話を使用して、ユーザーが電子メール、音声メッセージ、個人用連絡先、および予定表情報にアクセスすることができます。

**目次**

ボイス メール ユーザーのプロパティ

ボイス メール ユーザーと他の UM コンポーネントとの関係

内線番号と SIP アドレス

EAC を使用してユーザーの UM およびボイス メールを有効にする

シェルを使用してユーザーの UM およびボイス メールを有効にする

ユーザーの UM を無効にする

## ボイス メール ユーザーのプロパティ

ユニファイド メッセージングを有効にするには、事前にユーザーにメールボックスを持たせる必要があります。 しかし、既定では、メールボックスを持つユーザーのユニファイド メッセージングは有効になっていません。 ユーザーの UM を有効にすると、ユーザーの UM プロパティおよびボイス メール機能を管理、変更、および構成できるようになります。 EAC またはシェルを使用して、ユーザーのユニファイド メッセージングを有効にすることができます。詳細については、「[ボイス メール用にユーザーを有効にする](enable-a-user-for-voice-mail-exchange-2013-help.md)」を参照してください。 複数の UM ユーザーを有効にするには、EAC または Exchange 管理シェルの **Enable-UMMailbox** コマンドレットを使用します。

## ボイス メール ユーザーと他の UM コンポーネントとの関係

あるユーザーのユニファイド メッセージングを有効にする場合、そのユーザーは既存の UM メールボックス ポリシーに関連付けされているか、またはリンクされている必要があります。また、ユーザーの内線番号を指定する必要があります。 シェルで **Enable-UMMailbox** コマンドレットを使用するか、またはユーザーのユニファイド メッセージングを有効にする際に UM メールボックス ポリシーを選択することにより、ユーザーを UM メールボックス ポリシーに関連付けることができます。 既定では、UM ダイヤル プランを作成すると、新しく UM メールボックス ポリシーが作成されます。 このポリシーを変更することもできますし、別のポリシーを作成してダイヤル プランにリンクすることで、ユーザーまたはユーザー グループに適用する機能や設定を指定することもできます。

UM メールボックス ポリシーには、ユーザーに対するダイヤル制限や PIN ポリシーなどの設定が含まれています。 UM メールボックス ポリシーを作成する場合、1 つの UM ダイヤル プランにのみ関連付ける必要があります。 クライアント アクセス サーバーまたはメールボックス サーバーはすべて着信呼び出しに応答が可能になり、UM ダイヤル プランにリンクされている UM が有効なユーザーすべてに対しボイス メール サービスを提供できます。ユーザーに対してユニファイド メッセージングを有効にすると、UM メールボックス ポリシーの設定が、UM が有効なユーザーに適用されます。

## 内線番号と SIP アドレス

ユーザーのユニファイド メッセージングを有効にする場合、ボイス メールがそのユーザーのメールボックスに送信されたときにユニファイド メッセージングで使用する内線番号を少なくとも 1 つ定義する必要があります。 ユーザーのユニファイド メッセージングを有効にすると、ユーザーのメールボックスに 2 つめの内線番号を追加することも、ユーザーのメールボックスに Exchange ユニファイド メッセージング プロキシ アドレス (EUM プロキシ アドレス) を構成することで、2 つめの内線番号を変更または削除することも、さらには EAC でユーザーの追加の内線番号または 2 つめの内線番号を追加または削除することもできます。 EUM プロキシ アドレスを削除することで EAC 内のメインの内線番号を削除できますが、メインの内線番号を削除することはお勧めしません。 メインの内線番号を削除すると、ユーザーのメールボックスに呼び出しを適切に転送できなくなります。


> [!NOTE]
> UM が有効なユーザーに追加可能な 2 つめの内線番号には制限はありませんが、ユーザーごとに設定可能なメインの内線番号は 1 つだけです。



UM が有効なユーザーのメールボックスに関連付けることができるのは、1 つの UM ダイヤル プランだけです。 UM が有効なユーザーには、内線番号を次のように割り当てることができます。

  - 1 つのメインの内線番号、SIP (セッション開始プロトコル) アドレス、または 1 つのダイヤル プランの E.164 アドレス。

  - 複数の 2 つめの内線番号、SIP アドレス、または 1 つのダイヤル プランの E.164 アドレス。

  - 複数のメインの内線番号、SIP アドレス、または 2 つの個別のダイヤル プランの E.164 アドレス。


> [!NOTE]
> 各内線番号、SIP アドレス、E.164 番号は、ダイヤル プラン内で一意である必要があり、ダイヤル プランの桁数は、ダイヤル プランにリンクされているすべてのユーザーに使用されます。



たとえば、ニューヨークから東京に頻繁に旅行する、UM が有効なユーザーがいるとします。 このユーザーのメールボックスには、ニューヨークのダイヤル プランが関連付けられていて、1 つの内線番号が構成されています。 また、このユーザーのメールボックスには、東京のダイヤル プラン用に 2 つ目の内線番号が構成されています。 発信者がいずれの内線番号をダイヤルしてこのユーザーに音声メッセージを残した場合も、音声メッセージは同じ UM が有効なメールボックスに配信されます。

ページのトップへ

## EAC を使用してユーザーの UM およびボイス メールを有効にする

ユーザーの Exchange メールボックスを作成すると、EAC で **\[ユニファイド メッセージング\]** の下の **\[詳細の表示\]** を使用して UM メールボックス設定を構成できます。 ユーザーを有効にすると、構成する必要がある設定が次のようにいくつかあります。

1.  **\[SIP アドレス\]**   これは、ユーザーの SIP アドレスです。 UM に対して有効にしようとしているユーザーが SIP URI ダイヤル プランにリンクされている UM メールボックス ポリシーに割り当てられている場合は、この設定を確認できます。 SIP URI ダイヤル プランは、Office Communications Server 2007 R2 または Microsoft Lync Server を統合する際に使用されます。 ユーザーを SIP URI または E.164 ダイヤル プランにリンクされている UM メールボックス ポリシーに割り当てる場合、これまでどおりユーザーの内線番号も入力する必要があります。 メインの内線番号は、ユーザーが Outlook Voice Access にアクセスする際に使用されます。

2.  **\[内線番号\]**   UM を有効にするユーザーに対しては、内線番号を手動で入力する必要があります。
    
    ユーザーに対し有効な内線番号を指定し、番号をダイヤル プランで指定された桁数と一致させる必要があります。 1 ～ 20 の数字しか入力できません。一般的な内線番号は 3 ～ 7 桁の番号で、UM メールボックス ポリシーがリンクされ、ユーザーに割り当てられているダイヤル プラン上で構成します。

3.  **ユーザーの PIN 設定:** 
    
      - **\[PIN を自動的に生成する\]**   この設定を行うと、UM が有効なユーザーが Outlook Voice Access を介してボイス メールにアクセスするために使用する PIN が自動的に生成されます。これは既定の設定です。 このボタンをクリックすると、ユーザーに割り当てられた UM メールボックス ポリシーで構成された PIN ポリシーに基づいて、自動的に PIN が生成されます。ユーザーの PIN を保護するために、この設定を使用することをお勧めします。 UM が有効になった後にユーザーが受け取るウェルカム メッセージの中で、PIN が送信されます。 既定では、ボイス メールを取得するためにユーザーがはじめてメールボックスにサインインしたときに、ユーザーはこの PIN を変更する必要があります。
    
      - **\[PIN の入力\]**   この設定を行うと、ユーザーがボイス メール システムにアクセスする際に使用する PIN を手動で指定できるようになります。
        
        指定する PIN は、この UM が有効なユーザーと関連付けられた UM メールボックス ポリシーで構成された PIN ポリシーの設定に従っている必要があります。 たとえば、UM メールボックス ポリシーが 7 桁以上の PIN だけを受け付けるように構成されている場合、このボックスに入力する PIN は 7 桁以上にする必要があります。
    
      - **\[初回サインイン時にユーザーに PIN のリセットを要求する\]**   この設定を行うと、ユーザーは、はじめて Outlook Voice Access を使用して電話からボイス メール システムにアクセスしたときに、ボイス メールの PIN が強制的にリセットされます。 ユーザーはよりわかりやすい PIN を入力することを要求されます。データや受信トレイを不正なアクセスから保護するために、ユーザーがはじめてサインインしたときに PIN を変更することを UM が有効なユーザーに強制することは、セキュリティ上のベスト プラクティスです。このチェック ボックスは既定でオンになっています。

## シェルを使用してユーザーの UM およびボイス メールを有効にする

この例では、tonysmith@contoso.com に対するメールボックスのユニファイド メッセージングとボイス メールを有効にし、内線番号を設定し、ユーザーの PIN を手動で設定し、このユーザーを `MyUMMailboxPolicy` という名前の UM メールボックス ポリシーに割り当てます。

    Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -PINExpired $true

この例では、tonysmith@contoso.com に対するメールボックスのユニファイド メッセージングとボイス メールを有効にし、`MyUMMailboxPolicy` という名前の UM メールボックス ポリシーにユーザーを割り当て、内線番号と SIP アドレスを設定し、このユーザーの PIN を手動で設定します。

    Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -SIPResourceIdentifier "tonysmith@contoso.com" -PINExpired $true

## ユーザーの UM を無効にする

ユーザーのユニファイド メッセージングを無効にしても、発信者が UM 自動応答メニューまたは Outlook Voice Access を使用してディレクトリ検索を実行した場合、ユーザーのアカウントが表示されることがあります。 発信者がディレクトリにユーザーを見つけたとしても、そのユーザーに連絡しようとすると、ユニファイド メッセージングのメイン メニューに戻ります。 そのため、発信者にシステムへの不満が生じる可能性があります。 発信者がディレクトリ検索を使用してユニファイド メッセージングが無効になっているユーザーに連絡できないようにするには、ユーザーを別のボイス メール システムに接続し、UM 自動応答のディレクトリ検索からユーザーを削除するか、ユーザーのアカウントを削除します。

UM が有効なユーザー アカウントのユニファイド メッセージングを無効にした後でも、そのユーザーは、Outlook Voice Access または Microsoft Outlook を使用して自分の UM が有効なメールボックスにアクセスできる場合があります。このようなことは、すべての変更がディレクトリ内で一致していない場合に起こる可能性があります。 アカウントのユニファイド メッセージングが無効になっているにもかかわらず、そのユーザーがメールボックスにアクセスできるというリスクを軽減するには、レプリケーションを手動で行うか、ユーザーのユニファイド メッセージングを無効にしたときにそのユーザーのメールボックスからすべてのユニファイド メッセージング情報を削除します。

