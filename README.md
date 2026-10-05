# hp-en

## 英語HP自動生成の流れ

1. クライアントがフォームに回答
   → 自動で英語HPが作成される
2. Slackで社内通知が来る
3. クライアントに確認して完了（修正があればClaude Codeで対応、手順は下記「修正対応の手順（Claude Code）」を参照）
4. 移管依頼があれば対応

## このリポジトリの役割

- **メイン**：クライアントからフォームで申し込みがあったら自動でHPを生成し、Slackへ通知する
  - フォームリンク：https://forms.gle/tYcisLbQMpKqvDWr5
- **サブ**：生成したHPをクライアント管理へ移行する際のスキル置き場

## クライアントから移管依頼があった際の手順リンク

- 社内手順書：https://league-jp.github.io/hp-en/docs/domain-migration-guide.html
- クライアント依頼手順書：https://league-jp.github.io/hp-en/docs/client-domain-migration-request.html

## 修正対応の手順（Claude Code）

クライアントから文言・ロゴなどの修正依頼があったとき、Claude Codeを使えば誰でも対応できます。特定の担当者（竹安）に依存しません。

### 事前準備（初回のみ）

1. GitHub（league-jp organization）へのアクセス権があることを確認する
2. ローカルPCにgitをインストールする
3. Claude Codeを使えるようにする
4. gitに自分の名前・メールアドレスを登録する（未設定だとコミット時にエラーになる）
   ```bash
   git config --global user.name "自分の名前"
   git config --global user.email "自分のメールアドレス"
   ```

### 修正対応の流れ

1. Claude Codeを起動し、このリポジトリをclone、またはclone済みのフォルダを開く
   ```bash
   git clone https://github.com/league-jp/hp-en.git
   ```
2. 対象のクライアントのHPファイル（`sites/〇〇.html`）を伝え、どこをどう直したいかをチャットで指示する
   - 例：「`sites/studionika.html` の社名を『STUDIO NIKA, Inc.』から『STUDIO NIKA』に直して」
   - スクリーンショットを貼って「この赤枠の部分を直して」のように伝えるとより正確
   - ロゴ画像を差し替えたい場合は画像ファイルをチャットに添付する
3. Claude Codeが修正し、ブラウザで修正後の見た目を見せてくれるので確認する
   - おかしければ「ここが違う」と伝えて直してもらう
4. 問題なければ「コミットして、pushして」と伝える
   - Claude Codeがgitの変更内容を見せてくれるので、意図した修正だけになっているか確認してから進める
5. 数分後、自動反映される（反映の仕組みはメイン機能の自動生成フローと同じ）

### 困ったとき

- GitHubの権限がない／pushできない場合は、league-jp organizationの管理者にアクセス権を依頼する
- どのファイルがどのクライアントのHPか分からない場合は、Slack通知やGoogleフォームの回答内容からクライアント名・ドメイン名で `sites/` 配下を検索する
