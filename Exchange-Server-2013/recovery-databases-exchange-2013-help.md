﻿---
title: '回復用データベース: Exchange 2013 Help'
TOCTitle: 回復用データベース
ms:assetid: f3c6fd0b-2e25-442e-a0fc-46f663130c3e
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dd876954(v=EXCHG.150)
ms:contentKeyID: 48270246
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# 回復用データベース

 

_**適用先:** Exchange Server 2013_

_**トピックの最終更新日:** 2012-11-02_

回復用データベース (RDB) は特別な種類のメールボックス データベースで、回復操作の一部として、復元されたメールボックス データベースをマウントし、復元されたデータベースからデータを抽出できます。[New-MailboxRestoreRequest](https://technet.microsoft.com/ja-jp/library/ff829875\(v=exchg.150\)) コマンドレットを使用すると、RDB からデータを抽出できます。抽出後、データをフォルダーにエクスポートしたり、既存のメールボックスに結合したりできます。RDB を使用すると、現在のデータへのユーザー アクセスを妨げずに、データベースのバックアップやコピーからデータを回復できます。

Microsoft Exchange Server 2013 は、回復用データベースに直接データを復元する機能をサポートしています。回復されたデータを回復用データベースとしてマウントすると、管理者は個々のメールボックス、またはメールボックス内の個々のアイテムを復元できます。回復用データベースを復元する方法は 2 通りあります。

  - 回復用データベースが既に存在する場合、アプリケーションはデータベースをマウント解除し、データを回復用データベースとログ ファイル上に復元してから、データベースをもう一度マウントできます。

  - データベースとログ ファイルは任意のディスク位置に復元できます。Exchange は復元されたデータを分析してトランザクション ログを再生することで、データベースを最新の状態にします。その後、回復済みのデータベース ファイルをポイントするように回復用データベースを構成できます。

## メールボックス データベースと回復用データベースの相違

RDB はいくつかの点で、標準的なメールボックス データベースとは異なります。

  - RDB は、Exchange 管理シェルを使用して作成されます。

  - RDB からメールを送受信することはできません。RDB へのすべてのクライアント プロトコルのアクセス (SMTP、POP3、IMAP4 など) はブロックされます。この設計のため、RDB を使用して、メールをメッセージング システムに挿入したり、メッセージング システムから削除したりすることはできません。

  - Microsoft OfficeOutlook や Outlook Web App を使用したクライアント MAPI アクセスはブロックされます。RDB では MAPI アクセスがサポートされていますが、回復ツールやアプリケーションのみによってサポートされます。MAPI を使用して RDB のメールボックスにログインする場合は、メールボックス GUID とデータベース GUID の両方を指定する必要があります。

  - RDB 内のメールボックスをユーザー アカウントに接続することはできません。ユーザーが RDB 内のメールボックスのデータにアクセスできるようにするには、メールボックスを既存のメールボックスに結合するか、フォルダーにエクスポートする必要があります。

  - システムとメールボックスの管理ポリシーは適用されません。この設計により、回復プロセス中、RDB の項目はシステムによって削除されることはありません。

  - RDB では、オンライン保守は実行されません。

  - RDB では、循環ログを有効にすることはできません。

  - 任意の時点でメールボックス サーバーにマウントできる RDB は 1 つのみです。RDB の使用は、メールボックス サーバーごとのデータベース制限に対してカウントされません。

  - RDB のメールボックス データベース コピーを作成することはできません。

  - RDB は、復元操作のターゲットとして使用することはできますが、バックアップ操作のターゲットとして使用することはできません。

  - RDB としてマウントされた、回復したデータベースはいかなる方法でも、元のメールボックスに結び付けられることはありません。

## 回復用データベースの使用

RDB を使用する前に、特定の要件を満たす必要があります。RDB は、Exchange 2013 メールボックス データベースにのみ使用できます。Exchange の以前のバージョンのメールボックス データベースはサポートされていません。また、データの結合と抽出に使用するターゲット メールボックスは、RDB にマウントされたデータベースと同じ Active Directory フォレスト内に存在する必要があります。

RDB を使用すると、次のような場合にデータを回復することができます。

  - **同じサーバーのダイヤル トーン回復**   元のデータベースをバックアップから復元した後、ダイヤル トーン回復操作の一部として、RDB から回復を実行することができます。

  - **代替サーバーのダイヤル トーン回復**   代替サーバーを使用してダイヤル トーン データベースをホストし、元のデータベースをバックアップから復元した後で、RDB からデータを回復することができます。

  - **メールボックスの回復**   削除されたメールボックス保存期間が過ぎると、個々のメールボックスをバックアップから回復できるようになります。その後、復元されたメールボックスからデータを抽出して、ターゲット フォルダーにコピーするか、別のメールボックスと結合することができます。

  - **特定の項目の回復**   メールボックスから削除またはパージした項目をバックアップ データから復元することができます。


> [!NOTE]
> コンテンツをアクティブなメールボックスに回復する際、フォルダー アクセス制御リスト (ACL) は保持されません。通常、回復プロセスではメールボックス データが回復され、元のデータベースにコンテンツが結合されるので、ACL を回復またはコピーする必要はありません。



RDB は、次の条件とシナリオで、メールボックス データベースの回復に使用されます。

  - 元のデータベースとそのデータベース内のメールボックスに関する論理情報は、Active Directory 内で変更されずにそのまま残ります。

  - 1 つのメールボックスや 1 つのデータベースを復元する必要があります。回復シナリオには、次のものがあります。
    
      - ダイヤル トーン データベースの使用中に、データベースを回復または修復して、最終的には 2 つのデータベースを結合する。
    
      - そのデータベースの元のサーバー以外のサーバーで、データベースを回復する。その後、必要に応じて、回復したデータを元のサーバーに結合できる。
    
      - 削除された項目の保存期間が過ぎた後、ユーザーが以前にメールボックスから削除した項目を回復する。

一般的に RDB は、サーバー全体を復元する必要がある場合、複数のデータベースを復元する必要がある場合、Active Directory トポロジを変更または再構築する必要のある緊急事態の場合向けには設計されていません。

RDB を作成する手順について詳しくは、「[回復用データベースを作成する](create-a-recovery-database-exchange-2013-help.md)」をご覧ください。RDB を使用する方法について詳しくは、「[回復用データベースを使用してデータを復元する](restore-data-using-a-recovery-database-exchange-2013-help.md)」をご覧ください。

