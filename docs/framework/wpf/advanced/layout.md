---
title: "配置 | Microsoft Docs"
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
  - "控制項 [WPF], 配置系統"
  - "配置系統 [WPF]"
  - "WPF 配置系統"
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# 配置
本主題說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 配置系統。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中建立使用者介面時，務必了解配置計算的發生方式和時機。  
  
 此主題包括下列章節：  
  
-   [項目周框方塊](#LayoutSystem_BoundingBox)  
  
-   [配置系統](#LayoutSystem_Overview)  
  
-   [測量和排列子系](#LayoutSystem_Measure_Arrange)  
  
-   [面板項目和自訂配置行為](#LayoutSystem_PanelsCustom)  
  
-   [配置效能考量](#LayoutSystem_Performance)  
  
-   [子像素呈現和配置進位](#LayoutSystem_LayoutRounding)  
  
-   [下一步](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## 項目周框方塊  
 在考慮 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的配置時，務必了解圍繞所有項目的周框方塊。  配置系統所取用的每個 <xref:System.Windows.FrameworkElement>，都可視為已放入配置中的矩形。  <xref:System.Windows.Controls.Primitives.LayoutInformation> 類別會傳回項目配置的界限或位置。  透過計算可用的螢幕空間、任何條件約束的大小、配置專用屬性 \(像是邊界與邊框距離\)，以及父 <xref:System.Windows.Controls.Panel> 項目的個別行為，即可決定該矩形的大小。  處理此資料後，配置系統即可計算特定 <xref:System.Windows.Controls.Panel> 所有子系的位置。  務必記得，父項目上定義的調整大小特性 \(例如 <xref:System.Windows.Controls.Border>\) 會影響其子系。  
  
 下圖顯示簡單的配置。  
  
 ![典型的 Grid，沒有週框方塊疊加於其上。](../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 使用下列 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，即可達成此配置。  
  
 [!code-xml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 單一 <xref:System.Windows.Controls.TextBlock> 項目會裝載於 <xref:System.Windows.Controls.Grid> 內。  而文字僅填滿第一欄的左上角，所以 <xref:System.Windows.Controls.TextBlock> 的配置空間實際上大很多。  使用 <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> 方法即可擷取任何 <xref:System.Windows.FrameworkElement> 的周框方塊。  下圖顯示 <xref:System.Windows.Controls.TextBlock> 項目的周框方塊。  
  
 ![現在可以看得到 TextBlock 的週框方塊。](../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 如黃色矩形所顯示，<xref:System.Windows.Controls.TextBlock> 項目的配置空間實際上比所顯示的空間大很多。  隨著其他項目加入至 <xref:System.Windows.Controls.Grid>，根據所加入項目的類型與大小而定，此配置可以縮減或擴大。  
  
 <xref:System.Windows.Controls.TextBlock> 的配置位置是使用 <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> 方法轉譯為 <xref:System.Windows.Shapes.Path>。  這項技術用來顯示項目的周框方塊時相當實用。  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## 配置系統  
 簡單來說，配置是一個遞迴系統，可以調整項目大小、定位項目以及繪製項目。  具體而言，配置是描述測量和排列 <xref:System.Windows.Controls.Panel> 項目之 <xref:System.Windows.Controls.Panel.Children%2A> 集合成員的程序。  配置是一項密集的程序。  <xref:System.Windows.Controls.Panel.Children%2A> 集合越大，必須計算的次數就越多。  根據擁有集合的 <xref:System.Windows.Controls.Panel> 項目所定義的配置行為而定，也有可能會讓整個程序變得更複雜。  與較複雜的 <xref:System.Windows.Controls.Panel> \(例如 <xref:System.Windows.Controls.Grid>\) 相較之下，相對簡單的 <xref:System.Windows.Controls.Panel> \(例如 <xref:System.Windows.Controls.Canvas>\) 可以產生較佳的效能。  
  
 每次子 <xref:System.Windows.UIElement> 變更它的位置時，配置系統就可能觸發新的傳遞。  因此，務必了解可以叫用配置系統的事件，因為不必要的叫用可能會導致應用程式效能變差。  以下說明叫用配置系統時發生的處理序。  
  
1.  子 <xref:System.Windows.UIElement> 開始配置處理序的第一步，是先測量它的核心屬性。  
  
2.  接著評估 <xref:System.Windows.FrameworkElement> 上定義的調整大小屬性，例如 <xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Margin%2A>。  
  
3.  然後套用 <xref:System.Windows.Controls.Panel> 專屬的邏輯，例如 <xref:System.Windows.Controls.Dock> 方向或堆疊 <xref:System.Windows.Controls.StackPanel.Orientation%2A>。  
  
4.  測量所有子系之後，排列內容。  
  
5.  在螢幕上繪製 <xref:System.Windows.Controls.Panel.Children%2A> 集合。  
  
6.  如果有其他 <xref:System.Windows.Controls.Panel.Children%2A> 加入至集合、套用 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>，或呼叫 <xref:System.Windows.UIElement.UpdateLayout%2A> 方法，則會再次叫用此處理序。  
  
 下面各節將更詳細地定義此處理序及其叫用方式。  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## 測量和排列子系  
 配置系統會針對 <xref:System.Windows.Controls.Panel.Children%2A> 集合中的每個成員完成兩項傳遞：測量傳遞和排列傳遞。  每個子 <xref:System.Windows.Controls.Panel> 會提供它自己的 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法，以便達成本身特有的配置行為。  
  
 在測量傳遞期間，會評估 <xref:System.Windows.Controls.Panel.Children%2A> 集合的每個成員。  此處理序一開始會呼叫 <xref:System.Windows.UIElement.Measure%2A> 方法。  此方法是在父 <xref:System.Windows.Controls.Panel> 項目的實作內呼叫，而且不需要明確呼叫，配置即可發生。  
  
 首先，評估 <xref:System.Windows.UIElement> 的原生大小屬性，例如 <xref:System.Windows.UIElement.Clip%2A> 和 <xref:System.Windows.UIElement.Visibility%2A>。  這樣做會產生名為 `constraintSize` 的值，該值會傳遞至 <xref:System.Windows.FrameworkElement.MeasureCore%2A>。  
  
 接著會處理 <xref:System.Windows.FrameworkElement> 上定義的架構屬性，進而影響 `constraintSize` 的值。  這些屬性一般用於描述基礎 <xref:System.Windows.UIElement> 的調整大小特性，例如其 <xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.Margin%2A> 和 <xref:System.Windows.FrameworkElement.Style%2A>。  每一個屬性都可以改變顯示項目所需的空間。  接著會呼叫 <xref:System.Windows.FrameworkElement.MeasureOverride%2A>，並且使用 `constraintSize` 做為參數。  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 的屬性，與 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 和 <xref:System.Windows.FrameworkElement.ActualWidth%2A> 的屬性之間有差異存在。  例如，<xref:System.Windows.FrameworkElement.ActualHeight%2A> 屬性是根據其他高度輸入和配置系統所計算的值。  該值是由配置系統本身根據實際呈現動作而設定，因此會稍微落在 <xref:System.Windows.FrameworkElement.Height%2A> 之類屬性 \(此類屬性是輸入變更的基礎\) 的設定值之後。  
>   
>  因為 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 是計算而來的值，所以您應該注意，配置系統的各種作業可能會對此值產生眾多或累加的回報變更。  配置系統可能正在計算子項目所需的測量空間、父項目的條件約束等。  
  
 發生於 <xref:System.Windows.FrameworkElement.MeasureCore%2A> 呼叫期間的測量傳遞，其最終目的是要讓子系決定其 <xref:System.Windows.UIElement.DesiredSize%2A>。  <xref:System.Windows.UIElement.Measure%2A> 會儲存 <xref:System.Windows.UIElement.DesiredSize%2A> 值，以供內容排列傳遞期間使用。  
  
 排列傳遞一開始會呼叫 <xref:System.Windows.UIElement.Arrange%2A> 方法。  在排列動作期間，父 <xref:System.Windows.Controls.Panel> 項目會產生可表示子系界限的矩形。  此值會傳遞至 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> 方法以供處理。  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> 方法會評估子項目的 <xref:System.Windows.UIElement.DesiredSize%2A>，以及評估可能影響項目呈現大小的其他任何邊界。  <xref:System.Windows.FrameworkElement.ArrangeCore%2A> 會產生 `arrangeSize`，它會做為參數傳遞至 <xref:System.Windows.Controls.Panel> 的 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法。  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 會產生子項目的 `finalSize`。  最後，<xref:System.Windows.FrameworkElement.ArrangeCore%2A> 方法會進行位移 \(Offset\) 屬性 \(例如邊界和排列方式\) 的最終評估，並將子項目放在其配置位置內。  子項目並不需要 \(而且經常不會\) 填滿整個配置的空間。  然後控制項會傳回至父 <xref:System.Windows.Controls.Panel>，如此配置處理序便完成。  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## 面板項目和自訂配置行為  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含衍生自 <xref:System.Windows.Controls.Panel> 的項目群組。  這些 <xref:System.Windows.Controls.Panel> 項目可啟用許多複雜的配置。  例如，使用 <xref:System.Windows.Controls.StackPanel> 項目即可輕鬆達成堆疊項目，而更複雜且自由流動的配置則可使用 <xref:System.Windows.Controls.Canvas> 達成。  
  
 下表摘要說明可用的配置 <xref:System.Windows.Controls.Panel> 項目。  
  
|面板名稱|描述|  
|----------|--------|  
|<xref:System.Windows.Controls.Canvas>|定義一個區域，您可以在這個區域內依據相對於 <xref:System.Windows.Controls.Canvas> 區域的座標，明確定位子項目。|  
|<xref:System.Windows.Controls.DockPanel>|定義一個區域，您可以在這個區域內水平或垂直排列子項目 \(彼此相對\)。|  
|<xref:System.Windows.Controls.Grid>|定義由資料行和資料列組成的彈性方格區域。|  
|<xref:System.Windows.Controls.StackPanel>|將子項目排列在可為水平或垂直方向的單一行中。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|提供 <xref:System.Windows.Controls.Panel> 項目的架構，這些項目會虛擬化其子資料集合。  這是個抽象類別。|  
|<xref:System.Windows.Controls.WrapPanel>|將子項目由左至右依序放置，在包含方塊的邊緣將內容換行。  之後的順序則根據 <xref:System.Windows.Controls.WrapPanel.Orientation%2A> 屬性值而定，可循序由上至下或由右至左。|  
  
 至於所需配置不可能使用任何預先定義之 <xref:System.Windows.Controls.Panel> 項目的應用程式，自訂的配置行為可以透過繼承自 <xref:System.Windows.Controls.Panel> 並且覆寫 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法的方式達成。  如需範例，請參閱[自訂放射狀面板範例](http://go.microsoft.com/fwlink/?LinkID=159982) \(英文\)。  
  
<a name="LayoutSystem_Performance"></a>   
## 配置效能考量  
 配置是個遞迴處理序。  <xref:System.Windows.Controls.Panel.Children%2A> 集合中的每個子項目會在每次引動配置系統時進行處理。  因此，應避免在非必要時觸發配置系統。  下列考量可協助您獲得更佳的效能。  
  
-   請注意哪一個屬性值改變會強制配置系統進行遞迴更新。  
  
     如果相依性屬性的值可能造成初始化配置系統，則應使用公用旗標加以標示。  <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> 和 <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> 會提供有用的線索，告訴您哪一個屬性值變更將強制配制系統進行遞迴更新。  一般而言，應該將任何會影響項目周框方塊大小之屬性的 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> 旗標設定為 true。  如需詳細資訊，請參閱 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
-   盡可能使用 <xref:System.Windows.UIElement.RenderTransform%2A>，不要使用 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>。  
  
     <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 可以成為影響[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 內容的有用方法。  不過，如果轉換的效果不需影響其他項目的位置，最好是改用 <xref:System.Windows.UIElement.RenderTransform%2A>，因為 <xref:System.Windows.UIElement.RenderTransform%2A> 不會叫用配置系統。  <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 會套用其轉換並強制執行遞迴配置更新，這麼做是考慮到受影響項目的新位置。  
  
-   避免不必要的 <xref:System.Windows.UIElement.UpdateLayout%2A> 呼叫。  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> 方法會強制執行遞迴配置更新，但經常是不必要的。  除非您確定需要進行完全更新，否則就讓配置系統為您呼叫此方法。  
  
-   處理大型 <xref:System.Windows.Controls.Panel.Children%2A> 集合時，請考慮使用 <xref:System.Windows.Controls.VirtualizingStackPanel>，而不要使用一般的 <xref:System.Windows.Controls.StackPanel>。  
  
     透過虛擬化子集合，<xref:System.Windows.Controls.VirtualizingStackPanel> 只會在記憶體中保存目前在父代 [ViewPort](GTMT) 內的物件。  因此，在大部分情況下都能大幅改善效能。  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## 子像素呈現和配置進位  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形系統使用與裝置無關的單位以獲得解析度和裝置的獨立性。  每個與裝置無關的像素都會隨系統的 [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] 設定自動縮放。  這可以讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式在不同的 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 設定下適當縮放，使應用程式自動成為 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 感知。  
  
 不過，這個與 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 無關的特性可能由於消除鋸齒而建立不規則的邊緣呈現。  這些疊影通常為模糊或半透明邊緣，當邊緣的位置落在裝置像素中 \(而非裝置像素之間\) 時，就可能出現。  配置系統提供了使用配置進位調整這種情況的方式。  配置進位是配置系統在配置傳遞時，四捨五入任何非整數的像素值的功能。  
  
 配置進位預設為停用狀態。  若要啟用配置進位，請將任何 <xref:System.Windows.FrameworkElement> 上的 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> 屬性設定為 `true`。  由於它是相依性屬性，因此值會填充至視覺化樹狀結構中的所有子系。  若要啟用整個 UI 的配置進位，請在根容器上將 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> 設定為 `true`。  如需範例，請參閱 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>。  
  
<a name="LayoutSystem_whatsnext"></a>   
## 下一步  
 了解項目的測量和排列方式，就是了解配置的第一步。  如需可用 <xref:System.Windows.Controls.Panel> 項目的詳細資訊，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。  若要進一步了解各種會影響配置的定位屬性，請參閱[對齊、邊界和填補概觀](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)。  如需自訂 <xref:System.Windows.Controls.Panel> 項目的範例，請參閱[自訂放射狀面板範例](http://go.microsoft.com/fwlink/?LinkID=159982) \(英文\)。  若您已準備好在輕量 \(Light\-Weight\) 應用程式中親自體驗，請參閱[逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.UIElement>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [對齊、邊界和填補概觀](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)