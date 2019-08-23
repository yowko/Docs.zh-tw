---
title: 優化效能:2D 圖形和影像處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 764e7e802ccaff50b76229b9441380bfe77fefb5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933343"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>優化效能:2D 圖形和影像處理
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供各種 2D 圖形和影像處理功能，可以針對您的應用程式需求最佳化。 本主題提供下列領域的效能最佳化相關資訊。  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>繪圖和圖形  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Media.Drawing>提供和<xref:System.Windows.Shapes.Shape>物件來表示圖形化繪圖內容。 不過, <xref:System.Windows.Media.Drawing>物件比<xref:System.Windows.Shapes.Shape>物件更簡單, 而且提供較佳的效能特性。  
  
 可<xref:System.Windows.Shapes.Shape>讓您在螢幕上繪製圖形形狀。 由於它們是衍生自<xref:System.Windows.FrameworkElement>類別, <xref:System.Windows.Shapes.Shape>因此可以在面板和大部分控制項內使用物件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了數層的圖形和轉譯服務存取權。 在最上層, <xref:System.Windows.Shapes.Shape>物件很容易使用, 並提供許多有用的功能, 例如版面配置和事件處理。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 則提供數個立即可用的 Shape 物件。 所有繪圖物件都是<xref:System.Windows.Shapes.Shape>繼承自類別。 可用的繪圖物件<xref:System.Windows.Shapes.Ellipse>包括<xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Path>、 <xref:System.Windows.Shapes.Polygon>、 <xref:System.Windows.Shapes.Polyline>、和<xref:System.Windows.Shapes.Rectangle>。  
  
 <xref:System.Windows.Media.Drawing>另一方面, 物件不是衍生自<xref:System.Windows.FrameworkElement>類別, 而是提供較輕量的實作為圖形、影像和文字的呈現。  
  
 <xref:System.Windows.Media.Drawing>物件有四種類型:  
  
- <xref:System.Windows.Media.GeometryDrawing>繪製圖形。  
  
- <xref:System.Windows.Media.ImageDrawing>繪製影像。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>繪製文字。  
  
- <xref:System.Windows.Media.DrawingGroup>繪製其他繪圖。 您可以使用繪圖群組，來將其他繪圖結合為單一複合繪圖。  
  
 <xref:System.Windows.Media.GeometryDrawing>物件可用來轉譯幾何內容。 衍生<xref:System.Windows.Media.Geometry>自它的類別和實體類別 ( <xref:System.Windows.Media.CombinedGeometry>例如、 <xref:System.Windows.Media.EllipseGeometry>和<xref:System.Windows.Media.PathGeometry>) 提供呈現2d 圖形的方法, 以及提供點擊測試和裁剪支援。 舉例來說，Geometry 物件可用來定義控制項的區域，或定義要套用至影像的裁剪區域。 Geometry 物件可以是矩形和圓形之類的簡單區域，或從兩個或多個 Geometry 物件建立的複合區域。 更複雜的幾何區域可以藉由合併<xref:System.Windows.Media.PathSegment>衍生的物件 ( <xref:System.Windows.Media.ArcSegment>例如、 <xref:System.Windows.Media.BezierSegment>和<xref:System.Windows.Media.QuadraticBezierSegment>) 來建立。  
  
 在介面上, <xref:System.Windows.Media.Geometry>類別<xref:System.Windows.Shapes.Shape>和類別相當類似。 這兩者都用於轉譯2d 圖形, 而且兩者都有類似的具體類別, 其衍生自它們, <xref:System.Windows.Media.EllipseGeometry>例如和。 <xref:System.Windows.Shapes.Ellipse> 不過，這兩組類別之間有非常重要的差異。 其中一個<xref:System.Windows.Media.Geometry>類別缺少<xref:System.Windows.Shapes.Shape>類別的某些功能, 例如能夠自行繪製。 若要繪製 Geometry 物件，必須使用 DrawingContext、Drawing 或 Path (注意，Path 也是一種 Shape) 等其他類別來執行繪製作業。 填滿、筆觸以及筆觸粗細等呈現屬性位於可繪製 Geometry 物件的類別中，而 Shape 物件則包含這些屬性。 針對這項差異的其中一個理解方式是：Geometry 物件可定義區域 (例如圓形)；而 Shape 物件則可定義區域、該區域的填滿方式和外框方式，並參與版面配置系統。  
  
 由於<xref:System.Windows.Shapes.Shape>物件衍生<xref:System.Windows.FrameworkElement>自類別, 因此使用它們可以在您的應用程式中增加更多的記憶體耗用量。 如果您真的不需要圖形內容<xref:System.Windows.FrameworkElement>的功能, 請考慮使用較輕量<xref:System.Windows.Media.Drawing>的物件。  
  
 如需<xref:System.Windows.Media.Drawing>物件的詳細資訊, 請參閱[繪圖物件總覽](../graphics-multimedia/drawing-objects-overview.md)。  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry 物件  
 物件是用來<xref:System.Windows.Media.PathGeometry>建立幾何圖案的輕量替代方式。 <xref:System.Windows.Media.StreamGeometry> <xref:System.Windows.Media.StreamGeometry>當您需要描述複雜幾何時, 請使用。 <xref:System.Windows.Media.StreamGeometry>已針對處理許多<xref:System.Windows.Media.PathGeometry>物件進行優化, 且相較于使用許多個別<xref:System.Windows.Media.PathGeometry>物件時執行得更好。  
  
 下列範例會使用屬性語法, 在中<xref:System.Windows.Media.StreamGeometry> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]建立三角形。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 如需<xref:System.Windows.Media.StreamGeometry>物件的詳細資訊, 請參閱[使用 system.windows.media.streamgeometry> 建立圖形](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)。  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual 物件  
 <xref:System.Windows.Media.DrawingVisual>物件是輕量繪圖類別, 用來呈現圖形、影像或文字。 此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，這使它有更好的效能。 基於此原因，它適合用於背景或美工圖案繪圖。 如需詳細資訊，請參閱[使用 DrawingVisual 物件](../graphics-multimedia/using-drawingvisual-objects.md)。  
  
