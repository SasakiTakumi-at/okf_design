# okf_design

## OKF構成案

```text
.
├── README.md #プロジェクトの入口
│
├── docs/ #リポジトリ全体の運用・設計・仕様を管理するエリア
│   ├── AGENTS.md #AIエージェント向け運用ルール
│   ├── INDEX.md #リポジトリ全体のカタログ
│   ├── SPEC.md #OKFの標準仕様
│   ├── ARCHITECTURE.md #リポジトリの構造説明
│   ├── DEVELOPMENT_GUIDE.md #開発ルール
│   ├── GLOSSARY.md　#用語集
│   ├── NAME_RULE.md　#命名規則
│   └── README.md #docsの入口
│
├── instructions/
│   └── LLM / Agentへ与えるカスタム指示・定期整理プロンプト
│
├── okf_repository/ #OKF外部メモリーのリポジトリ
│   ├── README.md/ #okf_repositoryの入口
│   │
│   ├── device_docs/ #ベンダーナレッジ専用領域
│   │   ├── INDEX.md #リポジトリのカタログ
│   │   ├── cisco/ cisco独自のreference
│   │   │   ├── nxos_command_reference.md #AIが参照するnxosのSource of Truth
│   │   │   └── iosxe_command_reference.md #AIが参照するiosxeのSource of Truth
│   │   └── arista/ arista独自のreference
│   │       └── eos_command_reference.md #AIが参照するeosのSource of Truth
│   │
│   ├── template/ #生成物の雛形
│   │   ├── INDEX.md #リポジトリのカタログ
│   │   ├── testcase_template.md #実施されたテスト記録Format
│   │   ├── incident_template.md #発生したインシデント記録Format
│   │   ├── python_template.md #生成するPythonファイルのFormat
│   │   └── robot_template.md #生成するRobotframeworkのFormat
│   │
│   ├── Knowledge_at/ #ATが蓄積していくKnowledge
│   │   ├── INDEX.md #リポジトリのカタログ
│   │   ├── scenario/ #作成したPythonファイルとRobotframeworkファイル
│   │   ├── testcases/ #実施されたテスト記録
│   │   └── incidents/ #発生したインシデント記録
│   │
│   ├── Knowledge/ #一般化して蓄積していくKnowledge
│   │   ├── INDEX.md #リポジトリのカタログ
│   │   ├── workflows/
│   │   └── tools/
│   │
│   └── memory/ # 固有の現在状態・重要な遷移
│       ├── state/ #継続作業で「今どうなっているか」を確認するための文書
│       └── events/ #工程完了、方針変更、重要な検証結果など
│
└── core/ #ネットワーク検証自動化プラットフォーム
    ├── 
```
