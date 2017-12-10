---
title: "逐步解說：從 EDMX 結構描述檔案產生 F# 類型 (F#)"
description: "了解如何建立 F # 類型的資料表示的實體資料模型 (EDM) 在 F # 3.0 中，於.edmx 檔中指定結構描述的位置。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 1df0344e8dab2b40d82d1b9c61ccd2f026906243
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a><span data-ttu-id="60eff-104">逐步解說：從 EDMX 結構描述檔案產生 F# 類型</span><span class="sxs-lookup"><span data-stu-id="60eff-104">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>

> [!NOTE]
<span data-ttu-id="60eff-105">本指南針對 F # 3.0 所撰寫，而且會更新。</span><span class="sxs-lookup"><span data-stu-id="60eff-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="60eff-106">請參閱 [FSharp.Data](http://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。</span><span class="sxs-lookup"><span data-stu-id="60eff-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="60eff-107">應用程式開發介面參考連結將帶您到 MSDN。</span><span class="sxs-lookup"><span data-stu-id="60eff-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="60eff-108">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="60eff-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="60eff-109">這個 F# 3.0 的逐步解說將說明如何針對實體資料模型 (EDM) 這種在 .edmx 檔案中指定的結構描述所表示的資料建立類型。</span><span class="sxs-lookup"><span data-stu-id="60eff-109">This walkthrough for F# 3.0 shows you how to create types for data that is represented by the Entity Data Model (EDM), the schema for which is specified in an .edmx file.</span></span> <span data-ttu-id="60eff-110">這個逐步解說也將示範如何使用 EdmxFile 類型提供者。</span><span class="sxs-lookup"><span data-stu-id="60eff-110">This walkthrough also shows how to use the EdmxFile type provider.</span></span> <span data-ttu-id="60eff-111">在您開始之前，請考慮 SqlEntityConnection 類型提供者是否為更適當的類型提供者選項。</span><span class="sxs-lookup"><span data-stu-id="60eff-111">Before you begin, consider whether a SqlEntityConnection type provider is a more appropriate type provider option.</span></span> <span data-ttu-id="60eff-112">如果您擁有可在專案開發階段連接的線上資料庫，並且不介意在編譯時期指定連接字串，則 SqlEntityConnection 類型提供者會是最適合的選擇。</span><span class="sxs-lookup"><span data-stu-id="60eff-112">The SqlEntityConnection type provider works best for scenarios where you have a live database that you can connect to during the development phase of your project, and you do not mind specifying the connection string at compile time.</span></span> <span data-ttu-id="60eff-113">不過，這種類型提供者也存在限制，它不像 EdmxFile 類型提供者一樣提供許多資料庫功能。</span><span class="sxs-lookup"><span data-stu-id="60eff-113">However, this type provider is also limited in that it doesn't expose as much database functionality as the EdmxFile type provider.</span></span> <span data-ttu-id="60eff-114">此外，如果您沒有線上資料庫可供使用實體資料模型的資料庫專案使用，您可以使用 .edmx 檔案對資料庫進行編碼。</span><span class="sxs-lookup"><span data-stu-id="60eff-114">Also, if you don't have a live database connection for a database project that uses the Entity Data Model, you can use the .edmx file to code against the database.</span></span> <span data-ttu-id="60eff-115">當您使用 EdmxFile 類型提供者時，F# 編譯器會執行 EdmGen.exe 產生它所提供的類型。</span><span class="sxs-lookup"><span data-stu-id="60eff-115">When you use the EdmxFile type provider, the F# compiler runs EdmGen.exe to generate the types that it provides.</span></span>

<span data-ttu-id="60eff-116">這個逐步解說將說明下列工作，您必須按照這個逐步解說的順序執行才會成功：</span><span class="sxs-lookup"><span data-stu-id="60eff-116">This walkthrough illustrates the following tasks, which you must perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="60eff-117">建立 EDMX 檔案</span><span class="sxs-lookup"><span data-stu-id="60eff-117">Creating an EDMX file</span></span>
<br />

- <span data-ttu-id="60eff-118">建立專案</span><span class="sxs-lookup"><span data-stu-id="60eff-118">Creating the project</span></span>
<br />

