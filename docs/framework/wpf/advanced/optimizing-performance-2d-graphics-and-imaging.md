---
title: 最佳化效能：2D 圖形和影像處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: eb3686367873276587572addda436471cd1abf27
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291795"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>最佳化效能：2D 圖形和影像處理
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供各種 2D 圖形和影像處理功能，可以針對您的應用程式需求最佳化。 本主題提供下列領域的效能最佳化相關資訊。  

<a name="Drawing_and_Shapes"></a>
## <a name="drawing-and-shapes"></a>繪圖和圖形  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供<xref:System.Windows.Media.Drawing>和<xref:System.Windows.Shapes.Shape>物件來表示圖形繪圖內容。 但是，<xref:System.Windows.Media.Drawing>物件比<xref:System.Windows.Shapes.Shape>物件更簡單的構造，並提供更好的性能特徵。  
  
 A<xref:System.Windows.Shapes.Shape>允許您將圖形形狀繪製到螢幕。 由於物件派生自類，<xref:System.Windows.FrameworkElement><xref:System.Windows.Shapes.Shape>因此可以在面板和大多數控制項內使用物件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了數層的圖形和轉譯服務存取權。 在頂層，<xref:System.Windows.Shapes.Shape>物件便於使用，並提供許多有用的功能，如佈局和事件處理。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 則提供數個立即可用的 Shape 物件。 所有形狀物件都從<xref:System.Windows.Shapes.Shape>類繼承。 可用的形狀物件包括<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path>、、、<xref:System.Windows.Shapes.Polygon><xref:System.Windows.Shapes.Polyline>和<xref:System.Windows.Shapes.Rectangle>。  
  
 <xref:System.Windows.Media.Drawing>另一方面，物件不派生自類<xref:System.Windows.FrameworkElement>，並為渲染形狀、圖像和文本提供較輕的實現。  
  
 有四種類型的<xref:System.Windows.Media.Drawing>物件：  
  
- <xref:System.Windows.Media.GeometryDrawing>繪製形狀。  
  
- <xref:System.Windows.Media.ImageDrawing>繪製圖像。  
  
- <xref:System.Windows.Media.GlyphRunDrawing>繪製文本。  
  
- <xref:System.Windows.Media.DrawingGroup>繪製其他圖形。 您可以使用繪圖群組，將其他繪圖結合為單一複合繪圖。  
  
 該<xref:System.Windows.Media.GeometryDrawing>物件用於渲染幾何內容。 從<xref:System.Windows.Media.Geometry>它派生的類和具體類（如<xref:System.Windows.Media.CombinedGeometry>和<xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.PathGeometry>）提供了一種渲染 2D 圖形並提供點擊測試和剪輯支援的方法。 舉例來說，Geometry 物件可用來定義控制項的區域，或定義要套用至影像的裁剪區域。 Geometry 物件可以是矩形和圓形之類的簡單區域，或從兩個或多個 Geometry 物件建立的複合區域。 可以通過組合<xref:System.Windows.Media.PathSegment>派生物件（如<xref:System.Windows.Media.ArcSegment>、<xref:System.Windows.Media.BezierSegment>和<xref:System.Windows.Media.QuadraticBezierSegment>）來創建更複雜的幾何區域。  
  
 從表面上看，<xref:System.Windows.Media.Geometry>類和<xref:System.Windows.Shapes.Shape>類是相似的。 兩者都用於 2D 圖形的渲染，並且都有從它們派生的類似具體類，例如 和<xref:System.Windows.Media.EllipseGeometry><xref:System.Windows.Shapes.Ellipse>。 不過，這兩組類別之間有非常重要的差異。 首先，<xref:System.Windows.Media.Geometry>類缺乏<xref:System.Windows.Shapes.Shape>類的某些功能，例如繪製自身的能力。 若要繪製 Geometry 物件，必須使用 DrawingContext、Drawing 或 Path (注意，Path 也是一種 Shape) 等其他類別來執行繪製作業。 渲染屬性（如填充、描邊和描邊粗細）位於繪製幾何物件的類上，而形狀物件包含這些屬性。 考慮這種差異的一種方法是幾何物件定義區域（例如，圓，而形狀物件定義區域、定義該區域填滿和輪廓的方式以及參與佈局系統）。  
  
 由於<xref:System.Windows.Shapes.Shape>物件派生自類<xref:System.Windows.FrameworkElement>，因此使用它們可以在應用程式中顯著增加更多的記憶體消耗。 如果真的不需要圖形內容的功能，<xref:System.Windows.FrameworkElement>請考慮使用較輕<xref:System.Windows.Media.Drawing>的物件。  
  
 有關<xref:System.Windows.Media.Drawing>物件的詳細資訊，請參閱[繪製物件概述](../graphics-multimedia/drawing-objects-overview.md)。  
  
