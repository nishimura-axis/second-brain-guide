Obsidian Vault と GitHub を連携してください。

前提:
- GitHubはCodexのGitHubプラグインで接続済みです
- GitHubの認証トークンをユーザーに入力させる前提にはしないでください
- トークンや認証情報をAGENTS.md、Vault内ノート、共有資料に書かないでください
- Obsidian VaultをGitHubでバックアップ・同期できるようにする作業です
- リポジトリは private で作成・運用してください
- この資料の手順に沿って、Codexで実行してください
- この後の10分同期はObsidian Gitプラグインで設定します

まず以下を確認してください。

1. 現在の作業ディレクトリがObsidian Vaultルートか
2. .git が存在するか
3. 既存のremoteが設定されているか
4. 未コミット変更があるか
5. AGENTS.md、60_Templates、20_Contextなどがあるか
6. .gitignore があるか

## まだGit管理されていない場合

以下を実行してください。

1. git init
2. .gitignore を作成
3. 機密情報が含まれないように除外設定
4. 初回コミット
5. CodexのGitHubプラグインを使って private repository を作成
6. 作成されたrepositoryをremoteに設定
7. main ブランチとしてpush

.gitignore には最低限以下を含めてください。

.DS_Store
.obsidian/workspace.json
.obsidian/workspace-mobile.json
.env
.env.*
*.key
*token*
sa-key.json
*.pem

## すでにGit管理されている場合

以下を確認してください。

1. git status -sb
2. git remote -v
3. git branch --show-current
4. git log --oneline -5

remoteが未設定なら、CodexのGitHubプラグインで private repository を作成し、remoteを設定してください。
remoteが設定済みなら、現在の状態を説明し、必要ならpushしてください。

## GitHub連携時のルール

- repository name は MyVault を基本にする
- 公開設定は必ず private
- 初回セットアップのみ main に初期コミットしてよい
- 認証情報、APIキー、トークン、個人情報が含まれていないか確認する
- stage後に必ず git diff --cached を確認する
- push前に .gitignore が効いているか確認する
- GitHub操作はCodex GitHubプラグインを優先する
- GitHub CLIやトークン手入力は、プラグインで対応できない場合だけ検討する
- 認証が必要な場面では、勝手にトークン入力を求めず、プラグイン接続状態を確認する

## 初回コミットメッセージ

Initialize Obsidian second brain vault

## 完了後に報告してほしいこと

最後に以下を報告してください。

1. Git管理の状態
2. GitHub repository URL
3. remote URL
4. 現在のブランチ
5. push済みかどうか
6. .gitignore に含めた内容
7. 機密情報チェック結果
8. 次にやるべきこと
9. Obsidian Gitプラグインで同期設定へ進める状態か

不明点、private repository作成、push、外部公開範囲に関わる操作は、必要に応じて確認してから進めてください。
