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
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046385"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="870d2-102">逐步解說：驗證 Windows Forms DataGridView 控制項的資料</span><span class="sxs-lookup"><span data-stu-id="870d2-102">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="870d2-103">當您向使用者顯示資料輸入功能時, 您經常需要驗證輸入表單中的資料。</span><span class="sxs-lookup"><span data-stu-id="870d2-103">When you display data entry functionality to users, you frequently have to validate the data entered into your form.</span></span> <span data-ttu-id="870d2-104"><xref:System.Windows.Forms.DataGridView>類別提供便利的方式來執行驗證, 再將資料認可到資料存放區。</span><span class="sxs-lookup"><span data-stu-id="870d2-104">The <xref:System.Windows.Forms.DataGridView> class provides a convenient way to perform validation before data is committed to the data store.</span></span> <span data-ttu-id="870d2-105">您可以藉由處理<xref:System.Windows.Forms.DataGridView.CellValidating>事件來驗證資料, <xref:System.Windows.Forms.DataGridView>當目前的儲存格變更時, 就會引發。</span><span class="sxs-lookup"><span data-stu-id="870d2-105">You can validate data by handling the <xref:System.Windows.Forms.DataGridView.CellValidating> event, which is raised by the <xref:System.Windows.Forms.DataGridView> when the current cell changes.</span></span>

<span data-ttu-id="870d2-106">在此逐步解說中, 您將從 Northwind `Customers`範例資料庫中的資料表抓取資料列, 並將<xref:System.Windows.Forms.DataGridView>其顯示在控制項中。</span><span class="sxs-lookup"><span data-stu-id="870d2-106">In this walkthrough, you will retrieve rows from the `Customers` table in the Northwind sample database and display them in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="870d2-107">當使用者編輯資料`CompanyName`行中的儲存格並嘗試離開儲存格時<xref:System.Windows.Forms.DataGridView.CellValidating> , 事件處理常式會檢查新的公司名稱字串以確定它不是空的; 如果新的值是空字串, 則<xref:System.Windows.Forms.DataGridView>會防止使用者的資料指標離開儲存格, 直到輸入非空白字串為止。</span><span class="sxs-lookup"><span data-stu-id="870d2-107">When a user edits a cell in the `CompanyName` column and tries to leave the cell, the <xref:System.Windows.Forms.DataGridView.CellValidating> event handler will examine new company name string to make sure it is not empty; if the new value is an empty string, the <xref:System.Windows.Forms.DataGridView> will prevent the user's cursor from leaving the cell until a non-empty string is entered.</span></span>

