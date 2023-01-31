# InterSystemsIRIS SQLクックブック

## SQL実行の方法
InterSystems IRISでは、いくつかの方法でSQLを実行することができます。ここでは、対話的方法について紹介します。プログラムからSQLを実行する方法については、[クライアントアクセス](#クライアントアクセス)、[サーバでのSQL実行](#サーバでのsql実行)を参照してください。


- ターミナルから$system.SQL.Shell()を起動する

  InterSystems IRISはターミナルからのアクセスが可能です。

  Windowsでは、IRISキューブから`ターミナル`を選択すると、ターミナルウィンドウが開きます。

  LinuxやMacOSなどその他のOSでは、OSのターミナルを利用します。OSのターミナルからirisコマンドを実行します。ここで最後の"iris"はインスタンス名です。


  ```shell
    
    **iris session iris**

    ノード: ec8e008bfccd インスタンス: IRIS

    USER>
  ```

  

    ```shell
    SQLDEMO>do $system.SQL.Shell()
    SQL Command Line Shell
    ----------------------------------------------------

    The command prefix is currently set to: <<nothing>>.
    Enter <command>, 'q' to quit, '?' for help.
    [SQL]SQLDEMO>>
    ```

- 管理ポータル
- 3rdパーティSQLツール



## テーブルの作成
テーブルを作成するには、CREATE TABLE文を使用します。次の例は、コード、名称、カナ名の3つのフィールドを持つ都道府県テーブル(Demo.Prewfecture)を定義しています。

```sql
CREATE TABLE Demo.Prefecture (
    Code VARCHAR(6),
    Name VARCHAR(20),
    KanaName VARCHAR(50)
)
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
