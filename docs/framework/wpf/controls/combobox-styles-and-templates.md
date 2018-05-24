---
title: ComboBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: 4dbffd2dcc0b2f798f6e75d01b58df54b09229e8
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="combobox-styles-and-templates"></a>ComboBox 樣式和範本
本主題描述樣式和範本<xref:System.Windows.Controls.ComboBox>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="combobox-parts"></a>下拉式方塊部分  
 下表列出的具名組件<xref:System.Windows.Controls.ComboBox>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|包含文字的<xref:System.Windows.Controls.ComboBox>。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|在下拉式清單，其中包含下拉式方塊中的項目。|  
  
 當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ComboBox>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.ComboBox>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。  
  
## <a name="combobox-states"></a>下拉式方塊的狀態  
 下表列出的狀態<xref:System.Windows.Controls.ComboBox>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|已停用控制項。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.ComboBox>控制項。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|FocusedDropDown|FocusStates|針對下拉式<xref:System.Windows.Controls.ComboBox>具有焦點。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
|可編輯|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 屬性為 `true`。|  
|無法編輯|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 屬性為 `false`。|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem 組件  
 <xref:System.Windows.Controls.ComboBoxItem>控制項沒有任何已命名的組件。  
  
## <a name="comboboxitem-states"></a>ComboBoxItem 狀態  
 下表列出的狀態<xref:System.Windows.Controls.ComboBoxItem>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|已停用控制項。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.ComboBox>控制項。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|已選取|SelectionStates|目前選取項目。|  
|未選取|SelectionStates|項目未獲選取。|  
|SelectedUnfocused|SelectionStates|項目已獲選取，但未取得焦點。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="combobox-controltemplate-example"></a>下拉式方塊 ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ComboBox>控制項和相關聯的類型。  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
