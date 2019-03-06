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
ms.openlocfilehash: 300fd8d6c6bc8a73257d71280bbb0b5565c275ec
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375554"
---
# <a name="treeview-styles-and-templates"></a>TreeView 樣式和範本
本主題描述的樣式和範本<xref:System.Windows.Controls.TreeView>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="treeview-parts"></a>樹狀檢視組件  
 <xref:System.Windows.Controls.TreeView>控制項沒有任何具名組件。  
  
 當您建立<xref:System.Windows.Controls.ControlTemplate>for <xref:System.Windows.Controls.TreeView>，您的範本可能會包含<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>會顯示在每個項目<xref:System.Windows.Controls.TreeView>;<xref:System.Windows.Controls.ScrollViewer>可在控制項內捲動)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須給予<xref:System.Windows.Controls.ItemsPresenter>名稱， `ItemsPresenter`。  
  
## <a name="treeview-states"></a>樹狀檢視狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.TreeView>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem 的組件  
 下表列出的具名組件<xref:System.Windows.Controls.TreeViewItem>控制項。  
  
|組件|類型|描述|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|包含該內容的標頭的視覺元素<xref:System.Windows.Controls.TreeView>控制項。|  
  
## <a name="treeviewitem-states"></a>TreeViewItem 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.TreeViewItem>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.TreeViewItem>。|  
|已停用|CommonStates|<xref:System.Windows.Controls.TreeViewItem>已停用。|  
|已取得焦點|FocusStates|<xref:System.Windows.Controls.TreeViewItem>具有焦點。|  
|未取得焦點|FocusStates|<xref:System.Windows.Controls.TreeViewItem>未取得焦點。|  
|展開|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>展開控制項。|  
|Collapsed|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>摺疊控制項。|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>有項目。|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>沒有任何項目。|  
|已選取|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>已選取。|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>選取但非作用中。|  
|未選取|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>未選取。|  
|驗證|ValidationStates|控制項使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`已在控制項具有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的屬性是`true`有控制項沒有焦點。|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.TreeView>控制項和其相關聯的類型。  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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
