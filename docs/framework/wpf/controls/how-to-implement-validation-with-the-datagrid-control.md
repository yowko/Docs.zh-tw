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
ms.openlocfilehash: 8ae651b3085b39673a51cf8d5f65e9bfb9da87d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962046"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="4ba10-102">作法：使用 DataGrid 控制項實作驗證</span><span class="sxs-lookup"><span data-stu-id="4ba10-102">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="4ba10-103"><xref:System.Windows.Controls.DataGrid>控制項可讓您在資料格和資料列層級執行驗證。</span><span class="sxs-lookup"><span data-stu-id="4ba10-103">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="4ba10-104">使用資料格層級驗證時, 您會在使用者更新值時驗證系結資料物件的個別屬性。</span><span class="sxs-lookup"><span data-stu-id="4ba10-104">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="4ba10-105">使用資料列層級驗證時, 您會在使用者認可資料列的變更時, 驗證整個資料物件。</span><span class="sxs-lookup"><span data-stu-id="4ba10-105">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="4ba10-106">您也可以針對驗證錯誤提供自訂的視覺效果意見反應, 或使用<xref:System.Windows.Controls.DataGrid>控制項提供的預設視覺效果意見反應。</span><span class="sxs-lookup"><span data-stu-id="4ba10-106">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="4ba10-107">下列程式說明如何將驗證規則套用至<xref:System.Windows.Controls.DataGrid>系結, 並自訂視覺效果的意見反應。</span><span class="sxs-lookup"><span data-stu-id="4ba10-107">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="4ba10-108">驗證個別的資料格值</span><span class="sxs-lookup"><span data-stu-id="4ba10-108">To validate individual cell values</span></span>  
  