<a name="StreamGeometry_Objects"></a>
## <a name="streamgeometry-objects"></a>StreamGeometry 物件  
 該<xref:System.Windows.Media.StreamGeometry>物件是創建幾何形狀的羽量級<xref:System.Windows.Media.PathGeometry>替代方法。 當您需要<xref:System.Windows.Media.StreamGeometry>描述複雜的幾何體時，請使用 。 <xref:System.Windows.Media.StreamGeometry>針對處理許多<xref:System.Windows.Media.PathGeometry>物件進行了優化，與使用許多單個<xref:System.Windows.Media.PathGeometry>物件相比，性能更好。  
  
 下面的示例使用屬性語法在 中<xref:System.Windows.Media.StreamGeometry>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]創建三角形。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 有關<xref:System.Windows.Media.StreamGeometry>物件的詳細資訊，請參閱[使用流幾何創建形狀](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)。  
  
<a name="DrawingVisual_Objects"></a>
## <a name="drawingvisual-objects"></a>DrawingVisual 物件  
 該<xref:System.Windows.Media.DrawingVisual>物件是一個羽量級繪圖類，用於渲染形狀、圖像或文本。 此類別之所以被視為輕量型，是因為它不提供版面配置或事件處理，這使它有更好的效能。 基於此原因，它適合用於背景或美工圖案繪圖。 如需詳細資訊，請參閱[使用 DrawingVisual 物件](../graphics-multimedia/using-drawingvisual-objects.md)。  
  
<a name="Images"></a>
## <a name="images"></a>影像  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]與早期版本的 Windows 中的映射功能相比，映射提供了顯著改進。 映射功能（如顯示點陣圖或使用公共控制項上的圖像）主要由 Microsoft Windows 圖形裝置介面 （GDI） 或 Microsoft Windows GDI+ 應用程式開發介面 （API） 處理。 這些 API 提供了基線成像功能，但缺少支援編解碼器可擴充性和高保真圖像支援等功能。 WPF 成像 API 已重新設計，以克服 GDI 和 GDI® 的缺點，並提供一組新的 API 來在應用程式中顯示和使用圖像。  
  
 使用影像時，請考慮下列建議事項以取得較佳的效能：  
  
- 如果您的應用程式需要顯示縮圖影像，請考慮建立影像的縮小版本。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 預設會載入您的影像，並將其解碼到完整大小。 如果您只需要影像的縮圖版本，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 仍會多此一舉地將影像解碼到完整大小，然後再縮至縮圖大小。 為了避免不必要的額外負荷，您可以要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 解碼影像至縮圖大小，或要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 載入縮圖大小的影像。  
  
- 一律將影像解碼至所需大小，而非預設大小。 如上所述，您可以要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將影像解碼至所需大小，而不是預設的完整大小。 這麼做不只能減少應用程式的工作集，還會降低執行速度。  
  
- 因此，可能的話，請將影像合併單一影像，例如多張影像組成的底片。  
  
- 有關詳細資訊，請參閱[映射概述](../graphics-multimedia/imaging-overview.md)。  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 為任何點陣圖的比例設置動畫時，預設的高品質圖像重採樣演算法有時會消耗足夠的系統資源，從而導致畫面播放速率下降，從而有效地導致動畫斷斷續續。 通過將<xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A><xref:System.Windows.Media.RenderOptions>物件的屬性設置為<xref:System.Windows.Media.BitmapScalingMode.LowQuality>，可以在縮放點陣圖時創建更平滑的動畫。 <xref:System.Windows.Media.BitmapScalingMode.LowQuality>模式告訴渲[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]染引擎在處理圖像時從品質優化演算法切換到速度優化演算法。  
  
 下面的示例演示如何為影像物件設置<xref:System.Windows.Media.BitmapScalingMode>。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 預設情況下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不緩存<xref:System.Windows.Media.TileBrush>物件的呈現內容，如<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。 在場景中的內容或使用<xref:System.Windows.Media.TileBrush>不變的靜態方案中，這是有道理的，因為它可以節省視頻記憶體。 當以非靜態方式使用<xref:System.Windows.Media.TileBrush>具有靜態內容的內容時，例如，當靜態<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>映射到旋轉 3D 物件的表面時，則沒有意義。 的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]預設行為是重新呈現<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>每個幀的整個內容，即使內容不變。  
  
 通過將<xref:System.Windows.Media.RenderOptions.CachingHint%2A><xref:System.Windows.Media.RenderOptions>物件的屬性設置為<xref:System.Windows.Media.CachingHint.Cache>，可以使用拼貼筆刷物件的緩存版本來提高性能。  
  
 和 屬性值是相對大小值，用於確定何時<xref:System.Windows.Media.TileBrush>應由於比例變化而重新生成物件。 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> 例如，通過將<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>屬性設置為 2.0，僅當其大小超過當前緩存<xref:System.Windows.Media.TileBrush>大小的兩倍時，才需要重新生成 該屬性的緩存。  
  
 下面的示例演示如何對 使用 緩存提示選項<xref:System.Windows.Media.DrawingBrush>。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [文本](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
- [動畫祕訣和訣竅](../graphics-multimedia/animation-tips-and-tricks.md)
