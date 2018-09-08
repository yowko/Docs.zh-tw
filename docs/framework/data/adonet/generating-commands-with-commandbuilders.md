---
title: 使用 CommandBuilder 產生命令
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: e1071261f45c56655f8e6fb5fec6fccb08fd13c6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128426"
---
# <a name="generating-commands-with-commandbuilders"></a><span data-ttu-id="dc2ca-102">使用 CommandBuilder 產生命令</span><span class="sxs-lookup"><span data-stu-id="dc2ca-102">Generating Commands with CommandBuilders</span></span>
<span data-ttu-id="dc2ca-103">當 `SelectCommand` 屬性是在執行階段時以動態方式指定 (例如透過能接收使用者下達文字命令的查詢工具)，則您可能無法於設計階段指定適當的 `InsertCommand`、`UpdateCommand` 或 `DeleteCommand`。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-103">When the `SelectCommand` property is dynamically specified at run time, such as through a query tool that takes a textual command from the user, you may not be able to specify the appropriate `InsertCommand`, `UpdateCommand`, or `DeleteCommand` at design time.</span></span> <span data-ttu-id="dc2ca-104">如果您的 <xref:System.Data.DataTable> 對應至或產生自單一資料庫資料表，則可以利用 <xref:System.Data.Common.DbCommandBuilder> 物件來自動產生 `DeleteCommand` 的 `InsertCommand`、`UpdateCommand` 和 <xref:System.Data.Common.DbDataAdapter>。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-104">If your <xref:System.Data.DataTable> maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` of the <xref:System.Data.Common.DbDataAdapter>.</span></span>  
  
 <span data-ttu-id="dc2ca-105">根據最小需求，您必須設定 `SelectCommand` 屬性，才能使用自動命令產生功能。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-105">As a minimum requirement, you must set the `SelectCommand` property in order for automatic command generation to work.</span></span> <span data-ttu-id="dc2ca-106">`SelectCommand` 屬性擷取的資料表結構描述則決定自動產生的 INSERT、UPDATE 和 DELETE 陳述式語法。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-106">The table schema retrieved by the `SelectCommand` property determines the syntax of the automatically generated INSERT, UPDATE, and DELETE statements.</span></span>  
  
 <span data-ttu-id="dc2ca-107"><xref:System.Data.Common.DbCommandBuilder> 必須執行 `SelectCommand`，才能傳回必要的中繼資料來建構 INSERT、UPDATE 和 DELETE SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-107">The <xref:System.Data.Common.DbCommandBuilder> must execute the `SelectCommand` in order to return the metadata necessary to construct the INSERT, UPDATE, and DELETE SQL commands.</span></span> <span data-ttu-id="dc2ca-108">因此必須要另外連至資料來源，但這可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-108">As a result, an extra trip to the data source is necessary, and this can hinder performance.</span></span> <span data-ttu-id="dc2ca-109">若要達到最佳效能，請明確地指定命令，而不要使用 <xref:System.Data.Common.DbCommandBuilder>。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-109">To achieve optimal performance, specify your commands explicitly rather than using the <xref:System.Data.Common.DbCommandBuilder>.</span></span>  
  
 <span data-ttu-id="dc2ca-110">`SelectCommand` 還必須傳回至少一個主索引鍵或唯一的資料行。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-110">The `SelectCommand` must also return at least one primary key or unique column.</span></span> <span data-ttu-id="dc2ca-111">如果兩個都不存在，便會發生 `InvalidOperation` 例外狀況 (Exception)，且不會產生命令。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-111">If none are present, an `InvalidOperation` exception is generated, and the commands are not generated.</span></span>  
  
 <span data-ttu-id="dc2ca-112">與 `DataAdapter` 產生關聯時，<xref:System.Data.Common.DbCommandBuilder> 會自動產生 `InsertCommand` 的 `UpdateCommand`、`DeleteCommand` 和 `DataAdapter` 屬性 (如果它們是 Null 參考)。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-112">When associated with a `DataAdapter`, the <xref:System.Data.Common.DbCommandBuilder> automatically generates the `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` if they are null references.</span></span> <span data-ttu-id="dc2ca-113">如果屬性的 `Command` 已經存在，則會使用現有的 `Command`。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-113">If a `Command` already exists for a property, the existing `Command` is used.</span></span>  
  
 <span data-ttu-id="dc2ca-114">您不能將兩個或多個資料表合併所建立的資料庫檢視視為單一資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-114">Database views that are created by joining two or more tables together are not considered a single database table.</span></span> <span data-ttu-id="dc2ca-115">在這個執行個體中，您無法使用 <xref:System.Data.Common.DbCommandBuilder> 自動產生命令，而且必須明確指定命令。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-115">In this instance you cannot use the <xref:System.Data.Common.DbCommandBuilder> to automatically generate commands; you must specify your commands explicitly.</span></span> <span data-ttu-id="dc2ca-116">如需明確設定命令以更新解析`DataSet`回到 資料來源，請參閱[使用 Dataadapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-116">For information about explicitly setting commands to resolve updates to a `DataSet` back to the data source, see [Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="dc2ca-117">您可能想要把輸出參數對應回 `DataSet` 已更新的資料列。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-117">You might want to map output parameters back to the updated row of a `DataSet`.</span></span> <span data-ttu-id="dc2ca-118">一項通用工作便是從資料來源擷取自動產生的識別欄位值或時間戳記值。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-118">One common task would be retrieving the value of an automatically generated identity field or time stamp from the data source.</span></span> <span data-ttu-id="dc2ca-119"><xref:System.Data.Common.DbCommandBuilder> 預設不會將輸出參數對應到已更新資料列中的資料行。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-119">The <xref:System.Data.Common.DbCommandBuilder> will not map output parameters to columns in an updated row by default.</span></span> <span data-ttu-id="dc2ca-120">在這種情形下，您必須明確地指定命令。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-120">In this instance you must specify your command explicitly.</span></span> <span data-ttu-id="dc2ca-121">回到 插入資料列的資料行對應會自動產生的識別欄位的範例，請參閱[擷取識別或自動編號值](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-121">For an example of mapping an automatically generated identity field back to a column of an inserted row, see [Retrieving Identity or Autonumber Values](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span></span>  
  
## <a name="rules-for-automatically-generated-commands"></a><span data-ttu-id="dc2ca-122">自動產生命令的規則</span><span class="sxs-lookup"><span data-stu-id="dc2ca-122">Rules for Automatically Generated Commands</span></span>  
 <span data-ttu-id="dc2ca-123">下列表格顯示產生自動產生命令的規則。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-123">The following table shows the rules for how automatically generated commands are generated.</span></span>  
  
|<span data-ttu-id="dc2ca-124">命令</span><span class="sxs-lookup"><span data-stu-id="dc2ca-124">Command</span></span>|<span data-ttu-id="dc2ca-125">規則</span><span class="sxs-lookup"><span data-stu-id="dc2ca-125">Rule</span></span>|  
|-------------|----------|  
|`InsertCommand`|<span data-ttu-id="dc2ca-126">針對含 <xref:System.Data.DataRow.RowState%2A> 的 <xref:System.Data.DataRowState.Added> 之資料表的所有資料列，插入資料來源上的資料列。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-126">Inserts a row at the data source for all rows in the table with a <xref:System.Data.DataRow.RowState%2A> of <xref:System.Data.DataRowState.Added>.</span></span> <span data-ttu-id="dc2ca-127">插入所有可更新的資料行值 (但非識別、運算式或時間籤記等資料行)。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-127">Inserts values for all columns that are updateable (but not columns such as identities, expressions, or timestamps).</span></span>|  
|`UpdateCommand`|<span data-ttu-id="dc2ca-128">針對含 `RowState` 的 <xref:System.Data.DataRowState.Modified> 之資料表的所有資料列，更新資料來源上的資料列。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-128">Updates rows at the data source for all rows in the table with a `RowState` of <xref:System.Data.DataRowState.Modified>.</span></span> <span data-ttu-id="dc2ca-129">除了無法更新的資料行 (例如識別或運算式) 之外，更新所有可更新的資料行值。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-129">Updates the values of all columns except for columns that are not updateable, such as identities or expressions.</span></span> <span data-ttu-id="dc2ca-130">並且在資料來源中，找出資料行值與資料列主索引鍵資料行值相符的資料列，以及剩餘資料行與資料列原始資料相符的資料列，將這些資料列全都更新。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-130">Updates all rows where the column values at the data source match the primary key column values of the row, and where the remaining columns at the data source match the original values of the row.</span></span> <span data-ttu-id="dc2ca-131">如需詳細資訊，請參閱這個主題稍後的＜更新和刪除的開放式同步存取模式＞。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-131">For more information, see "Optimistic Concurrency Model for Updates and Deletes," later in this topic.</span></span>|  
|`DeleteCommand`|<span data-ttu-id="dc2ca-132">針對含 `RowState` 的 <xref:System.Data.DataRowState.Deleted> 之資料表的所有資料列，刪除資料來源上的資料列。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-132">Deletes rows at the data source for all rows in the table with a `RowState` of <xref:System.Data.DataRowState.Deleted>.</span></span> <span data-ttu-id="dc2ca-133">在資料來源中，找出其資料行值與資料列的主索引鍵資料行值相符的所有資料列，以及剩餘資料行與原始資料列值相符的所有資料列，並將這些資料列全都刪除。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-133">Deletes all rows where the column values match the primary key column values of the row, and where the remaining columns at the data source match the original values of the row.</span></span> <span data-ttu-id="dc2ca-134">如需詳細資訊，請參閱這個主題稍後的＜更新和刪除的開放式同步存取模式＞。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-134">For more information, see "Optimistic Concurrency Model for Updates and Deletes," later in this topic.</span></span>|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a><span data-ttu-id="dc2ca-135">更新和刪除開放式同步存取模式</span><span class="sxs-lookup"><span data-stu-id="dc2ca-135">Optimistic Concurrency Model for Updates and Deletes</span></span>  
 <span data-ttu-id="dc2ca-136">自動替 UPDATE 和 DELETE 陳述式產生命令的邏輯根據*開放式並行存取*-也就是說，記錄進行編輯，不鎖定，而且可以隨時修改其他使用者或處理程序。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-136">The logic for generating commands automatically for UPDATE and DELETE statements is based on *optimistic concurrency*--that is, records are not locked for editing and can be modified by other users or processes at any time.</span></span> <span data-ttu-id="dc2ca-137">記錄從 SELECT 陳述式傳回後可能已經修改，但是發出 UPDATE 或 DELETE 陳述式之前，自動產生的 UPDATE 或 DELETE 陳述式會包含 WHERE 子句，指定只有資料列包含所有原始值且尚未從資料來源刪除時，才會更新該資料列。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-137">Because a record could have been modified after it was returned from the SELECT statement, but before the UPDATE or DELETE statement is issued, the automatically generated UPDATE or DELETE statement contains a WHERE clause, specifying that a row is only updated if it contains all original values and has not been deleted from the data source.</span></span> <span data-ttu-id="dc2ca-138">這樣是為了避免覆寫新資料。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-138">This is done to avoid overwriting new data.</span></span> <span data-ttu-id="dc2ca-139">自動產生的更新嘗試更新已刪除的資料列或未包含 <xref:System.Data.DataSet> 中所找到之原始值的資料列時，該命令不會影響任何記錄，且會擲回 <xref:System.Data.DBConcurrencyException>。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-139">Where an automatically generated update attempts to update a row that has been deleted or that does not contain the original values found in the <xref:System.Data.DataSet>, the command does not affect any records, and a <xref:System.Data.DBConcurrencyException> is thrown.</span></span>  
  
 <span data-ttu-id="dc2ca-140">如果您想完成 UPDATE 或 DELETE (不管是否為原始值)，則您必須明確設定 `UpdateCommand` 的 `DataAdapter`，而不是依賴自動命令產生功能。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-140">If you want the UPDATE or DELETE to complete regardless of original values, you must explicitly set the `UpdateCommand` for the `DataAdapter` and not rely on automatic command generation.</span></span>  
  
## <a name="limitations-of-automatic-command-generation-logic"></a><span data-ttu-id="dc2ca-141">自動命令產生的邏輯限制</span><span class="sxs-lookup"><span data-stu-id="dc2ca-141">Limitations of Automatic Command Generation Logic</span></span>  
 <span data-ttu-id="dc2ca-142">下列限制適用於自動命令產生。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-142">The following limitations apply to automatic command generation.</span></span>  
  
### <a name="unrelated-tables-only"></a><span data-ttu-id="dc2ca-143">僅限不相關的資料表</span><span class="sxs-lookup"><span data-stu-id="dc2ca-143">Unrelated Tables Only</span></span>  
 <span data-ttu-id="dc2ca-144">自動命令產生邏輯為獨立資料表產生 INSERT、UPDATE 或 DELETE 陳述式，而不顧及任何與資料來源中其他資料表的關聯性。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-144">The automatic command generation logic generates INSERT, UPDATE, or DELETE statements for stand-alone tables without taking into account any relationships to other tables at the data source.</span></span> <span data-ttu-id="dc2ca-145">所以，如果呼叫 `Update` 將變更送出至資料行，而這個資料行又擔任資料庫的外部索引鍵條件約束，則可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-145">As a result, you may encounter a failure when calling `Update` to submit changes for a column that participates in a foreign key constraint in the database.</span></span> <span data-ttu-id="dc2ca-146">為了避免發生這種例外狀況，請勿使用 <xref:System.Data.Common.DbCommandBuilder> 來更新外部索引鍵條件約束所牽涉的資料行，而應該明確地指定用於執行作業的陳述式。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-146">To avoid this exception, do not use the <xref:System.Data.Common.DbCommandBuilder> for updating columns involved in a foreign key constraint; instead, explicitly specify the statements used to perform the operation.</span></span>  
  
### <a name="table-and-column-names"></a><span data-ttu-id="dc2ca-147">資料表和資料行名稱</span><span class="sxs-lookup"><span data-stu-id="dc2ca-147">Table and Column Names</span></span>  
 <span data-ttu-id="dc2ca-148">如果資料行名稱或資料表名稱包含任何特殊字元，例如空格、句號、引號或其他非英數的字元，則即使以括弧分隔，自動命令產生邏輯仍可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-148">Automatic command generation logic may fail if column names or table names contain any special characters, such as spaces, periods, quotation marks, or other nonalphanumeric characters, even if delimited by brackets.</span></span> <span data-ttu-id="dc2ca-149">根據提供者而定，設定 QuotePrefix 和 QuoteSuffix 參數可能會允許產生邏輯以處理空格，不過，卻不能逸出特殊字元。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-149">Depending on the provider, setting the QuotePrefix and QuoteSuffix parameters may allow the generation logic to process spaces, but it cannot escape special characters.</span></span> <span data-ttu-id="dc2ca-150">完整資料表名稱的形式*catalog.schema.table*支援。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-150">Fully qualified table names in the form of *catalog.schema.table* are supported.</span></span>  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a><span data-ttu-id="dc2ca-151">使用 CommandBuilder 自動產生 SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="dc2ca-151">Using the CommandBuilder to Automatically Generate an SQL Statement</span></span>  
 <span data-ttu-id="dc2ca-152">若要自動產生 `DataAdapter` 的 SQL 陳述式，請首先設定 `SelectCommand` 的 `DataAdapter` 屬性，然後建立 `CommandBuilder` 物件，再指定為引數，該引數則是 `DataAdapter` 將自動為其產生 SQL 陳述式的 `CommandBuilder`。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-152">To automatically generate SQL statements for a `DataAdapter`, first set the `SelectCommand` property of the `DataAdapter`, then create a `CommandBuilder` object, and specify as an argument the `DataAdapter` for which the `CommandBuilder` will automatically generate SQL statements.</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object   
' inside of a Using block.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", connection)  
Dim builder As SqlCommandBuilder = New SqlCommandBuilder(adapter)  
builder.QuotePrefix = "["  
builder.QuoteSuffix = "]"  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object  
// inside of a using block.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", connection);  
SqlCommandBuilder builder = new SqlCommandBuilder(adapter);  
builder.QuotePrefix = "[";  
builder.QuoteSuffix = "]";  
```  
  
