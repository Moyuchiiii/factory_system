# claude-code-workflows サマリー

> リポジトリ: https://github.com/shinpr/claude-code-workflows
> ⭐ 279 | 🍴 47 | 最終更新: 2026-04-05
> 確認日: 2026-04-06

## 概要

Claude Code向けのプロダクション品質の開発ワークフローをプラグイン形式で提供するリポジトリ。要件分析・設計・実装・品質チェックを専門エージェントに分担させる仕組みで、「ただコードを生成する」のではなく「レビュー可能なコードを届ける」ことを目的としている。バックエンド・フロントエンド(React/TypeScript)・フルスタック対応の3プラグイン構成で、Claude Code公式のプラグインマーケットプレイス経由でインストールできる。

## ワークフローパターン一覧

### コアプラグイン

| プラグイン | 対象 | インストールコマンド |
|---|---|---|
| `dev-workflows` | バックエンド / 汎用 | `/plugin install dev-workflows@claude-code-workflows` |
| `dev-workflows-frontend` | React / TypeScript | `/plugin install dev-workflows-frontend@claude-code-workflows` |
| `dev-skills` | スキルのみ（既存WF向け） | `/plugin install dev-skills@claude-code-workflows` |

### オプションアドオン

| プラグイン | 用途 |
|---|---|
| `claude-code-discover` | 機能アイデアをエビデンスベースのPRDに変換 |
| `metronome` | Claudeのショートカット行動を検知して軌道修正 |
| `linear-prism` | 要件 → Linear タスクに変換（品質ゲート付き） |

### レシピコマンド（バックエンド・汎用）

| コマンド | 用途 |
|---|---|
| `/recipe-implement` | 機能の端から端まで実装 |
| `/recipe-task` | 単一タスクの精密実行（バグ修正・小変更） |
| `/recipe-design` | 設計ドキュメント作成 |
| `/recipe-plan` | 設計からワークプラン生成 |
| `/recipe-build` | 既存タスクプランから実行再開 |
| `/recipe-diagnose` | 問題調査・根本原因分析 |
| `/recipe-review` | 設計ドキュメントとのコードレビュー |
| `/recipe-reverse-engineer` | 既存コードからPRD・設計ドキュメントを逆生成 |

### フルスタック

| コマンド | 用途 |
|---|---|
| `/recipe-fullstack-implement` | バックエンド＋フロントエンドを横断した機能実装 |
| `/recipe-fullstack-build` | 既存フルスタックタスクプランから実行 |

## factory での活用方法

| フェーズ | 活用方法 |
|---|---|
| **要件整理** | `/recipe-implement` を叩くだけで `requirement-analyzer` が規模（Small/Medium/Large）を自動判定しワークフローを選択 |
| **設計生成** | `/recipe-design` で PRD → 技術設計ドキュメントを自動生成 |
| **実装** | `task-executor` が TDD スタイルで実装し、`quality-fixer` がテスト失敗・型エラー・Lint を自動修正 |
| **診断** | `/recipe-diagnose` で investigator → verifier → solver の3エージェントパイプラインが根本原因を特定 |
| **レガシー対応** | `/recipe-reverse-engineer` で既存コードからPRD・設計ドキュメントを逆生成 |

## 注目パターン

**規模適応型ワークフロー（requirement-analyzer）**
タスク規模を自動判定して実行パスを切り替える:
- Large（6ファイル以上）→ PRD → コードベース分析 → 技術設計 → テスト生成 → 実装
- Medium（3〜5ファイル）→ コードベース分析 → 技術設計 → 実装
- Small（1〜2ファイル）→ 直接実装

**垂直スライス実行（work-planner）**
フルスタック実装時にレイヤー別ではなく「価値単位の垂直スライス」でスケジューリング。各フェーズで動作する統合済みの状態を保てる。

**ACH + 悪魔の代弁者による診断（verifier）**
分析的階層プロセス（ACH）と Devil's Advocate 手法で仮説を検証。根拠なき修正ミスを防ぐ設計。

## 注意点

- **`dev-skills` と `dev-workflows` の共存禁止**: 同じスキルが重複登録され、Claude Code のスキル説明のコンテキスト上限を超えるとスキルがサイレントに無視される。どちらか一方だけインストールすること
- **フルスタックレシピの前提**: 両プラグインのインストールが必須
- **メンテ状況**: 最終コミットは 2026-04-05 で活発に更新されており、安定して使える状態
- **Codex CLI版あり**: 同じワークフロー設計で OpenAI Codex CLI 向けの `codex-workflows` も存在する
