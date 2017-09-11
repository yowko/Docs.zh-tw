---
title: "如何︰ 使用 LINQ (Visual Basic) 查詢結果中找到的最小或最大值 |Microsoft 文件"
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
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
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
ms.openlocfilehash: 76f5ad02dc79bf8447ae0656c0ea90b5d9bb8edc
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="3797a-102">如何：使用 LINQ 尋找查詢結果中的最小或最大值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3797a-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="3797a-103">語言整合查詢 (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="3797a-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="3797a-104">下列範例示範如何建立新的應用程式執行的 SQL Server 資料庫的查詢。</span><span class="sxs-lookup"><span data-stu-id="3797a-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="3797a-105">此範例使用決定結果的最小和最大值`Aggregate`和`Group By`子句。</span><span class="sxs-lookup"><span data-stu-id="3797a-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="3797a-106">如需詳細資訊，請參閱[Aggregate 子句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)和[By 子句群組](../../../../visual-basic/language-reference/queries/group-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="3797a-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="3797a-107">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3797a-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="3797a-108">如果您的開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)網站。</span><span class="sxs-lookup"><span data-stu-id="3797a-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="3797a-109">如需指示，請參閱[下載範例資料庫](https://msdn.microsoft.com/library/bb399411)。</span><span class="sxs-lookup"><span data-stu-id="3797a-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="3797a-110">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="3797a-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="3797a-111">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="3797a-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="3797a-112">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**然後按一下 **加入連接**。</span><span class="sxs-lookup"><span data-stu-id="3797a-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="3797a-113">指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="3797a-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="3797a-114">若要將專案加入包含 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="3797a-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="3797a-115">在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="3797a-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="3797a-116">選取 Visual Basic **Windows Form 應用程式**做為專案類型。</span><span class="sxs-lookup"><span data-stu-id="3797a-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="3797a-117">在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。</span><span class="sxs-lookup"><span data-stu-id="3797a-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="3797a-118">選取**LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="3797a-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="3797a-119">將檔案命名`northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="3797a-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="3797a-120">按一下 [加入] ****。</span><span class="sxs-lookup"><span data-stu-id="3797a-120">Click **Add**.</span></span> <span data-ttu-id="3797a-121">Northwind.dbml 檔案的開啟物件關聯式設計工具 （O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="3797a-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="3797a-122">若要將資料表加入至查詢至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="3797a-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="3797a-123">在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="3797a-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="3797a-124">展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="3797a-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="3797a-125">如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="3797a-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="3797a-126">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="3797a-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="3797a-127">按一下 「 訂單 」 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="3797a-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="3797a-128">設計工具建立新`Customer`和`Order`物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="3797a-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="3797a-129">請注意，在設計工具會自動偵測資料表之間的關聯性和建立子物件相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="3797a-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="3797a-130">例如，IntelliSense 會顯示，`Customer`物件具有`Orders`該客戶相關的所有訂單的屬性。</span><span class="sxs-lookup"><span data-stu-id="3797a-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="3797a-131">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="3797a-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="3797a-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="3797a-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="3797a-133">加入程式碼來查詢資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="3797a-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="3797a-134">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到預設的 Windows Form 專案，Form1。</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="3797a-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="3797a-135">按兩下 Form1 加入程式碼以`Load`形式的事件。</span><span class="sxs-lookup"><span data-stu-id="3797a-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="3797a-136">當您新增資料表至 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件，為您的專案。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="3797a-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="3797a-137">此物件包含的程式碼，您必須存取這些資料表，以及個別物件和集合的每個資料表。</span><span class="sxs-lookup"><span data-stu-id="3797a-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="3797a-138"><xref:System.Data.Linq.DataContext>物件針對您的專案名為基礎的.dbml 檔案名稱。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="3797a-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="3797a-139">針對此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="3797a-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="3797a-140">您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="3797a-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="3797a-141">加入下列程式碼以`Load`事件。</span><span class="sxs-lookup"><span data-stu-id="3797a-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="3797a-142">此程式碼會查詢公開為屬性的資料內容，並決定結果的最小和最大值的資料表。</span><span class="sxs-lookup"><span data-stu-id="3797a-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="3797a-143">此範例會使用他`Aggregate`子句來查詢單一的結果，而`Group By`子句來顯示平均值分組結果。</span><span class="sxs-lookup"><span data-stu-id="3797a-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     <span data-ttu-id="3797a-144">[!code-vb[VbLINQToSQLHowTos #&14;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3797a-144">[!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]</span></span>  
  
4.  <span data-ttu-id="3797a-145">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="3797a-145">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3797a-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3797a-146">See Also</span></span>  
 <span data-ttu-id="3797a-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="3797a-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="3797a-148"> [查詢](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="3797a-148"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="3797a-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="3797a-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="3797a-150"> [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="3797a-150"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

