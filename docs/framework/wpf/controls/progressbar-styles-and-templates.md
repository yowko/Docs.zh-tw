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
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283445"
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar 樣式和範本
本主題描述 <xref:System.Windows.Controls.ProgressBar> 控制項的樣式和範本。 您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="progressbar-parts"></a>ProgressBar 元件  
 下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的已命名元件。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|表示進度的物件。|  
|PART_Track|<xref:System.Windows.FrameworkElement>|定義進度指標路徑的物件。|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|Embellishes 進度列的物件。|  
  
## <a name="progressbar-states"></a>ProgressBar 狀態  
 下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|確定|CommonStates|<xref:System.Windows.Controls.ProgressBar> 會根據 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性來報告進度。|  
|處於|CommonStates|<xref:System.Windows.Controls.ProgressBar> 會以重複模式來報告一般進度。|  
|有效|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="progressbar-controltemplate-example"></a>ProgressBar ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ProgressBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
