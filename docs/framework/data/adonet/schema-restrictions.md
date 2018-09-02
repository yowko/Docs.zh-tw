---
title: 結構描述限制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417078"
---
# <a name="schema-restrictions"></a>結構描述限制
第二個選擇性參數**GetSchema**方法會傳回用來限制結構描述資訊量的限制，並將它傳遞至**GetSchema**方法作為字串的陣列. 陣列中的位置決定您可以傳遞的值，它相當於限制號碼。  
  
 例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。 SQL Server 結構描述集合的其他限制將列於本主題的結尾。  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|資料表|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>指定限制值  
 若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。 例如，若要限制資料表所傳回**GetSchema**方法，以只有"Sales"結構描述中的資料表設定為"Sales"陣列的第二個項目之前將其傳遞給**GetSchema**方法。  
  
> [!NOTE]
>  `SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。 限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它. 指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。  
  
> [!NOTE]
>  陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。 可以少於限制的最大數目。 假設遺漏的限制為 Null (未限制)。  
  
 您可以查詢來判斷支援的限制清單，藉由呼叫.NET Framework managed 提供者**GetSchema**方法具有限制結構描述集合，也就是 「 限制 」 的名稱。 這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>的.NET Framework Data Provider for SQL Server 的方法<xref:System.Data.SqlClient.SqlConnection>類別來擷取相關的所有資料表中所包含的結構描述資訊**AdventureWorks**範例資料庫，並將資訊限制傳回只有"Sales"結構描述中的資料表：  
  
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
|User_Name|@Name|名稱|1|  
  
### <a name="databases"></a>資料庫  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|名稱|@Name|名稱|1|  
  
### <a name="tables"></a>資料表  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|資料表|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>資料行  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|資料表|@Table|TABLE_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|資料表|@Table|TABLE_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>檢視  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|資料表|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|VIEW_CATALOG|1|  
|Owner|@Owner|VIEW_SCHEMA|2|  
|資料表|@Table|VIEW_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|SPECIFIC_CATALOG|1|  
|Owner|@Owner|SPECIFIC_SCHEMA|2|  
|名稱|@Name|SPECIFIC_NAME|3|  
|參數|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>程序  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|SPECIFIC_CATALOG|1|  
|Owner|@Owner|SPECIFIC_SCHEMA|2|  
|名稱|@Name|SPECIFIC_NAME|3|  
|類型|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|資料表|@Table|o.name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|資料行|@Column|c.name|5|  
  
### <a name="indexes"></a>Indexes  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|資料表|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|CONSTRAINT_CATALOG|1|  
|Owner|@Owner|CONSTRAINT_SCHEMA|2|  
|資料表|@Table|TABLE_NAME|3|  
|名稱|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 結構描述限制  
 下表將列出 SQL Server 2008 結構描述集合的限制。 從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。 舊版 .NET Framework 和 SQL Server 不支援它們。  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|資料表|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------------------|--------------------|-------------------------|------------------------|  
|Catalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|資料表|@Table|TABLE_NAME|3|  
|資料行|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
