---
title: DataAdapter 的參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
ms.openlocfilehash: e633c7cdd105125fc5fb595566d15cf5f5fe4e6f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845609"
---
# <a name="dataadapter-parameters"></a>DataAdapter 的參數
<xref:System.Data.Common.DbDataAdapter> 具有四個屬性，可用來擷取資料來源的資料，以及將資料更新至資料來源：<xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> 屬性可傳回資料來源的資料，而 <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 屬性可用來管理在資料來源的變更。 在您呼叫 `SelectCommand` 的 `Fill` 方法前，必須先設定 `DataAdapter` 屬性。 您必須先設定 `InsertCommand`、`UpdateCommand` 或 `DeleteCommand` 屬性，然後再呼叫 `Update` 的 `DataAdapter` 方法，端視針對 <xref:System.Data.DataTable> 中的資料進行哪些變更而定。 例如，如果已經加入資料列，則必須先設定 `InsertCommand`，才能呼叫 `Update`。 `Update` 正在處理已插入、已更新或已刪除的資料列時，`DataAdapter` 會使用個別的 `Command` 屬性來處理這項動作。 已修改資料列的目前資訊會透過 `Command` 集合傳遞給 `Parameters` 物件。  
  
 更新資料來源的資料列時，您呼叫的 UPDATE 陳述式會使用唯一的識別項來識別資料表中需要更新的資料列。 唯一的識別項一般是主索引鍵欄位的值。 UPDATE 陳述式所使用的參數包含唯一的識別項，以及要更新的資料行和值，如下列 Transact-SQL 陳述式所示。  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  參數預留位置的語法會隨資料來源而有所不同。 此範例將說明 SQL Server 資料來源的保留字元。 若為 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> 參數，請使用問號 (?) 保留字元。  
  
 在 Visual Basic 範例中，`CompanyName`欄位會更新其值為`@CompanyName`資料列的參數位置`CustomerID`等於值`@CustomerID`參數。 參數會擷取資訊從修改過的資料列使用<xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A>屬性<xref:System.Data.SqlClient.SqlParameter>物件。 下列是前述範例 UPDATE 陳述式的參數。 程式碼會假設變數 `adapter` 表示有效的 <xref:System.Data.SqlClient.SqlDataAdapter> 物件。  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Add` 集合的 `Parameters` 方法會擷取參數的名稱、資料型別、大小 (如果此型別有大小)，以及來自 <xref:System.Data.Common.DbParameter.SourceColumn%2A> 的 `DataTable` 名稱。 請注意，<xref:System.Data.Common.DbParameter.SourceVersion%2A> 參數的 `@CustomerID` 會設定為 `Original`。 如此一來，如果已修改的 <xref:System.Data.DataRow> 內識別欄位的值有所變更，便可確保資料來源內的現有資料列也已經更新。 在這種情況下，`Original` 資料列值會與資料來源中的目前值相符，而 `Current` 資料列值會包含已更新的值。 `SourceVersion` 參數的 `@CompanyName` 並未設定，因此會使用預設的 `Current` 資料列值。  
  
> [!NOTE]
>  `Fill` 的 `DataAdapter` 作業與 `Get` 的 `DataReader` 方法都是以 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者傳回的型別來推斷 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別。 推斷[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]型別和 Microsoft SQL Server、 OLE DB 和 ODBC 資料類型的存取子方法詳述於[ADO.NET 中的資料類型對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)。  
  
## <a name="parametersourcecolumn-parametersourceversion"></a>Parameter.SourceColumn、Parameter.SourceVersion  
 `SourceColumn` 和 `SourceVersion` 可當做參數傳遞給 `Parameter` 建構函式 (Constructor)，或設定為現有 `Parameter` 的屬性。 `SourceColumn` 是將在其中擷取 <xref:System.Data.DataColumn> 值之 <xref:System.Data.DataRow> 的 `Parameter` 名稱。 `SourceVersion` 會指定 `DataRow` 用來擷取值的 `DataAdapter` 版本。  
  
 下表顯示可與 <xref:System.Data.DataRowVersion> 搭配使用的 `SourceVersion` 列舉值。  
  
|DataRowVersion 列舉型別|描述|  
|--------------------------------|-----------------|  
|`Current`|這個參數會使用資料行目前的值。 這是預設值。|  
|`Default`|此參數會使用資料行的 `DefaultValue`。|  
|`Original`|這個參數會使用資料行的原始值。|  
|`Proposed`|這個會參數使用建議值。|  
  
 下一區段中的 `SqlClient` 程式碼範例會定義 <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 的參數，其中 `CustomerID` 資料行將做為兩個參數的 `SourceColumn` 使用：`@CustomerID` (`SET CustomerID = @CustomerID`) 和 `@OldCustomerID` (`WHERE CustomerID = @OldCustomerID`)。 `@CustomerID`參數用來更新**CustomerID**資料行中的目前值`DataRow`。 如此一來， `CustomerID` `SourceColumn`具有`SourceVersion`的`Current`用。 `@OldCustomerID`參數用來識別資料來源中的目前資料列。 因為在資料列的 `Original` 版本中找到相符的資料行值，所以會使用 `SourceColumn` 為 `CustomerID` 的同一個 `SourceVersion` (`Original`)。  
  
## <a name="working-with-sqlclient-parameters"></a>使用 SqlClient 參數  
 下列範例將示範如何建立 <xref:System.Data.SqlClient.SqlDataAdapter> 並將 <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> 設定為 <xref:System.Data.MissingSchemaAction.AddWithKey>，以便從資料庫中擷取其他結構描述資訊。 <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 屬性已設定而且其對應的 <xref:System.Data.SqlClient.SqlParameter> 物件已加入至 <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合。 此方法會傳回 `SqlDataAdapter` 物件。  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## <a name="oledb-parameter-placeholders"></a>OleDb 參數預留位置  
 若為 <xref:System.Data.OleDb.OleDbDataAdapter> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，則必須使用問號 (?) 保留字元來識別參數。  
  
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
  
 參數化的查詢陳述式可定義必須建立的輸入和輸出參數。 若要建立參數，請使用 `Parameters.Add` 方法或 `Parameter` 建構函式來指定資料行名稱、資料型別和大小。 如果資料型別為內建 (如 `Integer`)，則沒有必要包含大小，或者您也可以指定預設大小。  
  
 下列程式碼範例會建立 SQL 陳述式的參數，然後填入 `DataSet`。  
  
## <a name="oledb-example"></a>OleDb 範例  
  
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
  
## <a name="odbc-parameters"></a>Odbc 參數  
  
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
>  若參數名稱不提供給參數，參數會指定參數的累加預設名稱*N* *，* 從"Parameter1"開始。 我們建議您避免使用 Parameter*N*命名慣例，當您提供參數名稱，因為您所提供的名稱，可能會與現有的預設參數名稱中的衝突`ParameterCollection`。 如果提供的名稱已經存在，便會發生例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [使用 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [使用預存程序修改資料](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET 中的資料類型對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
