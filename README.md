# 大隈さんぽ(フロントエンド)

本レポジトリは、大隈さんぽのフロントエンドコードを共有しています。**Next.js + TypeScript + Tailwind CSS + Storybook** をベースに構築されており、  
開発効率や品質を維持するために、**ESLint + Prettier + Husky** などのツールが導入されています。  

---

## 必要要件

以下のツールがローカルマシンにインストールされていることを確認してください。

- **Node.js**: 推奨バージョンは LTS（例: `v20.x` 系）
- **npm** または **yarn**: このリポジトリでは npm を想定   
  特に指定がない場合は `npm` を使用してください。

---

## 初期セットアップ手順

1. **リポジトリのクローン**:
   ```bash
   git clone https://github.com/ユーザー名/okumasampo-front.git
   cd okumasampo-front

2. **依存関係のインストール**:
     ```bash
    npm install

3. **ローカルでの起動**
    ```bash
    npm run dev

## ディレクトリ構成

```
.
├─ .husky/               # HuskyによるGitフック関連
├─ .storybook/           # Storybook用の設定ファイル・アドオン設定
├─ public/               # 公開用静的ファイル(画像やフォントなど)
├─ src/                  # アプリケーションのソースコード
│  ├─ app/               # Next.js App Router関連のディレクトリ
│  │  ├─ api/            # Next.js API Routes
│  │  ├─ page.tsx        # アプリケーションのルートページ
│  │  ├─ layout.tsx      # 共通レイアウト定義
│  │  └─ globals.css     # グローバルスタイル
│  ├─ components/        # Reactコンポーネント
│  ├─ hooks/             # カスタムフック
│  ├─ stories/           # Storybook用のストーリーファイル
│  └─ utils/             # ヘルパー関数・ユーティリティ
├─ .eslintrc.js          # ESLintの設定ファイル
├─ .prettierrc           # Prettierの設定ファイル
├─ next.config.ts         # Next.jsの設定ファイル
├─ tailwind.config.ts     # Tailwind CSSの設定ファイル
├─ postcss.config.mjs     # PostCSSの設定ファイル
├─ tsconfig.json          # TypeScriptコンパイラオプション
└─ package.json
```

## 状態管理
**Jotai**
状態管理をシンプルに行うための React 用状態管理ライブラリである。
Jotai は軽量かつ宣言的なアトム (atom) を用いて状態を定義し、React コンポーネントと容易に共有することができる(FltuterのRiverpodに近い)。
また、Jotai は Redux のような大規模な設定を必要とせず、必要な箇所に必要な状態を提供する柔軟な状態管理が可能である。
このプロジェクトでは、Jotai を用いてコンポーネント間で状態を共有・更新し、スケーラブルかつ可読性の高い状態管理を実現する。


## 開発フローの一例
開発フローの一例
1. `git pull` で最新を取得。
2. 新たなブランチを切って (`git checkout -b feature/新機能`) 作業開始。
3. `npm run dev` でローカルサーバーを起動しながらコーディング。
4. コンポーネント作成時は `npm run storybook` でStorybookを起動し、コンポーネント単位で確認。
5. `git add . → git commit` (この際Huskyが自動でlintやformatを実行)
6. `git push` してプルリクエストを作成し、レビュー後にマージ。

## よくある問題と対処法
依存パッケージが不足している場合:
`npm install` の再実行で解決することが多い。

ESLintエラーが解消しない場合:
`npm run lint` および `npm run format` を実行し、指示された箇所を修正する(これは基本的にはコミット時に自動で行われる操作)。 それでも改善しない場合は、能瀬か小野に相談。

Storybookが起動しない場合:
Nodeバージョンや依存関係を確認し、`npm install` の再実行、その後 `npm run storybook`を試す。

