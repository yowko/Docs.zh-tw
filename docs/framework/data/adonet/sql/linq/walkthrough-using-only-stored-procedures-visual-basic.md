---
title: 逐步解說：僅使用預存程序 (Visual Basic)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c04fe5e81f19b89de7204ed2430c9acf08ce1647
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="ed4ad-102">逐步解說：僅使用預存程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed4ad-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="ed4ad-103">本逐步解說會針對只用預存程序來存取資料，提供基本的端對端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 案例。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="ed4ad-104">資料庫管理員會使用這個方法來限制對資料存放區的存取。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed4ad-105">妳也可以使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式中的預存程序來覆寫預設行為，特別是針對 `Create`、`Update` 和 `Delete` 處理序。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="ed4ad-106">如需詳細資訊，請參閱[自訂插入、 更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="ed4ad-107">基於本逐步解說的目的，您會使用兩個已對應至 Northwind 範例資料庫中之預存程序的方法：CustOrdersDetail 和 CustOrderHist。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="ed4ad-108">當您執行 SqlMetal 命令列工具來產生 Visual Basic 檔案時，會發生對應。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="ed4ad-109">如需詳細資訊，請參閱本逐步解說後面的「必要條件」一節。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="ed4ad-110">這個逐步解說並不依賴[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="ed4ad-111">使用 Visual Studio 的開發人員也可以使用[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]實作預存程序功能。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="ed4ad-112">請參閱[LINQ to SQL 工具，Visual Studio 中](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="ed4ad-113">這個逐步解說是使用 Visual Basic 開發設定所撰寫。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ed4ad-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="ed4ad-114">Prerequisites</span></span>  
 <span data-ttu-id="ed4ad-115">本逐步解說需要下列項目：</span><span class="sxs-lookup"><span data-stu-id="ed4ad-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="ed4ad-116">本逐步解說會使用專用資料夾 ("c:\linqtest3") 來保存檔案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="ed4ad-117">請先建立這個資料夾，再開始逐步解說。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="ed4ad-118">Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="ed4ad-119">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載網站下載。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="ed4ad-120">如需指示，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="ed4ad-121">下載此資料庫之後，請將 northwnd.mdf 檔複製到 c:\linqtest3 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="ed4ad-122">從 Northwind 資料庫產生的 Visual Basic 程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="ed4ad-123">這個逐步解說是使用 SqlMetal 工具，以下列命令列所撰寫：</span><span class="sxs-lookup"><span data-stu-id="ed4ad-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="ed4ad-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="ed4ad-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="ed4ad-125">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ed4ad-126">總覽</span><span class="sxs-lookup"><span data-stu-id="ed4ad-126">Overview</span></span>  
 <span data-ttu-id="ed4ad-127">此逐步解說包含六個主要工作：</span><span class="sxs-lookup"><span data-stu-id="ed4ad-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="ed4ad-128">設定[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 中的方案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="ed4ad-129">將 System.Data.Linq 組件加入至專案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="ed4ad-130">將資料庫程式碼檔案加入至專案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="ed4ad-131">建立資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="ed4ad-132">設定使用者介面。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="ed4ad-133">執行和測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="ed4ad-134">建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="ed4ad-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="ed4ad-135">在第一個工作中，您可以建立包含必要的參考，建置並執行 Visual Studio 方案[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="ed4ad-136">若要建立 LINQ to SQL 方案</span><span class="sxs-lookup"><span data-stu-id="ed4ad-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="ed4ad-137">在 Visual Studio 的 [檔案]  功能表上，按一下 [新增專案] 。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="ed4ad-138">在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 窗格中，展開 [ **Visual Basic**]，然後按一下 [ **Windows**]。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="ed4ad-139">在 [範本]  窗格中，按一下 [Windows Form 應用程式] 。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="ed4ad-140">在**名稱**方塊中，輸入**SprocOnlyApp**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="ed4ad-141">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="ed4ad-142">Windows Forms 設計工具隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="ed4ad-143">加入 LINQ to SQL 組件參考</span><span class="sxs-lookup"><span data-stu-id="ed4ad-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="ed4ad-144">標準 [Windows Form 應用程式] 範本不包含 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 組件。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="ed4ad-145">您必須按照下列步驟所述自行加入組件：</span><span class="sxs-lookup"><span data-stu-id="ed4ad-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="ed4ad-146">若要加入 System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="ed4ad-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="ed4ad-147">在**方案總管] 中**，按一下 [**顯示所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="ed4ad-148">在**方案總管] 中**，以滑鼠右鍵按一下**參考**，然後按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="ed4ad-149">在**加入參考**對話方塊中，按一下  **.NET**，按一下 System.Data.Linq 組件，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ed4ad-150">組件隨即加入至專案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ed4ad-151">將 Northwind 程式碼檔案加入至專案</span><span class="sxs-lookup"><span data-stu-id="ed4ad-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="ed4ad-152">這個步驟假設您已使用 SqlMetal 工具，從 Northwind 範例資料庫產生程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="ed4ad-153">如需詳細資訊，請參閱本逐步解說稍早的「必要條件」一節。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ed4ad-154">若要將 Northwind 程式碼檔案加入至專案</span><span class="sxs-lookup"><span data-stu-id="ed4ad-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="ed4ad-155">在**專案**功能表上，按一下 **加入現有項目**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="ed4ad-156">在**加入現有項目**對話方塊中，移至 c:\linqtest3\northwind.vb，，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="ed4ad-157">northwind.vb file 隨即加入至專案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="ed4ad-158">建立資料庫連接</span><span class="sxs-lookup"><span data-stu-id="ed4ad-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="ed4ad-159">在這個步驟中，您會定義與 Northwind 範例資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="ed4ad-160">本逐步解說會使用 "c:\linqtest3\northwnd.mdf" 做為路徑。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="ed4ad-161">若要建立資料庫連接</span><span class="sxs-lookup"><span data-stu-id="ed4ad-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="ed4ad-162">在**方案總管] 中**，以滑鼠右鍵按一下**Form1.vb**，然後按一下 [**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="ed4ad-163">`Class Form1` 會顯示在程式碼編輯器中。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-163">`Class Form1` appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="ed4ad-164">在 `Form1` 程式碼區塊中輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ed4ad-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="ed4ad-165">設定使用者介面</span><span class="sxs-lookup"><span data-stu-id="ed4ad-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="ed4ad-166">在這項工作中您會建立介面，供使用者執行預存程序來存取資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="ed4ad-167">在您按照本逐步解說開發的應用程式中，使用者只能透過應用程式內嵌的預存程序來存取資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="ed4ad-168">若要設定使用者介面</span><span class="sxs-lookup"><span data-stu-id="ed4ad-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="ed4ad-169">返回 [Windows Form 設計工具 (**form1.vb]**)。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="ed4ad-170">在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="ed4ad-171">工具箱隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ed4ad-172">按一下**自動隱藏**圖釘，保持工具箱 中開啟，當您執行的剩餘時這一節的步驟。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="ed4ad-173">將兩個按鈕、 兩個文字方塊和兩個標籤從工具箱拖曳至拖曳**Form1**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="ed4ad-174">如附圖所示排列控制項。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="ed4ad-175">展開**Form1** ，讓控制項輕易納入。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="ed4ad-176">以滑鼠右鍵按一下**Label1**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="ed4ad-177">變更**文字**屬性從**Label1**至**輸入 OrderID:**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="ed4ad-178">相同的方式對**Label2**，變更**文字**屬性從**Label2**至**輸入 CustomerID:**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="ed4ad-179">同樣地，在變更**文字**屬性**Button1**至**Order Details**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="ed4ad-180">變更**文字**屬性**Button2**至**訂單記錄**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="ed4ad-181">使按鈕控制項變寬，才能看見所有文字。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="ed4ad-182">若要處理按鈕按一下動作</span><span class="sxs-lookup"><span data-stu-id="ed4ad-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="ed4ad-183">按兩下**Order Details**上**Form1**建立`Button1`事件處理常式並開啟程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="ed4ad-184">將下列程式碼輸入到 `Button1` 處理常式中：</span><span class="sxs-lookup"><span data-stu-id="ed4ad-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="ed4ad-185">現在按兩下**Button2**上建立的 Form1`Button2`事件處理常式並開啟程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="ed4ad-186">將下列程式碼輸入到 `Button2` 處理常式中：</span><span class="sxs-lookup"><span data-stu-id="ed4ad-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="ed4ad-187">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="ed4ad-187">Testing the Application</span></span>  
 <span data-ttu-id="ed4ad-188">現在開始測試您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-188">Now it is time to test your application.</span></span> <span data-ttu-id="ed4ad-189">請注意，您與資料存放區的接觸受限於這兩個預存程序可以採取的所有動作。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="ed4ad-190">這些動作是為了傳回任何您輸入之 orderID 所含的產品，或傳回任何您輸入之 CustomerID 所訂購的產品記錄。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="ed4ad-191">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="ed4ad-191">To test the application</span></span>  
  
