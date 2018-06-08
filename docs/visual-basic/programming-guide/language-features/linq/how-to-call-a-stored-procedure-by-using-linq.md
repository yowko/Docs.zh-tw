---
title: 如何：使用 LINQ 呼叫預存程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 8aad85ce3369f84e82100072bccf389b03c38221
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826915"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="d8e3d-102">如何：使用 LINQ 呼叫預存程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8e3d-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="d8e3d-103">Language Integrated Query (LINQ) 可讓您更容易存取的資料庫資訊，包括資料庫物件，例如預存程序。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="d8e3d-104">下列範例會示範如何建立 SQL Server 資料庫中呼叫預存程序的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="d8e3d-105">此範例示範如何在資料庫中呼叫兩個不同的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="d8e3d-106">每個程序會傳回查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="d8e3d-107">一個程序會採用輸入的參數，以及其他程序不接受參數。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="d8e3d-108">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="d8e3d-109">如果您在開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="d8e3d-110">如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="d8e3d-111">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="d8e3d-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="d8e3d-112">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**伺服器總管**/**資料庫總管**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="d8e3d-113">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下 **加入連接**。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="d8e3d-114">指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="d8e3d-115">包含 LINQ to SQL 檔案加入專案</span><span class="sxs-lookup"><span data-stu-id="d8e3d-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="d8e3d-116">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="d8e3d-117">選取 Visual Basic **Windows Forms 應用程式**專案類型。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="d8e3d-118">在 [專案]  功能表中，按一下 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="d8e3d-119">選取**LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="d8e3d-120">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="d8e3d-121">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-121">Click **Add**.</span></span> <span data-ttu-id="d8e3d-122">物件關聯式設計工具 （O/R 設計工具） 會開啟 northwind.dbml 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="d8e3d-123">若要加入至 O/R 設計工具的預存程序</span><span class="sxs-lookup"><span data-stu-id="d8e3d-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="d8e3d-124">在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="d8e3d-125">展開**預存程序**資料夾。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="d8e3d-126">如果您關閉 O/R 設計工具，您可以按兩下您先前加入的 northwind.dbml 檔案重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="d8e3d-127">按一下**依年份銷售**預存程序，並將它拖曳至設計工具的右窗格。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="d8e3d-128">按一下**十個最高成本商品**預存程序將它拖曳至設計工具的右窗格。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="d8e3d-129">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="d8e3d-130">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="d8e3d-131">加入程式碼以顯示預存程序的結果</span><span class="sxs-lookup"><span data-stu-id="d8e3d-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="d8e3d-132">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>到您的專案，Form1 的預設值的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="d8e3d-133">按兩下 Form1 以將程式碼加入其`Load`事件。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="d8e3d-134">當您加入至 O/R 設計工具的預存程序時，在設計工具加入<xref:System.Data.Linq.DataContext>專案物件。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="d8e3d-135">此物件包含的程式碼，您必須存取這些程序。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="d8e3d-136"><xref:System.Data.Linq.DataContext>物件的專案名稱為根據的.dbml 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="d8e3d-137">針對此專案，<xref:System.Data.Linq.DataContext>物件命名為`northwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="d8e3d-138">您可以建立的執行個體<xref:System.Data.Linq.DataContext>O/R 設計工具所指定程式碼與呼叫中的預存程序的方法。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="d8e3d-139">繫結至<xref:System.Windows.Forms.DataGridView>物件，您可能要強制立即執行，藉由呼叫查詢<xref:System.Linq.Enumerable.ToList%2A>預存程序的結果上的方法。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="d8e3d-140">將下列程式碼加入`Load`呼叫其中一個做為資料內容的方法公開預存程序的事件。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]  
    [!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]  
  
4.  <span data-ttu-id="d8e3d-141">按 F5 執行您的專案，並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="d8e3d-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e3d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8e3d-142">See Also</span></span>  
 [<span data-ttu-id="d8e3d-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="d8e3d-143">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="d8e3d-144">查詢</span><span class="sxs-lookup"><span data-stu-id="d8e3d-144">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d8e3d-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d8e3d-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="d8e3d-146">DataContext 方法 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="d8e3d-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="d8e3d-147">如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="d8e3d-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
