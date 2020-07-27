---
title: Menu 樣式和範本
description: 瞭解功能表控制項 Windows Presentation Foundation 的樣式和範本。 修改 ControlTemplate，讓控制項具有獨特的外觀。
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164549"
---
# <a name="menu-styles-and-templates"></a>Menu 樣式和範本
本主題描述控制項的樣式和範本 <xref:System.Windows.Controls.Menu> 。 您可以修改預設值 <xref:System.Windows.Controls.ControlTemplate> ，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="menu-parts"></a>功能表元件  
 <xref:System.Windows.Controls.Menu>控制項沒有任何已命名的元件。  
  
 當您建立的時 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> ，您的範本可能會 <xref:System.Windows.Controls.ItemsPresenter> 在中包含 <xref:System.Windows.Controls.ScrollViewer> 。 （會 <xref:System.Windows.Controls.ItemsPresenter> 顯示中的每個專案 <xref:System.Windows.Controls.Menu> ; 會 <xref:System.Windows.Controls.ScrollViewer> 啟用控制項內的滾動功能）。  如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子系 <xref:System.Windows.Controls.ScrollViewer> ，您就必須指定 <xref:System.Windows.Controls.ItemsPresenter> 名稱 `ItemsPresenter` 。  
  
## <a name="menu-states"></a>功能表狀態  
 下表列出控制項的視覺狀態 <xref:System.Windows.Controls.Menu> 。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|有效|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `false` 。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性的 `true` 焦點是控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="menuitem-parts"></a>MenuItem 部分  
 下表列出控制項的已命名元件 <xref:System.Windows.Controls.Menu> 。  
  
|部分|類型|描述|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|子功能表的區域。|  
  
 當您建立的時 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> ，您的範本可能會 <xref:System.Windows.Controls.ItemsPresenter> 在中包含 <xref:System.Windows.Controls.ScrollViewer> 。 （會 <xref:System.Windows.Controls.ItemsPresenter> 顯示中的每個專案 <xref:System.Windows.Controls.MenuItem> ; 會 <xref:System.Windows.Controls.ScrollViewer> 啟用控制項內的滾動功能）。  如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子系 <xref:System.Windows.Controls.ScrollViewer> ，您就必須指定 <xref:System.Windows.Controls.ItemsPresenter> 名稱 `ItemsPresenter` 。  
  
## <a name="menuitem-states"></a>MenuItem 狀態  
 下表列出控制項的視覺狀態 <xref:System.Windows.Controls.MenuItem> 。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|有效|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `false` 。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性的 `true` 焦點是控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>功能表和 MenuItem ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> 控制項的。  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> 控制項的。  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 下列範例 `MenuScrollViewer` 會定義上一個範例中所使用的。  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 這些 <xref:System.Windows.Controls.ControlTemplate> 範例會使用下列一或多個資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)
