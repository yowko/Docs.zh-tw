---
title: 如何：使用 LINQ 計算、加總或平均資料
ms.date: 07/20/2015
helpviewer_keywords:
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause [Visual Basic]
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
ms.openlocfilehash: 7e105c75653f979f53567ef49f1f4cdeafaa4d0f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345015"
---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="b2b08-102">如何：使用 LINQ 統計、加總或平均資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2b08-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="b2b08-103">語言整合式查詢（LINQ）可讓您輕鬆地存取資料庫資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="b2b08-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="b2b08-104">下列範例示範如何建立新的應用程式，以對 SQL Server 資料庫執行查詢。</span><span class="sxs-lookup"><span data-stu-id="b2b08-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="b2b08-105">此範例會使用 `Aggregate` 和 `Group By` 子句來計算結果的總和，並求平均值。</span><span class="sxs-lookup"><span data-stu-id="b2b08-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="b2b08-106">如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[Group by 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b08-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="b2b08-107">本主題中的範例會使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="b2b08-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="b2b08-108">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。</span><span class="sxs-lookup"><span data-stu-id="b2b08-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="b2b08-109">如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b08-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="b2b08-110">建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="b2b08-110">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="b2b08-111">在 Visual Studio 中，按一下 [**視圖**]**功能表上的**[**伺服器總管**/資料庫總管]，開啟**伺服器總管**/**資料庫總管**。</span><span class="sxs-lookup"><span data-stu-id="b2b08-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="b2b08-112">以滑鼠右鍵按一下**伺服器總管**/**資料庫總管**中的 [**資料連線**]，然後按一下 [**新增連接**]。</span><span class="sxs-lookup"><span data-stu-id="b2b08-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="b2b08-113">請指定與 Northwind 範例資料庫的有效連接。</span><span class="sxs-lookup"><span data-stu-id="b2b08-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="b2b08-114">若要加入包含 LINQ to SQL 檔案的專案</span><span class="sxs-lookup"><span data-stu-id="b2b08-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="b2b08-115">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="b2b08-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="b2b08-116">選取 [Visual Basic **Windows Forms 應用程式**] 做為 [專案類型]。</span><span class="sxs-lookup"><span data-stu-id="b2b08-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="b2b08-117">在 [專案] 功能表中，按一下 [加入新項目]。</span><span class="sxs-lookup"><span data-stu-id="b2b08-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="b2b08-118">選取 [ **LINQ to SQL 類別**] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="b2b08-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="b2b08-119">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="b2b08-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="b2b08-120">按一下 [加入]。</span><span class="sxs-lookup"><span data-stu-id="b2b08-120">Click **Add**.</span></span> <span data-ttu-id="b2b08-121">[物件關聯式設計工具（O/R 設計工具）] 會針對 northwind .dbml 檔案開啟。</span><span class="sxs-lookup"><span data-stu-id="b2b08-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="b2b08-122">若要將資料表加入至 O/R 設計工具以進行查詢</span><span class="sxs-lookup"><span data-stu-id="b2b08-122">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="b2b08-123">在**伺服器總管**/**資料庫總管**中，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="b2b08-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="b2b08-124">展開 [**資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b2b08-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="b2b08-125">如果您已經關閉 O/R 設計工具，可以按兩下先前加入的 northwind 檔案來重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="b2b08-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="b2b08-126">按一下 [Customers] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="b2b08-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="b2b08-127">按一下 [Orders] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="b2b08-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="b2b08-128">設計工具會為您的專案建立新的 `Customer` 和 `Order` 物件。</span><span class="sxs-lookup"><span data-stu-id="b2b08-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="b2b08-129">請注意，設計工具會自動偵測資料表之間的關聯性，並建立相關物件的子屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b08-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="b2b08-130">例如，IntelliSense 會顯示 `Customer` 物件具有與該客戶相關之所有訂單的 `Orders` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b08-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="b2b08-131">儲存您的變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="b2b08-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="b2b08-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="b2b08-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="b2b08-133">若要加入程式碼以查詢資料庫並顯示結果</span><span class="sxs-lookup"><span data-stu-id="b2b08-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="b2b08-134">從 [**工具箱**] 中，將 [<xref:System.Windows.Forms.DataGridView>] 控制項拖曳至您的專案 [Form1] 的預設 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="b2b08-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="b2b08-135">按兩下 [Form1]，將程式碼加入表單的 `Load` 事件。</span><span class="sxs-lookup"><span data-stu-id="b2b08-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="b2b08-136">當您將資料表加入至 O/R 設計工具時，設計工具會為您的專案加入 <xref:System.Data.Linq.DataContext> 物件。</span><span class="sxs-lookup"><span data-stu-id="b2b08-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="b2b08-137">這個物件包含存取這些資料表所需的程式碼，以及存取每個資料表的個別物件和集合。</span><span class="sxs-lookup"><span data-stu-id="b2b08-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="b2b08-138">專案的 <xref:System.Data.Linq.DataContext> 物件是根據 .dbml 檔案的名稱來命名。</span><span class="sxs-lookup"><span data-stu-id="b2b08-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="b2b08-139">針對此專案，<xref:System.Data.Linq.DataContext> 物件的名稱為 `northwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="b2b08-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="b2b08-140">您可以在程式碼中建立 <xref:System.Data.Linq.DataContext> 的實例，並查詢 O/R 設計工具所指定的資料表。</span><span class="sxs-lookup"><span data-stu-id="b2b08-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="b2b08-141">將下列程式碼新增至 `Load` 事件，以查詢公開為 <xref:System.Data.Linq.DataContext> 屬性的資料表，以及計算結果的計數、總和和平均值。</span><span class="sxs-lookup"><span data-stu-id="b2b08-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="b2b08-142">此範例會使用 `Aggregate` 子句來查詢單一結果，而 `Group By` 子句會顯示群組結果的平均值。</span><span class="sxs-lookup"><span data-stu-id="b2b08-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form6.vb#13)]  
  
4. <span data-ttu-id="b2b08-143">按 F5 執行您的專案並查看結果。</span><span class="sxs-lookup"><span data-stu-id="b2b08-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b08-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2b08-144">See also</span></span>

- [<span data-ttu-id="b2b08-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="b2b08-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="b2b08-146">查詢</span><span class="sxs-lookup"><span data-stu-id="b2b08-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b2b08-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b2b08-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="b2b08-148">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="b2b08-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="b2b08-149">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="b2b08-149">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="b2b08-150">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="b2b08-150">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
