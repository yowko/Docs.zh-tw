---
title: "逐步解說：操作資料 (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 502023c3929ffaa6766c906ca32489b43915f0ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="f0b4e-102">逐步解說：操作資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b4e-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="f0b4e-103">本逐步解說針對加入、修改和刪除資料庫中的資料，提供基本的端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="f0b4e-104">您將使用範例 Northwind 資料庫的複本來加入客戶、變更客戶名稱，以及刪除訂單。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="f0b4e-105">本逐步解說的內容是依據 Visual C# 開發設定所撰寫的。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f0b4e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="f0b4e-106">Prerequisites</span></span>  
 <span data-ttu-id="f0b4e-107">本逐步解說需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="f0b4e-108">本逐步解說會使用專用資料夾 ("c:\linqtest6") 來保存檔案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="f0b4e-109">請先建立這個資料夾，再開始逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="f0b4e-110">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="f0b4e-111">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="f0b4e-112">如需指示，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="f0b4e-113">下載資料庫之後，請將 northwnd.mdf 檔案複製至 c:\linqtest6 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
-   <span data-ttu-id="f0b4e-114">會從 Northwind 資料庫產生 C# 程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="f0b4e-115">您可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]或 SQLMetal 工具來產生這個檔案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="f0b4e-116">本逐步解說是使用 SQLMetal 工具，以下列命令列所撰寫：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="f0b4e-117">**sqlmetal /code:"c:\linqtest6\northwind.cs"/language:csharp"C:\linqtest6\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="f0b4e-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="f0b4e-118">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="f0b4e-119">概觀</span><span class="sxs-lookup"><span data-stu-id="f0b4e-119">Overview</span></span>  
 <span data-ttu-id="f0b4e-120">此逐步解說包含六個主要工作：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="f0b4e-121">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中建立 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="f0b4e-122">將資料庫程式碼檔案加入至專案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="f0b4e-123">建立新的客戶物件。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="f0b4e-124">修改客戶的連絡人名稱。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="f0b4e-125">刪除訂單。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="f0b4e-126">將這些變更送出至 Northwind 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="f0b4e-127">建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="f0b4e-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="f0b4e-128">在第一個工作中，您要建立一個 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案內含必要的參考，以建置並執行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-128">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="f0b4e-129">若要建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="f0b4e-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="f0b4e-130">在[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-130">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f0b4e-131">在**專案類型**窗格**新專案**對話方塊中，按一下 **Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="f0b4e-132">按一下 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="f0b4e-133">在**名稱**方塊中，輸入**LinqDataManipulationApp**。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="f0b4e-134">在**位置**方塊中，確認您要儲存專案檔。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="f0b4e-135">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="f0b4e-136">加入 LINQ 參考和指示詞</span><span class="sxs-lookup"><span data-stu-id="f0b4e-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="f0b4e-137">本逐步解說使用的組件，可能在您的專案中預設為不安裝。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="f0b4e-138">如果 System.Data.Linq 未列為專案中的參考，請按照下列步驟所述將它加入：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="f0b4e-139">若要加入 System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="f0b4e-139">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="f0b4e-140">在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="f0b4e-141">在**加入參考**對話方塊中，按一下  **.NET**，按一下 System.Data.Linq 組件，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="f0b4e-142">組件隨即加入至專案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-142">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="f0b4e-143">將下列指示詞加在 Program.cs 的上方：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f0b4e-144">將 Northwind 程式碼檔案加入至專案</span><span class="sxs-lookup"><span data-stu-id="f0b4e-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="f0b4e-145">這些步驟假設您已使用 SQLMetal 工具，從 Northwind 範例資料庫產生程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="f0b4e-146">如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="f0b4e-147">若要將 Northwind 程式碼檔案加入至專案</span><span class="sxs-lookup"><span data-stu-id="f0b4e-147">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="f0b4e-148">在**專案**功能表上，按一下 **加入現有項目**。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="f0b4e-149">在**加入現有項目**對話方塊中，巡覽至 c:\linqtest6\northwind.cs，，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f0b4e-150">northwind.cs 檔案會加入至專案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="f0b4e-151">設定資料庫連接</span><span class="sxs-lookup"><span data-stu-id="f0b4e-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="f0b4e-152">請先測試與資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-152">First, test your connection to the database.</span></span> <span data-ttu-id="f0b4e-153">請特別注意，資料庫 Northwnd 沒有字母 i。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="f0b4e-154">如果在後續步驟發生錯誤，則請檢閱 northwind.cs 檔案，以判斷 Northwind 部分類別的拼法。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="f0b4e-155">若要設定和測試資料庫連接</span><span class="sxs-lookup"><span data-stu-id="f0b4e-155">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="f0b4e-156">將下列程式碼輸入或貼入 Program 類別的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  <span data-ttu-id="f0b4e-157">按 F5，立即測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="f0b4e-158">A**主控台**視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="f0b4e-159">您可以關閉應用程式中按 Enter 鍵**主控台**視窗中，或按一下**停止偵錯**上[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]**偵錯**功能表。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="f0b4e-160">建立新的實體</span><span class="sxs-lookup"><span data-stu-id="f0b4e-160">Creating a New Entity</span></span>  
 <span data-ttu-id="f0b4e-161">建立新的實體十分簡單。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="f0b4e-162">您可以使用 `Customer` 關鍵字，建立物件 (如 `new`)。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="f0b4e-163">在本節和下列各節中，您變更的只是本機快取。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="f0b4e-164">在本逐步解說最後呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 之前，都不會將變更傳送至資料庫。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="f0b4e-165">若要加入新的 Customer 實體物件</span><span class="sxs-lookup"><span data-stu-id="f0b4e-165">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="f0b4e-166">在 `Customer` 方法的 `Console.ReadLine();` 前面加入下列程式碼，建立新的 `Main`：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="f0b4e-167">按 F5 對方案進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-167">Press F5 to debug the solution.</span></span>  
  
