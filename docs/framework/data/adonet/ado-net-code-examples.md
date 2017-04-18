---
title: "ADO.NET 程式碼範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# ADO.NET 程式碼範例
本主題的程式碼清單示範如何使用下列 ADO.NET 技術來擷取資料庫中的資料：  
  
-   ADO.NET 資料提供者：  
  
    -   [SqlClient](#_SqlClient) (`System.Data.SqlClient`)  
  
    -   [OleDb](#_OleDb) (`System.Data.OleDb`)  
  
    -   [Odbc](#_Odbc) (`System.Data.Odbc`)  
  
    -   [OracleClient](#_OracleClient) (`System.Data.OracleClient`)  
  
-   ADO.NET Entity Framework：  
  
    -   [LINQ to Entities](#_LINQ)  
  
    -   [具型別的的 ObjectQuery](#_QBM)  
  
    -   [EntityClient](#_EntityClient) (`System.Data.EntityClient`)  
  
-   [LINQ to SQL](#_LINQ2SQL)  
  
## <a name="adonet-data-provider-examples"></a>ADO.NET 資料提供者範例  
 下列程式碼清單將示範如何使用 ADO.NET 資料提供者來擷取資料庫中的資料。 資料會傳入 `DataReader` 中。 如需詳細資訊，請參閱[資料擷取使用 DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)。  
  
<a name="_SqlClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 這則範例中的程式碼會假設您可以連接至 Microsoft `Northwind` 上的 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 範例資料庫。 程式碼會建立<xref:System.Data.SqlClient.SqlCommand>從 Products 資料表中，選取資料列加入<xref:System.Data.SqlClient.SqlParameter>以便將結果限制為 UnitPrice 大於指定的參數值，在此情況下為 5 的資料列。 <xref:System.Data.SqlClient.SqlConnection>內開啟`using`區塊中，以確保資源會關閉和處置程式碼結束時。 程式碼來使用執行此命令<xref:System.Data.SqlClient.SqlDataReader>，並將結果顯示在主控台視窗中。  
  
  [DataWorks SampleApp.SqlClient#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient#1)]  
  
 [[Top]](#_TOP)  
  
<a name="_OleDb"></a>   
### <a name="oledb"></a>OleDb  
 這則範例中的程式碼會假設您可以連接至 Microsoft Access Northwind 範例資料庫。 程式碼會建立<xref:System.Data.OleDb.OleDbCommand>從 Products 資料表中，選取資料列加入<xref:System.Data.OleDb.OleDbParameter>以便將結果限制為 UnitPrice 大於指定的參數值，在此情況下為 5 的資料列。 <xref:System.Data.OleDb.OleDbConnection>內開啟`using`區塊中，以確保資源會關閉和處置程式碼結束時。 程式碼來使用執行此命令<xref:System.Data.OleDb.OleDbDataReader>，並將結果顯示在主控台視窗中。  
  
  [DataWorks SampleApp.OleDb#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb#1)]  
  
 [[Top]](#_TOP)  
  
<a name="_Odbc"></a>   
### <a name="odbc"></a>Odbc  
 這則範例中的程式碼會假設您可以連接至 Microsoft Access Northwind 範例資料庫。 程式碼會建立<xref:System.Data.Odbc.OdbcCommand>從 Products 資料表中，選取資料列加入<xref:System.Data.Odbc.OdbcParameter>以便將結果限制為 UnitPrice 大於指定的參數值，在此情況下為 5 的資料列。 <xref:System.Data.Odbc.OdbcConnection>內開啟`using`區塊中，以確保資源會關閉和處置程式碼結束時。 執行命令，使用<xref:System.Data.Odbc.OdbcDataReader>，並將結果顯示在主控台視窗中。  
  
<!-- TODO: review snippet reference  [!CODE [DataWorksSampleApp.Odbc#1](DataWorksSampleApp.Odbc#1)]  -->  
  
 [[Top]](#_TOP)  
  
<a name="_OracleClient"></a>   
### <a name="oracleclient"></a>OracleClient  
 這則範例中的程式碼會假設您已連接到 Oracle 伺服器上的 DEMO.CUSTOMER。 您也必須加入 System.Data.OracleClient.dll 的參考。 程式碼會將資料<xref:System.Data.OracleClient.OracleDataReader>。  
  
  [DataWorks SampleApp.Oracle#1](../CodeSnippet/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle#1)]  
  
 [[Top]](#_TOP)  
  
## <a name="entity-framework-examples"></a>Entity Framework 範例  
 下列程式碼清單將示範如何透過查詢 Entity Data Model (EDM) 中的實體，擷取資料來源中的資料。 這些範例使用[Northwind 模型](http://msdn.microsoft.com/zh-tw/74521f8c-e974-48cb-8858-c08deff52638)。 如需詳細資訊，請參閱[Entity Framework 概觀](../../../../docs/framework/data/adonet/ef/overview.md)。  
  
<a name="_LINQ"></a>   
### <a name="linq-to-entities"></a>LINQ to Entities  
 這則範例中的程式碼會使用 LINQ 查詢來傳回資料當做 Categories 物件，而這些物件會投影成僅包含 CategoryID 和 CategoryName 屬性的匿名型別。 如需詳細資訊，請參閱[LINQ to Entities 概觀](http://msdn.microsoft.com/zh-tw/86d87a27-c17a-45ac-b28d-72c8500333c6)。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Linq  
Imports System.Data.Objects  
Imports NorthwindModel  
  
Class LinqSample  
    Public Shared Sub ExecuteQuery()  
        Using context As NorthwindEntities = New NorthwindEntities()  
            Try  
                Dim query = From category In context.Categories _  
                            Select New With _  
                            { _  
                                .categoryID = category.CategoryID, _  
                                .categoryName = category.CategoryName _  
                            }  
  
                For Each categoryInfo In query  
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                        categoryInfo.categoryID, categoryInfo.categoryName)  
                Next  
            Catch ex As Exception  
                Console.WriteLine(ex.Message)  
            End Try  
        End Using  
    End Sub  
End Class  
```  
  
 在 C# 中：  
  
```  
using System;  
using System.Linq;  
using System.Data.Objects;  
using NorthwindModel;  
  
class LinqSample  
{  
    public static void ExecuteQuery()  
    {  
        using (NorthwindEntities context = new NorthwindEntities())  
        {  
            try  
            {  
                var query = from category in context.Categories  
                            select new  
                            {  
                                categoryID = category.CategoryID,  
                                categoryName = category.CategoryName  
                            };  
  
                foreach (var categoryInfo in query)  
                {  
                    Console.WriteLine("\t{0}\t{1}",  
                        categoryInfo.categoryID, categoryInfo.categoryName);  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
 [[Top]](#_TOP)  
  
<a name="_QBM"></a>   
### <a name="typed-objectquery"></a>具型別的 ObjectQuery  
 在此範例程式碼會使用<xref:System.Data.Objects.ObjectQuery%601>傳回資料當做 Categories 物件。 如需詳細資訊，請參閱[物件查詢](http://msdn.microsoft.com/zh-tw/0768033c-876f-471d-85d5-264884349276)。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Objects  
Imports NorthwindModel  
  
Class ObjectQuerySample  
    Public Shared Sub ExecuteQuery()  
        Using context As NorthwindEntities = New NorthwindEntities()  
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories  
  
            For Each category As Categories In _  
                categoryQuery.Execute(MergeOption.AppendOnly)  
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                    category.CategoryID, category.CategoryName)  
            Next  
        End Using  
    End Sub  
End Class  
```  
  
 在 C# 中：  
  
```  
using System;  
using System.Data.Objects;  
using NorthwindModel;  
  
class ObjectQuerySample  
{  
    public static void ExecuteQuery()  
    {  
        using (NorthwindEntities context = new NorthwindEntities())  
        {  
            ObjectQuery<Categories> categoryQuery = context.Categories;  
  
            foreach (Categories category in   
                categoryQuery.Execute(MergeOption.AppendOnly))  
            {  
                Console.WriteLine("\t{0}\t{1}",  
                    category.CategoryID, category.CategoryName);  
            }  
        }  
    }  
}  
```  
  
 [[Top]](#_TOP)  
  
<a name="_EntityClient"></a>   
### <a name="entityclient"></a>EntityClient  
 在此範例程式碼會使用<xref:System.Data.EntityClient.EntityCommand>來執行 Entity SQL 查詢。 這個查詢會傳回代表 Categories 實體類型之執行個體 (Instance) 的記錄清單。 <xref:System.Data.EntityClient.EntityDataReader>用來存取結果集中的資料記錄。 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data  
Imports System.Data.Common  
Imports System.Data.EntityClient  
Imports NorthwindModel  
  
Class EntityClientSample  
    Public Shared Sub ExecuteQuery()  
        Dim queryString As String = _  
            "SELECT c.CategoryID, c.CategoryName " & _  
                "FROM NorthwindEntities.Categories AS c"  
  
        Using conn As EntityConnection = _  
            New EntityConnection("name=NorthwindEntities")  
  
            Try  
                conn.Open()  
                Using query As EntityCommand = _  
                New EntityCommand(queryString, conn)  
                    Using rdr As DbDataReader = _  
                        query.ExecuteReader(CommandBehavior.SequentialAccess)  
                        While rdr.Read()  
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                                              rdr(0), rdr(1))  
                        End While  
                    End Using  
                End Using  
            Catch ex As Exception  
                Console.WriteLine(ex.Message)  
            End Try  
        End Using   
    End Sub  
End Class  
```  
  
 在 C#" 中  
  
```  
using System;  
using System.Data;  
using System.Data.Common;  
using System.Data.EntityClient;  
using NorthwindModel;  
  
class EntityClientSample  
{  
    public static void ExecuteQuery()  
    {  
        string queryString =  
            @"SELECT c.CategoryID, c.CategoryName   
                FROM NorthwindEntities.Categories AS c";  
  
        using (EntityConnection conn =  
            new EntityConnection("name=NorthwindEntities"))  
        {  
            try  
            {  
                conn.Open();  
                using (EntityCommand query = new EntityCommand(queryString, conn))  
                {  
                    using (DbDataReader rdr =   
                        query.ExecuteReader(CommandBehavior.SequentialAccess))  
                    {  
                        while (rdr.Read())  
                        {  
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);  
                        }  
                    }  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
 [[Top]](#_TOP)  
  
<a name="_LINQ2SQL"></a>   
## <a name="linq-to-sql"></a>LINQ to SQL  
 這則範例中的程式碼會使用 LINQ 查詢來傳回資料當做 Categories 物件，而這些物件會投影成僅包含 CategoryID 和 CategoryName 屬性的匿名型別。 這則範例是以 Northwind 資料內容為基礎。 如需詳細資訊，請參閱[開始](../../../../docs/framework/data/adonet/sql/linq/getting-started.md)。  
  
```  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Collections.Generic  
Imports System.Linq  
Imports System.Text  
Imports Northwind  
  
Class LinqSqlSample  
    Public Shared Sub ExecuteQuery()  
        Using db As NorthwindDataContext = New NorthwindDataContext()  
            Try  
                Dim query = From category In db.Categories _  
                                Select New With _  
                                { _  
                                    .categoryID = category.CategoryID, _  
                                    .categoryName = category.CategoryName _  
                                }  
  
                For Each categoryInfo In query  
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _  
                            categoryInfo.categoryID, categoryInfo.categoryName)  
                Next  
            Catch ex As Exception  
                Console.WriteLine(ex.Message)  
            End Try  
            End Using   
    End Sub  
End Class  
```  
  
 在 C# 中：  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Northwind;  
  
    class LinqSqlSample  
    {  
        public static void ExecuteQuery()  
        {  
            using (NorthwindDataContext db = new NorthwindDataContext())  
            {  
                try  
                {  
                    var query = from category in db.Categories  
                                select new  
                                {  
                                    categoryID = category.CategoryID,  
                                    categoryName = category.CategoryName  
                                };  
  
                    foreach (var categoryInfo in query)  
                    {  
                        Console.WriteLine("vbTab {0} vbTab {1}",  
                            categoryInfo.categoryID, categoryInfo.categoryName);  
                    }  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex.Message);  
                }  
            }  
        }  
    }  
```  
  
 [[Top]](#_TOP)  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [建立資料應用程式](../Topic/Creating%20Data%20Applications.md)   
 [查詢 Entity Data Model （Entity Framework 工作）](http://msdn.microsoft.com/zh-tw/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)   
 [如何︰ 執行傳回匿名型別物件的查詢](http://msdn.microsoft.com/zh-tw/3b264025-e911-4d73-90ce-992d2b9d189d)   
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)