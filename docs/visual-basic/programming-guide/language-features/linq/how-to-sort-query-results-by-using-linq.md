---
title: "如何︰ 使用 LINQ (Visual Basic) 來排序查詢結果 |Microsoft 文件"
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
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
caps.latest.revision: 5
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
ms.openlocfilehash: 0c728d9e52add00c9d3241a9f598c15eb2db17a5
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="8bf0c-102">如何：使用 LINQ 排序查詢結果 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bf0c-102">How to: Sort Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="8bf0c-103">語言整合查詢 (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="8bf0c-104">下列範例示範如何建立新的應用程式，以執行針對 SQL Server 資料庫的查詢，並使用以排序結果，您可以多個欄位`Order By`子句。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-104">The following example shows how to create a new application that performs queries against a SQL Server database and sorts the results by multiple fields by using the `Order By` clause.</span></span> <span data-ttu-id="8bf0c-105">每個欄位的排序次序可以遞增或遞減順序。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-105">The sort order for each field can be ascending order or descending order.</span></span> <span data-ttu-id="8bf0c-106">如需詳細資訊，請參閱[Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-106">For more information, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="8bf0c-107">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="8bf0c-108">如果您的開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)網站。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="8bf0c-109">如需指示，請參閱[下載範例資料庫](https://msdn.microsoft.com/library/bb399411)。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="8bf0c-110">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="8bf0c-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="8bf0c-111">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="8bf0c-112">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**然後按一下 **加入連接**。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="8bf0c-113">指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="8bf0c-114">若要將專案加入包含 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="8bf0c-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="8bf0c-115">在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="8bf0c-116">選取 Visual Basic **Windows Form 應用程式**做為專案類型。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="8bf0c-117">在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="8bf0c-118">選取**LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="8bf0c-119">將檔案命名`northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="8bf0c-120">按一下 [加入] ****。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-120">Click **Add**.</span></span> <span data-ttu-id="8bf0c-121">Northwind.dbml 檔案的開啟物件關聯式設計工具 （O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="8bf0c-122">若要將資料表加入至查詢至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="8bf0c-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="8bf0c-123">在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="8bf0c-124">展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="8bf0c-125">如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="8bf0c-126">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="8bf0c-127">按一下 「 訂單 」 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="8bf0c-128">設計工具建立新`Customer`和`Order`物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="8bf0c-129">請注意，在設計工具會自動偵測資料表之間的關聯性和建立子物件相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="8bf0c-130">例如，IntelliSense 會顯示，`Customer`物件具有`Orders`該客戶相關的所有訂單的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="8bf0c-131">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="8bf0c-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="8bf0c-133">加入程式碼來查詢資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="8bf0c-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="8bf0c-134">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到預設的 Windows Form 專案，Form1。</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="8bf0c-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="8bf0c-135">按兩下 Form1 加入程式碼以`Load`形式的事件。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="8bf0c-136">當您新增資料表至 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件至您的專案。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bf0c-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="8bf0c-137">此物件包含的程式碼，您必須擁有存取這些資料表，以及存取個別物件和集合的每個資料表。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="8bf0c-138"><xref:System.Data.Linq.DataContext>物件針對您的專案名為基礎的.dbml 檔案名稱。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bf0c-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="8bf0c-139">針對此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bf0c-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="8bf0c-140">您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="8bf0c-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="8bf0c-141">加入下列程式碼以`Load`事件，以查詢公開為屬性的資料內容，並將結果排序的資料表。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context and sort the results.</span></span> <span data-ttu-id="8bf0c-142">查詢的客戶訂單，以遞減順序排序結果。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-142">The query sorts the results by the number of customer orders, in descending order.</span></span> <span data-ttu-id="8bf0c-143">依公司名稱，以遞增順序 （預設值） 排序具有相同數目的訂單的客戶。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-143">Customers that have the same number of orders are ordered by company name in ascending order (the default).</span></span>  
  
     <span data-ttu-id="8bf0c-144">[!code-vb[VbLINQToSQLHowTos #&10;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8bf0c-144">[!code-vb[VbLINQToSQLHowTos#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="8bf0c-145">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="8bf0c-145">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf0c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bf0c-146">See Also</span></span>  
 <span data-ttu-id="8bf0c-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="8bf0c-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="8bf0c-148"> [查詢](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="8bf0c-148"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="8bf0c-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="8bf0c-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="8bf0c-150"> [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="8bf0c-150"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

