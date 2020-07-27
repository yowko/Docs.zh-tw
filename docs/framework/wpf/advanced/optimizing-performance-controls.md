---
title: 優化控制效能
description: Windows Presentation Foundation 包含大部分 Windows 應用程式中使用的許多常見元件。 瞭解如何改善使用者介面的效能。
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: de348dd93e5710b5b81af035ec7aa56e01dc4981
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168308"
---
# <a name="optimizing-performance-controls"></a>優化效能：控制項

Windows Presentation Foundation （WPF）包含大部分 Windows 應用程式中使用的許多常見使用者介面（UI）元件。 本主題包含提升 UI 效能的技巧。

## <a name="displaying-large-data-sets"></a>顯示大型資料集

WPF 控制項（例如 <xref:System.Windows.Controls.ListView> 和） <xref:System.Windows.Controls.ComboBox> 會用來顯示應用程式中的專案清單。 如果要顯示的清單是大型清單，可能會影響應用程式的效能。 這是因為標準版面配置系統會建立與清單控制項相關聯之每個項目的版面配置容器，並計算其版面配置的大小和位置。 一般而言，您不需要同時顯示所有項目；而可以改為顯示子集，讓使用者自行捲動清單。 在此情況下，使用虛擬化 UI** 就是合理的作法，這表示，系統會延後產生項目的項目容器和相關聯的版面配置計算，直到顯示項目為止。

UI 虛擬化是清單控制項的重要層面。 請不要將 UI 虛擬化和資料虛擬化混淆。 UI 虛擬化只會在記憶體中存放可見的項目；若為資料繫結案例，則會在記憶體中存放整個資料結構。 相反地，資料虛擬化只會在記憶體中存放螢幕上顯示的資料項目。

根據預設， <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ListBox> 當和控制項的清單專案系結至資料時，會對其啟用 UI 虛擬化。 <xref:System.Windows.Controls.TreeView>將附加屬性設定為，即可啟用虛擬化 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> `true` 。 如果您想要啟用自訂控制項（衍生自 <xref:System.Windows.Controls.ItemsControl> ）或使用類別之現有專案控制項（例如）的 UI 虛擬化， <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.ComboBox> 您可以將設定 <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> 為 <xref:System.Windows.Controls.VirtualizingStackPanel> ，並將設 <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> 為 `true` 。 不過，您可能會停用這些控制項的 UI 虛擬化而不自知。 以下是停用 UI 虛擬化的條件清單。

- 專案容器會直接加入至 <xref:System.Windows.Controls.ItemsControl> 。 例如，如果應用程式明確地將 <xref:System.Windows.Controls.ListBoxItem> 物件加入至 <xref:System.Windows.Controls.ListBox> ，則不 <xref:System.Windows.Controls.ListBox> 會將物件虛擬化 <xref:System.Windows.Controls.ListBoxItem> 。

- 中的專案容器屬於 <xref:System.Windows.Controls.ItemsControl> 不同的類型。 例如， <xref:System.Windows.Controls.Menu> 使用 <xref:System.Windows.Controls.Separator> 物件的無法執行專案回收，因為 <xref:System.Windows.Controls.Menu> 包含和類型的物件 <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.MenuItem> 。

- 將設定 <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> 為 `false` 。

- 將設定 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> 為 `false` 。

在虛擬化項目容器時，也應該考量是否具有與項目所屬之項目容器相關聯的其他狀態資訊。 在這種情況下，您必須將其他狀態儲存起來。 例如，您可能有一個專案包含在控制項中， <xref:System.Windows.Controls.Expander> 而該 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 狀態系結至專案的容器，而不是系結至專案本身。 當新專案重複使用容器時， <xref:System.Windows.Controls.Expander.IsExpanded%2A> 新專案會使用的目前值。 此外，舊專案會失去正確的 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 值。

目前，WPF 控制項皆未內建支援資料虛擬化。

## <a name="container-recycling"></a>容器回收

