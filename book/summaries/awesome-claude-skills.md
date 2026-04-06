# awesome-claude-skills サマリー

> リポジトリ: https://github.com/travisvn/awesome-claude-skills
> ⭐ 10,619 | 🍴 1,048 | 最終更新: 2026-03-16
> 確認日: 2026-04-06

## 概要

Claude Code（およびClaude AI全般）向けのスキル・リソース・ツールをまとめたキュレーションリスト。Anthropic公式スキルからコミュニティ製スキルまで幅広くカバーしており、スキルを使ったClaudeのワークフロー拡張に特化している。2025年10月に作成されてから急速に成長しており（スター1万超）、Claude活用コミュニティの中心的なリソースになっている。

## スキル一覧

### 公式スキル（Anthropic製）

#### ドキュメント処理
- **docx** — Wordドキュメントの作成・編集・解析（トラック変更・コメント・フォーマット保持対応）
- **pdf** — PDFのテキスト/テーブル抽出、作成、マージ/分割、フォーム処理
- **pptx** — PowerPointプレゼンの作成・編集（レイアウト・テンプレート・チャート対応）
- **xlsx** — Excelスプレッドシートの作成・編集（数式・フォーマット・データ分析・可視化対応）

#### デザイン・クリエイティブ
- **algorithmic-art** — p5.jsを使ったジェネラティブアート生成（シードランダム・フローフィールド・パーティクル）
- **canvas-design** — デザイン哲学に基づくビジュアルアートをPNG/PDF形式で生成
- **slack-gif-creator** — Slackのサイズ制限に最適化されたアニメーションGIF作成

#### 開発
- **frontend-design** — React & Tailwind対応のUI設計スキル
- **web-artifacts-builder** — React・Tailwind CSS・shadcn/uiを使ったHTMLアーティファクト生成
- **mcp-builder** — 外部APIと連携するMCPサーバーの構築ガイド
- **webapp-testing** — PlaywrightによるローカルWebアプリのUIテスト・デバッグ

#### コミュニケーション
- **internal-comms** — ステータスレポート・ニュースレター・FAQ等の社内コミュニケーション文書作成

#### スキル作成
- **skill-creator** — Q&A形式でインタラクティブに新スキルを構築するツール

### コミュニティスキル（抜粋）

- **obra/superpowers** — TDD・デバッグ・コラボパターンを含む20以上のバトルテスト済みスキル集（特に著名）
- **ios-simulator-skill** — iOSアプリのビルド・ナビゲーション・自動化テスト
- **ffuf-web-fuzzing** — ペネトレーションテスト向けWebファジング
- **playwright-skill** — 汎用ブラウザ自動化（Playwright）
- **loki-mode** — 6スウォームにまたがる37 AIエージェントを指揮するマルチエージェント自律システム
- **Trail of Bits Security Skills** — CodeQL/Semgrep静的解析・コード監査・脆弱性検出
- **frontend-slides** — アニメーションリッチなHTMLプレゼン作成（PowerPoint変換対応）
- **shadcn/ui** — shadcnコンポーネントへのコンテキスト付与＋パターン強制
- **Skill_Seekers** — ドキュメントサイトをClaudeスキルに変換するツール

## factory での活用方法

### スキルの構造パターンを参照する
- Markdownファイルのフォーマット・書き方の規約を確立するための参考に
- `skill-creator` スキルを使えば、factory固有スキルを体系的に構築できる

### 再利用可能なスキルをそのまま組み込む
- `obra/superpowers` のTDD・デバッグスキルは開発系案件の品質管理に即活用できる
- `pdf`・`xlsx`・`docx` は納品物生成・帳票作成に直接使える
- `webapp-testing` はWebアプリ案件のQA自動化に組み込める

### `/transform` での活用
- `loki-mode`（37エージェント指揮）は factory のマルチエージェント構成の参考になる
- `Skill_Seekers` を使って、受注したクライアントのドキュメントを動的にスキル化できる

## 注目スキル

| スキル | 用途 | 注目理由 |
|--------|------|----------|
| **obra/superpowers** | TDD・デバッグ・協調パターン | 20+スキルをまとめたバッテリー込みのベストプラクティス集 |
| **loki-mode** | マルチエージェント自律システム | 37エージェントを6スウォームで動かす仕組みは factory のアーキテクチャ設計参考になる |
| **skill-creator** | スキル自作ツール | factory用スキルを量産するメタスキル |
| **Trail of Bits Security Skills** | セキュリティ静的解析 | セキュリティ案件受注時に即使える |
| **mcp-builder** | MCPサーバー構築 | 外部API連携を必要とする案件でMCPを素早く作るためのガイド |
| **Skill_Seekers** | ドキュメント→スキル変換 | クライアントのAPIドキュメントをスキル化して効率化できる |

## 注意点

- **メンテ状況**: last pushed が 2026-03-16 で約3週間更新なし。open issues が264件あり
- **ライセンス未指定**: コミュニティスキルの再配布には元リポジトリのライセンスを個別確認すること
- **コミュニティスキルの品質差**: 公式スキルと異なり、メンテ状況・品質にばらつきがある
- **バージョン管理**: Claude Codeのアップデートにより、古いスキルの挙動が変わる可能性がある
