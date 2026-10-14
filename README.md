# OKF_Design
Open Knowledge Format（OKF）を、LLM / Agentが継続利用する外部メモリーの保存・整理形式として活用するための設計・運用上の知見をまとめた資料です。

## Repository Guide
このリポジトリは、目的別に8つの領域へ分けています。

```text
.
├── README.md プロジェクトの入口
│
├── docs/ 
│   └── リポジトリ全体の運用・設計・仕様を管理するエリア
│
├── instructions/
│   └── LLM / Agentへ与えるカスタム指示・定期整理プロンプト
│
├── device_docs/
│   └── 各ベンダー機器Knowledge
│
├── template/ 
│   └── 生成物の雛形
│
├── okf_repos_at/
│   └── AT専用Knowledge
│
├── okf_repos/
│   └── 一般化Knowledge
│
├── memory/
│   └── 固有の現在状態・重要な遷移
│
└── core/
    └── ネットワーク検証自動化プラットフォーム

```
### docs/
OKFをどのように設計し、どのように運用しているかを説明する資料です。

### instructions/
LLM / Agentへ与える運用指示です。

### device_docs/
各ベンダーごとの機器に使用するコマンドリファレンスです。

### template/
作成するPython / Robotframework ファイルと実行した testcase に対する結果/インシデント記録のテンプレートです。

### okf_repos_at/
OKFを使った AT 専用 Git リポジトリの構成例です。

### okf_repos/
OKFを使った一般化用 Git リポジトリの構成例です。

### core/
作成したPython / Robotframework ファイルを実行するためのネットワーク検証自動化プラットフォームです。