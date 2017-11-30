---
title: "逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="5f91f-102">逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率</span><span class="sxs-lookup"><span data-stu-id="5f91f-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="5f91f-103">TPL 資料流程式庫提供<xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType>和<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType>類別，讓您可以接收與緩衝一或多個來源的資料，然後散佈該緩衝的資料，做為一個集合。</span><span class="sxs-lookup"><span data-stu-id="5f91f-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="5f91f-104">當您從一個或多個來源收集資料，然後以批次中處理多個資料元素，此批次處理機制是很有用。</span><span class="sxs-lookup"><span data-stu-id="5f91f-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="5f91f-105">例如，請考慮將記錄插入資料庫中使用資料流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f91f-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="5f91f-106">這項作業可以更有效率，如果多個項目會以循序方式插入在同一時間而非一次。</span><span class="sxs-lookup"><span data-stu-id="5f91f-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="5f91f-107">本文件說明如何使用<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別來改善效率的這類資料庫插入作業。</span><span class="sxs-lookup"><span data-stu-id="5f91f-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="5f91f-108">它也說明如何使用<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>類別來擷取結果和在程式讀取資料庫時，會發生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5f91f-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="5f91f-109">TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f91f-109">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="5f91f-110">若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。</span><span class="sxs-lookup"><span data-stu-id="5f91f-110">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5f91f-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="5f91f-111">Prerequisites</span></span>  
  
