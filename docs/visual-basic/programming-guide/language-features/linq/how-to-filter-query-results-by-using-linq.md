---
title: HOW TO：使用 LINQ (Visual Basic) 來篩選查詢結果
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: fc4d43ef9181f1a290d37c137b4fc6f7f16588b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001022"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="5fe4a-102">HOW TO：使用 LINQ (Visual Basic) 來篩選查詢結果</span><span class="sxs-lookup"><span data-stu-id="5fe4a-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="5fe4a-103">Language Integrated Query (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="5fe4a-104">下列範例示範如何建立新的應用程式會執行對 SQL Server 資料庫的查詢，並使用依特定值篩選結果`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="5fe4a-105">如需詳細資訊，請參閱 < [Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="5fe4a-106">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="5fe4a-107">如果您的開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="5fe4a-108">如需相關指示，請參閱 <<c0> [ 下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="5fe4a-109">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="5fe4a-109">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="5fe4a-110">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫檔案總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="5fe4a-111">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下**加入連接**。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="5fe4a-112">請指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="5fe4a-113">若要將專案加入包含 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="5fe4a-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="5fe4a-114">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="5fe4a-115">選取 Visual Basic **Windows Forms 應用程式**作為專案類型。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="5fe4a-116">在 [專案]  功能表中，按一下 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="5fe4a-117">選取  **LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="5fe4a-118">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="5fe4a-119">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-119">Click **Add**.</span></span> <span data-ttu-id="5fe4a-120">Northwind.dbml 檔案會開啟 物件關聯式設計工具 （O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="5fe4a-121">若要將資料表加入至查詢至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="5fe4a-121">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="5fe4a-122">在 **伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="5fe4a-123">依序展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="5fe4a-124">如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="5fe4a-125">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="5fe4a-126">按一下 [Orders] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="5fe4a-127">設計工具建立新`Customer`和`Order`物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="5fe4a-128">請注意，設計工具會自動偵測資料表之間的關聯性並建立的子系相關物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="5fe4a-129">例如，IntelliSense 會顯示`Customer`物件具有`Orders`該客戶所有訂單的屬性相關。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3. <span data-ttu-id="5fe4a-130">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-130">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="5fe4a-131">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="5fe4a-132">加入程式碼來查詢資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="5fe4a-132">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="5fe4a-133">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到您的專案，Form1 的預設 Windows 表單。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="5fe4a-134">按兩下 Form1 以將程式碼加入`Load`形式的事件。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3. <span data-ttu-id="5fe4a-135">當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="5fe4a-136">此物件包含的程式碼，您必須存取這些資料表，除了個別的物件和每個資料表的集合。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="5fe4a-137"><xref:System.Data.Linq.DataContext>物件您專案的名稱為根據的.dbml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="5fe4a-138">此專案而言<xref:System.Data.Linq.DataContext>物件會命名為`northwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="5fe4a-139">您可以建立的執行個體<xref:System.Data.Linq.DataContext>資料表指定 O/R 設計工具在您的程式碼和查詢。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="5fe4a-140">將下列程式碼加入`Load`事件來查詢公開為屬性的資料內容的資料表。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="5fe4a-141">查詢會篩選結果，並傳回位於的客戶`London`。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]  
  
4. <span data-ttu-id="5fe4a-142">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-142">Press F5 to run your project and view the results.</span></span>  
  
5. <span data-ttu-id="5fe4a-143">以下是一些您可以嘗試的其他篩選。</span><span class="sxs-lookup"><span data-stu-id="5fe4a-143">Following are some other filters that you can try.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="5fe4a-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fe4a-144">See also</span></span>

- [<span data-ttu-id="5fe4a-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="5fe4a-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="5fe4a-146">查詢</span><span class="sxs-lookup"><span data-stu-id="5fe4a-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="5fe4a-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5fe4a-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="5fe4a-148">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="5fe4a-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
