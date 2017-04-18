---
title: "面板概觀 | Microsoft Docs"
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
  - "控制項, 面板"
  - "Panel 控制項 [WPF], 關於 Panel 控制項"
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
caps.latest.revision: 48
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 45
---
# 面板概觀
<xref:System.Windows.Controls.Panel> 項目是可控制項目呈現方式的元件 \- 即項目的大小與維度、位置及其子內容的排列。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了多項預先定義的 <xref:System.Windows.Controls.Panel> 項目及用以建構自訂 <xref:System.Windows.Controls.Panel> 項目的功能。  
  
 本主題包含下列章節。  
  
-   [面板類別](#Panels_view_from_10000_feet)  
  
-   [面板項目的一般成員](#Panels_declared_members)  
  
-   [衍生面板項目](#Panels_derived_elements)  
  
-   [使用者介面面板](#Panels_main_UI_elements)  
  
-   [巢狀面板項目](#Panels_nested_panel_elements)  
  
-   [自訂面板項目](#Panels_custom_panel_elements)  
  
-   [當地語系化\/全球化支援](#Panels_global_localization)  
  
-   [相關主題](#seeAlsoToggle)  
  
<a name="Panels_view_from_10000_feet"></a>   
## 面板類別  
 <xref:System.Windows.Controls.Panel> 是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中所有支援配置之項目的基底類別 \(Base Class\)。  衍生的 <xref:System.Windows.Controls.Panel> 項目可用於定位和排列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼中的項目。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含一套完善的衍生面板實作可進行許多複雜的配置。  這些衍生類別會公開相關的屬性與方法，以運用在最標準的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 案例中。  開發人員若找不到符合其需求的子排列行為，可以覆寫 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 與 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 方法以建立新配置。  如需自訂配置行為的詳細資訊，請參閱[自訂面板項目](#Panels_custom_panel_elements)。  
  
<a name="Panels_declared_members"></a>   
## 面板的一般成員  
 所有 <xref:System.Windows.Controls.Panel> 項目都支援 <xref:System.Windows.FrameworkElement> 所定義的基底大小與定位，包括 <xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A> 與 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>。  如需 <xref:System.Windows.FrameworkElement> 所定義之定位屬性的其他資訊，請參閱[對齊、邊界和填補概觀](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)。  
  
 <xref:System.Windows.Controls.Panel> 會公開了解及使用配置時所不可或缺的其他屬性。  <xref:System.Windows.Controls.Panel.Background%2A> 屬性可用以透過 <xref:System.Windows.Media.Brush> 填滿衍生面板項目之邊界間的區域。  <xref:System.Windows.Controls.Panel.Children%2A> 表示組成 <xref:System.Windows.Controls.Panel> 的項目子集合。  <xref:System.Windows.Controls.Panel.InternalChildren%2A> 表示 <xref:System.Windows.Controls.Panel.Children%2A> 集合的內容，加上資料繫結產生的成員。  兩者都包含父 <xref:System.Windows.Controls.Panel> 內裝載之子項目的 <xref:System.Windows.Controls.UIElementCollection>。  
  
 面板也會公開 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> 附加屬性，用以達成衍生 <xref:System.Windows.Controls.Panel> 中的分層順序。  就面板 <xref:System.Windows.Controls.Panel.Children%2A> 集合的成員而言，<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> 值較高者會顯示在 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> 值較低者之前。  對於 <xref:System.Windows.Controls.Canvas> 與 <xref:System.Windows.Controls.Grid> 等允許子系共用相同座標空間的面板，這特別有用。  
  
 <xref:System.Windows.Controls.Panel> 也會定義 <xref:System.Windows.Controls.Panel.OnRender%2A> 方法，用以覆寫 <xref:System.Windows.Controls.Panel> 的預設表示行為。  
  
#### 附加屬性  
 衍生面板項目可廣泛運用[附加屬性](GTMT)。  附加屬性是一種特殊形式的[相依性屬性](GTMT)，這種屬性沒有傳統的 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性「包裝函式」。  附加屬性具有[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 的特殊語法，可見於下列數個範例中。  
  
 附加屬性的其中一個用途，就是讓子項目能夠儲存父項目實際定義之屬性的唯一值。  具有此功能的應用程式可讓子項目告知父代其本身在[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中所需的呈現方式，這在進行應用程式配置時極為有用。  如需詳細資訊，請參閱 [附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
<a name="Panels_derived_elements"></a>   
## 衍生面板項目  
 許多物件都衍生自 <xref:System.Windows.Controls.Panel>，但它們並非全都可做為根配置提供者。  特別針對建立應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 而設計的已定義面板類別有六種 \(<xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Grid>、<xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.VirtualizingStackPanel> 與 <xref:System.Windows.Controls.WrapPanel>\)。  
  
 每個面板項目都封裝其本身的特殊功能，如下表所示。  
  
|項目名稱|是否為 UI 面板？|描述|  
|----------|----------------|--------|  
|<xref:System.Windows.Controls.Canvas>|是|定義一個區域，您可以在這個區域內依據相對於 <xref:System.Windows.Controls.Canvas> 區域的座標，明確定位子項目。|  
|<xref:System.Windows.Controls.DockPanel>|是|定義一個區域，您可以在這個區域內水平或垂直排列子項目 \(彼此相對\)。|  
|<xref:System.Windows.Controls.Grid>|是|定義由資料行和資料列組成的彈性方格區域。  <xref:System.Windows.Controls.Grid> 的子項目可透過 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性精確定位。|  
|<xref:System.Windows.Controls.StackPanel>|是|將子項目排列在可為水平或垂直方向的單一行中。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|否|處理 <xref:System.Windows.Controls.TabControl> 中索引標籤按鈕的配置。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|否|排列 <xref:System.Windows.Controls.ToolBar> 控制項內的內容。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|否|<xref:System.Windows.Controls.Primitives.UniformGrid> 可用以在儲存格大小皆相等的方格內排列子系。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|否|針對可「虛擬化」其子集合的面板提供基底類別。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|是|將內容排列及虛擬化在水平或垂直方向的單行。|  
|<xref:System.Windows.Controls.WrapPanel>|是|<xref:System.Windows.Controls.WrapPanel> 可將子項目從左到右依序放置，並在包含的方塊邊緣將內容中斷，換到下一行。  之後的順序則根據 <xref:System.Windows.Controls.WrapPanel.Orientation%2A> 屬性值而定，可循序由上至下或由右至左。|  
  
<a name="Panels_main_UI_elements"></a>   
## 使用者介面面板  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有六種可用的面板類別，這些類別都以最佳化的方式來支援 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例：<xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Grid>、<xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.VirtualizingStackPanel> 與 <xref:System.Windows.Controls.WrapPanel>。  這些面板項目都具有易用、多樣化與可擴充的特點，適用於大部分的應用程式。  
  
 各個衍生 <xref:System.Windows.Controls.Panel> 項目會以不同的方式處理大小條件約束。  若能了解 <xref:System.Windows.Controls.Panel> 如何處理水平或垂直方向的條件約束，將使配置更符合預期。  
  
|**面板名稱**|**x 維度**|**y 維度**|  
|--------------|--------------|--------------|  
|<xref:System.Windows.Controls.Canvas>|限制為內容|限制為內容|  
|<xref:System.Windows.Controls.DockPanel>|受限制|受限制|  
|<xref:System.Windows.Controls.StackPanel> \(垂直方向\)|受限制|限制為內容|  
|<xref:System.Windows.Controls.StackPanel> \(水平方向\)|限制為內容|受限制|  
|<xref:System.Windows.Controls.Grid>|受限制|受限制，但在 <xref:System.Windows.GridUnitType> 套用至資料列與資料行時例外|  
|<xref:System.Windows.Controls.WrapPanel>|限制為內容|限制為內容|  
  
 本文稍後將提供這些項目的詳細說明與使用方式範例。  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### Canvas  
 <xref:System.Windows.Controls.Canvas> 項目可讓內容根據 *x* 與 *y* 的絕對座標進行定位。  項目可在唯一的位置上繪製，若項目位於相同的座標上，則其顯示於標記中的順序將決定其繪製順序。  
  
 <xref:System.Windows.Controls.Canvas> 可為任何 <xref:System.Windows.Controls.Panel> 提供最富彈性的配置支援。  高度與寬度屬性可用以定義畫布區域，而畫布內的項目會被指定相對於父 <xref:System.Windows.Controls.Canvas> 區域的絕對座標。  <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=fullName>、<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=fullName>、<xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=fullName> 與 <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=fullName> 這四個附加屬性，可讓開發人員妥善控制 <xref:System.Windows.Controls.Canvas> 內的物件放置，進而精確地定位及排列畫面上的項目。  
  
#### 畫布內的 ClipToBounds  
 <xref:System.Windows.Controls.Canvas> 可將子項目放在畫面上的任意位置，即使在其本身定義的 <xref:System.Windows.FrameworkElement.Height%2A> 與 <xref:System.Windows.FrameworkElement.Width%2A> 以外的座標上也是如此。  此外，<xref:System.Windows.Controls.Canvas> 並不會受其子系的大小影響。  因此，子項目有可能會在父 <xref:System.Windows.Controls.Canvas> 的週框 \(bounding rectangle\) 以外繪製其他項目。  <xref:System.Windows.Controls.Canvas> 的預設行為就是讓子系能在父 <xref:System.Windows.Controls.Canvas> 的邊界之外繪製。  若不使用此行為，可將 <xref:System.Windows.UIElement.ClipToBounds%2A> 屬性設為 `true`。  這樣會使 <xref:System.Windows.Controls.Canvas> 裁剪成自己的大小。  <xref:System.Windows.Controls.Canvas> 是唯一允許在其邊界之外繪製子系的配置項目。  
  
 此行為會在[寬度屬性比較範例](http://go.microsoft.com/fwlink/?LinkID=160050) \(英文\) 中以圖形方式說明。  
  
#### 定義和使用畫布  
 <xref:System.Windows.Controls.Canvas> 只要透過[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 或程式碼即可具現化 \(Instantiated\)。  下列範例會示範如何使用 <xref:System.Windows.Controls.Canvas> 以絕對的方式定位內容。  此程式碼會產生三個 100 像素的方形。  第一個方形為紅色，其左上角 \(*x, y*\) 位置指定為 \(0, 0\)。  第二個方形為綠色，其左上角位置 \(100, 100\) 正好位於第一個方形的右下角。  第三個方形為藍色，其左上角位置為 \(50, 50\)，因此會涵蓋第一個方形的右下角四分之一，以及第二個方形的左上角四分之一。  因為第三個方形最後才放置，所以會顯示在另外兩個方形上面，也就是說，重疊的部分會呈現第三個方塊的色彩。  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 完成編譯的應用程式會產生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如下所示。  
  
 ![典型的 Canvas 項目。](../../../../docs/framework/wpf/controls/media/panel-intro-canvas.png "panel\_intro\_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### DockPanel  
 <xref:System.Windows.Controls.DockPanel> 項目會使用子內容項目中設定的 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 附加屬性，沿著容器邊緣定位內容。  當 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 設為 <xref:System.Windows.Controls.Dock> 或 <xref:System.Windows.Controls.Dock> 時，它會讓子項目彼此上下放置。  當 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 設為 <xref:System.Windows.Controls.Dock> 或 <xref:System.Windows.Controls.Dock> 時，它會讓子項目彼此左右放置。  <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> 屬性可決定最後加入為 <xref:System.Windows.Controls.DockPanel> 之子系的項目位置。  
  
 您可以使用 <xref:System.Windows.Controls.DockPanel> 來放置一組相關的控制項，例如一組按鈕。  或者，也可以使用它來建立「附有窗格的」[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，類似於 [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)] 中的功能。  
  
#### 隨內容調整大小  
 若未指定其 <xref:System.Windows.FrameworkElement.Height%2A> 與 <xref:System.Windows.FrameworkElement.Width%2A> 屬性，<xref:System.Windows.Controls.DockPanel> 即會調整為其內容的大小。  大小會增加或減少，以容納其子項目的大小。  但是，若已指定這些屬性，並且已沒有空間可供下一個指定的子項目使用，<xref:System.Windows.Controls.DockPanel> 則不會顯示該子項目或後續的子項目，也不會測量後續的子項目。  
  
#### LastChildFill  
 根據預設，<xref:System.Windows.Controls.DockPanel> 項目的最後一個子系會「填滿」未配置的剩餘空間。  若不使用此行為，請將 <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> 屬性設為 `false`。  
  
#### 定義和使用 DockPanel  
 下列範例會示範如何使用 <xref:System.Windows.Controls.DockPanel> 來分割空間。  有五個 <xref:System.Windows.Controls.Border> 項目會加入成為 <xref:System.Windows.Controls.DockPanel> 的子系。  每個項目會使用 <xref:System.Windows.Controls.DockPanel> 的不同定位屬性進行空間分割。  最後一個項目會「填滿」未配置的剩餘空間。  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 完成編譯的應用程式會產生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如下所示。  
  
 ![典型的 DockPanel 案例。](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.png "panel\_intro\_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### Grid  
 <xref:System.Windows.Controls.Grid> 項目合併了絕對定位與表格式資料控制的功能。  <xref:System.Windows.Controls.Grid> 可讓您輕鬆設定項目的位置和樣式。  <xref:System.Windows.Controls.Grid> 可讓您定義富彈性的資料列與資料行群組，甚至提供在多個 <xref:System.Windows.Controls.Grid> 項目間共用大小資訊的機制。  
  
#### 方格和資料表有何不同？  
 <xref:System.Windows.Documents.Table> 與 <xref:System.Windows.Controls.Grid> 會共用某些通用功能，但兩者分別適用於不同的情況。  <xref:System.Windows.Documents.Table> 的設計適合在非固定格式內容中使用 \(如需非固定格式內容的詳細資訊，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)\)。  方格則適用於表單內 \(基本上，只要是非固定格式內容都適用\)。  在 <xref:System.Windows.Documents.FlowDocument> 內，<xref:System.Windows.Documents.Table> 支援分頁、資料行重新排列與內容選取等非固定格式內容行為，而 <xref:System.Windows.Controls.Grid> 則否。  另一方面，<xref:System.Windows.Controls.Grid> 適用於 <xref:System.Windows.Documents.FlowDocument> 以外的地方，其原因眾多，包括 <xref:System.Windows.Controls.Grid> 會根據資料列與資料行索引加入項目，<xref:System.Windows.Documents.Table> 則否。  <xref:System.Windows.Controls.Grid> 項目可允許將子內容分層，所以單一「儲存格」中可以有多個項目。<xref:System.Windows.Documents.Table> 不支援分層。  <xref:System.Windows.Controls.Grid> 的子項目可放在相對於其「儲存格」界限區域的絕對位置。  但 <xref:System.Windows.Documents.Table> 不支援此功能。  最後，<xref:System.Windows.Controls.Grid> 的粗細小於 <xref:System.Windows.Documents.Table>。  
  
#### 資料行與資料列的縮放行為  
 定義在 <xref:System.Windows.Controls.Grid> 中的資料行和資料列可利用 <xref:System.Windows.GridUnitType> 縮放，按照比例分配剩餘空間。  選取 <xref:System.Windows.GridUnitType> 做為資料列或資料行的高度或寬度時，該資料行或資料列會接收加權比例的剩餘可用空間。  這種情形與 <xref:System.Windows.GridUnitType> 相反，其會根據資料行或資料列中的內容大小來平均分配空間。  使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 時，此值會以 `*` 或 `2*` 表示。  如為前者，資料列或資料行會獲得一倍的可用空間，如為後者，則會獲得兩倍的可用空間，依此類推。  若將這個依比例散發空間的技術與 `Stretch` 的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 值相結合，則可依螢幕空間的百分比來分割配置空間。  <xref:System.Windows.Controls.Grid> 是唯一可以用這種方式分配空間的配置面板。  
  
#### 定義和使用方格  
 下列範例會示範如何建置類似於 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] \[開始\] 功能表的 \[執行\] 對話方塊上的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 完成編譯的應用程式會產生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如下所示。  
  
 ![典型的 Grid 項目。](../../../../docs/framework/wpf/controls/media/avalon-run-dialog.png "avalon\_run\_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### StackPanel  
 <xref:System.Windows.Controls.StackPanel> 可讓您以指定的方向「堆疊」項目。  預設的堆疊方向為垂直。  <xref:System.Windows.Controls.StackPanel.Orientation%2A> 屬性可用以控制內容方向。  
  
#### 比較 StackPanel 與DockPanel  
 雖然 <xref:System.Windows.Controls.DockPanel> 也會「堆疊」子項目，但 <xref:System.Windows.Controls.DockPanel> 與 <xref:System.Windows.Controls.StackPanel> 在某些使用案例中不會產生類似的結果。  例如，子項目的順序會影響它們在 <xref:System.Windows.Controls.DockPanel> 中的大小，但在 <xref:System.Windows.Controls.StackPanel> 中則沒有影響。  這是因為 <xref:System.Windows.Controls.StackPanel> 會測量於 <xref:System.Double.PositiveInfinity> 堆疊的方向，但是 <xref:System.Windows.Controls.DockPanel> 只會測量可用的大小。  
  
 下列範例說明此主要差異。  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 下圖顯示呈現行為的差異。  
  
 ![螢幕擷取畫面：StackPanel 與DockPanel 螢幕擷取畫面的比較](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.png "layout\_smiley\_stackpanel")  
  
#### 定義和使用 StackPanel  
 下列範例會示範如何使用 <xref:System.Windows.Controls.StackPanel> 建立一組垂直放置的按鈕。  至於水平放置，請將 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 屬性設為 <xref:System.Windows.Controls.Orientation>。  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 完成編譯的應用程式會產生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如下所示。  
  
 ![典型的 StackPanel 項目。](../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.png "panel\_intro\_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也提供另一種 <xref:System.Windows.Controls.StackPanel> 項目，這種項目會自動「虛擬化」資料繫結子內容。  在此情況下，「虛擬化」一詞是指一種技術，這種技術可以依據畫面上所顯示的項目，從眾多資料項目當中產生項目的子集。  在指定時間畫面上只會出現少數項目時，產生大量 UI 項目會耗用許多記憶體和處理器資源。  <xref:System.Windows.Controls.VirtualizingStackPanel> 會 \(透過 <xref:System.Windows.Controls.VirtualizingPanel> 所提供的功能\) 計算可見項目 \(Item\)，並從 <xref:System.Windows.Controls.ItemsControl> \(例如 <xref:System.Windows.Controls.ListBox> 或 <xref:System.Windows.Controls.ListView>\) 搭配 <xref:System.Windows.Controls.ItemContainerGenerator> 使用，只為可見項目 \(Item\) 建立項目 \(Element\)。  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel> 項目會自動設為 <xref:System.Windows.Controls.ListBox> 等控制項的主項目。  裝載資料繫結集合時，內容只要位於 <xref:System.Windows.Controls.ScrollViewer> 的邊界內，就會自動進行虛擬化。  如此可在裝載許多子項目時大幅提升效能。  
  
 下列標記示範如何將 <xref:System.Windows.Controls.VirtualizingStackPanel> 做為主項目。  <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> [附加屬性](GTMT)必須設為 `true` \(預設值\)，才能進行虛擬化。  
  
 [!code-xml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> 可用以將子項目從左到右依序放置，並在內容到達父容器的邊緣時將其換到下一行。  內容的方向可以是水平或垂直。  <xref:System.Windows.Controls.WrapPanel> 對於簡單的流動[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 情況來說十分實用。  也可用以對其所有子項目套用統一的大小。  
  
 下列範例會示範如何建立 <xref:System.Windows.Controls.WrapPanel>，以顯示會在到達其容器邊緣時換行的 <xref:System.Windows.Controls.Button> 控制項。  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 完成編譯的應用程式會產生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如下所示。  
  
 ![典型的 WrapPanel 項目。](../../../../docs/framework/wpf/controls/media/wrappanel-element.png "WrapPanel\_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## 巢狀面板項目  
 <xref:System.Windows.Controls.Panel> 項目可彼此以巢狀方式放置，以產生複雜的配置。  若有個 <xref:System.Windows.Controls.Panel> 非常適用於部分 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，但不符合 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 其他部分的需求，這種配置方式會很實用。  
  
 應用程式可支援的巢狀數量並沒有實際限制，但一般而言，最好將應用程式限定為僅使用您所需配置真正需要的面板。  在許多情況下，可以使用 <xref:System.Windows.Controls.Grid> 項目來取代巢狀面板，因為該項目具有可做為配置容器的彈性。  如此可將非必要的項目排除在樹狀結構外，而提升應用程式的效能。  
  
 下列範例會示範如何建立透過 <xref:System.Windows.Controls.Panel> 項目完成特定配置的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  在此特殊情況下，<xref:System.Windows.Controls.DockPanel> 項目用於提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 結構，而 <xref:System.Windows.Controls.StackPanel> 項目、<xref:System.Windows.Controls.Grid> 與 <xref:System.Windows.Controls.Canvas> 則用於將子項目精確地放置在父 <xref:System.Windows.Controls.DockPanel> 內。  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 完成編譯的應用程式會產生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如下所示。  
  
 ![會利用巢狀面板的 UI。](../../../../docs/framework/wpf/controls/media/nested-panels.png "nested\_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## 自訂面板項目  
 雖然 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了許多富有彈性的配置控制項，但您也可以覆寫 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 與 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 方法，以進行自訂配置行為。  自訂縮放與定位可藉由在覆寫方法內定義新的定位行為完成。  
  
 同樣地，您也可以覆寫 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 與 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 方法，而根據衍生類別 \(如 <xref:System.Windows.Controls.Canvas> 或 <xref:System.Windows.Controls.Grid>\) 定義自訂配置行為。  
  
 下列標記示範如何建立自訂的 <xref:System.Windows.Controls.Panel> 項目。  這項新的 <xref:System.Windows.Controls.Panel> \(定義為 `PlotPanel`\) 支援利用硬式編碼的 *x\-* 和 *y\-* 座標進行子項目的定位。  在此範例中，<xref:System.Windows.Shapes.Rectangle> 項目 \(未顯示\) 會定位於描繪點 50 \(*x*\) 與 50 \(*y*\)。  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 若要檢視更複雜的自訂面板實作，請參閱[建立自訂內容換行面板範例](http://go.microsoft.com/fwlink/?LinkID=159979) \(英文\)。  
  
<a name="Panels_global_localization"></a>   
## 當地語系化\/全球化支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援多項有助於建立可當地語系化之 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的功能。  
  
 所有面板項目原本即支援 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性，此屬性可根據使用者的地區設定或語言設定，以動態方式重新排列內容。  如需詳細資訊，請參閱 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 <xref:System.Windows.Window.SizeToContent%2A> 屬性可提供適當機制，讓應用程式開發人員能夠預測當地語系化 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的需求。  使用此屬性的 <xref:System.Windows.SizeToContent> 值時，父 <xref:System.Windows.Window> 一律會動態調整大小以符合內容，而不受人工高度或寬度的限制。  
  
 <xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Grid> 與 <xref:System.Windows.Controls.StackPanel> 都很適用於可當地語系化的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  <xref:System.Windows.Controls.Canvas> 則不是很好的選擇，因為它會以絕對的方式放置內容，而難以進行當地語系化。  
  
 如需建立含可當地語系化[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] 之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的其他資訊，請參閱[使用自動配置概觀](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)。  
  
## 請參閱  
 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)   
 [WPF 配置圖庫範例](http://go.microsoft.com/fwlink/?LinkID=160054)   
 [配置](../../../../docs/framework/wpf/advanced/layout.md)   
 [WPF 控制項圖庫範例](http://go.microsoft.com/fwlink/?LinkID=160053)   
 [對齊、邊界和填補概觀](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)   
 [建立自訂內容換行面板範例](http://go.microsoft.com/fwlink/?LinkID=159979)   
 [附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)   
 [使用自動配置概觀](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)