針對繼承自的控制項，在 .NET Framework 3.5 SP1 中新增的 UI 虛擬化優化 <xref:System.Windows.Controls.ItemsControl> 是*容器回收，* 這也可以改善滾動效能。 當 <xref:System.Windows.Controls.ItemsControl> 已填入使用 UI 虛擬化的時，它會為每個可向外查看的專案建立一個專案容器，並為每個向外流覽的專案終結專案容器。 *容器回收*可讓控制項針對不同資料項目重複使用現有的專案容器，以便在使用者滾動時，不會經常建立和終結專案容器 <xref:System.Windows.Controls.ItemsControl> 。 您可以將附加屬性設定為，以選擇啟用專案回收 <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> <xref:System.Windows.Controls.VirtualizationMode.Recycling> 。

任何 <xref:System.Windows.Controls.ItemsControl> 支援虛擬化的都可以使用容器回收。 如需如何在上啟用容器回收的範例 <xref:System.Windows.Controls.ListBox> ，請參閱[改善 ListBox 的滾動效能](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)。

## <a name="supporting-bidirectional-virtualization"></a>支援雙向虛擬化

<xref:System.Windows.Controls.VirtualizingStackPanel>以水準或垂直方式提供對 UI 虛擬化的內建支援。 如果您想要針對控制項使用雙向虛擬化，則必須執行擴充類別的自訂面板 <xref:System.Windows.Controls.VirtualizingStackPanel> 。 <xref:System.Windows.Controls.VirtualizingStackPanel>類別會公開虛擬方法，例如 <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A> 、 <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A> 、 <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A> 和 <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A> 。這些虛擬方法可讓您偵測清單可見部分中的變更，並據以處理。

## <a name="optimizing-templates"></a>優化範本

視覺化樹狀結構包含應用程式中所使用的所有視覺項目。 除了直接建立的物件，它也包含範本展開所帶來的物件。 例如，當您建立時 <xref:System.Windows.Controls.Button> ，您也會 <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.ContentPresenter> 在視覺化樹狀結構中取得和物件。 如果您尚未最佳化控制項範本，視覺化樹狀結構中就可能會建立許多不必要的物件。 如需視覺化樹狀結構的詳細資訊，請參閱 [WPF 圖形呈現概觀](../graphics-multimedia/wpf-graphics-rendering-overview.md)。

## <a name="deferred-scrolling"></a>延後捲動

根據預設，當使用者拖曳捲軸上的捲動方塊時，內容檢視就會不斷更新。 如果控制項中的捲動變慢，請考慮使用延後捲動。 延後捲動時，只有當使用者放開捲動方塊之後，才會更新內容。

若要執行延後的滾動，請將 <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 屬性設定為 `true` 。 <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>是附加屬性，而且可以在 <xref:System.Windows.Controls.ScrollViewer> 控制項範本中的和任何具有的控制項上設定 <xref:System.Windows.Controls.ScrollViewer> 。

## <a name="controls-that-implement-performance-features"></a>執行效能功能的控制項

下表列出用來顯示資料的常見控制項，以及其支援的效能功能。 請參閱前面幾節，以取得如何啟用這些功能的資訊。

|控制|虛擬化|容器回收|延後捲動|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|可以啟用|可以啟用|可以啟用|
|<xref:System.Windows.Controls.ContextMenu>|可以啟用|可以啟用|可以啟用|
|<xref:System.Windows.Controls.DocumentViewer>|無法使用|無法使用|可以啟用|
|<xref:System.Windows.Controls.ListBox>|預設|可以啟用|可以啟用|
|<xref:System.Windows.Controls.ListView>|預設|可以啟用|可以啟用|
|<xref:System.Windows.Controls.TreeView>|可以啟用|可以啟用|可以啟用|
|<xref:System.Windows.Controls.ToolBar>|無法使用|無法使用|可以啟用|

> [!NOTE]
> 如需如何在上啟用虛擬化和容器回收的範例 <xref:System.Windows.Controls.TreeView> ，請參閱[改善 TreeView 的效能](../controls/how-to-improve-the-performance-of-a-treeview.md)。

## <a name="see-also"></a>另請參閱

- [版面配置](layout.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [資料系結](optimizing-performance-data-binding.md)
- [控制項](../controls/index.md)
- [樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [逐步解說：在 WPF 應用程式中快取應用程式資料](walkthrough-caching-application-data-in-a-wpf-application.md)
