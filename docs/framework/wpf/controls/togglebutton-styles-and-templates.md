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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805918"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton 樣式和範本

本主題介紹控件的<xref:System.Windows.Controls.Primitives.ToggleButton>樣式和範本。 您可以修改預設值<xref:System.Windows.Controls.ControlTemplate>,為控制項提供唯一的外觀。 有關詳細資訊,請參閱為[控制項建立樣本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。

## <a name="togglebutton-parts"></a>切換按鈕零件

該<xref:System.Windows.Controls.Primitives.ToggleButton>控件沒有任何命名部件。

## <a name="togglebutton-states"></a>切換按鈕狀態

下表列出了控件的<xref:System.Windows.Controls.Primitives.ToggleButton>可視狀態。

|VisualState 名稱|VisualStateGroup 名稱|描述|
|-|-|-|
|正常|CommonStates|預設狀態。|
|MouseOver|CommonStates|滑鼠指標移到控制項上。|
|按下|CommonStates|已按下控制項。|
|已停用|CommonStates|已停用控制項。|
|已取得焦點|FocusStates|控制項已取得焦點。|
|未取得焦點|FocusStates|控制項未取得焦點。|
|已檢查|檢查狀態|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。|
|未核取|檢查狀態|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。|
|定|檢查狀態|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 為 `true`，而 <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `null`。|
|有效|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>, 附加`false`屬性為 。|
|InvalidFocused|ValidationStates|附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性`true`是 ,控件具有焦點。|
|InvalidUnfocused|ValidationStates|附加<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>屬性`true`為 ,控件沒有焦點。|

> [!NOTE]
> 如果控件範本中不存在不確定的可視狀態,則"未選中的可視狀態"將用作預設可視狀態。

## <a name="togglebutton-controltemplate-example"></a>切換按鈕控制樣本範例

下面的範例展示如何為<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.Primitives.ToggleButton>控制項定義 。

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

上述範例使用下列一或多項資源。

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [為控制項建立樣本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
