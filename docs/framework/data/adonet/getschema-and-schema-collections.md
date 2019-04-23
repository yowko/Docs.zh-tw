---
title: GetSchema 和結構描述集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 11cfad81e40e76691db9f99efd1d60f5528600d2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230170"
---
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="54141-102">GetSchema 和結構描述集合</span><span class="sxs-lookup"><span data-stu-id="54141-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="54141-103">**連接**中每個.NET Framework managed 提供者實作類別**GetSchema**方法用來擷取有關目前連接的資料庫結構描述資訊和從傳回的結構描述資訊**GetSchema**方法共有的形式<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="54141-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="54141-104">**GetSchema**方法是多載的方法，提供選擇性參數指定要傳回的結構描述集合及限制傳回的資訊量。</span><span class="sxs-lookup"><span data-stu-id="54141-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="54141-105">指定結構描述集合</span><span class="sxs-lookup"><span data-stu-id="54141-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="54141-106">第一個選擇性參數**GetSchema**方法是指定為字串的集合名稱。</span><span class="sxs-lookup"><span data-stu-id="54141-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="54141-107">結構描述集合有兩種型別：通用於所有提供者的通用結構描述集合與每個提供者特有的特定結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="54141-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="54141-108">您可以查詢來判斷支援的結構描述集合清單，藉由呼叫.NET Framework managed 提供者**GetSchema**方法沒有引數，或以結構描述集合名稱"MetaDataCollections"。</span><span class="sxs-lookup"><span data-stu-id="54141-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="54141-109">這會傳回 <xref:System.Data.DataTable>，包括支援的結構描述集合清單、每個集合所支援的限制數目，以及集合所使用之識別項部分的數目。</span><span class="sxs-lookup"><span data-stu-id="54141-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="54141-110">擷取結構描述集合範例</span><span class="sxs-lookup"><span data-stu-id="54141-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="54141-111">下列範例示範如何使用<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>的.NET Framework Data Provider for SQL Server 的方法<xref:System.Data.SqlClient.SqlConnection>類別來擷取相關的所有資料表中所包含的結構描述資訊**AdventureWorks**範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="54141-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54141-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54141-112">See also</span></span>

- [<span data-ttu-id="54141-113">擷取資料庫結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="54141-113">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="54141-114">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="54141-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
