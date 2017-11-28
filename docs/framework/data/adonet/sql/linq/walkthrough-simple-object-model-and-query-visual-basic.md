---
title: "逐步解說：簡單的物件模型和查詢 (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed6436dcac1791d735132c295943519af36e307d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="60c9c-102">逐步解說：簡單的物件模型和查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60c9c-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>
<span data-ttu-id="60c9c-103">這個逐步解說提供極為簡單的基本端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。</span><span class="sxs-lookup"><span data-stu-id="60c9c-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="60c9c-104">您將建立的實體類別會構成 Northwind 範例資料庫中的 Customers 資料表。</span><span class="sxs-lookup"><span data-stu-id="60c9c-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="60c9c-105">接著，您會建立簡單查詢，以便列出位於倫敦的客戶。</span><span class="sxs-lookup"><span data-stu-id="60c9c-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="60c9c-106">這個逐步解說的設計是以程式碼為導向，以協助說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 概念。</span><span class="sxs-lookup"><span data-stu-id="60c9c-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="60c9c-107">一般來說，您會使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="60c9c-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="60c9c-108">這個逐步解說是使用 Visual Basic 開發設定所撰寫。</span><span class="sxs-lookup"><span data-stu-id="60c9c-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="60c9c-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="60c9c-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="60c9c-110">這個逐步解說會使用專用資料夾 ("c:\linqtest") 來保存檔案。</span><span class="sxs-lookup"><span data-stu-id="60c9c-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="60c9c-111">請先建立這個資料夾，再開始逐步解說。</span><span class="sxs-lookup"><span data-stu-id="60c9c-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="60c9c-112">這個逐步解說需要使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="60c9c-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="60c9c-113">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。</span><span class="sxs-lookup"><span data-stu-id="60c9c-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="60c9c-114">如需指示，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="60c9c-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="60c9c-115">下載這個資料庫之後，請將檔案複製至 c:\linqtest 資料夾。</span><span class="sxs-lookup"><span data-stu-id="60c9c-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="60c9c-116">概觀</span><span class="sxs-lookup"><span data-stu-id="60c9c-116">Overview</span></span>  
 <span data-ttu-id="60c9c-117">此逐步解說包含六個主要工作：</span><span class="sxs-lookup"><span data-stu-id="60c9c-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="60c9c-118">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中建立 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="60c9c-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="60c9c-119">將類別對應至資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="60c9c-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="60c9c-120">指定類別的屬性以表示資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="60c9c-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="60c9c-121">指定與 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="60c9c-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="60c9c-122">建立要對資料庫執行的簡單查詢。</span><span class="sxs-lookup"><span data-stu-id="60c9c-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="60c9c-123">執行查詢並觀察結果。</span><span class="sxs-lookup"><span data-stu-id="60c9c-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="60c9c-124">建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="60c9c-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="60c9c-125">在第一個工作中，您要建立一個 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案內含必要的參考，以建置並執行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="60c9c-125">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="60c9c-126">若要建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="60c9c-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="60c9c-127">按一下 [檔案] 功能表上的 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="60c9c-127">On the **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="60c9c-128">在**專案類型**窗格**新專案**對話方塊中，按一下  **Visual Basic**。</span><span class="sxs-lookup"><span data-stu-id="60c9c-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="60c9c-129">按一下 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="60c9c-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="60c9c-130">在**名稱**方塊中，輸入**LinqConsoleApp**。</span><span class="sxs-lookup"><span data-stu-id="60c9c-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="60c9c-131">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="60c9c-131">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="60c9c-132">加入 LINQ 參考和指示詞</span><span class="sxs-lookup"><span data-stu-id="60c9c-132">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="60c9c-133">本逐步解說使用的組件，可能在您的專案中預設為不安裝。</span><span class="sxs-lookup"><span data-stu-id="60c9c-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="60c9c-134">如果`System.Data.Linq`未列為專案中參考 (按一下**顯示所有檔案**中**方案總管 中**展開**參考**節點)，請將它加入中所述下列步驟。</span><span class="sxs-lookup"><span data-stu-id="60c9c-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="60c9c-135">若要加入 System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="60c9c-135">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="60c9c-136">在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="60c9c-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="60c9c-137">在**加入參考**對話方塊中，按一下  **.NET**，按一下 System.Data.Linq 組件，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="60c9c-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="60c9c-138">組件隨即加入至專案。</span><span class="sxs-lookup"><span data-stu-id="60c9c-138">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="60c9c-139">此外，在**加入參考**對話方塊中，按一下  **.NET**、 捲動至並按一下 System.Windows.Forms，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="60c9c-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>  
  
     <span data-ttu-id="60c9c-140">這個組件支援這個逐步解說中的訊息方塊，並加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="60c9c-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>  
  
