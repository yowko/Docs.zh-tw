---
title: 建立未系結的 DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: ceb75d4ee845d1f643d4d88d5a9f1bde73edcc70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740182"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="a0d52-102">逐步解說：建立未繫結的 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="a0d52-102">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a0d52-103">您可能經常想要顯示不是源自資料庫的表格式資料。</span><span class="sxs-lookup"><span data-stu-id="a0d52-103">You may frequently want to display tabular data that does not originate from a database.</span></span> <span data-ttu-id="a0d52-104">例如，您可能會想要顯示字串二維陣列的內容。</span><span class="sxs-lookup"><span data-stu-id="a0d52-104">For example, you may want to show the contents of a two-dimensional array of strings.</span></span> <span data-ttu-id="a0d52-105"><xref:System.Windows.Forms.DataGridView> 類別提供簡單且可高度自訂的方式來顯示資料，而不需要系結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="a0d52-105">The <xref:System.Windows.Forms.DataGridView> class provides an easy and highly customizable way to display data without binding to a data source.</span></span> <span data-ttu-id="a0d52-106">本逐步解說示範如何在「未系結」模式中填入 <xref:System.Windows.Forms.DataGridView> 控制項，以及管理資料列的加入和刪除。</span><span class="sxs-lookup"><span data-stu-id="a0d52-106">This walkthrough shows how to populate a <xref:System.Windows.Forms.DataGridView> control and manage the addition and deletion of rows in "unbound" mode.</span></span> <span data-ttu-id="a0d52-107">根據預設，使用者可以加入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="a0d52-107">By default, the user can add new rows.</span></span> <span data-ttu-id="a0d52-108">若要避免加入資料列，請將 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a0d52-108">To prevent row addition, set the <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property is `false`.</span></span>  
  
 <span data-ttu-id="a0d52-109">若要將本主題中的程式碼複製成單一清單，請參閱[如何：建立未系結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d52-109">To copy the code in this topic as a single listing, see [How to: Create an Unbound Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="a0d52-110">建立表單</span><span class="sxs-lookup"><span data-stu-id="a0d52-110">Creating the Form</span></span>  
  
#### <a name="to-use-an-unbound-datagridview-control"></a><span data-ttu-id="a0d52-111">使用未系結的 DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="a0d52-111">To use an unbound DataGridView control</span></span>  
  
1. <span data-ttu-id="a0d52-112">建立衍生自 <xref:System.Windows.Forms.Form> 的類別，並包含下列變數宣告和 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="a0d52-112">Create a class that derives from <xref:System.Windows.Forms.Form> and contains the following variable declarations and `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2. <span data-ttu-id="a0d52-113">在表單的類別定義中執行 `SetupLayout` 方法，以設定表單的版面配置。</span><span class="sxs-lookup"><span data-stu-id="a0d52-113">Implement a `SetupLayout` method in your form's class definition to set up the form's layout.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3. <span data-ttu-id="a0d52-114">建立 `SetupDataGridView` 方法來設定 <xref:System.Windows.Forms.DataGridView> 的資料行和屬性。</span><span class="sxs-lookup"><span data-stu-id="a0d52-114">Create a `SetupDataGridView` method to set up the <xref:System.Windows.Forms.DataGridView> columns and properties.</span></span>  
  
     <span data-ttu-id="a0d52-115">這個方法會先將 <xref:System.Windows.Forms.DataGridView> 控制項新增至表單的 <xref:System.Windows.Forms.Control.Controls%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="a0d52-115">This method first adds the <xref:System.Windows.Forms.DataGridView> control to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span> <span data-ttu-id="a0d52-116">接下來，會使用 <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> 屬性來設定要顯示的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="a0d52-116">Next, the number of columns to be displayed is set using the <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> property.</span></span> <span data-ttu-id="a0d52-117">資料行標頭的預設樣式是藉由設定 [<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>] 屬性所傳回之 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 [<xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>]、[<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>] 和 [<xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> 屬性] 來設定。</span><span class="sxs-lookup"><span data-stu-id="a0d52-117">The default style for the column headers is set by setting the <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, and <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> returned by the <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> property.</span></span>  
  
     <span data-ttu-id="a0d52-118">設定版面配置和外觀屬性，然後指派資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a0d52-118">Layout and appearance properties are set, and then the column names are assigned.</span></span> <span data-ttu-id="a0d52-119">當這個方法結束時，就可以填入 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="a0d52-119">When this method exits, the <xref:System.Windows.Forms.DataGridView> control is ready to be populated.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4. <span data-ttu-id="a0d52-120">建立 `PopulateDataGridView` 方法，將資料列加入 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="a0d52-120">Create a `PopulateDataGridView` method to add rows to the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="a0d52-121">每個資料列都代表一個歌曲和其相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a0d52-121">Each row represents a song and its associated information.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5. <span data-ttu-id="a0d52-122">備妥公用程式方法之後，您就可以附加事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a0d52-122">With the utility methods in place, you can attach event handlers.</span></span>  
  
     <span data-ttu-id="a0d52-123">您將處理 [**加入**] 和 [**刪除**] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件、表單的 <xref:System.Windows.Forms.Form.Load> 事件和 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件。</span><span class="sxs-lookup"><span data-stu-id="a0d52-123">You will handle the **Add** and **Delete** buttons' <xref:System.Windows.Forms.Control.Click> events, the form's <xref:System.Windows.Forms.Form.Load> event, and the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
     <span data-ttu-id="a0d52-124">當引發 [**加入**] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件時，新的空白資料列就會加入至 <xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="a0d52-124">When the **Add** button's <xref:System.Windows.Forms.Control.Click> event is raised, a new, empty row is added to the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="a0d52-125">當 [**刪除**] 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件引發時，會刪除選取的資料列，除非它是新記錄的資料列，讓使用者可以加入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="a0d52-125">When the **Delete** button's <xref:System.Windows.Forms.Control.Click> event is raised, the selected row is deleted, unless it is the row for new records, which enables the user add new rows.</span></span> <span data-ttu-id="a0d52-126">這個資料列一律是 <xref:System.Windows.Forms.DataGridView> 控制項中的最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a0d52-126">This row is always the last row in the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="a0d52-127">當表單的 <xref:System.Windows.Forms.Form.Load> 事件引發時，會呼叫 `SetupLayout`、`SetupDataGridView`和 `PopulateDataGridView` 公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="a0d52-127">When the form's <xref:System.Windows.Forms.Form.Load> event is raised, the `SetupLayout`, `SetupDataGridView`, and `PopulateDataGridView` utility methods are called.</span></span>  
  
     <span data-ttu-id="a0d52-128">當 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件引發時，`Date` 資料行中的每個儲存格都會格式化為完整日期，除非無法剖析儲存格的值。</span><span class="sxs-lookup"><span data-stu-id="a0d52-128">When the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is raised, each cell in the `Date` column is formatted as a long date, unless the cell's value cannot be parsed.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="a0d52-129">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="a0d52-129">Testing the Application</span></span>  
 <span data-ttu-id="a0d52-130">您現在可以測試表單，以確定它會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="a0d52-130">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="a0d52-131">測試表單</span><span class="sxs-lookup"><span data-stu-id="a0d52-131">To test the form</span></span>  
  
- <span data-ttu-id="a0d52-132">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0d52-132">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="a0d52-133">您會看到 <xref:System.Windows.Forms.DataGridView> 控制項，其中顯示 `PopulateDataGridView`中列出的歌曲。</span><span class="sxs-lookup"><span data-stu-id="a0d52-133">You will see a <xref:System.Windows.Forms.DataGridView> control that displays the songs listed in `PopulateDataGridView`.</span></span> <span data-ttu-id="a0d52-134">您可以使用 [**加入資料列**] 按鈕加入新的資料列，也可以使用 [**刪除資料列**] 按鈕來刪除選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="a0d52-134">You can add new rows with the **Add Row** button, and you can delete selected rows with the **Delete Row** button.</span></span> <span data-ttu-id="a0d52-135">未系結的 <xref:System.Windows.Forms.DataGridView> 控制項是資料存放區，而且其資料與任何外部來源（例如 <xref:System.Data.DataSet> 或陣列）無關。</span><span class="sxs-lookup"><span data-stu-id="a0d52-135">The unbound <xref:System.Windows.Forms.DataGridView> control is the data store, and its data is independent of any external source, such as a <xref:System.Data.DataSet> or an array.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a0d52-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a0d52-136">Next Steps</span></span>  
 <span data-ttu-id="a0d52-137">此應用程式可讓您對 <xref:System.Windows.Forms.DataGridView> 控制項的功能有基本瞭解。</span><span class="sxs-lookup"><span data-stu-id="a0d52-137">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="a0d52-138">您可以透過數種方式自訂 <xref:System.Windows.Forms.DataGridView> 控制項的外觀和行為：</span><span class="sxs-lookup"><span data-stu-id="a0d52-138">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
- <span data-ttu-id="a0d52-139">變更框線和標題樣式。</span><span class="sxs-lookup"><span data-stu-id="a0d52-139">Change border and header styles.</span></span> <span data-ttu-id="a0d52-140">如需詳細資訊，請參閱[如何：變更 Windows Forms DataGridView 控制項中的框線和格線樣式](change-the-border-and-gridline-styles-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d52-140">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
- <span data-ttu-id="a0d52-141">啟用或限制 <xref:System.Windows.Forms.DataGridView> 控制項的使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="a0d52-141">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a0d52-142">如需詳細資訊，請參閱[如何：防止在 Windows Forms Datagridview 控制項中新增和刪除](prevent-row-addition-and-deletion-datagridview.md)資料[列和如何：將 Windows Forms DataGridView 控制項中](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)的資料行設為唯讀。</span><span class="sxs-lookup"><span data-stu-id="a0d52-142">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
- <span data-ttu-id="a0d52-143">檢查使用者輸入中是否有資料庫相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="a0d52-143">Check user input for database-related errors.</span></span> <span data-ttu-id="a0d52-144">如需詳細資訊，請參閱[逐步解說：處理 Windows Forms DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d52-144">For more information, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
- <span data-ttu-id="a0d52-145">使用虛擬模式處理非常大型的資料集。</span><span class="sxs-lookup"><span data-stu-id="a0d52-145">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="a0d52-146">如需詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d52-146">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
- <span data-ttu-id="a0d52-147">自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="a0d52-147">Customize the appearance of cells.</span></span> <span data-ttu-id="a0d52-148">如需詳細資訊，請參閱[如何：在 Windows Forms Datagridview 控制項中自訂儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)和[如何：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d52-148">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d52-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0d52-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="a0d52-150">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="a0d52-150">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a0d52-151">操作說明：建立未繫結的 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="a0d52-151">How to: Create an Unbound Windows Forms DataGridView Control</span></span>](how-to-create-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="a0d52-152">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="a0d52-152">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
