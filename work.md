# 手順書_シナリオ自動生成テスト用(パケロス閾値特定試験).txt
検証PC⇔VDI
---
プロジェクト名:シナリオ自動生成テスト
対象機能:UDP通信確認
大項目番号:1
大項目名:性能試験
中項目番号:
中項目名:
小項目番号:
小項目名:
OKF：障害切り分け
---
## 検証目的
　パケットロス発生時の帯域変更試験。パケットロスが発生する帯域閾値を特定する

## 検証観点
　二分探索を用いてトラフィック送信帯域を決定していき、パケットロス発生帯域を特定する
　
## 試験構成
　Janog58デモ構成
　
## 試験手順
　検索手順
　　1.パケットロスが発生した帯域を初期値とする
　　2.パケットロス発生有無に応じて二分探索を用いて帯域を調整する
　　3.パケットロスが発生した帯域を上限値、ロスが発生しなかった帯域を下限値として記録する
　　4.上限値と下限値の中間値で下記の試験手順を実施する
　　5.終了条件を満たすまで繰り返す
　　6.ロス発生閾値を記録する
　
　終了条件
　　上限値と下限値の差が10Mbps以下となった場合

　試験手順
　　1.router1にSSHログイン
　　2.show running-configを取得
　　3.clear conters GigabitEthernet0/4 を実行
　　4.show interface GigabitEthernet0/4 を取得し、実行前情報として保存
　　5.show process cpu を定期取得開始
　　6.show process resources を定期取得開始
　　7.router1からログアウト
　　8.サーバ側測定器 にログイン
　　9.iperfサーバを起動
　　10.クライアント側測定器にログイン
　　11.指定された試験帯域でiperfを実行
　　12.結果を取得
　　13.show purocess cpu,show purocess resourcesの取得を終了
　　14.show interface GigabitEthernet0/4を取得
　　15.Lost/Totalからパケットロス率を算出する
　　16.パケットロス率が5%未満の場合は「ロスなし」と判定する
　　17.パケットロス率が5%以上の場合は「ロスあり」と判定する
　　18.iperf実行前後のshow interface GigabitEthernet0/4を比較する
　　19.output packets が増加していることを確認する
　　20.判定結果を探索手順へ返却する

## 判定基準
   判定方式:固定値判定
   判定条件:
    - パケットロス率が5%未満であること

## 取得する証跡
　show runnning-config
　clear conters GigabitEthernet0/4
　show interface GigabitEthernet0/4
　クライアント側測定器のiperf実行結果

　### 定期取得
　コマンド: show purocess cpu を1秒間隔で取得
　取得間隔: 1秒
　取得期間: 試験開始から終了まで

　### 定期取得
　コマンド: show purocess resources を1秒間隔で取得
　取得間隔: 1秒
　取得期間: 試験開始から終了まで
　
