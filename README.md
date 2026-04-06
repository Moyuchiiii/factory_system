# Factory System

ビジネスアイデアを入力するだけで、Claude Code の収益化プロジェクトに自動変身するファクトリー。
全ステップに批判エージェント（Opus）を噛ませることで高精度を実現。

---

## コンセプト

```
git clone → 5ステップ実行 → 専用プロジェクトに変身 → 収益化
```

clone したこのリポジトリが、あなたのビジネスアイデアに合わせた
Claude Code プロジェクトへと自律的に変身します。

---

## Quick Start

```bash
# 1. クローン（プロジェクト名は自由に）
git clone https://github.com/Moyuchiiii/factory_system my-project
cd my-project

# 2. Claude Code で開く
# 3. 以下のスキルを順に実行する
```

---

## 5ステップ

| Step | コマンド | 内容 | critic |
|---|---|---|---|
| 1 | `/research` | 何で稼ぐかを決める | 最大3ラウンド |
| 2 | `/select-repos` | 必要なリポジトリを選ぶ | 最大2ラウンド |
| 3 | `/plan` | プロジェクトを設計する | 最大4ラウンド |
| 4 | `/transform` | このリポジトリを変身させる | 最大3ラウンド |
| 5 | `/optimize` | スキルを改善し続ける | 最大2ラウンド（任意） |

---

## 品質保証の仕組み

全ステップに **critic エージェント（Opus モデル）** を噛ませています。

- `/research` → ソースの信頼性・数値の根拠を徹底検証
- `/select-repos` → 選定理由の妥当性をチェック
- `/plan` → 技術的実現可能性・収益モデルとの整合性を4ラウンドで確認
- `/transform` → 生成ファイルの品質を3ラウンドでレビュー

critic は **根拠なし批判禁止**。修正済みの点は再批判しません。

---

## 生成されるプロジェクトの例

- AI 業務効率化ツール（SaaS）
- コンテンツ販売自動化プロジェクト
- 自動化スクリプト販売・受注プロジェクト
- API サービス開発・販売プロジェクト

---

## ファイル構成

```
factory/
├── CLAUDE.md                    ← factory のメイン設定
├── .claude/
│   ├── rules/                   ← soul / roles / workflow 等
│   ├── skills/                  ← /research 〜 /optimize
│   └── agents/                  ← researcher / planner / critic / builder
└── book/
    ├── claude-code-repos.md     ← リポジトリリスト
    ├── factory-repos-selection.md ← 選定済みリポジトリ
    └── summaries/               ← 主要リポジトリのサマリー
```

`/transform` 実行後:

```
（上記に加えて）
└── .factory/                    ← factory ファイルの退避先
    ├── CLAUDE.md                ← 元の CLAUDE.md
    ├── .claude/                 ← 元の .claude/
    └── state.json               ← 実行状態の記録
```

---

## Requirements

- [Claude Code](https://claude.ai/code)
- Git
- Node.js v18 以上（一部リポジトリのインストールに必要）
- Python 3.10 以上（一部リポジトリのインストールに必要）

---

## セッション中断・再開

途中でセッションが終わっても `.factory/state.json` に状態が保存されます。
再開時は Claude Code を開いて「前回の続きから始めてください」と伝えるだけです。

---

## book/ の更新について

`book/claude-code-repos.md` は定期的に更新することを推奨します。
Claude Code エコシステムは急速に進化しており、新しい高品質リポジトリが継続的に登場しています。

---

## License

MIT
