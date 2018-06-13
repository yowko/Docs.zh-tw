---
title: 最佳化效能：控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 9e4ceee26263a1d047aeda0881b955070de4326d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549259"
---
# <a name="optimizing-performance-controls"></a>最佳化效能：控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 包含許多可用於大多數 Windows 應用程式的通用使用者介面 (UI) 元件。 本主題包含提升 UI 效能的技巧。  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>顯示大型資料集  
 WPF 控制項，例如<xref:System.Windows.Controls.ListView>和<xref:System.Windows.Controls.ComboBox>用來顯示應用程式中的項目清單。 如果要顯示的清單是大型清單，可能會影響應用程式的效能。 這是因為標準版面配置系統會建立與清單控制項相關聯之每個項目的版面配置容器，並計算其版面配置的大小和位置。 一般而言，您不需要同時顯示所有項目；而可以改為顯示子集，讓使用者自行捲動清單。 在此情況下，使用虛擬化 UI 就是合理的作法，這表示，系統會延後產生項目的項目容器和相關聯的版面配置計算，直到顯示項目為止。  
  
 UI 虛擬化是清單控制項的重要層面。 請不要將 UI 虛擬化和資料虛擬化混淆。 UI 虛擬化只會在記憶體中存放可見的項目；若為資料繫結案例，則會在記憶體中存放整個資料結構。 相反地，資料虛擬化只會在記憶體中存放螢幕上顯示的資料項目。  
  
 根據預設，啟用 UI 虛擬化的<xref:System.Windows.Controls.ListView>和<xref:System.Windows.Controls.ListBox>控制其清單項目資料繫結。 <xref:System.Windows.Controls.TreeView> 您可以啟用虛擬化設定<!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> -->`IsVirtualizing`附加屬性`true`。 如果您想要啟用自訂控制項衍生自 UI 虛擬化<xref:System.Windows.Controls.ItemsControl>或現有的項目控制項使用<xref:System.Windows.Controls.StackPanel>類別，例如<xref:System.Windows.Controls.ComboBox>，您可以設定<xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A>至<xref:System.Windows.Controls.VirtualizingStackPanel>並設定<xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A>至`true`. 不過，您可能會停用這些控制項的 UI 虛擬化而不自知。 以下是停用 UI 虛擬化的條件清單。  
  
-   項目容器會直接加入<xref:System.Windows.Controls.ItemsControl>。 例如，如果應用程式明確地加入<xref:System.Windows.Controls.ListBoxItem>物件加入至<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ListBox>未虛擬化<xref:System.Windows.Controls.ListBoxItem>物件。  
  
-   項目中的容器<xref:System.Windows.Controls.ItemsControl>屬於不同類型。 例如，<xref:System.Windows.Controls.Menu>使用<xref:System.Windows.Controls.Separator>物件不能實作項目回收，因為<xref:System.Windows.Controls.Menu>包含型別的物件<xref:System.Windows.Controls.Separator>和<xref:System.Windows.Controls.MenuItem>。  
  
-   設定<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>至`false`。  
  
-   設定<!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>-->`IsVirtualizing`至`false`。  
  
 在虛擬化項目容器時，也應該考量是否具有與項目所屬之項目容器相關聯的其他狀態資訊。 在這種情況下，您必須將其他狀態儲存起來。 例如，您可能必須包含在項目<xref:System.Windows.Controls.Expander>控制項和<xref:System.Windows.Controls.Expander.IsExpanded%2A>所繫結項目的容器，而不在項目本身的狀態。 當容器會重複使用的新項目，目前的值<xref:System.Windows.Controls.Expander.IsExpanded%2A>用於新的項目。 此外，舊的項目失去正確<xref:System.Windows.Controls.Expander.IsExpanded%2A>值。  
  
 目前，WPF 控制項皆未內建支援資料虛擬化。  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>容器回收  
 在.NET Framework 3.5 SP1，繼承的控制項加入 UI 虛擬化的最佳化<xref:System.Windows.Controls.ItemsControl>是*容器回收、* 也可以改善捲動的效能。  當<xref:System.Windows.Controls.ItemsControl>，使用 UI 虛擬化會擴展，它會建立每個項目捲動到檢視，並終結的項目容器，每個項目捲動超出檢視的項目容器。 *容器回收*可讓控制項重複使用現有的項目容器的不同資料的項目，使項目容器不會持續建立和終結捲動<xref:System.Windows.Controls.ItemsControl>。 您可以選擇啟用回收藉由設定項目<xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A>附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling>。  
  
 任何<xref:System.Windows.Controls.ItemsControl>虛擬化可以使用容器回收的支援。  如需如何啟用容器回收上的範例<xref:System.Windows.Controls.ListBox>，請參閱[改善捲動的效能 ListBox](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)。  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>支援雙向虛擬化  
 <xref:System.Windows.Controls.VirtualizingStackPanel> 提供內建支援一個方向的 UI 虛擬化，水平或垂直。 如果您想要使用雙向虛擬化您的控制項，您必須實作自訂的面板擴充<xref:System.Windows.Controls.VirtualizingStackPanel>類別。 <xref:System.Windows.Controls.VirtualizingStackPanel>類別會公開虛擬方法例如<xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>， <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>， <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>，和<xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>。這些虛擬方法可讓您在清單的可見部分中偵測到變更，並據以處理。  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>最佳化範本  
 視覺化樹狀結構包含應用程式中所使用的所有視覺項目。  除了直接建立的物件，它也包含範本展開所帶來的物件。  例如，當您建立<xref:System.Windows.Controls.Button>，您也可以取得<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>和<xref:System.Windows.Controls.ContentPresenter>視覺化樹狀結構中的物件。  如果您尚未最佳化控制項範本，視覺化樹狀結構中就可能會建立許多不必要的物件。   如需視覺化樹狀結構的詳細資訊，請參閱 [WPF 圖形呈現概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>延後捲動  
 根據預設，當使用者拖曳捲軸上的捲動方塊時，內容檢視就會不斷更新。  如果控制項中的捲動變慢，請考慮使用延後捲動。  延後捲動時，只有當使用者放開捲動方塊之後，才會更新內容。  
  
 若要實作延後捲動功能，設定<xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>屬性`true`。  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 是附加的屬性，而且可以設定上<xref:System.Windows.Controls.ScrollViewer>和具有任何控制項<xref:System.Windows.Controls.ScrollViewer>控制項範本中。  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>實作效能功能的控制項  
 下表列出用來顯示資料的常見控制項，以及其支援的效能功能。  請參閱前面幾節，以取得如何啟用這些功能的資訊。  
  
|控制項|虛擬化|容器回收|延後捲動|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|可以啟用|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.ContextMenu>|可以啟用|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.DocumentViewer>|無法使用|無法使用|可以啟用|  
|<xref:System.Windows.Controls.ListBox>|預設|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.ListView>|預設|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.TreeView>|可以啟用|可以啟用|可以啟用|  
|<xref:System.Windows.Controls.ToolBar>|無法使用|無法使用|可以啟用|  
  
> [!NOTE]
>  如需如何啟用虛擬化和容器上回收<xref:System.Windows.Controls.TreeView>，請參閱[改善效能的 treeview](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [版面配置](../../../../docs/framework/wpf/advanced/layout.md)  
 [版面配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [控制項](../../../../docs/framework/wpf/controls/index.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [逐步解說：在 WPF 應用程式中快取應用程式資料](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
