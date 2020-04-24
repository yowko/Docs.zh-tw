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
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>如何：使用 DataGrid 控制項實作驗證
該<xref:System.Windows.Controls.DataGrid>控制項使您能夠在儲存格和行等級執行驗證。 使用單元格級驗證,當使用者更新值時,可以驗證綁定數據對象的單個屬性。 使用行級驗證,當使用者將更改提交到行時,可以驗證整個數據物件。 您還可以為驗證錯誤提供自定義的可視反饋,或使用<xref:System.Windows.Controls.DataGrid>控制項提供的預設視覺反饋。  
  
 以下過程介紹如何將驗證規則應用於<xref:System.Windows.Controls.DataGrid>綁定並自定義可視反饋。  
  
### <a name="to-validate-individual-cell-values"></a>驗證儲存格值  
  
- 在列使用的綁定上指定一個或多個驗證規則。 這類似於在簡單控件中驗證數據,如[數據綁定概述](../../../desktop-wpf/data/data-binding-overview.md)中所述。  
  
     下面的示例顯示一個<xref:System.Windows.Controls.DataGrid>控件,該控件的四列綁定到業務物件的不同屬性。 三列<xref:System.Windows.Controls.ExceptionValidationRule>透過<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>屬性設定為`true`指定 。  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     當使用者輸入無效值(如課程 ID 列中的非整數)時,單元格周圍會出現紅色邊框。 您可以按照以下過程所述更改此默認驗證反饋。  
  
### <a name="to-customize-cell-validation-feedback"></a>自訂儲存格驗證回饋  
  
- 將列的屬性<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>設置為適合列編輯控制項的樣式。 由於編輯控制項是在執行時創建的,因此不能像使用簡單控制項那樣<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>使用附加屬性。  
  
     下面的範例透過添加由三列共用的具有驗證規則的錯誤樣式來更新前面的範例。 當使用者輸入無效值時,樣式將更改單元格背景顏色並添加工具提示。 請注意使用觸發器來確定是否存在驗證錯誤。 這是必需的,因為當前沒有專用的單元格錯誤範本。  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     您可以通過替換列使用來<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>實現 更廣泛的自定義。  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>驗證一列中的多個值  
  
1. 實現一<xref:System.Windows.Controls.ValidationRule>個子類,該子類檢查綁定數據物件的多個屬性。 在方法<xref:System.Windows.Controls.ValidationRule.Validate%2A>實現中,`value`將參數值轉換<xref:System.Windows.Data.BindingGroup>為 實例。 然後,您可以<xref:System.Windows.Data.BindingGroup.Items%2A>通過 屬性訪問數據物件。  
  
     下面的範例演示了此過程,以驗證`StartDate``Course`物件的屬性值是否早於`EndDate`其 屬性值。  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. 將驗證規則添加到<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>集合中。 該<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>屬性提供<xref:System.Windows.Data.BindingGroup.ValidationRules%2A><xref:System.Windows.Data.BindingGroup>對 實例屬性的直接訪問,該實例對控制項使用的所有綁定進行分組。  
  
     下面的範例在 XAML<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>中設置 屬性。 屬性<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>設置<xref:System.Windows.Controls.ValidationStep.UpdatedValue>為 ,以便驗證僅在更新綁定數據物件後進行。  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     當使用者指定早於開始日期的結束日期時,行標題中將顯示一個紅色感歎號 (!)。 您可以按照以下過程所述更改此默認驗證反饋。  
  
### <a name="to-customize-row-validation-feedback"></a>自訂行驗證回饋  
  
- 設定 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 屬性。 此屬性使您能夠為各個<xref:System.Windows.Controls.DataGrid>控制件自定義行驗證回饋。 還可以通過使用隱式行樣式來設置<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>屬性來影響多個控制件。  
  
     下面的範例將預設行驗證反饋替換為更可見的指示器。 當使用者輸入無效值時,行標題中將顯示一個帶有白色感嘆號的紅色圓圈。 對於行和單元驗證錯誤,都會發生這種情況。 關聯的錯誤消息將顯示在工具提示中。  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>範例  
 下面的範例提供了儲存格和行驗證的完整演示。 類`Course`提供一個範例數據物件,<xref:System.ComponentModel.IEditableObject>該物件實現以支援事務。 該<xref:System.Windows.Controls.DataGrid>控件與<xref:System.ComponentModel.IEditableObject>這些控制者互動,使用戶能夠透過按 ESC 還原更改。  
  
> [!NOTE]
> 如果使用 Visual Basic,則在 MainWindow.xaml`x:Class="DataGridValidation.MainWindow"`的第`x:Class="MainWindow"`一行中, 取代為 。  
  
 要測試驗證,請嘗試以下操作:  
  
- 在"課程ID"列中,輸入非整數值。  
  
- 在"結束日期"列中,輸入早於開始日期的日期。  
  
- 刪除課程 ID、開始日期或結束日期中的值。  
  
- 要撤銷無效的儲存格值,請將游標放回單元格中,然後按 ESC 鍵。  
  
- 要在當前儲存格處於編輯模式時撤消整個行的更改,請按 ESC 鍵兩次。  
  
- 發生驗證錯誤時,將滑鼠指標移到行標題中的指示器上以查看關聯的錯誤訊息。  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [資料繫結](../../../desktop-wpf/data/data-binding-overview.md)
- [實作連結](../data/how-to-implement-binding-validation.md)
- [在自訂物件上實現驗證邏輯](../data/how-to-implement-validation-logic-on-custom-objects.md)
