---
title: 資料表值參數
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: b968c599cf061fbd03b7ba8fb19470f6ace11a55
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202179"
---
# <a name="table-valued-parameters"></a>資料表值參數
資料表值參數提供從用戶端應用程式，將多個資料列的資料封送至 SQL Sever 的簡便方式，而不需多次來回存取或特殊的伺服器端邏輯才能處理資料。 您可以使用資料表值參數，以一個參數化命令在用戶端應用程式中封裝資料列的資料，並傳送至伺服器。 傳入的資料列會儲存於資料表變數中，之後可使用 Transact-SQL 進行運算。  
  
 資料表值參數中的資料行值可透過標準的 Transact-SQL SELECT 陳述式加以存取。 資料表值參數為強型別參數，其結構會自動驗證。 資料表值參數的大小只受限於伺服器記憶體。  
  
> [!NOTE]
> 您無法以資料表值參數傳回資料。 資料表值參數是僅限輸入；不支援 OUTPUT 關鍵字。  
  
 如需有關資料表值參數的詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[使用資料表值參數 (Database Engine)](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|描述如何建立及使用資料表值參數。|  
|[使用者定義資料表類型](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))|說明用來宣告資料表值參數的使用者定義資料表類型。|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>在舊版 SQL Server 中傳遞多個資料列  
 在 SQL Server 2008 中引進資料表值參數之前，將多個資料列傳遞至預存程序或參數化 SQL 命令的選項有所限制。 開發人員可以從下列選項中選擇將多個資料列傳遞至伺服器的方式：  
  
- 使用一系列的個別參數來代表多個資料行與資料列中的值。 使用這個方法時，可以傳遞的資料量會受到允許的參數數目限制。 SQL Server 程序最多可以有 2100 個參數。 需要伺服器端邏輯，才能將這些個別的值組合成資料表變數或暫存資料表來進行處理。  
  
- 將多個資料值組合成分隔字串或 XML 文件，然後將那些文字值傳遞給程序或陳述式。 這需要程序或陳述式包含驗證資料結構及拆開值所需的邏輯。  
  
- 針對會影響多個資料列的資料修改建立一系列的獨立 SQL 陳述式，例如透過呼叫 <xref:System.Data.SqlClient.SqlDataAdapter> 的 `Update` 方法所建立的陳述式。 變更可以以個別方式，或以批次處理成群組的方式提交給伺服器。 不過，即使是以包含多個陳述式的批次方式提交，每個陳述式都會在伺服器上個別執行。  
  
- 使用 `bcp` 公用程式或 <xref:System.Data.SqlClient.SqlBulkCopy> 物件，將許多資料列載入至資料表。 雖然此技術非常有效率，但除非將資料載入暫存資料表或資料表變數中，否則不支援伺服器端處理。  
  
## <a name="creating-table-valued-parameter-types"></a>建立資料表值參數型別  
 資料表值參數是以使用 Transact-sql CREATE TYPE 語句所定義的強型別資料表結構為基礎。 您必須先在 SQL Server 中建立資料表類型並定義此結構，然後才能在用戶端應用程式中使用資料表值參數。 如需建立資料表類型的詳細資訊，請參閱[使用者定義資料表類型](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))。  
  
 下列陳述式會建立名為 CategoryTableType 的資料表類型，其中包含 CategoryID 與 CategoryName 資料行：  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 建立資料表類型之後，您可以根據該類型來宣告資料表值參數。 下列 Transact-SQL 片段將示範如何在預存程序定義中宣告資料表值參數。 請注意，必須要有 READONLY 關鍵字才能宣告資料表值參數。  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>使用資料表值參數 &#40;transact-SQL&#41; 修改資料  
 資料表值參數可透過執行單一陳述式，在以集合為基礎且會影響多個資料列的資料修改中使用。 例如，您可以選取資料表值參數中的所有資料列，並將其插入資料庫資料表中，或者您可以透過將資料表值參數聯結至您要更新的資料表，以建立更新陳述式。  
  
 下列 Transact-SQL UPDATE 陳述式會示範如何將資料表值參數聯結至 Categories 資料表，藉以運用此參數。 當您在 FROM 子句中搭配 JOIN 使用資料表值參數時，也必須為其設定別名，例如下方所示，其中資料表值參數設定別名 "ec"：  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 這個 Transact-SQL 範例將示範如何從資料表值參數中選取資料列，以便在單一集合式作業中執行 INSERT。  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>資料表值參數的限制  
 資料表值參數有幾項限制：  
  
