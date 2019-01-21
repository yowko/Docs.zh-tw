---
title: 逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0367b4224b49377d8d17045e044976e1c511a8ed
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222090"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="ef329-102">逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率</span><span class="sxs-lookup"><span data-stu-id="ef329-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="ef329-103">TPL 資料流程程式庫提供 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> 類別，如此您可以接收來自一或多個來源的資料並緩衝，然後將該已緩衝的資料作為集合散佈。</span><span class="sxs-lookup"><span data-stu-id="ef329-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="ef329-104">這個批次機制在您從一或多個來源收集資料時非常實用，而且可接著批次處理多個資料元素。</span><span class="sxs-lookup"><span data-stu-id="ef329-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="ef329-105">例如，以使用資料流程將記錄插入資料庫的應用程式為例。</span><span class="sxs-lookup"><span data-stu-id="ef329-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="ef329-106">如果多個項目可以同時插入，而不是以循序方式逐一插入，這項作業就會更有效率。</span><span class="sxs-lookup"><span data-stu-id="ef329-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="ef329-107">本文件描述如何使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別來改善這類資料庫插入作業的效率。</span><span class="sxs-lookup"><span data-stu-id="ef329-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="ef329-108">文中也描述如何使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 類別，在程式從資料庫進行讀取時擷取結果以及所發生的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ef329-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="ef329-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="ef329-109">Prerequisites</span></span>  
  
