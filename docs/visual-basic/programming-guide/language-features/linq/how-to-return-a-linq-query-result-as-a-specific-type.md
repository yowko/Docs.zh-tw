---
title: HOW TO：將 LINQ 查詢結果傳回成特定的類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 5ccd71d93185f9478f6720419369df713d590c39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334935"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="3c505-102">HOW TO：將 LINQ 查詢結果傳回成特定的類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c505-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="3c505-103">Language Integrated Query (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="3c505-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="3c505-104">根據預設，LINQ 查詢會傳回非匿名型別物件的清單。</span><span class="sxs-lookup"><span data-stu-id="3c505-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="3c505-105">您也可以指定查詢傳回特定型別的清單，使用`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="3c505-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="3c505-106">下列範例示範如何建立新的應用程式會執行對 SQL Server 資料庫的查詢，並將結果投射成特定的具名類型。</span><span class="sxs-lookup"><span data-stu-id="3c505-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="3c505-107">如需詳細資訊，請參閱 <<c0> [ 匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)並[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="3c505-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="3c505-108">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c505-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="3c505-109">如果您的開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。</span><span class="sxs-lookup"><span data-stu-id="3c505-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="3c505-110">如需相關指示，請參閱 <<c0> [ 下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="3c505-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="3c505-111">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="3c505-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="3c505-112">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫檔案總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="3c505-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="3c505-113">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下**加入連接**。</span><span class="sxs-lookup"><span data-stu-id="3c505-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="3c505-114">請指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c505-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="3c505-115">若要將專案加入包含 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="3c505-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="3c505-116">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="3c505-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="3c505-117">選取 Visual Basic **Windows Forms 應用程式**作為專案類型。</span><span class="sxs-lookup"><span data-stu-id="3c505-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="3c505-118">在 [專案]  功能表中，按一下 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="3c505-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="3c505-119">選取  **LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="3c505-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="3c505-120">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="3c505-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="3c505-121">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="3c505-121">Click **Add**.</span></span> <span data-ttu-id="3c505-122">Northwind.dbml 檔案會開啟 物件關聯式設計工具 （O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="3c505-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="3c505-123">若要將資料表加入至查詢至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="3c505-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="3c505-124">在 **伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="3c505-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="3c505-125">依序展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="3c505-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="3c505-126">如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="3c505-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="3c505-127">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="3c505-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="3c505-128">設計工具建立新`Customer`物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="3c505-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="3c505-129">您可以投影查詢結果當做`Customer`類型或為您建立的型別。</span><span class="sxs-lookup"><span data-stu-id="3c505-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="3c505-130">此範例會在稍後的程序中建立新的類型，並在投射查詢結果為該型別。</span><span class="sxs-lookup"><span data-stu-id="3c505-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="3c505-131">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="3c505-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="3c505-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="3c505-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="3c505-133">加入程式碼來查詢資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="3c505-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="3c505-134">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到您的專案，Form1 的預設 Windows 表單。</span><span class="sxs-lookup"><span data-stu-id="3c505-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="3c505-135">按兩下 Form1 以修改，在 Form1 類別。</span><span class="sxs-lookup"><span data-stu-id="3c505-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="3c505-136">在後`End Class`陳述式，在 Form1 類別，新增下列程式碼，以建立`CustomerInfo`保存此範例的查詢結果的型別。</span><span class="sxs-lookup"><span data-stu-id="3c505-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="3c505-137">當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件加入專案。</span><span class="sxs-lookup"><span data-stu-id="3c505-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="3c505-138">此物件包含的程式碼，您必須擁有存取這些資料表，以及存取個別的物件和每個資料表的集合。</span><span class="sxs-lookup"><span data-stu-id="3c505-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="3c505-139"><xref:System.Data.Linq.DataContext>物件您專案的名稱為根據的.dbml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c505-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="3c505-140">此專案而言<xref:System.Data.Linq.DataContext>物件會命名為`northwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="3c505-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="3c505-141">您可以建立的執行個體<xref:System.Data.Linq.DataContext>資料表指定 O/R 設計工具在您的程式碼和查詢。</span><span class="sxs-lookup"><span data-stu-id="3c505-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="3c505-142">在 `Load`事件，在 Form1 類別，新增下列程式碼來查詢公開為屬性的資料內容的資料表。</span><span class="sxs-lookup"><span data-stu-id="3c505-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="3c505-143">`Select`會建立新的查詢子句`CustomerInfo`類型而不是每個項目查詢結果的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="3c505-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="3c505-144">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="3c505-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c505-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c505-145">See also</span></span>

- [<span data-ttu-id="3c505-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="3c505-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="3c505-147">查詢</span><span class="sxs-lookup"><span data-stu-id="3c505-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3c505-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3c505-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="3c505-149">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="3c505-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
