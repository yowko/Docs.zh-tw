---
title: 面板概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 5fe464f2b79fa1f7b0674c049110d32f2ad32335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944812"
---
# <a name="panels-overview"></a>面板概觀
<xref:System.Windows.Controls.Panel>元素是控制專案轉譯的元件, 其大小和維度、位置, 以及其子內容的相片順序。 提供數個預先定義<xref:System.Windows.Controls.Panel>的專案, 以及可建立自訂<xref:System.Windows.Controls.Panel>元素的能力。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]  
  
 此主題包括下列各節。  
  
- [面板類別](#Panels_view_from_10000_feet)  
  
- [面板元素的一般成員](#Panels_declared_members)  
  
- [衍生的面板元素](#Panels_derived_elements)  
  
- [使用者介面面板](#Panels_main_UI_elements)  
  
- [巢狀面板元素](#Panels_nested_panel_elements)  
  
- [自訂面板元素](#Panels_custom_panel_elements)  
  
- [當地語系化/全球化支援](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>面板類別  
 <xref:System.Windows.Controls.Panel>是在中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供版面配置支援之所有專案的基類 (base class)。 衍生<xref:System.Windows.Controls.Panel>的專案是用來定位和排列和[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼中的元素。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含一套完整的衍生面板實作，可讓您進行許多複雜的版面配置。 這些衍生的類別會公開可促成大多數標準 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 案例的屬性和方法。 找不到符合其需求的子系排列行為的開發人員, 可以藉由覆寫<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>和<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法來建立新的版面配置。 如需有關自訂版面配置行為的詳細資訊，請參閱[自訂面板元素](#Panels_custom_panel_elements)。  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>面板的一般成員  
 所有<xref:System.Windows.Controls.Panel>元素都支援所<xref:System.Windows.FrameworkElement>定義的基底調整大小和<xref:System.Windows.FrameworkElement.Height%2A>位置屬性, 包括<xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、和。 如需定位所<xref:System.Windows.FrameworkElement>定義之屬性的詳細資訊, 請參閱[對齊、邊界和填補總覽](../advanced/alignment-margins-and-padding-overview.md)。  
  
 <xref:System.Windows.Controls.Panel>公開瞭解和使用版面配置中重要重要性的其他屬性。 屬性是用來填滿<xref:System.Windows.Media.Brush>具有的衍生面板元素界限之間的區域。 <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Panel.Children%2A>表示由組成之元素<xref:System.Windows.Controls.Panel>的子集合。 <xref:System.Windows.Controls.Panel.InternalChildren%2A>表示<xref:System.Windows.Controls.Panel.Children%2A>集合的內容, 加上資料系結所產生的成員。 兩者都是<xref:System.Windows.Controls.UIElementCollection>由父系<xref:System.Windows.Controls.Panel>內裝載之子專案的組成。  
  
 面板也會公開<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>附加屬性, 可用來在衍生<xref:System.Windows.Controls.Panel>的中達成分層順序。 具有較高<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>值的<xref:System.Windows.Controls.Panel.Children%2A>面板集合成員會出現在較低<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>值的前面。 這對於的面板 (例如<xref:System.Windows.Controls.Canvas>和) 而言特別有用, <xref:System.Windows.Controls.Grid>可讓子系共用相同的座標空間。  
  
 <xref:System.Windows.Controls.Panel>也會定義<xref:System.Windows.Controls.Panel.OnRender%2A>方法, 其可用來覆寫的預設呈現行為。 <xref:System.Windows.Controls.Panel>  
  
#### <a name="attached-properties"></a>附加屬性  
 衍生的面板元素廣泛運用了附加屬性。 附加屬性是不具有傳統 common language runtime (CLR) 屬性「包裝函式」的特殊形式的相依性屬性。 附加屬性在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中有特製化的語法，在接下來的數個範例中將可以看到。  
  
 附加屬性的其中一個用途是要允許子元素儲存父元素實際定義之屬性的唯一值。 此功能的其中一項應用是讓子元素通知父元素它們想要如何在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中呈現，這對應用程式版面配置而言極為有用。 如需詳細資訊，請參閱[附加屬性概觀](../advanced/attached-properties-overview.md)。  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>衍生的面板元素  
 許多物件都是<xref:System.Windows.Controls.Panel>衍生自, 但並非全部都是用於根配置提供者。 有六個定義的面板類別<xref:System.Windows.Controls.Canvas>( <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.VirtualizingStackPanel>、和<xref:System.Windows.Controls.WrapPanel>) 專門設計來建立應用程式[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 每個面板元素都會封裝自己的特殊功能，如下表所示。  
  
|元素名稱|UI 面板？|描述|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|是|定義一個區域, 您可以在其中以相對於<xref:System.Windows.Controls.Canvas>區域的座標, 明確地定位子項目。|  
|<xref:System.Windows.Controls.DockPanel>|是|定義一個區域，可供您在其中以子項目彼此間相對的水平或垂直方式排列子項目。|  
|<xref:System.Windows.Controls.Grid>|是|定義由資料行與資料列組成的彈性方格區域。 的子項目<xref:System.Windows.Controls.Grid>可以<xref:System.Windows.FrameworkElement.Margin%2A>使用屬性精確定位。|  
|<xref:System.Windows.Controls.StackPanel>|是|將子元素排成單一行，以水平或垂直方式排列。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|否|處理中<xref:System.Windows.Controls.TabControl>索引標籤按鈕的版面配置。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|否|排列控制項內的<xref:System.Windows.Controls.ToolBar>內容。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|否|<xref:System.Windows.Controls.Primitives.UniformGrid>是用來排列具有所有相等儲存格大小之方格中的子系。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|否|為面板提供一個可將其子集合「虛擬化」的基底類別。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|是|將內容以單行水平方向或垂直方向來排列並虛擬化。|  
|<xref:System.Windows.Controls.WrapPanel>|是|<xref:System.Windows.Controls.WrapPanel>從左至右將子專案放在順序位置, 將內容細分為包含方塊邊緣的下一行。 根據<xref:System.Windows.Controls.WrapPanel.Orientation%2A>屬性的值, 後續順序會依序從上到下或由右至左進行。|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>使用者介面面板  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中有六個可用的面板類別, 已優化為[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]支援案例<xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.VirtualizingStackPanel>: <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.StackPanel>、、和<xref:System.Windows.Controls.WrapPanel>。 這些面板元素相當容易使用、多樣化且可延伸，足以滿足大多數應用程式的需求。  
  
 每個<xref:System.Windows.Controls.Panel>衍生的專案會以不同的方式來對待大小限制。 瞭解如何<xref:System.Windows.Controls.Panel>在水準或垂直方向處理條件約束, 可以讓版面配置更容易預測。  
  
|**面板名稱**|**x 維度**|**y 維度**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|受內容限制|受內容限制|  
|<xref:System.Windows.Controls.DockPanel>|受限|受限|  
|<xref:System.Windows.Controls.StackPanel>(垂直方向)|受限|受內容限制|  
|<xref:System.Windows.Controls.StackPanel>(水準方向)|受內容限制|受限|  
|<xref:System.Windows.Controls.Grid>|受限|條件<xref:System.Windows.GridUnitType.Auto>約束, 但適用于資料列和資料行的情況除外|  
|<xref:System.Windows.Controls.WrapPanel>|受內容限制|受內容限制|  
  
 如需這些元素中每個元素的詳細描述和使用方式範例，請參閱下方。  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Canvas  
 元素會根據絕對 x 和*y*座標來啟用內容的定位。 <xref:System.Windows.Controls.Canvas> 元素的繪製位置可以是一個唯一的位置；或者，如果元素佔據相同的座標，則它們在標記中的出現順序會決定元素的繪製順序。  
  
 <xref:System.Windows.Controls.Canvas>為任何<xref:System.Windows.Controls.Panel>提供最具彈性的版面配置支援。 Height 和 Width 屬性是用來定義畫布的區域, 而內的專案則是指派相對於父系<xref:System.Windows.Controls.Canvas>區域的絕對座標。 四個附加屬性<xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>: <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> 、和<xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, 可讓您精確控制中<xref:System.Windows.Controls.Canvas>的物件位置, 讓開發人員能夠在螢幕上精確定位和排列元素。  
  
#### <a name="cliptobounds-within-a-canvas"></a>畫布內的 ClipToBounds  
 <xref:System.Windows.Controls.Canvas>可以將子專案放在螢幕上的任何位置, 即使是在其本身定義<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>之外的座標。 此外, <xref:System.Windows.Controls.Canvas>不會受到其子系的大小影響。 因此, 子項目可以過度繪製父系<xref:System.Windows.Controls.Canvas>周框外的其他元素。 的預設行為<xref:System.Windows.Controls.Canvas>是允許子系在父系<xref:System.Windows.Controls.Canvas>的界限外繪製。 如果不想要此行為, <xref:System.Windows.UIElement.ClipToBounds%2A>可以將屬性設定為`true`。 這會<xref:System.Windows.Controls.Canvas>導致裁剪到它自己的大小。 <xref:System.Windows.Controls.Canvas>是唯一允許子系在其範圍外繪製的配置元素。  
  
 在[寬度屬性比較範例](https://go.microsoft.com/fwlink/?LinkID=160050)中有此行為的圖例解說。  
  
#### <a name="defining-and-using-a-canvas"></a>定義和使用 Canvas  
 只要使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼,就可以具現化。<xref:System.Windows.Controls.Canvas> 下列範例示範如何使用<xref:System.Windows.Controls.Canvas>絕對位置內容。 此程式碼會產生三個 100 像素的方形。 第一個方形為紅色，其左上角 (*x, y*) 位置是指定為 (0, 0)。 第二個方形為綠色，其左上角位置是 (100, 100)，正好是在第一個方形的右下方。 第三個方形為藍色，其左上角位置是 (50, 50)，因此包含第一個方形的右下象限，以及第二個方形的左上象限。 由於第三個方形是最後放置的，因此它會顯示在另外兩個方形上方，也就是說，重疊部分會呈現第三個方塊的顏色。  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 Canvas 元素。](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 元素會使用子<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> content 元素中設定的附加屬性, 沿著容器的邊緣放置內容。 <xref:System.Windows.Controls.DockPanel> 當<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>設定為<xref:System.Windows.Controls.Dock.Top> 或<xref:System.Windows.Controls.Dock.Bottom>時, 它會將子項目放在彼此的上方或下方。 當<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>設定為<xref:System.Windows.Controls.Dock.Left> 或<xref:System.Windows.Controls.Dock.Right>時, 它會將子項目放在彼此的左邊或右方。 屬性會決定加入做為子系<xref:System.Windows.Controls.DockPanel>之最後一個元素的位置。 <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>  
  
 您可以使用<xref:System.Windows.Controls.DockPanel>來放置相關控制項的群組, 例如一組按鈕。 或者, 您可以使用它來建立「窗格[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]」, 類似于 Microsoft Outlook 中所找到的。  
  
#### <a name="sizing-to-content"></a>依內容調整大小  
 如果未<xref:System.Windows.FrameworkElement.Height%2A>指定<xref:System.Windows.FrameworkElement.Width%2A>其和屬性, <xref:System.Windows.Controls.DockPanel>則為其內容的大小。 大小可以因應其子元素的大小來增加或縮減。 不過, 當指定這些屬性, 但沒有下一個指定子專案的空間時, <xref:System.Windows.Controls.DockPanel>就不會顯示該子項目或後續的子專案, 也不會測量後續的子項目。  
  
#### <a name="lastchildfill"></a>LastChildFill  
 根據預設, <xref:System.Windows.Controls.DockPanel>元素的最後一個子系會「填滿」剩餘的未配置空間。 如果不想要此行為, 請將<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>屬性設定`false`為。  
  
#### <a name="defining-and-using-a-dockpanel"></a>定義和使用 DockPanel  
 下列範例示範如何使用<xref:System.Windows.Controls.DockPanel>分割空間。 有<xref:System.Windows.Controls.Border>五個元素會當做父系<xref:System.Windows.Controls.DockPanel>的子系加入。 每個都會使用不同的<xref:System.Windows.Controls.DockPanel>定位屬性來分割空間。 最後的元素會「填滿」剩餘的未配置空間。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 DockPanel 案例。](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Grid  
 <xref:System.Windows.Controls.Grid>元素會合並絕對位置和表格式資料控制項的功能。 可<xref:System.Windows.Controls.Grid>讓您輕鬆地定位和樣式元素。 <xref:System.Windows.Controls.Grid>可讓您定義彈性的資料列和資料行群組, 甚至提供在多個<xref:System.Windows.Controls.Grid>元素之間共用調整大小資訊的機制。  
  
#### <a name="how-is-grid-different-from-table"></a>Grid 和 Table 有何不同？  
 <xref:System.Windows.Documents.Table>和<xref:System.Windows.Controls.Grid>共用一些常見的功能, 但每個都適用于不同的案例。 的<xref:System.Windows.Documents.Table>設計目的是要在非固定格式內容中使用 (如需有關「流動內容」的詳細資訊, 請參閱[flow 檔總覽](../advanced/flow-document-overview.md))。 方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。 在中<xref:System.Windows.Documents.Table> <xref:System.Windows.Controls.Grid> , 支援分頁、資料行重新排列和內容選取等非固定格式內容行為。 <xref:System.Windows.Documents.FlowDocument> 另一方面, 最好是<xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Documents.Table>在之外使用, 因為有許多原因, 包括根據資料列和資料行索引來加入元素。 <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid>元素允許子內容的分層, 讓一個以上的專案存在於單一「資料格」內。 <xref:System.Windows.Documents.Table>不支援分層。 的子項目<xref:System.Windows.Controls.Grid>可以相對於其「儲存格」界限的區域進行絕對位置。 <xref:System.Windows.Documents.Table>不支援這項功能。 最後, 的<xref:System.Windows.Controls.Grid>權數<xref:System.Windows.Documents.Table>比更輕。  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>資料行和資料列的調整大小行為  
 在中定義的<xref:System.Windows.Controls.Grid>資料行和資料列可以<xref:System.Windows.GridUnitType.Star>利用調整大小, 以按比例分配其餘的空間。 當<xref:System.Windows.GridUnitType.Star>選取做為資料列或資料行的高度或寬度時, 該資料行或資料列會收到剩餘可用空間的加權比例。 這與不同<xref:System.Windows.GridUnitType.Auto>, 它會根據資料行或資料列內的內容大小, 將空間平均分散。 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 時，這個值是以 `*` 或 `2*` 表示。 在第一個案例中，資料列或資料行會獲得一倍的可用空間，在第二個案例中，則會獲得兩倍的可用空間，依此類推。 藉由結合這項技術來按比例分配<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>具有<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>和值`Stretch`的空間, 可以透過螢幕空間百分比分割版面配置空間。 <xref:System.Windows.Controls.Grid>是唯一能夠以這種方式散佈空間的版面配置面板。  
  
#### <a name="defining-and-using-a-grid"></a>定義和使用 Grid  
 下列範例示範如何建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]類似于在 Windows [開始] 功能表上的 [執行] 對話方塊中找到的。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 Grid 元素。](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 可<xref:System.Windows.Controls.StackPanel>讓您以指定的方向「堆疊」元素。 預設的堆疊方向為垂直。 <xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性可以用來控制內容流程。  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel 與DockPanel  
 雖然<xref:System.Windows.Controls.DockPanel>也可以「堆疊」子項目, <xref:System.Windows.Controls.DockPanel>而且<xref:System.Windows.Controls.StackPanel>在某些使用案例中不會產生類似的結果。 例如, 子專案的順序可能會影響其在中<xref:System.Windows.Controls.DockPanel>的大小, 而不是<xref:System.Windows.Controls.StackPanel>中的。 這是因為<xref:System.Windows.Controls.StackPanel>量值是<xref:System.Double.PositiveInfinity>堆疊的方向, 而<xref:System.Windows.Controls.DockPanel>只測量可用的大小。  
  
 下列範例示範這項主要的差異。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 下圖顯示轉譯行為的差異。  
  
 ![截取StackPanel 與DockPanel 螢幕擷取畫面的比較](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>定義和使用 StackPanel  
 下列範例示範如何使用<xref:System.Windows.Controls.StackPanel>來建立一組垂直定位的按鈕。 針對水準定位, 將<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性設定為。 <xref:System.Windows.Controls.Orientation.Horizontal>  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 StackPanel 元素。](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也提供可自動「虛擬<xref:System.Windows.Controls.StackPanel>化」資料系結子內容的元素變化。 在此內容中，「虛擬化」一字係指一種技術，藉由這種技術，將可從較大量的資料項目，根據畫面上可見的項目來產生元素子集。 當在指定的時間內畫面上只能有幾個 UI 項目時，不論是就記憶體還是處理器而言，產生大量 UI 項目都會相當耗費資源。 <xref:System.Windows.Controls.VirtualizingStackPanel>(透過提供<xref:System.Windows.Controls.VirtualizingPanel>的功能) 會計算可見專案, 並使用<xref:System.Windows.Controls.ItemContainerGenerator> <xref:System.Windows.Controls.ListBox>從<xref:System.Windows.Controls.ItemsControl> (例如或<xref:System.Windows.Controls.ListView>) 的來建立可見專案的元素。  
  
 元素會自動設定為控制項 (例如<xref:System.Windows.Controls.ListBox>) 的專案主機。 <xref:System.Windows.Controls.VirtualizingStackPanel> 裝載資料系結集合時, 只要內容在的界限<xref:System.Windows.Controls.ScrollViewer>內, 內容就會自動虛擬化。 當裝載許多子項目時，這可大幅改善效能。  
  
 下列標記會示範如何使用<xref:System.Windows.Controls.VirtualizingStackPanel>做為專案主控制項。 附加屬性必須設定為`true` (預設值), 才會發生虛擬化。 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>是用來從左至右的順序位置放置子專案, 並在到達其父容器的邊緣時, 將內容細分為下一行。 內容的方向可以是水平或垂直方向。 <xref:System.Windows.Controls.WrapPanel>適用于簡單的流動[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]案例。 它也可用來在其所有子元素套用統一的大小。  
  
 下列範例示範如何建立<xref:System.Windows.Controls.WrapPanel> , 以顯示<xref:System.Windows.Controls.Button>當控制項到達其容器的邊緣時, 會換行。  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 WrapPanel 元素。](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>巢狀面板元素  
 <xref:System.Windows.Controls.Panel>專案可以彼此嵌套, 以便產生複雜的版面配置。 當其中一個<xref:System.Windows.Controls.Panel>適合某個部分[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], 但可能不符合的不同部分[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的需求時, 這會非常有用。  
  
 針對您應用程式可支援的巢狀結構數量並沒有特定的限制，不過，通常最好是讓您應用程式僅限使用對您所需版面配置而言實際必要的面板。 在許多情況下, <xref:System.Windows.Controls.Grid>可以使用專案來取代嵌套面板, 因為它的彈性是版面配置容器。 這可以將不必要的元素排除在樹狀結構之外，以提升應用程式中的效能。  
  
 下列範例示範如何建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]利用嵌套<xref:System.Windows.Controls.Panel>專案的, 以達成特定的版面配置。 在這個特殊情況下, <xref:System.Windows.Controls.DockPanel>專案是用來提供[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]結構<xref:System.Windows.Controls.Grid>和嵌套<xref:System.Windows.Controls.StackPanel>專案、和<xref:System.Windows.Controls.Canvas> , 用來精確地將子專案放在父系<xref:System.Windows.Controls.DockPanel>內。  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![會利用巢狀面板的 UI。](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>自訂面板元素  
 雖然[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供彈性版面配置控制項的陣列, 但也可以藉由覆<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>寫和<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法來達成自訂配置行為。 藉由在這些覆寫方法內定義新的置放行為，即可達到自訂大小和位置的目的。  
  
 同樣地, 以衍生類別 ( <xref:System.Windows.Controls.Canvas>例如或<xref:System.Windows.Controls.Grid>) 為基礎的自訂版面配置行為, 可以藉<xref:System.Windows.FrameworkElement.MeasureOverride%2A>由覆寫其<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>和方法來定義。  
  
 下列標記示範如何建立自訂<xref:System.Windows.Controls.Panel>元素。 這個新<xref:System.Windows.Controls.Panel>的 (定義`PlotPanel`為) 支援透過使用硬式編碼的*x*和*y*座標來定位子項目。 在此範例中, <xref:System.Windows.Shapes.Rectangle>元素 (未顯示) 位於繪圖點 50 (*x*) 和 50 (*y*)。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 若要檢視更複雜的自訂面板實作，請參閱[建立自訂的內容換行面板範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159979)。  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>當地語系化/全球化支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援一些功能，能夠協助建立可當地語系化的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 所有面板元素原本就支援<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性, 其可用來根據使用者的地區設定或語言設定動態重新傳送內容。 如需詳細資訊，請參閱 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 屬性提供一種機制, 可讓應用程式開發人員預期當地語系化[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的需求。 <xref:System.Windows.Window.SizeToContent%2A> 使用此<xref:System.Windows.SizeToContent.WidthAndHeight>屬性的值, 父系<xref:System.Windows.Window>一律會動態調整以符合內容, 而且不會受到人工高度或寬度限制的限制。  
  
 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]和<xref:System.Windows.Controls.StackPanel>都是可當地語系化的絕佳選擇。 <xref:System.Windows.Controls.Canvas>不是理想的選擇, 因為它會將內容設為絕對, 因此難以當地語系化。  
  
 如需有關建立具有可當地語系化 [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] 之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的其他資訊，請參閱[使用自動版面配置概觀](../advanced/use-automatic-layout-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：我的第一個 WPF 傳統型應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF 版面配置庫範例](https://go.microsoft.com/fwlink/?LinkID=160054)
- [版面配置](../advanced/layout.md)
- [WPF 控制項陳列庫範例](https://go.microsoft.com/fwlink/?LinkID=160053)
- [對齊、邊界和填補概觀](../advanced/alignment-margins-and-padding-overview.md)
- [建立自訂的內容包裝面板範例](https://go.microsoft.com/fwlink/?LinkID=159979)
- [附加屬性概觀](../advanced/attached-properties-overview.md)
- [使用自動配置概觀](../advanced/use-automatic-layout-overview.md)
- [版面配置與設計](../advanced/optimizing-performance-layout-and-design.md)
