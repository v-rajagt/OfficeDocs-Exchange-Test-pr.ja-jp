﻿---
title: 'ボイス メール プレビューの拡張機能: Exchange 2013 Help'
TOCTitle: ボイス メール プレビューの拡張機能
ms:assetid: 1fcccec1-4edc-40b8-948c-111647d7d770
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ150501(v=EXCHG.150)
ms:contentKeyID: 48269245
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# ボイス メール プレビューの拡張機能

 

_**適用先:** Exchange Server 2013, Exchange Server 2016_

_**トピックの最終更新日:** 2012-07-05_

ボイス メールのプレビューは、Microsoft Exchange Server 2010 や Exchange Server 2013 ユニファイド メッセージング (UM) でボイス メール メッセージを受信するユーザー向けの機能です。 ボイス メールのプレビューでは、テキスト形式による録音出力により、UM ボイス メールの機能を強化しました。 ボイス メール テキストは、Microsoft Office Outlook Web App、Outlook 2010、その他の電子メール プログラムの電子メール メッセージに表示されます。

## ボイス メールのプレビューの機能拡張

Exchange 2013 では、UM に Outlook Web App や Outlook クライアントのユーザー インターフェイスの拡張機能と強化機能を組み込んで、ボイス メールのプレビューの信頼性と正確性を改善しました。 また、Microsoft Speech Platform (Version 11.0) と Unified Communications Managed API (UCMA) 4.0 によって、一部の音声認識関連サービスを充実し、文法生成と言語サポートを強化しました。

ユニファイド メッセージングでは、Exchange 2010 にボイス メールのプレビュー機能を導入しました。 ボイス メールのプレビューでは、自動音声認識 (ASR) で、音声メッセージにボイス メール オーディオ ファイルのテキスト バージョンを追加します。 ASR は完全に正確というわけではありません。未知の音声やノイズが含まれる電話を通して音声を録音するのに ASR が使用される場合は、特にそうです。

組織によっては、全員とまでは言わないまでも一部のユーザーに、あくまでエラーのない、またはそれに近い状態のボイス メール メッセージのトランスクリプトが求められる場合があります。 ボイス メール プレビュー パートナー プログラムは、そのような組織が要件を満たすのに役立ちます。 ボイス メール パートナー プログラムは、ボイス メールのプレビューでより良い結果を得るために、Exchange 2010 向けに設計したプログラムですが、そのオーバーヘッドとコストのために、Exchange 2010 のユーザーには利用されませんでした。 これらの問題に対処するため、Exchange 2013 では、ボイス メールのプレビューに以下のような機能強化を実施しました。

  - **音声の正規化の強化**   音声の正規化とは、目標値または標準値と一致するピーク振幅が得られるように、音声信号全体の振幅を均一に増加 (または減少) させるプロセスです。 UM は、録音を圧縮してユーザーに送信する前に、録音を正規化します。

  - **音声認識の強化**   ボイス メール メッセージの収集 (Exchange ユーザーがこの情報の共有を選択した場合のみ) により、ボイス メールのプレビューの結果を利用して、音声認識エンジンに単語と文字列を追加できます。 その場合、**Set-UMMailbox** コマンドレットで *VoiceMailAnalysisEnabled* パラメーターを `$true` に設定するか、*AllowVoiceMailAnalysis* パラメーターを **Set-UMMailboxPolicy** コマンドレットで `$true` に設定します。 また、Exchange 2013 UM は、Outlook Voice Access を使用してユーザーが作成した電子メール スレッドからの情報を効率的に使用します。 これらの情報には、国、市町村、会社などの参加者 (Active Directory や個人用の連絡先) の情報や Outlook Voice Access ユーザーの電話番号などが含まれます。

  - **ボイス メールのプレビューの信頼度**   信頼度のスコアは、ユニファイド メッセージングに割り当てられた数字であり、トランスクリプション全体の精度に直接関係があります。 UM で使用する信頼度の計算は、高い精度が得られるように調節されており、変換したメッセージの実際の精度を表します。

  - **フィルタリング**   不適切な単語を検出してフィルター処理し、ユーザーのメールボックスにこれらの結果をキャッシュして保存します。

  - **テキスト プレビューの非表示**   ボイス メールのプレビューの信頼度スコアが指定したしきい値を下回る場合、ボイス メールのプレビュー テキストは非表示になります。 テキストが非表示の場合、ボイス メールの信頼度が結果を表示する基準に達しないことを示すテキストがボイス メール メッセージに添付されます。

  - **トランスクリプション パフォーマンス**   ボイス メールのプレビューは CPU に大きな負荷がかかり、その処理にはオーディオ ファイルの約 2 倍の時間がかかります。 ボイス メールのプレビュー テキストの生成に時間がかかりすぎる場合は、CPU の調整によりプレビューの処理が停止しています。 Exchange 2010 では、UM は 75 秒を超えるすべてのボイス メッセージを変換しませんでした。 Exchange 2013 では、ボイス メッセージ全体を変換しますが、75 秒を超えるとメッセージのテキストが含まれません。

  - **配色**   ボイス メールのプレビューの信頼度の高、中、低を区別するための色が混乱していたため、Outlook Web App と Outlook の Exchange 2013 の配色は削除しました。
