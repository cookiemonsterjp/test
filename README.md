# test

## Notion MCP Integration

Claude CodeからNotion MCPサーバーを利用して、Notionワークスペースと連携するための設定です。

### セットアップ手順

#### 1. Notion APIキーを取得する

1. [Notion Integrations](https://www.notion.so/my-integrations) にアクセス
2. 「New integration」をクリックして新しいインテグレーションを作成
3. 名前を付けて、対象のワークスペースを選択
4. 「Internal Integration Secret」をコピー

#### 2. インテグレーションをNotionページに接続する

連携したいNotionページ/データベースで:
1. ページ右上の「...」メニューを開く
2. 「Connections」→ 作成したインテグレーション名を選択して追加

#### 3. APIキーを設定する

`.claude/settings.json` 内の `YOUR_NOTION_API_KEY` を取得したAPIキーに置き換えてください:

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "OPENAPI_MCP_HEADERS": "{\"Authorization\":\"Bearer ntn_xxxxxxxxxxxxx\",\"Notion-Version\":\"2022-06-28\"}"
      }
    }
  }
}
```

#### 4. 必要な依存関係

- Node.js (v18以上)
- npm / npx

### 利用可能な操作

Notion MCPサーバーを通じて、以下の操作が可能です:

- ページの検索・取得
- ページの作成・更新
- データベースのクエリ
- ブロックの追加・更新・削除
- コメントの取得・追加
