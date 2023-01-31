# InterSystems　IRIS SQLクックブック

このドキュメントは、InterSystems IRISでSQL文を実行するための基本的な事項や、役に立つヒントを記述しています。

InterSystems IRISをインストールし、基本的な操作方法を習得されている方を想定しています。InterSystems IRISを初めて操作される方や、SQL以外のことについて知りたい方は、[開発者コミュニティの記事](https://jp.community.intersystems.com/node/484466)などを参考にしてください。

## SQL実行の方法
InterSystems IRISでは、いくつかの方法でSQLを実行することができます。ここでは、対話的方法について紹介します。プログラムからSQLを実行する方法については、[クライアントアクセス](#クライアントアクセス)、[サーバでのSQL実行](#サーバでのsql実行)を参照してください。


- ターミナルからSQLシェルを起動する

  InterSystems IRISはターミナルからのアクセスが可能です。

  Windowsでは、IRISキューブから`ターミナル`を選択すると、ターミナルウィンドウが開きます。

  LinuxやMacOSなどその他のOSでは、OSのターミナルを利用します。OSのターミナルから`iris session`コマンドを実行します。引数にはインスタンス名を指定します（以下実行例では"iris"）。


  ```shell
    
    $ iris session iris

    ノード: ec8e008bfccd インスタンス: IRIS

    USER>
  ```

  標準ではUSERネームスペースが作業環境になりますので、必要に応じて、`ZNAMESPACE`コマンド（`ZN`と省略できます）でネームスペースを移動します。

  ```shell

    USER>zn "sqldemo"
    SQLDEMO>

  ```

  ここで、`do $system.SQL.Shell()`コマンドを実行します。
  ```shell
    SQLDEMO>do $system.SQL.Shell()
    SQL Command Line Shell
    ----------------------------------------------------

    The command prefix is currently set to: <<nothing>>.
    Enter <command>, 'q' to quit, '?' for help.
    [SQL]SQLDEMO>>
  ```
  
  このプロンプトからSQL文を実行することができます。SQLシェルの詳細については[ドキュメント](https://docs.intersystems.com/iris20221/csp/docbookj/DocBook.UI.Page.cls?KEY=GSQL_shell#GSQL_shell_executemode)を参照してください。


- 管理ポータル
  
  管理ポータルからSQL文を実行することができます。方法については、[ドキュメント](https://docs.intersystems.com/iris20221/csp/docbookj/DocBook.UI.Page.cls?KEY=GSQL_smp#GSQL_smp_sqlexecute)を参照してください。

- 3rdパーティSQLツール
  
  InterSystems IRISは、JDBC/ODBCアクセスをサポートしていますので、それらのプロトコルを利用している3rdパーティのツールが利用できます。各ツールからInterSystems IRISへの接続については、[クライアントアクセス](#クライアントアクセス)を参照してください。

  また、Visual Studio Codeのエクステンション["SQLTools InterSystems IRIS"](https://marketplace.visualstudio.com/items?itemName=intersystems-community.sqltools-intersystems-driver)を利用すれば、Visual Studio Codeから、InterSystems IRISに接続し、SQLを実行することができます。


## テーブルの作成
テーブルを作成するには、CREATE TABLE文を使用します。次の例は、コード、名称、カナ名の3つのフィールドを持つ都道府県テーブル(Demo.Prefecture)を定義しています。

```sql
CREATE TABLE Demo.Prefecture (
    Code VARCHAR(6),
    Name VARCHAR(20),
    KanaName VARCHAR(50)
)
```

SQLシェルを使った実行例です。SQLシェルでは、SQL文を1行にまとめて実行する必要があることに注意してください。

```shell
[SQL]SQLDEMO>>CREATE TABLE Demo.Prefecture (Code VARCHAR(6), Name VARCHAR(20), KanaName VARCHAR(50))
2.      CREATE TABLE Demo.Prefecture (Code VARCHAR(6), Name VARCHAR(20), KanaName VARCHAR(50))

0 Rows Affected
statement prepare time(s)/globals/cmds/disk: 0.0066s/2,187/21,907/0ms
          execute time(s)/globals/cmds/disk: 0.0906s/67,772/512,672/0ms
                          cached query class: %sqlcq.SQLDEMO.cls27
---------------------------------------------------------------------------
[SQL]SQLDEMO>>
```

IRISでのテーブル名は、

> [スキーマ名] . [テーブル名]

のように、スキーマ名でテーブル名を修飾できます。スキーマ名を省略した場合は、デフォルトで SQLUser というスキーマ名が付加されます。

なお、スキーマ名は、複数の"."を使って階層的に定義することはできません。

CREATE TABLE文の詳細は、[こちら](https://docs.intersystems.com/iris20221/csp/docbookj/DocBook.UI.Page.cls?KEY=RSQL_CREATETABLE)をご覧ください。


クラス定義

## データのロード

SMPウィザード
### LOAD Table
- 結果の確認

## インデックスの作成

## サーバでのSQL実行
  - サーバサイド
    - 埋め込みSQL
    - 動的SQL
    - カスタムクエリ
    - Embedded Pythonによる記述

## クライアントアクセス

## SQL文のテクニック

### 日付

### 文字列

### エラーチェック

### ユーザ定義関数

## パフォーマンス
### クエリプラン

### インデックスの使い分け
### 統計情報
