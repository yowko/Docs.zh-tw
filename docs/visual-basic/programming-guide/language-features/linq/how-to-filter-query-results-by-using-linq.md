---
title: 作法：使用 LINQ （Visual Basic）篩選查詢結果
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
ms.openlocfilehash: 1250f2fe0ccd7661b9bc1986000143ec4a15a9f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053282"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="48aea-102">HOW TO：使用 LINQ （Visual Basic）篩選查詢結果</span><span class="sxs-lookup"><span data-stu-id="48aea-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="48aea-103">語言整合式查詢（LINQ）可讓您輕鬆地存取資料庫資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="48aea-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>

<span data-ttu-id="48aea-104">下列範例示範如何建立新的應用程式，以對 SQL Server 資料庫執行查詢，並使用`Where`子句依特定值來篩選結果。</span><span class="sxs-lookup"><span data-stu-id="48aea-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="48aea-105">如需詳細資訊，請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="48aea-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>

<span data-ttu-id="48aea-106">本主題中的範例會使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="48aea-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="48aea-107">如果您的開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載。</span><span class="sxs-lookup"><span data-stu-id="48aea-107">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="48aea-108">如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="48aea-108">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="48aea-109">建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="48aea-109">To create a connection to a database</span></span>

1. <span data-ttu-id="48aea-110">在 Visual Studio 中，按一下 [ **View** ] 功能表上的 [**伺服器總管**/**資料庫總管**] 來開啟**伺服器總管**/**資料庫總管**。</span><span class="sxs-lookup"><span data-stu-id="48aea-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>

2. <span data-ttu-id="48aea-111">以滑鼠右鍵按一下**伺服器總管**/**資料庫總管**中的 [**資料連線**]，然後按一下 [**新增連接**]。</span><span class="sxs-lookup"><span data-stu-id="48aea-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>

3. <span data-ttu-id="48aea-112">請指定與 Northwind 範例資料庫的有效連接。</span><span class="sxs-lookup"><span data-stu-id="48aea-112">Specify a valid connection to the Northwind sample database.</span></span>

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="48aea-113">若要加入包含 LINQ to SQL 檔案的專案</span><span class="sxs-lookup"><span data-stu-id="48aea-113">To add a project that contains a LINQ to SQL file</span></span>

1. <span data-ttu-id="48aea-114">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="48aea-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="48aea-115">選取 [Visual Basic **Windows Forms 應用程式**] 做為 [專案類型]。</span><span class="sxs-lookup"><span data-stu-id="48aea-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>

2. <span data-ttu-id="48aea-116">在 [專案] 功能表中，按一下 [加入新項目]。</span><span class="sxs-lookup"><span data-stu-id="48aea-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="48aea-117">選取 [ **LINQ to SQL 類別**] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="48aea-117">Select the **LINQ to SQL Classes** item template.</span></span>

3. <span data-ttu-id="48aea-118">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="48aea-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="48aea-119">按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="48aea-119">Click **Add**.</span></span> <span data-ttu-id="48aea-120">[物件關聯式設計工具（O/R 設計工具）] 會針對 northwind .dbml 檔案開啟。</span><span class="sxs-lookup"><span data-stu-id="48aea-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>

## <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="48aea-121">若要將資料表加入至 O/R 設計工具以進行查詢</span><span class="sxs-lookup"><span data-stu-id="48aea-121">To add tables to query to the O/R Designer</span></span>

1. <span data-ttu-id="48aea-122">在**伺服器總管**/**資料庫總管**中，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="48aea-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="48aea-123">展開 [**資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="48aea-123">Expand the **Tables** folder.</span></span>

     <span data-ttu-id="48aea-124">如果您已經關閉 O/R 設計工具，可以按兩下先前加入的 northwind 檔案來重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="48aea-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>

2. <span data-ttu-id="48aea-125">按一下 [Customers] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="48aea-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="48aea-126">按一下 [Orders] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="48aea-126">Click the Orders table and drag it to the left pane of the designer.</span></span>

     <span data-ttu-id="48aea-127">設計工具會為`Customer`您`Order`的專案建立新的和物件。</span><span class="sxs-lookup"><span data-stu-id="48aea-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="48aea-128">請注意，設計工具會自動偵測資料表之間的關聯性，並建立相關物件的子屬性。</span><span class="sxs-lookup"><span data-stu-id="48aea-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="48aea-129">例如，IntelliSense 會顯示`Customer`物件`Orders`具有與該客戶相關之所有訂單的屬性。</span><span class="sxs-lookup"><span data-stu-id="48aea-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>

3. <span data-ttu-id="48aea-130">儲存您的變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="48aea-130">Save your changes and close the designer.</span></span>

4. <span data-ttu-id="48aea-131">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="48aea-131">Save your project.</span></span>

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="48aea-132">若要加入程式碼以查詢資料庫並顯示結果</span><span class="sxs-lookup"><span data-stu-id="48aea-132">To add code to query the database and display the results</span></span>

1. <span data-ttu-id="48aea-133">從 [**工具箱**] 中， <xref:System.Windows.Forms.DataGridView>將控制項拖曳至專案的預設 Windows Form （Form1）。</span><span class="sxs-lookup"><span data-stu-id="48aea-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>

2. <span data-ttu-id="48aea-134">按兩下 [Form1]，將程式碼`Load`加入表單的事件中。</span><span class="sxs-lookup"><span data-stu-id="48aea-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>

3. <span data-ttu-id="48aea-135">當您將資料表加入至 O/R 設計工具時，設計工具<xref:System.Data.Linq.DataContext>會為您的專案加入物件。</span><span class="sxs-lookup"><span data-stu-id="48aea-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="48aea-136">除了每個資料表的個別物件和集合之外，此物件還包含存取這些資料表所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="48aea-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="48aea-137">專案<xref:System.Data.Linq.DataContext>的物件會根據 .dbml 檔案的名稱來命名。</span><span class="sxs-lookup"><span data-stu-id="48aea-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="48aea-138">針對此專案，物件<xref:System.Data.Linq.DataContext>的名稱`northwindDataContext`為。</span><span class="sxs-lookup"><span data-stu-id="48aea-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>

    <span data-ttu-id="48aea-139">您可以在程式碼中建立<xref:System.Data.Linq.DataContext>的實例，並查詢 O/R 設計工具所指定的資料表。</span><span class="sxs-lookup"><span data-stu-id="48aea-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>

    <span data-ttu-id="48aea-140">將下列程式碼`Load`加入至事件，以查詢公開為數據內容屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="48aea-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="48aea-141">查詢會篩選結果，並只傳回位於`London`的客戶。</span><span class="sxs-lookup"><span data-stu-id="48aea-141">The query filters the results and returns only customers that are located in `London`.</span></span>

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. <span data-ttu-id="48aea-142">按 F5 執行您的專案並查看結果。</span><span class="sxs-lookup"><span data-stu-id="48aea-142">Press F5 to run your project and view the results.</span></span>

5. <span data-ttu-id="48aea-143">以下是一些您可以嘗試的其他篩選準則。</span><span class="sxs-lookup"><span data-stu-id="48aea-143">Following are some other filters that you can try.</span></span>

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a><span data-ttu-id="48aea-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48aea-144">See also</span></span>

- [<span data-ttu-id="48aea-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="48aea-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="48aea-146">查詢</span><span class="sxs-lookup"><span data-stu-id="48aea-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="48aea-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="48aea-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="48aea-148">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="48aea-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