1.  <span data-ttu-id="5f91f-112">讀取的聯結區塊 」 一節中[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)開始這個逐步解說之前，先記錄。</span><span class="sxs-lookup"><span data-stu-id="5f91f-112">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="5f91f-113">確定您有一份 Northwind 資料庫，Northwind.sdf，在電腦上。</span><span class="sxs-lookup"><span data-stu-id="5f91f-113">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="5f91f-114">這個檔案通常位於資料夾 %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\。</span><span class="sxs-lookup"><span data-stu-id="5f91f-114">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5f91f-115">在某些版本的 Windows 中，您無法連接至 Northwind.sdf 如果[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]以非系統管理員模式執行。</span><span class="sxs-lookup"><span data-stu-id="5f91f-115">In some versions of Windows, you cannot connect to Northwind.sdf if [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] is running in a non-administrator mode.</span></span> <span data-ttu-id="5f91f-116">若要連接到 Northwind.sdf，啟動[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]或[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]命令提示字元中**系統管理員身分執行**模式。</span><span class="sxs-lookup"><span data-stu-id="5f91f-116">To connect to Northwind.sdf, start [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="5f91f-117">本逐步解說包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="5f91f-117">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="5f91f-118">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="5f91f-118">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="5f91f-119">定義 「 員工 」 類別</span><span class="sxs-lookup"><span data-stu-id="5f91f-119">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="5f91f-120">定義員工資料庫作業</span><span class="sxs-lookup"><span data-stu-id="5f91f-120">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="5f91f-121">加入資料庫中的員工資料，而不需使用緩衝處理</span><span class="sxs-lookup"><span data-stu-id="5f91f-121">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="5f91f-122">使用緩衝將員工資料加入至資料庫</span><span class="sxs-lookup"><span data-stu-id="5f91f-122">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="5f91f-123">若要從資料庫讀取的員工資料使用緩衝的聯結</span><span class="sxs-lookup"><span data-stu-id="5f91f-123">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="5f91f-124">完整範例</span><span class="sxs-lookup"><span data-stu-id="5f91f-124">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="5f91f-125">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="5f91f-125">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="5f91f-126">在[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，建立 Visual C# 或 Visual Basic**主控台應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="5f91f-126">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="5f91f-127">在本文件中，專案命名為 `DataflowBatchDatabase`。</span><span class="sxs-lookup"><span data-stu-id="5f91f-127">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="5f91f-128">在您的專案，加入的參考 System.Data.SqlServerCe.dll 和 System.Threading.Tasks.Dataflow.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="5f91f-128">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="5f91f-129">確定 Form1.cs (為 Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 包含下列`using`(`Imports`中[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5f91f-129">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="5f91f-130">將下列資料成員新增至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="5f91f-130">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="5f91f-131">定義 「 員工 」 類別</span><span class="sxs-lookup"><span data-stu-id="5f91f-131">Defining the Employee Class</span></span>  
 <span data-ttu-id="5f91f-132">若要新增`Program`類別`Employee`類別。</span><span class="sxs-lookup"><span data-stu-id="5f91f-132">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="5f91f-133">`Employee`類別包含三個屬性， `EmployeeID`， `LastName`，和`FirstName`。</span><span class="sxs-lookup"><span data-stu-id="5f91f-133">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="5f91f-134">這些屬性對應於`Employee ID`， `Last Name`，和`First Name`中的資料行`Employees`Northwind 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="5f91f-134">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="5f91f-135">此示範中，`Employee`類別也會定義`Random`方法，建立`Employee`有其內容的隨機值的物件。</span><span class="sxs-lookup"><span data-stu-id="5f91f-135">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="5f91f-136">定義員工資料庫作業</span><span class="sxs-lookup"><span data-stu-id="5f91f-136">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="5f91f-137">若要新增`Program`類別`InsertEmployees`， `GetEmployeeCount`，和`GetEmployeeID`方法。</span><span class="sxs-lookup"><span data-stu-id="5f91f-137">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="5f91f-138">`InsertEmployees`方法會將新員工記錄加入到資料庫。</span><span class="sxs-lookup"><span data-stu-id="5f91f-138">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="5f91f-139">`GetEmployeeCount`方法會擷取中的項目數`Employees`資料表。</span><span class="sxs-lookup"><span data-stu-id="5f91f-139">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="5f91f-140">`GetEmployeeID`方法會擷取具有所提供的名稱的第一個員工的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f91f-140">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="5f91f-141">每一種方法採用 Northwind 資料庫的連接字串，並使用中的功能`System.Data.SqlServerCe`命名空間與資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="5f91f-141">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="5f91f-142">加入資料庫中的員工資料，而不需使用緩衝處理</span><span class="sxs-lookup"><span data-stu-id="5f91f-142">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="5f91f-143">若要新增`Program`類別`AddEmployees`和`PostRandomEmployees`方法。</span><span class="sxs-lookup"><span data-stu-id="5f91f-143">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="5f91f-144">`AddEmployees`方法使用資料流程會隨機員工資料加入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="5f91f-144">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="5f91f-145">它會建立<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件呼叫`InsertEmployees`方法，將員工項目加入至資料庫。</span><span class="sxs-lookup"><span data-stu-id="5f91f-145">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="5f91f-146">`AddEmployees`方法接著呼叫`PostRandomEmployees`張貼多個方法`Employee`物件加入至<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件。</span><span class="sxs-lookup"><span data-stu-id="5f91f-146">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="5f91f-147">`AddEmployees`方法然後等候所有插入作業完成。</span><span class="sxs-lookup"><span data-stu-id="5f91f-147">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="5f91f-148">使用緩衝將員工資料加入至資料庫</span><span class="sxs-lookup"><span data-stu-id="5f91f-148">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="5f91f-149">若要新增`Program`類別`AddEmployeesBatched`方法。</span><span class="sxs-lookup"><span data-stu-id="5f91f-149">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="5f91f-150">這個方法類似於`AddEmployees`，不同之處在於它也會使用<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>要緩衝處理多個類別`Employee`物件傳送至這些物件之前<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件。</span><span class="sxs-lookup"><span data-stu-id="5f91f-150">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="5f91f-151">因為<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別散佈多個項目集合，做<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件遭到修改，在陣列上執行`Employee`物件。</span><span class="sxs-lookup"><span data-stu-id="5f91f-151">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="5f91f-152">在`AddEmployees`方法，`AddEmployeesBatched`呼叫`PostRandomEmployees`張貼多個方法`Employee`物件; 不過，`AddEmployeesBatched`張貼至這些物件<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件。</span><span class="sxs-lookup"><span data-stu-id="5f91f-152">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="5f91f-153">`AddEmployeesBatched`方法也等候所有插入作業完成。</span><span class="sxs-lookup"><span data-stu-id="5f91f-153">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="5f91f-154">若要從資料庫讀取的員工資料使用緩衝的聯結</span><span class="sxs-lookup"><span data-stu-id="5f91f-154">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="5f91f-155">若要新增`Program`類別`GetRandomEmployees`方法。</span><span class="sxs-lookup"><span data-stu-id="5f91f-155">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="5f91f-156">這個方法會列印到主控台的隨機員工的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5f91f-156">This method prints information about random employees to the console.</span></span> <span data-ttu-id="5f91f-157">它會建立數個隨機`Employee`物件並呼叫`GetEmployeeID`方法來擷取每個物件的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f91f-157">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="5f91f-158">因為`GetEmployeeID`方法擲回例外狀況，如果沒有指定第一個和最後一個名稱，不符合員工`GetRandomEmployees`方法會使用<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>類別來儲存`Employee`成功呼叫的物件`GetEmployeeID`和<xref:System.Exception?displayProperty=nameWithType>失敗的呼叫的物件。</span><span class="sxs-lookup"><span data-stu-id="5f91f-158">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="5f91f-159"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601>在此範例中的物件充當<xref:System.Tuple%602>保存一份物件`Employee`物件和一份<xref:System.Exception>物件。</span><span class="sxs-lookup"><span data-stu-id="5f91f-159">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="5f91f-160"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>物件會散佈此資料時收到的總和`Employee`和<xref:System.Exception>物件計數等於批次大小。</span><span class="sxs-lookup"><span data-stu-id="5f91f-160">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="5f91f-161">完整範例</span><span class="sxs-lookup"><span data-stu-id="5f91f-161">The Complete Example</span></span>  
 <span data-ttu-id="5f91f-162">下列範例顯示完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f91f-162">The following example shows the complete code.</span></span> <span data-ttu-id="5f91f-163">`Main`方法會比較所需執行批次的資料庫插入執行非批次的資料庫插入的時間與時間。</span><span class="sxs-lookup"><span data-stu-id="5f91f-163">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="5f91f-164">它也會示範使用緩衝的聯結，可從資料庫讀取的員工資料，及也報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f91f-164">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="5f91f-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f91f-165">See Also</span></span>  
 [<span data-ttu-id="5f91f-166">資料流程</span><span class="sxs-lookup"><span data-stu-id="5f91f-166">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
