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
ms.openlocfilehash: 887698bdaebf7bc5ddac8997167589d9fbd3dd4d
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960372"
---
# <a name="combobox-styles-and-templates"></a>ComboBox 樣式和範本
本主題描述 <xref:System.Windows.Controls.ComboBox> 控制項的樣式和範本。 您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="combobox-parts"></a>ComboBox 元件  
 下表列出 <xref:System.Windows.Controls.ComboBox> 控制項的已命名元件。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|包含 <xref:System.Windows.Controls.ComboBox>的文字。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|下拉式方塊中包含專案的下拉式方塊。|  
  
 當您建立 <xref:System.Windows.Controls.ComboBox>的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能會在 <xref:System.Windows.Controls.ScrollViewer>中包含 <xref:System.Windows.Controls.ItemsPresenter>。 （<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.ComboBox>中的每個專案，<xref:System.Windows.Controls.ScrollViewer> 可在控制項內進行滾動）。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer>的直接子系，您必須為 <xref:System.Windows.Controls.ItemsPresenter> 指定名稱，`ItemsPresenter`。  
  
## <a name="combobox-states"></a>ComboBox 狀態  
 下表列出 <xref:System.Windows.Controls.ComboBox> 控制項的狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|Disabled|CommonStates|已停用控制項。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.ComboBox> 控制項上。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|FocusedDropDown|FocusStates|<xref:System.Windows.Controls.ComboBox> 的下拉式會有焦點。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
|Editable|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 屬性為 `true`。|  
|編輯|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 屬性為 `false`。|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem 元件  
 <xref:System.Windows.Controls.ComboBoxItem> 控制項沒有任何已命名的元件。  
  
## <a name="comboboxitem-states"></a>ComboBoxItem 狀態  
 下表列出 <xref:System.Windows.Controls.ComboBoxItem> 控制項的狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|Disabled|CommonStates|已停用控制項。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.ComboBoxItem> 控制項上。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|Selected|SelectionStates|目前已選取專案。|  
|未選取|SelectionStates|項目未獲選取。|  
|SelectedUnfocused|SelectionStates|項目已獲選取，但未取得焦點。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="combobox-controltemplate-example"></a>ComboBox ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ComboBox> 控制項和相關聯類型的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
