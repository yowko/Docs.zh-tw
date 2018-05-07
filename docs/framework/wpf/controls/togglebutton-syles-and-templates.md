---
title: ToggleButton 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: 4e6d5b1cc8e19e0ebc2750baa403cb4e64f773d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="togglebutton-syles-and-templates"></a>ToggleButton 樣式和範本
本主題描述樣式和範本<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="togglebutton-parts"></a>ToggleButton 組件  
 <xref:System.Windows.Controls.Primitives.ToggleButton>控制項沒有任何已命名的組件。  
  
## <a name="togglebutton-states"></a>切換狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|按下|CommonStates|已按下控制項。|  
|已停用|CommonStates|已停用控制項。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|已核取|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。|  
|若未選取|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。|  
|不定|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 是`true`，和<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>是`null`。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
> [!NOTE]
>  如果不確定的視覺狀態不存在於控制項範本，然後取消核取的視覺狀態會用作預設視覺狀態。  
  
## <a name="togglebutton-controltemplate-example"></a>ToggleButton ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
