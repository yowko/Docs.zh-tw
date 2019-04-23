---
title: 逐步解說：驗證 Windows Forms DataGridView 控制項的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: a4bf0850b28b7101ba76f1c1fedc6633eccb81a1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59346050"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="123c0-102">逐步解說：驗證 Windows Forms DataGridView 控制項的資料</span><span class="sxs-lookup"><span data-stu-id="123c0-102">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="123c0-103">當您向使用者顯示的項目資料功能時，您經常必須驗證您的表單中輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="123c0-103">When you display data entry functionality to users, you frequently have to validate the data entered into your form.</span></span> <span data-ttu-id="123c0-104"><xref:System.Windows.Forms.DataGridView>類別提供便利的方式，資料就會認可到資料存放區之前先執行驗證。</span><span class="sxs-lookup"><span data-stu-id="123c0-104">The <xref:System.Windows.Forms.DataGridView> class provides a convenient way to perform validation before data is committed to the data store.</span></span> <span data-ttu-id="123c0-105">您可以藉由處理驗證資料<xref:System.Windows.Forms.DataGridView.CellValidating>事件，會引發<xref:System.Windows.Forms.DataGridView>目前儲存格的變更時。</span><span class="sxs-lookup"><span data-stu-id="123c0-105">You can validate data by handling the <xref:System.Windows.Forms.DataGridView.CellValidating> event, which is raised by the <xref:System.Windows.Forms.DataGridView> when the current cell changes.</span></span>  
  
 <span data-ttu-id="123c0-106">在本逐步解說中，您將擷取的資料列`Customers`Northwind 範例資料庫中的表格，以及它們顯示在<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="123c0-106">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="123c0-107">當使用者編輯中的資料格`CompanyName`資料行，嘗試將資料格，保留<xref:System.Windows.Forms.DataGridView.CellValidating>事件處理常式會檢查新的公司名稱字串，以確定它是不是空的; 如果新的值為空字串，<xref:System.Windows.Forms.DataGridView>會造成使用者的資料指標從輸入非空白字串之前，請將儲存格。</span><span class="sxs-lookup"><span data-stu-id="123c0-107">When a user edits a cell in the `CompanyName` column and tries to leave the cell, the <xref:System.Windows.Forms.DataGridView.CellValidating> event handler will examine new company name string to make sure it is not empty; if the new value is an empty string, the <xref:System.Windows.Forms.DataGridView> will prevent the user's cursor from leaving the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="123c0-108">若要將此主題中的程式碼複製為單一清單，請參閱[如何：驗證 Windows Form DataGridView 控制項中的資料](how-to-validate-data-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="123c0-108">To copy the code in this topic as a single listing, see [How to: Validate Data in the Windows Forms DataGridView Control](how-to-validate-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="123c0-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="123c0-109">Prerequisites</span></span>  
 <span data-ttu-id="123c0-110">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="123c0-110">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="123c0-111">存取權可 Northwind SQL Server 範例資料庫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="123c0-111">Access to a server that has the Northwind SQL Server sample database.</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="123c0-112">建立表單</span><span class="sxs-lookup"><span data-stu-id="123c0-112">Creating the Form</span></span>  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a><span data-ttu-id="123c0-113">若要驗證在 DataGridView 中輸入的資料</span><span class="sxs-lookup"><span data-stu-id="123c0-113">To validate data entered in a DataGridView</span></span>  
  
1. <span data-ttu-id="123c0-114">建立衍生自類別<xref:System.Windows.Forms.Form>且包含<xref:System.Windows.Forms.DataGridView>控制項和<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="123c0-114">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     <span data-ttu-id="123c0-115">下列程式碼範例提供基本的初始化，而且包含`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="123c0-115">The following code example provides basic initialization and includes a `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2. <span data-ttu-id="123c0-116">在您的表單類別定義處理資料庫連接的詳細資料中實作的方法。</span><span class="sxs-lookup"><span data-stu-id="123c0-116">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>  
  
     <span data-ttu-id="123c0-117">此程式碼範例會使用`GetData`方法會傳回填入<xref:System.Data.DataTable>物件。</span><span class="sxs-lookup"><span data-stu-id="123c0-117">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="123c0-118">請確定您設定`connectionString`變數的值，適用於您的資料庫。</span><span class="sxs-lookup"><span data-stu-id="123c0-118">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="123c0-119">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="123c0-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="123c0-120">使用 Windows 驗證，也稱為整合式安全性，是更安全的方式，來控制資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="123c0-120">Using Windows Authentication, also known as integrated security, is a more secure way to control access to a database.</span></span> <span data-ttu-id="123c0-121">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="123c0-121">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3. <span data-ttu-id="123c0-122">實作您的表單的處理常式<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>和<xref:System.Windows.Forms.BindingSource>和設定資料繫結。</span><span class="sxs-lookup"><span data-stu-id="123c0-122">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4. <span data-ttu-id="123c0-123">實作的處理常式<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellValidating>和<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件。</span><span class="sxs-lookup"><span data-stu-id="123c0-123">Implement handlers for the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellValidating> and <xref:System.Windows.Forms.DataGridView.CellEndEdit> events.</span></span>  
  
     <span data-ttu-id="123c0-124"><xref:System.Windows.Forms.DataGridView.CellValidating>事件處理常式是在您判定是否在儲存格的值`CompanyName`是空的資料行。</span><span class="sxs-lookup"><span data-stu-id="123c0-124">The <xref:System.Windows.Forms.DataGridView.CellValidating> event handler is where you determine whether the value of a cell in the `CompanyName` column is empty.</span></span> <span data-ttu-id="123c0-125">如果驗證失敗的儲存格的值，設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>的屬性<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>類別`true`。</span><span class="sxs-lookup"><span data-stu-id="123c0-125">If the cell value fails validation, set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property of the <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> class to `true`.</span></span> <span data-ttu-id="123c0-126">這會導致<xref:System.Windows.Forms.DataGridView>以防止資料指標離開儲存格的控制項。</span><span class="sxs-lookup"><span data-stu-id="123c0-126">This causes the <xref:System.Windows.Forms.DataGridView> control to prevent the cursor from leaving the cell.</span></span> <span data-ttu-id="123c0-127">設定<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>說明的字串資料列上的屬性。</span><span class="sxs-lookup"><span data-stu-id="123c0-127">Set the <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> property on the row to an explanatory string.</span></span> <span data-ttu-id="123c0-128">這會顯示錯誤圖示與包含的錯誤文字的工具提示。</span><span class="sxs-lookup"><span data-stu-id="123c0-128">This displays an error icon with a ToolTip that contains the error text.</span></span> <span data-ttu-id="123c0-129">在 <xref:System.Windows.Forms.DataGridView.CellEndEdit>事件處理常式中，設定<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>為空字串的資料列上的屬性。</span><span class="sxs-lookup"><span data-stu-id="123c0-129">In the <xref:System.Windows.Forms.DataGridView.CellEndEdit> event handler, set the <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> property on the row to the empty string.</span></span> <span data-ttu-id="123c0-130"><xref:System.Windows.Forms.DataGridView.CellEndEdit>只儲存格結束編輯模式，它無法這麼做，如果它驗證失敗時，事件就會發生。</span><span class="sxs-lookup"><span data-stu-id="123c0-130">The <xref:System.Windows.Forms.DataGridView.CellEndEdit> event occurs only when the cell exits edit mode, which it cannot do if it fails validation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="123c0-131">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="123c0-131">Testing the Application</span></span>  
 <span data-ttu-id="123c0-132">您現在可以測試表單，以確定它如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="123c0-132">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="123c0-133">若要測試表單</span><span class="sxs-lookup"><span data-stu-id="123c0-133">To test the form</span></span>  
  
