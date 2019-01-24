---
title: HOW TO：使用 DataGrid 控制項實作驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 8921d9fd36e011fd33628e15f8a055d79c3959d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674592"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="4acb0-102">HOW TO：使用 DataGrid 控制項實作驗證</span><span class="sxs-lookup"><span data-stu-id="4acb0-102">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="4acb0-103"><xref:System.Windows.Controls.DataGrid>控制項可讓您執行的資料格 」 和 「 資料列層級的驗證。</span><span class="sxs-lookup"><span data-stu-id="4acb0-103">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="4acb0-104">資料格層級驗證，您驗證繫結的資料物件的個別屬性，當使用者更新的值。</span><span class="sxs-lookup"><span data-stu-id="4acb0-104">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="4acb0-105">資料列層級驗證，您會驗證整個資料的物件，當使用者認可變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="4acb0-105">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="4acb0-106">您也可以提供自訂的視覺化回饋，對於驗證錯誤，或使用預設的視覺化回饋，<xref:System.Windows.Controls.DataGrid>控制項提供。</span><span class="sxs-lookup"><span data-stu-id="4acb0-106">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="4acb0-107">下列程序描述如何套用驗證規則來<xref:System.Windows.Controls.DataGrid>繫結和自訂的視覺化回饋。</span><span class="sxs-lookup"><span data-stu-id="4acb0-107">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="4acb0-108">若要驗證個別的資料格的值</span><span class="sxs-lookup"><span data-stu-id="4acb0-108">To validate individual cell values</span></span>  
  
