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
│   │   ├── concepts/ #理解するための知識
│   │   ├── workflows/ #作業手順
│   │   ├── tools/ #実装方法
│   │   ├── references/ #正解ソース
│   │   ├── experiments/ #過去事例
│   │   └── decisions/ #判断理由
│   │
│   └── memory/ # 固有の現在状態・重要な遷移
│       ├── state/ #継続作業で「今どうなっているか」を確認するための文書
│       └── events/ #工程完了、方針変更、重要な検証結果など
│
└── core/ #ネットワーク検証自動化プラットフォーム
    ├── 
```

# okf_design

## OKF構成案（簡略版）

現在の構成は、設計書と実運用の保存領域を分離し、必要最小限の整理で運用する形に整理しています。

```text
.
├── README.md                     # プロジェクトの入口
├── docs/                         # 設計・運用・仕様の共通資料
│   ├── AGENTS.md
│   ├── ARCHITECTURE.md
│   ├── DEVELOPMENT_GUIDE.md
│   ├── GLOSSARY.md
│   ├── INDEX.md
│   ├── NAME_RULE.md
│   ├── README.md
│   └── SPEC.md
├── instructions/                 # AI / Agent 向けの運用指示
│   ├── custom-instructions.md
│   └── memory-consolidation-prompt.md
├── okf_repository/              # 実運用用の OKF 外部メモリー
│   ├── README.md
│   ├── memory/                   # 現在状態と重要な変化
│   │   ├── state/
│   │   │   ├── current-state.md
│   │   │   └── index.md
│   │   └── events/
│   │       ├── important-change.md
│   │       └── index.md
│   ├── knowledge_at/            # シナリオ・テスト・インシデントの実記録
│   │   ├── INDEX.md
│   │   ├── scenario/
│   │   │   └── 生成シナリオ（Robotframework）
│   │   ├── testcases/
│   │   │   └── 実施済みテストケース
│   │   └── incidents/
│   │       └── 発生したインシデント
│   ├── knowledge/                # 汎用化した作業知識
│   │   ├── INDEX.md
│   │   └── workflows/
│   │       └── 01-01-01_interface_recovery_workflow.md
│   ├── device_docs/             # ベンダー別の参照資料
│   │   ├── INDEX.md
│   │   ├── arista/
│   │   │   └── eos_command_reference.md
│   │   └── cisco/
│   │       ├── iosxe_command_reference.md
│   │       └── nxos_command_reference.md
│   └── template/                # 記録・生成物の雛形
│       ├── INDEX.md
│       ├── incident_template.md
│       ├── knowledge_template.md
│       ├── python_template.md
│       ├── robot_template.robot
│       └── testcase_template.md
└── core/                         # 補助的な運用・統合的な説明用領域
    └── README.md
