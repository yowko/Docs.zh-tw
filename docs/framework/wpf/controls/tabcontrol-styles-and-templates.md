---
title: TabControl 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TabControl
- TabControl [WPF], styles and templates [WPF]
- parts [WPF], TabControl
- styles [WPF], TabControl
- states [WPF], TabControl
- templates [WPF], TabControl
ms.assetid: f6b19a30-f10e-4fa1-96ce-f17a54092ab6
ms.openlocfilehash: ac8349453eaef2167746de639a7e2c111a019b86
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356308"
---
# <a name="tabcontrol-styles-and-templates"></a>TabControl 樣式和範本
本主題描述的樣式和範本<xref:System.Windows.Controls.TabControl>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="tabcontrol-parts"></a>TabControl 組件  
 下表列出的具名組件<xref:System.Windows.Controls.TabControl>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_SelectedContentHost|<xref:System.Windows.Controls.ContentPresenter>|顯示目前選取的內容物件<xref:System.Windows.Controls.TabItem>。|  
  
 當您建立<xref:System.Windows.Controls.ControlTemplate>for <xref:System.Windows.Controls.TabControl>，您的範本可能會包含<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>會顯示在每個項目<xref:System.Windows.Controls.TabControl>;<xref:System.Windows.Controls.ScrollViewer>可在控制項內捲動)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須給予<xref:System.Windows.Controls.ItemsPresenter>名稱， `ItemsPresenter`。  
  
## <a name="tabcontrol-states"></a>TabControl 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.TabControl>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|已停用控制項。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="tabitem-parts"></a>TabItem 組件  
 <xref:System.Windows.Controls.TabItem>控制項沒有任何具名組件。  
  
## <a name="tabitem-states"></a>TabItem 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.TabItem>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|已停用|CommonStates|已停用控制項。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|已選取|SelectionStates|選取控制項。|  
|未選取|SelectionStates|未選取控制項。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="tabcontrol-controltemplate-example"></a>TabControl ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>for<xref:System.Windows.Controls.TabControl>和<xref:System.Windows.Controls.TabItem>控制項。  
  
 [!code-xaml[ControlTemplateExamples#TabControl](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tabcontrol.xaml#tabcontrol)]  
  
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