4.  <span data-ttu-id="60c9c-141">將下列指示詞加到 `Module1` 上方：</span><span class="sxs-lookup"><span data-stu-id="60c9c-141">Add the following directives above `Module1`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="60c9c-142">將類別對應至資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="60c9c-142">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="60c9c-143">在這個步驟中，您會建立類別並將它對應至資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="60c9c-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="60c9c-144">這類類別稱為*實體類別*。</span><span class="sxs-lookup"><span data-stu-id="60c9c-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="60c9c-145">請注意，只要加入 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性，即可完成對應。</span><span class="sxs-lookup"><span data-stu-id="60c9c-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="60c9c-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性會指定資料庫中資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="60c9c-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="60c9c-147">若要建立實體類別並將它對應至資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="60c9c-147">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="60c9c-148">將下列程式碼輸入並貼到 Module1.vb 的 `Sub Main` 正上方：</span><span class="sxs-lookup"><span data-stu-id="60c9c-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="60c9c-149">指定類別的屬性以表示資料庫資料行</span><span class="sxs-lookup"><span data-stu-id="60c9c-149">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="60c9c-150">在這個步驟中，您會完成下列幾項工作：</span><span class="sxs-lookup"><span data-stu-id="60c9c-150">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="60c9c-151">您會使用 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute) 指定實體類別的 `CustomerID` 和 `City` 屬性 (Property)，以表示資料庫資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="60c9c-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="60c9c-152">您會指定 `CustomerID` 屬性 (Property)，以表示資料庫中的主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="60c9c-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="60c9c-153">您會指定 `_CustomerID` 和 `_City` 欄位做為私用儲存區。</span><span class="sxs-lookup"><span data-stu-id="60c9c-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> <span data-ttu-id="60c9c-154">然後，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可以直接儲存和擷取值，而不必使用可能含有商務邏輯的公用存取子。</span><span class="sxs-lookup"><span data-stu-id="60c9c-154">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="60c9c-155">若要表示兩個資料庫資料行的特性</span><span class="sxs-lookup"><span data-stu-id="60c9c-155">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="60c9c-156">將下列程式碼輸入並貼到 Module1.vb 的 `End Class` 正前方：</span><span class="sxs-lookup"><span data-stu-id="60c9c-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="60c9c-157">指定與 Northwind 資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="60c9c-157">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="60c9c-158">在這個步驟中，您會使用 <xref:System.Data.Linq.DataContext> 物件，在程式碼架構的資料結構與資料庫本身間建立連接。</span><span class="sxs-lookup"><span data-stu-id="60c9c-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="60c9c-159"><xref:System.Data.Linq.DataContext> 為主要通道，您可透過該通道擷取資料庫中的物件以及送出變更。</span><span class="sxs-lookup"><span data-stu-id="60c9c-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="60c9c-160">您也可以宣告 `Table(Of Customer)` 做為邏輯具型別資料表，供您查詢資料庫中的 Customers 資料表。</span><span class="sxs-lookup"><span data-stu-id="60c9c-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="60c9c-161">您會在後面幾個步驟中，建立和執行這些查詢。</span><span class="sxs-lookup"><span data-stu-id="60c9c-161">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="60c9c-162">若要指定資料庫連接</span><span class="sxs-lookup"><span data-stu-id="60c9c-162">To specify the database connection</span></span>  
  
