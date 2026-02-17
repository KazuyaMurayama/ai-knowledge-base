---
title: "RAGナレッジベースの設計方針と運用ルール"
date: 2025-02-17
source: claude
tags: [rag, knowledge-management, prompt-engineering, ai-strategy, llm]
use_case: [advice, proposal]
perspective: ai_knowledge
topic_area: ai-consulting
---

## 要点

- 生成AIとの対話から得た知見をマークダウンで蓄積し、RAGのデータソースとして活用する
- YAML Front Matterで構造化メタデータを付与し、検索精度と分類性を両立する
- tags（自由タグ）・use_case（利用シーン）・perspective（視点）・topic_area（大分類）の4軸でフィルタリング可能にする
- タグの表記揺れを防ぐため、_tag-index.mdで一覧管理する

## 詳細

### なぜマークダウン + Front Matter なのか

1. **ポータビリティ**: プレーンテキストなのでどのツール・AIでも読み込める
2. **構造化と自由度の両立**: Front Matterで検索用メタデータを持ちつつ、本文は自由に書ける
3. **Git管理との相性**: 差分管理・履歴追跡・ブランチ運用が自然にできる
4. **RAG最適化**: チャンク分割時にFront Matterのメタデータをフィルタ条件として使える

### メタデータ設計のポイント

- `source` で生成元AIを記録し、後から品質傾向を分析可能にする
- `perspective` で「自分らしさ」と「AI知見」を切り分け、パーソナライズされた回答生成を支援する
- `tags` はRAG検索精度に最も直結するため、固定リストにせず自由記述とし粒度を細かく保つ
- `topic_area` はタグの上位カテゴリとして大まかな絞り込みに使う

### ファイル命名規則

`YYYY-MM-DD_slug.md` とすることで：
- フォルダ内で時系列ソートされる
- slugで内容が一目でわかる
- 一意性が保たれる

## 活用シーン

- 新しいナレッジベースを構築する際の設計リファレンスとして
- RAGシステムのデータソース設計をクライアントに提案する際の参考資料として
- チームでナレッジ共有の仕組みを整備する際の運用ルールのベースとして
