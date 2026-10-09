# okf_design

## OKF構成案

```text
.
├── README.md プロジェクトの入口
│
├── docs/ リポジトリ全体の運用・設計・仕様を管理するエリア
│   ├── AGENTS.md AIエージェント向け運用ルール
│   ├── INDEX.md リポジトリ全体のカタログ
│   ├── SPEC.md OKFの標準仕様
│   ├── ARCHITECTURE.md リポジトリの構造説明
│   ├── DEVELOPMENT_GUIDE.md 開発ルール
│   ├── LOG.md 変更履歴
│   └── README.md docsの入口
│
├── device_docs/ ベンダーナレッジ専用領域
│   ├── cisco/ cisco独自のreference
│   │   ├── nxos_command_reference.md AIが参照するnxosのSource of Truth
│   │   └── iosxe_command_reference.md AIが参照するiosxeのSource of Truth
│   └── Arista/ arista独自のreference
│       └── eos_command_reference.md AIが参照するeosのSource of Truth
│
├── template/ 生成物の雛形
│   ├── testcase_template.md 実施されたテスト記録Format
│   ├── incident_template.md 発生したインシデント記録Format
│   ├── python_template.md 生成するPythonファイルのFormat
│   └── robot_template.md 生成するRobotframeworkのFormat
│
├── at_Knowledge/ ATが蓄積していく固有のKnowledge
│   ├── workflows/
│   ├── tools/
│   ├── references/
│   ├── experiments/
│   └── decisions/
│
├── customer_Knowledge/ 顧客が蓄積していく固有のKnowledge
│   ├── workflows/
│   ├── tools/
│   ├── references/
│   ├── experiments/
│   └── decisions/
│
├── memory/       # 固有の現在状態・重要な遷移
│   ├── state/
│   └── events/
│
└── core
    ├──
    ├──  
```
