---
title: 資料表值參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 333154f26a575886f19a914ce2f91beebd6be49e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742512"
---
# <a name="table-valued-parameters"></a>資料表值參數
資料表值參數提供封送處理的簡易方式，可將用戶端應用程式的多個資料列封送處理到 SQL Server，而不需多次來回存取或使用特殊的伺服器端邏輯來處理資料。 您可以使用資料表值參數，在用戶端應用程式中封裝資料列，以及在單一參數型命令 (Parameterized Command) 中，將資料傳送至伺服器。 內送資料列會儲存在資料表變數中，然後您可以使用 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 來操作此變數。  
  
 資料表值參數中的資料行值可透過標準的 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT 陳述式加以存取。 資料表值參數為強型別 (Strongly Typed)，其結構會自動驗證。 資料表值參數的大小僅受到伺服器記憶體的限制。  
  
> [!NOTE]
>  您不能以資料表值參數傳回資料。 資料表值參數只能接受輸入；OUTPUT 關鍵字不受支援。  
  
 如需資料表值參數的詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[資料表值參數 (Database Engine)](https://go.microsoft.com/fwlink/?LinkId=98363)中 SQL Server 線上叢書|說明如何建立及使用資料表值參數。|  
|[使用者定義資料表類型](https://go.microsoft.com/fwlink/?LinkId=98364)中 SQL Server 線上叢書|說明用於宣告資料表值參數的使用者定義資料表型別。|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>在舊版 SQL Server 中傳遞多個資料列  
 SQL Server 2008 導入資料表值參數之前，將多個資料列傳遞至預存程序或參數化的 SQL 命令的選項有所限制。 若要將多個資料列傳遞至伺服器，開發人員可能會從下列選項中選擇：  
  
-   使用一連串個別的參數來代表多個資料行和資料列中的值。 使用這個方法可傳遞的資料量會受到允許的參數數目所限制。 SQL Server 程序最多可以有 2100 個參數。 伺服器端邏輯必須將這些個別的值組合成資料表變數或暫存資料表，以便進行處理。  
  
-   將多個資料值包裝成分隔字串或 XML 文件，然後將這些文字值傳遞至程序或陳述式 (Statement)。 此程序或陳述式必須包含驗證資料結構和取消包裝值所需的邏輯。  
  
-   針對影響多個資料列的資料修改項目建立一連串個別的 SQL 陳述式，例如呼叫 `Update` 之 <xref:System.Data.SqlClient.SqlDataAdapter> 方法所建立的修改項目。 您可以將變更個別送出至伺服器，也可以將它們批次處理成為群組。 不過，即使按照包含多個陳述式的批次送出，每個陳述式仍然會分別在伺服器上執行。  
  
-   使用 `bcp` 公用程式或 <xref:System.Data.SqlClient.SqlBulkCopy> 物件，將許多資料列載入資料表中。 雖然這項技術非常有效率，不過除非資料會載入暫存資料表或資料表變數中，否則它不支援伺服器端處理。  
  
## <a name="creating-table-valued-parameter-types"></a>建立資料表值參數型別  
 資料表值參數是以使用 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE 陳述式所定義的強型別資料表結構為基礎。 您必須先在 SQL Server 中建立資料表型別並定義此結構，然後才能在用戶端應用程式中使用資料表值參數。 如需建立資料表類型的詳細資訊，請參閱[使用者定義資料表類型](https://go.microsoft.com/fwlink/?LinkID=98364)SQL Server 線上叢書 》 中。  
  
 下列陳述式會建立名為 CategoryTableType 的資料表型別，其中包含 CategoryID 和 CategoryName 資料行：  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 建立資料表型別之後，您就可以根據該型別來宣告資料表值參數。 下列 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 片段將示範如何在預存程序定義中宣告資料表值參數。 請注意，READONLY 關鍵字是宣告資料表值參數的必要項目。  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>使用資料表值參數來修改資料 (Transact-SQL)  
 資料表值參數可用於透過執行單一陳述式來影響多個資料列的集合式資料修改作業中。 例如，您可以選擇資料表值參數中的所有資料列，然後將其插入至資料庫資料表，或者將資料表值參數與您要更新的資料表聯結 (Join) 而建立更新陳述式。  
  
 下列 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE 陳述式會示範如何將資料表值參數聯結至 Categories 資料表，藉以運用此參數。 當您在 FROM 子句中使用資料表值參數搭配 JOIN 時，也必須設定其別名，如下面所示，其中資料表值參數的別名設定為 "ec"：  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 這個 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 範例將示範如何從資料表值參數中選取資料列，以便在單一集合式作業中執行 INSERT。  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>資料表值參數的限制  
 資料表值參數有許多限制：  
  
-   您無法將資料表值參數傳遞[CLR 使用者定義函式](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)。  
  
-   資料表值參數只能針對支援 UNIQUE 或 PRIMARY KEY 條件約束 (Constraint) 而建立索引。 SQL Server 不會維護資料表值參數的統計資料。  
  
-   資料表值參數在 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 程式碼中處於唯讀狀態。 您無法更新資料表值參數之資料列中的資料行值，也無法插入或刪除資料列。 若要修改在資料表值參數中傳遞至預存程序或參數化陳述式的資料，您必須將這項資料插入暫存資料表或資料表變數中。  
  
-   您無法使用 ALTER TABLE 陳述式來修改資料表值參數的設計。  
  
## <a name="configuring-a-sqlparameter-example"></a>設定 SqlParameter 範例  
 <xref:System.Data.SqlClient> 支援填入資料表值參數<xref:System.Data.DataTable>，<xref:System.Data.Common.DbDataReader>或是<xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord>物件。 您必須使用 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 的 <xref:System.Data.SqlClient.SqlParameter> 屬性來指定資料表值參數的型別名稱。 `TypeName` 必須與之前在伺服器上所建立之相容型別的名稱相符。 下列程式碼片段示範如何設定 <xref:System.Data.SqlClient.SqlParameter> 以插入資料。  
  
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
  
 您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數，如本片段所示：  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a>將資料表值參數傳遞至預存程序  
 這則範例會示範如何將資料表值參數資料傳遞至預存程序。 此程式碼會使用 <xref:System.Data.DataTable> 方法來擷取加入至新 <xref:System.Data.DataTable.GetChanges%2A> 的資料列。 然後，此程式碼會定義 <xref:System.Data.SqlClient.SqlCommand>，並將 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 屬性設定成 <xref:System.Data.CommandType.StoredProcedure>。 <xref:System.Data.SqlClient.SqlParameter> 是使用 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 方法填入的，而且 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 會設定為 `Structured`。 接著，系統就會使用 <xref:System.Data.SqlClient.SqlCommand> 方法來執行 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>。  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>將資料表值參數傳遞至參數化 SQL 陳述式  
 下列範例會示範如何使用 INSERT 陳述式搭配具有資料表值參數當做資料來源的 SELECT 子查詢，將資料插入 dbo.Categories 資料表中。 將資料表值參數傳遞至參數化 SQL 陳述式時，您必須使用 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 的新 <xref:System.Data.SqlClient.SqlParameter> 屬性來指定資料表值參數的型別名稱。 這個 `TypeName` 必須與之前在伺服器上所建立之相容型別的名稱相符。 這則範例中的程式碼會使用 `TypeName` 屬性來參考 dbo.CategoryTableType 中定義的型別結構。  
  
> [!NOTE]
>  如果您針對資料表值參數中的識別資料行提供一個值，就必須發出此工作階段 (Session) 的 SET IDENTITY_INSERT 陳述式。  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>使用 DataReader 來資料流處理資料列  
 您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數。 下列程式碼片段會示範如何使用 <xref:System.Data.OracleClient.OracleCommand> 和 <xref:System.Data.OracleClient.OracleDataReader>，從 Oracle 資料庫中擷取資料。 然後，此程式碼會設定 <xref:System.Data.SqlClient.SqlCommand>，以便使用單一輸入參數來叫用 (Invoke) 預存程序。 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 的 <xref:System.Data.SqlClient.SqlParameter> 屬性會設定為 `Structured`。 最後，<xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 會將 `OracleDataReader` 結果集傳遞至預存程序，當做資料表值參數。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [設定參數和參數資料類型](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [命令和參數](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapter 參數](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [ADO.NET 中的 SQL Server 資料作業](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