3.  <span data-ttu-id="f0b4e-168">中按 Enter 鍵**主控台**視窗以停止偵錯並繼續進行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="f0b4e-169">更新實體</span><span class="sxs-lookup"><span data-stu-id="f0b4e-169">Updating an Entity</span></span>  
 <span data-ttu-id="f0b4e-170">在下列步驟中，您會擷取 `Customer` 物件，並修改它的其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="f0b4e-171">若要變更 Customer 的名稱</span><span class="sxs-lookup"><span data-stu-id="f0b4e-171">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="f0b4e-172">將下列程式碼加入至 `Console.ReadLine();` 的上方：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="f0b4e-173">刪除實體</span><span class="sxs-lookup"><span data-stu-id="f0b4e-173">Deleting an Entity</span></span>  
 <span data-ttu-id="f0b4e-174">您可以使用同一個客戶物件，刪除第一份訂單。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="f0b4e-175">在下列程式碼中，會示範如何中斷資料列之間的關聯性 (Relationship)，以及如何刪除資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="f0b4e-176">將下列程式碼加入至 `Console.ReadLine` 的前面，以查看如何刪除物件：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="f0b4e-177">若要刪除資料列</span><span class="sxs-lookup"><span data-stu-id="f0b4e-177">To delete a row</span></span>  
  
-   <span data-ttu-id="f0b4e-178">將下列程式碼加入至 `Console.ReadLine();` 的正上方：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="f0b4e-179">將變更送出至資料庫</span><span class="sxs-lookup"><span data-stu-id="f0b4e-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="f0b4e-180">建立、更新和刪除物件的最終必要步驟是實際將變更送出至資料庫。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="f0b4e-181">沒有這個步驟，所進行的變更只是針對本機，並不會出現在查詢結果中。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="f0b4e-182">若要將變更送出至資料庫</span><span class="sxs-lookup"><span data-stu-id="f0b4e-182">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="f0b4e-183">將下列程式碼插入至 `Console.ReadLine` 的正上方：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="f0b4e-184">將下列程式碼插入至 `SubmitChanges` 的後面，以顯示送出變更之前和之後的效果：</span><span class="sxs-lookup"><span data-stu-id="f0b4e-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  <span data-ttu-id="f0b4e-185">按 F5 對方案進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-185">Press F5 to debug the solution.</span></span>  
  
4.  <span data-ttu-id="f0b4e-186">中按 Enter 鍵**主控台**關閉應用程式的視窗。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0b4e-187">送出變更以加入新的客戶之後，無法再照原狀執行這個方案。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="f0b4e-188">若要重新執行方案，請變更要加入的客戶名稱和客戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="f0b4e-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b4e-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0b4e-189">See Also</span></span>  
 [<span data-ttu-id="f0b4e-190">依逐步解說學習</span><span class="sxs-lookup"><span data-stu-id="f0b4e-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
