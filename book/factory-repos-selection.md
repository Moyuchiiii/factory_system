# Factory Select-Repos 選定結果

> 作成日: 2026-04-06
> 対象: factory プロジェクト（https://github.com/Moyuchiiii/factory_system）
> 参照元: book/claude-code-repos.md + X(@oooodjdjd)の40リポジトリリスト

---

## Tier 1 — 直接インストール（factory本体の品質に直結）

| リポジトリ | 用途 |
|---|---|
| hesreallyhim/awesome-claude-code | Claude Codeベストプラクティス全網羅。factoryが「正しいプロジェクト」を生成するための知識源 |
| obra/superpowers | ⭐93,000+。TDD・YAGNI・DRYを強制する品質フレームワーク。生成プロジェクトの品質担保 |
| Piebald-AI/claude-code-system-prompts | Claude Code内部動作の把握。CLAUDE.mdとスキルを正しく書くために必須 |
| disler/claude-code-hooks-mastery | ⭐3,000+。13イベント全実装。factory自身のフック＋生成プロジェクトのフック設計に使う |
| ChrisWiles/claude-code-showcase | フック・スキル・エージェント・コマンドが全部揃ったリファレンス実装。生成プロジェクトの完成形の参考 |

---

## Tier 2 — 知識ベースとして参照（インストールはしないが読み込む）

### Claude Code パターン系
| リポジトリ | 用途 |
|---|---|
| rohitg00/awesome-claude-code-toolkit | 135エージェント・35スキルのプール。/transformでスキルを生成するときの引き出し |
| affaan-m/everything-claude-code | ハッカソン優勝作。スキル・メモリ・セキュリティ・調査を統合したアーキテクチャ参考 |
| vinicius91carvalho/.claude | factoryが生成するものとほぼ同じ構造。ポータブル設定の設計パターン |
| travisvn/awesome-claude-skills | ワークフロー特化スキルの集合。/transformでスキルを選ぶときの選択肢 |
| shinpr/claude-code-workflows | 本番品質のワークフローパターン。生成プロジェクトの設計に使う |

### ビジネス・収益化方法論系
| リポジトリ | 用途 |
|---|---|
| easychen/one-person-businesses-methodology | 一人会社のゼロ→収益の完全方法論。トピック選定・価格設定・顧客獲得・運用の全フロー。/researchの「何で稼ぐか」設計の核 |
| mezod/awesome-indie | 独立開発者の収益化アイデア・成功事例・ツール集。/researchが参照する稼ぎ方パターン辞典 |
| XiaomingX/ai-money-maker-handbook | AI副業アイデア大全。factoryが扱うAI系収益化モデルのアイデアプール |

---

## Tier 3 — 生成プロジェクトのテンプレ・スキル（ユースケース別）

| リポジトリ | 条件 |
|---|---|
| wasp-lang/open-saas | SaaS系プロジェクト生成時。Stripe・認証・メール・購読管理・AI連携内蔵のフルスタックテンプレ |
| nextjs/saas-starter | 軽量SaaS系プロジェクト生成時。Next.js公式・Postgres・Stripe・shadcn/ui |
| kevinrgu/autoagent | /optimizeスキルの設計思想として参照。Docker重いので直接インストールはしない |
| github/github-mcp-server | 生成プロジェクトがGit操作を必要とするケース |
| czlonkowski/n8n-mcp | n8n系の案件を生成するケース |
| harry0703/MoneyPrinterTurbo | 動画系収益化プロジェクト生成時。※メンテ不足注意、アイデア参考として |
| dreammis/social-auto-upload | SNS自動投稿が必要なプロジェクト生成時 |

---

## 不要（factory本体には）

- quemsah/awesome-claude-plugins — 週次追跡ツール、運用フェーズ向け
- steipete/claude-code-mcp — 複雑すぎる
- zilliztech/claude-context — 大規模コードベース向け
- CloudAI-X/claude-workflow-v2 — superpowersで代替可能
- 金融・Crypto系全般 — Claude Codeプロジェクト生成と無関係
- リモートワークリスト系 — ただのリンク集
- 中国SNS特化系（md2wechat, XiaohongshuSkills等）— 日本市場での優先度低