1.  <span data-ttu-id="ed4ad-192">按 F5 鍵啟動偵錯作業。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="ed4ad-193">Form1 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="ed4ad-194">在**輸入 OrderID**方塊中，輸入**10249** ，然後按一下  **Order Details**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="ed4ad-195">訊息方塊會列出訂單 10249 中所含的產品。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="ed4ad-196">按一下**確定**以關閉訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="ed4ad-197">在**輸入 CustomerID**方塊中，輸入`ALFKI`，然後按一下 **訂單記錄**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="ed4ad-198">訊息方塊會列出客戶 ALFKI 的訂單記錄。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="ed4ad-199">按一下**確定**以關閉訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="ed4ad-200">在**輸入 OrderID**方塊中，輸入`123`，然後按一下  **Order Details**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="ed4ad-201">訊息方塊會顯示 "No results."</span><span class="sxs-lookup"><span data-stu-id="ed4ad-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="ed4ad-202">按一下**確定**以關閉訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="ed4ad-203">在**偵錯**功能表上，按一下 **停止偵錯**。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="ed4ad-204">偵錯工作階段 (Session) 隨即關閉。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="ed4ad-205">如果您已完成實驗，您可以按一下**關閉專案**上**檔案**功能表上，並儲存您的專案，當系統提示您。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ed4ad-206">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ed4ad-206">Next Steps</span></span>  
 <span data-ttu-id="ed4ad-207">您可以進行一些變更，以強化這個專案。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="ed4ad-208">例如，您可以在清單方塊中列出可用的預存程序，讓使用者選取所要執行的程序。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="ed4ad-209">您也可以將報表輸出送至文字檔。</span><span class="sxs-lookup"><span data-stu-id="ed4ad-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed4ad-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed4ad-210">See Also</span></span>  
 [<span data-ttu-id="ed4ad-211">依逐步解說學習</span><span class="sxs-lookup"><span data-stu-id="ed4ad-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="ed4ad-212">預存程序</span><span class="sxs-lookup"><span data-stu-id="ed4ad-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
