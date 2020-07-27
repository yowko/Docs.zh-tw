---
title: TreeView 概觀
description: 瞭解 Windows Presentation Foundation TreeView 控制項如何使用節點來顯示階層式結構中的資訊，包括簡單的範例。
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 6ef77febdd3facb7c7e1af566841c2a1aeaff810
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164536"
---
# <a name="treeview-overview"></a>TreeView 概觀
<xref:System.Windows.Controls.TreeView>控制項提供使用可折迭節點，在階層式結構中顯示資訊的方式。 本主題介紹 <xref:System.Windows.Controls.TreeView> 和 <xref:System.Windows.Controls.TreeViewItem> 控制項，並提供其用法的簡單範例。  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>什麼是 TreeView？  
 <xref:System.Windows.Controls.TreeView>是 <xref:System.Windows.Controls.ItemsControl> ，它會使用控制項來嵌套專案 <xref:System.Windows.Controls.TreeViewItem> 。 下列範例會建立 <xref:System.Windows.Controls.TreeView> 。  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>建立 TreeView  
 <xref:System.Windows.Controls.TreeView>控制項包含控制項的階層 <xref:System.Windows.Controls.TreeViewItem> 。 <xref:System.Windows.Controls.TreeViewItem>控制項是 <xref:System.Windows.Controls.HeaderedItemsControl> 具有 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 和 <xref:System.Windows.Controls.ItemsControl.Items%2A> 集合的。  
  
 如果您要使用定義 <xref:System.Windows.Controls.TreeView> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，可以明確定義 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 控制項的內容 <xref:System.Windows.Controls.TreeViewItem> 和組成其集合的專案。 上圖示範這個方法。  
  
 您也可以將指定 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 為數據源，然後指定 <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 以定義 <xref:System.Windows.Controls.TreeViewItem> 內容。  
  
 若要定義控制項的版面配置 <xref:System.Windows.Controls.TreeViewItem> ，您也可以使用 <xref:System.Windows.HierarchicalDataTemplate> 物件。 如需詳細資訊和範例，請參閱[使用 SelectedValue、SelectedValuePath 和 SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 如果專案不是控制項，則會在控制項 <xref:System.Windows.Controls.TreeViewItem> 顯示時，自動將其括住 <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView> 。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>展開和摺疊 TreeViewItem  
 如果使用者展開 <xref:System.Windows.Controls.TreeViewItem> ， <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> 屬性會設定為 `true` 。 您也可以 <xref:System.Windows.Controls.TreeViewItem> 將 <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> 屬性設定為 `true` （expand）或（折迭），而不使用任何直接使用者動作來展開或折迭 `false` 。 當這個屬性變更時， <xref:System.Windows.Controls.TreeViewItem.Expanded> <xref:System.Windows.Controls.TreeViewItem.Collapsed> 就會發生或事件。  
  
 在 <xref:System.Windows.FrameworkElement.BringIntoView%2A> 控制項上呼叫方法時 <xref:System.Windows.Controls.TreeViewItem> ， <xref:System.Windows.Controls.TreeViewItem> 和其父 <xref:System.Windows.Controls.TreeViewItem> 控制項會展開。 如果 <xref:System.Windows.Controls.TreeViewItem> 看不到或部分可見，則會 <xref:System.Windows.Controls.TreeView> 滾動以使其可見。  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem 選取  
 當使用者按一下 <xref:System.Windows.Controls.TreeViewItem> 控制項來選取它時， <xref:System.Windows.Controls.TreeViewItem.Selected> 就會發生事件，而且其 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 屬性會設定為 `true` 。 <xref:System.Windows.Controls.TreeViewItem>也會成為 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 控制項的 <xref:System.Windows.Controls.TreeView> 。 相反地，當選取範圍從控制項變更時 <xref:System.Windows.Controls.TreeViewItem> ， <xref:System.Windows.Controls.TreeViewItem.Unselected> 就會發生事件，而且其 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 屬性會設定為 `false` 。  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>控制項上的屬性 <xref:System.Windows.Controls.TreeView> 是唯讀屬性，因此，您無法明確地設定它。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>如果使用者按一下 <xref:System.Windows.Controls.TreeViewItem> 控制項，或 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 控制項上的屬性設定為，則會設定屬性 `true` <xref:System.Windows.Controls.TreeViewItem> 。  
  
 使用 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 屬性來指定 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 的 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 。 如需詳細資訊，請參閱[使用 SelectedValue、SelectedValuePath 和 SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 您可以在事件上註冊事件處理常式 <xref:System.Windows.Controls.TreeView.SelectedItemChanged> ，以便判斷選取的變更時間 <xref:System.Windows.Controls.TreeViewItem> 。 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>提供給事件處理常式的會指定 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> ，這是先前的選取專案，而則 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> 是目前的選取專案。 如果應用程式或使用者沒有做出先前或目前的選取，則這兩個值都有可能是 `null`。  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>TreeView 樣式  
 控制項的預設樣式 <xref:System.Windows.Controls.TreeView> 會將它放在 <xref:System.Windows.Controls.StackPanel> 包含控制項的物件內 <xref:System.Windows.Controls.ScrollViewer> 。 當您設定的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性時 <xref:System.Windows.Controls.TreeView> ，會使用這些值來調整顯示的 <xref:System.Windows.Controls.StackPanel> 物件大小 <xref:System.Windows.Controls.TreeView> 。 如果要顯示的內容大於顯示區域， <xref:System.Windows.Controls.ScrollViewer> 會自動顯示，讓使用者可以流覽 <xref:System.Windows.Controls.TreeView> 內容。  
  
 若要自訂控制項的外觀 <xref:System.Windows.Controls.TreeViewItem> ，請將 <xref:System.Windows.FrameworkElement.Style%2A> 屬性設定為自訂 <xref:System.Windows.Style> 。  
  
 下列範例顯示如何使用來設定 <xref:System.Windows.Controls.Control.Foreground%2A> 控制項的和 <xref:System.Windows.Controls.Control.FontSize%2A> 屬性值 <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.FrameworkElement.Style%2A> 。  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>將影像和其他內容新增至 TreeView 項目  
 您可以在的內容中包含一個以上的物件 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> 。 若要在內容中包含多個物件 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> ，請將物件括在版面配置控制項中，例如 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.StackPanel> 。  
  
 下列範例顯示如何將 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 的定義 <xref:System.Windows.Controls.TreeViewItem> 為 <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.TextBlock> 同時包含在控制項中的和 <xref:System.Windows.Controls.DockPanel> 。  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 下列範例示範如何定義 <xref:System.Windows.DataTemplate> ，其中包含 <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.TextBlock> 控制項中所括住的和 <xref:System.Windows.Controls.DockPanel> 。 您可以使用 <xref:System.Windows.DataTemplate> 來設定的 <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> 或 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.TreeViewItem> 。  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [操作說明主題](treeview-how-to-topics.md)
- [WPF 內容模型](wpf-content-model.md)
