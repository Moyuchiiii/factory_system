# Claude Code 厳選リポジトリ集

> X・YouTube・技術記事で話題になったレベルの高評価リポジトリをジャンル別にまとめたリスト。
> 最終更新: 2026-03-26

---

## 目次

1. [キュレーション・まとめ系](#キュレーションまとめ系)
2. [スキル・フレームワーク系](#スキルフレームワーク系)
3. [ワークフロー・エージェント系](#ワークフローエージェント系)
4. [フック・設定系](#フック設定系)
5. [MCPサーバー系](#mcpサーバー系)
6. [システムプロンプト・公式リソース系](#システムプロンプト公式リソース系)
7. [チュートリアル・学習系](#チュートリアル学習系)

---

## キュレーション・まとめ系

Claude Code 関連のリポジトリやツールをまとめたキュレーションリスト。

| リポジトリ | 説明 | 特徴 |
|---|---|---|
| [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | Claude Code 公式認定キュレーションリスト | スキル・フック・コマンド・エージェントなど幅広くカバー。コミュニティの中心的リファレンス |
| [rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) | 最も包括的なツールキット | エージェント135件・スキル35件（SkillKit経由40万件以上）・コマンド42件・プラグイン150件以上・フック19件を収録 |
| [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code) | エージェントハーネス最適化システム | Cerebral Valley × Anthropic ハッカソン（2026年2月）優勝作。スキル・記憶・セキュリティ・調査機能を統合 |
| [quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins) | プラグイン採用指標の自動集計 | n8nワークフローで8,600件以上のリポジトリを週次追跡 |
| [awesomeclaude.ai](https://awesomeclaude.ai/) | ビジュアルディレクトリ | Webサイト形式でawesome-claude-codeを閲覧可能 |

---

## スキル・フレームワーク系

Claude Code のスキル（`/skill` コマンド）を拡張するフレームワークとコレクション。

| リポジトリ | 説明 | 特徴 |
|---|---|---|
| [obra/superpowers](https://github.com/obra/superpowers) | **エコシステム最大の人気リポジトリ** ⭐93,000+ | TDD・YAGNI・DRY を強制するエージェント型開発方法論。Anthropic マーケットプレイス公式採用 |
| [obra/superpowers-marketplace](https://github.com/obra/superpowers-marketplace) | Superpowers 用マーケットプレイス | `/plugin marketplace add obra/superpowers-marketplace` で登録可能 |
| [obra/superpowers-skills](https://github.com/obra/superpowers-skills) | コミュニティ編集可能なスキル集 | Superpowers プラグイン向けのコミュニティスキル |
| [obra/superpowers-chrome](https://github.com/obra/superpowers-chrome) | Chrome ブラウザ制御プラグイン | DevTools Protocol 経由の直接操作。依存関係ゼロ |
| [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) | スキルのキュレーションリスト | Claude Code ワークフロー特化の厳選スキル集 |
| [langgptai/awesome-claude-prompts](https://github.com/langgptai/awesome-claude-prompts) | Claude 汎用プロンプト集 | Claude をより効果的に使うためのプロンプトキュレーション |

---

## ワークフロー・エージェント系

マルチエージェント・オーケストレーション・自動化ワークフローに特化したリポジトリ。

| リポジトリ | 説明 | 特徴 |
|---|---|---|
| [shinpr/claude-code-workflows](https://github.com/shinpr/claude-code-workflows) | 本番対応の開発ワークフロー | 専門AIエージェントによるプロダクション品質のワークフロー集 |
| [CloudAI-X/claude-workflow-v2](https://github.com/CloudAI-X/claude-workflow-v2) | ユニバーサルワークフロープラグイン | エージェント・スキル・フック・コマンドを統合した汎用プラグイン |
| [vinicius91carvalho/.claude](https://github.com/vinicius91carvalho/.claude) | ポータブルワークフローシステム | フック・エージェント・スキル・強制ルールを含む移植可能な設定 |
| [danielrosehill/Claude-Code-Repos-Index](https://github.com/danielrosehill/Claude-Code-Repos-Index) | Claude Code 関連リポジトリインデックス | スターターテンプレートを含む幅広いリポジトリカタログ |
| [Comfy-Org/comfy-claude-prompt-library](https://github.com/Comfy-Org/comfy-claude-prompt-library) | アジェンティックコーディング向けコマンド集 | ComfyUI 開発チームが実運用で使うコマンドとメモリ集 |
| [kevinrgu/autoagent](https://github.com/kevinrgu/autoagent) | エージェント自己最適化ライブラリ | メタエージェントがタスクエージェントのハーネス（プロンプト・ツール・オーケストレーション）を自動改善。SpreadsheetBench 1位(96.5%)・TerminalBench 1位(55.1%)を24時間の自律最適化で達成 |

---

## フック・設定系

Claude Code のフック（Hooks）や `.claude/` 設定ファイルに特化したリポジトリ。

| リポジトリ | 説明 | 特徴 |
|---|---|---|
| [disler/claude-code-hooks-mastery](https://github.com/disler/claude-code-hooks-mastery) | フックマスター講座 ⭐3,000+ | フックライフサイクル全13イベント実装・TTS音声フィードバック・セキュリティ強化フックを含む実践的チュートリアル |
| [ChrisWiles/claude-code-showcase](https://github.com/ChrisWiles/claude-code-showcase) | プロジェクト設定のショーケース | フック・スキル・エージェント・コマンド・GitHub Actions を網羅したリファレンス実装 |

---

## MCPサーバー系

Model Context Protocol (MCP) を活用してClaude Code の機能を拡張するサーバー。

| リポジトリ | 説明 | 特徴 |
|---|---|---|
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | **MCP公式サーバー集** | Anthropic 公式のリファレンス実装集。MCPの起点となるリポジトリ |
| [github/github-mcp-server](https://github.com/github/github-mcp-server) | GitHub 公式 MCP サーバー | PR・Issue・リポジトリ操作を Claude から直接実行可能 |
| [steipete/claude-code-mcp](https://github.com/steipete/claude-code-mcp) | Claude Code をMCPサーバーとして動かす | エージェント内エージェント構成を実現するワンショットMCPサーバー |
| [czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp) | n8n ワークフロー自動化 MCP | n8nの1,239ノードに関する深い知識を Claude に付与 |
| [zilliztech/claude-context](https://github.com/zilliztech/claude-context) | コードベース全体をセマンティック検索 | ベクトル検索でコードベース全体をコンテキスト化するMCPプラグイン |
| [tolkonepiu/best-of-mcp-servers](https://github.com/tolkonepiu/best-of-mcp-servers) | MCPサーバーランキング（週次更新） | スター数・利用率でランク付けされたMCPサーバーリスト |

---

## システムプロンプト・公式リソース系

Claude Code の内部プロンプトや公式設定を公開・解析しているリポジトリ。

| リポジトリ | 説明 | 特徴 |
|---|---|---|
| [Piebald-AI/claude-code-system-prompts](https://github.com/Piebald-AI/claude-code-system-prompts) | Claude Code のシステムプロンプト全文公開 | ビルトインツール説明18件・サブエージェントプロンプト・CLAUDE.md・statusline等を収録。バージョンごとに更新 |

---

## チュートリアル・学習系

Claude Code の使い方を体系的に学べるガイドやサンプル集。

| リポジトリ | 説明 | 特徴 |
|---|---|---|
| [wesammustafa/Claude-Code-Everything-You-Need-to-Know](https://github.com/wesammustafa/Claude-Code-Everything-You-Need-to-Know) | Claude Code 完全ガイド | セットアップ・プロンプトエンジニアリング・コマンド・フック・MCP・BMADメソッドまでステップバイステップで解説 |

---

## 参考リンク

- [Claude Code 公式ドキュメント](https://code.claude.com/docs)
- [claude-code GitHub Topics](https://github.com/topics/claude-code)
- [9 GitHub Repos That Made My Claude Code 10x Faster](https://www.mejba.me/blog/best-github-repos-claude-code)
- [Top 50 Claude Skills and Github Repos (2026)](https://www.blockchain-council.org/claude-ai/top-50-claude-skills-and-github-repos/)
- [Top 5 GitHub Repositories for Free Claude Code Skills](https://www.analyticsvidhya.com/blog/2026/03/github-repositories-to-get-free-claude-code-skills/)
