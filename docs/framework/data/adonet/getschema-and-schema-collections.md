---
title: GetSchema 和結構描述集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 4ac0216ce2965d555f7283ba66a085ea9d7cac3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783833"
---
# <a name="getschema-and-schema-collections"></a>GetSchema 和結構描述集合
每個 .NET Framework managed 提供者中的**連接**類別都會執行**GetSchema**方法，用來抓取目前連接之資料庫的架構資訊，以及傳回**的架構資訊。GetSchema**方法的形式<xref:System.Data.DataTable>為。 **GetSchema**方法是一種多載的方法，它會提供選擇性參數來指定要傳回的架構集合，以及限制傳回的資訊量。  
  
## <a name="specifying-the-schema-collections"></a>指定結構描述集合  
 **GetSchema**方法的第一個選擇性參數是指定為字串的集合名稱。 結構描述集合有兩種型別：通用於所有提供者的通用結構描述集合與每個提供者特有的特定結構描述集合。  
  
 您可以查詢 .NET Framework 的 managed 提供者，以判斷支援的架構集合清單，方法是呼叫不含引數的**GetSchema**方法，或使用架構集合名稱 "MetaDataCollections"。 這會傳回 <xref:System.Data.DataTable>，包括支援的結構描述集合清單、每個集合所支援的限制數目，以及集合所使用之識別項部分的數目。  
  
### <a name="retrieving-schema-collections-example"></a>擷取結構描述集合範例  
 下列範例示範如何使用<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server <xref:System.Data.SqlClient.SqlConnection>類別之 .NET Framework Data Provider 的方法，來抓取**AdventureWorks**範例資料庫中包含之所有資料表的架構資訊：  
  
```vb  
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
  
```csharp  
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
  
## <a name="see-also"></a>另請參閱

- [擷取資料庫結構描述資訊](retrieving-database-schema-information.md)
- [ADO.NET 概觀](ado-net-overview.md)
