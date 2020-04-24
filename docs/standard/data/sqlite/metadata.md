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
# <a name="metadata"></a><span data-ttu-id="47084-103">中繼資料</span><span class="sxs-lookup"><span data-stu-id="47084-103">Metadata</span></span>

<span data-ttu-id="47084-104">有兩個 Api 可用於在 ADO.NET 中抓取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="47084-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="47084-105">其中一個會抓取有關查詢結果的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="47084-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="47084-106">另一個則會抓取有關資料庫架構的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="47084-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="47084-107">查詢結果中繼資料</span><span class="sxs-lookup"><span data-stu-id="47084-107">Query result metadata</span></span>

<span data-ttu-id="47084-108">您可以使用上<xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> `SqliteDataReader`的方法，來抓取有關查詢結果的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="47084-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="47084-109">傳回<xref:System.Data.DataTable>的包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="47084-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="47084-110">資料行</span><span class="sxs-lookup"><span data-stu-id="47084-110">Column</span></span>             | <span data-ttu-id="47084-111">類型</span><span class="sxs-lookup"><span data-stu-id="47084-111">Type</span></span>    | <span data-ttu-id="47084-112">說明</span><span class="sxs-lookup"><span data-stu-id="47084-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="47084-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="47084-113">Boolean</span></span> | <span data-ttu-id="47084-114">如果來源資料行可為 Null，則為 True。</span><span class="sxs-lookup"><span data-stu-id="47084-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="47084-115">String</span><span class="sxs-lookup"><span data-stu-id="47084-115">String</span></span>  | <span data-ttu-id="47084-116">來源資料行的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="47084-116">The name of the origin column's database.</span></span> <span data-ttu-id="47084-117">運算式的一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="47084-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="47084-118">String</span><span class="sxs-lookup"><span data-stu-id="47084-118">String</span></span>  | <span data-ttu-id="47084-119">原始資料行的 unaliased 名稱。</span><span class="sxs-lookup"><span data-stu-id="47084-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="47084-120">運算式的一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="47084-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="47084-121">String</span><span class="sxs-lookup"><span data-stu-id="47084-121">String</span></span>  | <span data-ttu-id="47084-122">一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="47084-122">Always NULL.</span></span> <span data-ttu-id="47084-123">SQLite 不支援架構。</span><span class="sxs-lookup"><span data-stu-id="47084-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="47084-124">String</span><span class="sxs-lookup"><span data-stu-id="47084-124">String</span></span>  | <span data-ttu-id="47084-125">連接字串中指定之資料庫檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="47084-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="47084-126">String</span><span class="sxs-lookup"><span data-stu-id="47084-126">String</span></span>  | <span data-ttu-id="47084-127">原始資料行的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="47084-127">The name of the origin column's table.</span></span> <span data-ttu-id="47084-128">運算式的一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="47084-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="47084-129">String</span><span class="sxs-lookup"><span data-stu-id="47084-129">String</span></span>  | <span data-ttu-id="47084-130">結果集中資料行的名稱或別名。</span><span class="sxs-lookup"><span data-stu-id="47084-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="47084-131">Int32</span><span class="sxs-lookup"><span data-stu-id="47084-131">Int32</span></span>   | <span data-ttu-id="47084-132">結果集中資料行的序數。</span><span class="sxs-lookup"><span data-stu-id="47084-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="47084-133">Int32</span><span class="sxs-lookup"><span data-stu-id="47084-133">Int32</span></span>   | <span data-ttu-id="47084-134">一律為-1。</span><span class="sxs-lookup"><span data-stu-id="47084-134">Always -1.</span></span> <span data-ttu-id="47084-135">這在未來的`Microsoft.Data.Sqlite`版本中可能會變更。</span><span class="sxs-lookup"><span data-stu-id="47084-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="47084-136">類型</span><span class="sxs-lookup"><span data-stu-id="47084-136">Type</span></span>    | <span data-ttu-id="47084-137">資料行的預設 .NET 資料類型。</span><span class="sxs-lookup"><span data-stu-id="47084-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="47084-138">String</span><span class="sxs-lookup"><span data-stu-id="47084-138">String</span></span>  | <span data-ttu-id="47084-139">資料行的 SQLite 資料類型。</span><span class="sxs-lookup"><span data-stu-id="47084-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="47084-140">Boolean</span><span class="sxs-lookup"><span data-stu-id="47084-140">Boolean</span></span> | <span data-ttu-id="47084-141">如果資料行名稱在結果集中為別名，則為 True。</span><span class="sxs-lookup"><span data-stu-id="47084-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="47084-142">Boolean</span><span class="sxs-lookup"><span data-stu-id="47084-142">Boolean</span></span> | <span data-ttu-id="47084-143">如果來源資料行是使用自動遞增關鍵字所建立，則為 True。</span><span class="sxs-lookup"><span data-stu-id="47084-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="47084-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="47084-144">Boolean</span></span> | <span data-ttu-id="47084-145">如果資料行來自查詢中的運算式，則為 True。</span><span class="sxs-lookup"><span data-stu-id="47084-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="47084-146">Boolean</span><span class="sxs-lookup"><span data-stu-id="47084-146">Boolean</span></span> | <span data-ttu-id="47084-147">如果來源資料行是主要索引鍵的一部分，則為 True。</span><span class="sxs-lookup"><span data-stu-id="47084-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="47084-148">Boolean</span><span class="sxs-lookup"><span data-stu-id="47084-148">Boolean</span></span> | <span data-ttu-id="47084-149">如果來源資料行是唯一的，則為 True。</span><span class="sxs-lookup"><span data-stu-id="47084-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="47084-150">Int16</span><span class="sxs-lookup"><span data-stu-id="47084-150">Int16</span></span>   | <span data-ttu-id="47084-151">一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="47084-151">Always NULL.</span></span> <span data-ttu-id="47084-152">這在未來的`Microsoft.Data.Sqlite`版本中可能會變更。</span><span class="sxs-lookup"><span data-stu-id="47084-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="47084-153">Int16</span><span class="sxs-lookup"><span data-stu-id="47084-153">Int16</span></span>   | <span data-ttu-id="47084-154">一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="47084-154">Always NULL.</span></span> <span data-ttu-id="47084-155">這在未來的`Microsoft.Data.Sqlite`版本中可能會變更。</span><span class="sxs-lookup"><span data-stu-id="47084-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="47084-156">下列範例示範如何使用`GetSchemaTable`來建立會顯示結果相關中繼資料的 debug 字串：</span><span class="sxs-lookup"><span data-stu-id="47084-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="47084-157">例如，此查詢會產生下列的 debug 字串：</span><span class="sxs-lookup"><span data-stu-id="47084-157">For example, this query would produce the following debug string:</span></span>

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

## <a name="schema-metadata"></a><span data-ttu-id="47084-158">架構中繼資料</span><span class="sxs-lookup"><span data-stu-id="47084-158">Schema metadata</span></span>

<span data-ttu-id="47084-159">GetSchema 方法不會在 DbConnection 上執行。</span><span class="sxs-lookup"><span data-stu-id="47084-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="47084-160">相反地，您可以使用[sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)資料表和 PRAGMA 語句（例如[table_info](https://www.sqlite.org/pragma.html#pragma_table_info)和[foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list)）直接查詢架構資訊。</span><span class="sxs-lookup"><span data-stu-id="47084-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="47084-161">例如，此查詢將會抓取資料庫中所有資料行的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="47084-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="47084-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47084-162">See also</span></span>

* [<span data-ttu-id="47084-163">SQL Database 架構的儲存體</span><span class="sxs-lookup"><span data-stu-id="47084-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="47084-164">PRAGMA 語句</span><span class="sxs-lookup"><span data-stu-id="47084-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="47084-165">資料類型</span><span class="sxs-lookup"><span data-stu-id="47084-165">Data types</span></span>](types.md)