- <span data-ttu-id="60eff-119">尋找或建立實體資料模型連接字串</span><span class="sxs-lookup"><span data-stu-id="60eff-119">Finding or creating the entity data model connection string</span></span>
<br />

- <span data-ttu-id="60eff-120">設定型別提供者</span><span class="sxs-lookup"><span data-stu-id="60eff-120">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="60eff-121">查詢資料</span><span class="sxs-lookup"><span data-stu-id="60eff-121">Querying the data</span></span>
<br />

- <span data-ttu-id="60eff-122">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="60eff-122">Calling a stored procedure</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="60eff-123">必要條件</span><span class="sxs-lookup"><span data-stu-id="60eff-123">Prerequisites</span></span>

## <a name="creating-an-edmx-file"></a><span data-ttu-id="60eff-124">建立 EDMX 檔案</span><span class="sxs-lookup"><span data-stu-id="60eff-124">Creating an EDMX file</span></span>
<span data-ttu-id="60eff-125">如果您已經有 EDMX 檔案，就可以略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="60eff-125">If you already have an EDMX file, you can skip this step.</span></span>


#### <a name="to-create-an-edmx-file"></a><span data-ttu-id="60eff-126">若要建立 EDMX 檔</span><span class="sxs-lookup"><span data-stu-id="60eff-126">To create an EDMX file</span></span>

- <span data-ttu-id="60eff-127">如果您還沒有 EDMX 檔案，您可以依照本逐步解說步驟中的結尾指示[設定實體資料模型](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model)。</span><span class="sxs-lookup"><span data-stu-id="60eff-127">If you don't already have an EDMX file, you can follow the instructions at the end of this walkthrough in the step [Configuring the Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span></span>
<br />

## <a name="creating-the-project"></a><span data-ttu-id="60eff-128">建立專案</span><span class="sxs-lookup"><span data-stu-id="60eff-128">Creating the project</span></span>
<span data-ttu-id="60eff-129">在這個步驟中，您會建立專案並且在其中加入適當的參考，以便使用 EDMX 類型提供者。</span><span class="sxs-lookup"><span data-stu-id="60eff-129">In this step, you create a project and add appropriate references to it to use the EDMX type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="60eff-130">若要建立並設定 F# 專案</span><span class="sxs-lookup"><span data-stu-id="60eff-130">To create and set up an F# project</span></span>

1. <span data-ttu-id="60eff-131">關閉先前的專案，建立另一個專案，並將它命名為 SchoolEDM。</span><span class="sxs-lookup"><span data-stu-id="60eff-131">Close the previous project, create another project, and name it SchoolEDM.</span></span>
<br />

2. <span data-ttu-id="60eff-132">在**方案總管] 中**，開啟捷徑功能表**參考**，然後選擇 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="60eff-132">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="60eff-133">在**組件**區域中，選擇**Framework**節點。</span><span class="sxs-lookup"><span data-stu-id="60eff-133">In the **Assemblies** area, choose the **Framework** node.</span></span>
<br />

4. <span data-ttu-id="60eff-134">在可用組件清單中，選擇  **System.Data.Entity**和**System.Data.Linq**組件，然後選擇 **新增**將參考加入至這些按鈕您的專案的組件。</span><span class="sxs-lookup"><span data-stu-id="60eff-134">In the list of available assemblies, choose the **System.Data.Entity** and **System.Data.Linq** assemblies, and then choose the **Add** button to add references to these assemblies to your project.</span></span>
<br />

5. <span data-ttu-id="60eff-135">在**組件**區域中，選取**延伸**節點。</span><span class="sxs-lookup"><span data-stu-id="60eff-135">In the **Assemblies** area, select the **Extensions** node.</span></span>
<br />

6. <span data-ttu-id="60eff-136">在可用的擴充功能清單中，加入 FSharp.Data.TypeProviders 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="60eff-136">In the  list of available extensions, add a reference to the FSharp.Data.TypeProviders assembly.</span></span>
<br />

