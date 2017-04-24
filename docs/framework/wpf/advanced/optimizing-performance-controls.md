---
title: "最佳化效能：控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "容器回收"
  - "控制項 [WPF], 改善效能"
  - "使用者介面虛擬化"
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 最佳化效能：控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 包含大部分 Windows 應用程式所使用的許多常見使用者介面 \(UI\) 元件。  本主題包含用於改善 UI 效能的技術。  
  
   
  
<a name="Displaying"></a>   
## 顯示大量資料集  
 <xref:System.Windows.Controls.ListView> 和 <xref:System.Windows.Controls.ComboBox> 這類的 WPF 控制項是用於顯示應用程式的項目清單。  如果要顯示的清單很大的話，應用程式的效能可能就會受到影響。  這是因為標準的配置系統會針對與清單控制項相關聯的每個項目建立配置容器，並計算其配置大小和位置。  一般而言，您不需要同時顯示所有的項目，而是改為顯示其子集，並讓使用者捲動清單。  在這種情況下，就比較適合使用 UI「*虛擬化*」\(Virtualization\)，這表示項目容器的產生作業和項目的相關聯配置計算作業，會延後到顯示項目時才進行。  
  
 UI 虛擬化是清單控制項的一個重要層面。  UI 虛擬化不應與資料虛擬化混為一談。  UI 虛擬化只會在記憶體中儲存可見項目，但會針對資料繫結的案例在記憶體中儲存整個資料結構。  相對地，資料虛擬化則只會在記憶體中儲存螢幕上可見的資料項目。  
  
 根據預設，當 <xref:System.Windows.Controls.ListView> 和 <xref:System.Windows.Controls.ListBox> 控制項的清單項目繫結至資料時，就會啟用 UI 虛擬化。  <xref:System.Windows.Controls.TreeView> 虛擬化可以藉由將 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> 附加屬性設為 `true` 的方式加以啟用。  如果要針對衍生自 <xref:System.Windows.Controls.ItemsControl> 的自訂控制項或是使用 <xref:System.Windows.Controls.StackPanel> 類別的現有項目控制項 \(例如 <xref:System.Windows.Controls.ComboBox>\) 啟用 UI 虛擬化，可以將 <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> 設為 <xref:System.Windows.Controls.VirtualizingStackPanel> 並將 <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> 設為 `true`。  可惜的是，您可能會在不了解的情況下停用這些控制項的 UI 虛擬化。  下列清單是會停用 UI 虛擬化的情況。  
  
-   項目容器是直接加入至 <xref:System.Windows.Controls.ItemsControl> 中的。  例如，當應用程式將 <xref:System.Windows.Controls.ListBoxItem> 物件明確加入至 <xref:System.Windows.Controls.ListBox> 時，<xref:System.Windows.Controls.ListBox> 並不會虛擬化 <xref:System.Windows.Controls.ListBoxItem> 物件。  
  
-   <xref:System.Windows.Controls.ItemsControl> 中項目容器的型別不相同。  例如，使用 <xref:System.Windows.Controls.Separator> 物件的 <xref:System.Windows.Controls.Menu> 不能實作項目回收，因為 <xref:System.Windows.Controls.Menu> 所包含物件的型別為 <xref:System.Windows.Controls.Separator> 和 <xref:System.Windows.Controls.MenuItem>。  
  
-   將 <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> 設為 `false`。  
  
-   將 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> 設為 `false`。  
  
 重要的考量，當您將虛擬化項目容器會是您是否有項目容器所屬的項目相關聯的額外狀態資訊。  在這種情況下，您必須儲存額外的狀態。  例如，您的項目可能包含在 <xref:System.Windows.Controls.Expander> 控制項中，而 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 狀態是繫結到項目的容器，而非項目本身。  將容器重複使用於新項目時，會將目前的 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 值用於新項目。  此外，舊項目會遺失正確的 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 值。  
  
 目前沒有 WPF 控制項提供內建的資料虛擬化支援。  
  