## <a name="modifying-the-selectcommand"></a><span data-ttu-id="dc2ca-153">修改 SelectCommand</span><span class="sxs-lookup"><span data-stu-id="dc2ca-153">Modifying the SelectCommand</span></span>  
 <span data-ttu-id="dc2ca-154">如果您在 INSERT、UPDATE 或 DELETE 命令自動產生後，修改 `CommandText` 的 `SelectCommand`，便可能發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-154">If you modify the `CommandText` of the `SelectCommand` after the INSERT, UPDATE, or DELETE commands have been automatically generated, an exception may occur.</span></span> <span data-ttu-id="dc2ca-155">如果已修改的 `SelectCommand.CommandText` 包含的結構描述資訊與插入、更新或刪除命令自動產生時使用的 `SelectCommand.CommandText` 不一致，日後呼叫的 `DataAdapter.Update` 方法便可能會到 `SelectCommand` 參考的目前資料表中，嘗試存取已不存在的資料行，這樣就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-155">If the modified `SelectCommand.CommandText` contains schema information that is inconsistent with the `SelectCommand.CommandText` used when the insert, update, or delete commands were automatically generated, future calls to the `DataAdapter.Update` method may attempt to access columns that no longer exist in the current table referenced by the `SelectCommand`, and an exception will be thrown.</span></span>  
  
 <span data-ttu-id="dc2ca-156">您可以藉由重新整理 `CommandBuilder` 使用的結構描述資訊，呼叫 `RefreshSchema` 的 `CommandBuilder` 方法以自動產生命令。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-156">You can refresh the schema information used by the `CommandBuilder` to automatically generate commands by calling the `RefreshSchema` method of the `CommandBuilder`.</span></span>  
  
 <span data-ttu-id="dc2ca-157">若您想要知道自動產生的命令為何，可以使用 `GetInsertCommand` 物件的 `GetUpdateCommand`、`GetDeleteCommand` 和 `CommandBuilder` 方法，取得自動產生命令的參考，然後檢查相關命令的 `CommandText` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-157">If you want to know what command was automatically generated, you can obtain a reference to the automatically generated commands by using the `GetInsertCommand`, `GetUpdateCommand`, and `GetDeleteCommand` methods of the `CommandBuilder` object and checking the `CommandText` property of the associated command.</span></span>  
  
 <span data-ttu-id="dc2ca-158">下列程式碼範例將自動產生的更新命令寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-158">The following code example writes to the console the update command that was automatically generated.</span></span>  
  
