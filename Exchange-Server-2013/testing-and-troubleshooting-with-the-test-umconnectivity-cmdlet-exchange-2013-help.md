﻿---
title: 'Test-UMConnectivity コマンドレットのテストとトラブルシューティング: Exchange 2013 Help'
TOCTitle: Test-UMConnectivity コマンドレットのテストとトラブルシューティング
ms:assetid: 08e67a99-e37f-4afd-bd58-455b62580af7
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Aa995978(v=EXCHG.150)
ms:contentKeyID: 56270036
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Test-UMConnectivity コマンドレットのテストとトラブルシューティング

 

_**適用先:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**トピックの最終更新日:** 2013-06-25_

クライアント アクセスおよびメールボックス サーバーをインストールしてユニファイド メッセージングを構成した後、テレフォニー接続およびユニファイド メッセージング サービスの動作についての複数の診断テストおよびソフトウェアベースの電話アプリケーションを使用することができます。

## Test-UMConnectivity

**Test-UMConnectivity** コマンドレットを使用すると、このコマンドレットで使用されているパラメーターに応じて、クライアント アクセスおよびメールボックス サーバーへの接続をいくつかの方法で確認できます。ユニファイド メッセージングの機能のテストには、次の 3 つがあります。

  - **ローカル** **Test-UMConnectivity** コマンドレットは、同じローカル コンピューター上で実行されているメールボックス サーバーとのボイス オーバー IP (VoIP) 通信を検証します。

  - **TUIlogin を使用したローカル** **Test-UMConnectivity** コマンドレットは、同じコンピューター上で実行されているメールボックス サーバーとの VoIP 通信の確立を試行します。接続された場合は、メールボックスの内線番号と PIN を送信することによって、UM が有効になっている 1 つ以上のメールボックスへのサインインを試行します。*–TUILogon* パラメーターを指定した場合は、テスト メールボックスの適切な情報と併せて、以下のパラメーター値も指定する必要があります。
    
      - *–Phone*   このパラメーターには、テスト メールボックスの内線番号を含める必要があります。
    
      - *–PIN*   このパラメーターには、UM が有効になっているメールボックスの PIN を含める必要があります。
    
      - *–UMDialPlan   * このパラメーターには、テスト メールボックスに関連付けられているダイヤル プランを含める必要があります。

  - **リモート** **Test-UMConnectivity** コマンドレットは、VoIP ゲートウェイ経由で電話をかけることによってリモートのクライアント アクセス サーバーへの接続を試行します。接続された後、リモートのクライアント アクセス サーバーとメディア パスに対する接続確認を実行します。
    

    > [!NOTE]
    > 次のメッセージが表示されたら、MicrosoftExchange ユニファイド メッセージング サービスが停止しているか、応答していないため、このサービスを再起動する必要があります。"Test-UMConnectivity タスクで、呼び出しを行っているときにエラーが発生しました。詳細 :接続を確立できません。"

