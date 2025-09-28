# Next.js + Material-UI ミニマルテンプレート

このプロジェクトは [Next.js](https://nextjs.org) と Material-UI を組み合わせたミニマルなテンプレートです。

## 特徴

- **Next.js 15** - App Router + Turbopack
- **Material-UI v7** - Emotion スタイリング + Next.js 統合
- **TypeScript** - 型安全性
- **Biome** - 高速リンター・フォーマッター
- **Lefthook** - Git フック自動化
- **pnpm** - パッケージマネージャー

## 開発開始

開発サーバーを起動:

```bash
pnpm dev
```

ブラウザで [http://localhost:3000](http://localhost:3000) を開いて結果を確認してください。

`src/app/page.tsx` を編集してページをカスタマイズできます。ファイル保存時に自動的に更新されます。

## 主要コマンド

### 開発
```bash
pnpm dev          # 開発サーバー起動
pnpm build        # プロダクションビルド
pnpm start        # プロダクションサーバー起動
```

### コード品質
```bash
pnpm check        # リント・フォーマットチェック
pnpm check:fix    # 自動修正（安全・非安全）
pnpm format:fix   # フォーマット修正のみ
pnpm typecheck    # TypeScript型チェック
```

## Git ワークフロー

Lefthook により以下が自動実行されます:
- **コミット前**: コードスタイル自動修正
- **プッシュ前**: コード品質検証 + 型チェック

## 技術スタック

- [Next.js](https://nextjs.org/docs) - React フレームワーク
- [Material-UI](https://mui.com/) - React UI コンポーネント
- [TypeScript](https://www.typescriptlang.org/) - 型安全な JavaScript
- [Biome](https://biomejs.dev/) - 高速ツールチェーン


