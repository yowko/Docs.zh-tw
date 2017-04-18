---
title: "最佳化效能：2D 圖形和影像處理 | Microsoft Docs"
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
  - "2D 圖形"
  - "繪製, 最佳化效能"
  - "圖形, 效能"
  - "影像, 最佳化效能"
  - "影像處理, 最佳化效能"
  - "圖案, 最佳化效能"
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 最佳化效能：2D 圖形和影像處理
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供大範圍的 2D 圖形和影像處理功能，可予以最佳化以符合應用程式的需求。  本主題提供那些區域的效能最佳化資訊。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Drawing_and_Shapes"></a>   
## 繪圖和圖案  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供 <xref:System.Windows.Media.Drawing> 和 <xref:System.Windows.Shapes.Shape> 物件來表示圖形繪圖內容。  不過，<xref:System.Windows.Media.Drawing> 物件是比 <xref:System.Windows.Shapes.Shape> 物件還要簡單的建構，而且提供較佳的效能特性。  
  
 <xref:System.Windows.Shapes.Shape> 可讓您將圖形圖案繪製至螢幕。  因為它們是衍生自 <xref:System.Windows.FrameworkElement> 類別，所以 <xref:System.Windows.Shapes.Shape> 物件可以用於面板和大部分控制項內。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供圖形和呈現服務的數個存取層。  在最上層，<xref:System.Windows.Shapes.Shape> 物件十分容易使用，而且會提供許多有用的功能 \(例如配置和事件處理\)。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會提供一些立即可用的圖案物件。  所有圖案物件都是繼承自 <xref:System.Windows.Shapes.Shape> 類別。  可用的圖案物件包括 <xref:System.Windows.Shapes.Ellipse>、<xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Path>、<xref:System.Windows.Shapes.Polygon>、<xref:System.Windows.Shapes.Polyline> 和 <xref:System.Windows.Shapes.Rectangle>。  
  
 反之，<xref:System.Windows.Media.Drawing> 物件不是衍生自 <xref:System.Windows.FrameworkElement> 類別，而且會提供較輕量 \(Lighter\-Weight\) 的圖案、影像和文字呈現實作 \(Implementation\)。  
  
 <xref:System.Windows.Media.Drawing> 物件有四種型別：  
  
-   <xref:System.Windows.Media.GeometryDrawing>：繪製圖案。  
  
-   <xref:System.Windows.Media.ImageDrawing>：繪製影像。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing>：繪製文字。  
  
-   <xref:System.Windows.Media.DrawingGroup>：繪製其他繪圖。  您可以使用繪圖群組，將其他繪圖結合為單一複合繪圖。  
  
 <xref:System.Windows.Media.GeometryDrawing> 物件是用來呈現幾何內容。  <xref:System.Windows.Media.Geometry> 類別以及從該類別衍生的具象類別 \(如 <xref:System.Windows.Media.CombinedGeometry>、<xref:System.Windows.Media.EllipseGeometry> 和 <xref:System.Windows.Media.PathGeometry>\) 提供呈現 2D 圖形的方法，以及提供點擊測試 \(Hit\-Test\) 和裁剪 \(Clipping\) 支援。  例如，幾何物件可以用來定義控制項區域，或定義要套用至影像的裁剪區域。  幾何物件可以是簡單的區域，例如矩形和圓形，或從兩個以上幾何物件建立的複合區域。  而透過結合 <xref:System.Windows.Media.PathSegment> 衍生物件 \(如 <xref:System.Windows.Media.ArcSegment>、<xref:System.Windows.Media.BezierSegment> 和 <xref:System.Windows.Media.QuadraticBezierSegment>\)，可以建立更複雜的幾何區域。  
  
 表面上看來，<xref:System.Windows.Media.Geometry> 類別和 <xref:System.Windows.Shapes.Shape> 類別十分相似。  這兩個類別都用於呈現 2D 圖形，而且也都具有從它們衍生的類似具象類別 \(例如，<xref:System.Windows.Media.EllipseGeometry> 和 <xref:System.Windows.Shapes.Ellipse>\)。  然而，這兩組類別之間還是有很大的不同。  其中一項是 <xref:System.Windows.Media.Geometry> 類別缺少 <xref:System.Windows.Shapes.Shape> 類別的一些功能 \(如繪製它自己的能力\)。  若要繪製幾何物件，則必須使用另一個類別 \(如 DrawingContext、Drawing 或 Path\) \(值得注意的是 Path 就是 Shape\) 來執行繪製作業。  呈現屬性 \(如填滿、筆劃和筆劃粗細\) 是位在可以繪製幾何物件的類別上，而圖案物件則包含這些屬性。  其中一種分辨這項差異的方式是，幾何物件會定義區域 \(例如圓形\)，而圖案物件則會定義區域、定義填滿該區域並為該區域加上外框的方式，並參與配置系統。  
  
 因為 <xref:System.Windows.Shapes.Shape> 物件是衍生自 <xref:System.Windows.FrameworkElement> 類別，所以在應用程式中使用它們會明顯增加記憶體的耗用。  如果確實不需要圖形內容的 <xref:System.Windows.FrameworkElement> 功能，請考慮使用較輕量的 <xref:System.Windows.Media.Drawing> 物件。  
  
 如需 <xref:System.Windows.Media.Drawing> 物件的詳細資訊，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。  
  
