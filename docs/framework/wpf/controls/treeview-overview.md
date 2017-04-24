---
title: "TreeView 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Control 類別, TreeView"
  - "展開節點"
  - "TreeView 控制項, 關於 TreeView 控制項"
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# TreeView 概觀
<xref:System.Windows.Controls.TreeView> 控制項使用可摺疊節點，提供在階層式結構中顯示資訊的方式。  本主題將介紹 <xref:System.Windows.Controls.TreeView> 和 <xref:System.Windows.Controls.TreeViewItem> 控制項，並提供控制項用途的簡單範例。  
  
   
  
<a name="Simple_TreeView_Control"></a>   
## 什麼是 TreeView  
 <xref:System.Windows.Controls.TreeView> 是一種 <xref:System.Windows.Controls.ItemsControl>，會使用 <xref:System.Windows.Controls.TreeViewItem> 控制項對項目進行巢狀化處理。  下列範例將建立 <xref:System.Windows.Controls.TreeView>。  
  
 [!code-xml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## 建立 TreeView  
 <xref:System.Windows.Controls.TreeView> 控制項包含 <xref:System.Windows.Controls.TreeViewItem> 控制項的階層。  <xref:System.Windows.Controls.TreeViewItem> 控制項是 <xref:System.Windows.Controls.HeaderedItemsControl>，具有 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 和 <xref:System.Windows.Controls.ItemsControl.Items%2A> 集合。  
  
 如果您使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義 <xref:System.Windows.Controls.TreeView>，則可以明確定義 <xref:System.Windows.Controls.TreeViewItem> 控制項的 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 內容以及組成其集合的項目。  前一個範例會示範這個方法。  
  
 您也可以將 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 指定為資料來源，然後再指定 <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 以定義 <xref:System.Windows.Controls.TreeViewItem> 內容。  
  
 您也可以使用 <xref:System.Windows.HierarchicalDataTemplate> 物件，來定義 <xref:System.Windows.Controls.TreeViewItem> 控制項的版面配置。  如需詳細資訊和其他範例，請參閱 [使用 SelectedValue、SelectedValuePath 和 SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 如果項目不是 <xref:System.Windows.Controls.TreeViewItem> 控制項，則在顯示 <xref:System.Windows.Controls.TreeView> 控制項時，會自動由 <xref:System.Windows.Controls.TreeViewItem> 控制項包含。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## 展開和摺疊 TreeViewItem  
 如果使用者展開 <xref:System.Windows.Controls.TreeViewItem>，<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> 屬性便會設定為 `true`。  透過將 <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> 屬性設定為 `true` \(展開\) 或 `false` \(摺疊\)，您也可以在沒有任何直接使用者動作的情況下，展開或折疊 <xref:System.Windows.Controls.TreeViewItem>。  當這個屬性值變更時，會引發 <xref:System.Windows.Controls.TreeViewItem.Expanded> 或 <xref:System.Windows.Controls.TreeViewItem.Collapsed> 事件。  
  
 在 <xref:System.Windows.Controls.TreeViewItem> 控制項上呼叫 <xref:System.Windows.FrameworkElement.BringIntoView%2A> 方法時，便會展開 <xref:System.Windows.Controls.TreeViewItem> 及其父 <xref:System.Windows.Controls.TreeViewItem> 控制項。  如果 <xref:System.Windows.Controls.TreeViewItem> 不可見或只有部分可見，<xref:System.Windows.Controls.TreeView> 便會捲動以顯示其內容。  
  
<a name="TreeViewItem_Selection"></a>   
## TreeViewItem 選取範圍  
 當使用者按一下 <xref:System.Windows.Controls.TreeViewItem> 控制項進行選取時，會引發 <xref:System.Windows.Controls.TreeViewItem.Selected> 事件，且其 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 屬性會設定為 `true`。  <xref:System.Windows.Controls.TreeViewItem> 也會成為 <xref:System.Windows.Controls.TreeView> 控制項的 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>。  相反地，如果從 <xref:System.Windows.Controls.TreeViewItem> 控制項變更選取範圍，便會引發 <xref:System.Windows.Controls.TreeViewItem.Unselected> 事件，且其 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 屬性會設定為 `false`。  
  
 <xref:System.Windows.Controls.TreeView> 控制項上的 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 屬性是唯讀屬性，因此，您無法明確地進行設定。  如果使用者按一下 <xref:System.Windows.Controls.TreeViewItem> 控制項或是將 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 設定為 <xref:System.Windows.Controls.TreeViewItem> 控制項上的 `true` 時，便會設定 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 屬性。  
  
 使用 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 屬性指定 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 的 <xref:System.Windows.Controls.TreeView.SelectedValue%2A>。  如需詳細資訊，請參閱 [使用 SelectedValue、SelectedValuePath 和 SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 您可以在 <xref:System.Windows.Controls.TreeView.SelectedItemChanged> 事件上註冊事件處理常式，才能判斷所選<xref:System.Windows.Controls.TreeViewItem> 改變的時間。  提供給事件處理常式的 <xref:System.Windows.RoutedPropertyChangedEventArgs%601> 會指定 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> \(亦即上一個選取範圍\) 和 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> \(目前的選取範圍\)。  如果應用程式或使用者沒有指定上一個或目前的選取範圍，則任一個值都可以是 `null`。  
  
<a name="TreeView_Style"></a>   
## TreeView 樣式  
 <xref:System.Windows.Controls.TreeView> 控制項的預設樣式會將之置放在 <xref:System.Windows.Controls.StackPanel> 物件內部，此物件包含 <xref:System.Windows.Controls.ScrollViewer> 控制項。  當您設定 <xref:System.Windows.Controls.TreeView> 的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性時，這些值可用來調整顯示 <xref:System.Windows.Controls.TreeView> 之 <xref:System.Windows.Controls.StackPanel> 物件的大小。  如果要顯示的內容大於顯示區域，<xref:System.Windows.Controls.ScrollViewer> 便會自動顯示，如此，使用者就可以捲動 <xref:System.Windows.Controls.TreeView> 內容。  
  
 若要自訂 <xref:System.Windows.Controls.TreeViewItem> 控制項的外觀，請將 <xref:System.Windows.FrameworkElement.Style%2A> 屬性設定為自訂 <xref:System.Windows.Style>。  
  
 下列範例將示範如何使用 <xref:System.Windows.FrameworkElement.Style%2A>，設定 <xref:System.Windows.Controls.TreeViewItem> 的 <xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontSize%2A> 屬性。  
  
 [!code-xml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## 將影像和其他內容加入至 TreeView 項目  
 您可以在 <xref:System.Windows.Controls.TreeViewItem> 的 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 內容中加入一個以上的物件。  若要在 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 加入多個物件，請將物件置於版面配置控制項內部，例如 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.StackPanel>。  
  
 下列範例將示範如何將 <xref:System.Windows.Controls.TreeViewItem> 的 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 定義為 <xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.TextBlock>，這兩個項目同時置於 <xref:System.Windows.Controls.DockPanel> 控制項中。  
  
 [!code-xml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 下列範例將示範如何定義包含 <xref:System.Windows.Controls.Image> 和 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.DataTemplate>，這兩個項目同時置於 <xref:System.Windows.Controls.DockPanel> 控制項中。  您可以使用 <xref:System.Windows.DataTemplate>，為 <xref:System.Windows.Controls.TreeViewItem> 設定 <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> 或 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。  
  
 [!code-xml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## 請參閱  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)   
 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)