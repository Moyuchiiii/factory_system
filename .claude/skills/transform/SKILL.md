---
name: transform
description: plan.md を読んでこのリポジトリ自体を収益化プロジェクトに変身させる。アトミック変換でファイルの整合性を保ち、critic と最大3ラウンドで品質を確認する。失敗してもブランチ戦略で安全にロールバックできる。
---

# /transform スキル

`plan.md` を読んでこのリポジトリ自体を収益化プロジェクトに変身させる。
アトミック変換でファイルの整合性を保ち、critic と最大3ラウンドで品質を確認する。
失敗してもブランチ戦略で安全にロールバックできる。

---

## フロー

### ステップ1: 前提確認

以下が存在することを確認する:
- `research.md` ✓
- `selected-repos.md` ✓
- `plan.md` ✓
- git が初期化されていること ✓

いずれかが欠けていれば作業を止めてユーザーに報告する。

### ステップ2: ブランチ作成

```bash
git checkout -b transform/[プロジェクト名]
```

### ステップ3: factory ファイルの退避

```
.factory/
├── CLAUDE.md          ← 元の CLAUDE.md をコピー
├── .claude/           ← 元の .claude/ を丸ごとコピー
├── state.json         ← 現在の状態
└── escalation-log.md  ← エスカレーションログ（あれば）
```

### ステップ4: アトミック変換（builder が実行）

```
1. .factory/temp/ を作成
2. plan.md を読んで全新ファイルを .factory/temp/ に生成:
   - temp/CLAUDE.md
   - temp/.claude/rules/
   - temp/.claude/skills/
   - temp/.claude/agents/
3. 全ファイルの完成を確認する（不完全なら temp/ を削除して中断）
4. 完成確認後、一括で本番パスにコピーする
5. .factory/temp/ を削除
6. selected-repos.md の手順でリポジトリをインストール
7. git add -A && git commit -m "transform: [プロジェクト名]に変身"
```

**途中で失敗した場合**:
`.factory/temp/` を削除して終了。本番ファイルには一切触れない。

### ステップ5: critic ループ（最大3ラウンド）

critic が以下を確認:
- 生成された CLAUDE.md は plan.md の設計通りか
- スキル・エージェント・ルールは正しく生成されているか
- リポジトリは正しくインストールされているか
- .factory/ への退避は完全か
- 動作するプロジェクトとして完成しているか

APPROVE → ステップ6へ
ESCALATE → `.factory/escalation-log.md` に記録してユーザーへ

### ステップ6: マージまたはロールバック

**問題なし（APPROVE）**:
```bash
git checkout main
git merge transform/[プロジェクト名]
```

**問題あり（ユーザー判断でロールバック）**:
```bash
git checkout main
git branch -D transform/[プロジェクト名]
# .factory/ から元ファイルを復元
cp .factory/CLAUDE.md ./CLAUDE.md
cp -r .factory/.claude/ ./.claude/
```

### ステップ7: 状態保存

`.factory/state.json` を更新:
```json
{ "currentStep": "transform", "status": "completed" }
```

---

## 変換完了レポート

```markdown
## Transform 完了レポート

### 変更ファイル
- 上書き: CLAUDE.md
- 再生成: .claude/rules/, .claude/skills/, .claude/agents/
- 退避: .factory/ に保存済み

### インストール済みリポジトリ
[種別ごとの一覧]

### 次のステップ
このリポジトリは [プロジェクト名] として動作します。
/optimize でスキルを改善できます。
```
