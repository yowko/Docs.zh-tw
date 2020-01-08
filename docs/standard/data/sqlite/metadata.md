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
# <a name="metadata"></a><span data-ttu-id="be564-103">中繼資料</span><span class="sxs-lookup"><span data-stu-id="be564-103">Metadata</span></span>

<span data-ttu-id="be564-104">有兩個 Api 可用於在 ADO.NET 中抓取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="be564-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="be564-105">其中一個會抓取有關查詢結果的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="be564-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="be564-106">另一個則會抓取有關資料庫架構的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="be564-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="be564-107">查詢結果中繼資料</span><span class="sxs-lookup"><span data-stu-id="be564-107">Query result metadata</span></span>

<span data-ttu-id="be564-108">您可以在 `SqliteDataReader`上使用 <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> 方法，來抓取有關查詢結果的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="be564-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="be564-109">傳回的 <xref:System.Data.DataTable> 包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="be564-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="be564-110">資料行</span><span class="sxs-lookup"><span data-stu-id="be564-110">Column</span></span>             | <span data-ttu-id="be564-111">類型</span><span class="sxs-lookup"><span data-stu-id="be564-111">Type</span></span>    | <span data-ttu-id="be564-112">描述</span><span class="sxs-lookup"><span data-stu-id="be564-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="be564-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="be564-113">Boolean</span></span> | <span data-ttu-id="be564-114">如果來源資料行可為 Null，則為 True。</span><span class="sxs-lookup"><span data-stu-id="be564-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="be564-115">字串</span><span class="sxs-lookup"><span data-stu-id="be564-115">String</span></span>  | <span data-ttu-id="be564-116">來源資料行的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="be564-116">The name of the origin column's database.</span></span> <span data-ttu-id="be564-117">運算式的一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="be564-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="be564-118">字串</span><span class="sxs-lookup"><span data-stu-id="be564-118">String</span></span>  | <span data-ttu-id="be564-119">原始資料行的 unaliased 名稱。</span><span class="sxs-lookup"><span data-stu-id="be564-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="be564-120">運算式的一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="be564-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="be564-121">字串</span><span class="sxs-lookup"><span data-stu-id="be564-121">String</span></span>  | <span data-ttu-id="be564-122">一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="be564-122">Always NULL.</span></span> <span data-ttu-id="be564-123">SQLite 不支援架構。</span><span class="sxs-lookup"><span data-stu-id="be564-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="be564-124">字串</span><span class="sxs-lookup"><span data-stu-id="be564-124">String</span></span>  | <span data-ttu-id="be564-125">連接字串中指定之資料庫檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="be564-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="be564-126">字串</span><span class="sxs-lookup"><span data-stu-id="be564-126">String</span></span>  | <span data-ttu-id="be564-127">原始資料行的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="be564-127">The name of the origin column's table.</span></span> <span data-ttu-id="be564-128">運算式的一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="be564-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="be564-129">字串</span><span class="sxs-lookup"><span data-stu-id="be564-129">String</span></span>  | <span data-ttu-id="be564-130">結果集中資料行的名稱或別名。</span><span class="sxs-lookup"><span data-stu-id="be564-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="be564-131">Int32</span><span class="sxs-lookup"><span data-stu-id="be564-131">Int32</span></span>   | <span data-ttu-id="be564-132">結果集中資料行的序數。</span><span class="sxs-lookup"><span data-stu-id="be564-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="be564-133">Int32</span><span class="sxs-lookup"><span data-stu-id="be564-133">Int32</span></span>   | <span data-ttu-id="be564-134">一律為-1。</span><span class="sxs-lookup"><span data-stu-id="be564-134">Always -1.</span></span> <span data-ttu-id="be564-135">這可能會在 `Microsoft.Data.Sqlite`的未來版本中變更。</span><span class="sxs-lookup"><span data-stu-id="be564-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="be564-136">類型</span><span class="sxs-lookup"><span data-stu-id="be564-136">Type</span></span>    | <span data-ttu-id="be564-137">資料行的預設 .NET 資料類型。</span><span class="sxs-lookup"><span data-stu-id="be564-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="be564-138">字串</span><span class="sxs-lookup"><span data-stu-id="be564-138">String</span></span>  | <span data-ttu-id="be564-139">資料行的 SQLite 資料類型。</span><span class="sxs-lookup"><span data-stu-id="be564-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="be564-140">Boolean</span><span class="sxs-lookup"><span data-stu-id="be564-140">Boolean</span></span> | <span data-ttu-id="be564-141">如果資料行名稱在結果集中為別名，則為 True。</span><span class="sxs-lookup"><span data-stu-id="be564-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="be564-142">Boolean</span><span class="sxs-lookup"><span data-stu-id="be564-142">Boolean</span></span> | <span data-ttu-id="be564-143">如果來源資料行是使用自動遞增關鍵字所建立，則為 True。</span><span class="sxs-lookup"><span data-stu-id="be564-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="be564-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="be564-144">Boolean</span></span> | <span data-ttu-id="be564-145">如果資料行來自查詢中的運算式，則為 True。</span><span class="sxs-lookup"><span data-stu-id="be564-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="be564-146">Boolean</span><span class="sxs-lookup"><span data-stu-id="be564-146">Boolean</span></span> | <span data-ttu-id="be564-147">如果來源資料行是主要索引鍵的一部分，則為 True。</span><span class="sxs-lookup"><span data-stu-id="be564-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="be564-148">Boolean</span><span class="sxs-lookup"><span data-stu-id="be564-148">Boolean</span></span> | <span data-ttu-id="be564-149">如果來源資料行是唯一的，則為 True。</span><span class="sxs-lookup"><span data-stu-id="be564-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="be564-150">Int16</span><span class="sxs-lookup"><span data-stu-id="be564-150">Int16</span></span>   | <span data-ttu-id="be564-151">一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="be564-151">Always NULL.</span></span> <span data-ttu-id="be564-152">這可能會在 `Microsoft.Data.Sqlite`的未來版本中變更。</span><span class="sxs-lookup"><span data-stu-id="be564-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="be564-153">Int16</span><span class="sxs-lookup"><span data-stu-id="be564-153">Int16</span></span>   | <span data-ttu-id="be564-154">一律為 Null。</span><span class="sxs-lookup"><span data-stu-id="be564-154">Always NULL.</span></span> <span data-ttu-id="be564-155">這可能會在 `Microsoft.Data.Sqlite`的未來版本中變更。</span><span class="sxs-lookup"><span data-stu-id="be564-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="be564-156">下列範例示範如何使用 `GetSchemaTable` 來建立會顯示結果相關中繼資料的 debug 字串：</span><span class="sxs-lookup"><span data-stu-id="be564-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="be564-157">例如，此查詢會產生下列的 debug 字串：</span><span class="sxs-lookup"><span data-stu-id="be564-157">For example, this query would produce the following debug string:</span></span>

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

## <a name="schema-metadata"></a><span data-ttu-id="be564-158">架構中繼資料</span><span class="sxs-lookup"><span data-stu-id="be564-158">Schema metadata</span></span>

<span data-ttu-id="be564-159">GetSchema 方法不會在 DbConnection 上執行。</span><span class="sxs-lookup"><span data-stu-id="be564-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="be564-160">相反地，您可以使用[sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)資料表和 PRAGMA 語句（例如[table_info](https://www.sqlite.org/pragma.html#pragma_table_info)和[foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list)）直接查詢架構資訊。</span><span class="sxs-lookup"><span data-stu-id="be564-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="be564-161">例如，此查詢將會抓取資料庫中所有資料行的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="be564-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="be564-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="be564-162">See also</span></span>

* [<span data-ttu-id="be564-163">SQL Database 架構的儲存體</span><span class="sxs-lookup"><span data-stu-id="be564-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="be564-164">PRAGMA 語句</span><span class="sxs-lookup"><span data-stu-id="be564-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="be564-165">資料類型</span><span class="sxs-lookup"><span data-stu-id="be564-165">Data types</span></span>](types.md)
