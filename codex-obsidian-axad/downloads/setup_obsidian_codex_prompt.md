# Codexに貼るセットアッププロンプト

私の「第二の脳」としてObsidian Vaultを構築してください。

## 前提

このフォルダにある配布ファイルを使います。

- ads_context_bundle.zip
- create_agents_prompt.md

## やってほしいこと

1. 標準フォルダを作成する
   - 00_Inbox
   - 07_DailyLog
   - 08_MeetingLog
   - 10_Goals
   - 20_Context
   - 30_Projects
   - 40_Knowledge
   - 50_Literature
   - 60_Templates
   - 70_Meetings
   - 80_Outputs

2. テンプレートを作成する
   - Project
   - Meeting_Log
   - Decision_Log
   - Context
   - HTML_Output_Template
   - Knowledge
   - Literature
   - Fleeting
   - System_Spec

   目的:
   - ユーザーが「どこに何を書けばいいか」で迷わないこと
   - Codexがノート作成時に毎回同じ型を使えること
   - 実運用Vaultを完全コピーするのではなく、初期導入で詰まりにくい最小構成にすること

3. AGENTS.mdを作成する
   - create_agents_prompt.md の内容をCodexに貼って作成する
   - 実運用AGENTS.mdから個人要素を除いた配布版として作る
   - 秘密情報、個人情報、キーは書かない

4. 広告コンテキストを配置する
   - ads_context_bundle.zip を展開する
   - 展開された ads_context/ 配下のMarkdownを 20_Context/AXIS/Ads/ に配置する
   - Lecture_01〜Lecture_09 の9ファイルだけが揃っていることを確認する

5. 動作確認する
   - フォルダが揃っているか
   - テンプレートがあるか
   - AGENTS.mdがあるか
   - 20_Context/AXIS/Ads/ に Lecture_01〜Lecture_09 の9ファイルだけが入っているか
   - Codexが次回以降どの入口を参照すればよいか

最後に、作成・配置したものと、次に整えるべきものを一覧で報告してください。