7. <span data-ttu-id="60eff-137">加入下列程式碼，開啟適當的命名空間。</span><span class="sxs-lookup"><span data-stu-id="60eff-137">Add the following code to open the appropriate namespaces.</span></span>
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="60eff-138">尋找或建立實體資料模型的連接字串</span><span class="sxs-lookup"><span data-stu-id="60eff-138">Finding or creating the connection string for the Entity Data Model</span></span>
<span data-ttu-id="60eff-139">實體資料模型的連接字串 (EDMX 連接字串) 不只包括資料庫提供者的連接字串，還包含其他資訊。</span><span class="sxs-lookup"><span data-stu-id="60eff-139">The connection string for the Entity Data Model (EDMX connection string) includes not only the connection string for the database provider but also additional information.</span></span> <span data-ttu-id="60eff-140">例如，簡單的 SQL Server 資料庫的 EDMX 連接字串類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="60eff-140">For example, EDMX connection string for a simple SQL Server database resembles the following code.</span></span>

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

<span data-ttu-id="60eff-141">如需 EDMX 連接字串的詳細資訊，請參閱[連接字串](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="60eff-141">For more information about EDMX connection strings, see [Connection Strings](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="60eff-142">若要尋找或建立實體資料模型的連接字串</span><span class="sxs-lookup"><span data-stu-id="60eff-142">To find or create the connection string for the Entity Data Model</span></span>

1. <span data-ttu-id="60eff-143">EDMX 連接字串可能不容易手動產生，因此用程式設計方式產生可以為您節省時間。</span><span class="sxs-lookup"><span data-stu-id="60eff-143">EDMX connection strings can be difficult to generate by hand, so you can save time by generating it programmatically.</span></span> <span data-ttu-id="60eff-144">如果您知道 EDMX 連接字串，就可以略過這個步驟，直接在下一個步驟中使用該字串即可。</span><span class="sxs-lookup"><span data-stu-id="60eff-144">If you know your EDMX connection string, you can bypass this step and simply use that string in the next step.</span></span> <span data-ttu-id="60eff-145">否則，請使用下列程式碼從您所提供的資料庫連接字串中產生 EDMX 連接字串。</span><span class="sxs-lookup"><span data-stu-id="60eff-145">If not, use the following code to generate the EDMX connection string from a database connection string that you provide.</span></span>
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a><span data-ttu-id="60eff-146">設定類型提供者</span><span class="sxs-lookup"><span data-stu-id="60eff-146">Configuring the type provider</span></span>
<span data-ttu-id="60eff-147">在這個步驟中，您將建立並設定包含 EDMX 連接字串的類型提供者，然後為 .edmx 檔案中定義的結構描述產生類型。</span><span class="sxs-lookup"><span data-stu-id="60eff-147">In this step, you create and configure the type provider with the EDMX connection string, and you generate types for the schema that's defined in the .edmx file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="60eff-148">若要設定類型提供者和產生類型</span><span class="sxs-lookup"><span data-stu-id="60eff-148">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="60eff-149">將您在這個逐步解說的第一個步驟中產生的 .edmx 檔案複製到專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="60eff-149">Copy the .edmx file that you generated in the first step of this walkthrough to your project folder.</span></span>
<br />

2. <span data-ttu-id="60eff-150">開啟專案節點，在 F # 專案的捷徑功能表選擇 **加入現有項目**，然後選擇.edmx 檔案，將它加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="60eff-150">Open the shortcut menu for the project node in your F# project, choose **Add Existing Item**, and then choose the .edmx file to add it to your project.</span></span>
<br />

3. <span data-ttu-id="60eff-151">輸入下列程式碼來啟用 .edmx 檔案的型別提供者。</span><span class="sxs-lookup"><span data-stu-id="60eff-151">Enter the following code to activate the type provider for your .edmx file.</span></span> <span data-ttu-id="60eff-152">取代*伺服器*\** 執行個體正在執行的 SQL Server 和您的執行個體的名稱用於此逐步解說的第一個步驟中在.edmx 檔案的名稱伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="60eff-152">Replace *Server*\*Instance* with the name of your server that's running SQL Server and the name of your instance, and use the name of your .edmx file from the first step in this walkthrough.</span></span>
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a><span data-ttu-id="60eff-153">查詢資料</span><span class="sxs-lookup"><span data-stu-id="60eff-153">Querying the data</span></span>
<span data-ttu-id="60eff-154">在這個步驟中，您會使用 F# 查詢運算式查詢資料庫。</span><span class="sxs-lookup"><span data-stu-id="60eff-154">In this step, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="60eff-155">若要查詢資料</span><span class="sxs-lookup"><span data-stu-id="60eff-155">To query the data</span></span>

- <span data-ttu-id="60eff-156">輸入下列程式碼可查詢實體資料模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="60eff-156">Enter the following code to query the data in the entity data model.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="60eff-157">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="60eff-157">Calling a stored procedure</span></span>
<span data-ttu-id="60eff-158">您可以使用 EDMX 型別提供者呼叫預存程序。</span><span class="sxs-lookup"><span data-stu-id="60eff-158">You can call stored procedures by using the EDMX type provider.</span></span> <span data-ttu-id="60eff-159">在下列程序中，School 資料庫包含預存程序， **UpdatePerson**，這會更新記錄時，指定新資料行值。</span><span class="sxs-lookup"><span data-stu-id="60eff-159">In the following procedure, the School database contains a stored procedure, **UpdatePerson**, which updates a record, given new values for the columns.</span></span> <span data-ttu-id="60eff-160">您可以使用這個預存程序，因為它會做為 DataContext 類型中的方法公開。</span><span class="sxs-lookup"><span data-stu-id="60eff-160">You can use this stored procedure because it's exposed as a method on the DataContext type.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="60eff-161">若要呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="60eff-161">To call a stored procedure</span></span>

- <span data-ttu-id="60eff-162">加入下列程式碼以更新記錄。</span><span class="sxs-lookup"><span data-stu-id="60eff-162">Add the following code to update records.</span></span>
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

<span data-ttu-id="60eff-163">如果成功，則結果會是 1。</span><span class="sxs-lookup"><span data-stu-id="60eff-163">The result is 1 if you succeed.</span></span> <span data-ttu-id="60eff-164">請注意， **exactlyOne**以確保只有一個會傳回結果，否則擲回例外狀況是用於查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="60eff-164">Notice that **exactlyOne** is used in the query expression to ensure that only one result is returned; otherwise, an exception is thrown.</span></span> <span data-ttu-id="60eff-165">此外，若要更輕鬆地使用可為 null 的值，您可以使用簡單**可為 null**函式定義於這個程式碼來建立從一般值為 null 的值。</span><span class="sxs-lookup"><span data-stu-id="60eff-165">Also, to work with nullable values more easily, you can use the simple **nullable** function that's defined in this code to create a nullable value out of an ordinary value.</span></span>

<br />

## <a name="configuring-the-entity-data-model"></a><span data-ttu-id="60eff-166">設定實體資料模型</span><span class="sxs-lookup"><span data-stu-id="60eff-166">Configuring the Entity Data Model</span></span>
<span data-ttu-id="60eff-167">只有在您想要知道如何從資料庫產生完整的實體資料模型，但是沒有可用來測試的資料庫時，才完成這個程序。</span><span class="sxs-lookup"><span data-stu-id="60eff-167">You should complete this procedure only if you want to know how to generate a full Entity Data Model from a database and you don't have a database with which to test.</span></span>


#### <a name="to-configure-the-entity-data-model"></a><span data-ttu-id="60eff-168">若要設定實體資料模型</span><span class="sxs-lookup"><span data-stu-id="60eff-168">To configure the Entity Data Model</span></span>

1. <span data-ttu-id="60eff-169">在功能表列上選擇  **SQL**， **TRANSACT-SQL 編輯器**，**新查詢**建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="60eff-169">On the menu bar, choose **SQL**, **Transact-SQL Editor**, **New Query** to create a database.</span></span> <span data-ttu-id="60eff-170">出現提示時，指定您的資料庫伺服器和執行個體。</span><span class="sxs-lookup"><span data-stu-id="60eff-170">If prompted, specify your database server and instance.</span></span>
<br />

2. <span data-ttu-id="60eff-171">複製並貼上建立學生的資料庫，將資料庫指令碼的內容中所述[Entity Framework 文件](http://msdn.microsoft.com/data/JJ614587.aspx)資料開發人員中心。</span><span class="sxs-lookup"><span data-stu-id="60eff-171">Copy and paste the contents of the database script that creates the Student database, as described in the [Entity Framework documentation](http://msdn.microsoft.com/data/JJ614587.aspx) in the Data Developer Center.</span></span>
<br />

3. <span data-ttu-id="60eff-172">選擇三角形符號的工具列按鈕，或選擇 Ctrl + Q 鍵以執行 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="60eff-172">Run the SQL script by choosing the toolbar button with the triangle symbol or choosing the Ctrl+Q keys.</span></span>
<br />

4. <span data-ttu-id="60eff-173">在**伺服器總管**，開啟捷徑功能表**資料連接**，選擇**加入連接**，然後輸入資料庫伺服器的執行個體名稱的名稱及 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="60eff-173">In **Server Explorer**, open the shortcut menu for **Data Connections**, choose **Add Connection**, and then enter the name of the database server, the name of the instance name, and the School database.</span></span>
<br />

5. <span data-ttu-id="60eff-174">建立 C# 或 Visual Basic 主控台應用程式專案，開啟其捷徑功能表，選擇**加入新項目**，然後選擇  **ADO.NET 實體資料模型**。</span><span class="sxs-lookup"><span data-stu-id="60eff-174">Create a C# or Visual Basic Console Application project, open its shortcut menu, choose **Add New Item**, and then choose **ADO.NET Entity Data Model**.</span></span>
<br />  <span data-ttu-id="60eff-175">[實體資料模型精靈] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="60eff-175">The Entity Data Model Wizard opens.</span></span> <span data-ttu-id="60eff-176">您可以使用這個精靈選擇要如何建立實體資料模型。</span><span class="sxs-lookup"><span data-stu-id="60eff-176">By using this wizard, you can choose how you want to create the Entity Data Model.</span></span>
<br />

6. <span data-ttu-id="60eff-177">在下**選擇模型內容**，選取**從資料庫產生**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="60eff-177">Under **Choose Model Contents**, select the **Generate from database** check box.</span></span>
<br />

7. <span data-ttu-id="60eff-178">在下一頁中，選擇新建立的 School 資料庫做為資料連接。</span><span class="sxs-lookup"><span data-stu-id="60eff-178">On the next page, choose your newly created School database as the data connection.</span></span>
<br />  <span data-ttu-id="60eff-179">這個連接應該類似 **&lt;servername&gt;。&lt;instancename&gt;。School.dbo**。</span><span class="sxs-lookup"><span data-stu-id="60eff-179">This connection should resemble **&lt;servername&gt;.&lt;instancename&gt;.School.dbo**.</span></span>
<br />

8. <span data-ttu-id="60eff-180">將實體連接字串複製到 [剪貼簿]，因為該字串對後續程序可能很重要。</span><span class="sxs-lookup"><span data-stu-id="60eff-180">Copy your entity connection string to the Clipboard because that string might be important later.</span></span>
<br />

9. <span data-ttu-id="60eff-181">請確定核取方塊以將實體連接字串儲存**App.Config**檔案已選取，並在文字方塊中，可幫助您尋找該連接字串更新版本中，視記的字串值。</span><span class="sxs-lookup"><span data-stu-id="60eff-181">Make sure the check box to save the entity connection string to the **App.Config** file is selected, and make note of the string value in the text box, which should help you locate the connection string later, if needed.</span></span>
<br />

10. <span data-ttu-id="60eff-182">在下一個頁面上，選擇**資料表**和**預存程序和函式**。</span><span class="sxs-lookup"><span data-stu-id="60eff-182">On the next page, choose **Tables** and **Stored Procedures and Functions**.</span></span>
<br />  <span data-ttu-id="60eff-183">藉由選擇這些最上層節點，就可以選擇所有資料表、預存程序和函式。</span><span class="sxs-lookup"><span data-stu-id="60eff-183">By choosing these top-level nodes, you choose all tables, stored procedures, and functions.</span></span> <span data-ttu-id="60eff-184">如有需要，您也可以個別選擇這些項目。</span><span class="sxs-lookup"><span data-stu-id="60eff-184">You can also choose these individually, if you want.</span></span>
<br />

11. <span data-ttu-id="60eff-185">確定已選取其他設定的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="60eff-185">Make sure that the check boxes for the other settings are selected.</span></span>
<br />  <span data-ttu-id="60eff-186">第一個**將化或單數化產生的物件名稱**核取方塊，指出是否將單數形式變更為複數形式，以符合命名代表資料庫資料表物件的慣例。</span><span class="sxs-lookup"><span data-stu-id="60eff-186">The first **Pluralize or singularize generated object names** check box indicates whether to change singular forms to plural to match conventions in naming objects that represent database tables.</span></span> <span data-ttu-id="60eff-187">**在模型中包含外部索引鍵資料行**核取方塊決定是否要包含用途為聯結至其他欄位中的資料庫結構描述產生的物件類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="60eff-187">The **Include foreign key columns in the model** check box determines whether to include fields for which the purpose is to join to other fields in the object types that are generated for the database schema.</span></span> <span data-ttu-id="60eff-188">第三個核取方塊表示，是否在模型中包含預存程序和函式。</span><span class="sxs-lookup"><span data-stu-id="60eff-188">The third check box indicates whether to include stored procedures and functions in the model.</span></span>
<br />

12. <span data-ttu-id="60eff-189">選取**完成** 按鈕，產生的.edmx 檔案，包含實體資料模型為基礎的 School 資料庫。</span><span class="sxs-lookup"><span data-stu-id="60eff-189">Select the **Finish** button to generate an .edmx file that contains an Entity Data Model that's based on the School database.</span></span>
<br />  <span data-ttu-id="60eff-190">檔案、 **Model1.edmx**，加入至您的專案，而且資料庫圖表會出現。</span><span class="sxs-lookup"><span data-stu-id="60eff-190">A file, **Model1.edmx**, is added to your project, and a database diagram appears.</span></span>
<br />

13. <span data-ttu-id="60eff-191">在功能表列上選擇 **檢視**，**其他視窗**，**實體資料模型瀏覽器**檢視模型的所有詳細資料或**實體資料模型對應詳細資料**開啟一個視窗，顯示產生的物件模型如何對應資料庫資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="60eff-191">On the menu bar, choose **View**, **Other Windows**, **Entity Data Model Browser** to view all the details of the model or **Entity Data Model Mapping Details** to open a window that shows how the generated object model maps onto database tables and columns.</span></span>
<br />


## <a name="next-steps"></a><span data-ttu-id="60eff-192">後續步驟</span><span class="sxs-lookup"><span data-stu-id="60eff-192">Next Steps</span></span>
<span data-ttu-id="60eff-193">藉由查看可用的查詢運算子，如下所示瀏覽其他查詢[查詢運算式](../../language-reference/query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="60eff-193">Explore other queries by looking at the available query operators as listed in [Query Expressions](../../language-reference/query-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="60eff-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60eff-194">See Also</span></span>
[<span data-ttu-id="60eff-195">類型提供者</span><span class="sxs-lookup"><span data-stu-id="60eff-195">Type Providers</span></span>](index.md)

[<span data-ttu-id="60eff-196">EdmxFile 類型提供者</span><span class="sxs-lookup"><span data-stu-id="60eff-196">EdmxFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="60eff-197">逐步解說：使用型別提供者和實體存取 SQL 資料庫</span><span class="sxs-lookup"><span data-stu-id="60eff-197">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>](accessing-a-sql-database-entities.md)

[<span data-ttu-id="60eff-198">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="60eff-198">Entity Framework</span></span>](http://msdn.microsoft.com/data/ef)

[<span data-ttu-id="60eff-199">.edmx 檔案概觀</span><span class="sxs-lookup"><span data-stu-id="60eff-199">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="60eff-200">EDM 產生器 &#40;EdmGen.exe &#41;</span><span class="sxs-lookup"><span data-stu-id="60eff-200">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)

