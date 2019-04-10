---
title: 在 ADO.NET 中修改大量數值 (max) 資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: eb938cfae645a9cc3811f1b5a02cddef742bac89
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317099"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="0cf2e-102">在 ADO.NET 中修改大量數值 (max) 資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="0cf2e-103">大型物件 (LOB) 資料型別是指資料列大小上限超過 8 KB 的資料型別。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="0cf2e-104">SQL Server 可提供 `max`、`varchar` 和 `nvarchar` 資料型別的 `varbinary` 規範，允許儲存最大達 2^32 位元組的值。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="0cf2e-105">資料表資料行及 Transact-SQL 變數可指定 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 資料型別。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="0cf2e-106">在 ADO.NET 中，`max` 資料型別可透過 `DataReader` 來擷取，也可指定為輸入及輸出參數值，並且不需要任何特殊處理。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="0cf2e-107">對於大型 `varchar` 資料型別，可透過遞增方式擷取及更新資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="0cf2e-108">`max` 資料型別可用於比較 (做為 Transact-SQL 變數) 及串連。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="0cf2e-109">它們也可用於 SELECT 陳述式的 DISTINCT、ORDER BY、GROUP BY 子句，以及彙總、聯結 (Join) 及子查詢中。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="0cf2e-110">下表將提供《SQL Server 線上叢書》中相關文件的連結。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 **<span data-ttu-id="0cf2e-111">SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="0cf2e-111">SQL Server Books Online</span></span>**  
  