- <span data-ttu-id="4ba10-109">在與資料行搭配使用的系結上, 指定一或多個驗證規則。</span><span class="sxs-lookup"><span data-stu-id="4ba10-109">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="4ba10-110">這類似于在簡單控制項中驗證資料, 如資料系結[總覽](../data/data-binding-overview.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="4ba10-110">This is similar to validating data in simple controls, as described in [Data Binding Overview](../data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="4ba10-111">下列範例顯示<xref:System.Windows.Controls.DataGrid>的控制項有四個數據行系結至商務物件的不同屬性。</span><span class="sxs-lookup"><span data-stu-id="4ba10-111">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="4ba10-112">有三個數據行會<xref:System.Windows.Controls.ExceptionValidationRule>藉由<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>將屬性設定`true`為來指定。</span><span class="sxs-lookup"><span data-stu-id="4ba10-112">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="4ba10-113">當使用者輸入不正確值 (例如 [課程識別碼] 資料行中的非整數) 時, 資料格周圍會出現紅色框線。</span><span class="sxs-lookup"><span data-stu-id="4ba10-113">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="4ba10-114">您可以變更此預設驗證意見反應, 如下列程式所述。</span><span class="sxs-lookup"><span data-stu-id="4ba10-114">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="4ba10-115">自訂資料格驗證意見反應</span><span class="sxs-lookup"><span data-stu-id="4ba10-115">To customize cell validation feedback</span></span>  
  
- <span data-ttu-id="4ba10-116">將資料行的<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>屬性設定為適用于資料行編輯控制項的樣式。</span><span class="sxs-lookup"><span data-stu-id="4ba10-116">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="4ba10-117">因為編輯控制項是在執行時間建立的, 所以您無法使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>附加屬性, 就像使用簡單的控制項一樣。</span><span class="sxs-lookup"><span data-stu-id="4ba10-117">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="4ba10-118">下列範例會藉由加入具有驗證規則的三個數據行所共用的錯誤樣式, 來更新上一個範例。</span><span class="sxs-lookup"><span data-stu-id="4ba10-118">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="4ba10-119">當使用者輸入不正確值時, 樣式會變更儲存格背景色彩, 並加入工具提示。</span><span class="sxs-lookup"><span data-stu-id="4ba10-119">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="4ba10-120">請注意, 使用觸發程式來判斷是否有驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="4ba10-120">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="4ba10-121">這是必要的, 因為目前沒有適用于資料格的專用錯誤範本。</span><span class="sxs-lookup"><span data-stu-id="4ba10-121">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="4ba10-122">您可以藉由取代資料行所使用<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>的來執行更廣泛的自訂。</span><span class="sxs-lookup"><span data-stu-id="4ba10-122">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="4ba10-123">若要驗證單一資料列中的多個值</span><span class="sxs-lookup"><span data-stu-id="4ba10-123">To validate multiple values in a single row</span></span>  
  
1. <span data-ttu-id="4ba10-124">執行檢查<xref:System.Windows.Controls.ValidationRule>系結資料物件之多個屬性的子類別。</span><span class="sxs-lookup"><span data-stu-id="4ba10-124">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="4ba10-125">在您<xref:System.Windows.Controls.ValidationRule.Validate%2A>的方法執行中, `value`將參數值轉換<xref:System.Windows.Data.BindingGroup>成實例。</span><span class="sxs-lookup"><span data-stu-id="4ba10-125">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="4ba10-126">接著, 您可以透過<xref:System.Windows.Data.BindingGroup.Items%2A>屬性存取資料物件。</span><span class="sxs-lookup"><span data-stu-id="4ba10-126">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="4ba10-127">下列範例會示範此程式, 以驗證`StartDate` `Course`物件的屬性值是否早于其`EndDate`屬性值。</span><span class="sxs-lookup"><span data-stu-id="4ba10-127">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. <span data-ttu-id="4ba10-128">將驗證規則新增至<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="4ba10-128">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="4ba10-129">屬性可讓您直接存取<xref:System.Windows.Data.BindingGroup>實例<xref:System.Windows.Data.BindingGroup.ValidationRules%2A>的屬性, 以將控制項所使用的所有系結組成群組。 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A></span><span class="sxs-lookup"><span data-stu-id="4ba10-129">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="4ba10-130">下列範例會在 XAML <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4ba10-130">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="4ba10-131">屬性會設定為<xref:System.Windows.Controls.ValidationStep.UpdatedValue> , 因此只有在更新系結的資料物件之後, 才會進行驗證。 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A></span><span class="sxs-lookup"><span data-stu-id="4ba10-131">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="4ba10-132">當使用者指定早于開始日期的結束日期時, 資料列標題中會出現紅色驚嘆號 (!)。</span><span class="sxs-lookup"><span data-stu-id="4ba10-132">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="4ba10-133">您可以變更此預設驗證意見反應, 如下列程式所述。</span><span class="sxs-lookup"><span data-stu-id="4ba10-133">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="4ba10-134">自訂資料列驗證意見反應</span><span class="sxs-lookup"><span data-stu-id="4ba10-134">To customize row validation feedback</span></span>  
  
- <span data-ttu-id="4ba10-135">設定 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4ba10-135">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4ba10-136">這個屬性可讓您自訂個別<xref:System.Windows.Controls.DataGrid>控制項的資料列驗證意見反應。</span><span class="sxs-lookup"><span data-stu-id="4ba10-136">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="4ba10-137">您也可以使用隱含的資料列樣式來設定<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>屬性, 來影響多個控制項。</span><span class="sxs-lookup"><span data-stu-id="4ba10-137">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="4ba10-138">下列範例會以更可見的指標取代預設資料列驗證意見反應。</span><span class="sxs-lookup"><span data-stu-id="4ba10-138">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="4ba10-139">當使用者輸入不正確值時, 資料列標頭中會出現含有白色驚嘆號的紅色圓圈。</span><span class="sxs-lookup"><span data-stu-id="4ba10-139">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="4ba10-140">這會發生于資料列和資料格驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="4ba10-140">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="4ba10-141">相關聯的錯誤訊息會顯示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="4ba10-141">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="4ba10-142">範例</span><span class="sxs-lookup"><span data-stu-id="4ba10-142">Example</span></span>  
 <span data-ttu-id="4ba10-143">下列範例提供儲存格和資料列驗證的完整示範。</span><span class="sxs-lookup"><span data-stu-id="4ba10-143">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="4ba10-144">類別會提供範例資料物件,以支援交易。<xref:System.ComponentModel.IEditableObject> `Course`</span><span class="sxs-lookup"><span data-stu-id="4ba10-144">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="4ba10-145"><xref:System.Windows.Controls.DataGrid>控制項會與<xref:System.ComponentModel.IEditableObject>互動, 讓使用者可以藉由按下 ESC 來還原變更。</span><span class="sxs-lookup"><span data-stu-id="4ba10-145">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ba10-146">如果您使用 Visual Basic, 請在 mainwindow.xaml 的第一行中, 將取代`x:Class="DataGridValidation.MainWindow"`為。 `x:Class="MainWindow"`</span><span class="sxs-lookup"><span data-stu-id="4ba10-146">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="4ba10-147">若要測試驗證, 請嘗試下列動作:</span><span class="sxs-lookup"><span data-stu-id="4ba10-147">To test the validation, try the following:</span></span>  
  
- <span data-ttu-id="4ba10-148">在 [課程識別碼] 資料行中, 輸入非整數值。</span><span class="sxs-lookup"><span data-stu-id="4ba10-148">In the Course ID column, enter a non-integer value.</span></span>  
  
- <span data-ttu-id="4ba10-149">在 [結束日期] 資料行中, 輸入早于開始日期的日期。</span><span class="sxs-lookup"><span data-stu-id="4ba10-149">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
- <span data-ttu-id="4ba10-150">刪除 [課程識別碼]、[開始日期] 或 [結束日期] 中的值。</span><span class="sxs-lookup"><span data-stu-id="4ba10-150">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
- <span data-ttu-id="4ba10-151">若要復原不正確資料格值, 請將游標放回儲存格中, 然後按下 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="4ba10-151">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
- <span data-ttu-id="4ba10-152">若要在當前儲存格處於編輯模式時復原整個資料列的變更, 請按 ESC 鍵兩次。</span><span class="sxs-lookup"><span data-stu-id="4ba10-152">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
- <span data-ttu-id="4ba10-153">發生驗證錯誤時, 請將滑鼠指標移到資料列行首中的指示器上方, 以查看相關聯的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4ba10-153">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="4ba10-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ba10-154">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="4ba10-155">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4ba10-155">DataGrid</span></span>](datagrid.md)
- [<span data-ttu-id="4ba10-156">資料繫結</span><span class="sxs-lookup"><span data-stu-id="4ba10-156">Data Binding</span></span>](../data/data-binding-wpf.md)
- [<span data-ttu-id="4ba10-157">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="4ba10-157">Implement Binding Validation</span></span>](../data/how-to-implement-binding-validation.md)
- [<span data-ttu-id="4ba10-158">對自訂物件實作驗證邏輯</span><span class="sxs-lookup"><span data-stu-id="4ba10-158">Implement Validation Logic on Custom Objects</span></span>](../data/how-to-implement-validation-logic-on-custom-objects.md)
