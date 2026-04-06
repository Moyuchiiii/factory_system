# portable-claude-config サマリー

> リポジトリ: https://github.com/vinicius91carvalho/.claude
> ⭐ 51 | 🍴 6 | 最終更新: 2026-03-12
> 確認日: 2026-04-06

## 概要

Claude Code の設定・ルール・エージェント・フックをポータブルにまとめた個人用AI開発システム。`~/.claude/` に配置することで全プロジェクトに自動適用される。「Compound Engineering」という哲学に基づき、作業のたびにシステム自体を学習・改善するフィードバックループを内蔵している。MITライセンス。

## ファイル構成

```
~/.claude/
├── CLAUDE.md                         # コアルール・判断プロトコル・作業モード定義
├── settings.json                     # フック強制設定（PreToolUse/PostToolUse）
├── agents/
│   ├── orchestrator.md               # バッチ実行エンジン（戦略ではなく手順に従う）
│   ├── sprint-executor.md            # 実装担当（worktree隔離）
│   └── code-reviewer.md             # 読み取り専用の監査役
├── skills/
│   ├── plan/SKILL.md                 # PRD生成・スプリント計画
│   ├── create-project/SKILL.md      # グリーンフィールドプロジェクトのセットアップ
│   ├── plan-build-test/SKILL.md     # ローカル実装パイプライン
│   ├── ship-test-ensure/SKILL.md    # デプロイパイプライン
│   ├── compound/SKILL.md            # タスク完了後の学習キャプチャ
│   ├── workflow-audit/SKILL.md      # システム自己レビュー
│   ├── research/SKILL.md            # 調査スキル
│   └── playwright-stealth/SKILL.md  # ブラウザ自動化
├── hooks/                            # 決定論的（bash）安全強制（19本）
│   ├── block-dangerous.sh           # 破壊的コマンドのブロック
│   ├── check-test-exists.sh         # TDDゲート
│   ├── check-invariants.sh          # アーキテクチャルール検証
│   ├── compound-reminder.sh         # 学習キャプチャの強制
│   ├── verify-completion.sh         # 完了詐称防止
│   └── ...他14本
├── docs/
│   ├── project-claude-md-template.md # プロジェクト別CLAUDE.mdテンプレート
│   ├── anti-patterns-full.md        # アンチパターン集
│   └── verification-gates.md        # 品質ゲート定義
└── test-workflow-mods/              # フック自体のテストスイート（266アサーション）
```

## 主なルール・エージェント・スキル

### エージェント（3体）

| 名前 | 役割 | ポリシー |
|---|---|---|
| orchestrator | バッチ実行エンジン。progress.jsonを読み→次バッチ特定→sprint-executorを起動→結果統合 | 戦略判断なし。決定論的チェックリストのみ |
| sprint-executor | worktree隔離環境での実装担当 | スプリントスペックのみ受け取り実行 |
| code-reviewer | 監査役 | 読み取り専用。実装不可 |

### スキル（9本）

- **compound**: タスク完了後の学習キャプチャ。ユーザーの修正を最高品質のシグナルとして扱い、session-learnings → docs → CLAUDE.md へ昇格させる
- **plan**: PRD生成→スプリント分割
- **plan-build-test**: TDDで実装（テスト先→実装→統合→E2E）
- **ship-test-ensure**: ステージングへの自動デプロイ。本番は人間承認必須
- **workflow-audit**: 月次のシステム自己レビュー

### フック（決定論的強制、19本）

- **block-dangerous.sh**: `rm -rf /` 等をハードブロック
- **check-test-exists.sh**: テストファイルなしのプロダクションコード変更をExit 2でブロック。16言語対応
- **compound-reminder.sh**: セッション終了時に学習キャプチャ未実施なら停止（compoundをブロッキング化）
- **verify-completion.sh**: 完了申告前に実際の検証証拠提示を強制
- **check-invariants.sh**: INVARIANTS.mdで定義したアーキテクチャルール違反を検出

## factory での活用方法

**1. CLAUDE.mdテンプレートの採用**
`docs/project-claude-md-template.md` を `/transform` 生成時のCLAUDE.mdひな型として使う。

**2. エージェント分業パターンの参照**
orchestrator（調整）→ sprint-executor（実装）→ code-reviewer（監査）の3体分業は factory の大規模案件での並列実行設計に応用可能。特に「orchestratorは戦略判断しない、チェックリストのみ実行」の原則は factory の roles.md と整合する。

**3. Compound（自己改善ループ）の導入検討**
`skills/compound/SKILL.md` の「ユーザー修正を最高シグナルとして扱い構造的に記録する」仕組みは、現在の `lessons.md` 運用をより自動化するヒントになる。

**4. INVARIANTS.mdパターン**
プロジェクトごとに `INVARIANTS.md` でアーキテクチャ不変条件を定義し、フックで自動検証するパターンは受注プロジェクトの品質保証に使える。

## 注目パターン

**Probabilistic vs. Deterministic の二重強制**
CLAUDE.mdでの「確率的ルール」（モデルへの指示）とhookでの「決定論的強制」（bashスクリプト）を明確に分ける。「モデルが守るべきもの」と「物理的に実行を止めるもの」を分離した設計。

**Compound Engineering ループ**
Plan → Work → Review → Compound の4サイクルで、作業のたびにシステム自体を改善する。`compound-reminder.sh` でセッション終了をブロックするアプローチは強制力が高い。

**フック自体にテストスイートを持つ**
`test-workflow-mods/` にフック自体の266アサーションテストがある。インフラコードもTDDで管理する徹底した姿勢。

## 注意点

- **最終更新 2026-03-12** — Claudeのアップデートでフックやプロンプトが追従していない可能性あり
- **`evolution/session-postmortems/` が空** — 学習データの蓄積はユーザー自身が運用する必要がある
- **フック依存がbash前提** — Windowsネイティブ環境では動作確認が必要（WSL2またはGit Bashを想定）
- **playwright-stealth設定が含まれる** — ブラウザ自動化のフィンガープリント回避設定なので、利用規約確認が必要な場面がある
