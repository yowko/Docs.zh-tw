---
title: 逐步解說：從 DBML 檔案產生 F# 類型 (F#)
description: '了解如何從 F # 3.0 中的資料庫建立 F # 類型的資料，當您有編碼.dbml 檔案中的結構描述資訊。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 3cd8df9becac0d1a8842eb22e2f772eee6307acf
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a><span data-ttu-id="86285-104">逐步解說：從 DBML 檔案產生 F# 類型</span><span class="sxs-lookup"><span data-stu-id="86285-104">Walkthrough: Generating F# Types from a DBML File</span></span>

> [!NOTE]
<span data-ttu-id="86285-105">本指南針對 F # 3.0 所撰寫，而且會更新。</span><span class="sxs-lookup"><span data-stu-id="86285-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="86285-106">請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。</span><span class="sxs-lookup"><span data-stu-id="86285-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="86285-107">應用程式開發介面參考連結將帶您到 MSDN。</span><span class="sxs-lookup"><span data-stu-id="86285-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="86285-108">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="86285-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="86285-109">這個 F # 3.0 的逐步解說描述如何從資料庫建立的資料類型，當您編碼.dbml 檔案中的結構描述資訊時。</span><span class="sxs-lookup"><span data-stu-id="86285-109">This walkthrough for F# 3.0 describes how to create types for data from a database when you have schema information encoded in a .dbml file.</span></span> <span data-ttu-id="86285-110">LINQ to SQL 會使用這種檔案格式來表示資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="86285-110">LINQ to SQL uses this file format to represent database schema.</span></span> <span data-ttu-id="86285-111">您可以使用物件關聯式 (O/R) 的設計工具，Visual Studio 中產生 LINQ to SQL 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="86285-111">You can generate a LINQ to SQL schema file in Visual Studio by using the Object Relational (O/R) Designer.</span></span> <span data-ttu-id="86285-112">如需詳細資訊，請參閱[O/R 設計工具概觀](https://msdn.microsoft.com/library/bb384511.aspx)和[LINQ to SQL 中的程式碼產生](../../../../docs/framework/data/adonet/sql/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="86285-112">For more information, see [O/R Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) and [Code Generation in LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>

