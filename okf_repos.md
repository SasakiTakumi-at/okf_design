# ai_automation_repos_design

## リポジトリ構成

```text
.
├── ai-automation_platfrom/         # 自動化機能領域
│   └── src/                       # ソースコードと実行基盤の集約先
│       ├── core/                  # 共通基盤・ロボット依存の中心
│       │   └── robot/
│       │       └── libs/          # Robot / Library 共通のライブラリ群
│       ├── main/                  # 実行の入口となるメイン処理
│       └── user/                  # 顧客が作成するカスタム領域
│           └── generate/          # 自動化生成したシナリオやライブラリの一時保存領域
│               ├── robot/         # 自動化生成した Robot ファイルの一時保存先
│               ├── python/        # 自動化生成した Python ファイルの一時保存先
│               └── reports/       # 実装判断・設計レビューの一時レポート保存先
│
├── ai-automation_test_docs/       # ユーザー操作・編集領域
│   ├── profile/                   # ユーザーまたは自動化生成したプロファイル
│   ├── test_plan/                 # ユーザーまたは自動化生成した実行計画書
│   └── procedure/                 # ユーザーが作成したテスト手順書
│
├── ai-automation_okf/              # OpenKnowledgeFormat 領域
│   ├── README.md                  # OKF の入口
│   ├── docs/                      # 設計・運用・仕様の共通資料
│   │   ├── README.md
│   │   ├── INDEX.md
│   │   ├── AGENTS.md
│   │   ├── ARCHITECTURE.md
│   │   ├── DEVELOPMENT_GUIDE.md
│   │   ├── GLOSSARY.md
│   │   ├── NAME_RULE.md
│   │   └── SPEC.md
│   ├── instructions/              # AI / Agent 向けの運用指示
│   │   ├── README.md
│   │   ├── level-1-custom-instructions.md
│   │   └── memory-consolidation-prompt.md
│   ├── generator/          # コード生成関連の実装・補助
│   └── okf_repository/            # 実運用用の OKF 外部メモリー
│       ├── README.md
│       ├── memory/                # 現在状態と重要な変化
│       │   ├── README.md
│       │   ├── events/
│       │   │   ├── README.md
│       │   │   └── important-change.md
│       │   └── state/
│       │       ├── README.md
│       │       └── current-state.md
│       ├── knowledge_at/          # シナリオ・補助実装・テスト・インシデントの実記録
│       │   ├── INDEX.md
│       │   ├── incidents/
│       │   │   └── (Robot シナリオ実行中に発生した事象記録)
│       │   ├── robot/
│       │   │   └── (実行した Robot シナリオ)
│       │   ├── python/
│       │   │   └── (ライブラリ / Keyword 実装)
│       │   └── testcases/
│       │       └── (実行したテスト記録)
│       ├── knowledge/             # 汎用化した作業知識
│       │   ├── INDEX.md
│       │   └── workflows/
│       │       └── 01-01-01_interface_recovery_workflow.md
│       ├── device_docs/           # ベンダー別の参照資料
│       │   ├── INDEX.md
│       │   ├── arista/
│       │   │   └── eos_command_reference.md
│       │   └── cisco/
│       │       ├── iosxe_command_reference.md
│       │       └── nxos_command_reference.md
│       └── template/              # 記録・生成物の雛形
│           ├── INDEX.md
│           ├── incident_template.md
│           ├── robot_template.robot
│           ├── testcase_template.md
│           └── README.md
│
└── ai-automation_harness/          # 実行支援ハーネス領域
    ├── main.py                     # エントリポイント（run_workflow）
    ├── general.yml                 # 共通設定
    ├── .secret.yml                 # API キー（Git 管理外）
    ├── agents/                     # エージェント定義とプロンプト
    │   ├── agent_builder.py
    │   ├── router/
    │   ├── normal_chat/
    │   ├── info/
    │   ├── test_plan_path_finder/
    │   ├── test_plan_gate/
    │   └── test_plan_builder/
    ├── tools/                      # ツール定義の窓口とローカルツール
    │   ├── tool_registry.py
    │   ├── mcpo_tool_loader.py
    │   └── local/
    ├── utils/                      # 設定・Git・ログ・Open WebUI連携
    │   ├── settings_loader.py
    │   ├── git_repository.py
    │   ├── checkpoint_cleanup.py
    │   ├── open_webui_client.py
    │   └── logger.py
    ├── workflow/                   # ワークフロー本体
    │   ├── graph.py
    │   ├── nodes.py
    │   ├── edges.py
    │   ├── state.py
    │   ├── context.py
    │   ├── schemas/
    │   ├── info_workflow/
    │   └── test_workflow/
    └── README.md                  # ハーネスの概要と起動方式
```
