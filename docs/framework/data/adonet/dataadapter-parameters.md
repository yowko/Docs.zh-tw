---
title: "DataAdapter 參數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DataAdapter 參數
<xref:System.Data.Common.DbDataAdapter> 具有四個屬性，可用來擷取資料來源的資料，以及將資料更新至資料來源：<xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> 屬性可傳回資料來源的資料，而 <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 屬性可用來管理在資料來源的變更。  在您呼叫 `DataAdapter` 的 `Fill` 方法前，必須先設定 `SelectCommand` 屬性。  您必須先設定 `InsertCommand`、`UpdateCommand` 或 `DeleteCommand` 屬性，然後再呼叫 `DataAdapter` 的 `Update` 方法，端視針對 <xref:System.Data.DataTable> 中的資料進行哪些變更而定。  例如，如果已經加入資料列，則必須先設定 `InsertCommand`，才能呼叫 `Update`。  `Update` 正在處理已插入、已更新或已刪除的資料列時，`DataAdapter` 會使用個別的 `Command` 屬性來處理這項動作。  已修改資料列的目前資訊會透過 `Parameters` 集合傳遞給 `Command` 物件。  
  
 更新資料來源的資料列時，您呼叫的 UPDATE 陳述式會使用唯一的識別項來識別資料表中需要更新的資料列。  唯一的識別項一般是主索引鍵欄位的值。  UPDATE 陳述式所使用的參數包含唯一的識別項，以及要更新的資料行和值，如下列 Transact\-SQL 陳述式所示。  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  參數預留位置的語法會隨資料來源而有所不同。  此範例將說明 SQL Server 資料來源的保留字元。  若為 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> 參數，請使用問號 \(?\) 保留字元。  
  
 在此 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 範例中，會針對 `CustomerID` 等於 `@CustomerID```參數值的資料列，以 `@CompanyName` 參數的值來更新 `CompanyName` 欄位。  這些參數會使用 <xref:System.Data.SqlClient.SqlParameter> 物件的 <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> 屬性，從已修改的資料列擷取資訊。  下列是前述範例 UPDATE 陳述式的參數。  程式碼會假設變數 `adapter` 表示有效的 <xref:System.Data.SqlClient.SqlDataAdapter> 物件。  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Parameters` 集合的 `Add` 方法會擷取參數的名稱、資料型別、大小 \(如果此型別有大小\)，以及來自 `DataTable` 的 <xref:System.Data.Common.DbParameter.SourceColumn%2A> 名稱。  請注意，`@CustomerID` 參數的 <xref:System.Data.Common.DbParameter.SourceVersion%2A> 會設定為 `Original`。  如此一來，如果已修改的 <xref:System.Data.DataRow> 內識別欄位的值有所變更，便可確保資料來源內的現有資料列也已經更新。  在這種情況下，`Original` 資料列值會與資料來源中的目前值相符，而 `Current` 資料列值會包含已更新的值。  `@CompanyName` 參數的 `SourceVersion` 並未設定，因此會使用預設的 `Current` 資料列值。  
  
> [!NOTE]
>  `DataAdapter` 的 `Fill` 作業與 `DataReader` 的 `Get` 方法都是以 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者傳回的型別來推斷 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別。  Microsoft SQL Server、OLE DB 和 ODBC 之資料型別的推斷 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別和存取子方法詳述於[ADO.NET 中的資料型別對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)。  
  
## Parameter.SourceColumn、Parameter.SourceVersion  
 `SourceColumn` 和 `SourceVersion` 可當做參數傳遞給 `Parameter` 建構函式 \(Constructor\)，或設定為現有 `Parameter` 的屬性。  `SourceColumn` 是將在其中擷取 `Parameter` 值之 <xref:System.Data.DataRow> 的 <xref:System.Data.DataColumn> 名稱。  `SourceVersion` 會指定 `DataAdapter` 用來擷取值的 `DataRow` 版本。  
  
 下表顯示可與 `SourceVersion` 搭配使用的 <xref:System.Data.DataRowVersion> 列舉值。  
  
|DataRowVersion 列舉型別|描述|  
|-------------------------|--------|  
|`Current`|這個參數會使用資料行目前的值。  這是預設值。|  
|`Default`|此參數會使用資料行的 `DefaultValue`。|  
|`Original`|這個參數會使用資料行的原始值。|  
|`Proposed`|這個會參數使用建議值。|  
  
 下一區段中的 `SqlClient` 程式碼範例會定義 <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 的參數，其中 `CustomerID` 資料行將做為兩個參數的 `SourceColumn` 使用：`@CustomerID` \(`SET CustomerID = @CustomerID`\) 和 `@OldCustomerID` \(`WHERE CustomerID = @OldCustomerID`\)。  `@CustomerID` 參數會用來將 **CustomerID** 資料行更新為 `DataRow` 中目前的值。  因此會使用包含 `Current` 之 `SourceVersion` 的 `CustomerID` `SourceColumn`。  *@OldCustomerID* 參數是用來識別資料來源中的目前資料列。  因為在資料列的 `Original` 版本中找到相符的資料行值，所以會使用 `SourceVersion` 為 `Original` 的同一個 `SourceColumn` \(`CustomerID`\)。  
  
## 使用 SqlClient 參數  
 下列範例將示範如何建立 <xref:System.Data.SqlClient.SqlDataAdapter> 並將 <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> 設定為 <xref:System.Data.MissingSchemaAction>，以便從資料庫中擷取其他結構描述資訊。  <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 屬性已設定而且其對應的 <xref:System.Data.SqlClient.SqlParameter> 物件已加入至 <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合。  此方法會傳回 `SqlDataAdapter` 物件。  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## OleDb 參數預留位置  
 若為 <xref:System.Data.OleDb.OleDbDataAdapter> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，則必須使用問號 \(?\) 保留字元來識別參數。  
  
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
  
 參數化的查詢陳述式可定義必須建立的輸入和輸出參數。  若要建立參數，請使用 `Parameters.Add` 方法或 `Parameter` 建構函式來指定資料行名稱、資料型別和大小。  如果資料型別為內建 \(如 `Integer`\)，則沒有必要包含大小，或者您也可以指定預設大小。  
  
 下列程式碼範例會建立 SQL 陳述式的參數，然後填入 `DataSet`。  
  
## OleDb 範例  
  
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
  
## Odbc 參數  
  
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
>  若未提供參數名稱給參數，則系統會為參數指定 Parameter*N* 的累加預設名稱，並且是從 "Parameter1" 開始。  當您提供參數名稱時，建議您避免使用 Parameter*N* 命名慣例，因為您所提供的名稱可能會與 `ParameterCollection` 中現有的預設參數名稱衝突。  如果提供的名稱已經存在，便會發生例外狀況。  
  
## 請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [以 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)   
 [使用預存程序修改資料](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)   
 [ADO.NET 中的資料型別對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)