<a name="Images"></a>   
## <a name="images"></a>影像  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]映射處理可大幅改善舊版 Windows 中的影像處理功能。 以往，影像處理功能 (例如顯示點陣圖或使用通用控制項上的影像) 主要是由 Microsoft Windows 圖形裝置介面 (GDI) 或 Microsoft Windows GDI+ 應用程式開發介面 (API) 進行處理。 這些 API 提供基本影像處理功能，但無法支援轉碼器擴充性和高畫質影像等功能。 WPF 影像處理 API 的設計目的是克服 GDI 和 GDI+ 的缺點，並提供一組新的 API 以在應用程式內顯示及使用影像。  
  
 使用影像時，請考慮下列建議事項以取得較佳的效能：  
  
- 如果您的應用程式需要顯示縮圖影像，請考慮建立影像的縮小版本。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 預設會載入您的影像，並將其解碼到完整大小。 如果您只需要影像的縮圖版本，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 仍會多此一舉地將影像解碼到完整大小，然後再縮至縮圖大小。 為了避免不必要的額外負荷，您可以要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 解碼影像至縮圖大小，或要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 載入縮圖大小的影像。  
  
- 一律將影像解碼至所需大小，而非預設大小。 如上所述，您可以要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將影像解碼至所需大小，而不是預設的完整大小。 這麼做不只能減少應用程式的工作集，還會降低執行速度。  
  
- 因此，可能的話，請將影像合併單一影像，例如多張影像組成的底片。  
  
- 如需詳細資訊，請參閱 [影像處理概觀](../graphics-multimedia/imaging-overview.md)。  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 建立任何點陣圖的比例動畫時，預設的高品質影像重新取樣演算法有時會耗用過多系統資源，導致畫面播放速率降低，從而造成動畫中斷。 藉由將<xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> <xref:System.Windows.Media.RenderOptions>物件的屬性設定為<xref:System.Windows.Media.BitmapScalingMode.LowQuality> , 您可以在縮放點陣圖時建立更平滑的動畫。 <xref:System.Windows.Media.BitmapScalingMode.LowQuality>模式會告訴[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]轉譯引擎在處理影像時, 從品質優化演算法切換到速度優化的演算法。  
  
 下列範例顯示如何設定影像物件的<xref:System.Windows.Media.BitmapScalingMode> 。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 根據預設, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不會快取呈現的<xref:System.Windows.Media.TileBrush>物件內容, 例如<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。 在靜態案例中, 場景<xref:System.Windows.Media.TileBrush>中的內容和使用都不會變更, 這是合理的, 因為它可節省視訊記憶體。 當使用靜態內容以非靜態方式使用<xref:System.Windows.Media.TileBrush>時 (例如, 當靜態<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>對應至旋轉3d 物件的介面) 時, 並不會有太大的意義。 的預設行為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是將<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>的整個內容重新轉譯為每個框架, 即使內容不變也一樣。  
  
 藉由將<xref:System.Windows.Media.RenderOptions.CachingHint%2A> <xref:System.Windows.Media.RenderOptions>物件的屬性設定為<xref:System.Windows.Media.CachingHint.Cache> , 您可以使用已快取的並排筆刷物件版本來增加效能。  
  
 和屬性值是相對大小的值, 可決定物件<xref:System.Windows.Media.TileBrush>因規模變更而應重新產生的時間。 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> 例如, 藉由將<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>屬性設定為 2.0, <xref:System.Windows.Media.TileBrush>只有當其大小超過目前快取大小的兩倍時, 才需要重新產生的快取。  
  
 下列範例顯示如何使用的快取提示選項<xref:System.Windows.Media.DrawingBrush>。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
- [動畫祕訣和訣竅](../graphics-multimedia/animation-tips-and-tricks.md)
