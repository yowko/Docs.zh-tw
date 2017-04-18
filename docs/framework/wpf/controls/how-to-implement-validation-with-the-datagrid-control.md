---
title: "如何：使用 DataGrid 控制項實作驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataGrid [WPF], 驗證"
  - "驗證 [WPF], DataGrid"
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用 DataGrid 控制項實作驗證
<xref:System.Windows.Controls.DataGrid> 控制項可讓您在儲存格和資料列層級執行驗證。  使用儲存格層級驗證，可在使用者更新值時驗證所繫結資料物件的個別屬性。  使用資料列層級驗證，可在使用者認可資料列變更時驗證整個資料物件。  您也可以提供驗證錯誤的自訂視覺化回應，或使用 <xref:System.Windows.Controls.DataGrid> 控制項提供的預設視覺化回應。  
  
 下列程序描述如何將驗證規則套用至 <xref:System.Windows.Controls.DataGrid> 繫結，以及自訂視覺化回應。  
  
### 若要驗證個別儲存格值  
  
-   針對與資料行搭配使用的繫結，指定一個或多個驗證規則。  這類似於驗證簡單控制項中的資料 \(如[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)所述\)。  
  
     下列範例顯示 <xref:System.Windows.Controls.DataGrid> 控制項，其具有四個資料行繫結至商務物件的不同屬性。  其中三個資料行將 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 屬性設為 `true`，指定 <xref:System.Windows.Controls.ExceptionValidationRule>。  
  
     [!code-xml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     如果使用者輸入無效值 \(例如 Course ID 資料行中的非整數\)，則儲存格周圍會出現紅色框線。  您可以如下列程序所述變更這個預設驗證回應。  
  
### 若要自訂儲存格驗證回應  
  
-   將資料行的 <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> 屬性設為資料行編輯控制項適用的樣式。  因為編輯控制項是在執行階段建立，所以您無法像使用簡單控制項一樣地使用 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=fullName> 附加屬性。  
  
     下列範例使用驗證規則加入三個資料行共用的錯誤樣式，來更新上一個範例。  如果使用者輸入無效值，則樣式會變更儲存格背景色彩，並加入工具提示。  請注意觸發程式的使用，以判斷是否發生驗證錯誤。  這是必要的條件，因為目前沒有儲存格專用的錯誤範本。  
  
     [!code-xml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     取代資料行使用的 <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>，就可以實作更廣泛的自訂。  
  
### 若要驗證單一資料列中的多個值  
  
1.  實作 <xref:System.Windows.Controls.ValidationRule> 子類別，檢查繫結之資料物件的多個屬性。  在您的 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法實作中，將 `value` 參數值轉型為 <xref:System.Windows.Data.BindingGroup> 執行個體。  然後，您就可以透過 <xref:System.Windows.Data.BindingGroup.Items%2A> 屬性來存取資料物件。  
  
     下列範例示範這個程序如何驗證 `Course` 物件的 `StartDate` 屬性值是否早於其 `EndDate` 屬性值。  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  將驗證規則加入至 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=fullName> 集合。  <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> 屬性可直接存取 <xref:System.Windows.Data.BindingGroup> 執行個體的 <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> 屬性，而這個執行個體群組控制項所使用的所有繫結。  
  
     下列範例會以 XAML 設定 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> 屬性。  <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 屬性會設為 <xref:System.Windows.Controls.ValidationStep>，只在更新繫結的資料物件之後進行驗證。  
  
     [!code-xml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     如果使用者指定的結束日期早於開始日期，則會在資料列標頭出現紅色驚嘆號 \(\!\)。  您可以如下列程序所述變更這個預設驗證回應。  
  
### 若要自訂資料列驗證回應  
  
-   設定 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=fullName> 屬性。  這個屬性可讓您自訂個別 <xref:System.Windows.Controls.DataGrid> 控制項的資料列驗證回應。  您也可以使用隱含的資料列樣式設定 <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=fullName> 屬性，以影響多個控制項。  
  
     下列範例會以更容易辨識的指標來取代預設資料列驗證回應。  如果使用者輸入無效值，則會在資料列標頭出現內含白色驚嘆號的紅色圓圈。  這發生於資料列和儲存格驗證錯誤時。  相關的錯誤訊息會顯示在工具提示中。  
  
     [!code-xml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## 範例  
 下列範例提供儲存格和資料列驗證的完整示範。  `Course` 類別提供可實作 <xref:System.ComponentModel.IEditableObject> 的範例資料物件，以支援交易。  <xref:System.Windows.Controls.DataGrid> 控制項會與 <xref:System.ComponentModel.IEditableObject> 互動，讓使用者可以按 ESC 鍵還原變更。  
  
> [!NOTE]
>  如果您是使用 Visual Basic，則請將 MainWindow.xaml 的第一行中的 `x:Class="DataGridValidation.MainWindow"` 取代為 `x:Class="MainWindow"`。  
  
 若要測試驗證，請嘗試下列作業：  
  
-   在 Course ID 資料行中，輸入非整數值。  
  
-   在 End Date 資料行中，輸入早於 Start Date 的日期。  
  
-   刪除 Course ID、Start Date 或 End Date 中的值。  
  
-   若要復原無效的儲存格值，請將游標放回儲存格，並按 ESC 鍵。  
  
-   若要在目前儲存格處於編輯模式時復原整個資料列的變更，請按兩次 ESC 鍵。  
  
-   發生驗證錯誤時，請將滑鼠指標移至資料列標頭的指標上方，以查看相關錯誤訊息。  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## 請參閱  
 <xref:System.Windows.Controls.DataGrid>   
 [DataGrid](../../../../docs/framework/wpf/controls/datagrid.md)   
 [資料繫結](../../../../docs/framework/wpf/data/data-binding-wpf.md)   
 [實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [對自訂物件實作驗證邏輯](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)