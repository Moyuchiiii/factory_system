---
name: select-repos
description: research.md を読んでビジネスアイデアに必要なリポジトリを選定し selected-repos.md を生成する。book/ の全リポジトリを参照して plugin/clone/copy/mcp/reference の5種別に分類。critic が最大2ラウンドで品質を担保する。
---

# /select-repos スキル

`research.md` を読んでビジネスアイデアに必要なリポジトリを選定する。
全リポジトリを参照した上で必要なものだけを選び、種別ごとにインストール手順を作成する。
critic と最大2ラウンドで品質を担保する。

---

## フロー

### ステップ1: 前提確認

`research.md` が存在することを確認する。なければ `/research` を先に実行するよう案内する。

### ステップ2: リポジトリ全参照

以下を全て読む:
- `book/claude-code-repos.md`
- `book/factory-repos-selection.md`
- `book/summaries/` 以下の全サマリーファイル

### ステップ3: 選定

`research.md` のビジネスアイデア・技術要件と照合して必要なリポジトリを選定する。

各リポジトリを以下の5種別に分類:

| 種別 | 処理 | 判断基準 |
|---|---|---|
| plugin | `claude plugin add` | Claude Code プラグイン形式 |
| clone | `git clone` して参照 | スクリプト・フック等を直接使う |
| copy | ファイルを `.claude/` にコピー | 設定ファイル・スキルをそのまま使う |
| mcp | `claude_desktop_config.json` に追記 | MCP サーバー |
| reference | `book/summaries/` を参照するだけ | 知識源として使う（インストール不要） |

### ステップ4: critic ループ（最大2ラウンド）

```
Round 1: builder が selected-repos.md を生成
Round 2: critic が批判（選定理由の妥当性・重複・見落とし）
Round 3: builder が修正 → critic が再評価 → APPROVE or ESCALATE
```

### ステップ5: 状態保存

`.factory/state.json` を更新。

---

## 出力: selected-repos.md

```markdown
# Selected Repos - [プロジェクト名]

## 選定リスト

### plugin（インストール: claude plugin add）
| リポジトリ | 用途 | コマンド |
|---|---|---|

### clone（インストール: git clone）
| リポジトリ | 用途 | パス |
|---|---|---|

### copy（ファイルコピー）
| リポジトリ | コピー元 | コピー先 |
|---|---|---|

### mcp（claude_desktop_config.json に追記）
| リポジトリ | 用途 | 設定キー |
|---|---|---|

### reference（book/summaries/ を参照）
| リポジトリ | サマリーファイル | 参照目的 |
|---|---|---|

## 選定理由
[各リポジトリを選んだ理由を簡潔に]

## インストール順序
1. plugin 系から順に実行
2. clone
3. copy
4. mcp
5. reference は参照のみ（インストール不要）
```
