---
title: "結構描述限制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 結構描述限制
**GetSchema** 方法的第二個選擇性參數是用於限制傳回之結構描述資訊量的限制，會以字串陣列傳遞至 **GetSchema** 方法。  陣列中的位置決定您可以傳遞的值，它相當於限制號碼。  
  
 例如，下表說明使用 .NET Framework Data Provider for SQL Server 之 "Tables" 結構描述集合所支援的限制。  SQL Server 結構描述集合的其他限制將列於本主題的結尾。  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|需要的|@Owner|TABLE\_SCHEMA|2|  
|資料表|@Name|TABLE\_NAME|3|  
|TableType|@TableType|TABLE\_TYPE|4|  
  
## 指定限制值  
 若要使用 "Tables" 結構描述集合的其中一個限制，只需使用四個元素建立字串陣列，然後將符合限制數目的值置於元素中。  例如，若要將 **GetSchema** 方法所傳回的資料表限制為只有 "Sales" 結構描述中的資料表，請先將陣列的第二個元素設定為 "Sales"，再將它傳送至 **GetSchema** 方法。  
  
> [!NOTE]
>  `SqlClient` 及 `OracleClient` 的限制集合具有其他 `ParameterName` 資料行。  限制預設值資料行仍存在，用於回溯相容性，但目前會忽略它.  指定限制值時，應使用參數化查詢而不是字串取代，來將 SQL 資料隱碼攻擊的風險減至最小。  
  
> [!NOTE]
>  陣列中的項目數目必須少於或等於指定結構描述集合所支援的限制數目，否則將擲回 <xref:System.ArgumentException>。  可以少於限制的最大數目。  假設遺漏的限制為 Null \(未限制\)。  
  
 您可以藉由呼叫 **GetSchema** 方法 \(具有限制結構描述集合的名稱 Restrictions\)，來查詢 .NET Framework Managed 提供者，以判定支援的限制清單。  這將傳回 <xref:System.Data.DataTable>，其包含集合名稱、限制名稱、預設限制值及限制號碼的清單。  
  
### 範例  
 下列範例將示範如何使用 .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> 類別的 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 方法來擷取 **AdventureWorks** 範例資料庫中包含之所有資料表的結構描述資訊，並將傳回的資訊限制為只有 "Sales" 結構描述中的資料表：  
  
 \[Visual Basic\]  
  
```  
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
  
 \[C\#\]  
  
```  
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
  
## SQL Server 結構描述限制  
 下表將列出 SQL Server 結構描述集合的限制。  
  
### 使用者  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|User\_Name|@Name|name|1|  
  
### 資料庫  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|名稱|@Name|名稱|1|  
  
### 資料表  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|需要的|@Owner|TABLE\_SCHEMA|2|  
|資料表|@Name|TABLE\_NAME|3|  
|TableType|@TableType|TABLE\_TYPE|4|  
  
### 資料行  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|需要的|@Owner|TABLE\_SCHEMA|2|  
|資料表|@Table|TABLE\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
### StructuredTypeMembers  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|需要的|@Owner|TABLE\_SCHEMA|2|  
|資料表|@Table|TABLE\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
### 檢視  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|需要的|@Owner|TABLE\_SCHEMA|2|  
|資料表|@Table|TABLE\_NAME|3|  
  
### ViewColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|VIEW\_CATALOG|1|  
|需要的|@Owner|VIEW\_SCHEMA|2|  
|資料表|@Table|VIEW\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
### ProcedureParameters  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|SPECIFIC\_CATALOG|1|  
|需要的|@Owner|SPECIFIC\_SCHEMA|2|  
|名稱|@Name|SPECIFIC\_NAME|3|  
|參數|@Parameter|PARAMETER\_NAME|4|  
  
### 程序  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|SPECIFIC\_CATALOG|1|  
|需要的|@Owner|SPECIFIC\_SCHEMA|2|  
|名稱|@Name|SPECIFIC\_NAME|3|  
|類型|@Type|ROUTINE\_TYPE|4|  
  
### IndexColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|db\_name\(\)|1|  
|需要的|@Owner|user\_name\(\)|2|  
|資料表|@Table|o.  name|3|  
|ConstraintName|@ConstraintName|x.  name|4|  
|Column|@Column|c.   name|5|  
  
### Indexes  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|db\_name\(\)|1|  
|需要的|@Owner|user\_name\(\)|2|  
|資料表|@Table|o.  name|3|  
  
### UserDefinedTypes  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|assembly\_name|@AssemblyName|組件。  name|1|  
|udt\_name|@UDTName|types.assembly\_class|2|  
  
### ForeignKeys  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|CONSTRAINT\_CATALOG|1|  
|需要的|@Owner|CONSTRAINT\_SCHEMA|2|  
|資料表|@Table|TABLE\_NAME|3|  
|名稱|@Name|CONSTRAINT\_NAME|4|  
  
## SQL Server 2008 結構描述限制  
 下表將列出 SQL Server 2008 結構描述集合的限制。  從 .NET Framework 3.5 版 SP1 和 SQL Server 2008 開始，這些限制便有效。  舊版 .NET Framework 和 SQL Server 不支援它們。  
  
### ColumnSetColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|需要的|@Owner|TABLE\_SCHEMA|2|  
|資料表|@Table|TABLE\_NAME|3|  
  
### AllColumns  
  
|限制名稱|參數名稱|預設限制值|限制號碼|  
|----------|----------|-----------|----------|  
|Catalog|@Catalog|TABLE\_CATALOG|1|  
|需要的|@Owner|TABLE\_SCHEMA|2|  
|資料表|@Table|TABLE\_NAME|3|  
|Column|@Column|COLUMN\_NAME|4|  
  
## 請參閱  
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)