<span data-ttu-id="870d2-108">若要將此主題中的程式碼複製為單一清單，請參閱[如何：驗證 Windows Forms DataGridView 控制項](how-to-validate-data-in-the-windows-forms-datagridview-control.md)中的資料。</span><span class="sxs-lookup"><span data-stu-id="870d2-108">To copy the code in this topic as a single listing, see [How to: Validate Data in the Windows Forms DataGridView Control](how-to-validate-data-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="870d2-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="870d2-109">Prerequisites</span></span>

<span data-ttu-id="870d2-110">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="870d2-110">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="870d2-111">具有 Northwind SQL Server 範例資料庫之伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="870d2-111">Access to a server that has the Northwind SQL Server sample database.</span></span>

## <a name="creating-the-form"></a><span data-ttu-id="870d2-112">建立表單</span><span class="sxs-lookup"><span data-stu-id="870d2-112">Creating the Form</span></span>

#### <a name="to-validate-data-entered-in-a-datagridview"></a><span data-ttu-id="870d2-113">驗證 DataGridView 中輸入的資料</span><span class="sxs-lookup"><span data-stu-id="870d2-113">To validate data entered in a DataGridView</span></span>

1. <span data-ttu-id="870d2-114">建立衍生自<xref:System.Windows.Forms.Form>的類別, 並<xref:System.Windows.Forms.DataGridView>包含控制項和<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="870d2-114">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control and a <xref:System.Windows.Forms.BindingSource> component.</span></span>

    <span data-ttu-id="870d2-115">下列程式碼範例提供基本的`Main`初始化, 並包含方法。</span><span class="sxs-lookup"><span data-stu-id="870d2-115">The following code example provides basic initialization and includes a `Main` method.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. <span data-ttu-id="870d2-116">在表單的類別定義中執行方法, 以處理連接至資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="870d2-116">Implement a method in your form's class definition for handling the details of connecting to the database.</span></span>

    <span data-ttu-id="870d2-117">這個程式碼範例會`GetData`使用方法來傳回已<xref:System.Data.DataTable>填入的物件。</span><span class="sxs-lookup"><span data-stu-id="870d2-117">This code example uses a `GetData` method that returns a populated <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="870d2-118">請務必將`connectionString`變數設定為適用于您資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="870d2-118">Be sure that you set the `connectionString` variable to a value that is appropriate for your database.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="870d2-119">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="870d2-119">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="870d2-120">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="870d2-120">Using Windows Authentication, also known as integrated security, is a more secure way to control access to a database.</span></span> <span data-ttu-id="870d2-121">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="870d2-121">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. <span data-ttu-id="870d2-122">為表單的<xref:System.Windows.Forms.Form.Load>事件執行處理常式, 以<xref:System.Windows.Forms.DataGridView>初始化和<xref:System.Windows.Forms.BindingSource> , 並設定資料系結。</span><span class="sxs-lookup"><span data-stu-id="870d2-122">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> and <xref:System.Windows.Forms.BindingSource> and sets up the data binding.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. <span data-ttu-id="870d2-123">執行<xref:System.Windows.Forms.DataGridView> 控制項和<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件的處理常式。 <xref:System.Windows.Forms.DataGridView.CellValidating></span><span class="sxs-lookup"><span data-stu-id="870d2-123">Implement handlers for the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellValidating> and <xref:System.Windows.Forms.DataGridView.CellEndEdit> events.</span></span>

    <span data-ttu-id="870d2-124">事件處理常式可讓您判斷資料`CompanyName`行中資料格的值是否為空白。 <xref:System.Windows.Forms.DataGridView.CellValidating></span><span class="sxs-lookup"><span data-stu-id="870d2-124">The <xref:System.Windows.Forms.DataGridView.CellValidating> event handler is where you determine whether the value of a cell in the `CompanyName` column is empty.</span></span> <span data-ttu-id="870d2-125">如果資料格值驗證失敗, 請將<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>類別的屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="870d2-125">If the cell value fails validation, set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property of the <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> class to `true`.</span></span> <span data-ttu-id="870d2-126">這會導致<xref:System.Windows.Forms.DataGridView>控制項防止游標離開儲存格。</span><span class="sxs-lookup"><span data-stu-id="870d2-126">This causes the <xref:System.Windows.Forms.DataGridView> control to prevent the cursor from leaving the cell.</span></span> <span data-ttu-id="870d2-127">將資料<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>列上的屬性設定為說明性字串。</span><span class="sxs-lookup"><span data-stu-id="870d2-127">Set the <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> property on the row to an explanatory string.</span></span> <span data-ttu-id="870d2-128">這會顯示錯誤圖示, 其中包含含有錯誤文字的工具提示。</span><span class="sxs-lookup"><span data-stu-id="870d2-128">This displays an error icon with a ToolTip that contains the error text.</span></span> <span data-ttu-id="870d2-129">在事件處理常式中, 將<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>資料列上的屬性設定為空字串。 <xref:System.Windows.Forms.DataGridView.CellEndEdit></span><span class="sxs-lookup"><span data-stu-id="870d2-129">In the <xref:System.Windows.Forms.DataGridView.CellEndEdit> event handler, set the <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> property on the row to the empty string.</span></span> <span data-ttu-id="870d2-130">只有<xref:System.Windows.Forms.DataGridView.CellEndEdit>當儲存格離開編輯模式時, 才會發生此事件, 如果驗證失敗, 就無法執行此動作。</span><span class="sxs-lookup"><span data-stu-id="870d2-130">The <xref:System.Windows.Forms.DataGridView.CellEndEdit> event occurs only when the cell exits edit mode, which it cannot do if it fails validation.</span></span>

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a><span data-ttu-id="870d2-131">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="870d2-131">Testing the Application</span></span>

<span data-ttu-id="870d2-132">您現在可以測試表單, 以確定它會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="870d2-132">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="870d2-133">測試表單</span><span class="sxs-lookup"><span data-stu-id="870d2-133">To test the form</span></span>

- <span data-ttu-id="870d2-134">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="870d2-134">Compile and run the application.</span></span>

  <span data-ttu-id="870d2-135">您會看到<xref:System.Windows.Forms.DataGridView>填入`Customers`資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="870d2-135">You will see a <xref:System.Windows.Forms.DataGridView> filled with data from the `Customers` table.</span></span> <span data-ttu-id="870d2-136">當您按兩下資料`CompanyName`行中的資料格時, 您可以編輯此值。</span><span class="sxs-lookup"><span data-stu-id="870d2-136">When you double-click a cell in the `CompanyName` column, you can edit the value.</span></span> <span data-ttu-id="870d2-137">如果您刪除所有字元, 並按 TAB 鍵來結束資料格, 則<xref:System.Windows.Forms.DataGridView>會導致無法結束。</span><span class="sxs-lookup"><span data-stu-id="870d2-137">If you delete all the characters and hit the TAB key to exit the cell, the <xref:System.Windows.Forms.DataGridView> prevents you from exiting.</span></span> <span data-ttu-id="870d2-138">當您將非空白字串輸入儲存格時, <xref:System.Windows.Forms.DataGridView>控制項可讓您結束儲存格。</span><span class="sxs-lookup"><span data-stu-id="870d2-138">When you type a non-empty string into the cell, the <xref:System.Windows.Forms.DataGridView> control lets you exit the cell.</span></span>

## <a name="next-steps"></a><span data-ttu-id="870d2-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="870d2-139">Next Steps</span></span>

<span data-ttu-id="870d2-140">此應用程式可讓您對<xref:System.Windows.Forms.DataGridView>控制項的功能有基本瞭解。</span><span class="sxs-lookup"><span data-stu-id="870d2-140">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="870d2-141">您可以透過數種方式自訂<xref:System.Windows.Forms.DataGridView>控制項的外觀和行為:</span><span class="sxs-lookup"><span data-stu-id="870d2-141">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>

- <span data-ttu-id="870d2-142">變更框線和標題樣式。</span><span class="sxs-lookup"><span data-stu-id="870d2-142">Change border and header styles.</span></span> <span data-ttu-id="870d2-143">如需詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項](change-the-border-and-gridline-styles-in-the-datagrid.md)中的框線和格線樣式。</span><span class="sxs-lookup"><span data-stu-id="870d2-143">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>

