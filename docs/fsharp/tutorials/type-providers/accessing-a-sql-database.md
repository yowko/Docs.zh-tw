---
title: "逐步解說：使用型別提供者存取 SQL 資料庫 (F#)"
description: "了解如何使用 SqlDataConnection (LINQ to SQL) 型別提供者在 F # 3.0 有即時資料庫連接時，產生 SQL 資料庫類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: 7177eca33ded712308bbc6198040d833b7364d55
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a><span data-ttu-id="1987b-104">逐步解說：使用型別提供者存取 SQL 資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-104">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="1987b-105">本指南針對 F # 3.0 所撰寫，而且會更新。</span><span class="sxs-lookup"><span data-stu-id="1987b-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="1987b-106">請參閱 [FSharp.Data](http://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。</span><span class="sxs-lookup"><span data-stu-id="1987b-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="1987b-107">應用程式開發介面參考連結將帶您到 MSDN。</span><span class="sxs-lookup"><span data-stu-id="1987b-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="1987b-108">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="1987b-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="1987b-109">本逐步解說將說明如何使用 SqlDataConnection (LINQ to SQL) 型別提供者所提供之 F # 3.0 有即時連接至資料庫時，SQL 資料庫中產生的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1987b-109">This walkthrough explains how to use the SqlDataConnection (LINQ to SQL) type provider that is available in F# 3.0 to generate types for data in a SQL database when you have a live connection to a database.</span></span> <span data-ttu-id="1987b-110">如果您沒有即時連接到資料庫，但您需要 LINQ to SQL 結構描述檔案 （DBML 檔案），請參閱[逐步解說： 產生 F # 類型從 DBML 檔案](generating-fsharp-types-from-dbml.md)。</span><span class="sxs-lookup"><span data-stu-id="1987b-110">If you do not have a live connection to a database, but you do have a LINQ to SQL schema file (DBML file), see [Walkthrough: Generating F# Types from a DBML File](generating-fsharp-types-from-dbml.md).</span></span>

<span data-ttu-id="1987b-111">這個逐步解說將說明下列工作。</span><span class="sxs-lookup"><span data-stu-id="1987b-111">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="1987b-112">必須執行這些工作順利完成本逐步解說的順序如下：</span><span class="sxs-lookup"><span data-stu-id="1987b-112">These tasks must be performed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="1987b-113">準備測試資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-113">Preparing a test database</span></span>

- <span data-ttu-id="1987b-114">建立專案</span><span class="sxs-lookup"><span data-stu-id="1987b-114">Creating the project</span></span>

- <span data-ttu-id="1987b-115">設定類型提供者</span><span class="sxs-lookup"><span data-stu-id="1987b-115">Setting up a type provider</span></span>

- <span data-ttu-id="1987b-116">查詢資料</span><span class="sxs-lookup"><span data-stu-id="1987b-116">Querying the data</span></span>

- <span data-ttu-id="1987b-117">使用可為 null 的欄位</span><span class="sxs-lookup"><span data-stu-id="1987b-117">Working with nullable fields</span></span>

- <span data-ttu-id="1987b-118">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="1987b-118">Calling a stored procedure</span></span>

- <span data-ttu-id="1987b-119">更新資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-119">Updating the database</span></span>

- <span data-ttu-id="1987b-120">執行 TRANSACT-SQL 程式碼</span><span class="sxs-lookup"><span data-stu-id="1987b-120">Executing Transact-SQL code</span></span>

- <span data-ttu-id="1987b-121">使用完整資料內容</span><span class="sxs-lookup"><span data-stu-id="1987b-121">Using the full data context</span></span>

- <span data-ttu-id="1987b-122">刪除資料</span><span class="sxs-lookup"><span data-stu-id="1987b-122">Deleting data</span></span>

- <span data-ttu-id="1987b-123">建立測試資料庫 （如有需要）</span><span class="sxs-lookup"><span data-stu-id="1987b-123">Create a test database (as needed)</span></span>

## <a name="preparing-a-test-database"></a><span data-ttu-id="1987b-124">準備測試資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-124">Preparing a Test Database</span></span>
<span data-ttu-id="1987b-125">在伺服器上執行 SQL Server，建立資料庫，以進行測試。</span><span class="sxs-lookup"><span data-stu-id="1987b-125">On a server that's running SQL Server, create a database for testing purposes.</span></span> <span data-ttu-id="1987b-126">您可以使用 「 資料庫建立指令碼的區段中的此頁面底部[建立測試資料庫](#creating-a-test-database)若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="1987b-126">You can use the database create script at the bottom of this page in the section [Creating a test database](#creating-a-test-database) to do this.</span></span>


#### <a name="to-prepare-a-test-database"></a><span data-ttu-id="1987b-127">若要準備測試資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-127">To prepare a test database</span></span>

<span data-ttu-id="1987b-128">執行 MyDatabase 建立指令碼，請開啟**檢視**功能表，然後選擇  **SQL Server 物件總管**或選擇 Ctrl +\, Ctrl + S 鍵。</span><span class="sxs-lookup"><span data-stu-id="1987b-128">To run the MyDatabase Create Script, open the **View** menu, and then choose **SQL Server Object Explorer** or choose the Ctrl+\, Ctrl+S keys.</span></span> <span data-ttu-id="1987b-129">在**SQL Server 物件總管**視窗中，開啟適當的執行個體的捷徑功能表，選擇 **新查詢**複製底部的這個頁面上，指令碼，然後貼到編輯器的 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1987b-129">In **SQL Server Object Explorer** window, open the shortcut menu for the appropriate instance, choose **New Query**, copy the script at the bottom of this page, and then paste the script into the editor.</span></span> <span data-ttu-id="1987b-130">若要執行的 SQL 指令碼，選擇工具列圖示，三重平滑的符號，或選擇 Ctrl + Q 鍵。</span><span class="sxs-lookup"><span data-stu-id="1987b-130">To run the SQL script, choose the toolbar icon with the triangular symbol, or choose the Ctrl+Q keys.</span></span> <span data-ttu-id="1987b-131">如需有關**SQL Server 物件總管**，請參閱[連接的資料庫開發](https://msdn.microsoft.com/library/hh272679(VS.103).aspx)。</span><span class="sxs-lookup"><span data-stu-id="1987b-131">For more information about **SQL Server Object Explorer**, see [Connected Database Development](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span></span>


## <a name="creating-the-project"></a><span data-ttu-id="1987b-132">建立專案</span><span class="sxs-lookup"><span data-stu-id="1987b-132">Creating the project</span></span>
<span data-ttu-id="1987b-133">接下來，您可以建立 F # 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="1987b-133">Next, you create an F# application project.</span></span>


#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="1987b-134">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="1987b-134">To create and set up the project</span></span>

1. <span data-ttu-id="1987b-135">建立新的 F # 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="1987b-135">Create a new F# Application project.</span></span>

2. <span data-ttu-id="1987b-136">將參考加入至[FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3)，以及`System.Data`，和`System.Data.Linq`。</span><span class="sxs-lookup"><span data-stu-id="1987b-136">Add references to [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), as well as `System.Data`, and `System.Data.Linq`.</span></span>

3. <span data-ttu-id="1987b-137">將下列程式碼加入至您 F # 程式碼檔案頂端 Program.fs 開啟適當的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1987b-137">Open the appropriate namespaces by adding the following lines of code to the top of your F# code file Program.fs.</span></span>

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. <span data-ttu-id="1987b-138">如同大部分 F # 程式中，您可以在此逐步解說中當做編譯的程式，執行程式碼，或者您可以執行它以互動方式做為指令碼。</span><span class="sxs-lookup"><span data-stu-id="1987b-138">As with most F# programs, you can execute the code in this walkthrough as a compiled program, or you can run it interactively as a script.</span></span> <span data-ttu-id="1987b-139">如果您想要使用指令碼，開啟專案的選取節點的捷徑功能表**加入新項目**、 F # 指令碼檔案，加上指令碼中每一個步驟中加入程式碼。</span><span class="sxs-lookup"><span data-stu-id="1987b-139">If you prefer to use scripts, open the shortcut menu for the project node, select **Add New Item**, add an F# script file, and add the code in each step to the script.</span></span> <span data-ttu-id="1987b-140">您必須在要載入的組件參考之檔案的頂端加入下列幾行。</span><span class="sxs-lookup"><span data-stu-id="1987b-140">You will need to add the following lines at the top of the file to load the assembly references.</span></span>

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  <span data-ttu-id="1987b-141">然後，當您將按 Alt + Enter 來執行 F # Interactive 中，您可以選取每個程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="1987b-141">You can then select each block of code as you add it and press Alt+Enter to run it in F# Interactive.</span></span>

## <a name="setting-up-a-type-provider"></a><span data-ttu-id="1987b-142">設定類型提供者</span><span class="sxs-lookup"><span data-stu-id="1987b-142">Setting up a type provider</span></span>
<span data-ttu-id="1987b-143">在此步驟中，您會建立型別提供者的資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="1987b-143">In this step, you create a type provider for your database schema.</span></span>


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a><span data-ttu-id="1987b-144">若要設定從直接連接資料庫的型別提供者</span><span class="sxs-lookup"><span data-stu-id="1987b-144">To set up the type provider from a direct database connection</span></span>

<span data-ttu-id="1987b-145">有兩個重要的行，您需要以建立可讓您查詢 SQL 資料庫使用的型別提供者類型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1987b-145">There are two critical lines of code that you need in order to create the types that you can use to query a SQL database using the type provider.</span></span> <span data-ttu-id="1987b-146">首先，您具現化型別提供者。</span><span class="sxs-lookup"><span data-stu-id="1987b-146">First, you instantiate the type provider.</span></span> <span data-ttu-id="1987b-147">若要這樣做，建立 外觀類型縮寫`SqlDataConnection`與靜態泛型參數。</span><span class="sxs-lookup"><span data-stu-id="1987b-147">To do this, create what looks like a type abbreviation for a `SqlDataConnection` with a static generic parameter.</span></span> <span data-ttu-id="1987b-148">`SqlDataConnection`SQL 型別提供者，而且不應該與混淆`SqlConnection`類型，它是在 ADO.NET 程式設計中使用。</span><span class="sxs-lookup"><span data-stu-id="1987b-148">`SqlDataConnection` is a SQL type provider, and should not be confused with `SqlConnection` type that is used in ADO.NET programming.</span></span> <span data-ttu-id="1987b-149">如果您有一個資料庫，您想要連接，而且連接字串，使用下列程式碼叫用型別提供者。</span><span class="sxs-lookup"><span data-stu-id="1987b-149">If you have a database that you want to connect to, and have a connection string, use the following code to invoke the type provider.</span></span> <span data-ttu-id="1987b-150">取代為指定的字串範例連接字串。</span><span class="sxs-lookup"><span data-stu-id="1987b-150">Substitute your own connection string for the example string given.</span></span> <span data-ttu-id="1987b-151">例如，如果您的伺服器 MYSERVER 和資料庫執行個體是執行個體、 資料庫名稱是 MyDatabase，和您想要使用 Windows 驗證來存取資料庫，則連接字串會是做為提供下列的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1987b-151">For example, if your server is MYSERVER and the database instance is INSTANCE, the database name is MyDatabase, and you want to use Windows Authentication to access the database, then the connection string would be as given in the following example code.</span></span>

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

<span data-ttu-id="1987b-152">現在您有一個型別， `dbSchema`，這是包含所有產生的型別代表資料庫資料表的父類型。</span><span class="sxs-lookup"><span data-stu-id="1987b-152">Now you have a type, `dbSchema`, which is a parent type that contains all the generated types that represent database tables.</span></span> <span data-ttu-id="1987b-153">您也可以是物件， `db`，其中包含做為其成員資料庫中的所有資料表。</span><span class="sxs-lookup"><span data-stu-id="1987b-153">You also have an object, `db`, which has as its members all the tables in the database.</span></span> <span data-ttu-id="1987b-154">資料表名稱屬性，且這些屬性的類型由 F # 編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="1987b-154">The table names are properties, and the type of these properties is generated by the F# compiler.</span></span> <span data-ttu-id="1987b-155">將型別本身顯示底下的巢狀型別為`dbSchema.ServiceTypes`。</span><span class="sxs-lookup"><span data-stu-id="1987b-155">The types themselves appear as nested types under `dbSchema.ServiceTypes`.</span></span> <span data-ttu-id="1987b-156">因此，擷取這些資料表的資料列的任何資料，都會產生該資料表的適當類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1987b-156">Therefore, any data retrieved for rows of these tables is an instance of the appropriate type that was generated for that table.</span></span> <span data-ttu-id="1987b-157">類型的名稱是`ServiceTypes.Table1`。</span><span class="sxs-lookup"><span data-stu-id="1987b-157">The name of the type is `ServiceTypes.Table1`.</span></span>

<span data-ttu-id="1987b-158">您熟悉如何 F # 語言解譯成 SQL 查詢的查詢，檢閱設定列`Log`資料內容上的屬性。</span><span class="sxs-lookup"><span data-stu-id="1987b-158">To familiarize yourself with how the F# language interprets queries into SQL queries, review the line that sets the `Log` property on the data context.</span></span>

<span data-ttu-id="1987b-159">若要進一步探索型別提供者所建立的類型，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="1987b-159">To further explore the types created by the type provider, add the following code.</span></span>

```fsharp
let table1 = db.Table1
```

<span data-ttu-id="1987b-160">將滑鼠停留在`table1`以查看它的型別。</span><span class="sxs-lookup"><span data-stu-id="1987b-160">Hover over `table1` to see its type.</span></span> <span data-ttu-id="1987b-161">它的類型是`System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>`和泛型引數表示每個資料列的類型是產生的型別， `dbSchema.ServiceTypes.Table1`。</span><span class="sxs-lookup"><span data-stu-id="1987b-161">Its type is `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` and the generic argument implies that the type of each row is the generated type, `dbSchema.ServiceTypes.Table1`.</span></span> <span data-ttu-id="1987b-162">編譯器會在資料庫中建立的每個資料表類似的類型。</span><span class="sxs-lookup"><span data-stu-id="1987b-162">The compiler creates a similar type for each table in the database.</span></span>

## <a name="querying-the-data"></a><span data-ttu-id="1987b-163">查詢資料</span><span class="sxs-lookup"><span data-stu-id="1987b-163">Querying the data</span></span>
<span data-ttu-id="1987b-164">在此步驟中，您可以撰寫查詢，使用 F # 查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="1987b-164">In this step, you write a query using F# query expressions.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="1987b-165">若要查詢資料</span><span class="sxs-lookup"><span data-stu-id="1987b-165">To query the data</span></span>

1. <span data-ttu-id="1987b-166">現在在資料庫中建立該資料表的查詢。</span><span class="sxs-lookup"><span data-stu-id="1987b-166">Now create a query for that table in the database.</span></span> <span data-ttu-id="1987b-167">加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="1987b-167">Add the following code.</span></span>

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  <span data-ttu-id="1987b-168">文字的外觀`query`指出這是查詢運算式會產生類似一般資料庫查詢結果的集合的計算運算式的型別。</span><span class="sxs-lookup"><span data-stu-id="1987b-168">The appearance of the word `query` indicates that this is a query expression, a type of computation expression that generates a collection of results similar of a typical database query.</span></span> <span data-ttu-id="1987b-169">如果您將滑鼠停留在查詢，您會看到它是的執行個體[Linq.QueryBuilder 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d)，定義查詢計算運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="1987b-169">If you hover over query, you will see that it is an instance of [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), a type that defines the query computation expression.</span></span> <span data-ttu-id="1987b-170">如果您將滑鼠停留在`query1`，您會看到它是的執行個體`System.Linq.IQueryable`。</span><span class="sxs-lookup"><span data-stu-id="1987b-170">If you hover over `query1`, you will see that it is an instance of `System.Linq.IQueryable`.</span></span> <span data-ttu-id="1987b-171">正如其名，`System.Linq.IQueryable`代表資料查詢，不是查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="1987b-171">As the name suggests, `System.Linq.IQueryable` represents data that may be queried, not the result of a query.</span></span> <span data-ttu-id="1987b-172">查詢受限於延遲評估，也就是說，資料庫才查詢評估查詢時。</span><span class="sxs-lookup"><span data-stu-id="1987b-172">A query is subject to lazy evaluation, which means that the database is only queried when the query is evaluated.</span></span> <span data-ttu-id="1987b-173">最後一行將透過查詢傳`Seq.iter`。</span><span class="sxs-lookup"><span data-stu-id="1987b-173">The final line passes the query through `Seq.iter`.</span></span> <span data-ttu-id="1987b-174">查詢是可列舉，而且可能會像順序逐一查看。</span><span class="sxs-lookup"><span data-stu-id="1987b-174">Queries are enumerable and may be iterated like sequences.</span></span> <span data-ttu-id="1987b-175">如需詳細資訊，請參閱[查詢運算式](../../language-reference/query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="1987b-175">For more information, see [Query Expressions](../../language-reference/query-expressions.md).</span></span>

2. <span data-ttu-id="1987b-176">現在加入至查詢的查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="1987b-176">Now add a query operator to the query.</span></span> <span data-ttu-id="1987b-177">有許多查詢運算子可讓您可以建構複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="1987b-177">There are a number of query operators available that you can use to construct more complex queries.</span></span> <span data-ttu-id="1987b-178">此範例也會顯示您可以用來消除查詢變數，並改為使用管線運算子。</span><span class="sxs-lookup"><span data-stu-id="1987b-178">This example also shows that you can eliminate the query variable and use a pipeline operator instead.</span></span>

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. <span data-ttu-id="1987b-179">加入兩個資料表的聯結與更複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="1987b-179">Add a more complex query with a join of two tables.</span></span>

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. <span data-ttu-id="1987b-180">在真實世界的程式碼，在您的查詢參數通常值或變數，不會進行編譯時間常數。</span><span class="sxs-lookup"><span data-stu-id="1987b-180">In real-world code, the parameters in your query are usually values or variables, not compile-time constants.</span></span> <span data-ttu-id="1987b-181">加入下列程式碼包裝函式，使用參數，然後再撥打該函式值為 10 中的查詢。</span><span class="sxs-lookup"><span data-stu-id="1987b-181">Add the following code that wraps a query in a function that takes a parameter, and then calls that function with the value 10.</span></span>

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a><span data-ttu-id="1987b-182">使用可為 null 的欄位</span><span class="sxs-lookup"><span data-stu-id="1987b-182">Working with nullable fields</span></span>
<span data-ttu-id="1987b-183">在資料庫中，欄位通常會允許 null 值。</span><span class="sxs-lookup"><span data-stu-id="1987b-183">In databases, fields often allow null values.</span></span> <span data-ttu-id="1987b-184">在.NET 類型系統中，您無法使用一般的數值資料類型，允許 null 因為這些型別沒有可能的值為 null 的資料。</span><span class="sxs-lookup"><span data-stu-id="1987b-184">In the .NET type system, you cannot use the ordinary numerical data types for data that allows nulls because those types do not have null as a possible value.</span></span> <span data-ttu-id="1987b-185">因此，這些值都由執行個體`System.Nullable`型別。</span><span class="sxs-lookup"><span data-stu-id="1987b-185">Therefore, these values are represented by instances of `System.Nullable` type.</span></span> <span data-ttu-id="1987b-186">而不是存取這類欄位的值，直接與欄位的名稱，您需要加入一些額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="1987b-186">Instead of accessing the value of such fields directly with the name of the field, you need to add some extra steps.</span></span> <span data-ttu-id="1987b-187">您可以使用`System.Nullable.Value`屬性來存取可為 null 型別的基礎值。</span><span class="sxs-lookup"><span data-stu-id="1987b-187">You can use the `System.Nullable.Value` property to access the underlying value of a nullable type.</span></span> <span data-ttu-id="1987b-188">`System.Nullable.Value`屬性擲回例外狀況的物件是 null，而不是值。</span><span class="sxs-lookup"><span data-stu-id="1987b-188">The `System.Nullable.Value` property throws an exception if the object is null rather than having a value.</span></span> <span data-ttu-id="1987b-189">您可以使用`System.Nullable.HasValue`布林方法，以判斷是否有值存在，或使用`System.Nullable.GetValueOrDefault()`以確保您在所有情況下有實際值。</span><span class="sxs-lookup"><span data-stu-id="1987b-189">You can use the `System.Nullable.HasValue` Boolean method to determine if a value exists, or use `System.Nullable.GetValueOrDefault()` to ensure that you have an actual value in all cases.</span></span> <span data-ttu-id="1987b-190">如果您使用`System.Nullable.GetValueOrDefault()`和 null 值在資料庫中，則會被取代的值為空字串的字串類型。 例如，0 的整數類資料類型或浮點 0.0 點類型。</span><span class="sxs-lookup"><span data-stu-id="1987b-190">If you use `System.Nullable.GetValueOrDefault()` and there is a null in the database, then it is replaced with a value such as an empty string for string types, 0 for integral types or 0.0 for floating point types.</span></span>

<span data-ttu-id="1987b-191">當您需要在可為 null 值上執行等號比較測試或比較`where`子句的查詢中，您可以使用可為 null 的運算子中找到[Linq.NullableOperators 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="1987b-191">When you need to perform equality tests or comparisons on nullable values in a `where` clause in a query, you can use the nullable operators found in the [Linq.NullableOperators Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span></span> <span data-ttu-id="1987b-192">這些就像是一般比較運算子`=`， `>`， `<=`，依此類推，不同之處在於問號會出現在左邊或右邊運算子可為 null 的值。</span><span class="sxs-lookup"><span data-stu-id="1987b-192">These are like the regular comparison operators `=`, `>`, `<=`, and so on, except that a question mark appears on the left or right of the operator where the nullable values are.</span></span> <span data-ttu-id="1987b-193">比方說，運算子`>?`大於-運算子右邊的可為 null 值。</span><span class="sxs-lookup"><span data-stu-id="1987b-193">For example, the operator `>?` is a greater-than operator with a nullable value on the right.</span></span> <span data-ttu-id="1987b-194">這些運算子的運作的方式是，如果任一邊的運算式為 null，則運算式評估為`false`。</span><span class="sxs-lookup"><span data-stu-id="1987b-194">The way these operators work is that if either side of the expression is null, the expression evaluates to `false`.</span></span> <span data-ttu-id="1987b-195">在`where`子句，這通常表示包含 null 欄位的資料列會未選取，而且不會傳回查詢結果中。</span><span class="sxs-lookup"><span data-stu-id="1987b-195">In a `where` clause, this generally means that the rows that contain null fields are not selected and not returned in the query results.</span></span>


#### <a name="to-work-with-nullable-fields"></a><span data-ttu-id="1987b-196">若要使用可為 null 的欄位</span><span class="sxs-lookup"><span data-stu-id="1987b-196">To work with nullable fields</span></span>

<span data-ttu-id="1987b-197">下列程式碼將示範使用可為 null 的值;假設**TestData1**是允許 null 整數欄位。</span><span class="sxs-lookup"><span data-stu-id="1987b-197">The following code shows working with nullable values; assume that **TestData1** is an integer field that allows nulls.</span></span>

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="1987b-198">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="1987b-198">Calling a stored procedure</span></span>
<span data-ttu-id="1987b-199">在資料庫上的任何預存程序可以呼叫從 F #。</span><span class="sxs-lookup"><span data-stu-id="1987b-199">Any stored procedures on the database can be called from F#.</span></span> <span data-ttu-id="1987b-200">您必須設定的靜態參數`StoredProcedures`至`true`型別提供者具現化。</span><span class="sxs-lookup"><span data-stu-id="1987b-200">You must set the static parameter `StoredProcedures` to `true` in the type provider instantiation.</span></span> <span data-ttu-id="1987b-201">型別提供者`SqlDataConnection`包含數個靜態方法，可讓您設定所產生的型別。</span><span class="sxs-lookup"><span data-stu-id="1987b-201">The type provider `SqlDataConnection` contains several static methods that you can use to configure the types that are generated.</span></span> <span data-ttu-id="1987b-202">其中的完整說明，請參閱[SqlDataConnection 類型提供者](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="1987b-202">For a complete description of these, see [SqlDataConnection Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span></span> <span data-ttu-id="1987b-203">資料內容型別上的方法會產生每個預存程序。</span><span class="sxs-lookup"><span data-stu-id="1987b-203">A method on the data context type is generated for each stored procedure.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="1987b-204">若要呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="1987b-204">To call a stored procedure</span></span>

<span data-ttu-id="1987b-205">如果預存程序會採用可為 null 的參數，您需要將適當`System.Nullable`值。</span><span class="sxs-lookup"><span data-stu-id="1987b-205">If the stored procedures takes parameters that are nullable, you need to pass an appropriate `System.Nullable` value.</span></span> <span data-ttu-id="1987b-206">傳回純量或資料表的預存程序方法的傳回值是`System.Data.Linq.ISingleResult`，其中包含屬性，讓您存取傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="1987b-206">The return value of a stored procedure method that returns a scalar or a table is `System.Data.Linq.ISingleResult`, which contains properties that enable you to access the returned data.</span></span> <span data-ttu-id="1987b-207">型別引數`System.Data.Linq.ISingleResult`相依於特定的程序，而且也是一樣的型別提供者產生的型別。</span><span class="sxs-lookup"><span data-stu-id="1987b-207">The type argument for `System.Data.Linq.ISingleResult` depends on the specific procedure and is also one of the types that the type provider generates.</span></span> <span data-ttu-id="1987b-208">名為預存程序`Procedure1`，型別是`Procedure1Result`。</span><span class="sxs-lookup"><span data-stu-id="1987b-208">For a stored procedure named `Procedure1`, the type is `Procedure1Result`.</span></span> <span data-ttu-id="1987b-209">型別`Procedure1Result`包含名稱的資料行中傳回的資料表，或傳回純量值的預存程序，它表示的傳回值。</span><span class="sxs-lookup"><span data-stu-id="1987b-209">The type `Procedure1Result` contains the names of the columns in a returned table, or, for a stored procedure that returns a scalar value, it represents the return value.</span></span>

<span data-ttu-id="1987b-210">下列程式碼會假設是程序`Procedure1`採用兩個可為 null 的整數，做為參數的資料庫，執行查詢，傳回的資料行`TestData1`，並傳回一個整數。</span><span class="sxs-lookup"><span data-stu-id="1987b-210">The following code assumes that there is a procedure `Procedure1` on the database that takes two nullable integers as parameters, runs a query that returns a column named `TestData1`, and returns an integer.</span></span>

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a><span data-ttu-id="1987b-211">更新資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-211">Updating the database</span></span>
<span data-ttu-id="1987b-212">LINQ DataContext 類型包含方法，讓您更輕鬆地在完整輸入的方式，與產生的型別中執行交易的資料庫更新。</span><span class="sxs-lookup"><span data-stu-id="1987b-212">The LINQ DataContext type contains methods that make it easier to perform transacted database updates in a fully typed fashion with the generated types.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="1987b-213">若要更新資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-213">To update the database</span></span>

1. <span data-ttu-id="1987b-214">下列程式碼，在數個資料列會加入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="1987b-214">In the following code, several rows are added to the database.</span></span> <span data-ttu-id="1987b-215">如果您只新增一個資料列，您可以使用`System.Data.Linq.Table.InsertOnSubmit()`來指定要加入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="1987b-215">If you are only adding a row, you can use `System.Data.Linq.Table.InsertOnSubmit()` to specify the new row to add.</span></span> <span data-ttu-id="1987b-216">如果您要插入多個資料列，您應該將其放入集合，且呼叫`System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`。</span><span class="sxs-lookup"><span data-stu-id="1987b-216">If you are inserting multiple rows, you should put them into a collection and call `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span></span> <span data-ttu-id="1987b-217">當您呼叫其中一種方法時，資料庫不會立即變更。</span><span class="sxs-lookup"><span data-stu-id="1987b-217">When you call either of these methods, the database is not immediately changed.</span></span> <span data-ttu-id="1987b-218">您必須呼叫`System.Data.Linq.DataContext.SubmitChanges`實際認可變更。</span><span class="sxs-lookup"><span data-stu-id="1987b-218">You must call `System.Data.Linq.DataContext.SubmitChanges` to actually commit the changes.</span></span> <span data-ttu-id="1987b-219">根據預設，您才能執行的所有項目呼叫`System.Data.Linq.DataContext.SubmitChanges`是隱含的相同交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="1987b-219">By default, everything that you do before you call `System.Data.Linq.DataContext.SubmitChanges` is implicitly part of the same transaction.</span></span>

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. <span data-ttu-id="1987b-220">現在清除資料列藉由呼叫刪除作業。</span><span class="sxs-lookup"><span data-stu-id="1987b-220">Now clean up the rows by calling a delete operation.</span></span>

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a><span data-ttu-id="1987b-221">執行 TRANSACT-SQL 程式碼</span><span class="sxs-lookup"><span data-stu-id="1987b-221">Executing Transact-SQL code</span></span>
<span data-ttu-id="1987b-222">您也可以使用來直接指定 TRANSACT-SQL`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`方法`DataContext`類別。</span><span class="sxs-lookup"><span data-stu-id="1987b-222">You can also specify Transact-SQL directly by using the `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` method on the `DataContext` class.</span></span>


#### <a name="to-execute-custom-sql-commands"></a><span data-ttu-id="1987b-223">若要執行自訂的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="1987b-223">To execute custom SQL commands</span></span>

<span data-ttu-id="1987b-224">下列程式碼會示範如何將 SQL 命令，將記錄插入資料表也可以從資料表刪除記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="1987b-224">The following code shows how to send SQL commands to insert a record into a table and also to delete a record from a table.</span></span>

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a><span data-ttu-id="1987b-225">使用完整資料內容</span><span class="sxs-lookup"><span data-stu-id="1987b-225">Using the full data context</span></span>
<span data-ttu-id="1987b-226">在上一個範例中，`GetDataContext`方法用來取得所謂*簡化的資料內容*資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="1987b-226">In the previous examples, the `GetDataContext` method was used to get what is called the *simplified data context* for the database schema.</span></span> <span data-ttu-id="1987b-227">簡化的資料內容是您更輕鬆地使用當您建構查詢時，因為沒有為許多成員時。</span><span class="sxs-lookup"><span data-stu-id="1987b-227">The simplified data context is easier to use when you are constructing queries because there are not as many members available.</span></span> <span data-ttu-id="1987b-228">因此，當您瀏覽在 IntelliSense 中的屬性，您可以專注於資料庫結構，例如資料表和預存程序。</span><span class="sxs-lookup"><span data-stu-id="1987b-228">Therefore, when you browse the properties in IntelliSense, you can focus on the database structure, such as the tables and stored procedures.</span></span> <span data-ttu-id="1987b-229">不過，沒有限制您可以使用簡化的資料內容執行。</span><span class="sxs-lookup"><span data-stu-id="1987b-229">However, there is a limit to what you can do with the simplified data context.</span></span> <span data-ttu-id="1987b-230">可讓您執行其他動作的完整資料內容。</span><span class="sxs-lookup"><span data-stu-id="1987b-230">A full data context that provides the ability to perform other actions.</span></span> <span data-ttu-id="1987b-231">也可以使用此檔案位於`ServiceTypes`和名稱為*DataContext*如果您所提供的靜態參數。</span><span class="sxs-lookup"><span data-stu-id="1987b-231">is also available This is located in the `ServiceTypes` and has the name of the *DataContext* static parameter if you provided it.</span></span> <span data-ttu-id="1987b-232">如果您未提供，資料內容型別名稱會為您產生由 SqlMetal.exe 根據其他的輸入。</span><span class="sxs-lookup"><span data-stu-id="1987b-232">If you did not provide it, the name of the data context type is generated for you by SqlMetal.exe based on the other input.</span></span> <span data-ttu-id="1987b-233">完整資料內容繼承自`System.Data.Linq.DataContext`並公開其基底類別，例如包含 ADO.NET 資料類型的參考成員`Connection`物件，這類方法`System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])`和`System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])`，您可以使用在 SQL 中，撰寫查詢而也表示明確使用交易。</span><span class="sxs-lookup"><span data-stu-id="1987b-233">The full data context inherits from `System.Data.Linq.DataContext` and exposes the members of its base class, including references to ADO.NET data types such as the `Connection` object, methods such as `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` and `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` that you can use to write queries in SQL, and also a means to work with transactions explicitly.</span></span>


#### <a name="to-use-the-full-data-context"></a><span data-ttu-id="1987b-234">若要使用完整資料內容</span><span class="sxs-lookup"><span data-stu-id="1987b-234">To use the full data context</span></span>

<span data-ttu-id="1987b-235">下列程式碼示範如何取得完整的資料內容物件，並使用它來直接對資料庫執行命令。</span><span class="sxs-lookup"><span data-stu-id="1987b-235">The following code demonstrates getting a full data context object and using it to execute commands directly against the database.</span></span> <span data-ttu-id="1987b-236">在此情況下，兩個命令會執行相同的交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="1987b-236">In this case, two commands are executed as part of the same transaction.</span></span>

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a><span data-ttu-id="1987b-237">刪除資料</span><span class="sxs-lookup"><span data-stu-id="1987b-237">Deleting data</span></span>
<span data-ttu-id="1987b-238">此步驟說明如何從資料表刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="1987b-238">This step shows you how to delete rows from a data table.</span></span>


#### <a name="to-delete-rows-from-the-database"></a><span data-ttu-id="1987b-239">若要從資料庫刪除資料列</span><span class="sxs-lookup"><span data-stu-id="1987b-239">To delete rows from the database</span></span>

<span data-ttu-id="1987b-240">現在，清除任何加入的資料列所撰寫的函式會從指定之資料表的執行個體中刪除資料列`System.Data.Linq.Table`類別。</span><span class="sxs-lookup"><span data-stu-id="1987b-240">Now, clean up any added rows by writing a function that deletes rows from a specified table, an instance of the `System.Data.Linq.Table` class.</span></span> <span data-ttu-id="1987b-241">撰寫查詢來尋找您想要刪除的所有資料列，然後將查詢的結果管線傳送`deleteRows`函式。</span><span class="sxs-lookup"><span data-stu-id="1987b-241">Then write a query to find all the rows that you want to delete, and pipe the results of the query into the `deleteRows` function.</span></span> <span data-ttu-id="1987b-242">此程式碼會利用提供的函式引數的部分應用程式的能力。</span><span class="sxs-lookup"><span data-stu-id="1987b-242">This code takes advantage of the ability to provide partial application of function arguments.</span></span>

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a><span data-ttu-id="1987b-243">建立測試資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-243">Creating a test database</span></span>
<span data-ttu-id="1987b-244">本節說明如何使用此逐步解說中設定測試資料庫。</span><span class="sxs-lookup"><span data-stu-id="1987b-244">This section shows you how to set up the test database to use in this walkthrough.</span></span>

<span data-ttu-id="1987b-245">請注意，是否您改變資料庫，在某些方面，您必須重設型別提供者。</span><span class="sxs-lookup"><span data-stu-id="1987b-245">Note that if you alter the database in some way, you will have to reset the type provider.</span></span> <span data-ttu-id="1987b-246">若要重設型別提供者，重建或清除包含型別提供者的專案。</span><span class="sxs-lookup"><span data-stu-id="1987b-246">To reset the type provider, rebuild or clean the project that contains the type provider.</span></span>


#### <a name="to-create-the-test-database"></a><span data-ttu-id="1987b-247">若要建立測試資料庫</span><span class="sxs-lookup"><span data-stu-id="1987b-247">To create the test database</span></span>

1. <span data-ttu-id="1987b-248">在**伺服器總管**，開啟捷徑功能表**資料連接**] 節點，然後選擇 [**加入連接**。</span><span class="sxs-lookup"><span data-stu-id="1987b-248">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and choose **Add Connection**.</span></span> <span data-ttu-id="1987b-249">**加入連接** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1987b-249">The **Add Connection** dialog box appears.</span></span>

2. <span data-ttu-id="1987b-250">在**伺服器名稱**方塊中，指定具有系統管理權限的 SQL Server 執行個體的名稱或您沒有存取伺服器，如果指定 (localdb\v11.0)。</span><span class="sxs-lookup"><span data-stu-id="1987b-250">In the **Server name** box, specify the name of an instance of SQL Server that you have administrative access to, or if you do not have access to a server, specify (localdb\v11.0).</span></span> <span data-ttu-id="1987b-251">SQL Express LocalDB 提供輕量型的資料庫伺服器供開發及測試您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1987b-251">SQL Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="1987b-252">在 建立新的節點**伺服器總管**下**資料連接**。</span><span class="sxs-lookup"><span data-stu-id="1987b-252">A new node is created in **Server Explorer** under **Data Connections**.</span></span> <span data-ttu-id="1987b-253">如需有關 LocalDB 的詳細資訊，請參閱[逐步解說： 在 Visual Studio 中建立本機資料庫檔案](https://msdn.microsoft.com/library/ms233763.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1987b-253">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>

3. <span data-ttu-id="1987b-254">開啟新連接節點的捷徑功能表，然後選取**新查詢**。</span><span class="sxs-lookup"><span data-stu-id="1987b-254">Open the shortcut menu for the new connection node, and select **New Query**.</span></span>

4. <span data-ttu-id="1987b-255">複製下列 SQL 指令碼，將它貼到查詢編輯器，然後選擇**Execute**工具列按鈕，或選擇 Ctrl + Shift + E 鍵。</span><span class="sxs-lookup"><span data-stu-id="1987b-255">Copy the following SQL script, paste it into the query editor, and then choose the **Execute** button on the toolbar or choose the Ctrl+Shift+E keys.</span></span>

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a><span data-ttu-id="1987b-256">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1987b-256">See Also</span></span>
[<span data-ttu-id="1987b-257">類型提供者</span><span class="sxs-lookup"><span data-stu-id="1987b-257">Type Providers</span></span>](index.md)

[<span data-ttu-id="1987b-258">SqlDataConnection 類型提供者</span><span class="sxs-lookup"><span data-stu-id="1987b-258">SqlDataConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="1987b-259">逐步解說： 從 DBML 檔案產生 F # 類型</span><span class="sxs-lookup"><span data-stu-id="1987b-259">Walkthrough: Generating F# Types from a DBML File</span></span>](generating-fsharp-types-from-dbml.md)

[<span data-ttu-id="1987b-260">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="1987b-260">Query Expressions</span></span>](../../language-reference/query-expressions.md)

[<span data-ttu-id="1987b-261">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1987b-261">LINQ to SQL</span></span>](../../../../docs/framework/data/adonet/sql/linq/index.md)

[<span data-ttu-id="1987b-262">SqlMetal.exe &#40;程式碼產生工具 &#41;</span><span class="sxs-lookup"><span data-stu-id="1987b-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)
