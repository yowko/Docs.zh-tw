---
title: DataAdapter 的參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: e633c7cdd105125fc5fb595566d15cf5f5fe4e6f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539601"
---
# <a name="dataadapter-parameters"></a><span data-ttu-id="6a155-102">DataAdapter 的參數</span><span class="sxs-lookup"><span data-stu-id="6a155-102">DataAdapter Parameters</span></span>
<span data-ttu-id="6a155-103"><xref:System.Data.Common.DbDataAdapter> 具有四個屬性，可用來擷取資料來源的資料，以及將資料更新至資料來源：<xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> 屬性可傳回資料來源的資料，而 <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 屬性可用來管理在資料來源的變更。</span><span class="sxs-lookup"><span data-stu-id="6a155-103">The <xref:System.Data.Common.DbDataAdapter> has four properties that are used to retrieve data from and update data to the data source: the <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> property returns data from the data source; and the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, and <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> properties are used to manage changes at the data source.</span></span> <span data-ttu-id="6a155-104">在您呼叫 `SelectCommand` 的 `Fill` 方法前，必須先設定 `DataAdapter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6a155-104">The `SelectCommand` property must be set before you call the `Fill` method of the `DataAdapter`.</span></span> <span data-ttu-id="6a155-105">您必須先設定 `InsertCommand`、`UpdateCommand` 或 `DeleteCommand` 屬性，然後再呼叫 `Update` 的 `DataAdapter` 方法，端視針對 <xref:System.Data.DataTable> 中的資料進行哪些變更而定。</span><span class="sxs-lookup"><span data-stu-id="6a155-105">The `InsertCommand`, `UpdateCommand`, or `DeleteCommand` properties must be set before the `Update` method of the `DataAdapter` is called, depending on what changes were made to the data in the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="6a155-106">例如，如果已經加入資料列，則必須先設定 `InsertCommand`，才能呼叫 `Update`。</span><span class="sxs-lookup"><span data-stu-id="6a155-106">For example, if rows have been added, the `InsertCommand` must be set before you call `Update`.</span></span> <span data-ttu-id="6a155-107">`Update` 正在處理已插入、已更新或已刪除的資料列時，`DataAdapter` 會使用個別的 `Command` 屬性來處理這項動作。</span><span class="sxs-lookup"><span data-stu-id="6a155-107">When `Update` is processing an inserted, updated, or deleted row, the `DataAdapter` uses the respective `Command` property to process the action.</span></span> <span data-ttu-id="6a155-108">已修改資料列的目前資訊會透過 `Command` 集合傳遞給 `Parameters` 物件。</span><span class="sxs-lookup"><span data-stu-id="6a155-108">Current information about the modified row is passed to the `Command` object through the `Parameters` collection.</span></span>  
  
 <span data-ttu-id="6a155-109">更新資料來源的資料列時，您呼叫的 UPDATE 陳述式會使用唯一的識別項來識別資料表中需要更新的資料列。</span><span class="sxs-lookup"><span data-stu-id="6a155-109">When you update a row at the data source, you call the UPDATE statement, which uses a unique identifier to identify the row in the table be updated.</span></span> <span data-ttu-id="6a155-110">唯一的識別項一般是主索引鍵欄位的值。</span><span class="sxs-lookup"><span data-stu-id="6a155-110">The unique identifier is typically the value of a primary key field.</span></span> <span data-ttu-id="6a155-111">UPDATE 陳述式所使用的參數包含唯一的識別項，以及要更新的資料行和值，如下列 Transact-SQL 陳述式所示。</span><span class="sxs-lookup"><span data-stu-id="6a155-111">The UPDATE statement uses parameters that contain both the unique identifier and the columns and values to be updated, as shown in the following Transact-SQL statement.</span></span>  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  <span data-ttu-id="6a155-112">參數預留位置的語法會隨資料來源而有所不同。</span><span class="sxs-lookup"><span data-stu-id="6a155-112">The syntax for parameter placeholders depends on the data source.</span></span> <span data-ttu-id="6a155-113">此範例將說明 SQL Server 資料來源的保留字元。</span><span class="sxs-lookup"><span data-stu-id="6a155-113">This example shows placeholders for a SQL Server data source.</span></span> <span data-ttu-id="6a155-114">若為 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> 參數，請使用問號 (?) 保留字元。</span><span class="sxs-lookup"><span data-stu-id="6a155-114">Use question mark (?) placeholders for <xref:System.Data.OleDb> and <xref:System.Data.Odbc> parameters.</span></span>  
  
 <span data-ttu-id="6a155-115">在 Visual Basic 範例中，`CompanyName`欄位會更新其值為`@CompanyName`資料列的參數位置`CustomerID`等於值`@CustomerID`參數。</span><span class="sxs-lookup"><span data-stu-id="6a155-115">In this Visual Basic example, the `CompanyName` field is updated with the value of the `@CompanyName` parameter for the row where `CustomerID` equals the value of the `@CustomerID` parameter.</span></span> <span data-ttu-id="6a155-116">參數會擷取資訊從修改過的資料列使用<xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A>屬性<xref:System.Data.SqlClient.SqlParameter>物件。</span><span class="sxs-lookup"><span data-stu-id="6a155-116">The parameters retrieve information from the modified row using the <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> property of the <xref:System.Data.SqlClient.SqlParameter> object.</span></span> <span data-ttu-id="6a155-117">下列是前述範例 UPDATE 陳述式的參數。</span><span class="sxs-lookup"><span data-stu-id="6a155-117">The following are the parameters for the previous sample UPDATE statement.</span></span> <span data-ttu-id="6a155-118">程式碼會假設變數 `adapter` 表示有效的 <xref:System.Data.SqlClient.SqlDataAdapter> 物件。</span><span class="sxs-lookup"><span data-stu-id="6a155-118">The code assumes that the variable `adapter` represents a valid <xref:System.Data.SqlClient.SqlDataAdapter> object.</span></span>  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 <span data-ttu-id="6a155-119">`Add` 集合的 `Parameters` 方法會擷取參數的名稱、資料型別、大小 (如果此型別有大小)，以及來自 <xref:System.Data.Common.DbParameter.SourceColumn%2A> 的 `DataTable` 名稱。</span><span class="sxs-lookup"><span data-stu-id="6a155-119">The `Add` method of the `Parameters` collection takes the name of the parameter, the data type, the size (if applicable to the type), and the name of the <xref:System.Data.Common.DbParameter.SourceColumn%2A> from the `DataTable`.</span></span> <span data-ttu-id="6a155-120">請注意，<xref:System.Data.Common.DbParameter.SourceVersion%2A> 參數的 `@CustomerID` 會設定為 `Original`。</span><span class="sxs-lookup"><span data-stu-id="6a155-120">Notice that the <xref:System.Data.Common.DbParameter.SourceVersion%2A> of the `@CustomerID` parameter is set to `Original`.</span></span> <span data-ttu-id="6a155-121">如此一來，如果已修改的 <xref:System.Data.DataRow> 內識別欄位的值有所變更，便可確保資料來源內的現有資料列也已經更新。</span><span class="sxs-lookup"><span data-stu-id="6a155-121">This guarantees that the existing row in the data source is updated if the value of the identifying column or columns has been changed in the modified <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="6a155-122">在這種情況下，`Original` 資料列值會與資料來源中的目前值相符，而 `Current` 資料列值會包含已更新的值。</span><span class="sxs-lookup"><span data-stu-id="6a155-122">In that case, the `Original` row value would match the current value at the data source, and the `Current` row value would contain the updated value.</span></span> <span data-ttu-id="6a155-123">`SourceVersion` 參數的 `@CompanyName` 並未設定，因此會使用預設的 `Current` 資料列值。</span><span class="sxs-lookup"><span data-stu-id="6a155-123">The `SourceVersion` for the `@CompanyName` parameter is not set and uses the default, `Current` row value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a155-124">`Fill` 的 `DataAdapter` 作業與 `Get` 的 `DataReader` 方法都是以 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者傳回的型別來推斷 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別。</span><span class="sxs-lookup"><span data-stu-id="6a155-124">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the type returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="6a155-125">推斷[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]型別和 Microsoft SQL Server、 OLE DB 和 ODBC 資料類型的存取子方法詳述於[ADO.NET 中的資料類型對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)。</span><span class="sxs-lookup"><span data-stu-id="6a155-125">The inferred [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and accessor methods for Microsoft SQL Server, OLE DB, and ODBC data types are described in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span>  
  
## <a name="parametersourcecolumn-parametersourceversion"></a><span data-ttu-id="6a155-126">Parameter.SourceColumn、Parameter.SourceVersion</span><span class="sxs-lookup"><span data-stu-id="6a155-126">Parameter.SourceColumn, Parameter.SourceVersion</span></span>  
 <span data-ttu-id="6a155-127">`SourceColumn` 和 `SourceVersion` 可當做參數傳遞給 `Parameter` 建構函式 (Constructor)，或設定為現有 `Parameter` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a155-127">The `SourceColumn` and `SourceVersion` may be passed as arguments to the `Parameter` constructor, or set as properties of an existing `Parameter`.</span></span> <span data-ttu-id="6a155-128">`SourceColumn` 是將在其中擷取 <xref:System.Data.DataColumn> 值之 <xref:System.Data.DataRow> 的 `Parameter` 名稱。</span><span class="sxs-lookup"><span data-stu-id="6a155-128">The `SourceColumn` is the name of the <xref:System.Data.DataColumn> from the <xref:System.Data.DataRow> where the value of the `Parameter` will be retrieved.</span></span> <span data-ttu-id="6a155-129">`SourceVersion` 會指定 `DataRow` 用來擷取值的 `DataAdapter` 版本。</span><span class="sxs-lookup"><span data-stu-id="6a155-129">The `SourceVersion` specifies the `DataRow` version that the `DataAdapter` uses to retrieve the value.</span></span>  
  
 <span data-ttu-id="6a155-130">下表顯示可與 <xref:System.Data.DataRowVersion> 搭配使用的 `SourceVersion` 列舉值。</span><span class="sxs-lookup"><span data-stu-id="6a155-130">The following table shows the <xref:System.Data.DataRowVersion> enumeration values available for use with `SourceVersion`.</span></span>  
  
|<span data-ttu-id="6a155-131">DataRowVersion 列舉型別</span><span class="sxs-lookup"><span data-stu-id="6a155-131">DataRowVersion Enumeration</span></span>|<span data-ttu-id="6a155-132">描述</span><span class="sxs-lookup"><span data-stu-id="6a155-132">Description</span></span>|  
|--------------------------------|-----------------|  
|`Current`|<span data-ttu-id="6a155-133">這個參數會使用資料行目前的值。</span><span class="sxs-lookup"><span data-stu-id="6a155-133">The parameter uses the current value of the column.</span></span> <span data-ttu-id="6a155-134">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="6a155-134">This is the default.</span></span>|  
|`Default`|<span data-ttu-id="6a155-135">此參數會使用資料行的 `DefaultValue`。</span><span class="sxs-lookup"><span data-stu-id="6a155-135">The parameter uses the `DefaultValue` of the column.</span></span>|  
|`Original`|<span data-ttu-id="6a155-136">這個參數會使用資料行的原始值。</span><span class="sxs-lookup"><span data-stu-id="6a155-136">The parameter uses the original value of the column.</span></span>|  
|`Proposed`|<span data-ttu-id="6a155-137">這個會參數使用建議值。</span><span class="sxs-lookup"><span data-stu-id="6a155-137">The parameter uses a proposed value.</span></span>|  
  
 <span data-ttu-id="6a155-138">下一區段中的 `SqlClient` 程式碼範例會定義 <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 的參數，其中 `CustomerID` 資料行將做為兩個參數的 `SourceColumn` 使用：`@CustomerID` (`SET CustomerID = @CustomerID`) 和 `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`)。</span><span class="sxs-lookup"><span data-stu-id="6a155-138">The `SqlClient` code example in the next section defines a parameter for an <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> in which the `CustomerID` column is used as a `SourceColumn` for two parameters: `@CustomerID` (`SET CustomerID = @CustomerID`), and `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`).</span></span> <span data-ttu-id="6a155-139">`@CustomerID`參數用來更新**CustomerID**資料行中的目前值`DataRow`。</span><span class="sxs-lookup"><span data-stu-id="6a155-139">The `@CustomerID` parameter is used to update the **CustomerID** column to the current value in the `DataRow`.</span></span> <span data-ttu-id="6a155-140">如此一來， `CustomerID` `SourceColumn`具有`SourceVersion`的`Current`用。</span><span class="sxs-lookup"><span data-stu-id="6a155-140">As a result, the `CustomerID` `SourceColumn` with a `SourceVersion` of `Current` is used.</span></span> <span data-ttu-id="6a155-141">`@OldCustomerID`參數用來識別資料來源中的目前資料列。</span><span class="sxs-lookup"><span data-stu-id="6a155-141">The `@OldCustomerID` parameter is used to identify the current row in the data source.</span></span> <span data-ttu-id="6a155-142">因為在資料列的 `Original` 版本中找到相符的資料行值，所以會使用 `SourceColumn` 為 `CustomerID` 的同一個 `SourceVersion` (`Original`)。</span><span class="sxs-lookup"><span data-stu-id="6a155-142">Because the matching column value is found in the `Original` version of the row, the same `SourceColumn` (`CustomerID`) with a `SourceVersion` of `Original` is used.</span></span>  
  
## <a name="working-with-sqlclient-parameters"></a><span data-ttu-id="6a155-143">使用 SqlClient 參數</span><span class="sxs-lookup"><span data-stu-id="6a155-143">Working with SqlClient Parameters</span></span>  
 <span data-ttu-id="6a155-144">下列範例將示範如何建立 <xref:System.Data.SqlClient.SqlDataAdapter> 並將 <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> 設定為 <xref:System.Data.MissingSchemaAction.AddWithKey>，以便從資料庫中擷取其他結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="6a155-144">The following example demonstrates how to create a <xref:System.Data.SqlClient.SqlDataAdapter> and set the <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> to <xref:System.Data.MissingSchemaAction.AddWithKey> in order to retrieve additional schema information from the database.</span></span> <span data-ttu-id="6a155-145"><xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 屬性已設定而且其對應的 <xref:System.Data.SqlClient.SqlParameter> 物件已加入至 <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="6a155-145">The <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties set and their corresponding <xref:System.Data.SqlClient.SqlParameter> objects added to the <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection.</span></span> <span data-ttu-id="6a155-146">此方法會傳回 `SqlDataAdapter` 物件。</span><span class="sxs-lookup"><span data-stu-id="6a155-146">The method returns a `SqlDataAdapter` object.</span></span>  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a><span data-ttu-id="6a155-147">OleDb 參數預留位置</span><span class="sxs-lookup"><span data-stu-id="6a155-147">OleDb Parameter Placeholders</span></span>  
 <span data-ttu-id="6a155-148">若為 <xref:System.Data.OleDb.OleDbDataAdapter> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，則必須使用問號 (?) 保留字元來識別參數。</span><span class="sxs-lookup"><span data-stu-id="6a155-148">For the <xref:System.Data.OleDb.OleDbDataAdapter> and <xref:System.Data.Odbc.OdbcDataAdapter> objects, you must use question mark (?) placeholders to identify the parameters.</span></span>  
  
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
  
 <span data-ttu-id="6a155-149">參數化的查詢陳述式可定義必須建立的輸入和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="6a155-149">The parameterized query statements define which input and output parameters must be created.</span></span> <span data-ttu-id="6a155-150">若要建立參數，請使用 `Parameters.Add` 方法或 `Parameter` 建構函式來指定資料行名稱、資料型別和大小。</span><span class="sxs-lookup"><span data-stu-id="6a155-150">To create a parameter, use the `Parameters.Add` method or the `Parameter` constructor to specify the column name, data type, and size.</span></span> <span data-ttu-id="6a155-151">如果資料型別為內建 (如 `Integer`)，則沒有必要包含大小，或者您也可以指定預設大小。</span><span class="sxs-lookup"><span data-stu-id="6a155-151">For intrinsic data types, such as `Integer`, you do not have to include the size, or you can specify the default size.</span></span>  
  
 <span data-ttu-id="6a155-152">下列程式碼範例會建立 SQL 陳述式的參數，然後填入 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="6a155-152">The following code example creates the parameters for a SQL statement and then fills a `DataSet`.</span></span>  
  
## <a name="oledb-example"></a><span data-ttu-id="6a155-153">OleDb 範例</span><span class="sxs-lookup"><span data-stu-id="6a155-153">OleDb Example</span></span>  
  
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
  
## <a name="odbc-parameters"></a><span data-ttu-id="6a155-154">Odbc 參數</span><span class="sxs-lookup"><span data-stu-id="6a155-154">Odbc Parameters</span></span>  
  
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
>  <span data-ttu-id="6a155-155">若參數名稱不提供給參數，參數會指定參數的累加預設名稱*N* *，* 從"Parameter1"開始。</span><span class="sxs-lookup"><span data-stu-id="6a155-155">If a parameter name is not supplied for a parameter, the parameter is given an incremental default name of Parameter*N* *,* starting with "Parameter1".</span></span> <span data-ttu-id="6a155-156">我們建議您避免使用 Parameter*N*命名慣例，當您提供參數名稱，因為您所提供的名稱，可能會與現有的預設參數名稱中的衝突`ParameterCollection`。</span><span class="sxs-lookup"><span data-stu-id="6a155-156">We recommend that you avoid the Parameter*N* naming convention when you supply a parameter name, because the name that you supply might conflict with an existing default parameter name in the `ParameterCollection`.</span></span> <span data-ttu-id="6a155-157">如果提供的名稱已經存在，便會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6a155-157">If the supplied name already exists, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a155-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a155-158">See Also</span></span>  
 [<span data-ttu-id="6a155-159">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="6a155-159">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="6a155-160">命令和參數</span><span class="sxs-lookup"><span data-stu-id="6a155-160">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="6a155-161">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="6a155-161">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="6a155-162">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="6a155-162">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="6a155-163">ADO.NET 中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="6a155-163">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="6a155-164">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6a155-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
