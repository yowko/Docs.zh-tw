---
title: ADO.NET 程式碼範例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 93cc0cf34d2bba23ff0938c8c13d7343d665192d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773601"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="cbf41-102">ADO.NET 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="cbf41-102">ADO.NET code examples</span></span>
<span data-ttu-id="cbf41-103">本主題的程式碼清單示範如何使用下列 ADO.NET 技術來擷取資料庫中的資料：</span><span class="sxs-lookup"><span data-stu-id="cbf41-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="cbf41-104">ADO.NET 資料提供者：</span><span class="sxs-lookup"><span data-stu-id="cbf41-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="cbf41-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="cbf41-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="cbf41-106">[OleDb](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="cbf41-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="cbf41-107">[Odbc](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="cbf41-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="cbf41-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="cbf41-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="cbf41-109">ADO.NET Entity Framework：</span><span class="sxs-lookup"><span data-stu-id="cbf41-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="cbf41-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="cbf41-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="cbf41-111">具型別的的 ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="cbf41-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="cbf41-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="cbf41-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="cbf41-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cbf41-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="cbf41-114">ADO.NET 資料提供者範例</span><span class="sxs-lookup"><span data-stu-id="cbf41-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="cbf41-115">下列程式碼清單將示範如何使用 ADO.NET 資料提供者來擷取資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="cbf41-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="cbf41-116">資料會傳入 `DataReader` 中。</span><span class="sxs-lookup"><span data-stu-id="cbf41-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="cbf41-117">如需詳細資訊，請參閱 <<c0> [ 擷取的資料使用 DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf41-117">For more information, see [Retrieving Data Using a DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="cbf41-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="cbf41-118">SqlClient</span></span>
<span data-ttu-id="cbf41-119">在此範例中的程式碼會假設您可以連接至`Northwind`上 Microsoft SQL Server 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="cbf41-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="cbf41-120">這段程式碼會建立 <xref:System.Data.SqlClient.SqlCommand>，以便從 Products 資料表中選取資料列，並且加入 <xref:System.Data.SqlClient.SqlParameter>，以便將結果限制為 UnitPrice 大於指定之參數值 (在此案例中為 5) 的資料列。</span><span class="sxs-lookup"><span data-stu-id="cbf41-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="cbf41-121"><xref:System.Data.SqlClient.SqlConnection>內開啟`using`區塊，可確保資源會關閉和處置程式碼結束時。</span><span class="sxs-lookup"><span data-stu-id="cbf41-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="cbf41-122">然後，程式碼會使用 <xref:System.Data.SqlClient.SqlDataReader> 來執行此命令，並且在主控台視窗中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="cbf41-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="cbf41-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="cbf41-123">OleDb</span></span>
<span data-ttu-id="cbf41-124">這則範例中的程式碼會假設您可以連接至 Microsoft Access Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="cbf41-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="cbf41-125">這段程式碼會建立 <xref:System.Data.OleDb.OleDbCommand>，以便從 Products 資料表中選取資料列，並且加入 <xref:System.Data.OleDb.OleDbParameter>，以便將結果限制為 UnitPrice 大於指定之參數值 (在此案例中為 5) 的資料列。</span><span class="sxs-lookup"><span data-stu-id="cbf41-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="cbf41-126"><xref:System.Data.OleDb.OleDbConnection> 是在 `using` 區塊內部開啟，可確保程式碼結束時，系統會關閉和處置 (Dispose) 資源。</span><span class="sxs-lookup"><span data-stu-id="cbf41-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="cbf41-127">然後，程式碼會使用 <xref:System.Data.OleDb.OleDbDataReader> 來執行此命令，並且在主控台視窗中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="cbf41-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="cbf41-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="cbf41-128">Odbc</span></span>
<span data-ttu-id="cbf41-129">這則範例中的程式碼會假設您可以連接至 Microsoft Access Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="cbf41-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="cbf41-130">這段程式碼會建立 <xref:System.Data.Odbc.OdbcCommand>，以便從 Products 資料表中選取資料列，並且加入 <xref:System.Data.Odbc.OdbcParameter>，以便將結果限制為 UnitPrice 大於指定之參數值 (在此案例中為 5) 的資料列。</span><span class="sxs-lookup"><span data-stu-id="cbf41-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="cbf41-131"><xref:System.Data.Odbc.OdbcConnection>內開啟`using`區塊，可確保資源會關閉和處置程式碼結束時。</span><span class="sxs-lookup"><span data-stu-id="cbf41-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="cbf41-132">然後，程式碼會使用 <xref:System.Data.Odbc.OdbcDataReader> 來執行此命令，並且在主控台視窗中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="cbf41-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="cbf41-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="cbf41-133">OracleClient</span></span>
<span data-ttu-id="cbf41-134">這則範例中的程式碼會假設您已連接到 Oracle 伺服器上的 DEMO.CUSTOMER。</span><span class="sxs-lookup"><span data-stu-id="cbf41-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="cbf41-135">您也必須加入 System.Data.OracleClient.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="cbf41-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="cbf41-136">此程式碼會將資料傳入 <xref:System.Data.OracleClient.OracleDataReader> 中。</span><span class="sxs-lookup"><span data-stu-id="cbf41-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="cbf41-137">Entity Framework 範例</span><span class="sxs-lookup"><span data-stu-id="cbf41-137">Entity Framework examples</span></span>
<span data-ttu-id="cbf41-138">下列程式碼清單將示範如何透過查詢 Entity Data Model (EDM) 中的實體，擷取資料來源中的資料。</span><span class="sxs-lookup"><span data-stu-id="cbf41-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="cbf41-139">這些範例會使用[Northwind 模型](https://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638)。</span><span class="sxs-lookup"><span data-stu-id="cbf41-139">These examples use the [Northwind model](https://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span></span> <span data-ttu-id="cbf41-140">如需詳細資訊，請參閱 < [Entity Framework 概觀](../../../../docs/framework/data/adonet/ef/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf41-140">For more information, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="cbf41-141">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="cbf41-141">LINQ to Entities</span></span>
<span data-ttu-id="cbf41-142">這則範例中的程式碼會使用 LINQ 查詢來傳回資料當做 Categories 物件，而這些物件會投影成僅包含 CategoryID 和 CategoryName 屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="cbf41-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="cbf41-143">如需詳細資訊，請參閱 < [LINQ to Entities 概觀](https://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6)。</span><span class="sxs-lookup"><span data-stu-id="cbf41-143">For more information, see [LINQ to Entities Overview](https://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span></span>

```csharp
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

```vb
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

### <a name="typed-objectquery"></a><span data-ttu-id="cbf41-144">具型別的 ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="cbf41-144">Typed ObjectQuery</span></span>
<span data-ttu-id="cbf41-145">這則範例中的程式碼會使用 <xref:System.Data.Objects.ObjectQuery%601> 來傳回資料當做 Categories 物件。</span><span class="sxs-lookup"><span data-stu-id="cbf41-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="cbf41-146">如需詳細資訊，請參閱 <<c0> [ 物件查詢](https://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276)。</span><span class="sxs-lookup"><span data-stu-id="cbf41-146">For more information, see [Object Queries](https://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span></span>

```csharp
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

```vb
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

### <a name="entityclient"></a><span data-ttu-id="cbf41-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="cbf41-147">EntityClient</span></span>
<span data-ttu-id="cbf41-148">這則範例中的程式碼會使用 <xref:System.Data.EntityClient.EntityCommand> 來執行 Entity SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="cbf41-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="cbf41-149">這個查詢會傳回代表 Categories 實體類型之執行個體 (Instance) 的記錄清單。</span><span class="sxs-lookup"><span data-stu-id="cbf41-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="cbf41-150"><xref:System.Data.EntityClient.EntityDataReader> 可用於存取結果集中的資料記錄。</span><span class="sxs-lookup"><span data-stu-id="cbf41-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="cbf41-151">如需詳細資訊，請參閱 < [Entity Framework 的 EntityClient 提供者](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf41-151">For more information, see [EntityClient Provider for the Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>

```csharp
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

```vb
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

## <a name="linq-to-sql"></a><span data-ttu-id="cbf41-152">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cbf41-152">LINQ to SQL</span></span>
<span data-ttu-id="cbf41-153">這則範例中的程式碼會使用 LINQ 查詢來傳回資料當做 Categories 物件，而這些物件會投影成僅包含 CategoryID 和 CategoryName 屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="cbf41-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="cbf41-154">這則範例是以 Northwind 資料內容為基礎。</span><span class="sxs-lookup"><span data-stu-id="cbf41-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="cbf41-155">如需詳細資訊，請參閱[使用者入門](../../../../docs/framework/data/adonet/sql/linq/getting-started.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf41-155">For more information, see [Getting Started](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span></span>

```csharp
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

```vb
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

## <a name="see-also"></a><span data-ttu-id="cbf41-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf41-156">See also</span></span>
 [<span data-ttu-id="cbf41-157">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="cbf41-157">ADO.NET Overview</span></span>](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [<span data-ttu-id="cbf41-158">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="cbf41-158">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="cbf41-159">建立資料應用程式</span><span class="sxs-lookup"><span data-stu-id="cbf41-159">Creating Data Applications</span></span>](https://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [<span data-ttu-id="cbf41-160">查詢 Entity Data Model （Entity Framework 工作）</span><span class="sxs-lookup"><span data-stu-id="cbf41-160">Querying an Entity Data Model (Entity Framework Tasks)</span></span>](https://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [<span data-ttu-id="cbf41-161">如何： 執行可傳回匿名類型集合的查詢</span><span class="sxs-lookup"><span data-stu-id="cbf41-161">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [<span data-ttu-id="cbf41-162">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="cbf41-162">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)  