-   <span data-ttu-id="4acb0-109">使用具有資料行的繫結上指定一個或多個驗證規則。</span><span class="sxs-lookup"><span data-stu-id="4acb0-109">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="4acb0-110">這是類似於驗證簡單的控制項中的資料中所述[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4acb0-110">This is similar to validating data in simple controls, as described in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="4acb0-111">下列範例所示<xref:System.Windows.Controls.DataGrid>控制項繫結至商務物件的不同屬性的四個資料行。</span><span class="sxs-lookup"><span data-stu-id="4acb0-111">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="4acb0-112">三個資料行的指定<xref:System.Windows.Controls.ExceptionValidationRule>splittunneling<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="4acb0-112">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="4acb0-113">當使用者輸入無效的值 （例如非整數課程 ID 資料行中） 時，則會在資料格周圍出現紅色框線。</span><span class="sxs-lookup"><span data-stu-id="4acb0-113">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="4acb0-114">您可以變更這個預設驗證回應如下列程序中所述。</span><span class="sxs-lookup"><span data-stu-id="4acb0-114">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="4acb0-115">若要自訂資料格驗證回應</span><span class="sxs-lookup"><span data-stu-id="4acb0-115">To customize cell validation feedback</span></span>  
  
-   <span data-ttu-id="4acb0-116">設定資料行的<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>資料行的編輯控制項適合的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="4acb0-116">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="4acb0-117">因為編輯控制項建立在執行階段中，您無法使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>附加屬性，就像使用簡單的控制項。</span><span class="sxs-lookup"><span data-stu-id="4acb0-117">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="4acb0-118">下列範例會更新先前的範例，加上共用的驗證規則的三個資料行的錯誤樣式。</span><span class="sxs-lookup"><span data-stu-id="4acb0-118">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="4acb0-119">當使用者輸入無效的值時，樣式會變更的資料格背景色彩，以及加入工具提示。</span><span class="sxs-lookup"><span data-stu-id="4acb0-119">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="4acb0-120">請注意，若要判斷是否有驗證錯誤的觸發程序使用。</span><span class="sxs-lookup"><span data-stu-id="4acb0-120">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="4acb0-121">這是必要的因為目前沒有資料格的專用的錯誤範本。</span><span class="sxs-lookup"><span data-stu-id="4acb0-121">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="4acb0-122">您可以實作更廣泛的自訂取代<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>資料行使用。</span><span class="sxs-lookup"><span data-stu-id="4acb0-122">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="4acb0-123">若要驗證的單一資料列中的多個值</span><span class="sxs-lookup"><span data-stu-id="4acb0-123">To validate multiple values in a single row</span></span>  
  
1.  <span data-ttu-id="4acb0-124">實作<xref:System.Windows.Controls.ValidationRule>檢查多個屬性的繫結的資料物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="4acb0-124">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="4acb0-125">在您<xref:System.Windows.Controls.ValidationRule.Validate%2A>轉換方法實作`value`參數值以<xref:System.Windows.Data.BindingGroup>執行個體。</span><span class="sxs-lookup"><span data-stu-id="4acb0-125">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="4acb0-126">然後，您就可以存取資料物件，可透過<xref:System.Windows.Data.BindingGroup.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4acb0-126">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="4acb0-127">下列範例示範此程序來驗證是否`StartDate`屬性值`Course`物件是早於其`EndDate`屬性值。</span><span class="sxs-lookup"><span data-stu-id="4acb0-127">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  <span data-ttu-id="4acb0-128">新增驗證規則，以<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="4acb0-128">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="4acb0-129"><xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>屬性會提供直接存取<xref:System.Windows.Data.BindingGroup.ValidationRules%2A>屬性<xref:System.Windows.Data.BindingGroup>群組控制項所使用的所有繫結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4acb0-129">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="4acb0-130">下列範例會設定<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>在 XAML 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="4acb0-130">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="4acb0-131"><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>屬性設定為<xref:System.Windows.Controls.ValidationStep.UpdatedValue>如此才會更新繫結的資料物件，就會發生驗證。</span><span class="sxs-lookup"><span data-stu-id="4acb0-131">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="4acb0-132">當使用者指定結束日期必須早於開始日期時，紅色驚嘆號 （！） 會出現在資料列標頭中。</span><span class="sxs-lookup"><span data-stu-id="4acb0-132">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="4acb0-133">您可以變更這個預設驗證回應如下列程序中所述。</span><span class="sxs-lookup"><span data-stu-id="4acb0-133">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="4acb0-134">若要自訂的資料列驗證回應</span><span class="sxs-lookup"><span data-stu-id="4acb0-134">To customize row validation feedback</span></span>  
  
-   <span data-ttu-id="4acb0-135">設定 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4acb0-135">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4acb0-136">這個屬性可讓您自訂個別的資料列驗證回應<xref:System.Windows.Controls.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="4acb0-136">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="4acb0-137">您也可以使用隱含資料列樣式設定來影響多個控制項<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="4acb0-137">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="4acb0-138">下列範例會將預設資料列驗證回應取代更明顯可見的指標。</span><span class="sxs-lookup"><span data-stu-id="4acb0-138">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="4acb0-139">當使用者輸入無效的值時，內含白色驚嘆號的紅色圓圈會出現在資料列標頭中。</span><span class="sxs-lookup"><span data-stu-id="4acb0-139">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="4acb0-140">發生這種情況的資料列和資料格的驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="4acb0-140">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="4acb0-141">相關聯的錯誤訊息會顯示在工具提示。</span><span class="sxs-lookup"><span data-stu-id="4acb0-141">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="4acb0-142">範例</span><span class="sxs-lookup"><span data-stu-id="4acb0-142">Example</span></span>  
 <span data-ttu-id="4acb0-143">下列範例會提供完整的示範儲存格和資料列的驗證。</span><span class="sxs-lookup"><span data-stu-id="4acb0-143">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="4acb0-144">`Course`類別會提供範例資料物件實作<xref:System.ComponentModel.IEditableObject>為支援交易。</span><span class="sxs-lookup"><span data-stu-id="4acb0-144">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="4acb0-145"><xref:System.Windows.Controls.DataGrid>與控制項互動<xref:System.ComponentModel.IEditableObject>，讓使用者可以按下 esc 鍵還原變更。</span><span class="sxs-lookup"><span data-stu-id="4acb0-145">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4acb0-146">如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="DataGridValidation.MainWindow"`與`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="4acb0-146">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="4acb0-147">若要測試驗證，請嘗試下列方法：</span><span class="sxs-lookup"><span data-stu-id="4acb0-147">To test the validation, try the following:</span></span>  
  
-   <span data-ttu-id="4acb0-148">在課程識別碼 欄中，輸入非整數值。</span><span class="sxs-lookup"><span data-stu-id="4acb0-148">In the Course ID column, enter a non-integer value.</span></span>  
  
-   <span data-ttu-id="4acb0-149">結束日期資料行中輸入日期早於開始日期。</span><span class="sxs-lookup"><span data-stu-id="4acb0-149">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
-   <span data-ttu-id="4acb0-150">刪除在課程 ID、 開始日期或結束日期值。</span><span class="sxs-lookup"><span data-stu-id="4acb0-150">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
-   <span data-ttu-id="4acb0-151">若要復原無效的資料格的值，將游標放回資料格中，並按下 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="4acb0-151">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
-   <span data-ttu-id="4acb0-152">若要到目前的儲存格處於編輯模式時，請復原整個資料列的變更，請按 ESC 鍵兩次。</span><span class="sxs-lookup"><span data-stu-id="4acb0-152">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
-   <span data-ttu-id="4acb0-153">發生驗證錯誤時，將滑鼠指標停留在指標資料列標頭，以查看相關聯的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4acb0-153">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="4acb0-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4acb0-154">See also</span></span>
- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="4acb0-155">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4acb0-155">DataGrid</span></span>](../../../../docs/framework/wpf/controls/datagrid.md)
- [<span data-ttu-id="4acb0-156">資料繫結</span><span class="sxs-lookup"><span data-stu-id="4acb0-156">Data Binding</span></span>](../../../../docs/framework/wpf/data/data-binding-wpf.md)
- [<span data-ttu-id="4acb0-157">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="4acb0-157">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)
- [<span data-ttu-id="4acb0-158">對自訂物件實作驗證邏輯</span><span class="sxs-lookup"><span data-stu-id="4acb0-158">Implement Validation Logic on Custom Objects</span></span>](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
