---
title: PasswordBox 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 227ccbda8d570868258508935a5d95f0f40663ab
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458834"
---
# <a name="passwordbox-styles-and-templates"></a>PasswordBox 樣式和範本

本主題描述 <xref:System.Windows.Controls.PasswordBox> 控制項的樣式和範本。 您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。

## <a name="passwordbox-parts"></a>PasswordBox 元件

下表列出 <xref:System.Windows.Controls.PasswordBox> 控制項的已命名元件。

|組件|輸入|描述|
|-|-|-|
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|可以包含 <xref:System.Windows.FrameworkElement>的視覺元素。 <xref:System.Windows.Controls.PasswordBox> 的文字會顯示在此元素中。|

## <a name="passwordbox-states"></a>PasswordBox 狀態

下表列出 <xref:System.Windows.Controls.PasswordBox> 控制項的視覺狀態。

|VisualState 名稱|VisualStateGroup 名稱|描述|
|-|-|-|
|一般|CommonStates|預設狀態。|
|MouseOver|CommonStates|滑鼠指標移到控制項上。|
|Disabled|CommonStates|已停用控制項。|
|已取得焦點|FocusStates|控制項已取得焦點。|
|未取得焦點|FocusStates|控制項未取得焦點。|
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|

## <a name="passwordbox-controltemplate-example"></a>PasswordBox ControlTemplate 範例

下列範例顯示如何定義 <xref:System.Windows.Controls.PasswordBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

上述範例使用下列一或多項資源。

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)
