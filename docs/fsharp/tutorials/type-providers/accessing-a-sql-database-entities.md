---
title: 逐步解說：使用型別提供者和實體存取 SQL 資料庫 (F#)
description: '了解如何存取 SQL 資料庫在 F # 3.0 ADO.NET 實體資料模型為基礎的型別的資料。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 153050f27ade0152741bdc2d77ab85eefa8418e9
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a><span data-ttu-id="746de-104">逐步解說：使用型別提供者和實體存取 SQL 資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-104">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>

> [!NOTE]
<span data-ttu-id="746de-105">本指南針對 F # 3.0 所撰寫，而且會更新。</span><span class="sxs-lookup"><span data-stu-id="746de-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="746de-106">請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。</span><span class="sxs-lookup"><span data-stu-id="746de-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="746de-107">應用程式開發介面參考連結將帶您到 MSDN。</span><span class="sxs-lookup"><span data-stu-id="746de-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="746de-108">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="746de-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="746de-109">這個 F# 3.0 的逐步解說將示範如何根據 ADO.NET 實體資料模型，存取 SQL 資料庫中具類型的資料。</span><span class="sxs-lookup"><span data-stu-id="746de-109">This walkthrough for F# 3.0 shows you how to access typed data for a SQL database based on the ADO.NET Entity Data Model.</span></span> <span data-ttu-id="746de-110">這個逐步解說將示範如何設定 `SqlEntityConnection` F# 類型提供者搭配 SQL 資料庫使用、如何撰寫對資料的查詢、如何在資料庫上呼叫預存程序，以及如何使用某些 ADO.NET Entity Framework 類型和方法更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="746de-110">This walkthrough shows you how to set up the F# `SqlEntityConnection` type provider for use with a SQL database, how to write queries against the data, how to call stored procedures on the database, as well as how to use some of the ADO.NET Entity Framework types and methods to update the database.</span></span>

<span data-ttu-id="746de-111">這個逐步解說將說明下列工作，您應該按照這個逐步解說的順序執行才能成功：</span><span class="sxs-lookup"><span data-stu-id="746de-111">This walkthrough illustrates the following tasks, which you should perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="746de-112">建立 School 資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-112">Create the School database</span></span>
<br />

- <span data-ttu-id="746de-113">建立並設定 F# 專案</span><span class="sxs-lookup"><span data-stu-id="746de-113">Create and configure an F# project</span></span>
<br />

- <span data-ttu-id="746de-114">設定類型提供者並連接至實體資料模型</span><span class="sxs-lookup"><span data-stu-id="746de-114">Configure the type provider and connect to the Entity Data Model</span></span>
<br />

- <span data-ttu-id="746de-115">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-115">Query the database</span></span>
<br />

- <span data-ttu-id="746de-116">更新資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-116">Updating the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="746de-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="746de-117">Prerequisites</span></span>
<span data-ttu-id="746de-118">您必須能夠存取執行 SQL Server 且可讓您建立資料庫的伺服器，才能完成這些步驟。</span><span class="sxs-lookup"><span data-stu-id="746de-118">You must have access to a server that's running SQL Server where you can create a database to complete these steps.</span></span>

## <a name="create-the-school-database"></a><span data-ttu-id="746de-119">建立 School 資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-119">Create the School database</span></span>
<span data-ttu-id="746de-120">您可以在任何您具有系統管理存取權限且執行 SQL Server 的伺服器上建立 School 資料庫，或者您也可以使用 LocalDB。</span><span class="sxs-lookup"><span data-stu-id="746de-120">You can create the School database on any server that's running SQL Server to which you have administrative access, or you can use LocalDB.</span></span>


#### <a name="to-create-the-school-database"></a><span data-ttu-id="746de-121">若要建立 School 資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-121">To create the School database</span></span>

1. <span data-ttu-id="746de-122">在**伺服器總管**，開啟捷徑功能表**資料連接**] 節點，然後選擇 [**加入連接**。</span><span class="sxs-lookup"><span data-stu-id="746de-122">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and then choose **Add Connection**.</span></span>
<br />  <span data-ttu-id="746de-123">**加入連接** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="746de-123">The **Add Connection** dialog box appears.</span></span>
<br />

2. <span data-ttu-id="746de-124">在**伺服器名稱**方塊中，指定您具有系統管理權限的 SQL Server 執行個體的名稱或指定 (localdb\v11.0)，如果您沒有伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="746de-124">In the **Server name** box, specify the name of an instance of SQL Server to which you have administrative access, or specify (localdb\v11.0) if you don't have access to a server.</span></span>
<br />  <span data-ttu-id="746de-125">SQL Server Express LocalDB 提供輕量型的資料庫伺服器，可讓您在電腦上進行開發和測試時使用。</span><span class="sxs-lookup"><span data-stu-id="746de-125">SQL Server Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="746de-126">如需有關 LocalDB 的詳細資訊，請參閱[逐步解說： 在 Visual Studio 中建立本機資料庫檔案](https://msdn.microsoft.com/library/ms233763.aspx)。</span><span class="sxs-lookup"><span data-stu-id="746de-126">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>
<br />  <span data-ttu-id="746de-127">在 建立新的節點**伺服器總管**下**資料連接**。</span><span class="sxs-lookup"><span data-stu-id="746de-127">A new node is created in **Server Explorer** under **Data Connections**.</span></span>
<br />

3. <span data-ttu-id="746de-128">開啟新連接節點的捷徑功能表，然後選擇**新查詢**。</span><span class="sxs-lookup"><span data-stu-id="746de-128">Open the shortcut menu for the new connection node, and then choose **New Query**.</span></span>
<br />

4. <span data-ttu-id="746de-129">開啟[建立 School 範例資料庫](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx)上 Microsoft 網站，然後複製並貼上將資料庫指令碼會建立 School 資料庫到編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="746de-129">Open [Creating the School Sample Database](https://msdn.microsoft.com/library/bb399731(v=vs.100).aspx) on the Microsoft website, and then copy and paste the database script that creates the School database into the editor window.</span></span>
<br />


## <span data-ttu-id="746de-130"><a name="BKMK_CreateConfigFSProj"> </a></span><span class="sxs-lookup"><span data-stu-id="746de-130"><a name="BKMK_CreateConfigFSProj"> </a></span></span>

## <a name="create-and-configure-an-f-project"></a><span data-ttu-id="746de-131">建立並設定 F# 專案</span><span class="sxs-lookup"><span data-stu-id="746de-131">Create and configure an F# project</span></span>
<span data-ttu-id="746de-132">在這個步驟中，您會建立專案並將進行設定，以便使用類型提供者。</span><span class="sxs-lookup"><span data-stu-id="746de-132">In this step, you create a project and set it up to use a type provider.</span></span>


#### <a name="to-create-and-configure-an-f-project"></a><span data-ttu-id="746de-133">若要建立和設定 F# 專案</span><span class="sxs-lookup"><span data-stu-id="746de-133">To create and configure an F# project</span></span>

1. <span data-ttu-id="746de-134">關閉先前的專案、 建立另一個專案，並將其命名**SchoolEDM**。</span><span class="sxs-lookup"><span data-stu-id="746de-134">Close the previous project, create another project, and name it **SchoolEDM**.</span></span>
<br />

2. <span data-ttu-id="746de-135">在**方案總管] 中**，開啟捷徑功能表**參考**，然後選擇 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="746de-135">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="746de-136">選擇**Framework**  節點，然後在**Framework**清單中，選擇**System.Data**， **System.Data.Entity**，和**System.Data.Linq**。</span><span class="sxs-lookup"><span data-stu-id="746de-136">Choose the **Framework** node, and then, in the **Framework** list, choose **System.Data**, **System.Data.Entity**,  and **System.Data.Linq**.</span></span>
<br />

4. <span data-ttu-id="746de-137">選擇**延伸**] 節點，將參考加入[FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3)組件，然後選擇 [ **[確定]**按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="746de-137">Choose the **Extensions** node, add a reference to the [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly, and then choose the **OK** button to dismiss the dialog box.</span></span>
<br />

5. <span data-ttu-id="746de-138">加入下列程式碼可定義內部模組並開啟適當的命名空間。</span><span class="sxs-lookup"><span data-stu-id="746de-138">Add the following code to define an internal module and open appropriate namespaces.</span></span> <span data-ttu-id="746de-139">型別提供者只能將類型插入私用或內部命名空間。</span><span class="sxs-lookup"><span data-stu-id="746de-139">The type provider can inject types only into a private or internal namespace.</span></span>
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. <span data-ttu-id="746de-140">在本逐步解說，以互動方式為當做編譯的程式而不是指令碼執行的程式碼，請開啟專案節點的捷徑功能表，選擇 **加入新項目**，加入 F # 指令碼檔，然後加入程式碼中每個步驟的指令碼。</span><span class="sxs-lookup"><span data-stu-id="746de-140">To run the code in this walkthrough interactively as a script instead of as a compiled program, open the shortcut menu for the project node, choose **Add New Item**, add an F# script file, and then add the code in each step to the script.</span></span> <span data-ttu-id="746de-141">若要載入組件參考，請加入下列各行。</span><span class="sxs-lookup"><span data-stu-id="746de-141">To load the assembly references, add the following lines.</span></span>
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. <span data-ttu-id="746de-142">在加入時反白顯示您加入的每一個程式碼區塊，然後選擇 Alt + Enter 鍵以 F# Interactive 執行。</span><span class="sxs-lookup"><span data-stu-id="746de-142">Highlight each block of code as you add it, and choose the Alt + Enter keys to run it in F# Interactive.</span></span>
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="746de-143">設定型別提供者並連接至實體資料模型</span><span class="sxs-lookup"><span data-stu-id="746de-143">Configure the type provider, and connect to the Entity Data Model</span></span>
<span data-ttu-id="746de-144">在這個步驟中，您將設定具有資料連接的型別提供者，並且取得可讓您使用資料的資料內容。</span><span class="sxs-lookup"><span data-stu-id="746de-144">In this step, you set up a type provider with a data connection and obtain a data context that allows you to work with data.</span></span>


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a><span data-ttu-id="746de-145">若要設定類型提供者並連接至實體資料模型</span><span class="sxs-lookup"><span data-stu-id="746de-145">To configure the type provider, and connect to the Entity Data Model</span></span>

1. <span data-ttu-id="746de-146">輸入下列程式碼，依據您先前所建立的實體資料模型設定產生 F# 類型的 `SqlEntityConnection` 類型提供者。</span><span class="sxs-lookup"><span data-stu-id="746de-146">Enter the following code to configure the `SqlEntityConnection` type provider that generates F# types based on the Entity Data Model that you created previously.</span></span> <span data-ttu-id="746de-147">僅使用 SQL 連接字串，而非完整的 EDMX 連接字串。</span><span class="sxs-lookup"><span data-stu-id="746de-147">Instead of the full EDMX connection string, use only the SQL connection string.</span></span>
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  <span data-ttu-id="746de-148">這個動作會設定具有您先前所建立資料庫連接的類型提供者。</span><span class="sxs-lookup"><span data-stu-id="746de-148">This action sets up a type provider with the database connection that you created earlier.</span></span> <span data-ttu-id="746de-149">當您使用 ADO.NET Entity Framework 時，會需要 `MultipleActiveResultSets` 屬性，因為這個屬性允許在單一連接中，於資料庫上以非同步方式執行多個命令，這種情況在 ADO.NET Entity Framework 程式碼中經常出現。</span><span class="sxs-lookup"><span data-stu-id="746de-149">The property `MultipleActiveResultSets` is needed when you use the ADO.NET Entity Framework because this property allows multiple commands to execute asynchronously on the database in one connection, which can occur frequently in ADO.NET Entity Framework code.</span></span> <span data-ttu-id="746de-150">如需詳細資訊，請參閱 [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars)。</span><span class="sxs-lookup"><span data-stu-id="746de-150">For more information, see [Multiple Active Result Sets (MARS)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).</span></span>
<br />

2. <span data-ttu-id="746de-151">取得資料內容，這個物件包含做為屬性的資料庫資料表，以及做為方法的資料庫預存程序和函式。</span><span class="sxs-lookup"><span data-stu-id="746de-151">Get the data context, which is an object that contains the database tables as properties and the database stored procedures and functions as methods.</span></span>
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a><span data-ttu-id="746de-152">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-152">Querying the database</span></span>
<span data-ttu-id="746de-153">在這個步驟中，您將使用 F# 查詢運算式在資料庫上執行各種查詢。</span><span class="sxs-lookup"><span data-stu-id="746de-153">In this step, you use F# query expressions to execute various queries on the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="746de-154">若要查詢資料</span><span class="sxs-lookup"><span data-stu-id="746de-154">To query the data</span></span>

- <span data-ttu-id="746de-155">輸入下列程式碼可查詢實體資料模型中的資料。</span><span class="sxs-lookup"><span data-stu-id="746de-155">Enter the following code to query the data from the entity data model.</span></span> <span data-ttu-id="746de-156">請注意 Pluralize = true 的效果，它會將資料庫資料表 Course 變更為 Courses 以及 Person 變更為 People。</span><span class="sxs-lookup"><span data-stu-id="746de-156">Note the effect of Pluralize = true, which changes the database table Course to Courses and Person to People.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a><span data-ttu-id="746de-157">更新資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-157">Updating the database</span></span>
<span data-ttu-id="746de-158">若要更新資料庫，您可以使用 Entity Framework 類別和方法。</span><span class="sxs-lookup"><span data-stu-id="746de-158">To update the database, you use the Entity Framework classes and methods.</span></span> <span data-ttu-id="746de-159">您可以使用兩種類型的資料內容搭配 SQLEntityConnection 類型提供者。</span><span class="sxs-lookup"><span data-stu-id="746de-159">You can use two types of data context with the SQLEntityConnection type provider.</span></span> <span data-ttu-id="746de-160">第一種是 `ServiceTypes.SimpleDataContextTypes.EntityContainer`，這是簡化的資料內容，只包含代表資料庫資料表和資料行的所提供屬性。</span><span class="sxs-lookup"><span data-stu-id="746de-160">First, `ServiceTypes.SimpleDataContextTypes.EntityContainer` is the simplified data context, which includes only the provided properties that represent database tables and columns.</span></span> <span data-ttu-id="746de-161">第二種是完整資料內容，這是 Entity Framework 類別 `System.Data.Objects.ObjectContext` 的執行個體，其中包含將資料列加入至資料庫的 `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` 方法。</span><span class="sxs-lookup"><span data-stu-id="746de-161">Second, the full data context is an instance of the Entity Framework class `System.Data.Objects.ObjectContext`, which contains the method `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` to add rows to the database.</span></span> <span data-ttu-id="746de-162">Entity Framework 可辨識資料表和資料表之間的關聯性，因此會強制資料庫的一致性。</span><span class="sxs-lookup"><span data-stu-id="746de-162">The Entity Framework recognizes the tables and the relationships between them, so it enforces database consistency.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="746de-163">若要更新資料庫</span><span class="sxs-lookup"><span data-stu-id="746de-163">To update the database</span></span>

1. <span data-ttu-id="746de-164">將下列程式碼加入您的程式中。</span><span class="sxs-lookup"><span data-stu-id="746de-164">Add the following code to your program.</span></span> <span data-ttu-id="746de-165">在這個範例中，您會加入兩個彼此之間具有關聯性的物件，而且會加入一位講師和一份辦公室工作。</span><span class="sxs-lookup"><span data-stu-id="746de-165">In this example, you add two objects with a relationship between them, and you add an instructor and an office assignment.</span></span> <span data-ttu-id="746de-166">資料表 `OfficeAssignments` 包含 `InstructorID` 資料行，該資料行參考 `PersonID` 資料表中的 `Person` 資料行。</span><span class="sxs-lookup"><span data-stu-id="746de-166">The table `OfficeAssignments` contains the `InstructorID` column, which references the `PersonID` column in the `Person` table.</span></span>
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

<span data-ttu-id="746de-167">在您呼叫 `System.Data.Objects.ObjectContext.SaveChanges` 之前，資料庫中不會有任何變更。</span><span class="sxs-lookup"><span data-stu-id="746de-167">Nothing is changed in the database until you call `System.Data.Objects.ObjectContext.SaveChanges`.</span></span>
<br />

2. <span data-ttu-id="746de-168">現在將您加入的物件刪除，藉此將資料庫還原至先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="746de-168">Now restore the database to its earlier state by deleting the objects that you added.</span></span>
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
<span data-ttu-id="746de-169">當您使用查詢運算式時，必須記住查詢受到延遲評估限制。</span><span class="sxs-lookup"><span data-stu-id="746de-169">When you use a query expression, you must remember that the query is subject to lazy evaluation.</span></span> <span data-ttu-id="746de-170">因此，資料庫在任何鏈結評估期間仍會保持開啟可供讀取，例如在 Lambda 運算式區塊中的每一個查詢運算式之後。</span><span class="sxs-lookup"><span data-stu-id="746de-170">Therefore, the database is still open for reading during any chained evaluations, such as in the lambda expression blocks after each query expression.</span></span> <span data-ttu-id="746de-171">所有資料庫作業無論是明確或隱含使用異動，都必須在讀取作業完成之後發生。</span><span class="sxs-lookup"><span data-stu-id="746de-171">Any database operation that explicitly or implicitly uses a transaction must occur after the read operations have completed.</span></span>


## <a name="next-steps"></a><span data-ttu-id="746de-172">後續步驟</span><span class="sxs-lookup"><span data-stu-id="746de-172">Next Steps</span></span>
<span data-ttu-id="746de-173">瀏覽其他查詢選項藉由檢視中可用的查詢運算子[查詢運算式](../../language-reference/query-expressions.md)，並同時檢閱[ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)來了解哪些功能時，您可以使用您使用這個型別提供者。</span><span class="sxs-lookup"><span data-stu-id="746de-173">Explore other query options by reviewing the query operators available in [Query Expressions](../../language-reference/query-expressions.md), and also review the [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) to understand what functionality is available to you when you use this type provider.</span></span>


## <a name="see-also"></a><span data-ttu-id="746de-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="746de-174">See Also</span></span>
[<span data-ttu-id="746de-175">類型提供者</span><span class="sxs-lookup"><span data-stu-id="746de-175">Type Providers</span></span>](index.md)  
[<span data-ttu-id="746de-176">SqlEntityConnection 類型提供者</span><span class="sxs-lookup"><span data-stu-id="746de-176">SqlEntityConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)  
[<span data-ttu-id="746de-177">逐步解說： 從 EDMX 結構描述檔案產生 F # 類型</span><span class="sxs-lookup"><span data-stu-id="746de-177">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>](generating-fsharp-types-from-edmx.md)  
[<span data-ttu-id="746de-178">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="746de-178">ADO.NET Entity Framework</span></span>](https://msdn.microsoft.com/library/bb399572)  
[<span data-ttu-id="746de-179">.edmx 檔案概觀</span><span class="sxs-lookup"><span data-stu-id="746de-179">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
[<span data-ttu-id="746de-180">EDM 產生器&#40;EdmGen.exe&#41;</span><span class="sxs-lookup"><span data-stu-id="746de-180">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)  
