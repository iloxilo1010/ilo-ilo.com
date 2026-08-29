# ilo-ilo.com 公開手順書

このフォルダには、構造設計事務所「ilo」のWebサイト一式が入っています。
GitHub Pagesを使えば**無料**でこのサイトを公開できます。以下の手順に沿って進めてください。

---

## 同梱ファイル

| ファイル | 内容 |
|---|---|
| `index.html` | トップページ（会社概要・事業内容・お問い合わせ） |
| `works.html` | 作品紹介ページ（実績一覧） |
| `style.css` | デザイン（シンプル・ミニマル） |
| `script.js` | スマホ用メニューの開閉、フッター年号の自動更新 |
| `CNAME` | 独自ドメイン（ilo-ilo.com）をGitHub Pagesに紐付けるための設定ファイル |

`index.html`・`works.html` 内で `【要差し替え】` と書かれている箇所は、実際の会社情報・プロジェクト事例に差し替えてください。

---

## 手順1：GitHubアカウントを作成する

1. https://github.com/ にアクセス
2. 「Sign up」からメールアドレス・パスワード・ユーザー名を登録（無料）
3. メール認証を完了する

---

## 手順2：リポジトリを作成する

1. GitHubにログイン後、右上の「+」→「New repository」
2. Repository name に `ilo-ilo.com`（何でも構いません）と入力
3. 「Public」を選択（GitHub Pagesの無料利用にはPublicが必要）
4. 「Create repository」をクリック

---

## 手順3：ファイルをアップロードする

1. 作成したリポジトリのページで「Add file」→「Upload files」
2. このフォルダ内の `index.html`・`works.html`・`style.css`・`script.js`・`CNAME` の5ファイルをドラッグ＆ドロップ
3. 下部の「Commit changes」をクリックしてアップロードを確定

---

## 手順4：GitHub Pagesを有効化する

1. リポジトリの「Settings」タブを開く
2. 左メニューの「Pages」を選択
3. 「Build and deployment」→「Source」で `Deploy from a branch` を選択
4. 「Branch」で `main`（または `master`）と `/(root)` を選択して「Save」
5. 数分待つと、`https://ユーザー名.github.io/ilo-ilo.com/` のようなURLでサイトが公開されます

ここまでで、無料の仮URLでの公開は完了です。

---

## 手順5：独自ドメイン（ilo-ilo.com）を紐付ける

すでに `CNAME` ファイル（中身は `ilo-ilo.com` の1行のみ）をアップロード済みなので、GitHub側の設定はほぼ完了しています。あとはドメインを購入した側（お名前.com、Google Domains、Cloudflareなど）でDNSレコードを設定します。

### ルートドメイン（ilo-ilo.com）を使う場合
ドメイン管理画面で、以下の **Aレコード** を4つ登録してください（GitHub Pages公式のIPアドレス）。

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

### www.ilo-ilo.com も使いたい場合
以下の **CNAMEレコード** を追加してください。

```
www → ユーザー名.github.io
```

### 設定後の確認
1. DNSの反映には数分〜数時間かかることがあります
2. GitHubリポジトリの「Settings」→「Pages」で、Custom domainに `ilo-ilo.com` と入力し「Save」
3. 反映されると「Enforce HTTPS」にチェックが入れられるようになるので、必ずチェックを入れる（無料でSSL化されます）

これで `https://ilo-ilo.com` でサイトが表示されるようになります。

---

## お問い合わせフォームについて

GitHub Pagesは静的サイトのみ対応のため、フォーム送信の裏側の処理（メール送信など）はできません。以下のどちらかの無料サービスを組み合わせてください。

### 案A：Googleフォーム（簡単・おすすめ）
1. https://forms.google.com でフォームを作成（会社名、氏名、メールアドレス、お問い合わせ内容など）
2. 右上の「送信」→「埋め込み `<>`」タブでiframeのコードをコピー
3. `index.html` 内の以下の部分を、コピーしたiframeの `src` の値に差し替える

```html
<iframe src="https://docs.google.com/forms/d/e/【要差し替え：GoogleフォームのフォームID】/viewform?embedded=true" ...>
```

回答はGoogleフォームの「回答」タブ、またはスプレッドシートに自動集計されます。

### 案B：Formspree（フォームのデザインを維持したい場合）
1. https://formspree.io で無料アカウントを作成
2. 発行されたエンドポイントURLを、`<form>` タグの `action` に設定
3. 送信内容が登録したメールアドレスに届きます

---

## 公開後にファイルを更新する方法（例：作品紹介ページの追加など）

すでにGitHub Pagesで公開済みのリポジトリにファイルを追加・更新する場合は、次の手順で反映できます。

1. GitHubでリポジトリのページを開く
2. 新しいファイル（例：`works.html`）を追加する場合は、これまでと同様に「Add file」→「Upload files」でドラッグ＆ドロップして「Commit changes」
3. 既存のファイル（例：更新した `index.html` や `style.css`）を上書きする場合も同じく「Add file」→「Upload files」で同名のファイルをドラッグ＆ドロップすると、自動的に上書き保存されます
4. コミット後、1〜数分程度で `https://ilo-ilo.com` に反映されます（すぐに反映されない場合はブラウザのキャッシュを一度クリアしてみてください）

毎回ファイルを1つずつ操作しなくても、複数ファイルをまとめてドラッグ＆ドロップして一度に「Commit changes」することも可能です。

---

## 補足：今後サーバーを契約する場合

将来的にレンタルサーバーを契約する場合も、このHTML/CSS/JSファイル一式はそのままアップロードして使えます（静的サイトなのでどのサーバーでも動作します）。ドメインのDNS設定を新しいサーバーのIP/CNAMEに向け直すだけで移行できます。
