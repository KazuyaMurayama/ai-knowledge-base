---
title: "フリーランス営業パイプライン自動化システム設計"
date: 2026-02-25
source: claude
tags: [freelance, automation, pipeline, career-planning, python, streamlit]
use_case: [advice, proposal]
perspective: experience
topic_area: career
---

## 要点

高単価AI案件（月250万円以上）の発見・評価・応募プロセスを自動化するシステムの設計。LLMで案件情報を構造化しスキルマッチスコアリング（0-100）を行い、提案書ドラフトを自動生成。CRM/パイプライン管理機能で複数案件の進捗を統合管理。技術スタックはPython + Streamlit + SQLite + Claude API。

## 詳細

### 解決する課題

| 優先度 | ボトルネック | 影響度 |
|:---:|---|---|
| 1 | 5社以上のエージェントサイト手動巡回（1日30-60分） | ★★★★★ |
| 2 | 提案書カスタマイズの工数（1件30分） | ★★★★ |
| 3 | 案件とスキルの適合判断に時間 | ★★★★ |

### MVP機能（4つ）

1. **案件入力・構造化**: URL/テキスト → LLMで構造化データ化
2. **スキルマッチスコアリング**: オーナースキルとの適合度0-100 + タグ付け・要約
3. **提案書ドラフト生成**: 案件情報 + 実績から応募文をカスタマイズ生成
4. **CRM/パイプライン管理**: 発見→評価済→応募中→面談→契約/見送りのステータス管理

### アーキテクチャ

```
Streamlit UI → Service Layer (JobParser / ProposalGenerator / PipelineManager) → Claude API + SQLite
```

### KPI

- 案件評価時間: 15分→3分（80%削減）
- 提案書作成時間: 30分→5分（83%削減）
- LLM APIコスト: 月50案件で$1.5-$4.5

**出典リポジトリ**: freelance-sales-pipeline

## 活用シーン

- フリーランス独立時の営業効率化ツール設計参考
- LLMを活用した業務自動化システムのアーキテクチャ参考
- 個人向けCRM/パイプライン管理の設計パターン
