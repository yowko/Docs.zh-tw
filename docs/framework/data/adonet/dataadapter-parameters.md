---
title: DataAdapter 的參數
description: 瞭解從資料來源傳回資料並管理資料來源變更的 DbDataAdapter 屬性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: 74b6787162b48f83a48127257dc8e23e31a859b7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286982"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="afb81-103">DataAdapter 的參數</span><span class="sxs-lookup"><span data-stu-id="afb81-103">DataAdapter Parameters</span></span>
<span data-ttu-id="afb81-104"><xref:System.Data.Common.DbDataAdapter> 具有四個屬性，可用來擷取資料來源的資料，以及將資料更新至資料來源：<xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> 屬性可傳回資料來源的資料，而 <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 屬性可用來管理在資料來源的變更。</span><span class="sxs-lookup"><span data-stu-id="afb81-104">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="afb81-105">在您呼叫 `SelectCommand` 的 `Fill` 方法前，必須先設定 `DataAdapter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="afb81-105">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="afb81-106">您必須先設定 `InsertCommand`、`UpdateCommand` 或 `DeleteCommand` 屬性，然後再呼叫 `Update` 的 `DataAdapter` 方法，端視針對 <xref:System.Data.DataTable> 中的資料進行哪些變更而定。</span><span class="sxs-lookup"><span data-stu-id="afb81-106">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="afb81-107">例如，如果已經加入資料列，則必須先設定 `InsertCommand`，才能呼叫 `Update`。</span><span class="sxs-lookup"><span data-stu-id="afb81-107">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="afb81-108">`Update` 正在處理已插入、已更新或已刪除的資料列時，`DataAdapter` 會使用個別的 `Command` 屬性來處理這項動作。</span><span class="sxs-lookup"><span data-stu-id="afb81-108">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="afb81-109">已修改資料列的目前資訊會透過 `Command` 集合傳遞給 `Parameters` 物件。</span><span class="sxs-lookup"><span data-stu-id="afb81-109">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="afb81-110">當您更新資料來源的資料列時，您會呼叫 UPDATE 語句，它會使用唯一識別碼來識別要更新之資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="afb81-110">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table to be updated.</span></span> <span data-ttu-id="afb81-111">唯一的識別項一般是主索引鍵欄位的值。</span><span class="sxs-lookup"><span data-stu-id="afb81-111">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="afb81-112">UPDATE 陳述式所使用的參數包含唯一的識別項，以及要更新的資料行和值，如下列 Transact-SQL 陳述式所示。</span><span class="sxs-lookup"><span data-stu-id="afb81-112">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```sql
UPDATE Customers SET CompanyName = @CompanyName
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
> <span data-ttu-id="afb81-113">參數預留位置的語法會隨資料來源而有所不同。</span><span class="sxs-lookup"><span data-stu-id="afb81-113">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="afb81-114">此範例將說明 SQL Server 資料來源的保留字元。</span><span class="sxs-lookup"><span data-stu-id="afb81-114">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="afb81-115">若為 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> 參數，請使用問號 (?) 保留字元。</span><span class="sxs-lookup"><span data-stu-id="afb81-115">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="afb81-116">在此 Visual Basic 範例中， `CompanyName` 會使用 `@CompanyName` 等於參數值之資料列的參數值來更新欄位 `CustomerID` `@CustomerID` 。</span><span class="sxs-lookup"><span data-stu-id="afb81-116">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="afb81-117">參數會使用物件的屬性，從修改過的資料列中取出資訊 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> <xref:System.Data.SqlClient.SqlParameter> 。</span><span class="sxs-lookup"><span data-stu-id="afb81-117">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="afb81-118">下列是前述範例 UPDATE 陳述式的參數。</span><span class="sxs-lookup"><span data-stu-id="afb81-118">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="afb81-119">程式碼會假設變數 `adapter` 表示有效的 <xref:System.Data.SqlClient.SqlDataAdapter> 物件。</span><span class="sxs-lookup"><span data-stu-id="afb81-119">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```vb
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="afb81-120">`Add` 集合的 `Parameters` 方法會擷取參數的名稱、資料型別、大小 (如果此型別有大小)，以及來自 <xref:System.Data.Common.DbParameter.SourceColumn%2A> 的 `DataTable` 名稱。</span><span class="sxs-lookup"><span data-stu-id="afb81-120">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="afb81-121">請注意，<xref:System.Data.Common.DbParameter.SourceVersion%2A> 參數的 `@CustomerID` 會設定為 `Original`。</span><span class="sxs-lookup"><span data-stu-id="afb81-121">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="afb81-122">如此一來，如果已修改的 <xref:System.Data.DataRow> 內識別欄位的值有所變更，便可確保資料來源內的現有資料列也已經更新。</span><span class="sxs-lookup"><span data-stu-id="afb81-122">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="afb81-123">在這種情況下，`Original` 資料列值會與資料來源中的目前值相符，而 `Current` 資料列值會包含已更新的值。</span><span class="sxs-lookup"><span data-stu-id="afb81-123">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="afb81-124">`SourceVersion` 參數的 `@CompanyName` 並未設定，因此會使用預設的 `Current` 資料列值。</span><span class="sxs-lookup"><span data-stu-id="afb81-124">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afb81-125">針對 `Fill` 的作業 `DataAdapter` 和的 `Get` 方法 `DataReader` ，會從 .NET Framework Data Provider 傳回的類型推斷 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="afb81-125">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the type returned from the .NET Framework data provider.</span></span> <span data-ttu-id="afb81-126">Microsoft SQL Server、OLE DB 和 ODBC 資料類型的推斷 .NET Framework 類型和存取子方法，會在[ADO.NET 的資料類型](data-type-mappings-in-ado-net.md)對應中加以說明。</span><span class="sxs-lookup"><span data-stu-id="afb81-126">The inferred .NET Framework types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="afb81-127">Parameter.SourceColumn、Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="afb81-127">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="afb81-128">`SourceColumn` 和 `SourceVersion` 可當做引數傳遞給 `Parameter` 建構函式 (Constructor)，或設定為現有 `Parameter` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="afb81-128">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="afb81-129">`SourceColumn` 是將在其中擷取 <xref:System.Data.DataColumn> 值之 <xref:System.Data.DataRow> 的 `Parameter` 名稱。</span><span class="sxs-lookup"><span data-stu-id="afb81-129">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="afb81-130">`SourceVersion` 會指定 `DataRow` 用來擷取值的 `DataAdapter` 版本。</span><span class="sxs-lookup"><span data-stu-id="afb81-130">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="afb81-131">下表顯示可與 <xref:System.Data.DataRowVersion> 搭配使用的 `SourceVersion` 列舉值。</span><span class="sxs-lookup"><span data-stu-id="afb81-131">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="afb81-132">DataRowVersion 列舉型別</span><span class="sxs-lookup"><span data-stu-id="afb81-132">DataRowVersion Enumeration</span></span>|<span data-ttu-id="afb81-133">描述</span><span class="sxs-lookup"><span data-stu-id="afb81-133">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="afb81-134">這個參數會使用資料行目前的值。</span><span class="sxs-lookup"><span data-stu-id="afb81-134">The parameter uses the current value of the column.</span></span> <span data-ttu-id="afb81-135">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="afb81-135">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="afb81-136">此參數會使用資料行的 `DefaultValue`。</span><span class="sxs-lookup"><span data-stu-id="afb81-136">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="afb81-137">這個參數會使用資料行的原始值。</span><span class="sxs-lookup"><span data-stu-id="afb81-137">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="afb81-138">這個會參數使用建議值。</span><span class="sxs-lookup"><span data-stu-id="afb81-138">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="afb81-139">下一區段中的 `SqlClient` 程式碼範例會定義 <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 的參數，其中 `CustomerID` 資料行將做為兩個參數的 `SourceColumn` 使用：`@CustomerID` (`SET CustomerID = @CustomerID`) 和 `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`)。</span><span class="sxs-lookup"><span data-stu-id="afb81-139">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="afb81-140">`@CustomerID`參數是用來將**CustomerID**資料行更新為中的目前值 `DataRow` 。</span><span class="sxs-lookup"><span data-stu-id="afb81-140">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="afb81-141">因此， `CustomerID` `SourceColumn` `SourceVersion` 會使用具有之的 `Current` 。</span><span class="sxs-lookup"><span data-stu-id="afb81-141">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="afb81-142">`@OldCustomerID`參數是用來識別資料來源中的目前資料列。</span><span class="sxs-lookup"><span data-stu-id="afb81-142">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="afb81-143">因為在資料列的 `Original` 版本中找到相符的資料行值，所以會使用 `SourceColumn` 為 `CustomerID` 的同一個 `SourceVersion` (`Original`)。</span><span class="sxs-lookup"><span data-stu-id="afb81-143">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="afb81-144">使用 SqlClient 參數</span><span class="sxs-lookup"><span data-stu-id="afb81-144">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="afb81-145">下列範例將示範如何建立 <xref:System.Data.SqlClient.SqlDataAdapter> 並將 <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> 設定為 <xref:System.Data.MissingSchemaAction.AddWithKey>，以便從資料庫中擷取其他結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="afb81-145">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="afb81-146"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 屬性已設定而且其對應的 <xref:System.Data.SqlClient.SqlParameter> 物件已加入至 <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="afb81-146">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="afb81-147">此方法會傳回 `SqlDataAdapter` 物件。</span><span class="sxs-lookup"><span data-stu-id="afb81-147">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="afb81-148">OleDb 參數預留位置</span><span class="sxs-lookup"><span data-stu-id="afb81-148">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="afb81-149">若為 <xref:System.Data.OleDb.OleDbDataAdapter> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，則必須使用問號 (?) 保留字元來識別參數。</span><span class="sxs-lookup"><span data-stu-id="afb81-149">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 <span data-ttu-id="afb81-150">參數化的查詢陳述式可定義必須建立的輸入和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="afb81-150">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="afb81-151">若要建立參數，請使用 `Parameters.Add` 方法或 `Parameter` 建構函式來指定資料行名稱、資料型別和大小。</span><span class="sxs-lookup"><span data-stu-id="afb81-151">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="afb81-152">如果資料型別為內建 (如 `Integer`)，則沒有必要包含大小，或者您也可以指定預設大小。</span><span class="sxs-lookup"><span data-stu-id="afb81-152">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="afb81-153">下列程式碼範例會建立 SQL 陳述式的參數，然後填入 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="afb81-153">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="afb81-154">OleDb 範例</span><span class="sxs-lookup"><span data-stu-id="afb81-154">OleDb Example</span></span>  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## <a name="odbc-parameters"></a><span data-ttu-id="afb81-155">Odbc 參數</span><span class="sxs-lookup"><span data-stu-id="afb81-155">Odbc Parameters</span></span>  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="afb81-156">如果沒有為參數提供參數名稱，則會將參數*N*的累加預設名稱指定為*參數，其開頭為*"Parameter1"。</span><span class="sxs-lookup"><span data-stu-id="afb81-156">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="afb81-157">當您提供參數名稱時，建議您避免使用參數*N*命名慣例，因為您所提供的名稱可能會與中現有的預設參數名稱相衝突 `ParameterCollection` 。</span><span class="sxs-lookup"><span data-stu-id="afb81-157">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="afb81-158">如果提供的名稱已經存在，便會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="afb81-158">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb81-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afb81-159">See also</span></span>

- [<span data-ttu-id="afb81-160">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="afb81-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="afb81-161">命令和參數</span><span class="sxs-lookup"><span data-stu-id="afb81-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="afb81-162">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="afb81-162">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="afb81-163">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="afb81-163">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="afb81-164">ADO.NET 中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="afb81-164">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- <span data-ttu-id="afb81-165">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="afb81-165">[ADO.NET Overview](ado-net-overview.md)</span></span>
