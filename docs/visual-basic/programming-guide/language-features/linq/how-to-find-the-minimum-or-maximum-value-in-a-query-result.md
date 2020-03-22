---
title: 如何：使用 LINQ 尋找查詢結果中的最小或最大值
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112358"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="7fefb-102">如何：使用 LINQ 尋找查詢結果中的最小或最大值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fefb-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="7fefb-103">語言集成查詢 （LINQ） 使訪問資料庫資訊和執行查詢變得容易。</span><span class="sxs-lookup"><span data-stu-id="7fefb-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="7fefb-104">下面的示例演示如何創建執行針對 SQL Server 資料庫的查詢的新應用程式。</span><span class="sxs-lookup"><span data-stu-id="7fefb-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="7fefb-105">該示例通過使用`Aggregate`和`Group By`子句確定結果的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="7fefb-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="7fefb-106">有關詳細資訊，請參閱[聚合子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[按子句分組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="7fefb-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="7fefb-107">本主題中的示例使用北風示例資料庫。</span><span class="sxs-lookup"><span data-stu-id="7fefb-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="7fefb-108">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。</span><span class="sxs-lookup"><span data-stu-id="7fefb-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="7fefb-109">有關說明，請參閱[下載示例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="7fefb-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a><span data-ttu-id="7fefb-110">創建與資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="7fefb-110">Create a connection to a database</span></span>  
  
1. <span data-ttu-id="7fefb-111">在視覺化工作室中，通過按一下 **"視圖"** 功能表上**的伺服器資源管理器**/**資料庫資源管理器**打開**伺服器資源管理器**/**資料庫資源管理器**。</span><span class="sxs-lookup"><span data-stu-id="7fefb-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="7fefb-112">按右鍵**伺服器資源管理器**/**資料庫資源管理器**中**的資料連線**，然後按一下"**添加連接**"。</span><span class="sxs-lookup"><span data-stu-id="7fefb-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="7fefb-113">指定到北風樣本資料庫的有效連接。</span><span class="sxs-lookup"><span data-stu-id="7fefb-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="7fefb-114">將包含 LINQ 的專案添加到 SQL 檔</span><span class="sxs-lookup"><span data-stu-id="7fefb-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="7fefb-115">在視覺化工作室中，在 **"檔"** 功能表上，指向 **"新建"，** 然後按一下"**專案**"。</span><span class="sxs-lookup"><span data-stu-id="7fefb-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="7fefb-116">選擇視覺化基本**視窗表單應用程式**作為專案類型。</span><span class="sxs-lookup"><span data-stu-id="7fefb-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="7fefb-117">在 [專案]\*\*\*\* 功能表上，按一下 [加入新項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7fefb-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="7fefb-118">選擇**LINQ 到 SQL 類**項範本。</span><span class="sxs-lookup"><span data-stu-id="7fefb-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="7fefb-119">開啟 `northwind.dbml` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7fefb-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="7fefb-120">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="7fefb-120">Click **Add**.</span></span> <span data-ttu-id="7fefb-121">為北風.dbml 檔打開物件關係設計器（O/R 設計器）。</span><span class="sxs-lookup"><span data-stu-id="7fefb-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
## <a name="add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="7fefb-122">將表添加到 O/R 設計器</span><span class="sxs-lookup"><span data-stu-id="7fefb-122">Add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="7fefb-123">在**伺服器資源管理器**/**資料庫資源管理器中**，展開與北風資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="7fefb-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="7fefb-124">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7fefb-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="7fefb-125">如果已關閉 O/R 設計器，則可以通過按兩下之前添加的 Northwind.dbml 檔重新打開它。</span><span class="sxs-lookup"><span data-stu-id="7fefb-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="7fefb-126">按一下"客戶"表並將其拖動到設計器的左側窗格。</span><span class="sxs-lookup"><span data-stu-id="7fefb-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="7fefb-127">按一下"訂單"表並將其拖動到設計器的左側窗格。</span><span class="sxs-lookup"><span data-stu-id="7fefb-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="7fefb-128">設計器為專案`Customer`創建新`Order`物件和物件。</span><span class="sxs-lookup"><span data-stu-id="7fefb-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="7fefb-129">請注意，設計器會自動檢測表之間的關係，並為相關物件創建子屬性。</span><span class="sxs-lookup"><span data-stu-id="7fefb-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="7fefb-130">例如，IntelliSense 將顯示`Customer`該物件具有與該客戶`Orders`相關的所有訂單的屬性。</span><span class="sxs-lookup"><span data-stu-id="7fefb-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="7fefb-131">保存更改並關閉設計器。</span><span class="sxs-lookup"><span data-stu-id="7fefb-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="7fefb-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="7fefb-132">Save your project.</span></span>  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="7fefb-133">添加代碼以查詢資料庫並顯示結果</span><span class="sxs-lookup"><span data-stu-id="7fefb-133">Add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="7fefb-134">從**工具箱**中<xref:System.Windows.Forms.DataGridView>，將控制項拖動到專案的預設 Windows 表單表單 Form1。</span><span class="sxs-lookup"><span data-stu-id="7fefb-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="7fefb-135">按兩下 Form1 可向表單`Load`的事件添加代碼。</span><span class="sxs-lookup"><span data-stu-id="7fefb-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="7fefb-136">將表添加到 O/R 設計器時，設計器會<xref:System.Data.Linq.DataContext>為專案添加物件。</span><span class="sxs-lookup"><span data-stu-id="7fefb-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="7fefb-137">除了每個表的各個物件和集合之外，此物件還包含訪問這些表必須具有的代碼。</span><span class="sxs-lookup"><span data-stu-id="7fefb-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="7fefb-138">專案<xref:System.Data.Linq.DataContext>的物件是根據 .dbml 檔的名稱命名的。</span><span class="sxs-lookup"><span data-stu-id="7fefb-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="7fefb-139">對於此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="7fefb-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="7fefb-140">您可以在代碼中創建 的<xref:System.Data.Linq.DataContext>實例，並查詢 O/R 設計器指定的表。</span><span class="sxs-lookup"><span data-stu-id="7fefb-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="7fefb-141">將以下代碼添加到事件`Load`。</span><span class="sxs-lookup"><span data-stu-id="7fefb-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="7fefb-142">此代碼查詢作為資料上下文的屬性公開的表，並確定結果的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="7fefb-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="7fefb-143">該示例使用`Aggregate`子句查詢單個結果，`Group By`子句顯示分組結果的平均值。</span><span class="sxs-lookup"><span data-stu-id="7fefb-143">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. <span data-ttu-id="7fefb-144">按**F5**運行專案並查看結果。</span><span class="sxs-lookup"><span data-stu-id="7fefb-144">Press **F5** to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fefb-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fefb-145">See also</span></span>

- [<span data-ttu-id="7fefb-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="7fefb-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="7fefb-147">查詢</span><span class="sxs-lookup"><span data-stu-id="7fefb-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="7fefb-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7fefb-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="7fefb-149">資料上下文方法（O/R 設計器）</span><span class="sxs-lookup"><span data-stu-id="7fefb-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
