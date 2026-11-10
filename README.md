# FiveM 車両ダッシュボード

FiveM（GTA V）の車両を、写真と値段つきのカードで一覧できるダッシュボード。
初期データは空で、みんなが車両を登録して埋めていく形です。登録内容は全員で共有されます。

## 機能
- 車両カード一覧（画像・車名・価格）
- 車名検索、並び替え（新着・価格・名前）
- 車両の登録・編集・削除（画像は登録時に新規アップロード）

## 構成
- `site/` … 静的ページ本体（GitHub Pages 等にそのまま置ける）
- `supabase/schema.sql` … 共有データベース（Supabase）の初期設定SQL

## 全員共有を有効にする手順（1回だけ）
1. https://supabase.com で無料プロジェクトを作成
2. SQL Editor で `supabase/schema.sql` を実行
3. Project Settings > API から Project URL と anon key をコピー
4. `site/config.js` の `SUPABASE_URL` と `SUPABASE_ANON_KEY` に貼る
   - 未設定の間は「ローカル確認モード」（そのブラウザ内だけ保存）で動作確認できます
5. （任意）Database > Replication で `vehicles` の realtime を有効にすると、他人の登録が自動反映されます

## GitHub Pages で公開する手順
1. GitHub でリポジトリを作成し、このフォルダの中身を push
2. リポジトリ Settings > Pages で、公開フォルダに `site/` を含むブランチを選択
3. 発行されたURLをメンバーに共有

## 注意
- schema.sql のポリシーは「誰でも読み書き可」です。小規模な身内コミュニティ向けの設定なので、
  不特定多数に公開する場合は書き込み制限（認証必須など）を追加してください。
