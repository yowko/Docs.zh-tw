---
title: "逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c602af6799da57fec904c87da7bed77c0040eff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0642c-102">逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="0642c-102">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0642c-103">從基礎資料存放區的錯誤處理是資料輸入應用程式的必備的功能。</span><span class="sxs-lookup"><span data-stu-id="0642c-103">Handling errors from the underlying data store is a required feature for a data-entry application.</span></span> <span data-ttu-id="0642c-104">Windows Form<xref:System.Windows.Forms.DataGridView>控制項簡化這由公開<xref:System.Windows.Forms.DataGridView.DataError>了條件約束違規或損毀的商務規則，偵測到資料存放區時引發的事件。</span><span class="sxs-lookup"><span data-stu-id="0642c-104">The Windows Forms <xref:System.Windows.Forms.DataGridView> control makes this easy by exposing the <xref:System.Windows.Forms.DataGridView.DataError> event, which is raised when the data store detects a constraint violation or a broken business rule.</span></span>  
  
 <span data-ttu-id="0642c-105">在本逐步解說中，您將會擷取資料列從`Customers`Northwind 範例資料庫中資料表，並顯示在<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="0642c-105">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0642c-106">當重複`CustomerID`值偵測到新的資料列或編輯現有的資料列，<xref:System.Windows.Forms.DataGridView.DataError>就會發生事件，但會處理透過顯示<xref:System.Windows.Forms.MessageBox>，描述例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0642c-106">When a duplicate `CustomerID` value is detected in a new row or an edited existing row, the <xref:System.Windows.Forms.DataGridView.DataError> event will occur, which will be handled by displaying a <xref:System.Windows.Forms.MessageBox> that describes the exception.</span></span>  
  
 <span data-ttu-id="0642c-107">若要為單一列出本主題中複製的程式碼，請參閱[如何： 處理錯誤，就會發生在資料輸入 Windows Form DataGridView 控制項中](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="0642c-107">To copy the code in this topic as a single listing, see [How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0642c-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="0642c-108">Prerequisites</span></span>  
 <span data-ttu-id="0642c-109">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="0642c-109">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="0642c-110">Northwind SQL Server 範例資料庫的伺服器存取。</span><span class="sxs-lookup"><span data-stu-id="0642c-110">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="0642c-111">建立表單</span><span class="sxs-lookup"><span data-stu-id="0642c-111">Creating the Form</span></span>  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a><span data-ttu-id="0642c-112">若要處理 DataGridView 控制項中的資料輸入錯誤</span><span class="sxs-lookup"><span data-stu-id="0642c-112">To handle data-entry errors in the DataGridView control</span></span>  
  
1.  <span data-ttu-id="0642c-113">建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項和<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="0642c-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="0642c-114">下列程式碼範例提供基本的初始化，並包含`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="0642c-114">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  <span data-ttu-id="0642c-115">在您的表單類別定義處理資料庫連接的詳細資料中實作的方法。</span><span class="sxs-lookup"><span data-stu-id="0642c-115">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="0642c-116">這個程式碼範例會使用`GetData`方法會傳回已填入<xref:System.Data.DataTable>物件。</span><span class="sxs-lookup"><span data-stu-id="0642c-116">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="0642c-117">請確定您設定`connectionString`變數的值，適用於您的資料庫。</span><span class="sxs-lookup"><span data-stu-id="0642c-117">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="0642c-118">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="0642c-118">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="0642c-119">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="0642c-119">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="0642c-120">如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="0642c-120">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  <span data-ttu-id="0642c-121">實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>和<xref:System.Windows.Forms.BindingSource>並設定資料繫結。</span><span class="sxs-lookup"><span data-stu-id="0642c-121">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  <span data-ttu-id="0642c-122">處理<xref:System.Windows.Forms.DataGridView.DataError>事件<xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="0642c-122">Handle the <xref:System.Windows.Forms.DataGridView.DataError> event on the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="0642c-123">如果此錯誤的內容是認可作業，顯示中的錯誤<xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="0642c-123">If the context for the error is a commit operation, display the error in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="0642c-124">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="0642c-124">Testing the Application</span></span>  
 <span data-ttu-id="0642c-125">您現在可以測試表單，以確定其如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="0642c-125">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="0642c-126">若要測試表單</span><span class="sxs-lookup"><span data-stu-id="0642c-126">To test the form</span></span>  
  
-   <span data-ttu-id="0642c-127">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0642c-127">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="0642c-128">您會看到<xref:System.Windows.Forms.DataGridView>控制項填滿 Customers 資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="0642c-128">You will see a <xref:System.Windows.Forms.DataGridView> control filled with data from the Customers table.</span></span> <span data-ttu-id="0642c-129">如果您輸入的重複值`CustomerID`和認可編輯，資料格的值將會自動還原，您會看到<xref:System.Windows.Forms.MessageBox>會顯示資料的項目時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0642c-129">If you enter a duplicate value for `CustomerID` and commit the edit, the cell value will revert automatically and you will see a <xref:System.Windows.Forms.MessageBox> that displays the data entry error.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0642c-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0642c-130">Next Steps</span></span>  
 <span data-ttu-id="0642c-131">此應用程式可讓您基本的了解<xref:System.Windows.Forms.DataGridView>控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="0642c-131">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="0642c-132">您可以自訂的外觀和行為<xref:System.Windows.Forms.DataGridView>數種方式控制：</span><span class="sxs-lookup"><span data-stu-id="0642c-132">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="0642c-133">變更框線和標題的樣式。</span><span class="sxs-lookup"><span data-stu-id="0642c-133">Change border and header styles.</span></span> <span data-ttu-id="0642c-134">如需詳細資訊，請參閱[如何： 變更 Windows Form DataGridView 控制項中的格線樣式和框線](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="0642c-134">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="0642c-135">啟用或限制使用者輸入到<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="0642c-135">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0642c-136">如需詳細資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)，和[如何： 使 Windows Form DataGridView 控制項中的資料行唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0642c-136">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="0642c-137">驗證使用者輸入，<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="0642c-137">Validate user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0642c-138">如需詳細資訊，請參閱[逐步解說： 驗證 Windows Form DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0642c-138">For more information, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="0642c-139">處理非常大型的資料集使用的虛擬模式。</span><span class="sxs-lookup"><span data-stu-id="0642c-139">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="0642c-140">如需詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0642c-140">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="0642c-141">自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="0642c-141">Customize the appearance of cells.</span></span> <span data-ttu-id="0642c-142">如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的儲存格外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)和[How to： 設定預設儲存格樣式的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0642c-142">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0642c-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0642c-143">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="0642c-144">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="0642c-144">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0642c-145">操作說明：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="0642c-145">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="0642c-146">逐步解說：驗證 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="0642c-146">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="0642c-147">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="0642c-147">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
