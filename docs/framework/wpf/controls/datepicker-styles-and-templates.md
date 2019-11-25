---
title: DatePicker 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: 002d1c3271827239dcd3a319621f66fb5bc68d4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283778"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker 樣式和範本
本主題描述 <xref:System.Windows.Controls.DatePicker> 控制項的樣式和範本。 您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="datepicker-parts"></a>DatePicker 元件  
 下表列出 <xref:System.Windows.Controls.DatePicker> 控制項的已命名元件。  
  
|組件|輸入|描述|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|控制項的根。|  
|PART_Button|<xref:System.Windows.Controls.Button>|開啟和關閉 <xref:System.Windows.Controls.Calendar>的按鈕。|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|可讓您輸入日期的文字方塊。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|<xref:System.Windows.Controls.DatePicker> 控制項的快顯。|  
  
## <a name="datepicker-states"></a>DatePicker 狀態  
 下表列出 <xref:System.Windows.Controls.DatePicker> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.DatePicker> 已停用。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox 元件  
 下表列出 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 控制項的已命名元件。  
  
|組件|輸入|描述|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|元素，其中包含 <xref:System.Windows.Controls.DatePicker>中的初始文字。|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|可以包含 <xref:System.Windows.FrameworkElement>的視覺元素。 <xref:System.Windows.Controls.TextBox> 的文字會顯示在此元素中。|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> 已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.Primitives.DatePickerTextBox>上。|  
|ReadOnly|CommonStates|使用者無法變更 <xref:System.Windows.Controls.Primitives.DatePickerTextBox>中的文字。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|浮水印|WatermarkStates|控制項會顯示其初始文字。  當使用者未輸入文字或選取日期時，<xref:System.Windows.Controls.Primitives.DatePickerTextBox> 處於狀態。|  
|Unwatermarked|WatermarkStates|使用者已在 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 中輸入文字，或在 <xref:System.Windows.Controls.DatePicker>中選取日期。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，且控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性 `true`，而且控制項沒有焦點。|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.DatePicker> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
