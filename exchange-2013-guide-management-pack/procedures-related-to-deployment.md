﻿---
title: 展開に関連した手順
TOCTitle: 展開に関連した手順
ms:assetid: 6b7682bd-fe3d-43b9-a7db-66c0ac17656f
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn195909(v=EXCHG.150)
ms:contentKeyID: 53181894
ms.date: 04/03/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# 展開に関連した手順

 

_**トピックの最終更新日:**  2013-04-17_

このセクションでは、Exchange Server 2013 管理パックをインポートする場合の参考用として使用可能な手順について説明します。展開後の処理に関連した手順については、「[Procedures related to post-deployment operation](procedures-related-to-post-deployment-operation.md)」を参照してください。

## エージェントの展開状態を確認する

Exchange Server 2013 管理パックをインポートする前に、Exchange サーバー上の SCOM エージェントが使用可能になっており、オペレーティング システムの正常性が SCOM に正しく報告されていることを確認します。

この手順を実行するには、使用するユーザー アカウントを Operations Manager 管理者役割のメンバーにする必要があります。

1.  SCOM サーバーにログオンして、SCOM コンソールを開きます。

2.  **\[監視\]** をクリックしてから、**\[Windows コンピューター\]** をクリックします。

3.  すべての Exchange サーバーが **\[正常\]** と表示されていることを確認します。

![SCOM コンソールの正常なエージェント](images/Dn195909.7d1ff0bb-419e-40dc-babf-5fa2fb7229a8(EXCHG.150).png "SCOM コンソールの正常なエージェント")

## エージェントのプロキシ構成を確認する

Exchange Server 2013 管理パックをインポートする前に、エージェント プロキシが SCOM での検索に対して有効になっていることを確認します。有効になっていない場合、Exchange サーバー上のエージェントは Exchange の正常性状態を報告しません。すべての Exchange サーバーに対してこの構成を確認する必要があります。

この手順を実行するには、使用するユーザー アカウントを Operations Manager 管理者役割のメンバーにする必要があります。

1.  SCOM サーバーにログオンして、SCOM コンソールを開きます。

2.  オペレーション コンソールで **\[管理\]** をクリックします。

3.  **\[エージェントで管理\]** をクリックし、Exchange サーバーを右クリックしてから、**\[プロパティ\]** を選択します。

4.  **\[セキュリティ\]** タブで **\[このエージェントをプロキシとして動作させ、他のコンピューター上の管理オブジェクトを検出する\]** チェック ボックスがオンになっていることを確認します。

5.  **\[OK\]** をクリックします。

## エージェントのセキュリティ構成を確認する

Exchange 2013 をテストするセキュリティ モデルでは、**LocalSystem** 以外のアカウントでの Exchange サーバー上の SCOM エージェント実行はサポートされていません。LocalSystem 以外のアカウントでエージェントを実行すると、代理トランザクションが実行できません。その他の問題が発生する可能性もあります。

この手順を実行するには、使用するユーザー アカウントを "Server Management/サーバーの管理" 役割グループのメンバーにする必要があります。

1.  Exchange サーバーにログオンします。

2.  **\[スタート\]** \> **\[管理ツール\]** \> **\[サービス\]** の順にクリックします。

3.  サービスの一覧を下にスクロールして **\[System Center 管理\]** サービスを探します。

4.  **\[ログオン方法\]** 列に **\[ローカル システム\]** と表示されていることを確認します。

5.  **\[ログオン方法\]** 列にこれ以外の値が表示されている場合は、サービス ログオンをローカル システムに変更します。
    
    1.  **\[System Center 管理\]** サービスを右クリックして、**\[プロパティ\]** を選択します。
    
    2.  **\[ログオン\]** タブを選択します。
    
    3.  **\[ローカル システム アカウント\]** オプションをクリックします。
    
    4.  **\[OK\]** をクリックします。

