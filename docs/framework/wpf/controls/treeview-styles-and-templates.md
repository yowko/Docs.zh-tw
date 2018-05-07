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
ms.openlocfilehash: 3a73127e409a96d5282272bd7a0e55a13a83a849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="treeview-styles-and-templates"></a>TreeView 樣式和範本
本主題描述樣式和範本<xref:System.Windows.Controls.TreeView>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="treeview-parts"></a>樹狀檢視組件  
 <xref:System.Windows.Controls.TreeView>控制項沒有任何已命名的組件。  
  
 當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.TreeView>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.TreeView>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。  
  
## <a name="treeview-states"></a>樹狀檢視狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.TreeView>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem 的組件  
 下表列出的具名組件<xref:System.Windows.Controls.TreeViewItem>控制項。  
  
|組件|類型|描述|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|包含該標頭內容的視覺項目<xref:System.Windows.Controls.TreeView>控制項。|  
  
## <a name="treeviewitem-states"></a>TreeViewItem 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.TreeViewItem>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.TreeViewItem>。|  
|已停用|CommonStates|<xref:System.Windows.Controls.TreeViewItem>已停用。|  
|已取得焦點|FocusStates|<xref:System.Windows.Controls.TreeViewItem>具有焦點。|  
|未取得焦點|FocusStates|<xref:System.Windows.Controls.TreeViewItem>沒有焦點。|  
|展開的|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>展開控制項。|  
|Collapsed|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>控制項摺疊。|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>有項目。|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>沒有任何項目。|  
|已選取|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>已選取。|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>選取但不在使用中。|  
|未選取|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>未選取。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.TreeView>控制項和其相關聯的類型。  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