- 您無法將資料表值參數傳遞至 [CLR 使用者定義函式](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)。  
  
- 資料表值參數只能編製索引，以支援 UNIQUE 或 PRIMARY KEY 條件約束。 SQL Server 不會維護資料表值參數的統計資料。  
  
- 資料表值參數在 Transact-SQL 程式碼中處於唯讀狀態。 您無法更新資料表值參數資料列中的資料行值，也無法插入或刪除資料列。 若要在資料表值參數中修改傳遞至預存程序或參數化陳述式的資料，您必須將資料插入至暫存資料表或資料表變數中。  
  
- 您無法使用 ALTER TABLE 陳述式來修改資料表值參數的設計。  
  
## <a name="configuring-a-sqlparameter-example"></a>設定 SqlParameter 範例  
 <xref:System.Data.SqlClient> 支援從 <xref:System.Data.DataTable>、<xref:System.Data.Common.DbDataReader> 或 <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord>物件填入資料表值參數。 您必須使用 <xref:System.Data.SqlClient.SqlParameter> 的 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 屬性來指定資料表值參數的類型名稱。 `TypeName` 必須與先前在伺服器上所建立的相容型別名稱相符。 下列程式碼片段示範如何設定 <xref:System.Data.SqlClient.SqlParameter> 以插入資料。  

在下列範例中，`addedCategories` 變數包含 <xref:System.Data.DataTable>。 若要查看變數的填入方式，請參閱下一節中的範例，[將資料表值參數傳遞至預存程序](#passing)。

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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a>將資料表值參數傳遞至預存程式  
 此範例示範如何將資料表值參數資料傳遞至預存程序。 程式碼會透過使用 <xref:System.Data.DataTable.GetChanges%2A> 方法，將加入的資料列解壓縮至新的 <xref:System.Data.DataTable> 之中。 然後，程式碼會定義 <xref:System.Data.SqlClient.SqlCommand>，將 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 屬性設定為 <xref:System.Data.CommandType.StoredProcedure>。 <xref:System.Data.SqlClient.SqlParameter> 是使用 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 方法填入的，而且 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 會設定為 `Structured`。 然後使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法來執行 <xref:System.Data.SqlClient.SqlCommand>。  
  
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
 下列範例示範如何使用 INSERT 陳述式搭配以資料表值參數作為資料來源的 SELECT 子查詢，將資料插入至 dbo.Category 資料表。 將資料表值參數傳遞至參數化 SQL 陳述式時，您必須使用 <xref:System.Data.SqlClient.SqlParameter> 的新 <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> 屬性來指定資料表值參數的類型名稱。 這個 `TypeName` 必須與先前在伺服器上所建立的相容型別名稱相符。 此範例中的程式碼會使用 `TypeName` 屬性來參考 dbo.CategoryTableType 中定義的型別結構。  
  
> [!NOTE]
> 如果您在資料表值參數中提供識別資料行的值，就必須為該工作階段發出 SET IDENTITY_INSERT 陳述式。  
  
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
 您也可以使用衍生自 <xref:System.Data.Common.DbDataReader> 的任何物件，將資料列的資料流導引至資料表值參數。 下列程式碼片段示範如何使用 <xref:System.Data.OracleClient.OracleCommand> 與 <xref:System.Data.OracleClient.OracleDataReader>，從 Oracle 資料庫擷取資料。 然後，程式碼會設定 <xref:System.Data.SqlClient.SqlCommand>，以使用單一輸入參數來叫用預存程序。 <xref:System.Data.SqlClient.SqlParameter> 的 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> 屬性會設定為 `Structured`。 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> 會將 `OracleDataReader` 結果集以資料表值參數的方式傳遞至預存程序。  
  
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

- [設定參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)
- [命令和參數](../commands-and-parameters.md)
- [DataAdapter 的參數](../dataadapter-parameters.md)
- [SQL Server ADO.NET 中的資料作業](sql-server-data-operations.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
