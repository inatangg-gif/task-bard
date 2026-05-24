# CLAUDE.md

このファイルはClaude Code（claude.ai/code）がこのリポジトリで作業する際のガイダンスを提供します。

## プロジェクト概要

**タスクボード**アプリケーション。タスクの作成・管理・進捗追跡を行うWebアプリです。

## 環境

- **OS**: Windows 11
- **シェル**: bash（Unix構文を使用。`/dev/null`、スラッシュ区切りのパスなど）
- **Node.js**: `node` コマンドで実行
- **Python 3.12**: `python <script>.py` で実行
- パッケージ管理: `npm install` / `pip install`

## Git運用ルール

### 基本方針

コードを変更するたびに必ずGitHubにプッシュしてください。

### 手順

1. 変更をステージングする: `git add <変更したファイル>`
2. コミットする（日本語または英語可）:
   ```bash
   git commit -m "変更内容の簡潔な説明"
   ```
3. GitHubにプッシュする:
   ```bash
   git push origin main
   ```

### コミットメッセージの規則

- `feat:` — 新機能の追加
- `fix:` — バグ修正
- `refactor:` — リファクタリング
- `docs:` — ドキュメント変更
- `test:` — テスト追加・修正
- `chore:` — ビルド設定やツール類の変更

例:
```
feat: タスクの締め切り日設定機能を追加
fix: 完了済みタスクが削除できないバグを修正
```

### 注意事項

- `main` ブランチへの直接プッシュは原則OK（個人プロジェクトのため）
- 大きな機能追加の場合はfeatureブランチを切ることを推奨
- `.env` などの機密情報を含むファイルは絶対にコミットしない
- `.gitignore` に `node_modules/`, `*.env`, `__pycache__/`, `.venv/` を必ず含める

## 技術スタック

| 用途 | 技術 |
|---|---|
| UIライブラリ | React 18 |
| ビルドツール | Vite 5 |
| 言語 | JavaScript (JSX) |
| スタイリング | CSS（単一ファイル `App.css`） |
| 状態管理 | React組み込み `useState` / `useEffect` |
| データ永続化 | `localStorage` |
| パッケージ管理 | npm |

## コンポーネント命名規約

- **ファイル名・コンポーネント名**: PascalCase（例: `App.jsx`, `TaskItem.jsx`）
- **関数・変数**: camelCase（例: `addTask`, `toggleTask`）
- **CSSクラス**: kebab-case（例: `task-item`, `add-button`）
- **localStorageキー**: kebab-case（例: `task-board-tasks`）
- コンポーネントは1ファイル1コンポーネントを基本とする
- コンポーネントファイルは `src/` 直下に配置（規模拡大時は `src/components/` へ移行）

## デプロイ先

- **本番URL**: https://inatangg.github.io/task-board/
- **ホスティング**: GitHub Pages
- **ベースパス**: `/task-board/`（`vite.config.js` の `base` に設定済み）

### デプロイ手順

```bash
npm run build
# dist/ フォルダの内容を gh-pages ブランチにプッシュ
```

または `gh-pages` パッケージを使う場合:

```bash
npm install --save-dev gh-pages
# package.json の scripts に追加:
# "deploy": "gh-pages -d dist"
npm run build && npm run deploy
```

## コーディング規則

- コメントは最小限に。「なぜ」が自明でない場合のみ記述する
- 不要な抽象化・早期最適化は避ける
- セキュリティ: SQLインジェクション、XSS等のOWASP Top 10に注意する

## ディレクトリ構成

```
task-board/
├── CLAUDE.md
├── .gitignore
├── index.html
├── package.json
├── vite.config.js
└── src/
    ├── main.jsx
    ├── App.jsx
    └── App.css
```
