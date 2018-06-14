---
title: 配置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 00c2b2bcb58e60c1a60d2d360f25089c079c0704
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549486"
---
# <a name="layout"></a>配置
本主題描述 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 配置系統。 了解如何和何時進行版面配置計算對於在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中建立使用者介面十分重要。  
  
 此主題包括下列章節：  
  
-   [項目週框方塊](#LayoutSystem_BoundingBox)  
  
-   [配置系統](#LayoutSystem_Overview)  
  
-   [測量和排列子系](#LayoutSystem_Measure_Arrange)  
  
-   [面板項目和自訂版面配置行為](#LayoutSystem_PanelsCustom)  
  
-   [版面配置效能考量](#LayoutSystem_Performance)  
  
-   [子像素轉譯和版面配置進位](#LayoutSystem_LayoutRounding)  
  
-   [後續步驟](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>項目週框方塊  
 考慮到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的版面配置時，請務必了解包圍所有項目的週框方塊。 每個<xref:System.Windows.FrameworkElement>耗用的版面配置系統可以視為螺絲到配置的矩形。 <xref:System.Windows.Controls.Primitives.LayoutInformation>類別會傳回項目的版面配置或位置的界限。 矩形的大小取決於可用的螢幕空間、 的任何條件約束、 版面配置特定屬性 （例如邊界和邊框距離），以及個別的父行為大小計算<xref:System.Windows.Controls.Panel>項目。 處理此資料時，版面配置系統是無法計算出的所有子系的特定位置<xref:System.Windows.Controls.Panel>。 務必記得，縮放特性定義父項目上這類<xref:System.Windows.Controls.Border>，會影響其子系。  
  
 下圖顯示簡單的版面配置。  
  
 ![典型的格線，沒有週框方塊疊加於其上。](../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 使用下列 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 可達成這個版面配置。  
  
 [!code-xaml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 單一<xref:System.Windows.Controls.TextBlock>項目裝載於<xref:System.Windows.Controls.Grid>。 當文字填滿只左上角的第一個資料行之已配置空間<xref:System.Windows.Controls.TextBlock>實際上太大。 週框方塊的任何<xref:System.Windows.FrameworkElement>可以擷取使用<xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>方法。 下圖顯示週框方塊<xref:System.Windows.Controls.TextBlock>項目。  
  
 ![現在可以看得到 TextBlock 的週框方塊。](../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 黃色的矩形中，已配置空間所示<xref:System.Windows.Controls.TextBlock>項目會比實際更大。 當其他項目加入至<xref:System.Windows.Controls.Grid>，此配置無法壓縮或展開時，根據類型和大小加入的項目。  
  
 配置位置的<xref:System.Windows.Controls.TextBlock>轉譯成<xref:System.Windows.Shapes.Path>使用<xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>方法。 這種方式可用於顯示項目的週框方塊。  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>配置系統  
 簡單來說，版面配置是可調整項目大小、定位項目並在螢幕上繪製項目的遞迴系統。 配置更具體來說，描述的程序的測量和排列的成員<xref:System.Windows.Controls.Panel>項目的<xref:System.Windows.Controls.Panel.Children%2A>集合。 版面配置是需要大量處理的程序。 較大<xref:System.Windows.Controls.Panel.Children%2A>集合，必須進行的計算數目愈大。 複雜性也會造成根據所定義的配置行為<xref:System.Windows.Controls.Panel>擁有集合的項目。 相當簡單<xref:System.Windows.Controls.Panel>，例如<xref:System.Windows.Controls.Canvas>，可以有更複雜效能明顯優於<xref:System.Windows.Controls.Panel>，例如<xref:System.Windows.Controls.Grid>。  
  
 每次的子系<xref:System.Windows.UIElement>變更它的位置，就有可能會觸發新的行程由配置系統。 因此，請務必了解可叫用配置系統的事件，因為不必要的叫用可能會導致不良的應用程式效能。 下列描述在叫用配置系統時所發生的程序。  
  
1.  子系<xref:System.Windows.UIElement>開始版面配置處理序的第一個具有測量其核心屬性。  
  
2.  調整大小屬性上定義<xref:System.Windows.FrameworkElement>會經過評估，例如<xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.Margin%2A>。  
  
3.  <xref:System.Windows.Controls.Panel>-套用的特定邏輯，例如<xref:System.Windows.Controls.Dock>方向或堆疊<xref:System.Windows.Controls.StackPanel.Orientation%2A>。  
  
4.  測量所有子系之後，會排列內容。  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A>集合在螢幕上繪製。  
  
6.  處理程序再次叫用時如果其他<xref:System.Windows.Controls.Panel.Children%2A>加入至集合，<xref:System.Windows.FrameworkElement.LayoutTransform%2A>套用，或<xref:System.Windows.UIElement.UpdateLayout%2A>方法呼叫。  
  
 下列各節會詳述定義此程序和其叫用方式。  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>測量和排列子系  
 版面配置系統的每個成員完成兩種途徑<xref:System.Windows.Controls.Panel.Children%2A>集合、 測量行程和排列傳遞。 每個子系<xref:System.Windows.Controls.Panel>提供它自己<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法來達成特定配置行為。  
  
 每個成員的測量傳遞期間<xref:System.Windows.Controls.Panel.Children%2A>集合進行評估。 程序一開始呼叫<xref:System.Windows.UIElement.Measure%2A>方法。 父代的實作中呼叫這個方法<xref:System.Windows.Controls.Panel>項目，而且沒有明確呼叫發生配置。  
  
 首先，原生大小屬性<xref:System.Windows.UIElement>會經過評估，例如<xref:System.Windows.UIElement.Clip%2A>和<xref:System.Windows.UIElement.Visibility%2A>。 這會產生名為的值`constraintSize`傳遞至<xref:System.Windows.FrameworkElement.MeasureCore%2A>。  
  
 架構屬性上定義的第二，<xref:System.Windows.FrameworkElement>處理，這會影響值`constraintSize`。 這些屬性通常會描述基礎的調整大小特性<xref:System.Windows.UIElement>，例如其<xref:System.Windows.FrameworkElement.Height%2A>， <xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Margin%2A>，和<xref:System.Windows.FrameworkElement.Style%2A>。 所有這些屬性都可以變更顯示項目所需的空間。 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 然後呼叫`constraintSize`做為參數。  
  
> [!NOTE]
>  屬性之間的差異<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.ActualHeight%2A>和<xref:System.Windows.FrameworkElement.ActualWidth%2A>。 例如，<xref:System.Windows.FrameworkElement.ActualHeight%2A>屬性是根據其他高度輸入和版面配置系統的導出的值。 值，由配置系統本身，根據實際呈現階段，並可能因此落後稍微設定值的屬性，例如<xref:System.Windows.FrameworkElement.Height%2A>，所輸入變更的基礎。  
>   
>  因為<xref:System.Windows.FrameworkElement.ActualHeight%2A>是計算的值，您應該注意可能有多個，或累加式報告，來變更各種作業的結果由配置系統。 配置系統可能會計算子項目所需的測量空間、父項目的條件約束，依此類推。  
  
 測量行程的最終目標為的子系，以判斷其<xref:System.Windows.UIElement.DesiredSize%2A>，期間發生<xref:System.Windows.FrameworkElement.MeasureCore%2A>呼叫。 <xref:System.Windows.UIElement.DesiredSize%2A>以儲存值<xref:System.Windows.UIElement.Measure%2A>供內容的排列傳遞期間使用。  
  
 排列傳遞開始呼叫<xref:System.Windows.UIElement.Arrange%2A>方法。 排列傳遞，而父期間<xref:System.Windows.Controls.Panel>項目會產生代表子系界限的矩形。 這個值會傳遞至<xref:System.Windows.FrameworkElement.ArrangeCore%2A>方法進行處理。  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>方法評估<xref:System.Windows.UIElement.DesiredSize%2A>子系，並評估任何其他的邊界，可能會影響項目的呈現的大小。 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> 會產生`arrangeSize`，傳遞給<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法<xref:System.Windows.Controls.Panel>做為參數。 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 會產生`finalSize`子系。 最後，<xref:System.Windows.FrameworkElement.ArrangeCore%2A>方法不位移的屬性，例如邊界和對齊方式、 最後一個評估，將其配置位置內的子系。 子系不需要 (通常也不會) 填入整個已配置的空間。 然後將控制權傳回給父<xref:System.Windows.Controls.Panel>和版面配置處理序已完成。  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>面板項目和自訂版面配置行為  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含一組項目衍生自<xref:System.Windows.Controls.Panel>。 這些<xref:System.Windows.Controls.Panel>以許多複雜的配置的項目。 例如，堆疊項目輕鬆可藉由使用<xref:System.Windows.Controls.StackPanel>項目，雖然使用可能更複雜和可用的流動配置<xref:System.Windows.Controls.Canvas>。  
  
 下表摘要說明可用的配置<xref:System.Windows.Controls.Panel>項目。  
  
|面板名稱|描述|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|定義在其中您可以明確定位子項目座標相對於區域<xref:System.Windows.Controls.Canvas>區域。|  
|<xref:System.Windows.Controls.DockPanel>|定義一個區域，可供您在其中以子項目彼此間相對的水平或垂直方式排列子項目。|  
|<xref:System.Windows.Controls.Grid>|定義彈性的格線區域，由欄與列組成。|  
|<xref:System.Windows.Controls.StackPanel>|將子元素排成單一行，以水平或垂直方式排列。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|提供的架構<xref:System.Windows.Controls.Panel>虛擬化其子資料集合的項目。 這是 abstract 類別。|  
|<xref:System.Windows.Controls.WrapPanel>|將子項目置放於由左至右的連續位置，其中會在包含方塊的邊緣將內容換至下一行。 後續發生的順序是從上或由右至左，根據的值<xref:System.Windows.Controls.WrapPanel.Orientation%2A>屬性。|  
  
 需要不使用預先定義之任何可能的版面配置的應用程式<xref:System.Windows.Controls.Panel>項目，自訂配置行為可藉由繼承自<xref:System.Windows.Controls.Panel>和覆寫<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。 如需範例，請參閱 [Custom Radial Panel Sample](http://go.microsoft.com/fwlink/?LinkID=159982) (自訂放射狀面板範例)。  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>版面配置效能考量  
 版面配置是遞迴程序。 在每個子項目<xref:System.Windows.Controls.Panel.Children%2A>配置系統的每個引動過程期間處理集合。 因此，不需要時，應該避免觸發配置系統。 下列考量可協助您達到更佳的效能。  
  
-   請注意哪些屬性值變更將會由配置系統強制遞迴更新。  
  
     使用公用旗標，可標記其值可以初始化配置系統的相依性屬性。 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> 和<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>提供有用的線索有關哪一個屬性值的變更將會強制遞迴更新由配置系統。 一般情況下，可能會影響項目的週框方塊的大小任何屬性應該會有<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>旗標設為 true。 如需詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
-   可能的話，請使用<xref:System.Windows.UIElement.RenderTransform%2A>而不是<xref:System.Windows.FrameworkElement.LayoutTransform%2A>。  
  
     A<xref:System.Windows.FrameworkElement.LayoutTransform%2A>可以是非常有用的方式來影響內容[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 不過，如果不需要轉換的效果不會影響其他元素的位置，最好是使用<xref:System.Windows.UIElement.RenderTransform%2A>相反地，因為<xref:System.Windows.UIElement.RenderTransform%2A>不叫用的版面配置系統。 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 適用於其轉換，並強制遞迴配置更新的受影響項目的新位置。  
  
-   避免不必要的呼叫<xref:System.Windows.UIElement.UpdateLayout%2A>。  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A>方法強制遞迴配置更新，並經常是不必要。 除非您確定需要完整更新，否則請依賴配置系統來呼叫此方法。  
  
-   當使用大型<xref:System.Windows.Controls.Panel.Children%2A>集合，請考慮使用<xref:System.Windows.Controls.VirtualizingStackPanel>而不是一般<xref:System.Windows.Controls.StackPanel>。  
  
     透過虛擬化其子集合中，<xref:System.Windows.Controls.VirtualizingStackPanel>只會保持在父項的檢視區內目前的記憶體中的物件。 因此，在大部分情況下，都可以大幅改善效能。  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>子像素轉譯和版面配置進位  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形系統會使用裝置獨立單位來啟用解析度和裝置獨立性。 每個裝置獨立像素都會依系統的 [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] 設定自動進行調整。 這讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式針對不同的 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 設定進行適當調整，並自動讓應用程式感知 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]。  
  
 不過，因為會消除鋸齒，所以此 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 獨立性可以建立不規則的邊緣轉譯。 如果邊緣位置落在裝置像素中間，而不是裝置像素之間，則這些成品一般會看起來模糊或具有半透明邊緣。 配置系統提供一種方式，利用版面配置來進行這項的調整。 版面配置進位是配置系統會在版面配置階段期間將任何非整數像素值四捨五入。  
  
 預設會停用版面配置進位。 若要啟用配置進位，<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>屬性`true`任何<xref:System.Windows.FrameworkElement>。 因為這是相依性屬性，所以值將會傳播到視覺樹狀結構中的所有子系。 若要啟用版面配置進位整個 ui，<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>至`true`根容器上。 如需範例，請參閱 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>。  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>後續步驟  
 了解如何測量和排列項目是了解版面配置的第一個步驟。 如需有關可用<xref:System.Windows.Controls.Panel>項目，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。 若要進一步了解會影響版面配置的各種定位屬性，請參閱[對齊、邊界和填補概觀](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)。 如需自訂的範例<xref:System.Windows.Controls.Panel>項目，請參閱[自訂放射狀面板範例](http://go.microsoft.com/fwlink/?LinkID=159982)。 當您準備好要將其全部一起放在輕量應用程式時，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.UIElement>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [對齊、邊界和填補概觀](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [版面配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
