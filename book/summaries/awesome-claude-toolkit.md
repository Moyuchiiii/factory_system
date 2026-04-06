# awesome-claude-code-toolkit サマリー

> リポジトリ: https://github.com/rohitg00/awesome-claude-code-toolkit
> ⭐ 1,097 | 🍴 300 | 最終更新: 2026-04-02
> 確認日: 2026-04-06

## 概要

Claude Code 向けの包括的なツールキット集。135のエージェント、35のキュレーション済みスキル（SkillKit経由で400,000以上）、42のコマンド、150+のプラグイン、19のフック、15のルール、7つのテンプレート、8つのMCP設定などを収録している。Claude Codeを使った開発ワークフローをプロダクションレベルに引き上げるためのリソースをワンストップで提供するリポジトリ。

## 主なカテゴリ

### Plugins（150+）

プラグインマーケットプレイス形式で配布。コマンド `/plugin marketplace add <repo>` で導入可能。

- **pro-workflow**（⭐1,400+）: 自己修正メモリ・並列worktree・8種フック・5エージェントを含む実戦的ワークフロー集
- **everything-claude-code**（⭐78,600+）: スキル・instinct・メモリ・セキュリティ・research-first開発を統合したエージェントハーネス最適化システム
- **skills-janitor**: スキルの監査・重複除去・修正・使用状況追跡

### Agents（135体・10カテゴリ）

Business & Product（12体）が特に収益化に直結: product-manager / ux-researcher / business-analyst / growth-hacker / sales-engineer など。

### Skills / Commands / Hooks

35スキル + SkillKit経由400,000+。コマンド42本（Git・Testing・Security・Architecture等）、フック19本。

### Ecosystem（51+）

claude-mem（⭐35,900+）・wshobson/agents（⭐31,300+）・oh-my-claudecode（⭐9,900+）・ccusage（⭐11,500+）・ccpm（⭐7,600+）など。

## factory での活用方法

| ステップ | 活用リソース |
|---|---|
| `/research` | Research & Analysis エージェント（market-researcher等） |
| `/select-repos` | Ecosystemのスター数・メンテ状況で既存実装を再利用 |
| `/plan` | Orchestration エージェント（multi-agent-coordinator等） |
| `/transform` | pro-workflow + Language Experts エージェント |
| `/optimize` | Business & Product エージェント（growth-hacker, pricing-strategist） |

## 注目アイテム

- **pro-workflow**: self-correcting memory 付きの実戦ワークフロー
- **claude-mem**: セッション跨ぎのコンテキスト保持
- **SkillKit Marketplace**: 自作スキルの外販チャネルにもなりうる
- **Business & Product エージェント群**: 受注判断・提案書作成に転用可能

## 注意点

- `everything-claude-code`（78,600+）等の異常なスター数はbot inflationの可能性あり
- READMEに「XVARY Stock Research」という無関係なプロモーションセクションが混在している
- SkillKit 400,000+は外部マーケットプレイスで品質はピンキリ
- 各プラグインの個別リポジトリのメンテ状況は別途確認が必要
