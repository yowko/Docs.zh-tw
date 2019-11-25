---
title: TreeView 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: 45276d23380fe956fc3d59b90d5baae23ee8a7e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283639"
---
# <a name="treeview-styles-and-templates"></a>TreeView 樣式和範本
本主題描述 <xref:System.Windows.Controls.TreeView> 控制項的樣式和範本。 您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[建立控制項的範本](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="treeview-parts"></a>TreeView 元件  
 <xref:System.Windows.Controls.TreeView> 控制項沒有任何已命名的元件。  
  
 當您建立 <xref:System.Windows.Controls.TreeView>的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能會在 <xref:System.Windows.Controls.ScrollViewer>中包含 <xref:System.Windows.Controls.ItemsPresenter>。 （<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.TreeView>中的每個專案，<xref:System.Windows.Controls.ScrollViewer> 可在控制項內進行滾動）。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer>的直接子系，您必須為 <xref:System.Windows.Controls.ItemsPresenter> 指定名稱，`ItemsPresenter`。  
  
## <a name="treeview-states"></a>TreeView 狀態  
 下表列出 <xref:System.Windows.Controls.TreeView> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem 元件  
 下表列出 <xref:System.Windows.Controls.TreeViewItem> 控制項的已命名元件。  
  
|組件|輸入|描述|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|包含 <xref:System.Windows.Controls.TreeView> 控制項之標頭內容的視覺元素。|  
  
## <a name="treeviewitem-states"></a>TreeViewItem 狀態  
 下表列出 <xref:System.Windows.Controls.TreeViewItem> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.TreeViewItem>上。|  
|已停用|CommonStates|<xref:System.Windows.Controls.TreeViewItem> 已停用。|  
|已取得焦點|FocusStates|<xref:System.Windows.Controls.TreeViewItem> 具有焦點。|  
|未取得焦點|FocusStates|<xref:System.Windows.Controls.TreeViewItem> 沒有焦點。|  
|展開|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> 控制項已展開。|  
|Collapsed|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> 控制項已折迭。|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> 有個專案。|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> 沒有專案。|  
|已選取|SelectionStates|已選取 [<xref:System.Windows.Controls.TreeViewItem>]。|  
|SelectedInactive|SelectionStates|已選取 <xref:System.Windows.Controls.TreeViewItem>，但未使用。|  
|未選取|SelectionStates|未選取 <xref:System.Windows.Controls.TreeViewItem>。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate 範例  
 下列範例示範如何定義 <xref:System.Windows.Controls.TreeView> 控制項及其關聯類型的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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
