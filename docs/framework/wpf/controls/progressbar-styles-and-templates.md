---
title: ProgressBar 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 89aea3e80fe17ece8a17f62f62290d34ddd55c60
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar 樣式和範本
本主題描述樣式和範本<xref:System.Windows.Controls.ProgressBar>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="progressbar-parts"></a>ProgressBar 組件  
 下表列出的具名組件<xref:System.Windows.Controls.ProgressBar>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|物件，表示進度。|  
|PART_Track|<xref:System.Windows.FrameworkElement>|定義進度列指示器的路徑物件。|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|物件，embellishes 進度列。|  
  
## <a name="progressbar-states"></a>進度列狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.ProgressBar>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|確定|CommonStates|<xref:System.Windows.Controls.ProgressBar> 報告進度根據<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>屬性。|  
|不定|CommonStates|<xref:System.Windows.Controls.ProgressBar> 報告泛型的進度，以重複模式。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="progressbar-controltemplate-example"></a>ProgressBar ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ProgressBar>控制項。  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
