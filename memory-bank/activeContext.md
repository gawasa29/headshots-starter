# アクティブコンテキスト

## 現在の作業フォーカス

現在、Headshot AI プロジェクトは初期セットアップ段階にあります。メモリバンクを初期化し、プロジェクトの基本的な理解と構造を文書化しています。

## 最近の変更

1. メモリバンクディレクトリの作成
2. 基本的なプロジェクト文書の作成:
   - `projectbrief.md`: プロジェクトの概要と目的
   - `productContext.md`: 製品の背景と解決する問題
   - `systemPatterns.md`: システムアーキテクチャとデザインパターン
   - `techContext.md`: 使用技術と開発環境

## 次のステップ

1. **環境設定の確認**: 必要な環境変数とサービス連携の確認
2. **ローカル開発環境のセットアップ**: 依存関係のインストールと開発サーバーの起動
3. **基本機能の確認**:
   - ユーザー認証フロー
   - モデルトレーニングフロー
   - ヘッドショット生成フロー
   - 支払いフロー（オプション）
4. **コードベースの詳細調査**: 主要コンポーネントとファイルの詳細な分析
5. **改善点の特定**: パフォーマンス、UX、コード品質の観点からの改善点の特定

## アクティブな決定と考慮事項

### アーキテクチャの決定

1. **サーバーレスアプローチ**: Next.js と Vercel を使用したサーバーレスアーキテクチャを採用
2. **マネージドサービスの活用**: Supabase、Vercel Blob などのマネージドサービスを活用して開発効率を向上
3. **Webhook パターン**: 非同期処理のための Webhook パターンの採用

### 技術的な考慮事項

1. **AI モデルの品質**: 高品質な結果を得るためのベストプラクティスの実装
2. **パフォーマンス最適化**: モデルトレーニングと画像生成の待ち時間を考慮した UX の最適化
3. **セキュリティ**: API キーの保護とユーザーデータのセキュリティ確保

### ユーザーエクスペリエンスの考慮事項

1. **シンプルなインターフェース**: 技術的な知識がなくても使いやすい UI/UX の設計
2. **フィードバックループ**: 長時間実行されるプロセス（モデルトレーニングなど）の進行状況の可視化
3. **結果の品質**: 高品質なヘッドショットを生成するためのガイダンスの提供

## 重要なパターンと設計方針

1. **コンポーネントベースの設計**: 再利用可能なコンポーネントに UI を分割
2. **型安全性**: TypeScript と Zod を使用した型安全なコードベース
3. **API ルートパターン**: 外部サービスとの通信を処理するための API ルート
4. **クレジットベースのシステム**: ユーザーアクションに対するクレジット消費モデル

## 学びとプロジェクトの洞察

1. **AI モデルトレーニングのベストプラクティス**:

   - 顔のクローズアップを使用
   - フレーム内に一人だけの人物を含める
   - サングラスや帽子などのアクセサリーを避ける
   - 顔が明確に見えるようにする

2. **結果の品質向上のためのヒント**:

   - サンプル画像は同じアスペクト比（1:1）を使用
   - 複数の人物を含むサンプルを避ける
   - 生成時にネガティブプロンプトを使用（例: "double torso, totem pole"）
   - サンプルと同じアスペクト比で生成

3. **拡張可能性**:

   - AI アバター
   - ペットのポートレート
   - 製品写真
   - 食品写真
   - アイコン
   - スタイル一貫性のあるアセット

4. **技術スタックの選択理由**:
   - Next.js: サーバーサイドレンダリングと API ルートの統合
   - Supabase: 認証とデータベースの簡素化
   - Vercel: デプロイメントとホスティングの簡素化
   - Tailwind CSS と Shadcn: 効率的な UI 開発
