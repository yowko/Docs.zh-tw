---
title: 中繼資料
ms.date: 12/13/2019
description: 瞭解如何取得資料庫的相關中繼資料。
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447192"
---
# <a name="metadata"></a>中繼資料

有兩個 Api 可用於在 ADO.NET 中抓取中繼資料。 其中一個會抓取有關查詢結果的中繼資料。 另一個則會抓取有關資料庫架構的中繼資料。

## <a name="query-result-metadata"></a>查詢結果中繼資料

您可以在 `SqliteDataReader`上使用 <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> 方法，來抓取有關查詢結果的中繼資料。 傳回的 <xref:System.Data.DataTable> 包含下列資料行：

| 資料行             | 類型    | 描述                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | Boolean | 如果來源資料行可為 Null，則為 True。                                    |
| `BaseCatalogName`  | 字串  | 來源資料行的資料庫名稱。 運算式的一律為 Null。    |
| `BaseColumnName`   | 字串  | 原始資料行的 unaliased 名稱。 運算式的一律為 Null。    |
| `BaseSchemaName`   | 字串  | 一律為 Null。 SQLite 不支援架構。                              |
| `BaseServerName`   | 字串  | 連接字串中指定之資料庫檔案的路徑。         |
| `BaseTableName`    | 字串  | 原始資料行的資料表名稱。 運算式的一律為 Null。       |
| `ColumnName`       | 字串  | 結果集中資料行的名稱或別名。                        |
| `ColumnOrdinal`    | Int32   | 結果集中資料行的序數。                              |
| `ColumnSize`       | Int32   | 一律為-1。 這可能會在 `Microsoft.Data.Sqlite`的未來版本中變更。   |
| `DataType`         | 類型    | 資料行的預設 .NET 資料類型。                                 |
| `DataTypeName`     | 字串  | 資料行的 SQLite 資料類型。                                       |
| `IsAliased`        | Boolean | 如果資料行名稱在結果集中為別名，則為 True。                     |
| `IsAutoIncrement`  | Boolean | 如果來源資料行是使用自動遞增關鍵字所建立，則為 True。     |
| `IsExpression`     | Boolean | 如果資料行來自查詢中的運算式，則為 True。            |
| `IsKey`            | Boolean | 如果來源資料行是主要索引鍵的一部分，則為 True。                     |
| `IsUnique`         | Boolean | 如果來源資料行是唯一的，則為 True。                                      |
| `NumericPrecision` | Int16   | 一律為 Null。 這可能會在 `Microsoft.Data.Sqlite`的未來版本中變更。 |
| `NumericScale`     | Int16   | 一律為 Null。 這可能會在 `Microsoft.Data.Sqlite`的未來版本中變更。 |

下列範例示範如何使用 `GetSchemaTable` 來建立會顯示結果相關中繼資料的 debug 字串：

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

例如，此查詢會產生下列的 debug 字串：

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a>架構中繼資料

GetSchema 方法不會在 DbConnection 上執行。 相反地，您可以使用[sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)資料表和 PRAGMA 語句（例如[table_info](https://www.sqlite.org/pragma.html#pragma_table_info)和[foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list)）直接查詢架構資訊。

例如，此查詢將會抓取資料庫中所有資料行的相關中繼資料。

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a>請參閱

* [SQL Database 架構的儲存體](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [PRAGMA 語句](https://www.sqlite.org/pragma.html)
* [資料類型](types.md)
