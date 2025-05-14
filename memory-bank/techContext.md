# 技術コンテキスト

## 使用技術

Headshot AI は、最新のウェブ開発技術とクラウドサービスを組み合わせて構築されています。以下は、プロジェクトで使用されている主要な技術とライブラリです。

### フロントエンド

- **Next.js**: React ベースのフレームワークで、サーバーサイドレンダリング、静的サイト生成、API ルートを提供
- **React**: ユーザーインターフェースを構築するための JavaScript ライブラリ
- **TypeScript**: 静的型付けを提供する JavaScript のスーパーセット
- **Tailwind CSS**: ユーティリティファーストの CSS フレームワーク
- **Shadcn UI**: Radix UI と Tailwind CSS に基づくコンポーネントライブラリ
- **React Hook Form**: フォーム処理のための React ライブラリ
- **Zod**: TypeScript ファーストのスキーマ検証ライブラリ

### バックエンド

- **Next.js API Routes**: サーバーレス関数として機能する API エンドポイント
- **Supabase**: PostgreSQL データベースと認証サービスを提供するバックエンドプラットフォーム
- **Vercel Blob**: ファイルストレージソリューション
- **Astria.ai API**: AI モデルトレーニングと推論のための外部 API
- **Stripe API**: 支払い処理のための API
- **Resend**: メール送信のための API（オプション）

### インフラストラクチャ

- **Vercel**: ホスティングとデプロイメントプラットフォーム
- **Supabase**: データベースとユーザー認証のホスティング

## 開発環境セットアップ

### 前提条件

- Node.js (バージョン 18.x 以上)
- npm または yarn パッケージマネージャー
- Git

### ローカル開発環境のセットアップ

1. リポジトリのクローン:

   ```bash
   git clone https://github.com/your-repo-name/headshots-starter.git
   cd headshots-starter
   ```

2. 依存関係のインストール:

   ```bash
   npm install
   # または
   yarn
   ```

3. 環境変数の設定:
   `.env.local.example` ファイルを `.env.local` にコピーし、必要な環境変数を設定します。

4. 開発サーバーの起動:

   ```bash
   npm run dev
   # または
   yarn dev
   ```

5. ブラウザで `http://localhost:3000` にアクセスして、アプリケーションを表示します。

## 技術的制約

### パフォーマンス

- **AI モデルトレーニング**: Astria.ai API でのモデルトレーニングには数分かかる場合があります。
- **画像生成**: 画像生成プロセスも時間がかかる場合があり、ユーザーエクスペリエンスを考慮する必要があります。

### セキュリティ

- **API キー**: Astria.ai API キー、Stripe シークレットキーなどの機密情報は、環境変数として安全に保存し、クライアントサイドに公開しないようにする必要があります。
- **ユーザーデータ**: アップロードされた画像やユーザー情報は、適切に保護する必要があります。

### スケーラビリティ

- **Webhook 処理**: 多数の同時リクエストがある場合、Webhook 処理が課題になる可能性があります。
- **画像ストレージ**: 多数のユーザーがいる場合、画像ストレージのコストと管理が課題になる可能性があります。

## 依存関係

### 主要な npm パッケージ

```json
{
  "dependencies": {
    "@hookform/resolvers": "^3.3.1",
    "@radix-ui/react-*": "各種 Radix UI コンポーネント",
    "@supabase/auth-helpers-nextjs": "^0.9.0",
    "@supabase/supabase-js": "^2.40.0",
    "@vercel/analytics": "^1.2.2",
    "@vercel/blob": "^0.22.1",
    "axios": "^1.6.8",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.0.0",
    "lucide-react": "^0.274.0",
    "next": "^14.1.4",
    "next-themes": "^0.4.6",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-dropzone": "^14.2.3",
    "react-hook-form": "^7.46.1",
    "resend": "^3.2.0",
    "stripe": "^13.6.0",
    "tailwindcss": "3.3.2",
    "zod": "^3.22.2"
  }
}
```

### 外部サービスの依存関係

1. **Astria.ai API**: AI モデルトレーニングと推論のために必要

   - API キーが必要
   - Webhook エンドポイントの設定が必要

2. **Supabase**: 認証とデータベースのために必要

   - プロジェクト ID とシークレットキーが必要
   - 適切なテーブルとポリシーの設定が必要

3. **Stripe**: 支払い処理のために必要（オプション）

   - API キーとウェブフックシークレットが必要
   - 製品とプライスの設定が必要

4. **Resend**: メール通知のために必要（オプション）

   - API キーが必要

5. **Vercel Blob**: 画像ストレージのために必要
   - Blob ストアの作成と API キーが必要

## ツール使用パターン

### 開発ツール

- **TypeScript**: 型安全性を確保するために使用
- **ESLint**: コード品質を維持するために使用
- **Prettier**: コードフォーマットを統一するために使用
- **Vercel CLI**: デプロイメントとプレビューのために使用

### デプロイメントフロー

1. GitHub リポジトリへのコードのプッシュ
2. Vercel による自動ビルドとデプロイメント
3. 環境変数の設定と外部サービスの連携

### 環境変数管理

アプリケーションは以下の環境変数に依存しています：

```
# Astria.ai
ASTRIA_API_KEY=your_api_key
APP_WEBHOOK_SECRET=your-webhook-secret
DEPLOYMENT_URL=your-deployment-url

# Supabase
NEXT_PUBLIC_SUPABASE_URL=your-supabase-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-supabase-anon-key
SUPABASE_SERVICE_ROLE_KEY=your-supabase-service-role-key

# Vercel Blob
BLOB_READ_WRITE_TOKEN=your-blob-read-write-token

# Resend (オプション)
RESEND_API_KEY=your-resend-api-key

# Stripe (オプション)
STRIPE_SECRET_KEY=your-stripe-secret-key
STRIPE_WEBHOOK_SECRET=your-stripe-webhook-secret
STRIPE_PRICE_ID_ONE_CREDIT=your-stripe-price-id-one-credit
STRIPE_PRICE_ID_THREE_CREDITS=your-stripe-price-id-three-credit
STRIPE_PRICE_ID_FIVE_CREDITS=your-stripe-price-id-five-credit
NEXT_PUBLIC_STRIPE_IS_ENABLED=true/false

# Astria Packs (オプション)
NEXT_PUBLIC_TUNE_TYPE=packs
PACK_QUERY_TYPE=both
```

## データベーススキーマ

Supabase には以下のテーブルが含まれています：

1. **credits**: ユーザーのクレジット残高を追跡
2. **images**: 生成された画像の情報を保存
3. **models**: トレーニングされた AI モデルの情報を保存
4. **samples**: モデルトレーニングに使用されたサンプル画像の情報を保存

各テーブルには適切な RLS（Row Level Security）ポリシーが設定されており、ユーザーは自分のデータのみにアクセスできます。
