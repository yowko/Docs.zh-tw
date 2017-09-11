---
title: "如何︰ 將 LINQ 查詢結果傳回成特定的類型 (Visual Basic) |Microsoft 文件"
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
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: 8
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
ms.openlocfilehash: ecbc691a0afeb7ba631949684a0457d9bcdb2728
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="94b5b-102">如何：將 LINQ 查詢結果當做特定類型傳回 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94b5b-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="94b5b-103">語言整合查詢 (LINQ) 可讓您輕鬆地存取資料庫的資訊並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="94b5b-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="94b5b-104">根據預設，LINQ 查詢會傳回匿名型別為物件的清單。</span><span class="sxs-lookup"><span data-stu-id="94b5b-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="94b5b-105">您也可以指定查詢傳回特定型別的清單，使用`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="94b5b-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="94b5b-106">下列範例示範如何建立新的應用程式，以執行針對 SQL Server 資料庫的查詢，並將結果投射成特定的具名類型。</span><span class="sxs-lookup"><span data-stu-id="94b5b-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="94b5b-107">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)和[Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="94b5b-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="94b5b-108">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="94b5b-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="94b5b-109">如果您的開發電腦上沒有 Northwind 範例資料庫，您可以下載從[Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)網站。</span><span class="sxs-lookup"><span data-stu-id="94b5b-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="94b5b-110">如需指示，請參閱[下載範例資料庫](https://msdn.microsoft.com/library/bb399411)。</span><span class="sxs-lookup"><span data-stu-id="94b5b-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="94b5b-111">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="94b5b-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="94b5b-112">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="94b5b-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="94b5b-113">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**然後按一下 **加入連接**。</span><span class="sxs-lookup"><span data-stu-id="94b5b-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="94b5b-114">指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="94b5b-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="94b5b-115">若要將專案加入包含 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="94b5b-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="94b5b-116">在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="94b5b-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="94b5b-117">選取 Visual Basic **Windows Form 應用程式**做為專案類型。</span><span class="sxs-lookup"><span data-stu-id="94b5b-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="94b5b-118">在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。</span><span class="sxs-lookup"><span data-stu-id="94b5b-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="94b5b-119">選取**LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="94b5b-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="94b5b-120">將檔案命名`northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="94b5b-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="94b5b-121">按一下 [加入] ****。</span><span class="sxs-lookup"><span data-stu-id="94b5b-121">Click **Add**.</span></span> <span data-ttu-id="94b5b-122">Northwind.dbml 檔案的開啟物件關聯式設計工具 （O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="94b5b-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="94b5b-123">若要將資料表加入至查詢至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="94b5b-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="94b5b-124">在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="94b5b-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="94b5b-125">展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="94b5b-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="94b5b-126">如果您已關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="94b5b-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="94b5b-127">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="94b5b-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="94b5b-128">設計工具建立新`Customer`物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="94b5b-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="94b5b-129">您可以投射查詢結果做為`Customer`類型或為您建立的型別。</span><span class="sxs-lookup"><span data-stu-id="94b5b-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="94b5b-130">此範例會在稍後的程序中建立新的型別，以及投射查詢結果為該型別。</span><span class="sxs-lookup"><span data-stu-id="94b5b-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="94b5b-131">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="94b5b-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="94b5b-132">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="94b5b-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="94b5b-133">加入程式碼來查詢資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="94b5b-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="94b5b-134">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>控制項拖曳到預設的 Windows Form 專案，Form1。</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="94b5b-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="94b5b-135">按兩下 Form1 以修改要屬於 Form1 類別。</span><span class="sxs-lookup"><span data-stu-id="94b5b-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="94b5b-136">之後`End Class`Form1 類別的陳述式加入下列程式碼來建立`CustomerInfo`來容納此範例的查詢結果的類型。</span><span class="sxs-lookup"><span data-stu-id="94b5b-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     <span data-ttu-id="94b5b-137">[!code-vb[VbLINQToSQLHowTos #&16;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="94b5b-137">[!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]</span></span>  
  
4.  <span data-ttu-id="94b5b-138">當您新增資料表至 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件至您的專案。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="94b5b-138">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="94b5b-139">此物件包含的程式碼，您必須擁有存取這些資料表，以及存取個別物件和集合的每個資料表。</span><span class="sxs-lookup"><span data-stu-id="94b5b-139">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="94b5b-140"><xref:System.Data.Linq.DataContext>物件針對您的專案名為基礎的.dbml 檔案名稱。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="94b5b-140">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="94b5b-141">針對此專案，<xref:System.Data.Linq.DataContext>物件名為`northwindDataContext`。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="94b5b-141">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="94b5b-142">您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼和查詢中的資料表。</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="94b5b-142">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="94b5b-143">在`Load`Form1 類別的事件新增下列程式碼來查詢公開為屬性的資料內容的資料表。</span><span class="sxs-lookup"><span data-stu-id="94b5b-143">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="94b5b-144">`Select`會建立新的查詢子句`CustomerInfo`型別，而不是每個項目查詢結果的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="94b5b-144">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     <span data-ttu-id="94b5b-145">[!code-vb[VbLINQToSQLHowTos #&15;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="94b5b-145">[!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]</span></span>  
  
5.  <span data-ttu-id="94b5b-146">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="94b5b-146">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b5b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94b5b-147">See Also</span></span>  
 <span data-ttu-id="94b5b-148">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="94b5b-148">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="94b5b-149"> [查詢](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="94b5b-149"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="94b5b-150"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="94b5b-150"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="94b5b-151"> [DataContext 方法 （O/R 設計工具）](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="94b5b-151"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

