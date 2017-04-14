---
title: "GetSchema 和結構描述集合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# GetSchema 和結構描述集合
每個 .NET Framework Managed 提供者中的 **Connection** 類別都會實作 **GetSchema** 方法，此方法用於擷取目前連接之資料庫的結構描述資訊，並且從 **GetSchema** 方法傳回之結構描述資訊的形式為 <xref:System.Data.DataTable>。  **GetSchema** 方法是一種多載方法，它為指定要傳回的結構描述集合及限制傳回的資訊量，提供選擇性參數。  
  
## 指定結構描述集合  
 **GetSchema** 方法的第一個選擇性參數是指定為字串的集合名稱。  結構描述集合有兩種型別：通用於所有提供者的通用結構描述集合與每個提供者特有的特定結構描述集合。  
  
 您可以藉由呼叫 **GetSchema** 方法 \(不使用引數或使用結構描述集合名稱 MetaDataCollections\)，來查詢 .NET Framework Managed 提供者，以決定支援的結構描述集合清單。  這會傳回 <xref:System.Data.DataTable>，包括支援的結構描述集合清單、每個集合所支援的限制數目，以及集合所使用之識別項部分的數目。  
  
### 擷取結構描述集合範例  
 下列範例示範如何使用 SQL Server 的 .NET Framework 資料提供者之 <xref:System.Data.SqlClient.SqlConnection> 類別的 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 方法，擷取 **AdventureWorks** 範例資料庫中包含之所有資料表的結構描述資訊：  
  
 \[Visual Basic\]  
  
```  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,    
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
   End Sub  
End Module  
```  
  
 \[C\#\]  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
   Console.WriteLine("Press any key to continue.");  
   Console.ReadKey();  
   }  
 }  
  
  private static string GetConnectionString()  
  {  
   // To avoid storing the connection string in your code,  
   // you can retrieve it from a configuration file.  
   return "Data Source=(local);Database=AdventureWorks;" +  
      "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## 請參閱  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)