<a name="StreamGeometry_Objects"></a>   
## StreamGeometry 物件  
 <xref:System.Windows.Media.StreamGeometry> 物件是 <xref:System.Windows.Media.PathGeometry> 的輕量替代方式，用於建立幾何圖案。  當您需要描述複雜幾何時，請使用 <xref:System.Windows.Media.StreamGeometry>。  <xref:System.Windows.Media.StreamGeometry> 已最佳化，適合用來處理許多 <xref:System.Windows.Media.PathGeometry> 物件，而且與使用多個個別 <xref:System.Windows.Media.PathGeometry> 物件相比，執行效能也較佳。  
  
 下列範例使用屬性語法，在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中建立三角形 <xref:System.Windows.Media.StreamGeometry>。  
  
 [!code-xml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 如需 <xref:System.Windows.Media.StreamGeometry> 物件的詳細資訊，請參閱 [使用 StreamGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)。  
  
<a name="DrawingVisual_Objects"></a>   
## DrawingVisual 物件  
 <xref:System.Windows.Media.DrawingVisual> 物件為輕量繪圖類別，可用於呈現圖案、影像或文字。  此類別因為不提供配置或事件處理，所以視為輕量類別，而配置或事件處理卻可改善其效能。  基於這個理由，繪圖適合用於背景或美工圖案。  如需詳細資訊，請參閱[使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)。  
  
<a name="Images"></a>   
## 影像  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 影像處理明顯改善了舊版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 中的影像處理功能。  影像處理功能 \(如在通用控制項上顯示點陣圖或使用影像\) 主要是透過 Microsoft Windows 繪圖裝置介面 \(Graphics Device Interface，GDI\) 或 Microsoft Windows GDI\+ 應用程式開發介面 \(Application Programming Interface，API\) 進行處理。  這些 API 提供基準的影像處理功能，但是缺少一些功能，例如支援轉碼器擴充性和高精確度影像支援。  WPF 影像處理 API 已經過重新設計，可以克服 GDI 和 GDI\+ 的缺點，並提供一組新的 API 以在應用程式內顯示及使用影像。  
  
 使用影像時，若要取得較佳的效能，請考慮下列建議：  
  
-   如果應用程式需要您顯示縮圖影像，請考慮建立尺寸縮小版的影像。  根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會載入影像，並將它解碼為完整大小。  如果只想要縮圖版本的影像，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 就不需要將影像解碼為完整大小，然後再將它縮小為縮圖大小。  為了避免這類不必要的負荷，您可以要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將影像解碼為縮圖大小，或要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 載入縮圖大小的影像。  
  
-   永遠將影像解碼為所要的大小，而不是預設的大小。  如前所述，請要求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將影像解碼為所要的大小，而不是預設的完整大小。  這樣不只會減少應用程式的工作集，還會提高執行速度。  
  
-   盡可能將影像合併為單一影像 \(如包含多個影像的軟片條\)。  
  
-   如需詳細資訊，請參閱[影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)。  
  
### BitmapScalingMode  
 建立任何點陣圖之縮放比例的動畫時，預設的高品質影像重新取樣演算法有時會耗用大量的系統資源，因而降低畫面格速率，可能也會讓動畫中斷。  將 <xref:System.Windows.Media.RenderOptions> 物件的 <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> 屬性設定為 <xref:System.Windows.Media.BitmapScalingMode>，則可以在縮放點陣圖時建立較平順的動畫。  <xref:System.Windows.Media.BitmapScalingMode> 模式會在處理影像時，告知 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 呈現引擎從品質最佳化演算法切換為速度最佳化演算法。  
  
 下列範例顯示如何設定影像物件的 <xref:System.Windows.Media.BitmapScalingMode>。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### CachingHint  
 根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 並不會快取 <xref:System.Windows.Media.TileBrush> 物件 \(如 <xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush>\) 的呈現內容。  在內容和場景中的 <xref:System.Windows.Media.TileBrush> 使用都未變更的靜態情況下，這樣有其意義，因為可以節省視訊記憶體。  但是在下列情況下則不具意義：以非靜態的方式使用具有靜態內容的 <xref:System.Windows.Media.TileBrush> \(例如，當靜態 <xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush> 對應至旋轉立體物件的表面時\)。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的預設行為是即使每個畫面格之 <xref:System.Windows.Media.DrawingBrush> 或 <xref:System.Windows.Media.VisualBrush> 的整個內容都未變更，仍然會重新呈現該內容。  
  
 藉由將 <xref:System.Windows.Media.RenderOptions> 物件的 <xref:System.Windows.Media.RenderOptions.CachingHint%2A> 屬性設定為 <xref:System.Windows.Media.CachingHint>，則可以使用並排顯示之筆刷物件的快取版本來提高效能。  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> 和 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 屬性值是相對大小值，可以判斷因縮放比例變更而應該重新產生 <xref:System.Windows.Media.TileBrush> 物件的時機。  例如，將 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> 屬性設定為 2.0，則 <xref:System.Windows.Media.TileBrush> 只有在大小超出目前快取大小的兩倍時才需要重新產生它的快取。  
  
 下列範例顯示如何使用 <xref:System.Windows.Media.DrawingBrush> 的快取提示選項。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## 請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)   
 [動畫秘訣和訣竅](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)