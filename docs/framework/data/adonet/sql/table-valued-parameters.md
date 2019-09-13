---
title: 資料表值參數
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 6c01453556a71925c322e9f9aef8065cbddb3540
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894386"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="ad85d-102">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="ad85d-102">Table-Valued Parameters</span></span>
<span data-ttu-id="ad85d-103">資料表值參數提供封送處理的簡易方式，可將用戶端應用程式的多個資料列封送處理到 SQL Server，而不需多次來回存取或使用特殊的伺服器端邏輯來處理資料。</span><span class="sxs-lookup"><span data-stu-id="ad85d-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="ad85d-104">您可以使用資料表值參數，在用戶端應用程式中封裝資料列，以及在單一參數型命令 (Parameterized Command) 中，將資料傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="ad85d-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="ad85d-105">內送資料列會儲存在資料表變數中，然後您可以使用 Transact-SQL 來操作此變數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="ad85d-106">資料表值參數中的資料行值可透過標準的 Transact-SQL SELECT 陳述式加以存取。</span><span class="sxs-lookup"><span data-stu-id="ad85d-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="ad85d-107">資料表值參數為強型別 (Strongly Typed)，其結構會自動驗證。</span><span class="sxs-lookup"><span data-stu-id="ad85d-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="ad85d-108">資料表值參數的大小僅受到伺服器記憶體的限制。</span><span class="sxs-lookup"><span data-stu-id="ad85d-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad85d-109">您不能以資料表值參數傳回資料。</span><span class="sxs-lookup"><span data-stu-id="ad85d-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="ad85d-110">資料表值參數只能接受輸入；OUTPUT 關鍵字不受支援。</span><span class="sxs-lookup"><span data-stu-id="ad85d-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="ad85d-111">如需資料表值參數的詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="ad85d-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="ad85d-112">Resource</span><span class="sxs-lookup"><span data-stu-id="ad85d-112">Resource</span></span>|<span data-ttu-id="ad85d-113">說明</span><span class="sxs-lookup"><span data-stu-id="ad85d-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ad85d-114">SQL Server 線上叢書中的[資料表值參數 (資料庫引擎)](https://go.microsoft.com/fwlink/?LinkId=98363)</span><span class="sxs-lookup"><span data-stu-id="ad85d-114">[Table-Valued Parameters (Database Engine)](https://go.microsoft.com/fwlink/?LinkId=98363) in SQL Server Books Online</span></span>|<span data-ttu-id="ad85d-115">說明如何建立及使用資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="ad85d-116">SQL Server 線上叢書中的[使用者定義資料表類型](https://go.microsoft.com/fwlink/?LinkId=98364)</span><span class="sxs-lookup"><span data-stu-id="ad85d-116">[User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server Books Online</span></span>|<span data-ttu-id="ad85d-117">說明用於宣告資料表值參數的使用者定義資料表型別。</span><span class="sxs-lookup"><span data-stu-id="ad85d-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="ad85d-118">在舊版 SQL Server 中傳遞多個資料列</span><span class="sxs-lookup"><span data-stu-id="ad85d-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="ad85d-119">在將資料表值參數引進 SQL Server 2008 之前, 將多個資料列傳遞至預存程式或參數化 SQL 命令的選項受到限制。</span><span class="sxs-lookup"><span data-stu-id="ad85d-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="ad85d-120">若要將多個資料列傳遞至伺服器，開發人員可能會從下列選項中選擇：</span><span class="sxs-lookup"><span data-stu-id="ad85d-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="ad85d-121">使用一連串個別的參數來代表多個資料行和資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="ad85d-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="ad85d-122">使用這個方法可傳遞的資料量會受到允許的參數數目所限制。</span><span class="sxs-lookup"><span data-stu-id="ad85d-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="ad85d-123">SQL Server 程序最多可以有 2100 個參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="ad85d-124">伺服器端邏輯必須將這些個別的值組合成資料表變數或暫存資料表，以便進行處理。</span><span class="sxs-lookup"><span data-stu-id="ad85d-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="ad85d-125">將多個資料值包裝成分隔字串或 XML 文件，然後將這些文字值傳遞至程序或陳述式 (Statement)。</span><span class="sxs-lookup"><span data-stu-id="ad85d-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="ad85d-126">此程序或陳述式必須包含驗證資料結構和取消包裝值所需的邏輯。</span><span class="sxs-lookup"><span data-stu-id="ad85d-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="ad85d-127">針對影響多個資料列的資料修改項目建立一連串個別的 SQL 陳述式，例如呼叫 `Update` 之 <xref:System.Data.SqlClient.SqlDataAdapter> 方法所建立的修改項目。</span><span class="sxs-lookup"><span data-stu-id="ad85d-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="ad85d-128">您可以將變更個別送出至伺服器，也可以將它們批次處理成為群組。</span><span class="sxs-lookup"><span data-stu-id="ad85d-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="ad85d-129">不過，即使按照包含多個陳述式的批次送出，每個陳述式仍然會分別在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="ad85d-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="ad85d-130">使用 `bcp` 公用程式或 <xref:System.Data.SqlClient.SqlBulkCopy> 物件，將許多資料列載入資料表中。</span><span class="sxs-lookup"><span data-stu-id="ad85d-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="ad85d-131">雖然這項技術非常有效率，不過除非資料會載入暫存資料表或資料表變數中，否則它不支援伺服器端處理。</span><span class="sxs-lookup"><span data-stu-id="ad85d-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="ad85d-132">建立資料表值參數型別</span><span class="sxs-lookup"><span data-stu-id="ad85d-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="ad85d-133">資料表值參數是以使用 Transact-SQL CREATE TYPE 陳述式所定義的強型別 (Strongly Typed) 資料表結構為基礎。</span><span class="sxs-lookup"><span data-stu-id="ad85d-133">Table-valued parameters are based on strongly-typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="ad85d-134">您必須先在 SQL Server 中建立資料表型別並定義此結構，然後才能在用戶端應用程式中使用資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="ad85d-135">如需建立資料表類型的詳細資訊, 請參閱 SQL Server 線上叢書中的[使用者定義資料表類型](https://go.microsoft.com/fwlink/?LinkID=98364)。</span><span class="sxs-lookup"><span data-stu-id="ad85d-135">For more information about creating table types, see [User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkID=98364) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="ad85d-136">下列陳述式會建立名為 CategoryTableType 的資料表型別，其中包含 CategoryID 和 CategoryName 資料行：</span><span class="sxs-lookup"><span data-stu-id="ad85d-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="ad85d-137">建立資料表型別之後，您就可以根據該型別來宣告資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="ad85d-138">下列 Transact-SQL 片段將示範如何在預存程序定義中宣告資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="ad85d-139">請注意，READONLY 關鍵字是宣告資料表值參數的必要項目。</span><span class="sxs-lookup"><span data-stu-id="ad85d-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="ad85d-140">使用資料表值參數來修改資料 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ad85d-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="ad85d-141">資料表值參數可用於透過執行單一陳述式來影響多個資料列的集合式資料修改作業中。</span><span class="sxs-lookup"><span data-stu-id="ad85d-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="ad85d-142">例如，您可以選擇資料表值參數中的所有資料列，然後將其插入至資料庫資料表，或者將資料表值參數與您要更新的資料表聯結 (Join) 而建立更新陳述式。</span><span class="sxs-lookup"><span data-stu-id="ad85d-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="ad85d-143">下列 Transact-SQL UPDATE 陳述式會示範如何將資料表值參數聯結至 Categories 資料表，藉以運用此參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="ad85d-144">當您在 FROM 子句中使用資料表值參數搭配 JOIN 時，也必須設定其別名，如下面所示，其中資料表值參數的別名設定為 "ec"：</span><span class="sxs-lookup"><span data-stu-id="ad85d-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="ad85d-145">這個 Transact-SQL 範例將示範如何從資料表值參數中選取資料列，以便在單一集合式作業中執行 INSERT。</span><span class="sxs-lookup"><span data-stu-id="ad85d-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="ad85d-146">資料表值參數的限制</span><span class="sxs-lookup"><span data-stu-id="ad85d-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="ad85d-147">資料表值參數有許多限制：</span><span class="sxs-lookup"><span data-stu-id="ad85d-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="ad85d-148">您無法將資料表值參數傳遞至[CLR 使用者定義函數](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)。</span><span class="sxs-lookup"><span data-stu-id="ad85d-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="ad85d-149">資料表值參數只能針對支援 UNIQUE 或 PRIMARY KEY 條件約束 (Constraint) 而建立索引。</span><span class="sxs-lookup"><span data-stu-id="ad85d-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="ad85d-150">SQL Server 不會維護資料表值參數的統計資料。</span><span class="sxs-lookup"><span data-stu-id="ad85d-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="ad85d-151">資料表值參數在 Transact-SQL 程式碼中處於唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="ad85d-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="ad85d-152">您無法更新資料表值參數之資料列中的資料行值，也無法插入或刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="ad85d-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="ad85d-153">若要修改在資料表值參數中傳遞至預存程序或參數化陳述式的資料，您必須將這項資料插入暫存資料表或資料表變數中。</span><span class="sxs-lookup"><span data-stu-id="ad85d-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="ad85d-154">您無法使用 ALTER TABLE 陳述式來修改資料表值參數的設計。</span><span class="sxs-lookup"><span data-stu-id="ad85d-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="ad85d-155">設定 SqlParameter 範例</span><span class="sxs-lookup"><span data-stu-id="ad85d-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="ad85d-156"><xref:System.Data.SqlClient>支援從<xref:System.Data.DataTable>、 <xref:System.Data.Common.DbDataReader>或<xref:System.Collections.Generic.IEnumerable%601>物件填入資料表值參數。 \  <xref:Microsoft.SqlServer.Server.SqlDataRecord></span><span class="sxs-lookup"><span data-stu-id="ad85d-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="ad85d-157">您必須使用 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 的 <xref:System.Data.SqlClient.SqlParameter> 屬性來指定資料表值參數的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ad85d-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="ad85d-158">`TypeName` 必須與之前在伺服器上所建立之相容型別的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="ad85d-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="ad85d-159">下列程式碼片段示範如何設定 <xref:System.Data.SqlClient.SqlParameter> 以插入資料。</span><span class="sxs-lookup"><span data-stu-id="ad85d-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
 
<span data-ttu-id="ad85d-160">在下列範例中， `addedCategories`變數<xref:System.Data.DataTable>包含。</span><span class="sxs-lookup"><span data-stu-id="ad85d-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="ad85d-161">若要查看變數的填入方式，請參閱下一節將[資料表值參數傳遞至預存程式](#passing)中的範例。</span><span class="sxs-lookup"><span data-stu-id="ad85d-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="ad85d-162">您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數，如本片段所示：</span><span class="sxs-lookup"><span data-stu-id="ad85d-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing"></a><span data-ttu-id="ad85d-163">將資料表值參數傳遞至預存程式</span><span class="sxs-lookup"><span data-stu-id="ad85d-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="ad85d-164">這則範例會示範如何將資料表值參數資料傳遞至預存程序。</span><span class="sxs-lookup"><span data-stu-id="ad85d-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="ad85d-165">此程式碼會使用 <xref:System.Data.DataTable> 方法來擷取加入至新 <xref:System.Data.DataTable.GetChanges%2A> 的資料列。</span><span class="sxs-lookup"><span data-stu-id="ad85d-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="ad85d-166">然後，此程式碼會定義 <xref:System.Data.SqlClient.SqlCommand>，並將 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 屬性設定成 <xref:System.Data.CommandType.StoredProcedure>。</span><span class="sxs-lookup"><span data-stu-id="ad85d-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="ad85d-167"><xref:System.Data.SqlClient.SqlParameter> 是使用 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 方法填入的，而且 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 會設定為 `Structured`。</span><span class="sxs-lookup"><span data-stu-id="ad85d-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="ad85d-168">接著，系統就會使用 <xref:System.Data.SqlClient.SqlCommand> 方法來執行 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>。</span><span class="sxs-lookup"><span data-stu-id="ad85d-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="ad85d-169">將資料表值參數傳遞至參數化 SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad85d-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="ad85d-170">下列範例會示範如何使用 INSERT 陳述式搭配具有資料表值參數當做資料來源的 SELECT 子查詢，將資料插入 dbo.Categories 資料表中。</span><span class="sxs-lookup"><span data-stu-id="ad85d-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="ad85d-171">將資料表值參數傳遞至參數化 SQL 陳述式時，您必須使用 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 的新 <xref:System.Data.SqlClient.SqlParameter> 屬性來指定資料表值參數的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="ad85d-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="ad85d-172">這個 `TypeName` 必須與之前在伺服器上所建立之相容型別的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="ad85d-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="ad85d-173">這則範例中的程式碼會使用 `TypeName` 屬性來參考 dbo.CategoryTableType 中定義的型別結構。</span><span class="sxs-lookup"><span data-stu-id="ad85d-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad85d-174">如果您針對資料表值參數中的識別資料行提供一個值，就必須發出此工作階段 (Session) 的 SET IDENTITY_INSERT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ad85d-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="ad85d-175">使用 DataReader 來資料流處理資料列</span><span class="sxs-lookup"><span data-stu-id="ad85d-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="ad85d-176">您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="ad85d-177">下列程式碼片段會示範如何使用 <xref:System.Data.OracleClient.OracleCommand> 和 <xref:System.Data.OracleClient.OracleDataReader>，從 Oracle 資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="ad85d-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="ad85d-178">然後，此程式碼會設定 <xref:System.Data.SqlClient.SqlCommand>，以便使用單一輸入參數來叫用 (Invoke) 預存程序。</span><span class="sxs-lookup"><span data-stu-id="ad85d-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="ad85d-179"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 的 <xref:System.Data.SqlClient.SqlParameter> 屬性會設定為 `Structured`。</span><span class="sxs-lookup"><span data-stu-id="ad85d-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="ad85d-180">最後，<xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 會將 `OracleDataReader` 結果集傳遞至預存程序，當做資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="ad85d-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad85d-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad85d-181">See also</span></span>

- [<span data-ttu-id="ad85d-182">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="ad85d-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="ad85d-183">命令和參數</span><span class="sxs-lookup"><span data-stu-id="ad85d-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="ad85d-184">DataAdapter 參數</span><span class="sxs-lookup"><span data-stu-id="ad85d-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="ad85d-185">ADO.NET 中的 SQL Server 資料作業</span><span class="sxs-lookup"><span data-stu-id="ad85d-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="ad85d-186">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="ad85d-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
