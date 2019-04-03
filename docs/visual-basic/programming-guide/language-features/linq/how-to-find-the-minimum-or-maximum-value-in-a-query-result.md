---
title: HOW TO：查詢結果中尋找最小值或最大值，使用 LINQ (Visual Basic)
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
ms.openlocfilehash: 311ba2d9c4be75e77cf134bf44dc96eab957736d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838166"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="9a278-102">HOW TO：查詢結果中尋找最小值或最大值，使用 LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a278-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="9a278-103">Language Integrated Query (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="9a278-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="9a278-104">下列範例示範如何建立新的應用程式會執行對 SQL Server 資料庫的查詢。</span><span class="sxs-lookup"><span data-stu-id="9a278-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="9a278-105">此範例使用決定結果的最小和最大值`Aggregate`和`Group By`子句。</span><span class="sxs-lookup"><span data-stu-id="9a278-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="9a278-106">如需詳細資訊，請參閱 <<c0> [ 彙總子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)並[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="9a278-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="9a278-107">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="9a278-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="9a278-108">如果您的開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。</span><span class="sxs-lookup"><span data-stu-id="9a278-108">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="9a278-109">如需相關指示，請參閱 <<c0> [ 下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="9a278-109">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="9a278-110">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="9a278-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="9a278-111">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫檔案總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="9a278-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="9a278-112">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下**加入連接**。</span><span class="sxs-lookup"><span data-stu-id="9a278-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="9a278-113">請指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="9a278-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="9a278-114">若要將專案加入包含 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="9a278-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="9a278-115">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="9a278-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="9a278-116">選取 Visual Basic **Windows Forms 應用程式**作為專案類型。</span><span class="sxs-lookup"><span data-stu-id="9a278-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="9a278-117">在 [專案]  功能表中，按一下 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="9a278-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="9a278-118">選取  **LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="9a278-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="9a278-119">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="9a278-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="9a278-120">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="9a278-120">Click **Add**.</span></span> <span data-ttu-id="9a278-121">Northwind.dbml 檔案會開啟 物件關聯式設計工具 （O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="9a278-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="9a278-122">若要將資料表加入至查詢至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="9a278-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="9a278-123">在 **伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="9a278-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="9a278-124">依序展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="9a278-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="9a278-125">如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="9a278-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="9a278-126">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="9a278-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="9a278-127">按一下 [Orders] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="9a278-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="9a278-128">設計工具建立新`Customer`和`Order`物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="9a278-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="9a278-129">請注意，設計工具會自動偵測資料表之間的關聯性並建立的子系相關物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9a278-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="9a278-130">例如，IntelliSense 會顯示`Customer`物件具有`Orders`該客戶所有訂單的屬性相關。</span><span class="sxs-lookup"><span data-stu-id="9a278-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="9a278-131">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="9a278-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="9a278-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="9a278-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="9a278-133">加入程式碼來查詢資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="9a278-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="9a278-134">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到您的專案，Form1 的預設 Windows 表單。</span><span class="sxs-lookup"><span data-stu-id="9a278-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="9a278-135">按兩下 Form1 以將程式碼加入`Load`形式的事件。</span><span class="sxs-lookup"><span data-stu-id="9a278-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="9a278-136">當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="9a278-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="9a278-137">此物件包含的程式碼，您必須存取這些資料表，除了個別的物件和每個資料表的集合。</span><span class="sxs-lookup"><span data-stu-id="9a278-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="9a278-138"><xref:System.Data.Linq.DataContext>物件您專案的名稱為根據的.dbml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a278-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="9a278-139">此專案而言<xref:System.Data.Linq.DataContext>物件會命名為`northwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="9a278-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="9a278-140">您可以建立的執行個體<xref:System.Data.Linq.DataContext>資料表指定 O/R 設計工具在您的程式碼和查詢。</span><span class="sxs-lookup"><span data-stu-id="9a278-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="9a278-141">將下列程式碼加入`Load`事件。</span><span class="sxs-lookup"><span data-stu-id="9a278-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="9a278-142">此程式碼會查詢公開為資料內容的屬性，並決定結果的最小和最大值的資料表。</span><span class="sxs-lookup"><span data-stu-id="9a278-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="9a278-143">此範例會使用他`Aggregate`子句，以單一的結果，查詢和`Group By`子句，以顯示平均值分組結果。</span><span class="sxs-lookup"><span data-stu-id="9a278-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4.  <span data-ttu-id="9a278-144">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="9a278-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a278-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a278-145">See also</span></span>

- [<span data-ttu-id="9a278-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="9a278-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="9a278-147">查詢</span><span class="sxs-lookup"><span data-stu-id="9a278-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="9a278-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9a278-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="9a278-149">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="9a278-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