<a name="Container"></a>   
## 容器回收  
 在 .NET Framework 3.5 SP1 中，針對繼承自 <xref:System.Windows.Controls.ItemsControl> 的控制項而加入的 UI 虛擬化最佳化是「*容器回收*」\(Container Recycling\)，這個功能也有助於改善捲動效能。  在填入使用 UI 虛擬化的 <xref:System.Windows.Controls.ItemsControl> 時，會針對捲入檢視範圍內的每個項目建立項目容器，並針對捲出檢視範圍外的每個項目終結項目容器。  「*容器回收*」\(Container Recycling\) 可以讓控制項將現有項目容器重複使用於不同的資料項目，這樣就不會在使用者捲動 <xref:System.Windows.Controls.ItemsControl> 時不斷建立和終結項目容器。  您可以選擇啟用回收設定的項目<xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A>附加屬性，以<xref:System.Windows.Controls.VirtualizationMode>。  
  
 任何支援虛擬化的 <xref:System.Windows.Controls.ItemsControl> 都可以使用容器回收。  如需如何對 <xref:System.Windows.Controls.ListBox> 啟用容器回收的範例，請參閱 [改善 ListBox 的捲動效能](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)。  
  
<a name="Supporting"></a>   
## 支援雙向虛擬化  
 <xref:System.Windows.Controls.VirtualizingStackPanel> 提供您 UI 虛擬化的單向內建支援，可以是水平方向也可以是垂直方向的。  如果要針對控制項使用雙向虛擬化，必須實作會擴充 <xref:System.Windows.Controls.VirtualizingStackPanel> 類別的自訂面板。  <xref:System.Windows.Controls.VirtualizingStackPanel> 類別會公開 \(Expose\) 虛擬方法，例如 <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>、<xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>、<xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A> 和 <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>。這些虛擬方法可以讓您偵測清單中可見部分的變更，並進行相對應的處理。  
  
<a name="Optimizing"></a>   
## 最佳化範本  
 視覺化樹狀結構包含應用程式中的所有視覺項目。  除了直接建立的物件之外，也包含範本擴充所帶來的物件。  例如，在建立 <xref:System.Windows.Controls.Button> 時，在視覺化樹狀結構中也會有 <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> 和 <xref:System.Windows.Controls.ContentPresenter> 物件。  如果您不曾最佳化控制項範本，則可能在視覺化樹狀結構中建立許多不必要的額外物件。  如需視覺化樹狀結構的詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
<a name="Deferred"></a>   
## 延後捲動  
 根據預設，在使用者拖曳捲軸的捲動方塊時，會不斷更新內容檢視。  如果控制項中的捲動作業緩慢，請考慮使用延後捲動。  在延後捲動的情況下，只有當使用者釋放捲動方塊時才會更新內容。  
  
 若要實作延後捲動，將 <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 屬性設為 `true`。  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 附加屬性的設定，可以用於 <xref:System.Windows.Controls.ScrollViewer> 以及控制項範本中具有 <xref:System.Windows.Controls.ScrollViewer> 的任何控制項。  
  
<a name="Controls"></a>   
## 實作效能功能的控制項  
 下表列出用於顯示資料的常見控制項，以及其支援的效能功能。  如需如何啟用這些功能的詳細資訊，請參閱前面的小節。  
  
|控制項|虛擬化|容器回收|延後捲動|  
|---------|---------|----------|----------|  
|<xref:System.Windows.Controls.ComboBox>|可以啟用|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.ContextMenu>|可以啟用|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.DocumentViewer>|無法使用|無法使用|可以啟用|  
|<xref:System.Windows.Controls.ListBox>|Default|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.ListView>|Default|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.TreeView>|可以啟用|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.ToolBar>|無法使用|無法使用|可以啟用|  
  
> [!NOTE]
>  如需如何對 <xref:System.Windows.Controls.TreeView> 啟用虛擬化和容器回收的範例，請參閱 [改善 TreeView 的效能](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)。  
  
## 請參閱  
 [配置](../../../../docs/framework/wpf/advanced/layout.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [控制項](../../../../docs/framework/wpf/controls/index.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [逐步解說：在 WPF 應用程式中快取應用程式資料](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)