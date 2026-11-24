# 手順書.txt
検証PC⇔VDI
■開発環境について
パイプラインを実行せずに、シナリオ動作を確認する方法をご共有します。
 
・前提
platformリポジトリ：「192.168.200.200:9000」 の 「ai-automation-platform」リポジトリ
test_docsリポジトリ：「192.168.200.200:9000」 の 「ai-automation_test_docs」 リポジトリ
open_webui：192.168.200.200:12000
 
①各自作業フォルダに、platformリポジトリと、test_docsリポジトリをクローンしてください。(gitlab webui > 各project > Code > Clone with HTTPから)
②platformリポジトリの「dev」ブランチから、「dev-maruyama」などの各自開発ブランチを作成してください。(以降のシナリオ作成はそちらで)
③各自のplatformローカルリポジトリで、各自の作業ブランチに切り替えてください。
④各自のplatformローカルリポジトリに、以下のリストのファイルをコピーしてください。
　フォルダ：/home/administrator/Desktop/maruyama/work/新設計実装/ai-automation-platform/
　　- kick_dev.py　ファイル
　　- .dev.env　ファイル
⑤各自のplatformローカルリポジトリの、トップレベルフォルダにて、以下のコマンドを実行してください。

---
python3 -m venv .venv
source .venv/bin/activate
python -m pip install pip --upgrade
pip install -r src/core/requirements.txt -r src/main/requirements.txt
---

ここで環境準備は終了です。venvに入っている状態が解除された場合(sshし直しなど)は、再度source .venv ~~~　をしてください。
 
⑥シナリオ実行にあたり、.dev.envの以下の項目を書き換えながら実行してください。
OPEN_WEBUI_CHAT_ID：open_webui画面上「フォルダ」の各自のチャットにて、出ています。「sample_pipe」を再度実行すると再発行されます
OPEN_WEBUI_MESSAGE_ID：open_webui画面上「フォルダ」の各自のチャットにて、出ています。「sample_pipe」を再度実行すると再発行されます
PLAN_FILE_PATH：test_docsリポジトリの、実行計画書のファイルパスを指定します。test_docsはmainブランチで自由に編集してください
 
⑦実行は、

---
# source .venvされている前提
python kick_dev.py

# source .venvしていなくても以下のコマンドで実行可能
.venv/bin/python kick_dev.py
---

コマンドで実行します。
　※RobotのCLI出力は出ないため、生成された証跡を確認して下さい。証跡パスは標準出力に出てきます。
 
⑧.dev.envに設定したchat_id、message_idのチャットの表示が更新されます。
 
 
■作成ユーザーの共有
OMENのGitLab（192.168.200.200:9000）
佐々木
　ユーザー：takumi.sasaki
　メール：takumi.sasaki@gitlab.com

 作業ファイルの被り防止用のファイルを作成しました。
/home/administrator/Desktop/share/Janog59/作業状況.md
