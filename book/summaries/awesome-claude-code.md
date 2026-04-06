# awesome-claude-code サマリー

> リポジトリ: https://github.com/hesreallyhim/awesome-claude-code
> ⭐ 36,756 | 🍴 2,907 | 最終更新: 2026-04-06
> 確認日: 2026-04-06

## 概要

Claude Code（Anthropic製AIコーディングエージェント）向けの厳選リソース集。スキル・フック・スラッシュコマンド・マルチエージェントオーケストレーター・IDE統合・CLAUDE.mdテンプレートなど100以上のリソースを網羅する。2025年4月に作成されてから急成長しており、現在も活発に更新・追加が続いている。

## 主なカテゴリ

- **Agent Skills 🤖**: DevOps・セキュリティ監査・フルスタック開発・科学研究など20以上の専門スキル集（Trail of Bits Security Skills、AgentSys等）
- **Workflows & Knowledge Guides 🧠**: スペック駆動開発・プロジェクト管理・マルチエージェントチーム設計・自律ループ実装など（General / Teams / Ralph Wiggum の3サブカテゴリ）
- **Tooling 🧰**: セッション管理・使用量モニター・オーケストレーター（Auto-Claude、Claude Squad、Ruflo等）・IDE拡張（VS Code / Emacs / Neovim / IntelliJ）
- **Hooks 🪝**: ライフサイクルフック実装例——安全ガードレール・品質チェック・スペルチェック・リアルタイムバリデーション（10以上）
- **Slash-Commands 🔪**: バージョン管理・コード分析・TDD・ドキュメント生成・CI/CD・タスク管理など用途別に整理されたカスタムコマンド集
- **CLAUDE.md Files 📂**: 言語別（Python / Go / TypeScript / Rust / Kotlin）・ドメイン別（ブロックチェーン / ゲーム / セキュリティ）のCLAUDE.mdテンプレート集
- **Status Lines 📊**: トークン使用量・モデル情報・git連携を表示するターミナルステータスバー設定（5種）
- **Alternative Clients 📱**: Web UI・デスクトップアプリ・tmux統合・モバイル同期など5種の代替クライアント
- **Official Documentation 🏛️**: Anthropic公式ガイド・APIリファレンス・GitHub Actions連携

## factory での活用方法

| ステップ | 活用方法 |
|---|---|
| `/research` | 「Tooling > Orchestrators」でマルチエージェントフレームワークを調査。既存実装を fork・参照して調査コストを削減 |
| `/select-repos` | 各カテゴリのスター数・最終コミット日で選定候補を絞り込む |
| `/plan` | 「Workflows & Knowledge Guides」のスペック駆動ワークフローをプランテンプレートとして流用 |
| `/transform` | 「CLAUDE.md Files」の言語・ドメイン別テンプレートをコンテキスト設定に活用。「Agent Skills」を専門スキルとして組み込む |
| `/optimize` | 「Tooling > Usage Monitors」でトークンコスト可視化。「Hooks」の品質チェック実装を自動検証パイプラインに組み込む |

## 注目アイテム

- **Trail of Bits Security Skills**: セキュリティ監査に特化したエージェントスキル集——脆弱性検査の自動化に直結
- **claude-devtools**: ターンベースのコンテキストデータを可視化するデスクトップアプリ。セッション観測・デバッグに有用
- **Claude Code Agent Teams Exercises**: マルチエージェントチーム設計の実践演習——チーム構成設計の参考に
- **Ruflo**: 自己学習・ベクターメモリ対応の自律マルチエージェントスウォームフレームワーク
- **Harness**: ドメイン特化エージェントチームの設計パターン集
- **Hooks実装集**: 危険コマンドブロック・コード品質自動チェック——既存の `.claude/hooks/` 強化の参考として即活用可能
- **CLAUDE.md テンプレート集**: TypeScript / Python / Rustなど言語別の設定ベストプラクティス

## 注意点

- リソースの品質にバラつきあり——スター数や最終コミット日を個別に確認してから採用すること
- 一部リソースはClaude Code初期（2025年前半）のAPIに依存している可能性があり、最新バージョンとの互換性を要確認
- コミュニティ提出ベースのため、ドキュメントが薄いor未メンテのリポジトリが混在している
- README が Awesome / Extra / Classic / Flat の4スタイルで提供されており、見やすい形式を選ぶと整理しやすい
- 169件のオープンイシューあり——追加リクエストが多く、今後も更新が見込まれる活発なリポジトリ
