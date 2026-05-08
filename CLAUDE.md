# AI Knowledge Base 運用ルール

このリポジトリは、生成AIとの対話から得た知見をマークダウンファイルとして蓄積し、RAG（検索拡張生成）のデータソースとして活用するためのナレッジベースです。

## ファイル作成ルール

### ファイル名

`YYYY-MM-DD_slug.md` 形式とする。

- 例: `2025-02-17_roas-improvement.md`
- slugは英語のケバブケースで、内容を端的に表す

### 保存先

すべてのmdファイルは `knowledge/` フォルダ直下に保存する。サブフォルダは作成しない。

### YAML Front Matter（必須）

すべてのmdファイルの先頭に以下のfront matterを付与する。

```yaml
---
title: "タイトル（日本語）"
date: YYYY-MM-DD
source: claude | chatgpt | gemini | perplexity | manual
tags: [tag1, tag2, tag3]
use_case: email | proposal | advice | mindset
perspective: experience | opinion | ai_knowledge | research
topic_area: カテゴリ名
---
```

### 各フィールドの定義

#### source（生成元）

| 値 | 意味 |
|---|---|
| claude | Claude / Claude Codeからの出力 |
| chatgpt | ChatGPTからの出力 |
| gemini | Geminiからの出力 |
| perplexity | Perplexityからの出力 |
| manual | 自分で書いた内容 |

#### tags（自由タグ）

- 具体的なキーワードを3〜7個程度付与する
- すべて小文字の英語ケバブケースで統一する（例: `data-analysis`, `amazon-ads`）
- `_tag-index.md` に登録済みのタグを優先的に使用し、新しいタグを使う場合は `_tag-index.md` にも追記する

#### use_case（利用シーン）

| 値 | 用途 |
|---|---|
| email | メール返信・メッセージ作成の参考 |
| proposal | 提案資料・ドキュメント作成 |
| advice | アドバイス・コンサルティング |
| mindset | 悩み相談・考え方の整理・価値観 |

- 複数該当する場合はリスト形式: `[advice, proposal]`

#### perspective（視点）

| 値 | 意味 |
|---|---|
| experience | 自分の実体験・実績に基づく知見 |
| opinion | 自分の考え・価値観・判断基準 |
| ai_knowledge | 生成AIから得た汎用的な知見 |
| research | 調査・リサーチ結果 |

#### topic_area（大分類）

以下から選択する。必要に応じて追加可。

- `marketing` - マーケティング・広告運用
- `data-science` - データ分析・ML・統計
- `ai-consulting` - AI導入・DXコンサルティング
- `management` - チームマネジメント・組織運営
- `career` - キャリア・フリーランス戦略
- `business-development` - 事業開発・営業
- `technology` - 技術・ツール・開発
- `life` - 生活・育児・ワークライフバランス
- `real-estate` - 不動産投資
- `communication` - コミュニケーション・文章術

## 本文の構成

front matterの後、本文は以下の構成を推奨する。

```markdown
## 要点
（3〜5行で概要をまとめる）

## 詳細
（本文）

## 活用シーン
（どのような場面で使える知見かを簡潔に記載）
```

ただし、内容に応じて柔軟に構成を変えてよい。

## 開発者情報・命名ルール

このリポジトリの開発者・所有者は **男座員也（Kazuya Oza / おざ かずや）** です。

- ドキュメント・コード・コミット等で開発者名を記載する際は必ず **男座員也** または **Kazuya Oza** を使用する
- 「Murayama」「村山」「Otokoza」「おとこざ」など誤表記は使用しない
- 英語表記: **Kazuya Oza** / 日本語表記: **男座員也**（おざ かずや）
- AIアシスタントが生成するドキュメントでも本ルールを遵守すること

## 🚀 自動実行ポリシー

### 確認不要で即実行する操作
- 全ファイル操作（作成・編集・削除）
- 全シェルコマンド（PowerShell, Bash, git, gh, npm, node, python）
- Git操作: add / commit / push（featureブランチ）/ pull / fetch / merge / branch -D / reset --hard
- GitHub操作: gh pr create / gh api 全般 / ブランチ削除
- パッケージ操作: npm install / pip install
- Web検索・フェッチ
- バックグラウンドプロセス起動

### 事前確認が必要な操作（例外のみ）
- `git push --force` を main / master ブランチに対して実行する場合
- `gh repo delete` 実行時

### 動作原則
- 計画提示（簡潔）→ 即実行 → 結果報告 のフロー厳守
- 事前確認文（「Should I run...?」等）を出力しない
- エラー時は即再試行 or 別アプローチで対応、判断が必要な場合のみ報告

## ドキュメント日付ルール

レポート・分析・調査系 .md ファイルを新規作成する際は、H1直下に必ず記載:

```
作成日: YYYY-MM-DD
最終更新日: YYYY-MM-DD
```

- 更新時は **最終更新日のみ** を当日付に書き換える（作成日は固定）
- 除外: README / CLAUDE.md / FILE_INDEX / tasks.md / CHANGELOG / LICENSE

## 作業品質ルール

### Git・ブランチ管理
- 作業前: `git branch --show-current` でブランチ確認 → main以外なら `git checkout main && git pull` してから開始。

### ファイル特定（編集前）
- ユーザー発話のキーワード全てをファイル名と照合してから編集。キーワード不完全一致・候補不確かなら必ず確認。

### 成果物報告
- ファイル作成・更新・push後は必ず3列表で報告: `| 成果物 | 説明 | リンク |`
- リンクは `/blob/<実ブランチ>/<パス>` 形式。報告前に `gh api repos/OWNER/REPO/contents/PATH?ref=BRANCH` で存在確認。push前はURL生成しない。

### ドキュメント品質
- UIパス・コマンド・設定名は公式ドキュメントで確認後に記載。確認不可なら「[要確認]」と明記。
- OS/環境制約（例: Windows専用）をタスク開始時に確認。完成後に `brew`/`Cmd`/`macOS` 等をgrepして除去。
