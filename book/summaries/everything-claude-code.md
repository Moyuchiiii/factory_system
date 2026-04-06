# everything-claude-code サマリー

> リポジトリ: https://github.com/affaan-m/everything-claude-code
> ⭐ 141k（※bot inflation の可能性あり、要確認） | 最終更新: 2025年9月以降
> 確認日: 2026-04-06

## 概要

Anthropicハッカソン（2025年9月）の優勝プロジェクト。Claude Codeを使って実プロダクト（zenith.chat）を丸ごとビルドした経験から生まれた「AIエージェントハーネスの性能最適化システム」。スキル180個・エージェント47体・ルール34セット・フック20本超を含み、Claude Code / Cursor / Codex / OpenCode / Gemini を横断して動く。単なる設定ファイル集ではなく、本番運用に耐える完成されたシステムとして設計されている。

## アーキテクチャ

```
ユーザー
  └── Claude Code（オーケストレーター）
        ├── Skills（180+）   ← 主なワークフロー実行単位
        ├── Agents（47体）   ← スコープ限定のサブプロセス
        ├── Rules（34セット） ← 言語・ドメイン別のガイドライン
        ├── Hooks（20本+）   ← ライフサイクルイベント駆動の自動化
        └── MCP Configs      ← 外部サービス接続（DB・デプロイ等）
```

**設計思想**: 「賢さよりも本番での再現性」。スキルを「再利用可能な知識の単位」として扱い、エージェントはスコープを限定して並列実行。コンテキストウィンドウは常に意識的に管理する。

## 主なコンポーネント

### Skills（180個）カテゴリ別

| カテゴリ | 代表スキル |
|---|---|
| AI/エージェント工学 | autonomous-loops, continuous-learning-v2, eval-harness |
| テスト・品質 | tdd-workflow, e2e-testing, security-review, ai-regression-testing |
| 言語別パターン | python-patterns, go-patterns, rust-patterns（12言語対応）|
| インフラ | docker-patterns, deployment-patterns, database-migrations |
| コスト最適化 | cost-aware-llm-pipeline, context-budget, token-budget-advisory |
| リサーチ | deep-research, exa-search, iterative-retrieval, market-research |
| ビジネス | billing-ops, lead-intelligence, cold-email, content-engine |
| セキュリティ | security-scan, secret-scanning, HIPAA-compliance |

### Agents（47体）

- **開発系**: planner, architect, code-reviewer（言語別10体）, build-error-resolver
- **品質系**: e2e-runner, tdd-guide, performance-optimizer, refactor-cleaner
- **分析系**: code-explorer, silent-failure-hunter, conversation-analyzer
- **PM系**: chief-of-staff, loop-operator, harness-optimizer
- **OSS系**: opensource-forker, opensource-packager, opensource-sanitizer

### メモリシステム

- SQLiteベースのステート管理（インストール済みコンポーネント・セッション履歴を追跡）
- `PreCompact`フック：論理的な区切りで手動圧縮を提案（95%での強制圧縮ではなく）
- `continuous-learning-v2`：セッションからパターンを自動抽出→スキル化（信頼度スコアリング付き）

## factory での活用方法

| ステップ | 活用箇所 |
|---|---|
| `/research` | `deep-research` + `exa-search` + `market-research` スキル |
| `/select-repos` | `opensource-forker` / `opensource-packager` エージェント |
| `/plan` | `planner` + `architect` エージェント |
| `/transform` | 言語別 `code-reviewer` + `build-error-resolver` 群 |
| `/optimize` | `cost-aware-llm-pipeline` + `context-budget` + `harness-optimizer` |

## 注目パターン

**1. スキルを「再利用単位」にするアーキテクチャ**
スラッシュコマンドをスキルに置き換えることで、プロンプト・サポートファイル・コードマップを1つにバンドル。エージェントへの委譲時にスキルごと渡せる。

**2. フック駆動の自動ガバナンス**
`PreToolUse` / `PostToolUse` / `UserPromptSubmit` / `Stop` / `PreCompact` の5イベントをフックで制御。承認なし送信防止・クレデンシャル検出・セッション保存を実現。

**3. Git Worktree並列化**
複数Claudeインスタンスが独立ブランチで同時作業。

**4. continuous-learning-v2（自己進化ループ）**
セッション中のパターンを自動抽出→信頼度スコアリング→スキル化。使うほど賢くなるシステム。

**5. エディタ非依存のCLIファースト設計**
`.cursor/`, `.codex/`, `.gemini/`等のディレクトリを並列管理。

## 注意点

- **スター数の読み方**: 141kは本家リポジトリと混同の可能性あり。実際の数値はリポジトリページで要確認
- **メンテ状況**: ハッカソン後（2025年9月以降）のコミット頻度は不明。実験的コンポーネントが含まれる
- **スケール前提**: 47エージェント・180スキルをフル活用する想定設計。小規模案件には過剰
- **MCP依存**: Exa検索・Railwayデプロイ等はMCPサーバー設定が前提
