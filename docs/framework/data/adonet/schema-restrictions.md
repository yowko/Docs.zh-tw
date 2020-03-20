---
title: 結構描述限制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149007"
---
# <a name="schema-restrictions"></a>結構描述限制
**GetSchema**方法的第二個可選參數是用於限制返回的架構資訊量的限制，它作為字串陣列傳遞給**GetSchema**方法。 陣列中的位置決定您可以傳遞的值，它相當於限制號碼。  
  
 例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。 SQL Server 結構描述集合的其他限制將列於本主題的結尾。  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|TABLE_CATALOG|1|  
|擁有者|@Owner|TABLE_SCHEMA|2|  
|Table|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>指定限制值  
 若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。 例如，要將**GetSchema**方法返回的表限制為"銷售"架構中的這些表，在將其傳遞給**GetSchema**方法之前，將陣列的第二個元素設置為"Sales"。  
  
> [!NOTE]
> `SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。 限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它. 指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。  
  
> [!NOTE]
> 陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。 可以少於限制的最大數目。 假設遺漏的限制為 Null (未限制)。  
  
 您可以查詢 .NET Framework 託管提供程式，通過調用具有限制架構集合名稱的**GetSchema**方法（即"限制"）來確定受支援限制的清單。 這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。  
  
### <a name="example"></a>範例  
 以下示例演示如何使用 SQL Server<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A><xref:System.Data.SqlClient.SqlConnection>類的 .NET 框架資料提供程式的方法檢索有關**AdventureWorks**示例資料庫中包含的所有表的架構資訊，並將返回的資訊限制為"銷售"架構中僅返回的資訊：  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
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
    string connectionString =
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
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
  
## <a name="sql-server-schema-restrictions"></a>SQL Server 結構描述限制  
 下表將列出 SQL Server 結構描述集合的限制。  
  
### <a name="users"></a>使用者  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_Name|@Name|NAME|1|  
  
### <a name="databases"></a>資料庫  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|名稱|@Name|名稱|1|  
  
### <a name="tables"></a>資料表  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|TABLE_CATALOG|1|  
|擁有者|@Owner|TABLE_SCHEMA|2|  
|Table|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>資料行  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|TABLE_CATALOG|1|  
|擁有者|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|TABLE_CATALOG|1|  
|擁有者|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>檢視  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|TABLE_CATALOG|1|  
|擁有者|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|VIEW_CATALOG|1|  
|擁有者|@Owner|VIEW_SCHEMA|2|  
|Table|@Table|VIEW_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|SPECIFIC_CATALOG|1|  
|擁有者|@Owner|SPECIFIC_SCHEMA|2|  
|名稱|@Name|SPECIFIC_NAME|3|  
|參數|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>程序  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|SPECIFIC_CATALOG|1|  
|擁有者|@Owner|SPECIFIC_SCHEMA|2|  
|名稱|@Name|SPECIFIC_NAME|3|  
|類型|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|db_name()|1|  
|擁有者|@Owner|user_name()|2|  
|Table|@Table|o.name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|資料行|@Column|c.name|5|  
  
### <a name="indexes"></a>索引  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|db_name()|1|  
|擁有者|@Owner|user_name()|2|  
|Table|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|CONSTRAINT_CATALOG|1|  
|擁有者|@Owner|CONSTRAINT_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|名稱|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 結構描述限制  
 下表將列出 SQL Server 2008 結構描述集合的限制。 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。 舊版 .NET Framework 和 SQL Server 不支援它們。  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|TABLE_CATALOG|1|  
|擁有者|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|目錄|@Catalog|TABLE_CATALOG|1|  
|擁有者|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