-   <span data-ttu-id="123c0-134">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="123c0-134">Compile and run the application.</span></span>  
  
     <span data-ttu-id="123c0-135">您會看到<xref:System.Windows.Forms.DataGridView>填滿資料從`Customers`資料表。</span><span class="sxs-lookup"><span data-stu-id="123c0-135">You will see a <xref:System.Windows.Forms.DataGridView> filled with data from the `Customers` table.</span></span> <span data-ttu-id="123c0-136">當您按兩下中的資料格`CompanyName` 欄中，您可以編輯的值。</span><span class="sxs-lookup"><span data-stu-id="123c0-136">When you double-click a cell in the `CompanyName` column, you can edit the value.</span></span> <span data-ttu-id="123c0-137">如果您刪除所有字元，然後按 TAB 鍵以結束資料格，<xref:System.Windows.Forms.DataGridView>防止您離開。</span><span class="sxs-lookup"><span data-stu-id="123c0-137">If you delete all the characters and hit the TAB key to exit the cell, the <xref:System.Windows.Forms.DataGridView> prevents you from exiting.</span></span> <span data-ttu-id="123c0-138">當您在儲存格中輸入非空白字串<xref:System.Windows.Forms.DataGridView>控制項可讓您結束資料格。</span><span class="sxs-lookup"><span data-stu-id="123c0-138">When you type a non-empty string into the cell, the <xref:System.Windows.Forms.DataGridView> control lets you exit the cell.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="123c0-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="123c0-139">Next Steps</span></span>  
 <span data-ttu-id="123c0-140">此應用程式可讓您的基本了解<xref:System.Windows.Forms.DataGridView>控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="123c0-140">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="123c0-141">您可以自訂外觀和行為<xref:System.Windows.Forms.DataGridView>控制項以數種方式：</span><span class="sxs-lookup"><span data-stu-id="123c0-141">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="123c0-142">變更框線和標題的樣式。</span><span class="sxs-lookup"><span data-stu-id="123c0-142">Change border and header styles.</span></span> <span data-ttu-id="123c0-143">如需詳細資訊，請參閱[如何：變更框線和格線樣式，在 Windows Form DataGridView 控制項](change-the-border-and-gridline-styles-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="123c0-143">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="123c0-144">啟用或限制使用者的輸入<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="123c0-144">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="123c0-145">如需詳細資訊，請參閱[如何：防止資料列中新增和刪除 Windows Form DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)，和[How to:資料行設為唯讀模式中的 Windows Form DataGridView 控制項](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="123c0-145">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="123c0-146">檢查使用者輸入的資料庫相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="123c0-146">Check user input for database-related errors.</span></span> <span data-ttu-id="123c0-147">如需詳細資訊，請參閱[逐步解說：處理在 Windows 中的資料輸入期間所發生的錯誤 Form DataGridView 控制項](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="123c0-147">For more information, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="123c0-148">處理非常大型的資料集使用的虛擬模式。</span><span class="sxs-lookup"><span data-stu-id="123c0-148">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="123c0-149">如需詳細資訊，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="123c0-149">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="123c0-150">自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="123c0-150">Customize the appearance of cells.</span></span> <span data-ttu-id="123c0-151">如需詳細資訊，請參閱[如何：自訂 Windows Form DataGridView 控制項中的儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)和[How to:設定 Windows Form DataGridView 控制項中的 字型和色彩樣式](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="123c0-151">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Font and Color Styles in the Windows Forms DataGridView Control](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="123c0-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="123c0-152">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="123c0-153">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="123c0-153">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="123c0-154">如何：驗證 Windows Form DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="123c0-154">How to: Validate Data in the Windows Forms DataGridView Control</span></span>](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="123c0-155">逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="123c0-155">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="123c0-156">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="123c0-156">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
