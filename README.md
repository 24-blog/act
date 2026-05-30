# 条文検索 / Law Article Search

GitHub Pages で動作する、法令条文の番号検索ツールです。

## ファイル構成

```
/
├── index.html
└── data/
    ├── manifest.json       ← 法令一覧（ここを編集して法令を追加）
    └── constitution.txt    ← 日本国憲法
```

## 法令を追加する方法

### 1. 条文テキストファイルを `data/` に追加

フォーマットは **1条1ブロック**。各条の開始行を `第〇条` または `第00条` で始めてください。

```
第一条　…本文…
２　…第2項…
第二条　…本文…
```

アラビア数字の場合：
```
第1条　…本文…
２　…
第2条　…
```

### 2. `data/manifest.json` に1行追加

```json
[
  {
    "id": "constitution",
    "label": "日本国憲法",
    "file": "data/constitution.txt",
    "maxArticle": 103,
    "articleStyle": "kanji"
  },
  {
    "id": "civil_code",
    "label": "民法",
    "file": "data/civil_code.txt",
    "maxArticle": 1050,
    "articleStyle": "arabic"
  }
]
```
#### ※Json追加は一行形式とする
| フィールド | 説明 |
|---|---|
| `id` | 識別子（英数字、重複不可） |
| `label` | ドロップダウンに表示される名称 |
| `file` | テキストファイルのパス |
| `maxArticle` | 最大条文番号（入力欄の上限・ヒント表示に使用） |
| `articleStyle` | `"kanji"`（第一条）または `"arabic"`（第1条） |

以上の2ステップで法令が追加されます。

### 3. 法令をtxt形式で取得する
https://24-blog.github.io/act/converter.html
