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
ms.openlocfilehash: e3be25fecc58ba41dbb5b2e904eddcb9c2b3c98a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371082"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>HOW TO：使用 DataGrid 控制項實作驗證
<xref:System.Windows.Controls.DataGrid>控制項可讓您執行的資料格 」 和 「 資料列層級的驗證。 資料格層級驗證，您驗證繫結的資料物件的個別屬性，當使用者更新的值。 資料列層級驗證，您會驗證整個資料的物件，當使用者認可變更的資料列。 您也可以提供自訂的視覺化回饋，對於驗證錯誤，或使用預設的視覺化回饋，<xref:System.Windows.Controls.DataGrid>控制項提供。  
  
 下列程序描述如何套用驗證規則來<xref:System.Windows.Controls.DataGrid>繫結和自訂的視覺化回饋。  
  
### <a name="to-validate-individual-cell-values"></a>若要驗證個別的資料格的值  
  
-   使用具有資料行的繫結上指定一個或多個驗證規則。 這是類似於驗證簡單的控制項中的資料中所述[資料繫結概觀](../data/data-binding-overview.md)。  
  
     下列範例所示<xref:System.Windows.Controls.DataGrid>控制項繫結至商務物件的不同屬性的四個資料行。 三個資料行的指定<xref:System.Windows.Controls.ExceptionValidationRule>splittunneling<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>屬性設`true`。  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     當使用者輸入無效的值 （例如非整數課程 ID 資料行中） 時，則會在資料格周圍出現紅色框線。 您可以變更這個預設驗證回應如下列程序中所述。  
  
### <a name="to-customize-cell-validation-feedback"></a>若要自訂資料格驗證回應  
  
-   設定資料行的<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>資料行的編輯控制項適合的樣式屬性。 因為編輯控制項建立在執行階段中，您無法使用<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>附加屬性，就像使用簡單的控制項。  
  
     下列範例會更新先前的範例，加上共用的驗證規則的三個資料行的錯誤樣式。 當使用者輸入無效的值時，樣式會變更的資料格背景色彩，以及加入工具提示。 請注意，若要判斷是否有驗證錯誤的觸發程序使用。 這是必要的因為目前沒有資料格的專用的錯誤範本。  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     您可以實作更廣泛的自訂取代<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>資料行使用。  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>若要驗證的單一資料列中的多個值  
  
1.  實作<xref:System.Windows.Controls.ValidationRule>檢查多個屬性的繫結的資料物件的子類別。 在您<xref:System.Windows.Controls.ValidationRule.Validate%2A>轉換方法實作`value`參數值以<xref:System.Windows.Data.BindingGroup>執行個體。 然後，您就可以存取資料物件，可透過<xref:System.Windows.Data.BindingGroup.Items%2A>屬性。  
  
     下列範例示範此程序來驗證是否`StartDate`屬性值`Course`物件是早於其`EndDate`屬性值。  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  新增驗證規則，以<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>集合。 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>屬性會提供直接存取<xref:System.Windows.Data.BindingGroup.ValidationRules%2A>屬性<xref:System.Windows.Data.BindingGroup>群組控制項所使用的所有繫結的執行個體。  
  
     下列範例會設定<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>在 XAML 中的屬性。 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>屬性設定為<xref:System.Windows.Controls.ValidationStep.UpdatedValue>如此才會更新繫結的資料物件，就會發生驗證。  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     當使用者指定結束日期必須早於開始日期時，紅色驚嘆號 （！） 會出現在資料列標頭中。 您可以變更這個預設驗證回應如下列程序中所述。  
  
### <a name="to-customize-row-validation-feedback"></a>若要自訂的資料列驗證回應  
  
-   設定 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 屬性。 這個屬性可讓您自訂個別的資料列驗證回應<xref:System.Windows.Controls.DataGrid>控制項。 您也可以使用隱含資料列樣式設定來影響多個控制項<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>屬性。  
  
     下列範例會將預設資料列驗證回應取代更明顯可見的指標。 當使用者輸入無效的值時，內含白色驚嘆號的紅色圓圈會出現在資料列標頭中。 發生這種情況的資料列和資料格的驗證錯誤。 相關聯的錯誤訊息會顯示在工具提示。  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>範例  
 下列範例會提供完整的示範儲存格和資料列的驗證。 `Course`類別會提供範例資料物件實作<xref:System.ComponentModel.IEditableObject>為支援交易。 <xref:System.Windows.Controls.DataGrid>與控制項互動<xref:System.ComponentModel.IEditableObject>，讓使用者可以按下 esc 鍵還原變更。  
  
> [!NOTE]
>  如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="DataGridValidation.MainWindow"`與`x:Class="MainWindow"`。  
  
 若要測試驗證，請嘗試下列方法：  
  
-   在課程識別碼 欄中，輸入非整數值。  
  
-   結束日期資料行中輸入日期早於開始日期。  
  
-   刪除在課程 ID、 開始日期或結束日期值。  
  
-   若要復原無效的資料格的值，將游標放回資料格中，並按下 ESC 鍵。  
  
-   若要到目前的儲存格處於編輯模式時，請復原整個資料列的變更，請按 ESC 鍵兩次。  
  
-   發生驗證錯誤時，將滑鼠指標停留在指標資料列標頭，以查看相關聯的錯誤訊息。  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [資料繫結](../data/data-binding-wpf.md)
- [實作繫結驗證](../data/how-to-implement-binding-validation.md)
- [對自訂物件實作驗證邏輯](../data/how-to-implement-validation-logic-on-custom-objects.md)
