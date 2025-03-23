# Stel メッセージアプリ デプロイ手順

このドキュメントでは、Stelメッセージアプリを GitHub と Vercel にデプロイする手順を説明します。

## 前提条件

デプロイを行うには、以下のアカウントが必要です：

1. **GitHub アカウント**: [GitHub サインアップ](https://github.com/signup)
2. **Vercel アカウント**: [Vercel サインアップ](https://vercel.com/signup)
3. **Ably アカウント**: [Ably サインアップ](https://ably.com/signup)（リアルタイムメッセージング用）

## 1. Ably API キーの取得

1. [Ably ダッシュボード](https://ably.com/accounts/any)にアクセスします
2. 「Create new app」をクリックします
3. アプリに名前を付けます（例：「stel」）
4. アプリが作成されたら、プライベート API キーをコピーします
   - このキーは後で Vercel の環境変数として使用するため、安全に保管してください

## 2. GitHub へのデプロイ

### リポジトリの作成

1. [GitHub](https://github.com) にログインします
2. 右上の「+」アイコンをクリックし、「New repository」を選択します
3. リポジトリ名を「stel」と入力します
4. 「Public」または「Private」を選択します（お好みで）
5. 「Create repository」をクリックします

### コードのアップロード

GitHub リポジトリを作成したら、以下のコマンドを使用してコードをアップロードします：

```bash
# ZIPファイルを解凍したディレクトリに移動
cd stel

# Gitリポジトリを初期化
git init

# すべてのファイルをステージング
git add .

# 最初のコミットを作成
git commit -m "Initial commit"

# リモートリポジトリを追加（URLは自分のGitHubリポジトリに置き換えてください）
git remote add origin https://github.com/あなたのユーザー名/stel.git

# コードをプッシュ
git push -u origin main
```

## 3. Vercel へのデプロイ

1. [Vercel](https://vercel.com) にログインします
2. 「Add New...」→「Project」をクリックします
3. 「Import Git Repository」セクションで、先ほど作成した「stel」リポジトリを選択します
4. プロジェクト名は自動的に「stel」となりますが、必要に応じて変更できます
5. 「Environment Variables」セクションで、以下の環境変数を追加します：
   - 名前: `ABLY_API_KEY`
   - 値: 先ほどコピーした Ably の API キー
6. 「Deploy」ボタンをクリックします

デプロイが完了すると、Vercel は自動的にアプリの URL を生成します（例：https://stel.vercel.app）。
この URL からアプリにアクセスできます。

## 4. 更新の反映方法

アプリを更新する場合は、ローカルで変更を加えた後、以下のコマンドを実行します：

```bash
git add .
git commit -m "更新内容の説明"
git push
```

GitHub にプッシュすると、Vercel は自動的に新しいバージョンをデプロイします。

## トラブルシューティング

- **デプロイエラー**: Vercel のデプロイログを確認して、エラーの原因を特定してください
- **アプリが動作しない**: 環境変数 `ABLY_API_KEY` が正しく設定されているか確認してください
- **リアルタイムメッセージングの問題**: Ably ダッシュボードでアプリのステータスを確認してください

## 注意事項

- Ably の無料プランには制限があります。大規模な利用を予定している場合は、有料プランへのアップグレードを検討してください
- API キーは公開しないでください。環境変数として安全に管理してください
