﻿---
title: 'メールボックス データベース ドライブの仕様が見つからない_MailboxEDBDriveDoesNotExist: Exchange 2013 Help'
TOCTitle: メールボックス データベース ドライブの仕様が見つからない_MailboxEDBDriveDoesNotExist
ms:assetid: 0e487aa1-3194-4a14-b255-a8b9f9afbf0e
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/ms.exch.setupreadiness.mailboxedbdrivedoesnotexist(v=EXCHG.150)
ms:contentKeyID: 48269171
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# メールボックス データベース ドライブの仕様が見つからない\_MailboxEDBDriveDoesNotExist

 

_**適用先:** Exchange Server_

_**トピックの最終更新日:** 2016-12-09_

このトピックの内容は、Microsoft Exchange Server 2013 向けに更新されていません。まだ更新されていませんが、そのままで Exchange 2013 にも適用できる可能性があります。ヘルプが必要な場合は、以下のコミュニティ リソースを確認してください。

問題がある場合は、Exchange のフォーラムで質問してください。 次のフォーラムにアクセスしてください。[Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612)、 [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542)、 または [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351)。

このサーバーの以前のインストールで使用されたメールボックス データベース ドライブの仕様にアクセスできないため、Microsoft® Exchange Server 2007 障害回復セットアップ プログラムを続行できません。

Microsoft Exchange 障害回復セットアップ プログラムを実行するには、以前このサーバーに対して使用したものと同じメールボックス データベース ドライブの仕様が、復元時に使用できる必要があります。

この問題を解決するには、ドライブを元の論理ドライブ構成に一致するように構成した後、Microsoft Exchange 障害回復セットアップ プログラムを再実行します。

**ドライブ文字の割り当てまたは変更**

1.  **\[コンピューターの管理** **(ローカル)\]** を開きます。

2.  コンソール ツリーで、**\[コンピューターの管理 (ローカル)\]** をクリックし、**\[記憶域\]** をクリックします。次に、**\[ディスクの管理\]** をクリックします。

3.  パーティション、論理ドライブ、またはボリュームを右クリックし、**\[ドライブ文字とパスの変更\]** をクリックします。

4.  次のいずれかの手順を実行します。
    
      - ドライブ文字を割り当てるには、**\[追加\]** をクリックします。次に、使用するドライブ文字をクリックし、**\[OK\]** をクリックします。
    
      - ドライブ文字を変更するには、そのドライブ文字をクリックし、**\[変更\]** をクリックします。次に、使用するドライブ文字をクリックし、**\[OK\]** をクリックします。

ドライブ文字を割り当てる方法の詳細については、ドライブ文字の割り当て、変更、または削除についてのページ ([http://go.microsoft.com/fwlink/?LinkId=66764](https://go.microsoft.com/fwlink/?linkid=66764)) を参照してください (このサイトは英語の場合があります)。

