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
ms.openlocfilehash: d38173cad01e0f2d17cd53be102e0b8afd75d608
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642970"
---
# <a name="scrollbar-styles-and-templates"></a>ScrollBar 樣式和範本
本主題描述的樣式和範本<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="scrollbar-parts"></a>捲軸的組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|指出的位置之項目的容器<xref:System.Windows.Controls.Primitives.ScrollBar>。|  
  
## <a name="scrollbar-states"></a>捲軸狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|已停用|CommonStates|已停用控制項。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="scrollbar-controltemplate-example"></a>ScrollBar 的 ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Primitives.ScrollBar>控制項。  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)
- [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
