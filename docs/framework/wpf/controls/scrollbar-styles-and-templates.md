---
title: ScrollBar 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671975"
---
# <a name="scrollbar-styles-and-templates"></a>ScrollBar 樣式和範本
本主題描述<xref:System.Windows.Controls.Primitives.ScrollBar>控制項的樣式和範本。 您可以修改預設值<xref:System.Windows.Controls.ControlTemplate> , 為控制項提供獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="scrollbar-parts"></a>捲軸部分  
 下表列出<xref:System.Windows.Controls.Primitives.ScrollBar>控制項的已命名元件。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|元素的容器, 這個專案表示的位置<xref:System.Windows.Controls.Primitives.ScrollBar>。|  
  
## <a name="scrollbar-states"></a>捲軸狀態  
 下表列出<xref:System.Windows.Controls.Primitives.ScrollBar>控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|已停用|CommonStates|已停用控制項。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> , 而附加屬性是`false`。|  
|InvalidFocused|ValidationStates|附加屬性為`true` , 且控制項具有焦點。 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>|  
|InvalidUnfocused|ValidationStates|附加屬性為`true` , 且控制項沒有焦點。 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>|  
  
## <a name="scrollbar-controltemplate-example"></a>捲軸 ControlTemplate 範例  
 下列範例顯示如何定義<xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Primitives.ScrollBar>控制項的。  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
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
