---
title: "使用 DataReader 擷取資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 使用 DataReader 擷取資料
使用 **DataReader** 擷取資料時會建立 **Command** 物件的執行個體，再藉由呼叫 **Command.ExecuteReader** 擷取資料來源的資料列，建立 **DataReader**。  下列範例將說明如何使用 **DataReader**，其中 `reader` 代表有效的 DataReader 而 `command` 代表有效的 Command 物件。  
  
```  
reader = command.ExecuteReader();  
```  
  
 您使用 **DataReader** 物件的 **Read** 方法，從查詢結果取得資料列。  您可以將資料行的名稱或循序參考傳遞給 **DataReader**，以存取傳回資料列的每個資料行。  不過，為了達到最佳效能，**DataReader** 也提供了一系列方法，讓您以資料行的原生資料型別 \(Native Data Type\)\(**GetDateTime**、**GetDouble**、**GetGuid**、**GetInt32** 等等\) 存取資料行的值。  如需資料提供者特有 **DataReaders** 之具型別存取子方法的清單，請參閱 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.SqlClient.SqlDataReader>。  假設已知基礎資料型別時，若使用具型別的存取子方法，可減少擷取資料行值時所需的型別轉換量。  
  
> [!NOTE]
>  .NET Framework 的 Windows Server 2003 版本包括 **DataReader**、**HasRows** 的額外屬性，可讓您在讀取 **DataReader** 傳回的結果前，先判斷是否已傳回該結果。  
  
 下列程式碼範例在 **DataReader** 物件中重複，並從每個資料列傳回兩個資料行。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader** 提供未緩衝的資料流，可使程序邏輯有效地循序處理來自資料來源的結果。  需要擷取大量資料時，**DataReader** 是不錯的選擇，因為資料不會快取至記憶體。  
  
## 關閉 DataReader  
 用完 **DataReader** 物件後，請務必呼叫 **Close** 方法。  
  
 如果您的 **Command** 包含輸出參數或傳回值，則必須等到 **DataReader** 關閉後才能使用它們。  
  
 請注意，**DataReader** 開啟期間，**Connection** 只能供該 **DataReader** 使用。  必須等到原始 **DataReader** 關閉後，才能執行 **Connection** 的任何命令，包括建立其他 **DataReader**。  
  
> [!NOTE]
>  請不要在 **Connection** 上呼叫 **Close** 或 **Dispose**、呼叫 **DataReader**，或您類別的 **Finalize** 方法中的任何其他 Managed  物件。  在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。  如果類別未擁有任何 Unmanaged 資源，請不要在類別定義中包含 **Finalize** 方法。  如需詳細資訊，請參閱[Garbage Collection](../../../../docs/standard/garbage-collection/index.md)。  
  
## 使用 NextResult 來擷取多個結果集  
 如果傳回多個結果集，**DataReader** 會提供 **NextResult** 方法依序在結果集中重複。  下列範例顯示 <xref:System.Data.SqlClient.SqlDataReader> 使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法，處理兩個 SELECT 陳述式的結果。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## 從 DataReader 取得結構描述資訊  
 **DataReader** 開啟期間，您可以使用 **GetSchemaTable** 方法擷取目前結果集的結構描述資訊。  **GetSchemaTable** 傳回 <xref:System.Data.DataTable> 物件，其內填入內含目前結果集之結構描述資訊的資料列和資料行。  **DataTable** 將針對結果集的每個資料行包含一個資料列。  結構描述資料表資料列的每個資料行會對應至結果集內所傳回的資料行屬性，其中 **ColumnName** 等於屬性名稱，而資料行值則等於屬性的值。  下列程式碼範例會寫出 **DataReader** 的結構描述資訊。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## 使用 OLE DB 章節  
 您可以使用 <xref:System.Data.OleDb.OleDbDataReader> 擷取階層式資料列集或章節 \(OLE DB 型別 **DBTYPE\_HCHAPTER**、ADO 型別 **adChapter**\)。  包含章節的查詢傳回為 **DataReader** 時，章節會傳回為 **DataReader** 中的資料行並公開為 **DataReader** 物件。  
  
 您也可以使用 ADO.NET **DataSet** 來表示階層式資料列集，方法是在資料表間使用父子關係。  如需詳細資訊，請參閱[DataSet、DataTable 及 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)。  
  
 下列程式碼範例使用 MSDataShape 提供者，替客戶清單中每位客戶的訂單產生章節資料行。  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## 使用 Oracle REF CURSOR 來傳回結果  
 Oracle 的 .NET Framework 資料提供者支援使用 Oracle REF CURSOR 傳回查詢結果。  Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 傳回。  
  
 您可以擷取 **OracleDataReader** 物件 \(其表示使用 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> 方法的 Oracle REF CURSOR\)，也可以指定傳回一或多個 Oracle REF CURSOR 的 <xref:System.Data.OracleClient.OracleCommand>，做為讓 <xref:System.Data.OracleClient.OracleDataAdapter> 用來填入 <xref:System.Data.DataSet> 的 **SelectCommand**。  
  
 若要存取從 Oracle 資料來源傳回的 REF CURSOR，請為查詢建立一個 **OracleCommand**，並參考 REF CURSOR 的輸出參數，將它加入至 **OracleCommand** 之 **Parameters** 集合。  參數的名稱必須符合查詢中 REF CURSOR 參數的名稱。  將參數的型別設定為 **OracleType.Cursor**。  **OracleCommand** 的 **ExecuteReader** 方法將傳回 REF CURSOR 的 **OracleDataReader**。  
  
 如果您的 **OracleCommand** 傳回多個 REF CURSOR，請加入多個輸出參數。  您可以呼叫 **OracleCommand.ExecuteReader** 方法來存取不同的 REF CURSOR。  呼叫 **ExecuteReader** 將傳回參考第一個 REF CURSOR 的 **OracleDataReader**。  接著即可呼叫 **OracleDataReader.NextResult** 方法存取後續的 REF CURSOR。  雖然 **OracleCommand.Parameters** 集合中的參數與 REF CURSOR 輸出參數在名稱上相符，但是 **OracleDataReader** 會以這些參數加入 **Parameters** 集合的順序進行存取。  
  
 例如，請考慮下列的 Oracle Package 和 Package 內容。  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 下列程式碼將 **OracleType.Cursor** 型別的兩個參數加入 **Parameters** 集合，藉此建立 **OracleCommand**，從上一個 Oracle Package 傳回 REF CURSOR。  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 下列程式碼使用 **OracleDataReader** 的 **Read** 和 **NextResult** 方法，傳回上一個命令的結果。  REF CURSOR 參數會依順序傳回。  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 下列範例使用上一個命令，以 Oracle Package 的結果填入 **DataSet**。  
  
> [!NOTE]
>  為了避免 **OverflowException**，建議您在 **DataRow** 中儲存值之前，也處理任何從 Oracle NUMBER 型別到有效 .NET Framework 型別的轉換。  您可以使用 **FillError** 事件判斷是否已發生 **OverflowException**。  如需 **FillError** 事件的詳細資訊，請參閱 [處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## 請參閱  
 [Working with DataReaders](http://msdn.microsoft.com/zh-tw/126a966a-d08d-4d22-a19f-f432908b2b54)   
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)