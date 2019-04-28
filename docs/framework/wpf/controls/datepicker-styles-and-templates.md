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
ms.openlocfilehash: 5c8e199dd7123e1490c8a836a62ffea158797eb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912245"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker 樣式和範本
本主題描述的樣式和範本<xref:System.Windows.Controls.DatePicker>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="datepicker-parts"></a>日期選擇器組件  
 下表列出的具名組件<xref:System.Windows.Controls.DatePicker>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|控制項的根目錄。|  
|PART_Button|<xref:System.Windows.Controls.Button>|開啟和關閉的按鈕<xref:System.Windows.Controls.Calendar>。|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|可讓您輸入的日期文字方塊中。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|快顯<xref:System.Windows.Controls.DatePicker>控制項。|  
  
## <a name="datepicker-states"></a>日期選擇器狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.DatePicker>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.DatePicker>已停用。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DatePickerTextBox>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|包含初始的文字中的項目<xref:System.Windows.Controls.DatePicker>。|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|可包含的視覺元素<xref:System.Windows.FrameworkElement>。 文字<xref:System.Windows.Controls.TextBox>會顯示此項目中。|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.DatePickerTextBox>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>已停用。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.Primitives.DatePickerTextBox>。|  
|ReadOnly|CommonStates|使用者無法變更中的文字<xref:System.Windows.Controls.Primitives.DatePickerTextBox>。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|浮水印|WatermarkStates|控制項會顯示其初始文字。  <xref:System.Windows.Controls.Primitives.DatePickerTextBox>處於執行狀態，當使用者未輸入文字，或選取日期。|  
|Unwatermarked|WatermarkStates|使用者輸入文字<xref:System.Windows.Controls.Primitives.DatePickerTextBox>或選取的日期<xref:System.Windows.Controls.DatePicker>。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.DatePicker>控制項。  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [樣式設定和範本化](styling-and-templating.md)
- [透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)
