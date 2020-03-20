---
title: GroupBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187483"
---
# <a name="groupbox-styles-and-templates"></a>GroupBox 樣式和範本
<a name="introduction"></a>本主題介紹控制項的<xref:System.Windows.Controls.GroupBox>樣式和範本。 您可以修改預設值<xref:System.Windows.Controls.ControlTemplate>，為控制項提供唯一的外觀。 有關詳細資訊，請參閱為[控制項創建範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a>組盒零件  
 該<xref:System.Windows.Controls.GroupBox>控制項沒有任何命名部件。  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a>組盒狀態  
 下表列出了控制項的<xref:System.Windows.Controls.GroupBox>可視狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|有效|ValidationStates|控制項使用 類<xref:System.Windows.Controls.Validation>，<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性為`false`。|  
|InvalidFocused|ValidationStates|附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性具有`true`控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性是`true`具有控制項沒有焦點。|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a>組盒控制範本示例  
 下面的示例演示如何為<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.GroupBox>控制項定義 。  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 使用<xref:System.Windows.Controls.ControlTemplate>以下一個或多個資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [為控制項創建範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
