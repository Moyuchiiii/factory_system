# Factory ワークフロー

## 5ステップ概要

| Step | スキル | 主担当 | critic ラウンド |
|---|---|---|---|
| 1 | /research | researcher | 最大3ラウンド |
| 2 | /select-repos | builder | 最大2ラウンド |
| 3 | /plan | planner | 最大4ラウンド |
| 4 | /transform | builder | 最大3ラウンド |
| 5 | /optimize | 全員 | 最大2ラウンド（任意） |

## critic 共通フロー

```
1. エージェントがアウトプットを生成・保存
2. critic エージェントに渡す
3. critic が構造化批判（根拠必須）を出力
4. エージェントが批判を受けて修正
5. critic が再評価
   - 修正済みの点は再批判しない
   - APPROVE → 即次のステップへ（残ラウンドはスキップ）
   - REVISE → 次のラウンドへ
   - ESCALATE → .factory/escalation-log.md に記録 → ユーザーへ
6. 上限ラウンド到達 → ユーザーに最終判断を委ねる
```

## 状態管理（セッション中断・再開対応）

各ステップ・ラウンドの終了時に `.factory/state.json` に保存する:

```json
{
  "currentStep": "plan",
  "currentRound": 2,
  "status": "in_progress",
  "completedSteps": ["research", "select-repos"],
  "lastUpdated": "2026-04-06T12:00:00Z"
}
```

セッション再開時は必ず state.json を確認し、続きから始める。
すでに完了したステップは再実行しない。

## ESCALATE ログフォーマット

`.factory/escalation-log.md` に追記:

```markdown
## ESCALATE - [日時] - [ステップ名] Round [N]

### critic の懸念
[批判内容]

### ユーザーの判断
[ユーザーの決定内容]

### リスク承認
承認者: ユーザー
承認日時: [日時]
```

## /transform のアトミック変換

```
1. .factory/temp/ に全新ファイルを生成・完成させる
2. 完成確認後に一括で本番パスにコピー
3. コピー完了後に git add & commit
4. 途中失敗時は .factory/temp/ を削除（本番には触れない）
```

## ブランチ戦略（/transform）

```bash
git checkout -b transform/[プロジェクト名]
# 問題なければ
git checkout main && git merge transform/[プロジェクト名]
# 問題あれば
git checkout main && git branch -D transform/[プロジェクト名]
```

## 並列実行

独立したタスクは必ず並列でエージェントを起動する。
同じファイルを複数エージェントが同時編集する設計は禁止。

## Plan Mode 使用基準

3ステップ以上、または設計判断を含むタスクは Plan Mode に入る。
曖昧な要件は実装前に仕様を明確化する。