1.  <span data-ttu-id="ef329-110">開始此逐步解說之前，請先閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)文件中的＜聯結區塊＞一節。</span><span class="sxs-lookup"><span data-stu-id="ef329-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="ef329-111">確定您電腦上有可用的 Northwind 資料庫複本 (Northwind.sdf)。</span><span class="sxs-lookup"><span data-stu-id="ef329-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="ef329-112">這個檔案通常位於資料夾：%Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\。</span><span class="sxs-lookup"><span data-stu-id="ef329-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="ef329-113">在某些 Windows 版本中，如果 Visual Studio 是以非系統管理員模式執行，就無法連線到 Northwind.sdf。</span><span class="sxs-lookup"><span data-stu-id="ef329-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="ef329-114">若要連線到 Northwind.sdf，請使用 [以系統管理員身分執行] 模式來啟動 Visual Studio 或 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ef329-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="ef329-115">本逐步解說包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="ef329-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="ef329-116">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ef329-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="ef329-117">定義員工類別</span><span class="sxs-lookup"><span data-stu-id="ef329-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="ef329-118">定義員工資料庫作業</span><span class="sxs-lookup"><span data-stu-id="ef329-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="ef329-119">不使用緩衝將員工資料新增至資料庫</span><span class="sxs-lookup"><span data-stu-id="ef329-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="ef329-120">使用緩衝將員工資料新增至資料庫</span><span class="sxs-lookup"><span data-stu-id="ef329-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="ef329-121">使用緩衝聯結從資料庫讀取員工資料</span><span class="sxs-lookup"><span data-stu-id="ef329-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="ef329-122">完整範例</span><span class="sxs-lookup"><span data-stu-id="ef329-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="ef329-123">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ef329-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="ef329-124">在 Visual Studio 中，建立 Visual C# 或 Visual Basic **主控台應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="ef329-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="ef329-125">在本文件中，專案命名為 `DataflowBatchDatabase`。</span><span class="sxs-lookup"><span data-stu-id="ef329-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="ef329-126">在您的專案中，加入 System.Data.SqlServerCe.dll 的參考，和 System.Threading.Tasks.Dataflow.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="ef329-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="ef329-127">確定 Form1.cs (在 Visual Basic 中為 Form1.vb) 包含下列 `using` (在 Visual Basic 中為 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ef329-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="ef329-128">將下列資料成員新增至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="ef329-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="ef329-129">定義員工類別</span><span class="sxs-lookup"><span data-stu-id="ef329-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="ef329-130">將 `Employee` 類別加入至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="ef329-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="ef329-131">`Employee` 類別包含三個屬性：`EmployeeID`、`LastName` 和 `FirstName`。</span><span class="sxs-lookup"><span data-stu-id="ef329-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="ef329-132">這些屬性對應至 Northwind 資料庫中 `Employees` 資料表的 `Employee ID`、`Last Name` 和 `First Name` 資料行。</span><span class="sxs-lookup"><span data-stu-id="ef329-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="ef329-133">在此示範中，`Employee` 類別也會定義 `Random` 方法，此方法會建立具有隨機屬性值的 `Employee` 物件。</span><span class="sxs-lookup"><span data-stu-id="ef329-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="ef329-134">定義員工資料庫作業</span><span class="sxs-lookup"><span data-stu-id="ef329-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="ef329-135">將 `InsertEmployees`、`GetEmployeeCount` 和 `GetEmployeeID` 方法加入到 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="ef329-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="ef329-136">`InsertEmployees` 方法會將新的員工記錄新增到資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef329-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="ef329-137">`GetEmployeeCount` 方法會擷取 `Employees` 資料表中的項目數量。</span><span class="sxs-lookup"><span data-stu-id="ef329-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="ef329-138">`GetEmployeeID` 方法會擷取具有所提供之名稱的第一位員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="ef329-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="ef329-139">這些方法都採用針對 Northwind 資料庫的連接字串，並且使用 `System.Data.SqlServerCe` 命名空間中的功能與資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="ef329-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="ef329-140">不使用緩衝將員工資料新增至資料庫</span><span class="sxs-lookup"><span data-stu-id="ef329-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="ef329-141">將 `AddEmployees` 和 `PostRandomEmployees` 方法加入到 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="ef329-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="ef329-142">`AddEmployees` 方法會使用資料流程，將隨機的員工資料新增到資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef329-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="ef329-143">它會建立呼叫 `InsertEmployees` 方法的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，以將員工項目新增到資料庫。</span><span class="sxs-lookup"><span data-stu-id="ef329-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="ef329-144">然後，`AddEmployees` 方法會呼叫 `PostRandomEmployees` 方法，將多個 `Employee` 物件張貼到 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="ef329-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="ef329-145">`AddEmployees` 方法接著等候所有插入作業完成。</span><span class="sxs-lookup"><span data-stu-id="ef329-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="ef329-146">使用緩衝將員工資料新增至資料庫</span><span class="sxs-lookup"><span data-stu-id="ef329-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="ef329-147">將 `AddEmployeesBatched` 方法加入至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="ef329-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="ef329-148">這個方法類似於 `AddEmployees`，不同之處在於它也會使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別來緩衝多個 `Employee` 物件，然後才將那些物件傳送到 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="ef329-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="ef329-149">因為 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別將多個元素以集合方式散佈，因此要修改 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件以在 `Employee` 物件陣列上運作。</span><span class="sxs-lookup"><span data-stu-id="ef329-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="ef329-150">如同在 `AddEmployees` 方法中，`AddEmployeesBatched` 會呼叫 `PostRandomEmployees` 方法以張貼多個 `Employee` 物件。不過，`AddEmployeesBatched` 會將這些物件張貼到 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="ef329-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="ef329-151">`AddEmployeesBatched` 方法也會等候所有插入作業完成。</span><span class="sxs-lookup"><span data-stu-id="ef329-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="ef329-152">使用緩衝聯結從資料庫讀取員工資料</span><span class="sxs-lookup"><span data-stu-id="ef329-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="ef329-153">將 `GetRandomEmployees` 方法加入至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="ef329-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="ef329-154">此方法會將有關隨機員工的資訊列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="ef329-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="ef329-155">它會建立數個隨機的 `Employee` 物件，並呼叫 `GetEmployeeID` 方法以擷取每個物件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ef329-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="ef329-156">因為 `GetEmployeeID` 方法會在沒有符合指定之姓名的員工時擲回例外狀況，`GetRandomEmployees` 方法會使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 類別來儲存呼叫 `GetEmployeeID` 成功時的 `Employee` 物件，以及呼叫失敗時的 <xref:System.Exception?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="ef329-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="ef329-157">本範例中的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件會作為保存 `Employee` 物件清單和 <xref:System.Exception> 物件清單的 <xref:System.Tuple%602> 物件。</span><span class="sxs-lookup"><span data-stu-id="ef329-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="ef329-158">當接收的 `Employee` 總和和 <xref:System.Exception> 物件計數與批次大小相等時，<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 物件會散佈此資料。</span><span class="sxs-lookup"><span data-stu-id="ef329-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="ef329-159">完整範例</span><span class="sxs-lookup"><span data-stu-id="ef329-159">The Complete Example</span></span>  
 <span data-ttu-id="ef329-160">下列範例顯示完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef329-160">The following example shows the complete code.</span></span> <span data-ttu-id="ef329-161">`Main` 方法會比較執行批次資料庫插入作業所需的時間，與執行非批次資料庫插入作業所需的時間。</span><span class="sxs-lookup"><span data-stu-id="ef329-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="ef329-162">它也會示範緩衝聯結的使用方式，以從資料庫讀取員工資料，而且也會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef329-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="ef329-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef329-163">See also</span></span>

- [<span data-ttu-id="ef329-164">資料流程</span><span class="sxs-lookup"><span data-stu-id="ef329-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
