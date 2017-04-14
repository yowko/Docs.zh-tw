---
title: "更新資料來源中的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 更新資料來源中的資料
會修改資料的 SQL 陳述式 \(例如 INSERT、UPDATE 或 DELETE\) 不會傳回資料列。  同樣地，許多預存程序會執行動作但不傳回資料列。  若要執行不傳回資料列的命令，請使用適當的 SQL 命令和 **Connection** \(包含任何所需的**參數**\) 來建立 **Command** 物件。  並且使用 **Command** 物件的 **ExecuteNonQuery** 方法執行命令。  
  
 **ExecuteNonQuery** 方法會傳回整數，表示受到執行的陳述式或預存程序影響的資料列數。  如果執行多個陳述式，傳回的值就是受到所有執行的陳述式影響的記錄數總和。  
  
## 範例  
 下列程式碼範例使用 **ExecuteNonQuery** 來執行 INSERT 陳述式，將記錄插入資料庫。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 下列程式碼範例執行由[執行資料庫目錄作業](../../../../docs/framework/data/adonet/performing-catalog-operations.md)中的程式碼範例所建立的預存程序。  預存程序不會傳回任何資料列，所以要使用 **ExecuteNonQuery** 方法，但是預存程序確實會收到輸入參數，並且傳回輸出參數和傳回值。  
  
 若為 <xref:System.Data.OleDb.OleDbCommand> 物件，必須先將 **ReturnValue** 參數加入 **Parameters** 集合。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## 請參閱  
 [使用命令來修改資料](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)   
 [以 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)   
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)