---
title: "如何：使用 DataGrid 控制項實作驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78846e2b6a1d73e011441b0ccb46b8aad365d5dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="66a6a-102">如何：使用 DataGrid 控制項實作驗證</span><span class="sxs-lookup"><span data-stu-id="66a6a-102">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="66a6a-103"><xref:System.Windows.Controls.DataGrid>控制項可讓您執行資料格和資料列層級的驗證。</span><span class="sxs-lookup"><span data-stu-id="66a6a-103">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="66a6a-104">資料格層級驗證時，您會驗證個別屬性繫結的資料物件的使用者更新值時。</span><span class="sxs-lookup"><span data-stu-id="66a6a-104">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="66a6a-105">資料列層級驗證時，您會驗證整個資料的物件，當使用者將變更認可至資料列。</span><span class="sxs-lookup"><span data-stu-id="66a6a-105">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="66a6a-106">您也可以提供自訂的視覺化回饋，對於驗證錯誤，或使用預設的視覺化回饋，<xref:System.Windows.Controls.DataGrid>控制項提供。</span><span class="sxs-lookup"><span data-stu-id="66a6a-106">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="66a6a-107">下列程序描述如何套用驗證規則加入至<xref:System.Windows.Controls.DataGrid>繫結和自訂的視覺化回應。</span><span class="sxs-lookup"><span data-stu-id="66a6a-107">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="66a6a-108">若要驗證個別資料格的值</span><span class="sxs-lookup"><span data-stu-id="66a6a-108">To validate individual cell values</span></span>  
  
