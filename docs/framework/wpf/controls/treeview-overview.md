---
title: TreeView 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: f8c49013bc34671ec590f0bd9f84a0f2cf3f9aaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="treeview-overview"></a>TreeView 概觀
<xref:System.Windows.Controls.TreeView>控制項可用來顯示階層式結構的資訊，使用可摺疊的節點。 本主題將介紹<xref:System.Windows.Controls.TreeView>和<xref:System.Windows.Controls.TreeViewItem>控制項，並提供其用法的簡單範例。  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>什麼是 TreeView？  
 <xref:System.Windows.Controls.TreeView> 是<xref:System.Windows.Controls.ItemsControl>，形成使用巢狀項目<xref:System.Windows.Controls.TreeViewItem>控制項。 下列範例會建立<xref:System.Windows.Controls.TreeView>。  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>建立 TreeView  
 <xref:System.Windows.Controls.TreeView>控制項中包含的階層<xref:System.Windows.Controls.TreeViewItem>控制項。 A<xref:System.Windows.Controls.TreeViewItem>控制項是<xref:System.Windows.Controls.HeaderedItemsControl>具有<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>和<xref:System.Windows.Controls.ItemsControl.Items%2A>集合。  
  
 如果您要定義<xref:System.Windows.Controls.TreeView>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您可以明確定義<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>內容的<xref:System.Windows.Controls.TreeViewItem>控制項和組成其集合的項目。 上圖示範這個方法。  
  
 您也可以指定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>做為資料來源，然後指定<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>和<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>定義<xref:System.Windows.Controls.TreeViewItem>內容。  
  
 若要定義的配置<xref:System.Windows.Controls.TreeViewItem>控制項，您也可以使用<xref:System.Windows.HierarchicalDataTemplate>物件。 如需詳細資訊和範例，請參閱[使用 SelectedValue、SelectedValuePath 和 SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 如果項目不是<xref:System.Windows.Controls.TreeViewItem>控制項，它會自動加上<xref:System.Windows.Controls.TreeViewItem>負責控制何時<xref:System.Windows.Controls.TreeView>顯示控制項。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>展開和摺疊 TreeViewItem  
 如果使用者展開<xref:System.Windows.Controls.TreeViewItem>、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>屬性設定為`true`。 您也可以展開或摺疊<xref:System.Windows.Controls.TreeViewItem>使用者並無任何直接動作藉由設定<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>屬性`true`(expand) 或`false`（摺疊）。 當這個屬性變更時，<xref:System.Windows.Controls.TreeViewItem.Expanded>或<xref:System.Windows.Controls.TreeViewItem.Collapsed>就會發生事件。  
  
 當<xref:System.Windows.FrameworkElement.BringIntoView%2A>上呼叫方法<xref:System.Windows.Controls.TreeViewItem>控制項，<xref:System.Windows.Controls.TreeViewItem>與其父系<xref:System.Windows.Controls.TreeViewItem>展開控制項。 如果<xref:System.Windows.Controls.TreeViewItem>不可見或部分可見的<xref:System.Windows.Controls.TreeView>捲動到設為可見。  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>TreeViewItem 選取  
 當使用者按一下<xref:System.Windows.Controls.TreeViewItem>控制項以選取它，<xref:System.Windows.Controls.TreeViewItem.Selected>事件發生時，並將其<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>屬性設定為`true`。 <xref:System.Windows.Controls.TreeViewItem>也會成為<xref:System.Windows.Controls.TreeView.SelectedItem%2A>的<xref:System.Windows.Controls.TreeView>控制項。 相反地，當選取範圍變更從<xref:System.Windows.Controls.TreeViewItem>控制項，其<xref:System.Windows.Controls.TreeViewItem.Unselected>就會發生事件及其<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>屬性設定為`false`。  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性<xref:System.Windows.Controls.TreeView>控制項是唯讀的屬性; 因此，您無法明確地設定它。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性設定，如果使用者在<xref:System.Windows.Controls.TreeViewItem>控制項或當<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>屬性設定為`true`上<xref:System.Windows.Controls.TreeViewItem>控制項。  
  
 使用<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>屬性來指定<xref:System.Windows.Controls.TreeView.SelectedValue%2A>的<xref:System.Windows.Controls.TreeView.SelectedItem%2A>。 如需詳細資訊，請參閱[使用 SelectedValue、SelectedValuePath 和 SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 您可以在註冊事件處理常式<xref:System.Windows.Controls.TreeView.SelectedItemChanged>事件以判斷當選取<xref:System.Windows.Controls.TreeViewItem>變更。 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>提供事件處理常式會指定會<xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>，這是上一個選取項目，而<xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>，這是目前的選取範圍。 如果應用程式或使用者沒有做出先前或目前的選取，則這兩個值都有可能是 `null`。  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView 樣式  
 預設樣式<xref:System.Windows.Controls.TreeView>控制項放在<xref:System.Windows.Controls.StackPanel>物件，其中包含<xref:System.Windows.Controls.ScrollViewer>控制項。 當您將<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性<xref:System.Windows.Controls.TreeView>，這些值可用來大小<xref:System.Windows.Controls.StackPanel>顯示物件<xref:System.Windows.Controls.TreeView>。 如果超過顯示 區域中，內容顯示<xref:System.Windows.Controls.ScrollViewer>會自動顯示，讓使用者可以捲動<xref:System.Windows.Controls.TreeView>內容。  
  
 若要自訂的外觀<xref:System.Windows.Controls.TreeViewItem>控制，請設定<xref:System.Windows.FrameworkElement.Style%2A>屬性設為 custom <xref:System.Windows.Style>。  
  
 下列範例示範如何設定<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.FontSize%2A>屬性值<xref:System.Windows.Controls.TreeViewItem>控制項使用<xref:System.Windows.FrameworkElement.Style%2A>。  
  
 [!code-xaml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>將影像和其他內容新增至 TreeView 項目  
 您可以包含多個物件中的<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>內容的<xref:System.Windows.Controls.TreeViewItem>。 若要包含在多個物件<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>內容，例如括住的版面配置控制項，其中的物件<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.StackPanel>。  
  
 下列範例示範如何定義<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>的<xref:System.Windows.Controls.TreeViewItem>為<xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.TextBlock>，同時加上<xref:System.Windows.Controls.DockPanel>控制項。  
  
 [!code-xaml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 下列範例示範如何定義<xref:System.Windows.DataTemplate>包含<xref:System.Windows.Controls.Image>和<xref:System.Windows.Controls.TextBlock>，括住<xref:System.Windows.Controls.DockPanel>控制項。 您可以使用<xref:System.Windows.DataTemplate>設定<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>或<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>如<xref:System.Windows.Controls.TreeViewItem>。  
  
 [!code-xaml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)  
 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)
