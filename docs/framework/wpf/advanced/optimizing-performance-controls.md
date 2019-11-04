---
title: 優化效能：控制項-WPF
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 595a4865e1d422f460aab18fc541326a4557476b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458534"
---
# <a name="optimizing-performance-controls"></a>優化效能：控制項

Windows Presentation Foundation （WPF）包含大部分 Windows 應用程式中使用的許多常見使用者介面（UI）元件。 本主題包含提升 UI 效能的技巧。

## <a name="displaying-large-data-sets"></a>顯示大型資料集

<xref:System.Windows.Controls.ListView> 和 <xref:System.Windows.Controls.ComboBox> 之類的 WPF 控制項，可用來顯示應用程式中的專案清單。 如果要顯示的清單是大型清單，可能會影響應用程式的效能。 這是因為標準版面配置系統會建立與清單控制項相關聯之每個項目的版面配置容器，並計算其版面配置的大小和位置。 一般而言，您不需要同時顯示所有項目；而可以改為顯示子集，讓使用者自行捲動清單。 在此情況下，使用虛擬化 UI 就是合理的作法，這表示，系統會延後產生項目的項目容器和相關聯的版面配置計算，直到顯示項目為止。

UI 虛擬化是清單控制項的重要層面。 請不要將 UI 虛擬化和資料虛擬化混淆。 UI 虛擬化只會在記憶體中存放可見的項目；若為資料繫結案例，則會在記憶體中存放整個資料結構。 相反地，資料虛擬化只會在記憶體中存放螢幕上顯示的資料項目。

根據預設，<xref:System.Windows.Controls.ListView> 和 <xref:System.Windows.Controls.ListBox> 控制項的 UI 虛擬化會在其清單專案系結至資料時啟用。 藉由將 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> 附加屬性設定為 [`true`]，即可啟用 <xref:System.Windows.Controls.TreeView> 虛擬化。 如果您想要針對衍生自 <xref:System.Windows.Controls.ItemsControl> 或使用 <xref:System.Windows.Controls.StackPanel> 類別之現有專案控制項（例如 <xref:System.Windows.Controls.ComboBox>）的自訂控制項啟用 UI 虛擬化，您可以將 <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> 設定為 [<xref:System.Windows.Controls.VirtualizingStackPanel>]，並將 [<xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A>] 設定為 [`true`]。 不過，您可能會停用這些控制項的 UI 虛擬化而不自知。 以下是停用 UI 虛擬化的條件清單。

- 專案容器會直接新增至 <xref:System.Windows.Controls.ItemsControl>。 例如，如果應用程式明確地將 <xref:System.Windows.Controls.ListBoxItem> 物件加入 <xref:System.Windows.Controls.ListBox>中，則 <xref:System.Windows.Controls.ListBox> 不會將 <xref:System.Windows.Controls.ListBoxItem> 物件虛擬化。

- <xref:System.Windows.Controls.ItemsControl> 中的專案容器屬於不同的類型。 例如，使用 <xref:System.Windows.Controls.Separator> 物件的 <xref:System.Windows.Controls.Menu> 無法執行專案回收，因為 <xref:System.Windows.Controls.Menu> 包含 <xref:System.Windows.Controls.Separator> 和 <xref:System.Windows.Controls.MenuItem>類型的物件。

- 將 <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> 設定為 `false`。

- 將 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> 設定為 `false`。

在虛擬化項目容器時，也應該考量是否具有與項目所屬之項目容器相關聯的其他狀態資訊。 在這種情況下，您必須將其他狀態儲存起來。 例如，您可能有一個包含在 <xref:System.Windows.Controls.Expander> 控制項中的專案，而 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 狀態會系結至專案的容器，而不是系結至專案本身。 當新專案重複使用容器時，新專案會使用 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 的目前值。 此外，舊專案會失去正確的 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 值。

目前，WPF 控制項皆未內建支援資料虛擬化。

## <a name="container-recycling"></a>容器回收

