# English Sentences

iPhoneで英語例文を音声再生しながら学習するためのシンプルなWebアプリ。HTMLファイル1個で完結。

## 機能

- 例文一覧の表示
- 各例文の音声再生(英語ネイティブ音声)
- 例文の追加・削除(localStorageに保存)
- 音声(voice)の選択(Samantha, Aaron, Daniel など)
- JSON エクスポート / インポート

## セットアップ

### 1. GitHub Pages にデプロイ

1. このリポジトリを GitHub 上に作成
2. `english_sentences.html` をアップロード
3. `Settings` → `Pages` → Source を `main` ブランチに設定
4. 数分後、以下のURLでアクセス可能になる:
   ```
   https://<username>.github.io/<repo-name>/english_sentences.html
   ```

### 2. iPhone でホーム画面に追加

1. Safari で上記URLを開く
2. 共有ボタン → 「ホーム画面に追加」
3. アイコンタップで起動するようになる

### 3. 英語音声のダウンロード(重要)

iOS で自然な英語音声を使うために、事前にダウンロードしておく:

`設定` → `アクセシビリティ` → `読み上げコンテンツ` → `声` → `英語`

→ `Samantha`(米)や `Daniel`(英)などをDL。「拡張」版を選ぶと品質が大きく上がる。

## 使い方

- **再生**: 例文左の ▶ ボタンをタップ
- **追加**: 画面下の入力欄に英文を打って `Add`
- **削除**: 例文右の ✕ ボタン
- **音声切り替え**: 上部の Voice セレクタ
- **Export JSON**: 現在の例文リストをJSON形式でクリップボードにコピー
- **Import JSON**: JSON配列を貼り付けて一括インポート(現在のリストは置き換えられる)
- **Reset**: デフォルトの3例文に戻す

## データ保存について

例文は **ブラウザの localStorage に保存** される。つまり:

- 追加した例文はそのデバイスのSafariにのみ残る
- Safari のキャッシュをクリアすると消える
- 他のデバイスとは同期しない

定期的に `Export JSON` でバックアップを取ることを推奨。バックアップしたJSONはこのリポジトリにcommitしておけば永続化できる。

## 技術スタック

- HTML / CSS / JavaScript(フレームワーク不使用)
- Web Speech API(`SpeechSynthesis`)
- localStorage

## iOS Safari の注意点

- 音声再生はユーザー操作(タップ)起点でのみ動作する(自動再生不可)
- `speechSynthesis.getVoices()` は初回呼び出し時に空配列を返すことがあるため、ポーリングで対応している
- `utter.lang` だけ指定しても無視されることがあるため、必ず `utter.voice` を明示的にセットしている

## ライセンス

個人利用のためのプロジェクト。