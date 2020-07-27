---
title: TextBox 樣式和範本
description: 瞭解 Windows Presentation Foundation TextBox 控制項的樣式和範本。 修改 ControlTemplate，讓控制項具有獨特的外觀。
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164730"
---
# <a name="textbox-styles-and-templates"></a>TextBox 樣式和範本
本主題描述控制項的樣式和範本 <xref:System.Windows.Controls.TextBox> 。 您可以修改預設值 <xref:System.Windows.Controls.ControlTemplate> ，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="textbox-parts"></a>TextBox 元件  
 下表列出控制項的已命名元件 <xref:System.Windows.Controls.TextBox> 。  
  
|部分|類型|描述|  
|-|-|-|  
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|可以包含的視覺元素 <xref:System.Windows.FrameworkElement> 。 的文字 <xref:System.Windows.Controls.TextBox> 會顯示在此元素中。|  
  
## <a name="textbox-states"></a>文字方塊狀態  
 下表列出控制項的視覺狀態 <xref:System.Windows.Controls.TextBox> 。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|正常|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|已停用|CommonStates|已停用控制項。|  
|唯讀|CommonStates|使用者無法變更中的文字 <xref:System.Windows.Controls.TextBox> 。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|有效|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `false` 。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性的 `true` 焦點是控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="textbox-controltemplate-example"></a>TextBox ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TextBox> 控制項的。  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