-   <span data-ttu-id="60c9c-163">將下列程式碼輸入或貼到 `Sub Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="60c9c-163">Type or paste the following code into the `Sub Main` method.</span></span>  
  
     <span data-ttu-id="60c9c-164">請注意，假設 `northwnd.mdf` 檔案是位於 linqtest 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="60c9c-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="60c9c-165">如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。</span><span class="sxs-lookup"><span data-stu-id="60c9c-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="60c9c-166">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="60c9c-166">Creating a Simple Query</span></span>  
 <span data-ttu-id="60c9c-167">在這個步驟中，您會建立查詢以尋找資料庫 Customers 資料表中有哪些客戶位於倫敦。</span><span class="sxs-lookup"><span data-stu-id="60c9c-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="60c9c-168">這個步驟中的查詢程式碼只會描述查詢，</span><span class="sxs-lookup"><span data-stu-id="60c9c-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="60c9c-169">而不會實際執行。</span><span class="sxs-lookup"><span data-stu-id="60c9c-169">It does not execute it.</span></span> <span data-ttu-id="60c9c-170">這種方法稱為*延後執行*。</span><span class="sxs-lookup"><span data-stu-id="60c9c-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="60c9c-171">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="60c9c-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="60c9c-172">此外，您還會產生記錄檔輸出，以顯示 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 所產生的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="60c9c-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="60c9c-173">這項記錄功能 (其使用 <xref:System.Data.Linq.DataContext.Log%2A>) 有助於進行偵錯，以及判斷要傳送至資料庫的命令是否正確地表示您的查詢。</span><span class="sxs-lookup"><span data-stu-id="60c9c-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="60c9c-174">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="60c9c-174">To create a simple query</span></span>  
  
-   <span data-ttu-id="60c9c-175">將下列程式碼輸入或貼到 `Sub Main` 方法的 `Table(Of Customer)` 宣告後面：</span><span class="sxs-lookup"><span data-stu-id="60c9c-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="60c9c-176">執行查詢</span><span class="sxs-lookup"><span data-stu-id="60c9c-176">Executing the Query</span></span>  
 <span data-ttu-id="60c9c-177">在這個步驟中，您要實際執行這個查詢。</span><span class="sxs-lookup"><span data-stu-id="60c9c-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="60c9c-178">而在需要結果時，才會評估您在前面的步驟中建立的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="60c9c-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="60c9c-179">當您開始 `For Each` 反覆運算時，會對資料庫執行 SQL 命令，並且將物件具體化。</span><span class="sxs-lookup"><span data-stu-id="60c9c-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="60c9c-180">查詢查詢</span><span class="sxs-lookup"><span data-stu-id="60c9c-180">To execute the query</span></span>  
  
1.  <span data-ttu-id="60c9c-181">將下列程式碼輸入或貼到 `Sub Main` 方法的結尾 (在查詢描述後面)：</span><span class="sxs-lookup"><span data-stu-id="60c9c-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="60c9c-182">按 F5，進行應用程式偵錯。</span><span class="sxs-lookup"><span data-stu-id="60c9c-182">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="60c9c-183">如果您的應用程式產生執行階段錯誤，請參閱 < 疑難排解 > 一節的[依逐步解說學習](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="60c9c-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="60c9c-184">訊息方塊會顯示內含六位客戶的清單。</span><span class="sxs-lookup"><span data-stu-id="60c9c-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="60c9c-185">[主控台] 視窗會顯示產生的 SQL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="60c9c-185">The Console window displays the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="60c9c-186">按一下**確定**來解除訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="60c9c-186">Click **OK** to dismiss the message box.</span></span>  
  
     <span data-ttu-id="60c9c-187">應用程式隨即關閉。</span><span class="sxs-lookup"><span data-stu-id="60c9c-187">The application closes.</span></span>  
  
4.  <span data-ttu-id="60c9c-188">在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="60c9c-188">On the **File** menu, click **Save All**.</span></span>  
  
     <span data-ttu-id="60c9c-189">如果繼續進行下一個逐步解說，則需要這個應用程式。</span><span class="sxs-lookup"><span data-stu-id="60c9c-189">You will need this application if you continue with the next walkthrough.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="60c9c-190">後續步驟</span><span class="sxs-lookup"><span data-stu-id="60c9c-190">Next Steps</span></span>  
 <span data-ttu-id="60c9c-191">[逐步解說： 跨關聯性查詢 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)主題會繼續本逐步解說結束的位置。</span><span class="sxs-lookup"><span data-stu-id="60c9c-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="60c9c-192">跨關聯性查詢逐步解說將示範如何[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]跨資料表，類似於查詢*聯結*關聯式資料庫中。</span><span class="sxs-lookup"><span data-stu-id="60c9c-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="60c9c-193">如果您想執行＜跨關聯性查詢＞逐步解說，請務必儲存您剛完成之逐步解說的方案，這是必要的條件。</span><span class="sxs-lookup"><span data-stu-id="60c9c-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c9c-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60c9c-194">See Also</span></span>  
 [<span data-ttu-id="60c9c-195">依逐步解說學習</span><span class="sxs-lookup"><span data-stu-id="60c9c-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
