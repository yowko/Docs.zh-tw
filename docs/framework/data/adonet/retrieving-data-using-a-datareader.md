---
title: 使用 DataReader 擷取資料
ms.date: 10/259/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: d3c59b667c05be083e44de8cc3e7e44d50fefc71
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "43516787"
---
# <a name="retrieve-data-using-a-datareader"></a>使用 DataReader 擷取資料
若要擷取的資料使用**DataReader**，建立的執行個體**命令**物件，然後再建立**DataReader**藉由呼叫**Command.ExecuteReader**從資料來源擷取資料列。 **DataReader**提供未緩衝處理資料流的資料，可讓程序邏輯有效地循序處理來自資料來源的結果。 **DataReader**是不錯的選擇，因為資料不會快取記憶體，在擷取大量資料時。

下列範例說明如何利用**DataReader**，其中`reader`代表有效的 DataReader 和`command`代表有效的命令物件。  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

使用**DataReader.Read**方法，以從查詢結果取得資料列。 您可以藉由傳遞的名稱或序數編號的資料行傳回的資料列的每個資料行**DataReader**。 不過，為了達到最佳效能， **DataReader**提供一系列的方法，可讓您存取其原生資料類型的資料行值 (**GetDateTime**， **GetDouble**， **GetGuid**， **GetInt32**等等)。 如需資料提供者特有的具型別存取子方法的清單**Datareader**，請參閱<xref:System.Data.OleDb.OleDbDataReader>和<xref:System.Data.SqlClient.SqlDataReader>。 使用具型別存取子方法，當您知道的基本資料型別可減少擷取資料行的值時所需的型別轉換的量。  
  
 下列範例會逐一**DataReader**物件，並傳回每個資料列的兩個資料行。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>關閉 DataReader  
 請務必呼叫**關閉**方法，當您完成使用**DataReader**物件。  
  
 如果您**命令**包含輸出參數或傳回值，這些值沒有直到**DataReader**已關閉。  
  
 雖然**DataReader**開啟，請**連線**處於只能供該**DataReader**。 您無法執行任何命令**連接**，包括建立其他**DataReader**，直到原始**DataReader**已關閉。  
  
> [!NOTE]
>  不要呼叫**關閉**或**Dispose**上**連接**，則**DataReader**，或在任何其他 managed 的物件**Finalize**您類別的方法。 在完成項中，只需釋放類別直接擁有的 Unmanaged 資源。 如果您的類別未擁有任何 unmanaged 的資源，並包含**Finalize**類別定義中的方法。 如需詳細資訊，請參閱 <<c0> [ 回收](../../../../docs/standard/garbage-collection/index.md)。  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>使用 nextresult 來擷取多個結果設定  
 如果**DataReader**會傳回多個結果集，呼叫**NextResult**來逐一查看結果的方法會以循序方式設定。 下列範例顯示 <xref:System.Data.SqlClient.SqlDataReader> 使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> 方法，處理兩個 SELECT 陳述式的結果。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>從 DataReader 取得結構描述資訊  
 雖然**DataReader**已開啟，您可以擷取目前結果集使用的結構描述資訊**GetSchemaTable**方法。 **GetSchemaTable**傳回<xref:System.Data.DataTable>填入資料列和資料行包含目前的結果集的結構描述資訊的物件。 **DataTable**包含一個資料列結果集的每個資料行。 結構描述資料表的每個資料行對應到屬性中傳回的資料行結果的資料列集，其中**ColumnName**是屬性的名稱和資料行的值是屬性的值。 下列範例會寫出的結構描述資訊**DataReader**。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>使用 OLE DB 章節  
 階層式資料列集或章節 (OLE DB 型別**DBTYPE_HCHAPTER**、 ADO 型別**adChapter**)，您可以使用擷取<xref:System.Data.OleDb.OleDbDataReader>。 當其中一章包含的查詢會以傳回**DataReader**，章節會傳回做為資料行中的**DataReader** ，並公開為**DataReader**物件。  
  
 ADO.NET**資料集**也可用來代表階層式資料列集使用資料表之間的父子式關聯性。 如需詳細資訊，請參閱 < [Dataset、 Datatable 和 Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)。  
  
 下列程式碼範例使用 MSDataShape 提供者，替客戶清單中每位客戶的訂單產生章節資料行。  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>傳回使用 Oracle REF Cursor 的結果  
 Oracle 的 .NET Framework 資料提供者支援使用 Oracle REF CURSOR 傳回查詢結果。 Oracle REF CURSOR 以 <xref:System.Data.OracleClient.OracleDataReader> 傳回。  
  
 您可以擷取<xref:System.Data.OracleClient.OracleDataReader>物件，表示所使用的 Oracle REF CURSOR<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>方法。 您也可以指定<xref:System.Data.OracleClient.OracleCommand>會傳回做為一或多個 Oracle REF Cursor **SelectCommand**如<xref:System.Data.OracleClient.OracleDataAdapter>用來填滿<xref:System.Data.DataSet>。  
  
 若要存取從 Oracle 資料來源傳回的 REF CURSOR，請建立<xref:System.Data.OracleClient.OracleCommand>為您的查詢，並新增參考至 REF CURSOR 輸出參數<xref:System.Data.OracleClient.OracleCommand.Parameters>的集合您<xref:System.Data.OracleClient.OracleCommand>。 參數的名稱必須符合查詢中 REF CURSOR 參數的名稱。 設定以參數的型別<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>。 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>方法您<xref:System.Data.OracleClient.OracleCommand>傳回<xref:System.Data.OracleClient.OracleDataReader>REF cursor。  
  
 如果您<xref:System.Data.OracleClient.OracleCommand>傳回多個 REF CURSOR，新增多個輸出參數。 您可以藉由呼叫不同的 REF Cursor<xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>方法。 若要在呼叫<xref:System.Data.OracleClient.OracleCommand.ExecuteReader>傳回<xref:System.Data.OracleClient.OracleDataReader>參考第一個 REF CURSOR。 您可以接著呼叫<xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType>方法來存取後續的 REF Cursor。 雖然的參數，在您<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合與 REF CURSOR 輸出參數名稱，<xref:System.Data.OracleClient.OracleDataReader>存取它們的順序已新增至<xref:System.Data.OracleClient.OracleCommand.Parameters>集合。  
  
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
  
 下列程式碼會建立<xref:System.Data.OracleClient.OracleCommand>，從上一個 Oracle package 傳回 REF Cursor 加上兩個參數類型<xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>到<xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>集合。  
  
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
  
 下列程式碼會傳回前一個命令使用的結果<xref:System.Data.OracleClient.OracleDataReader.Read>並<xref:System.Data.OracleClient.OracleDataReader.NextResult>方法<xref:System.Data.OracleClient.OracleDataReader>。 REF CURSOR 參數會依順序傳回。  
  
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
  
 下列範例會使用前一個命令來填入<xref:System.Data.DataSet>Oracle package 的結果。  
  
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

> [!NOTE]
>  若要避免**OverflowException**，我們建議您也會處理任何從 Oracle NUMBER 型別轉換為有效的.NET Framework 型別儲存中的值之前<xref:System.Data.DataRow>。 您可以使用<xref:System.Data.Common.DataAdapter.FillError>事件判斷是否**OverflowException**發生。 如需詳細資訊<xref:System.Data.Common.DataAdapter.FillError>事件，請參閱 <<c2> [ 處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Datareader](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
