# template-eval-mlit-dpf-mcp

MLIT DATA PLATFORM MCP Server を LLM がどのように活用するかを検証する。

**このリポジトリはGitHubのテンプレートリポジトリです**
テンプレートからリポジトリを作成する方法は、[テンプレートからリポジトリを作成する - GitHub ドキュメント](https://docs.github.com/ja/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) を参照してください。

## 注意事項

> **WARNING**: 本リポジトリのプロンプトは、LLM に対して MCP サーバーのツール利用回数に制限を設けていません。タスクの内容によっては、多数のツール呼び出し(数十回以上)が発生し、LLM のトークン消費が大幅に増加する場合があります。実行前にタスクの規模を見積もり、コストに十分注意してください。
>
## このリポジトリの目的

1. **MCP サーバーの動作確認**: MLIT DATA PLATFORM MCP Server が提供する18種のツールが正しく動作するか検証する
2. **LLM によるツール活用の検証**: LLM がどのツールを、どのような判断で、どのような順序で使うかを記録・分析する
3. **検索戦略の知見蓄積**: キーワード検索、空間検索、属性検索などの使い分けに関する実践的な知見を蓄積する

## 前提条件

- MLIT DATA PLATFORM MCP Server が利用可能な状態であること
- Visual Studio Code (VSCode) が利用出来る、かつMCPクライアントとして機能すること(オプション)

## 利用方法

1. MLIT DATA PLATFORM MCP Server をローカル環境にセットアップし起動する
2. [EXAMPLE-PROMPTS.md](EXAMPLE-PROMPTS.md) のプロンプトテンプレートを参考に、LLM へデータ調査・分析を依頼する
3. 実行結果(計画、ログ、分析レポート、MCP使用実績)がタイムスタンプ付きディレクトリに出力される

### MLIT DATA PLATFORM MCP Server

> MLIT DATA PLATFORM MCP Serverは、国土交通データプラットフォームが提供する利用者向けAPIと接続するMCP (Model Context Protocol) サーバーです。
> 本MCPサーバーを利用することで、大規模言語モデル（LLM）と直接連携し、対話形式で直感的にデータを検索・取得することが可能になります。APIに関する専門的な知識がなくても、誰でも簡単に国土交通データプラットフォームから曖昧な指示や複雑な条件設定でデータを検索・取得できる、新しいデータ活用のかたちを提供します。

MLIT DATA PLATFORM MCP Server
<https://data-platform.mlit.go.jp/#/Page?id=apps_mcp>

MLIT-DATA-PLATFORM/mlit-dpf-mcp
<https://github.com/MLIT-DATA-PLATFORM/mlit-dpf-mcp>

MLIT-DATA-PLATFORM/mlit-dpf-mcp | DeepWiki
<https://deepwiki.com/MLIT-DATA-PLATFORM/mlit-dpf-mcp>

### Visual Studio Code (オプション)

VSCode をMPCクライアントとして利用する場合は、`.vscode/mcp.json` が利用出来る。

#### `.vscode/mcp.json`

`command` と `args` の値は、ローカル環境にセットアップしたMCPサーバーに合わせて変更して下さい。

```jsonc
{
  "servers": {
    "mlit-dpf-mcp": {
      "command": "path/to/mlit-dpf-mcp/.venv/bin/python",
      "args": ["path/to/mlit-dpf-mcp/src/server.py"],
      ...
    }
  }
}
```

#### MCP サーバーの起動(VSCode)

- VSCode で Command Palette を開く
    - macOS: `Cmd+Shift+P`
    - Windows/Linux: `Ctrl+Shift+P`
- MCP サーバーの開始コマンドを実行する
    - 例: `MCP: Start` / `MCP: Start Server`（表示されるコマンド名は環境により異なる）
- 起動時に `MLIT_API_KEY` の入力プロンプトが表示されたら入力する

### EXAMPLE-PROMPTS.md

MCP サーバーを活用したデータ調査・分析を LLM に依頼するためのプロンプトテンプレートである。
「調査内容」セクションを書き換えることで、様々な調査タスクに転用できる。

### プロンプトの構成

| セクション | 内容 |
|-----------|------|
| タスクの目的 | MCP ツール群を活用した調査の実行、結果整理、有効性検証 |
| 調査内容 | 具体的な調査テーマ(例: 東京都中野区中央の避難所) |
| 出力要件 | ディレクトリ構成、記述言語、ファイル命名規則 |