```  
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```  
  
 <span data-ttu-id="dc2ca-159">下列範例會在 `Customers` 資料集中重新建立 `custDS` 資料表。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-159">The following example recreates the `Customers` table in the `custDS` dataset.</span></span> <span data-ttu-id="dc2ca-160">**RefreshSchema**呼叫方法來重新整理自動產生的命令，這個新的資料行資訊。</span><span class="sxs-lookup"><span data-stu-id="dc2ca-160">The **RefreshSchema** method is called to refresh the automatically generated commands with this new column information.</span></span>  
  
```vb  
' Assumes an open SqlConnection and SqlDataAdapter inside of a Using block.  
adapter.SelectCommand.CommandText = _  
  "SELECT CustomerID, ContactName FROM dbo.Customers"  
builder.RefreshSchema()  
  
custDS.Tables.Remove(custDS.Tables("Customers"))  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
// Assumes an open SqlConnection and SqlDataAdapter inside of a using block.  
adapter.SelectCommand.CommandText =   
  "SELECT CustomerID, ContactName FROM dbo.Customers";  
builder.RefreshSchema();  
  
custDS.Tables.Remove(custDS.Tables["Customers"]);  
adapter.Fill(custDS, "Customers");  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc2ca-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc2ca-161">See Also</span></span>  
 [<span data-ttu-id="dc2ca-162">命令和參數</span><span class="sxs-lookup"><span data-stu-id="dc2ca-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="dc2ca-163">執行命令</span><span class="sxs-lookup"><span data-stu-id="dc2ca-163">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="dc2ca-164">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="dc2ca-164">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="dc2ca-165">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="dc2ca-165">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
