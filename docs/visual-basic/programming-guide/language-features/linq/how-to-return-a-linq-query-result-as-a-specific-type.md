---
title: 如何：將 LINQ 查詢結果當做特定類型傳回
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: c8ed792bf3ffefd903d60522f621958e44546d32
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404948"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="7b4a8-102">如何：將 LINQ 查詢結果當做特定類型傳回 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b4a8-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="7b4a8-103">語言整合式查詢（LINQ）可讓您輕鬆地存取資料庫資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="7b4a8-104">根據預設，LINQ 查詢會傳回物件的清單做為匿名型別。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="7b4a8-105">您也可以使用子句，指定查詢傳回特定類型的清單 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="7b4a8-106">下列範例示範如何建立新的應用程式，以對 SQL Server 資料庫執行查詢，並將結果投射為特定的命名類型。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="7b4a8-107">如需詳細資訊，請參閱[匿名型別](../objects-and-classes/anonymous-types.md)和[Select 子句](../../../language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-107">For more information, see [Anonymous Types](../objects-and-classes/anonymous-types.md) and [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="7b4a8-108">本主題中的範例會使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="7b4a8-109">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="7b4a8-110">如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="7b4a8-111">建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="7b4a8-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="7b4a8-112">在 Visual Studio 中， **Server Explorer** / **Database Explorer**按一下**Server Explorer** / [ **View** ] 功能表上的 [伺服器總管**資料庫總管**] 來開啟伺服器總管資料庫總管。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="7b4a8-113">以滑鼠右鍵按一下**伺服器總管**資料庫總管中的 [**資料連線**] / **Database Explorer** ，然後按一下 [**新增連接**]。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="7b4a8-114">請指定與 Northwind 範例資料庫的有效連接。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="7b4a8-115">若要加入包含 LINQ to SQL 檔案的專案</span><span class="sxs-lookup"><span data-stu-id="7b4a8-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="7b4a8-116">**在 Visual Studio 的 [檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="7b4a8-117">選取 [Visual Basic **Windows Forms 應用程式**] 做為 [專案類型]。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="7b4a8-118">在 [專案]\*\*\*\* 功能表上，按一下 [加入新項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="7b4a8-119">選取 [ **LINQ to SQL 類別**] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="7b4a8-120">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="7b4a8-121">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-121">Click **Add**.</span></span> <span data-ttu-id="7b4a8-122">[物件關聯式設計工具（O/R 設計工具）] 會針對 northwind .dbml 檔案開啟。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="7b4a8-123">若要將資料表加入至 O/R 設計工具以進行查詢</span><span class="sxs-lookup"><span data-stu-id="7b4a8-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="7b4a8-124">在**伺服器總管** / **資料庫總管**中，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="7b4a8-125">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="7b4a8-126">如果您已經關閉 O/R 設計工具，可以按兩下先前加入的 northwind 檔案來重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="7b4a8-127">按一下 [Customers] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="7b4a8-128">設計工具會為您的專案建立新的 `Customer` 物件。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="7b4a8-129">您可以將查詢結果投影為 `Customer` 類型，或做為您所建立的類型。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="7b4a8-130">這個範例會在稍後的程式中建立新的型別，並將查詢結果投影為該型別。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="7b4a8-131">儲存您的變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="7b4a8-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="7b4a8-133">若要加入程式碼以查詢資料庫並顯示結果</span><span class="sxs-lookup"><span data-stu-id="7b4a8-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="7b4a8-134">從 [**工具箱**] 中，將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows Form （Form1）。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="7b4a8-135">按兩下 [Form1] 以修改 Form1 類別。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="7b4a8-136">在 `End Class` Form1 類別的語句後面，加入下列程式碼來建立類型， `CustomerInfo` 以保存此範例的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="7b4a8-137">當您將資料表加入至 O/R 設計工具時，設計工具會將 <xref:System.Data.Linq.DataContext> 物件加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="7b4a8-138">這個物件包含存取這些資料表所需的程式碼，以及存取每個資料表的個別物件和集合。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="7b4a8-139"><xref:System.Data.Linq.DataContext>專案的物件會根據 .dbml 檔案的名稱來命名。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="7b4a8-140">針對此專案， <xref:System.Data.Linq.DataContext> 物件的名稱為 `northwindDataContext` 。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="7b4a8-141">您可以 <xref:System.Data.Linq.DataContext> 在程式碼中建立的實例，並查詢 O/R 設計工具所指定的資料表。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="7b4a8-142">在 `Load` Form1 類別的事件中，加入下列程式碼來查詢公開為數據內容屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="7b4a8-143">`Select`查詢的子句會 `CustomerInfo` 針對查詢結果的每個專案，建立新的類型，而不是匿名型別。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="7b4a8-144">按 F5 執行您的專案並查看結果。</span><span class="sxs-lookup"><span data-stu-id="7b4a8-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b4a8-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b4a8-145">See also</span></span>

- [<span data-ttu-id="7b4a8-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="7b4a8-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="7b4a8-147">查詢</span><span class="sxs-lookup"><span data-stu-id="7b4a8-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="7b4a8-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7b4a8-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="7b4a8-149">DataCoNtext 方法（O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="7b4a8-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
