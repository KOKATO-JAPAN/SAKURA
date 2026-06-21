# 🎤 音声タスク追加アプリ

スマホで話すだけで、自分のタスクリストにタスクを追加できる個人用ツールです。
外出先など、PCと別のネットワークからでも使えます。

## 仕組み

```
📱 スマホ（このアプリ＝GitHub Pages）
   │ 話す → 文字化 → 受信箱に追記
   ▼
☁️ GitHub: 非公開の受信箱リポジトリ / inbox.json
   │
   ▼ PCが定期的に取り込み
💻 取り込みスクリプト → 手元のタスクリストに反映
```

- **このリポジトリ（公開）** … スマホの画面（`index.html`）だけを置きます。データは保存しません。
- **受信箱（非公開リポジトリ）** … 入力したタスクは、非公開リポジトリ側にのみ保存されます。

## アプリのURL（スマホで開く）

GitHub Pages 公開後、以下で開けます：

```
https://kokato-japan.github.io/SAKURA/
```

スマホのブラウザで開いたら、**「ホーム画面に追加」**しておくとアプリのように使えます。

## 初回設定：GitHubトークン（鍵）の作り方

スマホアプリが受信箱に書き込むための鍵を、一度だけ作ります。

1. GitHub にログイン
2. 次のページを開く → **https://github.com/settings/personal-access-tokens/new**
   （Settings → Developer settings → Personal access tokens → **Fine-grained tokens**）
3. 設定内容：
   - **Token name**: 任意（例：`task-inbox-phone`）
   - **Expiration**: 1年など
   - **Repository access**: 「Only select repositories」→ 受信箱リポジトリだけを選択
   - **Permissions** → Repository permissions → **Contents** を **Read and write**
4. 「Generate token」を押し、表示された `github_pat_...` を**コピー**
   （※この画面を閉じると二度と表示されません）
5. スマホアプリの **⚙️初回設定** を開き、トークンを貼り付けて「この端末に保存」

> 🔒 トークンは受信箱リポジトリ限定なので、万一漏れても他には影響しません。
> トークンはスマホのブラウザ内（localStorage）にのみ保存され、外部に送信されません。

## 使い方

1. アプリを開く
2. **🎤 話す** をタップ → タスク内容を話す
3. 必要ならカテゴリ・日付・時刻・メモを調整
4. **＋ タスクを追加** をタップ
5. PC側が取り込むと、手元のタスクリストに反映されます

※ 音声認識は Android Chrome が最も安定。iPhone Safari で動かない場合は手入力できます。
