---
title: "如何︰ 使用 LINQ (Visual Basic) 來篩選查詢結果 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: d6197e39ffef5b09b87b1b47cab04d4339bcaf3f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="6ade3-102">如何：使用 LINQ 篩選查詢結果 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ade3-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="6ade3-103">語言整合查詢 (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="6ade3-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="6ade3-104">下列範例示範如何建立新的應用程式，以執行針對 SQL Server 資料庫的查詢，並使用特定的值篩選結果`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="6ade3-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="6ade3-105">如需詳細資訊，請參閱[Where 子句](../../../../visual-basic/language-reference/queries/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="6ade3-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="6ade3-106">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="6ade3-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="6ade3-107">如果您的開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)網站。</span><span class="sxs-lookup"><span data-stu-id="6ade3-107">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="6ade3-108">如需指示，請參閱[下載範例資料庫](https://msdn.microsoft.com/library/bb399411)。</span><span class="sxs-lookup"><span data-stu-id="6ade3-108">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="6ade3-109">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="6ade3-109">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="6ade3-110">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="6ade3-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="6ade3-111">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**然後按一下 **加入連接**。</span><span class="sxs-lookup"><span data-stu-id="6ade3-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="6ade3-112">指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="6ade3-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="6ade3-113">若要將專案加入包含 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="6ade3-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="6ade3-114">在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="6ade3-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="6ade3-115">選取 Visual Basic **Windows Form 應用程式**做為專案類型。</span><span class="sxs-lookup"><span data-stu-id="6ade3-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="6ade3-116">在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。</span><span class="sxs-lookup"><span data-stu-id="6ade3-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="6ade3-117">選取**LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="6ade3-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="6ade3-118">將檔案命名`northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="6ade3-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="6ade3-119">按一下 [加入] ****。</span><span class="sxs-lookup"><span data-stu-id="6ade3-119">Click **Add**.</span></span> <span data-ttu-id="6ade3-120">Northwind.dbml 檔案會開啟 物件關聯式設計工具 （O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="6ade3-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="6ade3-121">若要將資料表加入至查詢至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="6ade3-121">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="6ade3-122">在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="6ade3-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="6ade3-123">展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6ade3-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="6ade3-124">如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="6ade3-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="6ade3-125">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="6ade3-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="6ade3-126">按一下 「 訂單 」 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="6ade3-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="6ade3-127">設計工具建立新`Customer`和`Order`物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="6ade3-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="6ade3-128">請注意，在設計工具會自動偵測資料表之間的關聯性和建立子物件相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ade3-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="6ade3-129">例如，IntelliSense 會顯示，`Customer`物件具有`Orders`該客戶相關的所有訂單的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ade3-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="6ade3-130">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="6ade3-130">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="6ade3-131">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="6ade3-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="6ade3-132">加入程式碼來查詢資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="6ade3-132">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="6ade3-133">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到預設的 Windows Form 專案，Form1。</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="6ade3-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="6ade3-134">按兩下 Form1 加入程式碼以`Load`形式的事件。</span><span class="sxs-lookup"><span data-stu-id="6ade3-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="6ade3-135">當您新增資料表至 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件，為您的專案。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="6ade3-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="6ade3-136">此物件包含的程式碼，您必須存取這些資料表，以及個別物件和集合的每個資料表。</span><span class="sxs-lookup"><span data-stu-id="6ade3-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="6ade3-137"><xref:System.Data.Linq.DataContext>物件針對您的專案名為基礎的.dbml 檔案名稱。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="6ade3-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="6ade3-138">針對此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="6ade3-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="6ade3-139">您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="6ade3-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="6ade3-140">加入下列程式碼以`Load`事件，以查詢公開為屬性的資料內容的資料表。</span><span class="sxs-lookup"><span data-stu-id="6ade3-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="6ade3-141">查詢篩選結果，並傳回位於的客戶`London`。</span><span class="sxs-lookup"><span data-stu-id="6ade3-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     <span data-ttu-id="6ade3-142">[!code-vb[VbLINQToSQLHowTos #&11;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6ade3-142">[!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="6ade3-143">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="6ade3-143">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="6ade3-144">以下是您可以嘗試的一些其他篩選。</span><span class="sxs-lookup"><span data-stu-id="6ade3-144">Following are some other filters that you can try.</span></span>  
  
     <span data-ttu-id="6ade3-145">[!code-vb[VbLINQToSQLHowTos #&12;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6ade3-145">[!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ade3-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ade3-146">See Also</span></span>  
 <span data-ttu-id="6ade3-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ade3-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="6ade3-148"> [查詢](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="6ade3-148"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="6ade3-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="6ade3-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="6ade3-150"> [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="6ade3-150"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

