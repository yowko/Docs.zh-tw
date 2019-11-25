---
title: Thumb 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: 0d0d88e3b527beacfa5f879027e696aa75b18147
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283686"
---
# <a name="thumb-styles-and-templates"></a>Thumb 樣式和範本

本主題描述 <xref:System.Windows.Controls.Primitives.Thumb> 控制項的樣式和範本。 您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。

## <a name="thumb-parts"></a>Thumb 部分

<xref:System.Windows.Controls.Primitives.Thumb> 控制項沒有任何已命名的元件。

## <a name="thumb-states"></a>Thumb 狀態

下表列出 <xref:System.Windows.Controls.Primitives.Thumb> 控制項的視覺狀態。

|VisualState 名稱|VisualStateGroup 名稱|描述|
|-|-|-|
|一般|CommonStates|預設狀態。|
|MouseOver|CommonStates|滑鼠指標移到控制項上。|
|按下|CommonStates|已按下控制項。|
|已停用|CommonStates|已停用控制項。|
|已取得焦點|FocusStates|控制項已取得焦點。|
|未取得焦點|FocusStates|控制項未取得焦點。|
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|

## <a name="thumb-controltemplate-example"></a>Thumb ControlTemplate 範例

下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.Thumb> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

上述範例使用下列一或多項資源。

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
