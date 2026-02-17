---
title: "RAGナレッジベースの設計方針と運用ルール策定"
date: 2025-02-17
source: claude
tags: [rag, generative-ai, prompt-engineering, automation]
use_case: advice
perspective: ai_knowledge
topic_area: technology
---

## 要点

生成AIの出力をマークダウンファイルとしてGitHubリポジトリに蓄積し、RAGの検索対象とする仕組みを構築した。YAML front matterによるメタデータ管理で、用途別・視点別の絞り込みを可能にしている。

## 詳細

### ストレージの選定

GitHub（プライベートリポジトリ）を採用。選定理由は以下の通り。

- LangChain・LlamaIndex等のRAGフレームワークにGitHubローダーが標準搭載
- マークダウンのネイティブレンダリング対応
- Gitによるバージョン管理
- Claude Codeからの直接push対応

Googleドライブはマークダウンのプレビューが弱く、NotionはAPIの制約があるため不採用とした。

### Front Matter設計

6つのフィールド（title, date, source, tags, use_case, perspective, topic_area）により、RAG検索時の多軸フィルタリングを実現。特にperspective（experience/opinion/ai_knowledge/research）の区分により、「自分らしさ」を反映した回答と汎用的知見の使い分けが可能。

## 活用シーン

- 新規ナレッジベース構築時の設計参考
- RAGシステムのメタデータ設計のテンプレート
