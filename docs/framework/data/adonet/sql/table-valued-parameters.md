---
title: 資料表值參數
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 2917a8d9b42d831566855271a2f2110637db586f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174468"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="dfdcf-102">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="dfdcf-102">Table-Valued Parameters</span></span>
<span data-ttu-id="dfdcf-103">資料表值參數提供從用戶端應用程式，將多個資料列的資料封送至 SQL Sever 的簡便方式，而不需多次來回存取或特殊的伺服器端邏輯才能處理資料。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="dfdcf-104">您可以使用資料表值參數，以一個參數化命令在用戶端應用程式中封裝資料列的資料，並傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="dfdcf-105">傳入的資料列會儲存於資料表變數中，之後可使用 Transact-SQL 進行運算。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="dfdcf-106">資料表值參數中的資料行值可透過標準的 Transact-SQL SELECT 陳述式加以存取。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="dfdcf-107">資料表值參數為強型別參數，其結構會自動驗證。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="dfdcf-108">資料表值參數的大小只受限於伺服器記憶體。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfdcf-109">您無法以資料表值參數傳回資料。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="dfdcf-110">資料表值參數是僅限輸入；不支援 OUTPUT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="dfdcf-111">如需有關資料表值參數的詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="dfdcf-112">資源</span><span class="sxs-lookup"><span data-stu-id="dfdcf-112">Resource</span></span>|<span data-ttu-id="dfdcf-113">描述</span><span class="sxs-lookup"><span data-stu-id="dfdcf-113">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="dfdcf-114">使用資料表值參數 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="dfdcf-114">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="dfdcf-115">描述如何建立及使用資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="dfdcf-116">[使用者定義的表類型](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="dfdcf-116">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="dfdcf-117">說明用來宣告資料表值參數的使用者定義資料表類型。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="dfdcf-118">在舊版 SQL Server 中傳遞多個資料列</span><span class="sxs-lookup"><span data-stu-id="dfdcf-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="dfdcf-119">在 SQL Server 2008 中引進資料表值參數之前，將多個資料列傳遞至預存程序或參數化 SQL 命令的選項有所限制。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="dfdcf-120">開發人員可以從下列選項中選擇將多個資料列傳遞至伺服器的方式：</span><span class="sxs-lookup"><span data-stu-id="dfdcf-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="dfdcf-121">使用一系列的個別參數來代表多個資料行與資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="dfdcf-122">使用這個方法時，可以傳遞的資料量會受到允許的參數數目限制。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="dfdcf-123">SQL Server 程序最多可以有 2100 個參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="dfdcf-124">需要伺服器端邏輯，才能將這些個別的值組合成資料表變數或暫存資料表來進行處理。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="dfdcf-125">將多個資料值組合成分隔字串或 XML 文件，然後將那些文字值傳遞給程序或陳述式。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="dfdcf-126">這需要程序或陳述式包含驗證資料結構及拆開值所需的邏輯。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="dfdcf-127">針對會影響多個資料列的資料修改建立一系列的獨立 SQL 陳述式，例如透過呼叫 <xref:System.Data.SqlClient.SqlDataAdapter> 的 `Update` 方法所建立的陳述式。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="dfdcf-128">變更可以以個別方式，或以批次處理成群組的方式提交給伺服器。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="dfdcf-129">不過，即使是以包含多個陳述式的批次方式提交，每個陳述式都會在伺服器上個別執行。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="dfdcf-130">使用 `bcp` 公用程式或 <xref:System.Data.SqlClient.SqlBulkCopy> 物件，將許多資料列載入至資料表。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="dfdcf-131">雖然此技術非常有效率，但除非將資料載入暫存資料表或資料表變數中，否則不支援伺服器端處理。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="dfdcf-132">建立資料表值參數型別</span><span class="sxs-lookup"><span data-stu-id="dfdcf-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="dfdcf-133">資料表值參數是以使用 Transact-SQL CREATE TYPE 陳述式所定義的強型別資料表結構為基礎。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-133">Table-valued parameters are based on strongly-typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="dfdcf-134">您必須先在 SQL Server 中建立資料表類型並定義此結構，然後才能在用戶端應用程式中使用資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="dfdcf-135">有關創建表類型的詳細資訊，請參閱[使用者定義的表類型](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-135">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="dfdcf-136">下列陳述式會建立名為 CategoryTableType 的資料表類型，其中包含 CategoryID 與 CategoryName 資料行：</span><span class="sxs-lookup"><span data-stu-id="dfdcf-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="dfdcf-137">建立資料表類型之後，您可以根據該類型來宣告資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="dfdcf-138">下列 Transact-SQL 片段將示範如何在預存程序定義中宣告資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="dfdcf-139">請注意，必須要有 READONLY 關鍵字才能宣告資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="dfdcf-140">使用資料表值參數 &#40;transact-SQL&#41; 修改資料</span><span class="sxs-lookup"><span data-stu-id="dfdcf-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="dfdcf-141">資料表值參數可透過執行單一陳述式，在以集合為基礎且會影響多個資料列的資料修改中使用。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="dfdcf-142">例如，您可以選取資料表值參數中的所有資料列，並將其插入資料庫資料表中，或者您可以透過將資料表值參數聯結至您要更新的資料表，以建立更新陳述式。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="dfdcf-143">下列 Transact-SQL UPDATE 陳述式會示範如何將資料表值參數聯結至 Categories 資料表，藉以運用此參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="dfdcf-144">當您在 FROM 子句中搭配 JOIN 使用資料表值參數時，也必須為其設定別名，例如下方所示，其中資料表值參數設定別名 "ec"：</span><span class="sxs-lookup"><span data-stu-id="dfdcf-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="dfdcf-145">這個 Transact-SQL 範例將示範如何從資料表值參數中選取資料列，以便在單一集合式作業中執行 INSERT。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="dfdcf-146">資料表值參數的限制</span><span class="sxs-lookup"><span data-stu-id="dfdcf-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="dfdcf-147">資料表值參數有幾項限制：</span><span class="sxs-lookup"><span data-stu-id="dfdcf-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="dfdcf-148">您無法將資料表值參數傳遞至 [CLR 使用者定義函式](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="dfdcf-149">資料表值參數只能編製索引，以支援 UNIQUE 或 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="dfdcf-150">SQL Server 不會維護資料表值參數的統計資料。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="dfdcf-151">資料表值參數在 Transact-SQL 程式碼中處於唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="dfdcf-152">您無法更新資料表值參數資料列中的資料行值，也無法插入或刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="dfdcf-153">若要在資料表值參數中修改傳遞至預存程序或參數化陳述式的資料，您必須將資料插入至暫存資料表或資料表變數中。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="dfdcf-154">您無法使用 ALTER TABLE 陳述式來修改資料表值參數的設計。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="dfdcf-155">設定 SqlParameter 範例</span><span class="sxs-lookup"><span data-stu-id="dfdcf-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="dfdcf-156"><xref:System.Data.SqlClient> 支援從 <xref:System.Data.DataTable>、<xref:System.Data.Common.DbDataReader> 或 <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord>物件填入資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="dfdcf-157">您必須使用 <xref:System.Data.SqlClient.SqlParameter> 的 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 屬性來指定資料表值參數的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="dfdcf-158">`TypeName` 必須與先前在伺服器上所建立的相容型別名稱相符。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="dfdcf-159">下列程式碼片段示範如何設定 <xref:System.Data.SqlClient.SqlParameter> 以插入資料。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="dfdcf-160">在下列範例中，`addedCategories` 變數包含 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="dfdcf-161">若要查看變數的填入方式，請參閱下一節中的範例，[將資料表值參數傳遞至預存程序](#passing)。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 <span data-ttu-id="dfdcf-162">您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數，如本片段所示：</span><span class="sxs-lookup"><span data-stu-id="dfdcf-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="dfdcf-163">將表值參數傳遞給預存程序</span><span class="sxs-lookup"><span data-stu-id="dfdcf-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="dfdcf-164">此範例示範如何將資料表值參數資料傳遞至預存程序。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="dfdcf-165">程式碼會透過使用 <xref:System.Data.DataTable.GetChanges%2A> 方法，將加入的資料列解壓縮至新的 <xref:System.Data.DataTable> 之中。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="dfdcf-166">然後，程式碼會定義 <xref:System.Data.SqlClient.SqlCommand>，將 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 屬性設定為 <xref:System.Data.CommandType.StoredProcedure>。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="dfdcf-167"><xref:System.Data.SqlClient.SqlParameter> 是使用 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 方法填入的，而且 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 會設定為 `Structured`。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="dfdcf-168">然後使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法來執行 <xref:System.Data.SqlClient.SqlCommand>。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="dfdcf-169">將資料表值參數傳遞至參數化 SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="dfdcf-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="dfdcf-170">下列範例示範如何使用 INSERT 陳述式搭配以資料表值參數作為資料來源的 SELECT 子查詢，將資料插入至 dbo.Category 資料表。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="dfdcf-171">將資料表值參數傳遞至參數化 SQL 陳述式時，您必須使用 <xref:System.Data.SqlClient.SqlParameter> 的新 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 屬性來指定資料表值參數的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="dfdcf-172">這個 `TypeName` 必須與先前在伺服器上所建立的相容型別名稱相符。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="dfdcf-173">此範例中的程式碼會使用 `TypeName` 屬性來參考 dbo.CategoryTableType 中定義的型別結構。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfdcf-174">如果您在資料表值參數中提供識別資料行的值，就必須為該工作階段發出 SET IDENTITY_INSERT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="dfdcf-175">使用 DataReader 來資料流處理資料列</span><span class="sxs-lookup"><span data-stu-id="dfdcf-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="dfdcf-176">您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="dfdcf-177">下列程式碼片段示範如何使用 <xref:System.Data.OracleClient.OracleCommand> 與 <xref:System.Data.OracleClient.OracleDataReader>，從 Oracle 資料庫擷取資料。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="dfdcf-178">然後，程式碼會設定 <xref:System.Data.SqlClient.SqlCommand>，以使用單一輸入參數來叫用預存程序。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="dfdcf-179"><xref:System.Data.SqlClient.SqlParameter> 的 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 屬性會設定為 `Structured`。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="dfdcf-180"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 會將 `OracleDataReader` 結果集以資料表值參數的方式傳遞至預存程序。</span><span class="sxs-lookup"><span data-stu-id="dfdcf-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfdcf-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfdcf-181">See also</span></span>

- [<span data-ttu-id="dfdcf-182">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="dfdcf-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="dfdcf-183">命令和參數</span><span class="sxs-lookup"><span data-stu-id="dfdcf-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="dfdcf-184">DataAdapter 的參數</span><span class="sxs-lookup"><span data-stu-id="dfdcf-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="dfdcf-185">ADO.NET中的 SQL 伺服器資料操作</span><span class="sxs-lookup"><span data-stu-id="dfdcf-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- <span data-ttu-id="dfdcf-186">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="dfdcf-186">[ADO.NET Overview](../ado-net-overview.md)</span></span>
