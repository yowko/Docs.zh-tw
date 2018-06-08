---
title: 如何：使用 LINQ 修改資料庫中的資料 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: 617bb62f9009c507658b5d1262657cb4dfa860e9
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827107"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="b44c8-102">如何：使用 LINQ 修改資料庫中的資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b44c8-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="b44c8-103">Language Integrated Query (LINQ) 查詢，讓您輕鬆存取資料庫的資訊，並修改資料庫中的值。</span><span class="sxs-lookup"><span data-stu-id="b44c8-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="b44c8-104">下列範例顯示如何建立新的應用程式擷取和更新資訊的 SQL Server 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b44c8-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="b44c8-105">本主題中的範例使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="b44c8-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="b44c8-106">如果您在開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。</span><span class="sxs-lookup"><span data-stu-id="b44c8-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="b44c8-107">如需指示，請參閱[下載範例資料庫](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="b44c8-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="b44c8-108">若要建立資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="b44c8-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="b44c8-109">在 Visual Studio 中開啟**伺服器總管**/**資料庫總管**按一下**檢視** 功能表，然後選取**伺服器總管**/**資料庫總管**。</span><span class="sxs-lookup"><span data-stu-id="b44c8-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="b44c8-110">以滑鼠右鍵按一下**資料連接**中**伺服器總管**/**資料庫總管**，然後按一下**加入連接**。</span><span class="sxs-lookup"><span data-stu-id="b44c8-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="b44c8-111">指定有效的連接至 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="b44c8-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="b44c8-112">若要加入在專案中的使用 LINQ to SQL 檔案</span><span class="sxs-lookup"><span data-stu-id="b44c8-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="b44c8-113">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="b44c8-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="b44c8-114">選取 Visual Basic **Windows Forms 應用程式**專案類型。</span><span class="sxs-lookup"><span data-stu-id="b44c8-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="b44c8-115">在 [專案]  功能表中，按一下 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="b44c8-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="b44c8-116">選取**LINQ to SQL 類別**項目範本。</span><span class="sxs-lookup"><span data-stu-id="b44c8-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="b44c8-117">將檔案命名為 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="b44c8-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="b44c8-118">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="b44c8-118">Click **Add**.</span></span> <span data-ttu-id="b44c8-119">物件關聯式設計工具 （O/R 設計工具） 已開啟進行`northwind.dbml`檔案。</span><span class="sxs-lookup"><span data-stu-id="b44c8-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="b44c8-120">若要將資料表加入至查詢及修改設計工具</span><span class="sxs-lookup"><span data-stu-id="b44c8-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="b44c8-121">在**伺服器總管**/**資料庫總管**，展開 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="b44c8-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="b44c8-122">展開**資料表**資料夾。</span><span class="sxs-lookup"><span data-stu-id="b44c8-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="b44c8-123">如果您關閉 O/R 設計工具，您可以重新開啟它按兩下`northwind.dbml`您先前加入的檔案。</span><span class="sxs-lookup"><span data-stu-id="b44c8-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="b44c8-124">按一下 [客戶] 資料表，並將它拖曳至設計工具的左窗格。</span><span class="sxs-lookup"><span data-stu-id="b44c8-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="b44c8-125">在設計工具會建立新的客戶物件，為您的專案。</span><span class="sxs-lookup"><span data-stu-id="b44c8-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="b44c8-126">儲存變更並關閉設計工具。</span><span class="sxs-lookup"><span data-stu-id="b44c8-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="b44c8-127">儲存您的專案。</span><span class="sxs-lookup"><span data-stu-id="b44c8-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="b44c8-128">加入程式碼以修改資料庫，並顯示結果</span><span class="sxs-lookup"><span data-stu-id="b44c8-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="b44c8-129">從**工具箱**，拖曳<xref:System.Windows.Forms.DataGridView>到您的專案，Form1 的預設值的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="b44c8-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="b44c8-130">當您將資料表加入 O/R 設計工具時，設計工具加入<xref:System.Data.Linq.DataContext>物件加入專案。</span><span class="sxs-lookup"><span data-stu-id="b44c8-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="b44c8-131">此物件包含可用來存取 「 客戶 」 資料表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b44c8-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="b44c8-132">它也包含定義區域的客戶物件和資料表的客戶集合的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b44c8-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="b44c8-133"><xref:System.Data.Linq.DataContext>物件針對名為您的專案是根據.dbml 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="b44c8-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="b44c8-134">針對此專案，<xref:System.Data.Linq.DataContext>物件命名為`northwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="b44c8-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="b44c8-135">您可以建立的執行個體<xref:System.Data.Linq.DataContext>物件在您的程式碼和查詢，並修改 O/R 設計工具所指定的客戶集合。</span><span class="sxs-lookup"><span data-stu-id="b44c8-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="b44c8-136">您對客戶集合的變更才會反映資料庫中您藉由呼叫提交<xref:System.Data.Linq.DataContext.SubmitChanges%2A>方法<xref:System.Data.Linq.DataContext>物件。</span><span class="sxs-lookup"><span data-stu-id="b44c8-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="b44c8-137">按兩下 Windows Form，Form1，加入程式碼以<xref:System.Windows.Forms.Form.Load>Customers 資料表，查詢的事件會公開的屬性為您<xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="b44c8-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="b44c8-138">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b44c8-138">Add the following code:</span></span>  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  <span data-ttu-id="b44c8-139">從**工具箱**，將三個<xref:System.Windows.Forms.Button>控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="b44c8-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="b44c8-140">選取第一個`Button`控制項。</span><span class="sxs-lookup"><span data-stu-id="b44c8-140">Select the first `Button` control.</span></span> <span data-ttu-id="b44c8-141">在**屬性**視窗中，將`Name`的`Button`控制權傳輸至`AddButton`和`Text`至`Add`。</span><span class="sxs-lookup"><span data-stu-id="b44c8-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="b44c8-142">選取第二個按鈕，並設定`Name`屬性`UpdateButton`和`Text`屬性`Update`。</span><span class="sxs-lookup"><span data-stu-id="b44c8-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="b44c8-143">選取第三個按鈕，並設定`Name`屬性`DeleteButton`和`Text`屬性`Delete`。</span><span class="sxs-lookup"><span data-stu-id="b44c8-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="b44c8-144">按兩下**新增** 按鈕，將程式碼加入其`Click`事件。</span><span class="sxs-lookup"><span data-stu-id="b44c8-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="b44c8-145">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b44c8-145">Add the following code:</span></span>  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  <span data-ttu-id="b44c8-146">按兩下**更新** 按鈕，將程式碼加入其`Click`事件。</span><span class="sxs-lookup"><span data-stu-id="b44c8-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="b44c8-147">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b44c8-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="b44c8-148">按兩下**刪除** 按鈕，將程式碼加入其`Click`事件。</span><span class="sxs-lookup"><span data-stu-id="b44c8-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="b44c8-149">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b44c8-149">Add the following code:</span></span>  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  <span data-ttu-id="b44c8-150">請按 F5 執行您的專案。</span><span class="sxs-lookup"><span data-stu-id="b44c8-150">Press F5 to run your project.</span></span> <span data-ttu-id="b44c8-151">按一下**新增**新增新的記錄。</span><span class="sxs-lookup"><span data-stu-id="b44c8-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="b44c8-152">按一下**更新**修改新的記錄。</span><span class="sxs-lookup"><span data-stu-id="b44c8-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="b44c8-153">按一下**刪除**刪除新的記錄。</span><span class="sxs-lookup"><span data-stu-id="b44c8-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44c8-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b44c8-154">See Also</span></span>  
 [<span data-ttu-id="b44c8-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="b44c8-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="b44c8-156">查詢</span><span class="sxs-lookup"><span data-stu-id="b44c8-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="b44c8-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="b44c8-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="b44c8-158">DataContext 方法 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="b44c8-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="b44c8-159">如何： 指派預存程序來執行更新、 插入和刪除 （O/R 設計工具）</span><span class="sxs-lookup"><span data-stu-id="b44c8-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