-   <span data-ttu-id="66a6a-109">使用具有資料行的繫結上指定一個或多個驗證規則。</span><span class="sxs-lookup"><span data-stu-id="66a6a-109">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="66a6a-110">這是類似於驗證簡單的控制項中的資料中所述[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="66a6a-110">This is similar to validating data in simple controls, as described in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="66a6a-111">下列範例所示<xref:System.Windows.Controls.DataGrid>控制項與四個資料行繫結至不同的商務物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="66a6a-111">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="66a6a-112">三個資料行的指定<xref:System.Windows.Controls.ExceptionValidationRule>藉由設定<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="66a6a-112">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="66a6a-113">當使用者輸入無效的值 （例如非整數的課程識別碼資料行） 時，資料格周圍會出現紅色框線。</span><span class="sxs-lookup"><span data-stu-id="66a6a-113">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="66a6a-114">您可以變更這個預設驗證回應下列程序中所述。</span><span class="sxs-lookup"><span data-stu-id="66a6a-114">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="66a6a-115">若要自訂儲存格驗證回應</span><span class="sxs-lookup"><span data-stu-id="66a6a-115">To customize cell validation feedback</span></span>  
  
-   <span data-ttu-id="66a6a-116">設定的資料行<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>樣式屬性適當資料行的編輯控制項。</span><span class="sxs-lookup"><span data-stu-id="66a6a-116">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="66a6a-117">因為編輯控制項在執行階段建立，您無法使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>附加屬性，就像使用簡單的控制項一樣。</span><span class="sxs-lookup"><span data-stu-id="66a6a-117">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="66a6a-118">下列範例會藉由新增共用的驗證規則的三個資料行錯誤樣式更新前一個範例。</span><span class="sxs-lookup"><span data-stu-id="66a6a-118">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="66a6a-119">當使用者輸入無效的值時，將儲存格的背景色彩變更樣式，以及加入工具提示。</span><span class="sxs-lookup"><span data-stu-id="66a6a-119">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="66a6a-120">請注意若要判斷是否有驗證錯誤的觸發程序使用。</span><span class="sxs-lookup"><span data-stu-id="66a6a-120">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="66a6a-121">這是必要的因為目前沒有儲存格專用的錯誤範本。</span><span class="sxs-lookup"><span data-stu-id="66a6a-121">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="66a6a-122">您可以實作更廣泛的自訂取代<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>資料行使用。</span><span class="sxs-lookup"><span data-stu-id="66a6a-122">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="66a6a-123">若要驗證單一資料列中的多個值</span><span class="sxs-lookup"><span data-stu-id="66a6a-123">To validate multiple values in a single row</span></span>  
  
1.  <span data-ttu-id="66a6a-124">實作<xref:System.Windows.Controls.ValidationRule>會檢查繫結的資料物件的多個屬性的子類別。</span><span class="sxs-lookup"><span data-stu-id="66a6a-124">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="66a6a-125">在您<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法實作中，轉換`value`參數值以<xref:System.Windows.Data.BindingGroup>執行個體。</span><span class="sxs-lookup"><span data-stu-id="66a6a-125">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="66a6a-126">然後，您就可以存取的資料物件，透過<xref:System.Windows.Data.BindingGroup.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="66a6a-126">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="66a6a-127">下列範例將示範此程序，驗證是否`StartDate`屬性值`Course`物件是早於其`EndDate`屬性值。</span><span class="sxs-lookup"><span data-stu-id="66a6a-127">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  <span data-ttu-id="66a6a-128">加入驗證規則<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>集合。</span><span class="sxs-lookup"><span data-stu-id="66a6a-128">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="66a6a-129"><xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>屬性可直接存取<xref:System.Windows.Data.BindingGroup.ValidationRules%2A>屬性<xref:System.Windows.Data.BindingGroup>群組控制項所使用的所有繫結的執行個體。</span><span class="sxs-lookup"><span data-stu-id="66a6a-129">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="66a6a-130">下列範例會設定<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>在 XAML 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="66a6a-130">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="66a6a-131"><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>屬性設定為<xref:System.Windows.Controls.ValidationStep.UpdatedValue>以便只在更新繫結的資料物件之後，就會發生驗證。</span><span class="sxs-lookup"><span data-stu-id="66a6a-131">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="66a6a-132">當使用者指定的結束日期早於開始日期時，紅色驚嘆號 （！） 會出現在資料列標頭中。</span><span class="sxs-lookup"><span data-stu-id="66a6a-132">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="66a6a-133">您可以變更這個預設驗證回應下列程序中所述。</span><span class="sxs-lookup"><span data-stu-id="66a6a-133">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="66a6a-134">若要自訂的資料列驗證回應</span><span class="sxs-lookup"><span data-stu-id="66a6a-134">To customize row validation feedback</span></span>  
  
-   <span data-ttu-id="66a6a-135">設定 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="66a6a-135">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="66a6a-136">這個屬性可讓您自訂個別的資料列驗證回應<xref:System.Windows.Controls.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="66a6a-136">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="66a6a-137">您也可以使用隱含資料列樣式，將會影響多個控制項<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="66a6a-137">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="66a6a-138">下列範例會將預設列驗證回應取代更明顯可見的指標。</span><span class="sxs-lookup"><span data-stu-id="66a6a-138">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="66a6a-139">當使用者輸入無效的值時，內含白色驚嘆號的紅色圓圈會出現在資料列標頭中。</span><span class="sxs-lookup"><span data-stu-id="66a6a-139">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="66a6a-140">這個問題發生的資料列和資料格的驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="66a6a-140">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="66a6a-141">相關聯的錯誤訊息會顯示在工具提示。</span><span class="sxs-lookup"><span data-stu-id="66a6a-141">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="66a6a-142">範例</span><span class="sxs-lookup"><span data-stu-id="66a6a-142">Example</span></span>  
 <span data-ttu-id="66a6a-143">下列範例提供完整示範儲存格和資料列驗證。</span><span class="sxs-lookup"><span data-stu-id="66a6a-143">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="66a6a-144">`Course`類別會提供範例資料物件實作<xref:System.ComponentModel.IEditableObject>為支援交易。</span><span class="sxs-lookup"><span data-stu-id="66a6a-144">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="66a6a-145"><xref:System.Windows.Controls.DataGrid>與控制項互動<xref:System.ComponentModel.IEditableObject>，讓使用者可以按下 esc 鍵還原變更。</span><span class="sxs-lookup"><span data-stu-id="66a6a-145">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66a6a-146">如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="DataGridValidation.MainWindow"`與`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="66a6a-146">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="66a6a-147">若要測試驗證，請嘗試下列方法：</span><span class="sxs-lookup"><span data-stu-id="66a6a-147">To test the validation, try the following:</span></span>  
  
-   <span data-ttu-id="66a6a-148">在課程 ID 資料行中，輸入非整數值。</span><span class="sxs-lookup"><span data-stu-id="66a6a-148">In the Course ID column, enter a non-integer value.</span></span>  
  
-   <span data-ttu-id="66a6a-149">結束日期資料行中輸入的日期早於開始日期。</span><span class="sxs-lookup"><span data-stu-id="66a6a-149">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
-   <span data-ttu-id="66a6a-150">刪除在課程 ID、 開始日期或結束日期值。</span><span class="sxs-lookup"><span data-stu-id="66a6a-150">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
-   <span data-ttu-id="66a6a-151">若要復原無效的資料格的值，請將游標放在資料格回並按下 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="66a6a-151">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
-   <span data-ttu-id="66a6a-152">若要復原變更整個資料列，目前儲存格處於編輯模式時，按 ESC 鍵兩次。</span><span class="sxs-lookup"><span data-stu-id="66a6a-152">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
-   <span data-ttu-id="66a6a-153">發生驗證錯誤時，將滑鼠指標停留在指標資料列標頭，以查看相關的錯誤訊息上。</span><span class="sxs-lookup"><span data-stu-id="66a6a-153">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="66a6a-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="66a6a-154">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="66a6a-155">DataGrid</span><span class="sxs-lookup"><span data-stu-id="66a6a-155">DataGrid</span></span>](../../../../docs/framework/wpf/controls/datagrid.md)  
 [<span data-ttu-id="66a6a-156">資料繫結</span><span class="sxs-lookup"><span data-stu-id="66a6a-156">Data Binding</span></span>](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [<span data-ttu-id="66a6a-157">實作繫結驗證</span><span class="sxs-lookup"><span data-stu-id="66a6a-157">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="66a6a-158">對自訂物件實作驗證邏輯</span><span class="sxs-lookup"><span data-stu-id="66a6a-158">Implement Validation Logic on Custom Objects</span></span>](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