<span data-ttu-id="86285-113">資料庫標記語言 」 (DBML) 型別提供者可讓您撰寫程式碼，會使用基礎資料庫結構描述，而不需要您在編譯時期指定靜態連接字串的類型。</span><span class="sxs-lookup"><span data-stu-id="86285-113">The Database Markup Language (DBML) type provider allows you to write code that uses types based on a database schema without requiring you to specify a static connection string at compile time.</span></span> <span data-ttu-id="86285-114">可以是如果您需要完成的應用程式將使用不同的資料庫，不同的認證或不同的連接字串比您用來開發應用程式可能很有用。</span><span class="sxs-lookup"><span data-stu-id="86285-114">That can be useful if you need to allow for the possibility that the final application will use a different database, different credentials, or a different connection string than the one you use to develop the application.</span></span> <span data-ttu-id="86285-115">如果您有直接的資料庫連接，您可以在編譯時期使用，而且這是相同的資料庫和最終建置應用程式中使用的認證，您也可以使用 SQLDataConnection 類型提供者。</span><span class="sxs-lookup"><span data-stu-id="86285-115">If you have a direct database connection that you can use at compile time and this is the same database and credentials that you will eventually use in your built application, you can also use the SQLDataConnection type provider.</span></span> <span data-ttu-id="86285-116">如需詳細資訊，請參閱[逐步解說： 存取 SQL 資料庫所使用的型別提供者](accessing-a-sql-database.md)。</span><span class="sxs-lookup"><span data-stu-id="86285-116">For more information, see [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>

<span data-ttu-id="86285-117">這個逐步解說將說明下列工作。</span><span class="sxs-lookup"><span data-stu-id="86285-117">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="86285-118">它們應該依此順序逐步解說中，才能成功完成：</span><span class="sxs-lookup"><span data-stu-id="86285-118">They should be completed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="86285-119">建立.dbml 檔案</span><span class="sxs-lookup"><span data-stu-id="86285-119">Creating a .dbml file</span></span>
<br />

- <span data-ttu-id="86285-120">建立並設定 F # 專案</span><span class="sxs-lookup"><span data-stu-id="86285-120">Creating and setting up an F# project</span></span>
<br />

- <span data-ttu-id="86285-121">設定類型提供者和產生的型別</span><span class="sxs-lookup"><span data-stu-id="86285-121">Configuring the type provider and generating the types</span></span>
<br />

- <span data-ttu-id="86285-122">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="86285-122">Querying the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="86285-123">必要條件</span><span class="sxs-lookup"><span data-stu-id="86285-123">Prerequisites</span></span>

## <a name="creating-a-dbml-file"></a><span data-ttu-id="86285-124">建立.dbml 檔案</span><span class="sxs-lookup"><span data-stu-id="86285-124">Creating a .dbml file</span></span>
<span data-ttu-id="86285-125">如果您沒有上測試資料庫，建立一個在底部的指示[逐步解說： 存取 SQL 資料庫所使用的型別提供者](accessing-a-sql-database.md)。</span><span class="sxs-lookup"><span data-stu-id="86285-125">If you do not have a database to test on, create one by following the instructions at the bottom of [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span> <span data-ttu-id="86285-126">如果您遵循這些指示時，您將建立名為 MyDatabase 包含幾個簡單的資料表和預存程序，在您的 SQL Server 上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="86285-126">If you follow these instructions, you will create a database called MyDatabase that contains a few simple tables and stored procedures on your SQL Server.</span></span>

<span data-ttu-id="86285-127">如果您已經有.dbml 檔，您可以跳至區段中，**建立並設定 F # 專案**。</span><span class="sxs-lookup"><span data-stu-id="86285-127">If you already have a .dbml file, you can skip to the section, **Create and Set Up an F# Project**.</span></span> <span data-ttu-id="86285-128">否則，您可以建立指定現有的 SQL database 的.dbml 檔案，並使用命令列工具 SqlMetal.exe。</span><span class="sxs-lookup"><span data-stu-id="86285-128">Otherwise, you can create a .dbml file given an existing SQL database and by using the command-line tool SqlMetal.exe.</span></span>


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a><span data-ttu-id="86285-129">若要建立使用 SqlMetal.exe.dbml 檔案</span><span class="sxs-lookup"><span data-stu-id="86285-129">To create a .dbml file by using SqlMetal.exe</span></span>

1. <span data-ttu-id="86285-130">開啟**開發人員命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="86285-130">Open a **Developer Command Prompt**.</span></span>
<br />

2. <span data-ttu-id="86285-131">請確定您輸入有存取權 SqlMetal.exe`SqlMetal.exe /?`在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="86285-131">Ensure that you have access to SqlMetal.exe by entering `SqlMetal.exe /?` at the command prompt.</span></span> <span data-ttu-id="86285-132">SqlMetal.exe 通常安裝在**Microsoft Sdk**資料夾中的**Program Files**或**Program Files (x86)**。</span><span class="sxs-lookup"><span data-stu-id="86285-132">SqlMetal.exe is typically installed under the **Microsoft SDKs** folder in **Program Files** or **Program Files (x86)**.</span></span>
<br />

3. <span data-ttu-id="86285-133">SqlMetal.exe 執行下列命令列選項。</span><span class="sxs-lookup"><span data-stu-id="86285-133">Run SqlMetal.exe with the following command-line options.</span></span> <span data-ttu-id="86285-134">取代的適當路徑來取代`c:\destpath`若要建立.dbml 檔案，並插入適當的值為資料庫伺服器，執行個體名稱和資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="86285-134">Substitute an appropriate path in place of `c:\destpath` to create the .dbml file, and insert appropriate values for the database server, instance name, and database name.</span></span>
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
<span data-ttu-id="86285-135">如果 SqlMetal.exe 無法建立檔案，因為權限問題，請將目前目錄變更到您具有寫入權限的資料夾。</span><span class="sxs-lookup"><span data-stu-id="86285-135">If SqlMetal.exe has trouble creating the file due to permissions issues, change the current directory to a folder that you have write access to.</span></span>


4. <span data-ttu-id="86285-136">您也可以查看其他可用的命令列選項。</span><span class="sxs-lookup"><span data-stu-id="86285-136">You can also look at the other available command-line options.</span></span> <span data-ttu-id="86285-137">比方說，是如果您想要檢視和 SQL 函式包含在產生的型別，您可以使用的選項。</span><span class="sxs-lookup"><span data-stu-id="86285-137">For example, there are options you can use if you want views and SQL functions included in the generated types.</span></span> <span data-ttu-id="86285-138">如需詳細資訊，請參閱[SqlMetal.exe&#40;程式碼產生工具&#41;](https://msdn.microsoft.com/library/bb386987)。</span><span class="sxs-lookup"><span data-stu-id="86285-138">For more information, see [SqlMetal.exe &#40;Code Generation Tool&#41;](https://msdn.microsoft.com/library/bb386987).</span></span>
<br />


## <a name="creating-and-setting-up-an-f-project"></a><span data-ttu-id="86285-139">建立並設定 F # 專案</span><span class="sxs-lookup"><span data-stu-id="86285-139">Creating and setting up an F# project</span></span>
<span data-ttu-id="86285-140">在此步驟中，您會建立專案，並加入適當的參考，以使用 DBML 型別提供者。</span><span class="sxs-lookup"><span data-stu-id="86285-140">In this step, you create a project and add appropriate references to use the DBML type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="86285-141">若要建立並設定 F# 專案</span><span class="sxs-lookup"><span data-stu-id="86285-141">To create and set up an F# project</span></span>

1. <span data-ttu-id="86285-142">將新的 F # 主控台應用程式專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="86285-142">Add a new F# Console Application project to your solution.</span></span>
<br />

2. <span data-ttu-id="86285-143">在**方案總管] 中**，開啟捷徑功能表**參考**，然後選擇 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="86285-143">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="86285-144">在**組件**區域中，選擇**Framework** ] 節點，然後在可用組件清單中，選擇 [ **System.Data**和**System.Data.Linq**組件。</span><span class="sxs-lookup"><span data-stu-id="86285-144">In the **Assemblies** area, choose the **Framework** node, and then, in the list of available assemblies, choose the **System.Data** and **System.Data.Linq** assemblies.</span></span>
<br />

4. <span data-ttu-id="86285-145">在**組件**區域中，選擇**延伸**，然後在可用組件清單中，選擇  **FSharp.Data.TypeProviders**。</span><span class="sxs-lookup"><span data-stu-id="86285-145">In the **Assemblies** area, choose **Extensions**, and then, in the list of available assemblies, choose **FSharp.Data.TypeProviders**.</span></span>
<br />

5. <span data-ttu-id="86285-146">選擇**確定**按鈕，將這些組件的參考加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="86285-146">Choose the **OK** button to add references to these assemblies to your project.</span></span>
<br />

6. <span data-ttu-id="86285-147">(選擇性)</span><span class="sxs-lookup"><span data-stu-id="86285-147">(Optional).</span></span> <span data-ttu-id="86285-148">將您在上一個步驟中建立的.dbml 檔案複製和貼上的主要專案資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="86285-148">Copy the .dbml file that you created in the previous step, and paste the file in the main folder for your project.</span></span> <span data-ttu-id="86285-149">此資料夾包含專案檔 (.fsproj) 和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="86285-149">This folder contains the project file (.fsproj) and code files.</span></span> <span data-ttu-id="86285-150">在功能表列上選擇 **專案**，**加入現有項目**，然後指定.dbml 檔案，將它加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="86285-150">On the menu bar, choose **Project**, **Add Existing Item**, and then specify the .dbml file to add it to your project.</span></span> <span data-ttu-id="86285-151">如果您完成這些步驟，您可以省略 ResolutionFolder 靜態參數，在下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="86285-151">If you complete these steps, you can omit the ResolutionFolder static parameter in the next step.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="86285-152">設定型別提供者</span><span class="sxs-lookup"><span data-stu-id="86285-152">Configuring the type provider</span></span>
<span data-ttu-id="86285-153">在本節中，您會建立型別提供者，並從.dbml 檔案中所述的結構描述產生類型。</span><span class="sxs-lookup"><span data-stu-id="86285-153">In this section, you create a type provider and generate types from the schema that’s described in the .dbml file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a><span data-ttu-id="86285-154">若要設定型別提供者和產生類型</span><span class="sxs-lookup"><span data-stu-id="86285-154">To configure the type provider and generate the types</span></span>

- <span data-ttu-id="86285-155">將開啟的程式碼加入**TypeProviders**命名空間和您想要使用的.dbml 檔案的類型提供者具現化。</span><span class="sxs-lookup"><span data-stu-id="86285-155">Add code that opens the **TypeProviders** namespace and instantiates the type provider for the .dbml file that you want to use.</span></span> <span data-ttu-id="86285-156">如果您將.dbml 檔案加入您的專案時，您可以省略 ResolutionFolder 靜態參數。</span><span class="sxs-lookup"><span data-stu-id="86285-156">If you added the .dbml file to your project, you can omit the ResolutionFolder static parameter.</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

<span data-ttu-id="86285-157">提供存取所有產生的型別 DataContext 類型，並且會繼承自`System.Data.Linq.DataContext`。</span><span class="sxs-lookup"><span data-stu-id="86285-157">The DataContext type provides access to all the generated types and inherits from `System.Data.Linq.DataContext`.</span></span> <span data-ttu-id="86285-158">DbmlFile 類型提供者有各種可以設定的靜態參數。</span><span class="sxs-lookup"><span data-stu-id="86285-158">The DbmlFile type provider has various static parameters that you can set.</span></span> <span data-ttu-id="86285-159">例如，您可以使用 DataContext 類型不同的名稱，藉由指定`DataContext=MyDataContext`。</span><span class="sxs-lookup"><span data-stu-id="86285-159">For example, you can use a different name for the DataContext type by specifying `DataContext=MyDataContext`.</span></span> <span data-ttu-id="86285-160">在此情況下，您的程式碼類似下列的範例：</span><span class="sxs-lookup"><span data-stu-id="86285-160">In that case, your code resembles the following example:</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a><span data-ttu-id="86285-161">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="86285-161">Querying the database</span></span>
<span data-ttu-id="86285-162">在本節中，您可以使用 F # 查詢運算式查詢資料庫。</span><span class="sxs-lookup"><span data-stu-id="86285-162">In this section, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="86285-163">若要查詢資料</span><span class="sxs-lookup"><span data-stu-id="86285-163">To query the data</span></span>

- <span data-ttu-id="86285-164">加入程式碼來查詢資料庫。</span><span class="sxs-lookup"><span data-stu-id="86285-164">Add code to query the database.</span></span>
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a><span data-ttu-id="86285-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="86285-165">Next Steps</span></span>
<span data-ttu-id="86285-166">您可以繼續使用其他查詢的運算式，或從資料內容取得資料庫連接和執行一般 ADO.NET 資料的作業。</span><span class="sxs-lookup"><span data-stu-id="86285-166">You can proceed to use other query expressions, or get a database connection from the data context and perform normal ADO.NET data operations.</span></span> <span data-ttu-id="86285-167">如需其他步驟，請參閱章節 「 查詢資料 」 之後[逐步解說： 存取 SQL 資料庫所使用的型別提供者](accessing-a-sql-database.md)。</span><span class="sxs-lookup"><span data-stu-id="86285-167">For additional steps, see the sections after "Query the Data" in [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="86285-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86285-168">See Also</span></span>
[<span data-ttu-id="86285-169">DbmlFile 類型提供者</span><span class="sxs-lookup"><span data-stu-id="86285-169">DbmlFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="86285-170">類型提供者</span><span class="sxs-lookup"><span data-stu-id="86285-170">Type Providers</span></span>](index.md)

[<span data-ttu-id="86285-171">逐步解說：使用型別提供者存取 SQL 資料庫</span><span class="sxs-lookup"><span data-stu-id="86285-171">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>](accessing-a-sql-database.md)

[<span data-ttu-id="86285-172">SqlMetal.exe&#40;程式碼產生工具&#41;</span><span class="sxs-lookup"><span data-stu-id="86285-172">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)

[<span data-ttu-id="86285-173">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="86285-173">Query Expressions</span></span>](../../language-reference/query-expressions.md)
