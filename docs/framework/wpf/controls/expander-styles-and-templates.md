---
title: Expander 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
ms.openlocfilehash: 99d11b599d79c9f0d998f49cc0f12fee9c83c39a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551965"
---
# <a name="expander-styles-and-templates"></a>Expander 樣式和範本
本主題描述的樣式和範本<xref:System.Windows.Controls.Expander>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="expander-parts"></a>展開器組件  
 <xref:System.Windows.Controls.Expander>控制項沒有任何具名組件。  
  
## <a name="expander-states"></a>展開器狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Expander>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|已停用|CommonStates|已停用控制項。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|展開的|ExpansionStates|展開此控制項。|  
|Collapsed|ExpansionStates|無法展開此控制項。|  
|ExpandDown|ExpandDirectionStates|控制會向下展開。|  
|ExpandUp|ExpandDirectionStates|控制項將向上擴充。|  
|ExpandLeft|ExpandDirectionStates|控制項會向左展開。|  
|ExpandRight|ExpandDirectionStates|控制項會向右展開。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="expander-controltemplate-example"></a>Expander ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Expander>控制項。  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
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