- <span data-ttu-id="870d2-144">啟用或限制控制項的<xref:System.Windows.Forms.DataGridView>使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="870d2-144">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="870d2-145">如需詳細資訊，請參閱[如何：防止在 Windows Forms DataGridView 控制項](prevent-row-addition-and-deletion-datagridview.md)中新增和刪除資料列, 以及[如何:將 Windows Forms DataGridView 控制項](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)中的資料行設為唯讀。</span><span class="sxs-lookup"><span data-stu-id="870d2-145">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>

- <span data-ttu-id="870d2-146">檢查使用者輸入中是否有資料庫相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="870d2-146">Check user input for database-related errors.</span></span> <span data-ttu-id="870d2-147">如需詳細資訊，請參閱[逐步解說：處理 Windows Forms DataGridView 控制項](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)中的資料輸入期間所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="870d2-147">For more information, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>

- <span data-ttu-id="870d2-148">使用虛擬模式處理非常大型的資料集。</span><span class="sxs-lookup"><span data-stu-id="870d2-148">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="870d2-149">如需詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)中執行虛擬模式。</span><span class="sxs-lookup"><span data-stu-id="870d2-149">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>

- <span data-ttu-id="870d2-150">自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="870d2-150">Customize the appearance of cells.</span></span> <span data-ttu-id="870d2-151">如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項](customize-the-appearance-of-cells-in-the-datagrid.md)中自訂儲存格的外觀, 以及[如何:設定 Windows Forms DataGridView 控制項](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)中的字型和色彩樣式。</span><span class="sxs-lookup"><span data-stu-id="870d2-151">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Font and Color Styles in the Windows Forms DataGridView Control](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="870d2-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="870d2-152">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="870d2-153">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="870d2-153">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="870d2-154">如何：驗證 Windows Forms DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="870d2-154">How to: Validate Data in the Windows Forms DataGridView Control</span></span>](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="870d2-155">逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="870d2-155">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="870d2-156">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="870d2-156">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
