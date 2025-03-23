# Stel - リアルタイムメッセージアプリ

Live example at: <https://next-js-chat-app.vercel.app>

このアプリケーションは[Next.js](https://nextjs.org/)と[Ably](https://ably.com)を使用したリアルタイムメッセージアプリです。

## 機能

- リアルタイムメッセージング
- Ablyのリアクトフック
- Ablyによるトークン認証

## 技術スタック

このプロジェクトは以下のコンポーネントを使用しています：

- [Next.js](https://nextjs.org/) - Vercelが提供するReactフレームワーク。サーバーサイドレンダリング、サーバーレス関数、シームレスなホスティングを備えた静的Webアプリケーションの構築に使用されます。
- [Ably](https://ably.com/) - リアルタイム、パブ/サブメッセージングプラットフォーム。
- [Vercel](https://vercel.com/) - Next.jsアプリとサーバーレス関数をホストするために構築されたホスティングプラットフォーム。
- [React](https://reactjs.org/) - ユーザーインターフェースを構築するためのJavaScriptライブラリ。

## ローカルでの構築と実行

### 前提条件

このアプリを構築してデプロイするには、以下が必要です：

- **Ablyアカウント** メッセージ送信用: [Ablyで無料アカウントを作成](https://ably.com/signup)
- **Vercelアカウント** 本番環境でのホスティング用: [Vercelで無料アカウントを作成](https://vercel.com/signup)
- **Node 16** 以上: [Nodeをインストール](https://nodejs.org/en/)

Ablyサービスで認証するにはAblyのAPIキーも必要です。APIキーを取得するには、[Ablyアカウントを作成](https://ably.com/signup)した後：

1. [アプリダッシュボード](https://ably.com/accounts/any)にアクセスし、「Create new app」をクリックします。
2. 新しいアプリに名前を付けます。
3. アプリが作成されたら、プライベートAPIキーをコピーします。これはAblyサービスでの認証に使用するため、安全に保管してください。

### プロジェクトの構築

1. このプロジェクトをローカルで実行するには、プロジェクトのルートに`.env`ファイルを作成し、AblyのAPIキーを含めます：

```sh
ABLY_API_KEY=your-ably-api-key:goes-here
```

2. `npm install`を実行します。
3. `npm run dev`を実行します。

Next.js開発サーバーが起動し、デモチャットアプリケーションが表示されます。

## Vercelでのホスティング

開発サーバーとビルドパイプラインとして`Vercel`を使用しています。

> Next.jsを本番環境にデプロイする最も簡単な方法は、Next.jsの作成者によるVercelプラットフォームを使用することです。Vercelは、静的およびJamstackデプロイメントとサーバーレス関数をサポートするグローバルCDNを備えたオールインワンプラットフォームです。
<cite>-- [Next.jsのドキュメント](https://nextjs.org/docs/deployment)</cive>

新しいチャットアプリをVercelにデプロイするには：

1. [GitHubアカウント](https://github.com/)を作成します（まだ持っていない場合）
2. [アプリをGitHubリポジトリにプッシュ](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository)します
3. [Vercelアカウントを作成](https://vercel.com/signup)します
4. 新しいVercelアプリを作成し、GitHubリポジトリからアプリをインポートします（VercelがGitHubアカウントを使用することを承認する必要があります）
5. 環境変数として`ABLY_API_KEY`を追加します
6. アプリのデプロイを待ちます
7. ブラウザで新しく作成されたURLにアクセスします！

## カスタマイズの可能性

このデモは以下のような方法で拡張できます：

### メッセージ履歴の追加

現在、このデモにはチャット履歴がなく、チャットに参加した後に届くメッセージのみが表示されます。[Ablyの巻き戻し機能](https://ably.com/docs/storage-history/history)を使用して、無料で最大2分間の履歴を、または有料アカウントで最大約48時間の履歴を追加できます。

### ユーザー名の追加

チャットメッセージにはユーザー名が送信されていません。このデモを拡張して、ユーザー名入力ボックスを導入し、送信されるメッセージに現在のユーザー名を追加することができます。

デモでは、ランダムに生成されたAblyクライアントIDを一意の識別子として使用しています - これにより、メッセージを送信したのが「自分」か「他の誰か」かを検出できます。

---
