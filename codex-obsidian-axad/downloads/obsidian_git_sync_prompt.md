Obsidian Gitプラグインで、Obsidian VaultをGitHubへ10分ごとに同期できる状態にしてください。

目的:
- 初めてCodex / Obsidian / GitHubを設定する人でも、難しいスクリプトなしで同期できるようにする
- 難しいローカル自動化設定は使わない
- Obsidian内のCommunity plugin「Obsidian Git」を使う

前提:
- Obsidianはインストール済みです
- Vaultは作成済みです
- VaultはGitHubのprivate repositoryと連携済みです
- 認証情報やトークンはAGENTS.md、Vault内ノート、共有資料に書かないでください
- .env やキー類は絶対に同期対象にしないでください

やってほしいこと:

1. 現在の状態を確認する
   - VaultがObsidianで開けるか
   - GitHub private repository があるか
   - Vaultルートで git status -sb が通るか
   - git remote -v でGitHub repositoryが設定されているか
   - .gitignore があるか

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

3. Obsidian Gitプラグインを入れる

Obsidian上で以下を案内してください。

1. Settings を開く
2. Community plugins を開く
3. Restricted mode をオフにする
4. Browse を押す
5. Obsidian Git を検索する
6. Install を押す
7. Enable を押す

4. Obsidian Gitの同期設定をする

Obsidian Gitの設定画面で、以下を設定してください。

- Auto pull interval: 10
- Auto backup interval: 10
- Auto Backup after stopping file edits: 有効
- Pull updates on startup: 有効
- Push on backup: 有効
- Commit message: auto-sync: update vault notes

設定名が画面上で少し違う場合は、同じ意味の項目を探してください。

5. 手動テストをする

ObsidianのCommand paletteから以下を試してください。

1. Obsidian Git: Pull
2. Obsidian Git: Create backup
3. Obsidian Git: Push

その後、GitHub上で最新commitが増えているか確認してください。

6. 10分同期の確認をする

軽いテスト用メモを1つ作り、10分以内にGitHubへ反映されるか確認してください。

テスト用メモ例:
00_Inbox/Obsidian_Git_Test.md

確認後、不要なら削除して構いません。

7. 完了後に報告する

以下を報告してください。

- Obsidian Gitプラグインをインストール・有効化できたか
- GitHub private repository URL
- Auto pull / Auto backup の設定値
- 手動Pull / Create backup / Push の結果
- 10分以内にGitHubへ反映されたか
- .gitignore の内容
- 機密情報チェック結果
- 詰まった場合の原因候補

注意:
- 難しいローカル自動化設定は使わない
- 認証情報をファイルに書かない
- コンフリクトが起きたら自動解決しない
- .env やキー類をstageしない
- 不明点があれば勝手に進めず確認する