針對繼承自 <xref:System.Windows.Controls.ItemsControl> 的控制項，在 .NET Framework 3.5 SP1 中新增的 UI 虛擬化優化是*容器回收，* 這也可以改善滾動效能。 填入使用 UI 虛擬化的 <xref:System.Windows.Controls.ItemsControl> 時，它會為每個可滾動到 view 的專案建立一個專案容器，並終結向外流覽之每個專案的專案容器。 *容器回收*可讓控制項針對不同資料項目重複使用現有的專案容器，如此一來，當使用者滾動 <xref:System.Windows.Controls.ItemsControl>時，就不會經常建立和終結專案容器。 您可以選擇將 [<xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A>] 附加屬性設定為 [<xref:System.Windows.Controls.VirtualizationMode.Recycling>]，藉以啟用專案回收。

任何支援虛擬化的 <xref:System.Windows.Controls.ItemsControl> 都可以使用容器回收。 如需如何在 <xref:System.Windows.Controls.ListBox>上啟用容器回收的範例，請參閱[改善 ListBox 的滾動效能](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)。

## <a name="supporting-bidirectional-virtualization"></a>支援雙向虛擬化

<xref:System.Windows.Controls.VirtualizingStackPanel> 以水準或垂直方式在單一方向提供對 UI 虛擬化的內建支援。 如果您想要針對控制項使用雙向虛擬化，則必須執行擴充 <xref:System.Windows.Controls.VirtualizingStackPanel> 類別的自訂面板。 <xref:System.Windows.Controls.VirtualizingStackPanel> 類別會公開 <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>、<xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>、<xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>和 <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>之類的虛擬方法。這些虛擬方法可讓您偵測清單可見部分中的變更，並據以處理。

## <a name="optimizing-templates"></a>優化範本

視覺化樹狀結構包含應用程式中所使用的所有視覺項目。 除了直接建立的物件，它也包含範本展開所帶來的物件。 例如，當您建立 <xref:System.Windows.Controls.Button>時，您也會在視覺化樹狀結構中取得 <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> 和 <xref:System.Windows.Controls.ContentPresenter> 物件。 如果您尚未最佳化控制項範本，視覺化樹狀結構中就可能會建立許多不必要的物件。 如需視覺化樹狀結構的詳細資訊，請參閱 [WPF 圖形呈現概觀](../graphics-multimedia/wpf-graphics-rendering-overview.md)。

## <a name="deferred-scrolling"></a>延後捲動

根據預設，當使用者拖曳捲軸上的捲動方塊時，內容檢視就會不斷更新。 如果控制項中的捲動變慢，請考慮使用延後捲動。 延後捲動時，只有當使用者放開捲動方塊之後，才會更新內容。

若要執行延後的滾動，請將 <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 屬性設為 `true`。 <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 是附加屬性，而且可以在 <xref:System.Windows.Controls.ScrollViewer> 和控制項範本中具有 <xref:System.Windows.Controls.ScrollViewer> 的任何控制項上設定。

## <a name="controls-that-implement-performance-features"></a>執行效能功能的控制項

下表列出用來顯示資料的常見控制項，以及其支援的效能功能。 請參閱前面幾節，以取得如何啟用這些功能的資訊。

|控制項|虛擬化|容器回收|延後捲動|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|可以啟用|可以啟用|可以啟用|
|<xref:System.Windows.Controls.ContextMenu>|可以啟用|可以啟用|可以啟用|
|<xref:System.Windows.Controls.DocumentViewer>|無法使用|無法使用|可以啟用|
|<xref:System.Windows.Controls.ListBox>|Default|可以啟用|可以啟用|
|<xref:System.Windows.Controls.ListView>|Default|可以啟用|可以啟用|
|<xref:System.Windows.Controls.TreeView>|可以啟用|可以啟用|可以啟用|
|<xref:System.Windows.Controls.ToolBar>|無法使用|無法使用|可以啟用|

> [!NOTE]
> 如需如何在 <xref:System.Windows.Controls.TreeView>上啟用虛擬化和容器回收的範例，請參閱[改善 TreeView 的效能](../controls/how-to-improve-the-performance-of-a-treeview.md)。

## <a name="see-also"></a>請參閱

- [版面配置](layout.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [控制項](../controls/index.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [逐步解說：在 WPF 應用程式中快取應用程式資料](walkthrough-caching-application-data-in-a-wpf-application.md)
