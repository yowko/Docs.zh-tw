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
ms.openlocfilehash: 7810bfbf4f5bedf51e0797a4b9017f589e0b0a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187585"
---
# <a name="panels-overview"></a>面板概觀
<xref:System.Windows.Controls.Panel>元素是控制元素呈現的元件，其大小和尺寸、位置及其子內容的排列。 提供了[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]許多預定義<xref:System.Windows.Controls.Panel>元素以及構造自訂<xref:System.Windows.Controls.Panel>元素的能力。  
  
 本主題包含下列各節。  
  
- [面板類別](#Panels_view_from_10000_feet)  
  
- [面板元素的一般成員](#Panels_declared_members)  
  
- [衍生的面板元素](#Panels_derived_elements)  
  
- [使用者介面面板](#Panels_main_UI_elements)  
  
- [巢狀面板元素](#Panels_nested_panel_elements)  
  
- [自訂面板元素](#Panels_custom_panel_elements)  
  
- [當地語系化/全球化支援](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>面板類別  
 <xref:System.Windows.Controls.Panel>是 提供 佈局支援的所有元素的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]基類。 派生<xref:System.Windows.Controls.Panel>元素用於在 和 代碼中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定位和排列元素。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含一套完整的衍生面板實作，可讓您進行許多複雜的版面配置。 這些衍生的類別會公開可促成大多數標準 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 案例的屬性和方法。 找不到滿足其需求的子排列行為的開發人員可以通過重寫<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>和<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法創建新佈局。 如需有關自訂版面配置行為的詳細資訊，請參閱[自訂面板元素](#Panels_custom_panel_elements)。  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>面板的一般成員  
 所有<xref:System.Windows.Controls.Panel>元素都支援由 定義的<xref:System.Windows.FrameworkElement>基大小調整和定位屬性，包括<xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>、、、、和<xref:System.Windows.FrameworkElement.LayoutTransform%2A>。 有關 定義的<xref:System.Windows.FrameworkElement>定位屬性的其他資訊，請參閱[對齊、邊距和填充概述](../advanced/alignment-margins-and-padding-overview.md)。  
  
 <xref:System.Windows.Controls.Panel>公開對理解和使用佈局至關重要的其他屬性。 該<xref:System.Windows.Controls.Panel.Background%2A>屬性用於使用 填充派生面板元素的邊界之間的區域<xref:System.Windows.Media.Brush>。 <xref:System.Windows.Controls.Panel.Children%2A>表示 由 的元素的<xref:System.Windows.Controls.Panel>子集合。 <xref:System.Windows.Controls.Panel.InternalChildren%2A>表示<xref:System.Windows.Controls.Panel.Children%2A>集合的內容以及資料繫結生成的成員。 兩者都由父<xref:System.Windows.Controls.UIElementCollection>級中託管的子項目組成<xref:System.Windows.Controls.Panel>。  
  
 面板還公開了一<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>個附加屬性，該屬性可用於在派生<xref:System.Windows.Controls.Panel>中實現分層順序。 具有較高<xref:System.Windows.Controls.Panel.Children%2A><xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>值的面板集合的成員顯示在值較低的<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>集合前面。 這對於允許子級共用相同座標空間的<xref:System.Windows.Controls.Canvas><xref:System.Windows.Controls.Grid>面板特別有用。  
  
 <xref:System.Windows.Controls.Panel>還定義了<xref:System.Windows.Controls.Panel.OnRender%2A>方法，該方法可用於重寫 的<xref:System.Windows.Controls.Panel>預設表示行為。  
  
#### <a name="attached-properties"></a>附加屬性  
 衍生的面板元素廣泛運用了附加屬性。 附加屬性是依賴項屬性的專用形式，沒有常規通用語言運行時 （CLR） 屬性"包裝器"。 附加屬性在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中有特製化的語法，在接下來的數個範例中將可以看到。  
  
 附加屬性的其中一個用途是要允許子元素儲存父元素實際定義之屬性的唯一值。 此功能的其中一項應用是讓子元素通知父元素它們想要如何在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中呈現，這對應用程式版面配置而言極為有用。 如需詳細資訊，請參閱[附加屬性概觀](../advanced/attached-properties-overview.md)。  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>衍生的面板元素  
 許多物件派生自<xref:System.Windows.Controls.Panel>，但並非所有物件都用作根佈局提供程式。 有六個定義的面板類<xref:System.Windows.Controls.Canvas><xref:System.Windows.Controls.DockPanel>（、、、、、<xref:System.Windows.Controls.WrapPanel>[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<xref:System.Windows.Controls.Grid><xref:System.Windows.Controls.StackPanel><xref:System.Windows.Controls.VirtualizingStackPanel>和 ）是專門為創建應用程式而設計的。  
  
 每個面板元素都會封裝自己的特殊功能，如下表所示。  
  
|元素名稱|UI 面板？|描述|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|是|定義一個區域，您可以在其中通過相對於區域的<xref:System.Windows.Controls.Canvas>座標顯式定位子項目。|  
|<xref:System.Windows.Controls.DockPanel>|是|定義一個區域，可供您在其中以子元素彼此間相對的水平或垂直方式排列子元素。|  
|<xref:System.Windows.Controls.Grid>|是|定義由資料行與資料列組成的彈性方格區域。 的<xref:System.Windows.Controls.Grid>子項目可以使用 屬性<xref:System.Windows.FrameworkElement.Margin%2A>精確定位。|  
|<xref:System.Windows.Controls.StackPanel>|是|將子元素排成單一行，以水平或垂直方式排列。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|否|處理 中的選項卡按鈕的佈局<xref:System.Windows.Controls.TabControl>。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|否|在<xref:System.Windows.Controls.ToolBar>控制項中排列內容。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|否|<xref:System.Windows.Controls.Primitives.UniformGrid>用於在具有所有相同儲存格大小的網格中排列子級。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|否|為面板提供一個可將其子集合「虛擬化」的基底類別。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|是|將內容以單行水平方向或垂直方向來排列並虛擬化。|  
|<xref:System.Windows.Controls.WrapPanel>|是|<xref:System.Windows.Controls.WrapPanel>將子項目從左向右定位為順序位置，將內容分解到包含框邊緣的下一行。 後續排序按順序從上到下或從右向左進行，具體取決於<xref:System.Windows.Controls.WrapPanel.Orientation%2A>屬性的值。|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>使用者介面面板  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]六個面板類可用於支援方案： <xref:System.Windows.Controls.Canvas>、 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.VirtualizingStackPanel>和<xref:System.Windows.Controls.WrapPanel>。 這些面板元素相當容易使用、多樣化且可延伸，足以滿足大多數應用程式的需求。  
  
 每個派生<xref:System.Windows.Controls.Panel>元素都以不同的方式處理大小調整約束。 瞭解水準或<xref:System.Windows.Controls.Panel>垂直方向的控制碼約束如何使佈局更加可預測。  
  
|**面板名稱**|**x 維度**|**y 維度**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|受內容限制|受內容限制|  
|<xref:System.Windows.Controls.DockPanel>|受限|受限|  
|<xref:System.Windows.Controls.StackPanel>（垂直方向）|受限|受內容限制|  
|<xref:System.Windows.Controls.StackPanel>（水準方向）|受內容限制|受限|  
|<xref:System.Windows.Controls.Grid>|受限|約束，但應用於行和<xref:System.Windows.GridUnitType.Auto>列的情況除外|  
|<xref:System.Windows.Controls.WrapPanel>|受內容限制|受內容限制|  
  
 如需這些元素中每個元素的詳細描述和使用方式範例，請參閱下方。  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>畫布  
 該<xref:System.Windows.Controls.Canvas>元素允許根據絕對*x 和*y*座標*定位內容。 元素的繪製位置可以是一個唯一的位置；或者，如果元素佔據相同的座標，則它們在標記中的出現順序會決定元素的繪製順序。  
  
 <xref:System.Windows.Controls.Canvas>提供任何<xref:System.Windows.Controls.Panel>最靈活的佈局支援。 高度和寬度屬性用於定義畫布的區域，其中的元素相對於父<xref:System.Windows.Controls.Canvas>區域分配絕對座標。 四個附加屬性<xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>和 允許精細控制物件放置在<xref:System.Windows.Controls.Canvas>， 允許開發人員在螢幕上精確定位和排列元素.  
  
#### <a name="cliptobounds-within-a-canvas"></a>畫布內的 ClipToBounds  
 <xref:System.Windows.Controls.Canvas>可以將子項目放置在螢幕上的任何位置，即使在超出其自身定義的<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>的座標處也是如此。 此外，<xref:System.Windows.Controls.Canvas>不受其子女規模的影響。 因此，子項目可以透支父<xref:System.Windows.Controls.Canvas>矩形的邊界矩形之外的其他元素。 的預設行為<xref:System.Windows.Controls.Canvas>是允許將子級繪製到父<xref:System.Windows.Controls.Canvas>項的邊界之外。 如果此行為不可取，則可以<xref:System.Windows.UIElement.ClipToBounds%2A>將 屬性設置為`true`。 這將導致<xref:System.Windows.Controls.Canvas>剪輯到其自己的大小。 <xref:System.Windows.Controls.Canvas>是唯一允許將子項目繪製在其邊界之外的佈局元素。  
  
 在[寬度屬性比較範例](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)中有此行為的圖例解說。  
  
#### <a name="defining-and-using-a-canvas"></a>定義和使用 Canvas  
 <xref:System.Windows.Controls.Canvas>只需使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或 代碼即可具現化 。 下面的示例演示如何使用<xref:System.Windows.Controls.Canvas>來絕對位置內容。 此程式碼會產生三個 100 像素的方形。 第一個方形為紅色，其左上角 (*x, y*) 位置是指定為 (0, 0)。 第二個方形為綠色，其左上角位置是 (100, 100)，正好是在第一個方形的右下方。 第三個方形為藍色，其左上角位置是 (50, 50)，因此包含第一個方形的右下象限，以及第二個方形的左上象限。 由於第三個方形是最後放置的，因此它會顯示在另外兩個方形上方，也就是說，重疊部分會呈現第三個方塊的顏色。  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 Canvas 項目。](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel 的比較  
 元素<xref:System.Windows.Controls.DockPanel>使用子內容<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>元素中設置的附加屬性沿容器的邊緣放置內容。 當<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>設置為<xref:System.Windows.Controls.Dock.Top>或<xref:System.Windows.Controls.Dock.Bottom>時，它將子項目分別位於或下方。 設置為<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType><xref:System.Windows.Controls.Dock.Left>或<xref:System.Windows.Controls.Dock.Right>時，它將子項目定位到彼此的左側或右側。 屬性<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>確定作為 的子項目添加的最終元素的位置<xref:System.Windows.Controls.DockPanel>。  
  
 可以使用<xref:System.Windows.Controls.DockPanel>來定位一組相關控制項，如一組按鈕。 或者，您可以使用它創建一個"平移"，類似于在[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Microsoft Outlook 中找到的"  
  
#### <a name="sizing-to-content"></a>依內容調整大小  
 如果未指定<xref:System.Windows.FrameworkElement.Height%2A>其<xref:System.Windows.FrameworkElement.Width%2A>和屬性，則<xref:System.Windows.Controls.DockPanel>對其內容的大小。 大小可以因應其子元素的大小來增加或縮減。 但是，當指定這些屬性並且不再具有下一個指定子項目的空間時，<xref:System.Windows.Controls.DockPanel>不會顯示該子項目或後續子項目，並且不測量後續子項目。  
  
#### <a name="lastchildfill"></a>LastChildFill  
 預設情況下，元素的最後一個<xref:System.Windows.Controls.DockPanel>子級將"填充"剩餘的未配置空間。 如果不需要此行為，則將<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>屬性設置為`false`。  
  
#### <a name="defining-and-using-a-dockpanel"></a>定義和使用 DockPanel  
 下面的示例演示如何使用 分區空間<xref:System.Windows.Controls.DockPanel>。 五<xref:System.Windows.Controls.Border>個元素作為父<xref:System.Windows.Controls.DockPanel>元素的子項目添加。 每個都使用不同的定位屬性<xref:System.Windows.Controls.DockPanel>來分區空間。 最後的元素會「填滿」剩餘的未配置空間。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 DockPanel 案例。](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>方格  
 該<xref:System.Windows.Controls.Grid>元素合併了絕對位置和表格資料控制的功能。 A<xref:System.Windows.Controls.Grid>使您能夠輕鬆定位和樣式元素。 <xref:System.Windows.Controls.Grid>允許您定義靈活的行和列分組，甚至提供在多個<xref:System.Windows.Controls.Grid>元素之間共用大小調整資訊的機制。  
  
#### <a name="how-is-grid-different-from-table"></a>Grid 和 Table 有何不同？  
 <xref:System.Windows.Documents.Table>並<xref:System.Windows.Controls.Grid>共用一些通用功能，但每個功能最適合不同的方案。 A<xref:System.Windows.Documents.Table>設計用於流內容中（有關流內容的詳細資訊，請參閱[流文檔概述](../advanced/flow-document-overview.md)）。 方格最適合在表單內部使用 (基本上，是在非固定格式內容以外的任何地方)。 在<xref:System.Windows.Documents.FlowDocument>中<xref:System.Windows.Documents.Table>，支援流內容行為，如分頁、列重流和內容選擇，而<xref:System.Windows.Controls.Grid>不支援。 另<xref:System.Windows.Controls.Grid>一方面，由於許多原因，包括<xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Controls.Grid>添加基於行和列索引的元素，<xref:System.Windows.Documents.Table>最好在 外部使用。 該<xref:System.Windows.Controls.Grid>元素允許分層子內容，允許多個元素存在於單個"儲存格"中。 <xref:System.Windows.Documents.Table>不支援分層。 子<xref:System.Windows.Controls.Grid>元素的子項目可以相對於其"儲存格"邊界區域絕對位置。 <xref:System.Windows.Documents.Table>不支援此功能。 最後，比<xref:System.Windows.Controls.Grid>的重量輕。 <xref:System.Windows.Documents.Table>  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>資料行和資料列的調整大小行為  
 在 中定義的列和<xref:System.Windows.Controls.Grid>行可以利用<xref:System.Windows.GridUnitType.Star>大小調整，以便按比例分配剩餘空間。 當<xref:System.Windows.GridUnitType.Star>選擇為行或列的高度或寬度時，該列或行將接收剩餘可用空間的加權比例。 這與 相反<xref:System.Windows.GridUnitType.Auto>，後者將根據列或行中的內容大小均勻分佈空間。 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 時，這個值是以 `*` 或 `2*` 表示。 在第一個案例中，資料列或資料行會獲得一倍的可用空間，在第二個案例中，則會獲得兩倍的可用空間，依此類推。 通過將此技術與 和<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A><xref:System.Windows.FrameworkElement.VerticalAlignment%2A>值`Stretch`按比例分配空間，可以按螢幕空間的百分比對佈局空間進行分區。 <xref:System.Windows.Controls.Grid>是唯一可以以這種方式分配空間的佈局面板。  
  
#### <a name="defining-and-using-a-grid"></a>定義和使用 Grid  
 下面的示例演示如何構建[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]類似于 Windows 開始功能表上的"運行"對話方塊中找到的。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 Grid 項目。](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 A<xref:System.Windows.Controls.StackPanel>使您能夠在指定的方向"堆疊"元素。 預設的堆疊方向為垂直。 該<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性可用於控制內容流。  
  
#### <a name="stackpanel-vs-dockpanel"></a>堆疊面板與碼頭面板  
 雖然<xref:System.Windows.Controls.DockPanel>也可以"堆疊"子項目，<xref:System.Windows.Controls.DockPanel>並且<xref:System.Windows.Controls.StackPanel>在某些使用方案中不會產生類似的結果。 例如，子項目的順序可能會影響其在 中<xref:System.Windows.Controls.DockPanel>的大小，但不能在 中。 <xref:System.Windows.Controls.StackPanel> 這是因為<xref:System.Windows.Controls.StackPanel>在 的堆疊方向度量<xref:System.Double.PositiveInfinity>，而<xref:System.Windows.Controls.DockPanel>僅測量可用大小。  
  
 下列範例示範這項主要的差異。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 下圖顯示轉譯行為的差異。  
  
 ![螢幕擷取畫面：StackPanel 和 DockPanel 螢幕擷取畫面的比較](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>定義和使用 StackPanel  
 下面的示例演示如何使用<xref:System.Windows.Controls.StackPanel>創建一組垂直定位的按鈕。 對於水準定位，將<xref:System.Windows.Controls.StackPanel.Orientation%2A>屬性設置為<xref:System.Windows.Controls.Orientation.Horizontal>。  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 StackPanel 項目。](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]還提供了自動"虛擬化"<xref:System.Windows.Controls.StackPanel>資料繫結子內容的元素的變體。 在此內容中，「虛擬化」一字係指一種技術，藉由這種技術，將可從較大量的資料項目，根據畫面上可見的項目來產生元素子集。 當在指定的時間內畫面上只能有幾個 UI 項目時，不論是就記憶體還是處理器而言，產生大量 UI 項目都會相當耗費資源。 <xref:System.Windows.Controls.VirtualizingStackPanel>（通過<xref:System.Windows.Controls.VirtualizingPanel>提供的功能計算可見項，並與<xref:System.Windows.Controls.ItemContainerGenerator>從<xref:System.Windows.Controls.ItemsControl>（如<xref:System.Windows.Controls.ListBox>）<xref:System.Windows.Controls.ListView>到僅為可見項創建元素。  
  
 元素<xref:System.Windows.Controls.VirtualizingStackPanel>將自動設置為控制項（如 ）<xref:System.Windows.Controls.ListBox>的項主機。 託管資料繫結集合時，只要內容在 的邊界內，內容就會自動虛擬化<xref:System.Windows.Controls.ScrollViewer>。 當裝載許多子項目時，這可大幅改善效能。  
  
 以下標記演示如何將 用作<xref:System.Windows.Controls.VirtualizingStackPanel>專案主機。 必須<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>將附加屬性設置為`true`（預設）才能進行虛擬化。  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>用於將子項目從左至右定位在順序位置，當它到達其父容器的邊緣時，將內容分解到下一行。 內容的方向可以是水平或垂直方向。 <xref:System.Windows.Controls.WrapPanel>對於簡單的流動[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]方案很有用。 它也可用來在其所有子元素套用統一的大小。  
  
 下面的示例演示如何創建<xref:System.Windows.Controls.WrapPanel>以顯示<xref:System.Windows.Controls.Button>在到達容器邊緣時換行的控制項。  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![典型的 WrapPanel 項目。](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>巢狀面板元素  
 <xref:System.Windows.Controls.Panel>元素可以嵌套在彼此中，以便生成複雜的佈局。 這可以證明非常有用的情況下，一個是<xref:System.Windows.Controls.Panel>理想的部分[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，但可能不能滿足不同部分的需要。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
 針對您應用程式可支援的巢狀結構數量並沒有特定的限制，不過，通常最好是讓您應用程式僅限使用對您所需版面配置而言實際必要的面板。 在許多情況下，<xref:System.Windows.Controls.Grid>元素作為佈局容器的靈活性，可以使用元素而不是嵌套面板。 這可以將不必要的元素排除在樹狀結構之外，以提升應用程式中的效能。  
  
 下面的示例演示如何創建[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]利用嵌套<xref:System.Windows.Controls.Panel>元素來實現特定佈局的 。 在此<xref:System.Windows.Controls.DockPanel>特定情況下，元素用於提供[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]結構，嵌套<xref:System.Windows.Controls.StackPanel>元素 、a<xref:System.Windows.Controls.Grid>和 a<xref:System.Windows.Controls.Canvas>用於精確地將子項目放置在父<xref:System.Windows.Controls.DockPanel>元素 中。  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 編譯後的應用程式會產生一個看起來如下的新 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 ![會利用巢狀面板的 UI。](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>自訂面板元素  
 雖然[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了一系列靈活的佈局控制項，但自訂佈局行為也可以通過重寫<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>和<xref:System.Windows.FrameworkElement.MeasureOverride%2A>方法來實現。 藉由在這些覆寫方法內定義新的置放行為，即可達到自訂大小和位置的目的。  
  
 同樣，<xref:System.Windows.Controls.Canvas>基於派生類（如 或<xref:System.Windows.Controls.Grid>）的自訂佈局行為可以通過重寫其<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>和方法<xref:System.Windows.FrameworkElement.MeasureOverride%2A>來定義。  
  
 下面的標記演示如何創建自訂<xref:System.Windows.Controls.Panel>元素。 這種定義為<xref:System.Windows.Controls.Panel>的新，`PlotPanel`支援使用硬編碼*的x和**y*座標定位子項目。 在此示例中，<xref:System.Windows.Shapes.Rectangle>元素（未顯示）位於繪圖點 50 *（x*） 和 50 *（y*） 處。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 若要檢視更複雜的自訂面板實作，請參閱[建立自訂的內容換行面板範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159979)。  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>當地語系化/全球化支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援一些功能，能夠協助建立可當地語系化的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 所有面板元素都本機支援該<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性，該屬性可用於根據使用者的地區設定或語言設置動態重新流內容。 如需詳細資訊，請參閱 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 該<xref:System.Windows.Window.SizeToContent%2A>屬性提供了一種機制，使應用程式開發人員能夠預測當地語系化[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的需求。 使用此屬性<xref:System.Windows.SizeToContent.WidthAndHeight>的值，父級<xref:System.Windows.Window>始終動態調整大小以適合內容，並且不受人工高度或寬度限制的限制。  
  
 <xref:System.Windows.Controls.DockPanel>，<xref:System.Windows.Controls.Grid>並且<xref:System.Windows.Controls.StackPanel>都是可[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]當地語系化的好選擇。 <xref:System.Windows.Controls.Canvas>然而，這不是一個不錯的選擇，因為它絕對位置內容，使得當地語系化變得困難。  
  
 有關使用可當地語系化使用者介面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]（UI） 創建應用程式的其他資訊，請參閱[使用自動佈局概述](../advanced/use-automatic-layout-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF 版面配置庫範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=160054)
- [版面配置](../advanced/layout.md)
- [WPF 控制項陳列庫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [對齊、邊界和填補概觀](../advanced/alignment-margins-and-padding-overview.md)
- [建立自訂的內容換行面板範例 (英文)](https://go.microsoft.com/fwlink/?LinkID=159979)
- [附加屬性概觀](../advanced/attached-properties-overview.md)
- [使用自動配置概觀](../advanced/use-automatic-layout-overview.md)
- [版面配置與設計](../advanced/optimizing-performance-layout-and-design.md)