1. [<span data-ttu-id="0cf2e-112">使用大數值資料類型</span><span class="sxs-lookup"><span data-stu-id="0cf2e-112">Using Large-Value Data Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="0cf2e-113">大數值型別限制</span><span class="sxs-lookup"><span data-stu-id="0cf2e-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="0cf2e-114">下列限制適用於 `max` 資料型別，而小型資料型別則沒有這些限制：</span><span class="sxs-lookup"><span data-stu-id="0cf2e-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
-   <span data-ttu-id="0cf2e-115">`sql_variant` 不可包含大型 `varchar` 資料型別。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
-   <span data-ttu-id="0cf2e-116">大型 `varchar` 資料行不可指定為索引中的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="0cf2e-117">而在非叢集索引的內含資料行中，則允許有大型資料行。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
-   <span data-ttu-id="0cf2e-118">大型 `varchar` 資料行不可用做分割索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="0cf2e-119">在 Transact-SQL 中使用大數值型別</span><span class="sxs-lookup"><span data-stu-id="0cf2e-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="0cf2e-120">Transact-SQL `OPENROWSET` 函式是連接及存取遠端資料的一次性方法。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="0cf2e-121">其包括從 OLE DB 資料來源存取遠端資料時所需的所有連接資訊。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> `OPENROWSET` <span data-ttu-id="0cf2e-122">可參考查詢的 FROM 子句中資料表名稱般。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-122">can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="0cf2e-123">此外，它也可參考為 INSERT、UPDATE 或 DELETE 陳述式的目標資料表，但會受到 OLE DB 提供者的功能影響。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="0cf2e-124">`OPENROWSET` 函式包含 `BULK` 資料列集提供者，可讓您直接從檔案讀取資料，不需將資料載入目標資料表中。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="0cf2e-125">這可讓您在簡單的 INSERT SELECT 陳述式中使用 `OPENROWSET`。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="0cf2e-126">`OPENROWSET BULK`選項引數可有效地控制何處開始及結束讀取資料、 如何處理錯誤，以及如何解譯資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="0cf2e-127">例如，您可以指定將資料檔案讀取為具有型別 `varbinary`、`varchar` 或 `nvarchar` 的單一資料列及單一資料行資料列集。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="0cf2e-128">如需完整的語法及選項，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="0cf2e-129">下列範例會將相片插入 AdventureWorks 範例資料庫中的 ProductPhoto 資料表。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="0cf2e-130">當使用`BULK OPENROWSET`提供者，您必須提供偶數的資料行的具名的清單，如果您未將值插入每個資料行。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="0cf2e-131">在此情況下，將主索引鍵定義為識別欄位，也可從資料行清單省略。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="0cf2e-132">請注意，您還必須提供關聯名稱，將其置於 `OPENROWSET` 陳述式的結尾處 (此情況中為 ThumbnailPhoto)。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="0cf2e-133">這會與要載入檔案之 `ProductPhoto` 資料表中的資料行關聯。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="0cf2e-134">使用 UPDATE .WRITE 更新資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="0cf2e-135">Transact-SQL UPDATE 陳述式具有新的 WRITE 語法，它可用來修改 `varchar(max)`、`nvarchar(max)` 或 `varbinary(max)` 資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="0cf2e-136">這允許您對資料進行部分更新。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="0cf2e-137">下面所示為簡略形式的 UPDATE .WRITE 語法：</span><span class="sxs-lookup"><span data-stu-id="0cf2e-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="0cf2e-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="0cf2e-138">UPDATE</span></span>  
  
 <span data-ttu-id="0cf2e-139">{ *\<object>* }</span><span class="sxs-lookup"><span data-stu-id="0cf2e-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="0cf2e-140">SET</span><span class="sxs-lookup"><span data-stu-id="0cf2e-140">SET</span></span>  
  
 <span data-ttu-id="0cf2e-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span><span class="sxs-lookup"><span data-stu-id="0cf2e-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="0cf2e-142">WRITE 方法指定的值的一個區段*column_name*將予修改。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="0cf2e-143">運算式是值，將會複製到*column_name*，則`@Offset`是要寫入的運算式的起點和`@Length`引數是資料行中區段的長度。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="0cf2e-144">如果</span><span class="sxs-lookup"><span data-stu-id="0cf2e-144">If</span></span>|<span data-ttu-id="0cf2e-145">然後</span><span class="sxs-lookup"><span data-stu-id="0cf2e-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="0cf2e-146">運算式設為 NULL</span><span class="sxs-lookup"><span data-stu-id="0cf2e-146">The expression is set to NULL</span></span>|`@Length` <span data-ttu-id="0cf2e-147">會忽略與中的值*column_name*截斷指定`@Offset`。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-147">is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|`@Offset` <span data-ttu-id="0cf2e-148">為 NULL</span><span class="sxs-lookup"><span data-stu-id="0cf2e-148">is NULL</span></span>|<span data-ttu-id="0cf2e-149">更新作業將附加至結尾的現有運算式*column_name*值並`@Length`會被忽略。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|`@Offset` <span data-ttu-id="0cf2e-150">大於 column_name 值的長度</span><span class="sxs-lookup"><span data-stu-id="0cf2e-150">is greater than the length of the column_name value</span></span>|<span data-ttu-id="0cf2e-151">SQL Server 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-151">SQL Server returns an error.</span></span>|  
|`@Length` <span data-ttu-id="0cf2e-152">為 NULL</span><span class="sxs-lookup"><span data-stu-id="0cf2e-152">is NULL</span></span>|<span data-ttu-id="0cf2e-153">更新作業會移除從 `@Offset` 到 `column_name` 值結尾的所有資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0cf2e-154">`@Offset` 及 `@Length` 都不可為負數。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cf2e-155">範例</span><span class="sxs-lookup"><span data-stu-id="0cf2e-155">Example</span></span>  
 <span data-ttu-id="0cf2e-156">此 Transact-SQL 範例會更新 DocumentSummary 中的部分值，其為 AdventureWorks 資料庫中 Document 資料表內的 `nvarchar(max)` 資料行。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="0cf2e-157">藉由指定取代單字、現有資料中要取代之單字的開始位置 (位移)，以及要取代的字元數 (長度)，將 components 這個字取代為 features 這個字。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="0cf2e-158">該範例會將 SELECT 陳述式併入到 UPDATE 陳述式之前與之後來比較結果。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```  
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="0cf2e-159">在 ADO.NET 中使用大數值型別</span><span class="sxs-lookup"><span data-stu-id="0cf2e-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="0cf2e-160">您可以使用 ADO.NET 中的大型值型別指定為大型值型別<xref:System.Data.SqlClient.SqlParameter>中的物件<xref:System.Data.SqlClient.SqlDataReader>才會傳回結果集，或使用<xref:System.Data.SqlClient.SqlDataAdapter>填滿`DataSet` / `DataTable`。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="0cf2e-161">大型值型別與其相關的小型值資料型別在使用方式上並無差異。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="0cf2e-162">使用 GetSqlBytes 擷取資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="0cf2e-163">`GetSqlBytes` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用於擷取 `varbinary(max)` 資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="0cf2e-164">下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 物件會從資料表選取 `varbinary(max)` 資料；名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會以 <xref:System.Data.SqlTypes.SqlBytes> 形式擷取資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="0cf2e-165">使用 GetSqlChars 擷取資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="0cf2e-166">`GetSqlChars` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用於擷取 `varchar(max)` 或 `nvarchar(max)` 資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="0cf2e-167">下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 物件會從資料表選取 `nvarchar(max)` 資料；名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會擷取資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="0cf2e-168">使用 GetSqlBinary 擷取資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="0cf2e-169">`GetSqlBinary` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可用於擷取 `varbinary(max)` 資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="0cf2e-170">下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlCommand> 的 `cmd` 物件會從資料表選取 `varbinary(max)` 資料；名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會以 <xref:System.Data.SqlTypes.SqlBinary> 資料流形式擷取資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="0cf2e-171">使用 GetBytes 擷取資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="0cf2e-172">`GetBytes` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可將位元組資料流，從指定的資料行位移讀取到在指定陣列位移處開始的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="0cf2e-173">下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會將位元組擷取到位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="0cf2e-174">請注意，`GetSqlBytes` 與 `GetBytes` 不同，其需要一定大小的陣列緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="0cf2e-175">使用 GetValue 擷取資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="0cf2e-176">`GetValue` 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可將值從指定的資料行位移讀取到陣列中。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="0cf2e-177">下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會從第一個資料行位移擷取二進位資料，然後從第二個資料行位移擷取字串資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="0cf2e-178">從大型值型別轉換為 CLR 型別</span><span class="sxs-lookup"><span data-stu-id="0cf2e-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="0cf2e-179">您可以使用任何字串轉換方法 (如 `varchar(max)`)，來轉換 `nvarchar(max)` 或 `ToString` 資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="0cf2e-180">下列程式碼片段假設名為 <xref:System.Data.SqlClient.SqlDataReader> 的 `reader` 物件會擷取資料。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="0cf2e-181">範例</span><span class="sxs-lookup"><span data-stu-id="0cf2e-181">Example</span></span>  
 <span data-ttu-id="0cf2e-182">下列程式碼會從 `LargePhoto` 資料庫中的 `ProductPhoto` 資料表擷取名稱及 `AdventureWorks` 物件，並將其儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="0cf2e-183">組件 (Assembly) 需要參考 <xref:System.Drawing> 命名空間 (Namespace) 才能進行編譯。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="0cf2e-184"><xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> 的 <xref:System.Data.SqlClient.SqlDataReader> 方法會傳回 <xref:System.Data.SqlTypes.SqlBytes> 物件，其會公開 `Stream` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="0cf2e-185">程式碼所使用的是這來建立新`Bitmap`物件，然後再將它儲存在 Gif `ImageFormat`。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="0cf2e-186">使用大型值型別參數</span><span class="sxs-lookup"><span data-stu-id="0cf2e-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="0cf2e-187">大型值型別可用於 <xref:System.Data.SqlClient.SqlParameter> 物件，其使用方式與在 <xref:System.Data.SqlClient.SqlParameter> 物件中使用小型值型別相同。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="0cf2e-188">您可以擷取大數值類型為<xref:System.Data.SqlClient.SqlParameter>值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="0cf2e-189">該程式碼假設下列 GetDocumentSummary 預存程序存在於 AdventureWorks 範例資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="0cf2e-190">預存程序會採用名為輸入的參數@DocumentID並傳回 DocumentSummary 資料行中的內容@DocumentSummary輸出參數。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```  
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="0cf2e-191">範例</span><span class="sxs-lookup"><span data-stu-id="0cf2e-191">Example</span></span>  
 <span data-ttu-id="0cf2e-192">ADO.NET 程式碼會建立 <xref:System.Data.SqlClient.SqlConnection> 及 <xref:System.Data.SqlClient.SqlCommand> 物件來執行 GetDocumentSummary 預存程序並擷取文件摘要 (以大型值型別儲存)。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="0cf2e-193">程式碼會將值傳遞@DocumentID輸入參數，並顯示結果傳回到@DocumentSummary輸出在主控台視窗中的參數。</span><span class="sxs-lookup"><span data-stu-id="0cf2e-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0cf2e-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cf2e-194">See also</span></span>

- [<span data-ttu-id="0cf2e-195">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="0cf2e-195">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="0cf2e-196">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="0cf2e-196">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="0cf2e-197">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="0cf2e-197">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [<span data-ttu-id="0cf2e-198">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0cf2e-198">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
