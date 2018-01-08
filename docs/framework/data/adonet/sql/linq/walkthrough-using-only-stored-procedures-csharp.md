---
title: "逐步解說：僅使用預存程序 (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1b3cc18f481a0e66d52f021b7bf6b76938fc5018
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="0898d-102">逐步解說：僅使用預存程序 (C#)</span><span class="sxs-lookup"><span data-stu-id="0898d-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="0898d-103">本逐步解說會針對只執行預存程序來存取資料，提供基本的端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。</span><span class="sxs-lookup"><span data-stu-id="0898d-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="0898d-104">資料庫管理員會使用這個方法來限制對資料存放區的存取。</span><span class="sxs-lookup"><span data-stu-id="0898d-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0898d-105">妳也可以使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中的預存程序來覆寫預設行為，特別是針對 `Create`、`Update` 和 `Delete` 處理序。</span><span class="sxs-lookup"><span data-stu-id="0898d-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="0898d-106">如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="0898d-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="0898d-107">基於本逐步解說的目的，您會使用兩個已對應至 Northwind 範例資料庫中之預存程序的方法：CustOrdersDetail 和 CustOrderHist。</span><span class="sxs-lookup"><span data-stu-id="0898d-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="0898d-108">當您執行 SqlMetal 命令列工具以產生 C# 檔案時，會發生對應。</span><span class="sxs-lookup"><span data-stu-id="0898d-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="0898d-109">如需詳細資訊，請參閱本逐步解說後面的「必要條件」一節。</span><span class="sxs-lookup"><span data-stu-id="0898d-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="0898d-110">這個逐步解說並不依賴[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0898d-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="0898d-111">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員也可以使用 [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] 來實作預存程序功能。</span><span class="sxs-lookup"><span data-stu-id="0898d-111">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="0898d-112">請參閱[LINQ to SQL 工具，Visual Studio 中](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。</span><span class="sxs-lookup"><span data-stu-id="0898d-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="0898d-113">本逐步解說的內容是依據 Visual C# 開發設定所撰寫的。</span><span class="sxs-lookup"><span data-stu-id="0898d-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0898d-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="0898d-114">Prerequisites</span></span>  
 <span data-ttu-id="0898d-115">本逐步解說需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="0898d-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="0898d-116">這個逐步解說會使用專用資料夾 ("c:\linqtest7") 來保存檔案。</span><span class="sxs-lookup"><span data-stu-id="0898d-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="0898d-117">請先建立這個資料夾，再開始逐步解說。</span><span class="sxs-lookup"><span data-stu-id="0898d-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="0898d-118">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="0898d-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="0898d-119">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。</span><span class="sxs-lookup"><span data-stu-id="0898d-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="0898d-120">如需指示，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="0898d-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="0898d-121">下載資料庫之後，請將 northwnd.mdf 檔案複製至 c:\linqtest7 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0898d-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="0898d-122">會從 Northwind 資料庫產生 C# 程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="0898d-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="0898d-123">這個逐步解說是使用 SqlMetal 工具，以下列命令列所撰寫：</span><span class="sxs-lookup"><span data-stu-id="0898d-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="0898d-124">**sqlmetal /code:"c:\linqtest7\northwind.cs"/language:csharp"c:\linqtest7\northwnd.mdf"/sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="0898d-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="0898d-125">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="0898d-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="0898d-126">總覽</span><span class="sxs-lookup"><span data-stu-id="0898d-126">Overview</span></span>  
 <span data-ttu-id="0898d-127">此逐步解說包含六個主要工作：</span><span class="sxs-lookup"><span data-stu-id="0898d-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="0898d-128">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中設定 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 解決方案。</span><span class="sxs-lookup"><span data-stu-id="0898d-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="0898d-129">將 System.Data.Linq 組件加入至專案。</span><span class="sxs-lookup"><span data-stu-id="0898d-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="0898d-130">將資料庫程式碼檔案加入至專案。</span><span class="sxs-lookup"><span data-stu-id="0898d-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="0898d-131">建立與資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="0898d-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="0898d-132">設定使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0898d-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="0898d-133">執行和測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="0898d-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="0898d-134">建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="0898d-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="0898d-135">在第一個工作中，您要建立一個 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 方案內含必要的參考，以建置並執行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="0898d-135">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="0898d-136">若要建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="0898d-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="0898d-137">在[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="0898d-137">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="0898d-138">在**專案類型**窗格**新專案**對話方塊中，按一下  **Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="0898d-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="0898d-139">在 [範本]  窗格中，按一下 [Windows Form 應用程式] 。</span><span class="sxs-lookup"><span data-stu-id="0898d-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="0898d-140">在**名稱**方塊中，輸入**SprocOnlyApp**。</span><span class="sxs-lookup"><span data-stu-id="0898d-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="0898d-141">在**位置**方塊中，確認您要儲存專案檔。</span><span class="sxs-lookup"><span data-stu-id="0898d-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="0898d-142">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="0898d-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="0898d-143">Windows Forms 設計工具隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0898d-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="0898d-144">加入 LINQ to SQL 組件參考</span><span class="sxs-lookup"><span data-stu-id="0898d-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="0898d-145">標準 [Windows Form 應用程式] 範本不包含 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="0898d-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="0898d-146">您必須按照下列步驟所述自行加入組件：</span><span class="sxs-lookup"><span data-stu-id="0898d-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="0898d-147">若要加入 System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="0898d-147">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="0898d-148">在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="0898d-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="0898d-149">在**加入參考**對話方塊中，按一下  **.NET**，按一下 System.Data.Linq 組件，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0898d-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0898d-150">組件隨即加入至專案。</span><span class="sxs-lookup"><span data-stu-id="0898d-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="0898d-151">將 Northwind 程式碼檔案加入至專案</span><span class="sxs-lookup"><span data-stu-id="0898d-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="0898d-152">這個步驟假設您已使用 SqlMetal 工具，從 Northwind 範例資料庫產生程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="0898d-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="0898d-153">如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。</span><span class="sxs-lookup"><span data-stu-id="0898d-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="0898d-154">若要將 Northwind 程式碼檔案加入至專案</span><span class="sxs-lookup"><span data-stu-id="0898d-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="0898d-155">在**專案**功能表上，按一下 **加入現有項目**。</span><span class="sxs-lookup"><span data-stu-id="0898d-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="0898d-156">在**加入現有項目**對話方塊中，移至 c:\linqtest7\northwind.cs，，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="0898d-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="0898d-157">northwind.cs 檔案會加入至專案。</span><span class="sxs-lookup"><span data-stu-id="0898d-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="0898d-158">建立資料庫連接</span><span class="sxs-lookup"><span data-stu-id="0898d-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="0898d-159">在這個步驟中，您會定義與 Northwind 範例資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="0898d-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="0898d-160">這個逐步解說會使用 "c:\linqtest7\northwnd.mdf" 做為路徑。</span><span class="sxs-lookup"><span data-stu-id="0898d-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="0898d-161">若要建立資料庫連接</span><span class="sxs-lookup"><span data-stu-id="0898d-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="0898d-162">在**方案總管] 中**，以滑鼠右鍵按一下**Form1.cs**，然後按一下 [**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="0898d-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="0898d-163">將下列程式碼輸入至 `Form1` 類別中：</span><span class="sxs-lookup"><span data-stu-id="0898d-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="0898d-164">設定使用者介面</span><span class="sxs-lookup"><span data-stu-id="0898d-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="0898d-165">在這項工作中，您會設定可供使用者執行預存程序的介面，以便存取資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="0898d-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="0898d-166">在使用這個逐步解說開發的應用程式中，使用者唯有使用應用程式內嵌的預存程序，才可以存取資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="0898d-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="0898d-167">若要設定使用者介面</span><span class="sxs-lookup"><span data-stu-id="0898d-167">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="0898d-168">返回 Windows Form 設計工具 (**form1.cs [design]**)。</span><span class="sxs-lookup"><span data-stu-id="0898d-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2.  <span data-ttu-id="0898d-169">在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="0898d-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="0898d-170">工具箱隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0898d-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0898d-171">按一下**自動隱藏**圖釘，保持工具箱 中開啟，當您執行的剩餘時這一節的步驟。</span><span class="sxs-lookup"><span data-stu-id="0898d-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="0898d-172">將兩個按鈕、 兩個文字方塊和兩個標籤從工具箱拖曳至拖曳**Form1**。</span><span class="sxs-lookup"><span data-stu-id="0898d-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="0898d-173">如附圖所示排列控制項。</span><span class="sxs-lookup"><span data-stu-id="0898d-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="0898d-174">展開**Form1** ，讓控制項輕易納入。</span><span class="sxs-lookup"><span data-stu-id="0898d-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="0898d-175">以滑鼠右鍵按一下**label1**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="0898d-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="0898d-176">變更**文字**屬性從**label1**至**輸入 OrderID:**。</span><span class="sxs-lookup"><span data-stu-id="0898d-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="0898d-177">相同的方式對**label2**，變更**文字**屬性從**label2**至**輸入 CustomerID:**。</span><span class="sxs-lookup"><span data-stu-id="0898d-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="0898d-178">同樣地，在變更**文字**屬性**button1**至**Order Details**。</span><span class="sxs-lookup"><span data-stu-id="0898d-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="0898d-179">變更**文字**屬性**button2**至**訂單記錄**。</span><span class="sxs-lookup"><span data-stu-id="0898d-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="0898d-180">使按鈕控制項變寬，才能看見所有文字。</span><span class="sxs-lookup"><span data-stu-id="0898d-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="0898d-181">若要處理按鈕按一下動作</span><span class="sxs-lookup"><span data-stu-id="0898d-181">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="0898d-182">按兩下**Order Details**上**Form1**程式碼編輯器中開啟 button1 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0898d-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2.  <span data-ttu-id="0898d-183">將下列程式碼輸入到 `button1` 處理常式中：</span><span class="sxs-lookup"><span data-stu-id="0898d-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  <span data-ttu-id="0898d-184">現在按兩下**button2**上**Form1**開啟`button2`處理常式</span><span class="sxs-lookup"><span data-stu-id="0898d-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4.  <span data-ttu-id="0898d-185">將下列程式碼輸入到 `button2` 處理常式中：</span><span class="sxs-lookup"><span data-stu-id="0898d-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="0898d-186">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="0898d-186">Testing the Application</span></span>  
 <span data-ttu-id="0898d-187">現在開始測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0898d-187">Now it is time to test your application.</span></span> <span data-ttu-id="0898d-188">請注意，您與資料存放區的接觸受限於這兩個預存程序可以採取的所有動作。</span><span class="sxs-lookup"><span data-stu-id="0898d-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="0898d-189">這些動作是為了傳回任何您輸入之 orderID 所含的產品，或傳回任何您輸入之 CustomerID 所訂購的產品記錄。</span><span class="sxs-lookup"><span data-stu-id="0898d-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="0898d-190">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="0898d-190">To test the application</span></span>  
  
1.  <span data-ttu-id="0898d-191">按 F5 鍵啟動偵錯作業。</span><span class="sxs-lookup"><span data-stu-id="0898d-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="0898d-192">Form1 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0898d-192">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="0898d-193">在**輸入 OrderID**方塊中，輸入`10249`，然後按一下  **Order Details**。</span><span class="sxs-lookup"><span data-stu-id="0898d-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="0898d-194">訊息方塊會列出訂單 10249 中所含的產品。</span><span class="sxs-lookup"><span data-stu-id="0898d-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="0898d-195">按一下**確定**以關閉訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="0898d-195">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="0898d-196">在**輸入 CustomerID**方塊中，輸入`ALFKI`，然後按一下 **訂單記錄**。</span><span class="sxs-lookup"><span data-stu-id="0898d-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="0898d-197">出現的訊息方塊會列出客戶 ALFKI 的訂單記錄。</span><span class="sxs-lookup"><span data-stu-id="0898d-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="0898d-198">按一下**確定**以關閉訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="0898d-198">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="0898d-199">在**輸入 OrderID**方塊中，輸入`123`，然後按一下  **Order Details**。</span><span class="sxs-lookup"><span data-stu-id="0898d-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="0898d-200">出現的訊息方塊會顯示 "No results."</span><span class="sxs-lookup"><span data-stu-id="0898d-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="0898d-201">按一下**確定**以關閉訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="0898d-201">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="0898d-202">在**偵錯**功能表上，按一下 **停止偵錯**。</span><span class="sxs-lookup"><span data-stu-id="0898d-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="0898d-203">偵錯工作階段 (Session) 隨即關閉。</span><span class="sxs-lookup"><span data-stu-id="0898d-203">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="0898d-204">如果您已完成實驗，您可以按一下**關閉專案**上**檔案**功能表上，並儲存您的專案，當系統提示您。</span><span class="sxs-lookup"><span data-stu-id="0898d-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0898d-205">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0898d-205">Next Steps</span></span>  
 <span data-ttu-id="0898d-206">您可以進行一些變更，以強化這個專案。</span><span class="sxs-lookup"><span data-stu-id="0898d-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="0898d-207">例如，您可以在清單方塊中列出可用的預存程序，讓使用者選取所要執行的程序。</span><span class="sxs-lookup"><span data-stu-id="0898d-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="0898d-208">您也可以將報表輸出送至文字檔。</span><span class="sxs-lookup"><span data-stu-id="0898d-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0898d-209">請參閱</span><span class="sxs-lookup"><span data-stu-id="0898d-209">See Also</span></span>  
 [<span data-ttu-id="0898d-210">依逐步解說學習</span><span class="sxs-lookup"><span data-stu-id="0898d-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="0898d-211">預存程序</span><span class="sxs-lookup"><span data-stu-id="0898d-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
