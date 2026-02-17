# AI Knowledge Base

生成AIとの対話から得た知見を蓄積し、RAGのデータソースとして活用するためのナレッジベースリポジトリ。

## 構成

```
├── CLAUDE.md              # 運用ルール（Claude/Claude Codeが参照）
├── README.md              # このファイル
└── knowledge/             # ナレッジファイル格納フォルダ
    ├── _tag-index.md      # タグ一覧
    └── YYYY-MM-DD_slug.md # 各ナレッジファイル
```

## 運用ルール

詳細は [CLAUDE.md](./CLAUDE.md) を参照。

- すべてのナレッジは `knowledge/` フォルダ直下にマークダウンで保存
- YAML front matter（title, date, source, tags, use_case, perspective, topic_area）を必ず付与
- タグは `_tag-index.md` で管理し、表記揺れを防ぐ
