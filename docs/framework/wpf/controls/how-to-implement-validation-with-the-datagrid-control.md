---
title: 如何：使用 DataGrid 控制項實作驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 38b4c9cd7679f0d8da9b18fb5bd6bb729d33ed54
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646092"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="f4355-102">如何：使用 DataGrid 控制項實作驗證</span><span class="sxs-lookup"><span data-stu-id="f4355-102">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="f4355-103">該<xref:System.Windows.Controls.DataGrid>控制項使您能夠在儲存格和行等級執行驗證。</span><span class="sxs-lookup"><span data-stu-id="f4355-103">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="f4355-104">使用單元格級驗證,當使用者更新值時,可以驗證綁定數據對象的單個屬性。</span><span class="sxs-lookup"><span data-stu-id="f4355-104">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="f4355-105">使用行級驗證,當使用者將更改提交到行時,可以驗證整個數據物件。</span><span class="sxs-lookup"><span data-stu-id="f4355-105">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="f4355-106">您還可以為驗證錯誤提供自定義的可視反饋,或使用<xref:System.Windows.Controls.DataGrid>控制項提供的預設視覺反饋。</span><span class="sxs-lookup"><span data-stu-id="f4355-106">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="f4355-107">以下過程介紹如何將驗證規則應用於<xref:System.Windows.Controls.DataGrid>綁定並自定義可視反饋。</span><span class="sxs-lookup"><span data-stu-id="f4355-107">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="f4355-108">驗證儲存格值</span><span class="sxs-lookup"><span data-stu-id="f4355-108">To validate individual cell values</span></span>  
  
