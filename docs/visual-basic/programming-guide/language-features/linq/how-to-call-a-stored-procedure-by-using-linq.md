---
title: 如何：使用 LINQ 呼叫預存程序
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 7e5fecf0c4c0d3a561ec7d0c4ac03c9d9ce7f759
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075131"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="4f068-102">如何：使用 LINQ 呼叫預存程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f068-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="4f068-103"> (LINQ) 的語言整合式查詢，可讓您輕鬆地存取資料庫資訊，包括資料庫物件，例如預存程式。</span><span class="sxs-lookup"><span data-stu-id="4f068-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="4f068-104">下列範例示範如何建立在 SQL Server 資料庫中呼叫預存程式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f068-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="4f068-105">此範例會示範如何在資料庫中呼叫兩個不同的預存程式。</span><span class="sxs-lookup"><span data-stu-id="4f068-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="4f068-106">每個程式都會傳回查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="4f068-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="4f068-107">其中一個程式採用輸入參數，而另一個程式不接受參數。</span><span class="sxs-lookup"><span data-stu-id="4f068-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="4f068-108">本主題中的範例會使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="4f068-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="4f068-109">如果您的開發電腦上沒有這個資料庫，則可以從 Microsoft 下載中心下載。</span><span class="sxs-lookup"><span data-stu-id="4f068-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="4f068-110">如需相關指示，請參閱 [下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="4f068-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="4f068-111">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="4f068-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="4f068-112">在 Visual Studio 中， **Server Explorer** / 按一下 [View] 功能表上的 [**伺服器總管**資料庫總管來開啟伺服器總管**資料庫總管** / **Database Explorer** 。 **View**</span><span class="sxs-lookup"><span data-stu-id="4f068-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="4f068-113">以滑鼠右鍵按一下**伺服器總管**資料庫總管中的 [**資料連線**] / **Database Explorer** ，然後按一下 [**加入連接**]。</span><span class="sxs-lookup"><span data-stu-id="4f068-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="4f068-114">請指定與 Northwind 範例資料庫的有效連接。</span><span class="sxs-lookup"><span data-stu-id="4f068-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="4f068-115">若要加入包含 LINQ to SQL 檔案的專案</span><span class="sxs-lookup"><span data-stu-id="4f068-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="4f068-116">在 Visual Studio **的 [檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。</span><span class="sxs-lookup"><span data-stu-id="4f068-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="4f068-117">選取 Visual Basic **Windows Forms 應用程式** 做為專案類型。</span><span class="sxs-lookup"><span data-stu-id="4f068-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="4f068-118">在 [專案]\*\*\*\* 功能表上，按一下 [加入新項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f068-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4f068-119">選取 [ **LINQ to SQL 類別** ] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="4f068-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="4f068-120">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="4f068-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="4f068-121">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="4f068-121">Click **Add**.</span></span> <span data-ttu-id="4f068-122">物件關聯式設計工具的 (O/R 設計工具) 會針對 northwind 檔案開啟。</span><span class="sxs-lookup"><span data-stu-id="4f068-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="4f068-123">若要將預存程式加入至 O/R 設計工具</span><span class="sxs-lookup"><span data-stu-id="4f068-123">To add stored procedures to the O/R Designer</span></span>  
  
1. <span data-ttu-id="4f068-124">在**伺服器總管** / **資料庫總管**中，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="4f068-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="4f068-125">展開 **[預存程序]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4f068-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="4f068-126">如果您已關閉 O/R 設計工具，您可以按兩下先前加入的 northwind 檔案來重新開啟它。</span><span class="sxs-lookup"><span data-stu-id="4f068-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="4f068-127">按一下 [ **依年份的銷售** ] 預存程式，並將它拖曳至設計工具的右窗格。</span><span class="sxs-lookup"><span data-stu-id="4f068-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="4f068-128">按一下 **十個最便宜的產品** 預存程式，將它拖曳到設計工具的右窗格中。</span><span class="sxs-lookup"><span data-stu-id="4f068-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3. <span data-ttu-id="4f068-129">儲存您的變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="4f068-129">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="4f068-130">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="4f068-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="4f068-131">加入程式碼以顯示預存程式的結果</span><span class="sxs-lookup"><span data-stu-id="4f068-131">To add code to display the results of the stored procedures</span></span>  
  
1. <span data-ttu-id="4f068-132">從 [ **工具箱**] 中，將 <xref:System.Windows.Forms.DataGridView> 控制項拖曳至專案的預設 Windows 表單（Form1）。</span><span class="sxs-lookup"><span data-stu-id="4f068-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="4f068-133">按兩下 [Form1]，將程式碼新增至其 `Load` 事件。</span><span class="sxs-lookup"><span data-stu-id="4f068-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3. <span data-ttu-id="4f068-134">當您將預存程式加入至 O/R 設計工具時，設計工具會 <xref:System.Data.Linq.DataContext> 為您的專案新增物件。</span><span class="sxs-lookup"><span data-stu-id="4f068-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="4f068-135">此物件包含存取這些程式所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f068-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="4f068-136"><xref:System.Data.Linq.DataContext>專案的物件會根據 .dbml 檔的名稱命名。</span><span class="sxs-lookup"><span data-stu-id="4f068-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="4f068-137">針對此專案， <xref:System.Data.Linq.DataContext> 會將物件命名為 `northwindDataContext` 。</span><span class="sxs-lookup"><span data-stu-id="4f068-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="4f068-138">您可以 <xref:System.Data.Linq.DataContext> 在程式碼中建立的實例，並呼叫 O/R 設計工具所指定的預存程式方法。</span><span class="sxs-lookup"><span data-stu-id="4f068-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="4f068-139">若要系 <xref:System.Windows.Forms.DataGridView> 結至物件，您可能必須 <xref:System.Linq.Enumerable.ToList%2A> 在預存程式的結果上呼叫方法，以強制立即執行查詢。</span><span class="sxs-lookup"><span data-stu-id="4f068-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="4f068-140">將下列程式碼加入至 `Load` 事件，以針對您的資料內容，呼叫公開為方法的其中一個預存程式。</span><span class="sxs-lookup"><span data-stu-id="4f068-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. <span data-ttu-id="4f068-141">按 F5 執行您的專案，並查看結果。</span><span class="sxs-lookup"><span data-stu-id="4f068-141">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f068-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f068-142">See also</span></span>

- [<span data-ttu-id="4f068-143">LINQ</span><span class="sxs-lookup"><span data-stu-id="4f068-143">LINQ</span></span>](index.md)
- [<span data-ttu-id="4f068-144">查詢</span><span class="sxs-lookup"><span data-stu-id="4f068-144">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="4f068-145">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4f068-145">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="4f068-146">DataContext 方法 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="4f068-146">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="4f068-147">如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)</span><span class="sxs-lookup"><span data-stu-id="4f068-147">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
