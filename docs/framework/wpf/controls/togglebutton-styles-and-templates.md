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
ms.openlocfilehash: 46fd7d07c3904ee752ae3f467f65af4b0c031c84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790750"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton 樣式和範本

本主題描述的樣式和範本<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。

## <a name="togglebutton-parts"></a>ToggleButton 組件

<xref:System.Windows.Controls.Primitives.ToggleButton>控制項沒有任何具名組件。

## <a name="togglebutton-states"></a>ToggleButton 狀態

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
|未選取|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。|
|不定|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 已`true`，並<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>是`null`。|
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|

> [!NOTE]
> 不定的視覺狀態不存在於您的控制項範本中，如果未選取的視覺狀態將會用為預設的可見狀態。

## <a name="togglebutton-controltemplate-example"></a>ToggleButton ControlTemplate 範例

下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Primitives.ToggleButton>控制項。

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

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
