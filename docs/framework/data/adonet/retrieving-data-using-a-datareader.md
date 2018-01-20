---
title: "使用 DataReader 擷取資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 60328d766a931abd7a1a3e9dc08c68928e01f2d2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="retrieving-data-using-a-datareader"></a>使用 DataReader 擷取資料
擷取使用資料**DataReader**牽涉到建立的執行個體**命令**物件，然後再建立**DataReader**藉由呼叫**Command.ExecuteReader**從資料來源擷取資料列。 下列範例說明如何使用**DataReader**其中`reader`代表有效的 DataReader 和`command`代表有效的命令物件。  
  
```  
reader = command.ExecuteReader();  
```  
  
 您使用**讀取**方法**DataReader**從查詢的結果取得資料列的物件。 您可以存取傳回的資料列的每個資料行名稱或序數參考的資料行傳遞**DataReader**。 不過，為了達到最佳效能， **DataReader**提供一系列的方法可讓您存取其原生資料類型的資料行值 (**GetDateTime**， **GetDouble**， **GetGuid**， **GetInt32**等等)。 如需資料提供者特有的具型別的存取子方法的清單**Datareader**，請參閱<xref:System.Data.OleDb.OleDbDataReader>和<xref:System.Data.SqlClient.SqlDataReader>。 假設已知基礎資料型別時，若使用具型別的存取子方法，可減少擷取資料行值時所需的型別轉換量。  
  
> [!NOTE]
>  Windows Server 2003 版本的.NET framework 包含的額外屬性**DataReader**， **HasRows**，可讓您判斷**DataReader**從中傳回任何結果之前讀取。  
  
 下列程式碼範例會逐一**DataReader**物件，並傳回每個資料列的兩個資料行。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader**提供未緩衝處理的資料流的資料，讓程序邏輯有效地循序處理來自資料來源的結果。 **DataReader**擷取大量資料，因為資料不會快取記憶體時，是不錯的選擇。  
  
## <a name="closing-the-datareader"></a>關閉 DataReader  
 您應該一律呼叫**關閉**方法，當您完成使用**DataReader**物件。  
  
 如果您**命令**包含輸出參數或傳回值，它們將無法使用之前**DataReader**已關閉。  
  
 請注意，當**DataReader**開啟時，**連接**正在以獨佔方式使用**DataReader**。 您無法執行任何命令**連接**，包括建立其他**DataReader**，直到原始**DataReader**已關閉。  
  
> [!NOTE]
>  請勿呼叫**關閉**或**處置**上**連接**、 **DataReader**，或在任何其他 managed 的物件**Finalize**類別的方法。 在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。 如果您的類別未擁有任何 unmanaged 的資源，並包含**Finalize**類別定義中的方法。 如需詳細資訊，請參閱[回收](../../../../docs/standard/garbage-collection/index.md)。  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>使用 NextResult 來擷取多個結果集  
 如果傳回多個結果集， **DataReader**提供**NextResult**設定在順序中的方法來逐一查看結果。 下列範例顯示 <xref:System.Data.SqlClient.SqlDataReader> 使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法，處理兩個 SELECT 陳述式的結果。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>從 DataReader 取得結構描述資訊  
 雖然**DataReader**是開啟時，您可以擷取目前結果集使用的結構描述資訊**GetSchemaTable**方法。 **GetSchemaTable**傳回<xref:System.Data.DataTable>填入資料列和資料行，內含目前結果集之結構描述資訊的物件。 **DataTable**包含一個資料列結果集的每一個資料行。 結構描述資料表資料列的每個資料行對應到屬性中傳回的資料行的結果集，其中**ColumnName**屬性的名稱，而資料行的值屬性的值。 下列程式碼範例會寫出的結構描述資訊**DataReader**。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>使用 OLE DB 章節  
 階層式資料列集或章節 (OLE DB 類型**DBTYPE_HCHAPTER**，ADO 類型**adChapter**) 可以使用擷取<xref:System.Data.OleDb.OleDbDataReader>。 當包含章節的查詢會傳回做為**DataReader**，章節會傳回做為資料行中的**DataReader**且公開為**DataReader**物件。  
  
 ADO.NET**資料集**也可用來代表階層式資料列集使用資料表之間的父子式關聯性。 如需詳細資訊，請參閱[資料集、 Datatable 和 Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)。  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>使用 Oracle REF CURSOR 來傳回結果  
 Oracle 的 .NET Framework 資料提供者支援使用 Oracle REF CURSOR 傳回查詢結果。 Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 傳回。  
  
 您可以擷取**OracleDataReader**物件，表示使用 Oracle REF CURSOR<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>方法之外，也可以指定<xref:System.Data.OracleClient.OracleCommand>傳回做為一或多個 Oracle REF Cursor **SelectCommand**如<xref:System.Data.OracleClient.OracleDataAdapter>用來填滿<xref:System.Data.DataSet>。  
  
 若要存取從 Oracle 資料來源傳回的 REF CURSOR，請建立**OracleCommand**為您的查詢並參考 REF CURSOR 以輸出參數加入**參數**您的集合**OracleCommand**。 參數的名稱必須符合查詢中 REF CURSOR 參數的名稱。 設定的參數類型**OracleType.Cursor**。 **ExecuteReader**方法您**OracleCommand**會傳回**OracleDataReader** REF cursor。  
  
 如果您**OracleCommand**傳回多個 REF CURSOR，新增多個輸出參數。 您可以藉由呼叫存取不同的 REF Cursor **OracleCommand.ExecuteReader**方法。 若要呼叫**ExecuteReader**傳回**OracleDataReader**參考第一個 REF CURSOR。 您可以接著呼叫**OracleDataReader.NextResult**方法來存取後續的 REF Cursor。 雖然參數在您**OracleCommand.Parameters**集合與 REF CURSOR 輸出參數的名稱， **OracleDataReader**它們已加入至順序進行存取**參數**集合。  
  
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
  
 下列程式碼會建立**OracleCommand** ，從上一個 Oracle package 傳回 REF Cursor 的兩個參數的型別加入**OracleType.Cursor**至**參數**集合。  
  
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
  
 下列程式碼會傳回前一個命令使用的結果**讀取**和**NextResult**方法**OracleDataReader**。 REF CURSOR 參數會依順序傳回。  
  
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
  
 下列範例使用前一個命令來填入**資料集**Oracle package 的結果。  
  
> [!NOTE]
>  若要避免**OverflowException**，我們建議您也處理任何從 Oracle NUMBER 型別轉換為有效的.NET Framework 型別儲存中的值之前**DataRow**。 您可以使用**FillError**事件，以判斷如果**OverflowException**發生。 如需有關**FillError**事件，請參閱[處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。  
  
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
  
## <a name="see-also"></a>請參閱  
 [使用 Datareader](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
