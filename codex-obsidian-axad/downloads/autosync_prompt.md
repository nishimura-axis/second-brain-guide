Obsidian Vault のGitHub同期を10分ごとに自動実行する設定を作ってください。

前提:
- このVaultはGitHubと連携済みです
- GitHubはCodexのGitHubプラグインで接続済みです
- 自動同期はローカル端末上で動く仕組みにしてください
- 10分ごとに pull → 変更確認 → commit → push を行う想定です
- 認証情報やトークンはファイルに書かないでください
- .env やキー類は絶対に同期対象にしないでください

やってほしいこと:

1. 現在のVaultがGit管理されているか確認する
   - git status -sb
   - git remote -v
   - git branch --show-current

2. .gitignore を確認・必要なら更新する

最低限以下を除外してください。

.DS_Store
.obsidian/workspace.json
.obsidian/workspace-mobile.json
.env
.env.*
*.key
*token*
sa-key.json
*.pem

3. 自動同期スクリプトを作成する

まず保存先フォルダを作成してください。

mkdir -p 05_CommandCenter/scripts 05_CommandCenter/logs

保存先:
05_CommandCenter/scripts/obsidian_git_autosync.sh

仕様:
- Vaultルートで実行されること
- スクリプトの先頭でVaultルートへ移動すること
- まず git pull --rebase --autostash を実行
- コンフリクトが起きたら停止し、ログに記録する
- 変更がなければ何もしない
- 変更があれば git add -A
- git diff --cached をログに残す
- コミットメッセージは以下にする

auto-sync: update vault notes

- pushする
- 実行結果をログに残す
- スクリプト作成後に chmod +x で実行権限を付ける

ログ保存先:
05_CommandCenter/logs/obsidian_git_autosync.log

4. 10分ごとに実行する設定を作成する

macOSの場合は launchd を使ってください。

plist保存先:
~/Library/LaunchAgents/com.obsidian.vault.autosync.plist

設定:
- 10分ごとに実行
- 標準出力・標準エラーはログに追記
- 実行対象は作成した obsidian_git_autosync.sh

5. launchdに登録する

以下を実行してください。

launchctl unload ~/Library/LaunchAgents/com.obsidian.vault.autosync.plist 2>/dev/null || true
launchctl load ~/Library/LaunchAgents/com.obsidian.vault.autosync.plist
launchctl start com.obsidian.vault.autosync

6. 動作確認する

以下を確認してください。

launchctl list | grep obsidian.vault.autosync
tail -n 50 05_CommandCenter/logs/obsidian_git_autosync.log

7. 完了後に報告する

以下を報告してください。

- 作成したスクリプト
- 作成したplist
- launchd登録状況
- 最初の実行ログ
- GitHub pushが成功したか
- コンフリクト時の挙動
- 解除方法
- 05_CommandCenter/scripts と 05_CommandCenter/logs を作成済みか

注意:
- 認証情報をファイルに書かない
- コンフリクトが起きたら自動解決しない
- .env やキー類をstageしない
- 初回実行前に git status -sb を見せる
- 不明点があれば勝手に進めず確認する
