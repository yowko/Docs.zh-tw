---
title: TreeView 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 267e870e13d26439e4fbcbba3c5741ff84cabe3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187376"
---
# <a name="treeview-overview"></a>TreeView 概觀
該<xref:System.Windows.Controls.TreeView>控制項提供了一種通過使用可折疊節點在分層結構中顯示資訊的方法。 本主題介紹<xref:System.Windows.Controls.TreeView>和<xref:System.Windows.Controls.TreeViewItem>控制項，並提供其使用的簡單示例。  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>什麼是 TreeView？  
 <xref:System.Windows.Controls.TreeView>是<xref:System.Windows.Controls.ItemsControl>使用<xref:System.Windows.Controls.TreeViewItem>控制項嵌套項的 。 下面的示例創建 一<xref:System.Windows.Controls.TreeView>個 。  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>建立 TreeView  
 該<xref:System.Windows.Controls.TreeView>控制項包含控制項的<xref:System.Windows.Controls.TreeViewItem>層次結構。 控制項<xref:System.Windows.Controls.TreeViewItem>是<xref:System.Windows.Controls.HeaderedItemsControl>具有<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>和 集合的<xref:System.Windows.Controls.ItemsControl.Items%2A>控制項。  
  
 如果使用 來定義<xref:System.Windows.Controls.TreeView>。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> 上圖示範這個方法。  
  
 還可以將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>指定 為數據源，然後指定 和<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A><xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>來定義<xref:System.Windows.Controls.TreeViewItem>內容。  
  
 要定義控制項的佈局，<xref:System.Windows.Controls.TreeViewItem>還可以使用<xref:System.Windows.HierarchicalDataTemplate>物件。 如需詳細資訊和範例，請參閱[使用 SelectedValue、SelectedValuePath 和 SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 如果項不是<xref:System.Windows.Controls.TreeViewItem>控制項，則當<xref:System.Windows.Controls.TreeViewItem><xref:System.Windows.Controls.TreeView>顯示控制項時，控制項會自動將其封閉。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>展開和摺疊 TreeViewItem  
 如果使用者展開 的 ，<xref:System.Windows.Controls.TreeViewItem>屬性<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>設置為`true`。 <xref:System.Windows.Controls.TreeViewItem>還可以通過將<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>屬性設置為`true`（展開）或`false`（折疊）來展開或折疊 ，而無需任何直接的使用者操作。 當此屬性更改時，將<xref:System.Windows.Controls.TreeViewItem.Expanded>發生<xref:System.Windows.Controls.TreeViewItem.Collapsed>或 事件。  
  
 在<xref:System.Windows.FrameworkElement.BringIntoView%2A><xref:System.Windows.Controls.TreeViewItem>控制項上調用方法時， 及其<xref:System.Windows.Controls.TreeViewItem>父<xref:System.Windows.Controls.TreeViewItem>控制項將展開。 如果<xref:System.Windows.Controls.TreeViewItem>不可見或部分可見，則<xref:System.Windows.Controls.TreeView>滾動使其可見。  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem 選取  
 當使用者按一下<xref:System.Windows.Controls.TreeViewItem>控制項以選擇它時，將發生該<xref:System.Windows.Controls.TreeViewItem.Selected>事件，其<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>屬性設置為`true`。 也<xref:System.Windows.Controls.TreeViewItem>將成為控制項<xref:System.Windows.Controls.TreeView.SelectedItem%2A>的<xref:System.Windows.Controls.TreeView>。 相反，當選擇<xref:System.Windows.Controls.TreeViewItem>從控制項更改時，將發生其<xref:System.Windows.Controls.TreeViewItem.Unselected>事件並將其<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>屬性設置為`false`。  
  
 控制項<xref:System.Windows.Controls.TreeView.SelectedItem%2A>上的<xref:System.Windows.Controls.TreeView>屬性是唯讀屬性;因此，您不能顯式設置它。 如果使用者<xref:System.Windows.Controls.TreeView.SelectedItem%2A>按一下<xref:System.Windows.Controls.TreeViewItem>控制項或將<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>該屬性設置為`true`<xref:System.Windows.Controls.TreeViewItem>控制項，則設置該屬性。  
  
 使用<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性指定 的<xref:System.Windows.Controls.TreeView.SelectedValue%2A>。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 如需詳細資訊，請參閱[使用 SelectedValue、SelectedValuePath 和 SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 您可以在<xref:System.Windows.Controls.TreeView.SelectedItemChanged>事件上註冊事件處理常式，以確定所選<xref:System.Windows.Controls.TreeViewItem>更改的次序。 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>提供給事件處理常式的 指定 ，<xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>是 上一個選擇， 和<xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>， 是當前選擇。 如果應用程式或使用者沒有做出先前或目前的選取，則這兩個值都有可能是 `null`。  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>TreeView 樣式  
 控制項的<xref:System.Windows.Controls.TreeView>預設樣式將其置於包含<xref:System.Windows.Controls.StackPanel><xref:System.Windows.Controls.ScrollViewer>控制項的物件中。 設置<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性時<xref:System.Windows.Controls.TreeView>，這些值用於調整 顯示<xref:System.Windows.Controls.StackPanel>的物件<xref:System.Windows.Controls.TreeView>的大小。 如果要顯示的內容大於顯示區域，則會自動顯示，<xref:System.Windows.Controls.ScrollViewer>以便使用者可以滾動流覽<xref:System.Windows.Controls.TreeView>內容。  
  
 要自訂控制項的外觀，<xref:System.Windows.Controls.TreeViewItem>請將<xref:System.Windows.FrameworkElement.Style%2A>屬性設置為自訂<xref:System.Windows.Style>。  
  
 下面的示例演示如何使用<xref:System.Windows.Controls.Control.Foreground%2A>設置<xref:System.Windows.Controls.Control.FontSize%2A><xref:System.Windows.Controls.TreeViewItem>控制項 的 和 屬性值。 <xref:System.Windows.FrameworkElement.Style%2A>  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>將影像和其他內容新增至 TreeView 項目  
 可以在 中包含多個物件<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A><xref:System.Windows.Controls.TreeViewItem>。 要在內容中<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>包含多個物件，請將物件包含在佈局控制項中，如 或<xref:System.Windows.Controls.Panel><xref:System.Windows.Controls.StackPanel>。  
  
 下面的<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>示例演示如何將 和 和<xref:System.Windows.Controls.TreeViewItem><xref:System.Windows.Controls.CheckBox><xref:System.Windows.Controls.TextBlock>的 將 定義為 和，它們都<xref:System.Windows.Controls.DockPanel>包含在控制項中。  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 下面的示例<xref:System.Windows.DataTemplate>演示如何定義 包含<xref:System.Windows.Controls.Image>和 的 控制項中<xref:System.Windows.Controls.TextBlock><xref:System.Windows.Controls.DockPanel>包含 的 。 <xref:System.Windows.DataTemplate>可以使用 設置<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>或<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。 <xref:System.Windows.Controls.TreeViewItem>  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [如何使用主題](treeview-how-to-topics.md)
- [WPF 內容模型](wpf-content-model.md)
