---
title: "逐步解說：簡單的物件模型和查詢 (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 444692cb035d97b0fe57c1ea9ba7802491ca2160
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="bf095-102">逐步解說：簡單的物件模型和查詢 (C#)</span><span class="sxs-lookup"><span data-stu-id="bf095-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="bf095-103">這個逐步解說提供極為簡單的基本端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。</span><span class="sxs-lookup"><span data-stu-id="bf095-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="bf095-104">您將建立的實體類別會構成 Northwind 範例資料庫中的 Customers 資料表。</span><span class="sxs-lookup"><span data-stu-id="bf095-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="bf095-105">接著，您會建立簡單查詢，以便列出位於倫敦的客戶。</span><span class="sxs-lookup"><span data-stu-id="bf095-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="bf095-106">這個逐步解說的設計是以程式碼為導向，以協助說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 概念。</span><span class="sxs-lookup"><span data-stu-id="bf095-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="bf095-107">一般來說，您會使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="bf095-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="bf095-108">本逐步解說的內容是依據 Visual C# 開發設定所撰寫的。</span><span class="sxs-lookup"><span data-stu-id="bf095-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bf095-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="bf095-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="bf095-110">本逐步解說會使用專用資料夾 ("c:\linqtest5") 來保存檔案。</span><span class="sxs-lookup"><span data-stu-id="bf095-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="bf095-111">請先建立這個資料夾，再開始逐步解說。</span><span class="sxs-lookup"><span data-stu-id="bf095-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="bf095-112">這個逐步解說需要使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="bf095-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="bf095-113">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。</span><span class="sxs-lookup"><span data-stu-id="bf095-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="bf095-114">如需指示，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="bf095-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="bf095-115">下載此資料庫之後，請將檔案複製到 c:\linqtest5 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bf095-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="bf095-116">概觀</span><span class="sxs-lookup"><span data-stu-id="bf095-116">Overview</span></span>  
 <span data-ttu-id="bf095-117">此逐步解說包含六個主要工作：</span><span class="sxs-lookup"><span data-stu-id="bf095-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="bf095-118">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中建立 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="bf095-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="bf095-119">將類別對應至資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="bf095-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="bf095-120">指定類別的屬性以表示資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="bf095-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="bf095-121">指定與 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="bf095-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="bf095-122">建立要對資料庫執行的簡單查詢。</span><span class="sxs-lookup"><span data-stu-id="bf095-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="bf095-123">執行查詢並觀察結果。</span><span class="sxs-lookup"><span data-stu-id="bf095-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="bf095-124">建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="bf095-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="bf095-125">在第一個工作中，您要建立一個 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案內含必要的參考，以建置並執行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="bf095-125">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="bf095-126">若要建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="bf095-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="bf095-127">在[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="bf095-127">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="bf095-128">在**專案類型**窗格**新專案**對話方塊中，按一下  **Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="bf095-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="bf095-129">按一下 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="bf095-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="bf095-130">在**名稱**方塊中，輸入**LinqConsoleApp**。</span><span class="sxs-lookup"><span data-stu-id="bf095-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="bf095-131">在**位置**方塊中，確認您要儲存專案檔。</span><span class="sxs-lookup"><span data-stu-id="bf095-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="bf095-132">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="bf095-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="bf095-133">加入 LINQ 參考和指示詞</span><span class="sxs-lookup"><span data-stu-id="bf095-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="bf095-134">本逐步解說使用的組件，可能在您的專案中預設為不安裝。</span><span class="sxs-lookup"><span data-stu-id="bf095-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="bf095-135">如果 System.Data.Linq 未列為專案中參考 (展開**參考**節點**方案總管 中**)，請將它加入下列步驟所述。</span><span class="sxs-lookup"><span data-stu-id="bf095-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="bf095-136">若要加入 System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="bf095-136">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="bf095-137">在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="bf095-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="bf095-138">在**加入參考**對話方塊中，按一下  **.NET**，按一下 System.Data.Linq 組件，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="bf095-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="bf095-139">組件隨即加入至專案。</span><span class="sxs-lookup"><span data-stu-id="bf095-139">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="bf095-140">在最上方加入下列指示詞**Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="bf095-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="bf095-141">將類別對應至資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="bf095-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="bf095-142">在這個步驟中，您會建立類別並將它對應至資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="bf095-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="bf095-143">這類類別稱為*實體類別*。</span><span class="sxs-lookup"><span data-stu-id="bf095-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="bf095-144">請注意，只要加入 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性，即可完成對應。</span><span class="sxs-lookup"><span data-stu-id="bf095-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="bf095-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性會指定資料庫中資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf095-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="bf095-146">若要建立實體類別並將它對應至資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="bf095-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="bf095-147">在 Program.cs 中的 `Program` 類別宣告正上方輸入或貼上下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="bf095-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="bf095-148">指定類別的屬性以表示資料庫資料行</span><span class="sxs-lookup"><span data-stu-id="bf095-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="bf095-149">在這個步驟中，您會完成下列幾項工作：</span><span class="sxs-lookup"><span data-stu-id="bf095-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="bf095-150">您會使用 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute) 指定實體類別的 `CustomerID` 和 `City` 屬性 (Property)，以表示資料庫資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="bf095-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="bf095-151">您會指定 `CustomerID` 屬性 (Property)，以表示資料庫中的主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="bf095-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="bf095-152">您會指定 `_CustomerID` 和 `_City` 欄位做為私用儲存區。</span><span class="sxs-lookup"><span data-stu-id="bf095-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> <span data-ttu-id="bf095-153">然後，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可以直接儲存和擷取值，而不必使用可能含有商務邏輯的公用存取子。</span><span class="sxs-lookup"><span data-stu-id="bf095-153">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="bf095-154">若要表示兩個資料庫資料行的特性</span><span class="sxs-lookup"><span data-stu-id="bf095-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="bf095-155">在 Program.cs 中 `Customer` 類別的大括號內輸入或貼上列程式碼：</span><span class="sxs-lookup"><span data-stu-id="bf095-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="bf095-156">指定與 Northwind 資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="bf095-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="bf095-157">在這個步驟中，您會使用 <xref:System.Data.Linq.DataContext> 物件，在程式碼架構的資料結構與資料庫本身間建立連接。</span><span class="sxs-lookup"><span data-stu-id="bf095-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="bf095-158"><xref:System.Data.Linq.DataContext> 為主要通道，您可透過該通道擷取資料庫中的物件以及送出變更。</span><span class="sxs-lookup"><span data-stu-id="bf095-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="bf095-159">您也可以宣告 `Table<Customer>` 做為邏輯具型別資料表，供您查詢資料庫中的 Customers 資料表。</span><span class="sxs-lookup"><span data-stu-id="bf095-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="bf095-160">您會在後面幾個步驟中，建立和執行這些查詢。</span><span class="sxs-lookup"><span data-stu-id="bf095-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="bf095-161">若要指定資料庫連接</span><span class="sxs-lookup"><span data-stu-id="bf095-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="bf095-162">將下列程式碼輸入或貼到 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="bf095-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="bf095-163">請注意，`northwnd.mdf` 檔案會假設位於 linqtest5 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bf095-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="bf095-164">如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。</span><span class="sxs-lookup"><span data-stu-id="bf095-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="bf095-165">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="bf095-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="bf095-166">在這個步驟中，您會建立查詢以尋找資料庫 Customers 資料表中有哪些客戶位於倫敦。</span><span class="sxs-lookup"><span data-stu-id="bf095-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="bf095-167">這個步驟中的查詢程式碼只會描述查詢，</span><span class="sxs-lookup"><span data-stu-id="bf095-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="bf095-168">而不會實際執行。</span><span class="sxs-lookup"><span data-stu-id="bf095-168">It does not execute it.</span></span> <span data-ttu-id="bf095-169">這種方法稱為*延後執行*。</span><span class="sxs-lookup"><span data-stu-id="bf095-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="bf095-170">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="bf095-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="bf095-171">此外，您還會產生記錄檔輸出，以顯示 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 所產生的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="bf095-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="bf095-172">這項記錄功能 (其使用 <xref:System.Data.Linq.DataContext.Log%2A>) 有助於進行偵錯，以及判斷要傳送至資料庫的命令是否正確地表示您的查詢。</span><span class="sxs-lookup"><span data-stu-id="bf095-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="bf095-173">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="bf095-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="bf095-174">在 `Main` 方法中的 `Table<Customer>` 宣告之後輸入或貼上下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf095-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="bf095-175">執行查詢</span><span class="sxs-lookup"><span data-stu-id="bf095-175">Executing the Query</span></span>  
 <span data-ttu-id="bf095-176">在這個步驟中，您要實際執行這個查詢。</span><span class="sxs-lookup"><span data-stu-id="bf095-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="bf095-177">而在需要結果時，才會評估您在前面的步驟中建立的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="bf095-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="bf095-178">當您開始 `foreach` 反覆運算時，會對資料庫執行 SQL 命令，並且將物件具體化。</span><span class="sxs-lookup"><span data-stu-id="bf095-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="bf095-179">查詢查詢</span><span class="sxs-lookup"><span data-stu-id="bf095-179">To execute the query</span></span>  
  
1.  <span data-ttu-id="bf095-180">在 `Main` 方法的尾端輸入或貼上下列程式碼 (在查詢描述之後)。</span><span class="sxs-lookup"><span data-stu-id="bf095-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="bf095-181">按 F5，進行應用程式偵錯。</span><span class="sxs-lookup"><span data-stu-id="bf095-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf095-182">如果您的應用程式產生執行階段錯誤，請參閱 < 疑難排解 > 一節的[依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="bf095-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="bf095-183">主控台視窗中的查詢結果應如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf095-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  <span data-ttu-id="bf095-184">在主控台視窗中按 Enter 鍵，以關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf095-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="bf095-185">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bf095-185">Next Steps</span></span>  
 <span data-ttu-id="bf095-186">[逐步解說： 跨關聯性查詢 (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)主題會繼續本逐步解說結束的位置。</span><span class="sxs-lookup"><span data-stu-id="bf095-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="bf095-187">跨關聯性查詢 > 逐步解說將示範如何[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]跨資料表，類似於查詢*聯結*關聯式資料庫中。</span><span class="sxs-lookup"><span data-stu-id="bf095-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="bf095-188">如果您想執行＜跨關聯性查詢＞逐步解說，請務必儲存您剛在本逐步解說完成的方案，這是必要的條件。</span><span class="sxs-lookup"><span data-stu-id="bf095-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf095-189">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf095-189">See Also</span></span>  
 [<span data-ttu-id="bf095-190">依逐步解說學習</span><span class="sxs-lookup"><span data-stu-id="bf095-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