```

## 役割の整理

- `docs/` : OKF の設計思想・運用ルール・仕様
- `instructions/` : AI / Agent が運用時に参照する指示
- `okf_repository/` : 実際に蓄積する知識・記録・現在状態
- `memory/` : 状態と重要イベント
- `knowledge_at/` : 実行したシナリオ・テスト・インシデント
- `knowledge/` : 再利用可能な汎用知識
- `device_docs/` : ベンダー資料の出典保持
- `template/` : 記録テンプレートと生成用雛形

この構成により、設計資料と実運用の情報を分離しつつ、必要最小限の記録を残せます。

---

## 引き継ぎ用: ファイル別の作成説明

以下は、他メンバーに作業を依頼するために、各ドキュメントの役割と作成ポイントをファイル単位で整理した説明です。

### README.md
- 役割: リポジトリ全体の入口。OKF の目的、位置づけ、利用の想定を説明する。
- 作成の狙い: 初見のメンバーが「何を管理するリポジトリか」をすぐ理解できるようにする。
- 記載すべき内容: 目的、対象範囲、構成概要、どこから読むか、運用方針の要点。
- 進行状況: 基本の骨格は整理済み。今後は利用者に合わせた説明文を簡潔に整える。

### docs/README.md
- 役割: 設計資料群の全体像を説明する導入資料。
- 作成の狙い: a) 設計思想の説明 b) 役割分離の説明 c) 参照の優先順を示す。
- 記載すべき内容: 背景、構成、責務、読み順、設計意図。
- 進行状況: 概要は入っているが、プロジェクト固有の背景をもう少し具体化すると良い。

### docs/INDEX.md
- 役割: 設計書の一覧と読み順を管理するインデックス。
- 作成の狙い: どの文書を先に読めばよいかを明確にする。
- 記載すべき内容: 文書名、役割、読む順番、参照先。
- 進行状況: 目次の骨格はできている。必要に応じて文書名や説明文を更新する。

### docs/ARCHITECTURE.md
- 役割: Memory / Knowledge / knowledge_at / device_docs / template などの責務を整理する。
- 作成の狙い: 管理対象の分離ルールを明文化する。
- 記載すべき内容: 保存領域ごとの責務、情報の持ち方、設計意図、運用の基本思想。
- 進行状況: 要件の整理は進んでいる。図や説明をより直感的にする作業が残る。

### docs/DEVELOPMENT_GUIDE.md
- 役割: 実運用における作成・保存・再利用フローを定義する。
- 作成の狙い: シナリオ作成から記録、再利用までの流れを標準化する。
- 記載すべき内容: 作業手順、記録タイミング、Metadata 付与、成功/失敗/障害の区分、知識抽出の方針。
- 進行状況: 実際の運用観点が入っており、最終的にはより短く簡潔な運用ルールにまとめると良い。

### docs/NAME_RULE.md
- 役割: ファイル名やキーワード、Robot の命名規則を統一する。
- 作成の狙い: 検索性と再利用性を上げるために命名を揃える。
- 記載すべき内容: 命名ルール、ケース規約、ファイル名の例、タグ命名、keyword ルール。
- 進行状況: ルールの定義自体は進んでいるため、実際の運用例を追加すると完成度が上がる。

### docs/GLOSSARY.md
- 役割: OKF で使う語彙を統一する。
- 作成の狙い: 「Scenario」「Incident」「Triage Test」などの意味が揺れないようにする。
- 記載すべき内容: 用語一覧、定義、使い分け、例。
- 進行状況: 初期定義は入っている。用語の増加に合わせて更新が必要。

### docs/SPEC.md
- 役割: 記録粒度や保存単位などの設計制約を明示する。
- 作成の狙い: 何を「保存すべき情報」とみなすかの基準を作る。
- 記載すべき内容: 保存粒度、記録単位、情報の抽出範囲、保存・非保存の基準。
- 進行状況: 原則は整理済み。実運用の具体例を増やすと強くなる。

### docs/AGENTS.md
- 役割: LLM / Agent に対する運用指示を定義する。
- 作成の狙い: Agent が外部メモリーを誤った使い方をしないようにする。
- 記載すべき内容: 事実ベースの記録、重要情報の分離、保存先のルール、安全な運用指示。
- 進行状況: 基本ルールはあるので、運用実績に合わせて指示を詳細化すると良い。

### instructions/README.md
- 役割: AI 向けの運用方針の入口。
- 作成の狙い: Agent が参照する指示の全体像を理解させる。
- 記載すべき内容: 目的、対象、読み方、重要ルール。
- 進行状況: 役割の説明は揃っている。

### instructions/INDEX.md
- 役割: 指示ファイルの一覧を管理する。
- 作成の狙い: 指示の用途を見失わないようにする。
- 記載すべき内容: ファイル名、役割、利用タイミング。
- 進行状況: 最小限の一覧は整っている。更新すれば十分に運用可能。

### instructions/memory-consolidation-prompt.md
- 役割: 定期整理やメモリ統合を行うためのプロンプト。
- 作成の狙い: 古い情報や重複情報を整理し、現在状態の正確性を保つ。
- 記載すべき内容: 整理対象、判定基準、統合ルール、出力フォーマット。
- 進行状況: 方向性はあるが、実運用に即した簡潔なテンプレート化が残っている。

### instructions/level-1-custom-instructions.md
- 役割: 初期レベル向けのカスタムルール。
- 作成の狙い: まずは基本ルールを守れる状態を作る。
- 記載すべき内容: 事実ベースの記録、保存先、重要情報の扱い、簡易ルール。
- 進行状況: ベースはできているので、運用例を足すとより使いやすくなる。

### okf_repository/README.md
- 役割: 実運用用のメモリ構成を示す入口。
- 作成の狙い: Memory / Knowledge / knowledge_at / device_docs / template の実例を把握させる。
- 記載すべき内容: 保存先の整理、配下の責務、運用原則。
- 進行状況: 基本構成は整っている。実体の記録例を増やすと理解しやすい。

### okf_repository/memory/README.md
- 役割: 現在状態と重要イベントを管理する領域の入口。
- 作成の狙い: 短時間で現在の状態を参照できるようにする。
- 記載すべき内容: State と Event の違い、保存方針、更新のルール。
- 進行状況: 役割の整理は完了している。

### okf_repository/memory/state/index.md
- 役割: 現在の状態を保持する一覧。
- 作成の狙い: 作業再開時に「今何を扱っているか」をすぐ確認できるようにする。
- 記載すべき内容: 現在の作業、重要な数値、未解決事項、次の作業。
- 進行状況: 形式は整っており、実際の更新例を入れると運用しやすい。

### okf_repository/memory/state/current-state.md
- 役割: 現在状態の実データをまとめたファイル。
- 作成の狙い: 現在の真実の状態を管理し、再開時の基準にする。
- 記載すべき内容: 対象機器、現在構成、確認済み事実、未解決事項、次の行動。
- 進行状況: ここは実データに依存するため、運用開始時に定期更新が必要。

### okf_repository/memory/events/index.md
- 役割: 重要な変化や節目の記録一覧。
- 作成の狙い: 重要な変化を履歴として残す。
- 記載すべき内容: 変更理由、変化の内容、タイミング、影響範囲。
- 進行状況: 形式は定まりつつある。イベント判定の基準を明文化すると良い。

### okf_repository/memory/events/important-change.md
- 役割: 重要な変化の実記録。
- 作成の狙い: 重大な判断変更や状態変化を記録する。
- 記載すべき内容: 変更前後、根拠、影響、次の対応。
- 進行状況: 重要イベントのテンプレートとして使う前提で整備しやすい。

### okf_repository/knowledge/INDEX.md
- 役割: 再利用可能な知識のインデックス。
- 作成の狙い: 汎用化した手順や判断基準を管理する。
- 記載すべき内容: 知識カテゴリ、メタデータ、関連キーワード、保存方針。
- 進行状況: 枠組みは揃っている。実知識の追加が残っている。

### okf_repository/knowledge/workflows/01-01-01_interface_recovery_workflow.md
- 役割: 一般化した復旧手順や再利用可能な作業フローを記録する。
- 作成の狙い: 特定のインシデントを汎用の手順として再利用できるようにする。
- 記載すべき内容: 目的、前提条件、手順、確認ポイント、失敗時の判断。
- 進行状況: 具体例はあるが、手順の汎用性を高める整形が必要。

### okf_repository/knowledge_at/INDEX.md
- 役割: 実行シナリオ・検証結果・インシデントの区分管理。
- 作成の狙い: 環境依存の実例を残し、後で一般化できるようにする。
- 記載すべき内容: scenario / testcases / incidents の役割分担、Metadata ルール。
- 進行状況: 役割の整理は進んでいる。

### okf_repository/knowledge_at/testcases/01-01-01_interface_status_check.md
- 役割: 実施した検証ケースの成功記録。
- 作成の狙い: どの確認手順が正しく動いたかを再利用可能な形で残す。
- 記載すべき内容: 検証目的、前提、手順、結果、判定、関連キーワード。
- 進行状況: ケースの形式が明確なので、実際の実行結果を埋める作業を進める。

### okf_repository/knowledge_at/incidents/01-01-01_interface_down_incident.md
- 役割: 障害や異常の再現条件と原因を記録する。
- 作成の狙い: 再発時に、前回の障害内容と切り分け方法を再利用できるようにする。
- 記載すべき内容: 発生時刻、影響範囲、観測結果、切り分けポイント、最終判断。
- 進行状況: 障害の詳細を整理する作業が残っている。

### okf_repository/device_docs/INDEX.md
- 役割: ベンダー別のコマンド参照が一覧化された入口。
- 作成の狙い: コマンド確認時に機器ごとに素早く参照できるようにする。
- 記載すべき内容: 対象機器、用途、参照ファイル、更新方針。
- 進行状況: 参照先の整理は進んでいる。

### okf_repository/device_docs/arista/eos_command_reference.md
- 役割: Arista EOS の代表的な確認・設定コマンドをまとめる。
- 作成の狙い: ベンダー差異を理解しながら切り分けや確認をできるようにする。
- 記載すべき内容: コマンド、目的、出力の見方、判定基準、注意事項。
- 進行状況: 参照資料として利用可能な状態に近づいている。

### okf_repository/device_docs/cisco/iosxe_command_reference.md
- 役割: Cisco IOS XE 向けのコマンド参照。
- 作成の狙い: IOS XE の確認手順と設定確認を再利用しやすくする。
- 記載すべき内容: 主要な show コマンド、状態確認、リンク切り分け、設定確認。
- 進行状況: 主要コマンドの整理が中心。表現の揃えを続ける。

### okf_repository/device_docs/cisco/nxos_command_reference.md
- 役割: Cisco NX-OS 向けの確認・判断コマンドをまとめる。
- 作成の狙い: NX-OS 独自のコマンド差異を明確にする。
- 記載すべき内容: show コマンド、状態判定、構成確認、注意点。
- 進行状況: 参照の骨格はできており、実運用との照合が残る。

### okf_repository/template/INDEX.md
- 役割: 雛形類の一覧と利用方針を示す。
- 作成の狙い: 記録の形式を統一して、後の検索や再利用を容易にする。
- 記載すべき内容: テンプレート名、用途、使用時期。
- 進行状況: 形式の整理は完了している。

### okf_repository/template/incident_template.md
- 役割: 障害記録の雛形。
- 作成の狙い: 事象・再現条件・影響・切り分け結果などを揃えて記録する。
- 記載すべき内容: 発生条件、観測結果、原因、影響、対応、教訓。
- 進行状況: 基本構造の定義は済んでいるので、具体例を入れると完成度が上がる。

### okf_repository/template/testcase_template.md
- 役割: 検証ケースの雛形。
- 作成の狙い: 成功した検証を再利用しやすい形式に統一する。
- 記載すべき内容: 目的、前提、手順、結果、判定、関連タグ。
- 進行状況: 雛形の骨格は揃っている。

### core/README.md
- 役割: 実装基盤の概要と参照元の説明。
- 作成の狙い: 実装の詳細は別リポジトリに委ねつつ、概要と責務を整理する。
- 記載すべき内容: 基盤の役割、GitLab 参照先、設計と実装の分離。
- 進行状況: 説明の基盤は整っている。今後は要件や構成図が補完されると良い。

## 作成時の共通ルール

- 事実に基づいて記録する。
- 現在状態と再利用知識を分離する。
- 重要ではない生の会話全文は保存しない。
- 実運用で使う情報は Metadata と関連キーワードを付与する。
- 汎用化できる内容は knowledge 側へ整理する。
- Git で履歴を管理し、重要な変更はイベントとして残す。

## 次に進めるべき作業

1. README 系と docs 系の説明文を、対象読者にとって簡潔でわかりやすく整える。
2. 実運用の記録例を `knowledge_at/` と `memory/` に追加する。
3. device_docs 配下の機器別コマンド記録を、実際の観測値と照合しながら埋める。
4. template を実データに合わせて使いやすい形式へ調整する。
5. 変化があった場合は、関連する Index / README へ反映する。

上記の方針に沿って、各ファイルを順次埋めていくことで、他メンバーが継続的に作業を進めやすい状態になります。

---
```

