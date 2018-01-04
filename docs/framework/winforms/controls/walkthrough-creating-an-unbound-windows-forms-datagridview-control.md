---
title: "逐步解說：建立未繫結的 Windows Form DataGridView 控制項"
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
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d737959ee0ecab4c611cebf996741516fc7be031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="5c3d5-102">逐步解說：建立未繫結的 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5c3d5-102">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5c3d5-103">您可能常要顯示不是來自資料庫的表格式資料。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-103">You may frequently want to display tabular data that does not originate from a database.</span></span> <span data-ttu-id="5c3d5-104">比方說，您可能想要顯示字串的二維陣列的內容。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-104">For example, you may want to show the contents of a two-dimensional array of strings.</span></span> <span data-ttu-id="5c3d5-105"><xref:System.Windows.Forms.DataGridView>類別會提供簡單高度可自訂的方式顯示資料，而不繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-105">The <xref:System.Windows.Forms.DataGridView> class provides an easy and highly customizable way to display data without binding to a data source.</span></span> <span data-ttu-id="5c3d5-106">本逐步解說示範如何以填入<xref:System.Windows.Forms.DataGridView>控制和管理的新增和刪除 「 未繫結 」 模式中的資料列。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-106">This walkthrough shows how to populate a <xref:System.Windows.Forms.DataGridView> control and manage the addition and deletion of rows in "unbound" mode.</span></span> <span data-ttu-id="5c3d5-107">根據預設，使用者可以加入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-107">By default, the user can add new rows.</span></span> <span data-ttu-id="5c3d5-108">若要避免資料列加入，將<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>屬性是`false`。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-108">To prevent row addition, set the <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property is `false`.</span></span>  
  
 <span data-ttu-id="5c3d5-109">若要為單一列出本主題中複製的程式碼，請參閱[How to： 建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-109">To copy the code in this topic as a single listing, see [How to: Create an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="5c3d5-110">建立表單</span><span class="sxs-lookup"><span data-stu-id="5c3d5-110">Creating the Form</span></span>  
  
#### <a name="to-use-an-unbound-datagridview-control"></a><span data-ttu-id="5c3d5-111">若要使用未繫結的 DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5c3d5-111">To use an unbound DataGridView control</span></span>  
  
1.  <span data-ttu-id="5c3d5-112">建立衍生自類別<xref:System.Windows.Forms.Form>而且包含下列變數宣告和`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-112">Create a class that derives from <xref:System.Windows.Forms.Form> and contains the following variable declarations and `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  <span data-ttu-id="5c3d5-113">實作`SetupLayout`表單的類別定義，若要設定表單的版面配置中的方法。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-113">Implement a `SetupLayout` method in your form's class definition to set up the form's layout.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  <span data-ttu-id="5c3d5-114">建立`SetupDataGridView`方法來設定<xref:System.Windows.Forms.DataGridView>資料行和屬性。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-114">Create a `SetupDataGridView` method to set up the <xref:System.Windows.Forms.DataGridView> columns and properties.</span></span>  
  
     <span data-ttu-id="5c3d5-115">這個方法會先加入<xref:System.Windows.Forms.DataGridView>控制項加入表單<xref:System.Windows.Forms.Control.Controls%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-115">This method first adds the <xref:System.Windows.Forms.DataGridView> control to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span> <span data-ttu-id="5c3d5-116">接下來，使用設定要顯示的資料行數目<xref:System.Windows.Forms.DataGridView.ColumnCount%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-116">Next, the number of columns to be displayed is set using the <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> property.</span></span> <span data-ttu-id="5c3d5-117">資料行標頭的預設樣式設定藉由設定<xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>， <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>，和<xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>傳回<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-117">The default style for the column headers is set by setting the <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, and <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> returned by the <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> property.</span></span>  
  
     <span data-ttu-id="5c3d5-118">設定版面配置和外觀屬性，，然後指派資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-118">Layout and appearance properties are set, and then the column names are assigned.</span></span> <span data-ttu-id="5c3d5-119">當這個方法會結束時，<xref:System.Windows.Forms.DataGridView>控制項已經準備要被填入。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-119">When this method exits, the <xref:System.Windows.Forms.DataGridView> control is ready to be populated.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  <span data-ttu-id="5c3d5-120">建立`PopulateDataGridView`方法，以將資料列加入<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-120">Create a `PopulateDataGridView` method to add rows to the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="5c3d5-121">每個資料列都代表一首歌曲和其相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-121">Each row represents a song and its associated information.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  <span data-ttu-id="5c3d5-122">使用就地公用程式方法，您可以附加事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-122">With the utility methods in place, you can attach event handlers.</span></span>  
  
     <span data-ttu-id="5c3d5-123">將處理**新增**和**刪除**按鈕<xref:System.Windows.Forms.Control.Click>事件、 將表單的<xref:System.Windows.Forms.Form.Load>事件，而<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-123">You will handle the **Add** and **Delete** buttons' <xref:System.Windows.Forms.Control.Click> events, the form's <xref:System.Windows.Forms.Form.Load> event, and the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
     <span data-ttu-id="5c3d5-124">當**新增**按鈕的<xref:System.Windows.Forms.Control.Click>引發事件時，新的空白資料列加入至<xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-124">When the **Add** button's <xref:System.Windows.Forms.Control.Click> event is raised, a new, empty row is added to the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="5c3d5-125">當**刪除**按鈕的<xref:System.Windows.Forms.Control.Click>就會引發事件，會刪除選取的資料列，除非它是新的記錄，可讓使用者的資料列加入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-125">When the **Delete** button's <xref:System.Windows.Forms.Control.Click> event is raised, the selected row is deleted, unless it is the row for new records, which enables the user add new rows.</span></span> <span data-ttu-id="5c3d5-126">這個資料列永遠是中的最後一個資料列<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-126">This row is always the last row in the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="5c3d5-127">當表單的<xref:System.Windows.Forms.Form.Load>引發事件時， `SetupLayout`， `SetupDataGridView`，和`PopulateDataGridView`呼叫公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-127">When the form's <xref:System.Windows.Forms.Form.Load> event is raised, the `SetupLayout`, `SetupDataGridView`, and `PopulateDataGridView` utility methods are called.</span></span>  
  
     <span data-ttu-id="5c3d5-128">當<xref:System.Windows.Forms.DataGridView.CellFormatting>引發事件時，每個儲存格`Date`除非儲存格的值無法剖析，將會格式化為完整日期的資料行。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-128">When the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is raised, each cell in the `Date` column is formatted as a long date, unless the cell's value cannot be parsed.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="5c3d5-129">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="5c3d5-129">Testing the Application</span></span>  
 <span data-ttu-id="5c3d5-130">您現在可以測試表單，以確定其如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-130">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="5c3d5-131">若要測試表單</span><span class="sxs-lookup"><span data-stu-id="5c3d5-131">To test the form</span></span>  
  
-   <span data-ttu-id="5c3d5-132">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-132">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="5c3d5-133">您會看到<xref:System.Windows.Forms.DataGridView>顯示中所列的歌曲控制項`PopulateDataGridView`。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-133">You will see a <xref:System.Windows.Forms.DataGridView> control that displays the songs listed in `PopulateDataGridView`.</span></span> <span data-ttu-id="5c3d5-134">您可以加入新資料列與**加入資料列** 按鈕，而且您可以刪除選取的資料列與**刪除資料列** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-134">You can add new rows with the **Add Row** button, and you can delete selected rows with the **Delete Row** button.</span></span> <span data-ttu-id="5c3d5-135">未繫結<xref:System.Windows.Forms.DataGridView>控制項的資料存放區，以及其資料是獨立於任何外部來源，例如<xref:System.Data.DataSet>或陣列。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-135">The unbound <xref:System.Windows.Forms.DataGridView> control is the data store, and its data is independent of any external source, such as a <xref:System.Data.DataSet> or an array.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5c3d5-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5c3d5-136">Next Steps</span></span>  
 <span data-ttu-id="5c3d5-137">此應用程式可讓您基本的了解<xref:System.Windows.Forms.DataGridView>控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-137">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="5c3d5-138">您可以自訂的外觀和行為<xref:System.Windows.Forms.DataGridView>數種方式控制：</span><span class="sxs-lookup"><span data-stu-id="5c3d5-138">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="5c3d5-139">變更框線和標題的樣式。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-139">Change border and header styles.</span></span> <span data-ttu-id="5c3d5-140">如需詳細資訊，請參閱[如何： 變更 Windows Form DataGridView 控制項中的格線樣式和框線](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-140">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="5c3d5-141">啟用或限制使用者輸入到<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-141">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5c3d5-142">如需詳細資訊，請參閱[如何： 防止資料列新增和刪除 Windows Form DataGridView 控制項中的](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)，和[如何： 使 Windows Form DataGridView 控制項中的資料行唯讀](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-142">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="5c3d5-143">檢查使用者輸入的資料庫相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-143">Check user input for database-related errors.</span></span> <span data-ttu-id="5c3d5-144">如需詳細資訊，請參閱[逐步解說： 處理所發生的錯誤在 Windows Form DataGridView 控制項中的資料輸入期間](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-144">For more information, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="5c3d5-145">處理非常大型的資料集使用的虛擬模式。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-145">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="5c3d5-146">如需詳細資訊，請參閱[逐步解說： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-146">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="5c3d5-147">自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-147">Customize the appearance of cells.</span></span> <span data-ttu-id="5c3d5-148">如需詳細資訊，請參閱[How to： 自訂 Windows Form DataGridView 控制項中的儲存格外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)和[How to： 設定預設儲存格樣式的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5c3d5-148">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c3d5-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c3d5-149">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="5c3d5-150">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="5c3d5-150">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5c3d5-151">操作說明：建立未繫結的 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5c3d5-151">How to: Create an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5c3d5-152">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="5c3d5-152">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