- <span data-ttu-id="f4355-109">在列使用的綁定上指定一個或多個驗證規則。</span><span class="sxs-lookup"><span data-stu-id="f4355-109">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="f4355-110">這類似於在簡單控件中驗證數據,如[數據綁定概述](../../../desktop-wpf/data/data-binding-overview.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="f4355-110">This is similar to validating data in simple controls, as described in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="f4355-111">下面的示例顯示一個<xref:System.Windows.Controls.DataGrid>控件,該控件的四列綁定到業務物件的不同屬性。</span><span class="sxs-lookup"><span data-stu-id="f4355-111">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="f4355-112">三列<xref:System.Windows.Controls.ExceptionValidationRule>透過<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>屬性設定為`true`指定 。</span><span class="sxs-lookup"><span data-stu-id="f4355-112">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="f4355-113">當使用者輸入無效值(如課程 ID 列中的非整數)時,單元格周圍會出現紅色邊框。</span><span class="sxs-lookup"><span data-stu-id="f4355-113">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="f4355-114">您可以按照以下過程所述更改此默認驗證反饋。</span><span class="sxs-lookup"><span data-stu-id="f4355-114">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="f4355-115">自訂儲存格驗證回饋</span><span class="sxs-lookup"><span data-stu-id="f4355-115">To customize cell validation feedback</span></span>  
  
- <span data-ttu-id="f4355-116">將列的屬性<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>設置為適合列編輯控制項的樣式。</span><span class="sxs-lookup"><span data-stu-id="f4355-116">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="f4355-117">由於編輯控制項是在執行時創建的,因此不能像使用簡單控制項那樣<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>使用附加屬性。</span><span class="sxs-lookup"><span data-stu-id="f4355-117">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="f4355-118">下面的範例透過添加由三列共用的具有驗證規則的錯誤樣式來更新前面的範例。</span><span class="sxs-lookup"><span data-stu-id="f4355-118">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="f4355-119">當使用者輸入無效值時,樣式將更改單元格背景顏色並添加工具提示。</span><span class="sxs-lookup"><span data-stu-id="f4355-119">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="f4355-120">請注意使用觸發器來確定是否存在驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4355-120">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="f4355-121">這是必需的,因為當前沒有專用的單元格錯誤範本。</span><span class="sxs-lookup"><span data-stu-id="f4355-121">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="f4355-122">您可以通過替換列使用來<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>實現 更廣泛的自定義。</span><span class="sxs-lookup"><span data-stu-id="f4355-122">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="f4355-123">驗證一列中的多個值</span><span class="sxs-lookup"><span data-stu-id="f4355-123">To validate multiple values in a single row</span></span>  
  
1. <span data-ttu-id="f4355-124">實現一<xref:System.Windows.Controls.ValidationRule>個子類,該子類檢查綁定數據物件的多個屬性。</span><span class="sxs-lookup"><span data-stu-id="f4355-124">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="f4355-125">在方法<xref:System.Windows.Controls.ValidationRule.Validate%2A>實現中,`value`將參數值轉換<xref:System.Windows.Data.BindingGroup>為 實例。</span><span class="sxs-lookup"><span data-stu-id="f4355-125">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="f4355-126">然後,您可以<xref:System.Windows.Data.BindingGroup.Items%2A>通過 屬性訪問數據物件。</span><span class="sxs-lookup"><span data-stu-id="f4355-126">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="f4355-127">下面的範例演示了此過程,以驗證`StartDate``Course`物件的屬性值是否早於`EndDate`其 屬性值。</span><span class="sxs-lookup"><span data-stu-id="f4355-127">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. <span data-ttu-id="f4355-128">將驗證規則添加到<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>集合中。</span><span class="sxs-lookup"><span data-stu-id="f4355-128">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="f4355-129">該<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>屬性提供<xref:System.Windows.Data.BindingGroup.ValidationRules%2A><xref:System.Windows.Data.BindingGroup>對 實例屬性的直接訪問,該實例對控制項使用的所有綁定進行分組。</span><span class="sxs-lookup"><span data-stu-id="f4355-129">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="f4355-130">下面的範例在 XAML<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>中設置 屬性。</span><span class="sxs-lookup"><span data-stu-id="f4355-130">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="f4355-131">屬性<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設置<xref:System.Windows.Controls.ValidationStep.UpdatedValue>為 ,以便驗證僅在更新綁定數據物件後進行。</span><span class="sxs-lookup"><span data-stu-id="f4355-131">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="f4355-132">當使用者指定早於開始日期的結束日期時,行標題中將顯示一個紅色感歎號 (!)。</span><span class="sxs-lookup"><span data-stu-id="f4355-132">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="f4355-133">您可以按照以下過程所述更改此默認驗證反饋。</span><span class="sxs-lookup"><span data-stu-id="f4355-133">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="f4355-134">自訂行驗證回饋</span><span class="sxs-lookup"><span data-stu-id="f4355-134">To customize row validation feedback</span></span>  
  
- <span data-ttu-id="f4355-135">設定 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f4355-135">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f4355-136">此屬性使您能夠為各個<xref:System.Windows.Controls.DataGrid>控制件自定義行驗證回饋。</span><span class="sxs-lookup"><span data-stu-id="f4355-136">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="f4355-137">還可以通過使用隱式行樣式來設置<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>屬性來影響多個控制件。</span><span class="sxs-lookup"><span data-stu-id="f4355-137">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="f4355-138">下面的範例將預設行驗證反饋替換為更可見的指示器。</span><span class="sxs-lookup"><span data-stu-id="f4355-138">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="f4355-139">當使用者輸入無效值時,行標題中將顯示一個帶有白色感嘆號的紅色圓圈。</span><span class="sxs-lookup"><span data-stu-id="f4355-139">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="f4355-140">對於行和單元驗證錯誤,都會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="f4355-140">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="f4355-141">關聯的錯誤消息將顯示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="f4355-141">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="f4355-142">範例</span><span class="sxs-lookup"><span data-stu-id="f4355-142">Example</span></span>  
 <span data-ttu-id="f4355-143">下面的範例提供了儲存格和行驗證的完整演示。</span><span class="sxs-lookup"><span data-stu-id="f4355-143">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="f4355-144">類`Course`提供一個範例數據物件,<xref:System.ComponentModel.IEditableObject>該物件實現以支援事務。</span><span class="sxs-lookup"><span data-stu-id="f4355-144">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="f4355-145">該<xref:System.Windows.Controls.DataGrid>控件與<xref:System.ComponentModel.IEditableObject>這些控制者互動,使用戶能夠透過按 ESC 還原更改。</span><span class="sxs-lookup"><span data-stu-id="f4355-145">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4355-146">如果使用 Visual Basic,則在 MainWindow.xaml`x:Class="DataGridValidation.MainWindow"`的第`x:Class="MainWindow"`一行中, 取代為 。</span><span class="sxs-lookup"><span data-stu-id="f4355-146">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="f4355-147">要測試驗證,請嘗試以下操作:</span><span class="sxs-lookup"><span data-stu-id="f4355-147">To test the validation, try the following:</span></span>  
  
- <span data-ttu-id="f4355-148">在"課程ID"列中,輸入非整數值。</span><span class="sxs-lookup"><span data-stu-id="f4355-148">In the Course ID column, enter a non-integer value.</span></span>  
  
- <span data-ttu-id="f4355-149">在"結束日期"列中,輸入早於開始日期的日期。</span><span class="sxs-lookup"><span data-stu-id="f4355-149">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
- <span data-ttu-id="f4355-150">刪除課程 ID、開始日期或結束日期中的值。</span><span class="sxs-lookup"><span data-stu-id="f4355-150">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
- <span data-ttu-id="f4355-151">要撤銷無效的儲存格值,請將游標放回單元格中,然後按 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="f4355-151">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
- <span data-ttu-id="f4355-152">要在當前儲存格處於編輯模式時撤消整個行的更改,請按 ESC 鍵兩次。</span><span class="sxs-lookup"><span data-stu-id="f4355-152">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
- <span data-ttu-id="f4355-153">發生驗證錯誤時,將滑鼠指標移到行標題中的指示器上以查看關聯的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f4355-153">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="f4355-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4355-154">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="f4355-155">DataGrid</span><span class="sxs-lookup"><span data-stu-id="f4355-155">DataGrid</span></span>](datagrid.md)
- [<span data-ttu-id="f4355-156">資料繫結</span><span class="sxs-lookup"><span data-stu-id="f4355-156">Data Binding</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f4355-157">實作連結</span><span class="sxs-lookup"><span data-stu-id="f4355-157">Implement Binding Validation</span></span>](../data/how-to-implement-binding-validation.md)
- [<span data-ttu-id="f4355-158">在自訂物件上實現驗證邏輯</span><span class="sxs-lookup"><span data-stu-id="f4355-158">Implement Validation Logic on Custom Objects</span></span>](../data/how-to-implement-validation-logic-on-custom-objects.md)
