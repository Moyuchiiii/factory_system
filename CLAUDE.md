# Factory System

@.claude/rules/soul.md
@.claude/rules/roles.md
@.claude/rules/workflow.md

Claude活用で収益化プロジェクトを自動生成するファクトリー。
clone → 5ステップ → 専用プロジェクトに変身。

## 基本方針

- 日本語で応答する
- コードのコメントは日本語で書く（変数名・関数名は英語）
- IMPORTANT: 変更を加える前に必ず対象ファイルを読んで理解すること
- IMPORTANT: セッション開始時に `.claude/rules/lessons.md` を読む
- IMPORTANT: 情報は必ず裏取り・ソース記載（`.claude/rules/security.md` 参照）

## 使い方（5ステップ）

| Step | コマンド | 内容 | critic ラウンド |
|---|---|---|---|
| 1 | `/research` | 何で稼ぐかを決める | 最大3ラウンド |
| 2 | `/select-repos` | 必要なリポジトリを選ぶ | 最大2ラウンド |
| 3 | `/plan` | プロジェクトを設計する | 最大4ラウンド |
| 4 | `/transform` | このリポジトリを変身させる | 最大3ラウンド |
| 5 | `/optimize` | スキルを改善し続ける | 最大2ラウンド（任意） |

## 品質保証

- 全ステップに critic エージェント（Opus）を噛ませる
- critic は根拠なし批判禁止。修正済みの点は再批判しない
- APPROVE が出たら即次のステップへ（ラウンド上限は最大値）
- ESCALATE は `.factory/escalation-log.md` に記録してユーザーへ

## 状態管理

セッション中断・再開に備えて `.factory/state.json` に状態を保存する。
セッション開始時は必ず state.json を確認し、途中から再開する。

## ファイル構成

- `.claude/rules/` : ルール定義（soul / roles / workflow / security 等）
- `.claude/skills/` : 5つのスキル（/research 〜 /optimize）
- `.claude/agents/` : researcher / planner / critic / builder
- `book/` : リポジトリリスト・選定結果・サマリー
- `.factory/` : transform 後に factory ファイルを退避（自動生成）

## コア原則

- **シンプル第一**: 変更は可能な限り単純に
- **根本解決**: 応急処置ではなく根本原因を解決する
- **検証必須**: 動作確認なしに完了扱いにしない
- **問題時は即停止**: 行き詰まったら再計画する
