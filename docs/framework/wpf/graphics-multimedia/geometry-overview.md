---
title: 幾何概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
ms.openlocfilehash: f45c13e1af9bc2d1f75da11b13a2c03936b136c1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455017"
---
# <a name="geometry-overview"></a>幾何概觀
本總覽說明如何使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> 類別來描述圖形。 本主題也會對比 <xref:System.Windows.Media.Geometry> 物件與 <xref:System.Windows.Shapes.Shape> 元素之間的差異。  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>什麼是幾何？  
 <xref:System.Windows.Media.Geometry> 類別以及從中衍生的類別，例如 <xref:System.Windows.Media.EllipseGeometry>、<xref:System.Windows.Media.PathGeometry>和 <xref:System.Windows.Media.CombinedGeometry>，可讓您描述2D 圖形的幾何。 這些幾何描繪有許多用途，像是定義圖形來繪製到螢幕或定義點擊測試和裁剪區域。 您甚至可以使用幾何來定義動畫路徑。  
  
 <xref:System.Windows.Media.Geometry> 物件可以很簡單，例如矩形和圓形，或從兩個或多個 geometry 物件所建立的複合。  您可以使用 <xref:System.Windows.Media.PathGeometry> 和 <xref:System.Windows.Media.StreamGeometry> 類別來建立更複雜的幾何，這可讓您描述弧形和曲線。  
  
 由於 <xref:System.Windows.Media.Geometry> 是一種 <xref:System.Windows.Freezable>類型，因此 <xref:System.Windows.Media.Geometry> 物件會提供數個特殊功能：它們可以宣告為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)，在多個物件之間共用，使其成為唯讀以改善效能、複製並使其成為安全線程。 如需 <xref:System.Windows.Freezable> 物件所提供之不同功能的詳細資訊，請參閱可[凍結物件的總覽](../advanced/freezable-objects-overview.md)。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>幾何與形狀的比較  
 <xref:System.Windows.Media.Geometry> 和 <xref:System.Windows.Shapes.Shape> 類別看起來很類似，兩者都描述2D 圖形（例如，比較 <xref:System.Windows.Media.EllipseGeometry> 和 <xref:System.Windows.Shapes.Ellipse>），但有重要的差異。  
  
 對於一個，<xref:System.Windows.Media.Geometry> 類別會繼承自 <xref:System.Windows.Freezable> 類別，而 <xref:System.Windows.Shapes.Shape> 類別則是繼承自 <xref:System.Windows.FrameworkElement>。 因為它們是元素，所以 <xref:System.Windows.Shapes.Shape> 物件可以自行呈現並參與配置系統，而 <xref:System.Windows.Media.Geometry> 物件則不能。  
  
 雖然 <xref:System.Windows.Shapes.Shape> 物件比 <xref:System.Windows.Media.Geometry> 物件更容易使用，<xref:System.Windows.Media.Geometry> 物件的用途更高。 當 <xref:System.Windows.Shapes.Shape> 物件用來轉譯2D 圖形時，<xref:System.Windows.Media.Geometry> 物件可以用來定義2D 圖形的幾何區域、定義要裁剪的區域，或定義用於點擊測試的區域，例如。  
  
### <a name="the-path-shape"></a>路徑圖形  
 其中一個 <xref:System.Windows.Shapes.Shape>，<xref:System.Windows.Shapes.Path> 類別實際上會使用 <xref:System.Windows.Media.Geometry> 來描述其內容。 藉由使用 <xref:System.Windows.Media.Geometry> 來設定 <xref:System.Windows.Shapes.Path> 的 <xref:System.Windows.Shapes.Path.Data%2A> 屬性，並設定其 <xref:System.Windows.Shapes.Shape.Fill%2A> 和 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性，您就可以呈現 <xref:System.Windows.Media.Geometry>。  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>採用幾何的通用屬性  
 如前幾節所述，Geometry 物件可以與其他物件一起用於許多用途，例如繪製圖形、動畫以及裁剪。 下表列出數個類別，其中具有接受 <xref:System.Windows.Media.Geometry> 物件的屬性。  
  
|輸入|屬性|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>簡單幾何類型  
 所有幾何的基類都是 <xref:System.Windows.Media.Geometry>的抽象類別。  衍生自 <xref:System.Windows.Media.Geometry> 類別的類別，大致上可分為三個類別：簡單幾何、路徑幾何和複合幾何。  
  
 簡單的 geometry 類別包括 <xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.RectangleGeometry>和 <xref:System.Windows.Media.EllipseGeometry>，用來建立基本的幾何圖案，例如線條、矩形和圓形。  
  
- <xref:System.Windows.Media.LineGeometry> 是藉由指定行的起點和結束點來定義。  
  
- <xref:System.Windows.Media.RectangleGeometry> 是使用 <xref:System.Windows.Rect> 結構所定義，它會指定其相對位置及其高度和寬度。 您可以藉由設定 [<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>] 和 [<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> 屬性] 來建立圓角矩形。  
  
- <xref:System.Windows.Media.EllipseGeometry> 是由中心點、x 半徑和 y 半徑所定義。  下列範例示範如何建立簡單的幾何以用於轉譯和裁剪。  
  
 這些相同的圖形以及更複雜的圖形，可以使用 <xref:System.Windows.Media.PathGeometry> 或結合 geometry 物件一起建立，但這些類別提供較簡單的方法來產生這些基本幾何圖案。  
  
 下列範例顯示如何建立和轉譯 <xref:System.Windows.Media.LineGeometry>。  如先前所述，<xref:System.Windows.Media.Geometry> 物件無法繪製本身，因此範例會使用 <xref:System.Windows.Shapes.Path> 圖形來呈現線條。  因為某一行沒有區域，所以設定 <xref:System.Windows.Shapes.Path> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性不會有任何作用;相反地，只會指定 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性。 下圖顯示範例的輸出。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
從 (10,20) 繪製到 (100,130) 的 LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 下一個範例顯示如何建立和轉譯 <xref:System.Windows.Media.EllipseGeometry>。  這些範例會將 <xref:System.Windows.Media.EllipseGeometry> 的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 設定為點 `50,50`，而 x 半徑和 y 半徑兩者都設定為 `50`，這會建立直徑為100的圓形。  將值指派給 Path 元素的 Fill 屬性，即可繪製橢圓形的內部，在此案例中為 <xref:System.Windows.Media.Brushes.Gold%2A>。 下圖顯示範例的輸出。  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
在 (50,50) 繪製的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 下列範例顯示如何建立和轉譯 <xref:System.Windows.Media.RectangleGeometry>。  矩形的位置和維度是由 <xref:System.Windows.Rect> 結構所定義。 這個位置是`50,50`，而高度和寬度都是 `25`，可建立一個正方形。 下圖顯示範例的輸出。  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
在 50,50 繪製的 RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 下列範例顯示如何使用 <xref:System.Windows.Media.EllipseGeometry> 做為影像的裁剪區域。  <xref:System.Windows.Controls.Image> 物件的定義 <xref:System.Windows.FrameworkElement.Width%2A> 為200，而 <xref:System.Windows.FrameworkElement.Height%2A> 為150。  <xref:System.Windows.Media.EllipseGeometry>，其 <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 值為100、<xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> 值為75，而 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 值為100，75則設定為影像的 <xref:System.Windows.UIElement.Clip%2A> 屬性。  只有橢圓形區域內的影像部分才會顯示。 下圖顯示範例的輸出。  
  
 ![遭裁剪和未遭裁剪的影像](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
用來裁剪影像控制項的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>路徑幾何  
 <xref:System.Windows.Media.PathGeometry> 類別及其輕量對等（<xref:System.Windows.Media.StreamGeometry> 類別）提供方法來描述由弧形、曲線和線條組成的多個複雜數位。  
  
 <xref:System.Windows.Media.PathGeometry> 的核心是 <xref:System.Windows.Media.PathFigure> 物件的集合，因此名為，因為每個圖形都會描述 <xref:System.Windows.Media.PathGeometry>中的離散圖形。 每個 <xref:System.Windows.Media.PathFigure> 本身都是由一或多個 <xref:System.Windows.Media.PathSegment> 物件所組成，其中每一個都描述了圖表的一個區段。  
  
 區段的類型繁多。  
  
|區段類型|描述|範例|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|在兩個點之間建立橢圓形弧線。|[建立橢圓形弧線](how-to-create-an-elliptical-arc.md)。|  
|<xref:System.Windows.Media.BezierSegment>|在兩個點之間建立三次方貝茲曲線。|[建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)。|  
|<xref:System.Windows.Media.LineSegment>|在兩個點之間建立線條。|[在 PathGeometry 中建立 LineSegment](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|建立一系列三次方貝茲曲線。|請參閱 <xref:System.Windows.Media.PolyBezierSegment> 類型 頁面。|  
|<xref:System.Windows.Media.PolyLineSegment>|建立一系列的線條。|請參閱 <xref:System.Windows.Media.PolyLineSegment> 類型 頁面。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|建立一系列二次方貝茲曲線。|請參閱 <xref:System.Windows.Media.PolyQuadraticBezierSegment> 頁面。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|建立二次方貝茲曲線。|[建立二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)。|  
  
 <xref:System.Windows.Media.PathFigure> 內的區段會合並成單一幾何圖形，其中每個區段的結束點都是下一個區段的起點。 <xref:System.Windows.Media.PathFigure> 的 <xref:System.Windows.Media.PathFigure.StartPoint%2A> 屬性會指定繪製第一個區段的起點。 每個後續區段都會從前一個區段的結束點開始。 例如，可以定義從 `10,50` 到 `10,150` 的垂直線，方法是將 <xref:System.Windows.Media.PathFigure.StartPoint%2A> 屬性設定為 `10,50`，並建立 <xref:System.Windows.Media.LineSegment> 屬性設定為 <xref:System.Windows.Media.LineSegment.Point%2A> 的 `10,150`。  
  
 下列範例會建立一個簡單的 <xref:System.Windows.Media.PathGeometry>，其中包含具有 <xref:System.Windows.Media.LineSegment> 的單一 <xref:System.Windows.Media.PathFigure>，並使用 <xref:System.Windows.Shapes.Path> 元素加以顯示。 <xref:System.Windows.Media.PathFigure> 物件的 <xref:System.Windows.Media.PathFigure.StartPoint%2A> 設定為 `10,20`，而且 <xref:System.Windows.Media.LineSegment> 是以 `100,130`的結束點定義。 下圖顯示此範例所建立的 <xref:System.Windows.Media.PathGeometry>。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
包含單一 LineSegment 的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 值得一提的是，這個範例與前面的 <xref:System.Windows.Media.LineGeometry> 範例相同。  用於 <xref:System.Windows.Media.PathGeometry> 的語法比用於簡單 <xref:System.Windows.Media.LineGeometry>更詳細，而且在此情況下使用 <xref:System.Windows.Media.LineGeometry> 類別可能更有意義，但 <xref:System.Windows.Media.PathGeometry> 的詳細語法可讓幾何區域變得非常複雜。  
  
 您可以使用 <xref:System.Windows.Media.PathSegment> 物件的組合來建立更複雜的幾何。  
  
 下一個範例會使用 <xref:System.Windows.Media.BezierSegment>、<xref:System.Windows.Media.LineSegment>和 <xref:System.Windows.Media.ArcSegment> 來建立圖形。 此範例會先藉由定義四個點來建立三次方貝茲曲線：一個起點，也就是上一個區段的終點、一個結束點（<xref:System.Windows.Media.BezierSegment.Point3%2A>）和兩個控制點（<xref:System.Windows.Media.BezierSegment.Point1%2A> 和 <xref:System.Windows.Media.BezierSegment.Point2%2A>）。  三次方貝茲曲線的兩個控制點作用類似磁鐵，吸引原本為直線的部分，產生曲線。 第一個控制點 <xref:System.Windows.Media.BezierSegment.Point1%2A>會影響曲線的開始部分;第二個控制點（<xref:System.Windows.Media.BezierSegment.Point2%2A>）會影響曲線的結束部分。  
  
 然後，此範例會新增一個 <xref:System.Windows.Media.LineSegment>，這會在先前 <xref:System.Windows.Media.BezierSegment> 的終點之間繪製，並在其 <xref:System.Windows.Media.LineSegment> 屬性所指定的點之前。  
  
 然後，此範例會將 <xref:System.Windows.Media.ArcSegment>，這是從上一個 <xref:System.Windows.Media.LineSegment> 的結束點繪製到其 <xref:System.Windows.Media.ArcSegment.Point%2A> 屬性所指定的點。 此範例也會指定弧線的 x 和 y 半徑（<xref:System.Windows.Media.ArcSegment.Size%2A>）、旋轉角度（<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>）、表示產生的弧線角度（<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>）的旗標，以及表示弧線繪製方向的值（<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>）。 下圖顯示此範例所建立的圖形。  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 在 <xref:System.Windows.Media.PathGeometry>中使用多個 <xref:System.Windows.Media.PathFigure> 物件，可以建立更複雜的幾何。  
  
 下列範例會建立具有兩個 <xref:System.Windows.Media.PathFigure> 物件的 <xref:System.Windows.Media.PathGeometry>，其中每一個都包含多個 <xref:System.Windows.Media.PathSegment> 物件。  上述範例中的 <xref:System.Windows.Media.PathFigure>，以及使用 <xref:System.Windows.Media.PolyLineSegment> 和 <xref:System.Windows.Media.QuadraticBezierSegment> 的 <xref:System.Windows.Media.PathFigure>。  <xref:System.Windows.Media.PolyLineSegment> 是以點陣列定義，而 <xref:System.Windows.Media.QuadraticBezierSegment> 是以控制點和結束點定義。 下圖顯示此範例所建立的圖形。  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
有多個圖形的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 就像 <xref:System.Windows.Media.PathGeometry> 類別一樣，<xref:System.Windows.Media.StreamGeometry> 會定義複雜幾何圖形，其中可能包含曲線、弧形和線條。 不同于 <xref:System.Windows.Media.PathGeometry>，<xref:System.Windows.Media.StreamGeometry> 的內容不支援資料系結、動畫或修改。 當您需要描述複雜幾何，但不想要支援資料系結、動畫或修改的額外負荷時，請使用 <xref:System.Windows.Media.StreamGeometry>。 基於其效率，<xref:System.Windows.Media.StreamGeometry> 類別是描述裝飾項的絕佳選擇。  
  
 如需範例，請參閱[使用 StreamGeometry 建立圖形](how-to-create-a-shape-using-a-streamgeometry.md)。  
  
### <a name="path-markup-syntax"></a>路徑標記語法  
 <xref:System.Windows.Media.PathGeometry> 和 <xref:System.Windows.Media.StreamGeometry> 類型使用一系列的 move 和 draw 命令，支援 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 的屬性語法。 如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>複合幾何  
 複合幾何物件可以使用 <xref:System.Windows.Media.GeometryGroup>、<xref:System.Windows.Media.CombinedGeometry>，或藉由呼叫靜態 <xref:System.Windows.Media.Geometry> 方法 <xref:System.Windows.Media.Geometry.Combine%2A>來建立。  
  
- <xref:System.Windows.Media.CombinedGeometry> 物件和 <xref:System.Windows.Media.Geometry.Combine%2A> 方法會執行布耳運算，以結合兩個幾何所定義的區域。 不會捨棄具有區域的 <xref:System.Windows.Media.Geometry> 物件。 只能結合兩個 <xref:System.Windows.Media.Geometry> 物件（雖然這兩個幾何也可以是複合幾何）。  
  
- <xref:System.Windows.Media.GeometryGroup> 類別會建立其所包含之 <xref:System.Windows.Media.Geometry> 物件的獨有，而不會結合其區域。 可以將任何數目的 <xref:System.Windows.Media.Geometry> 物件新增至 <xref:System.Windows.Media.GeometryGroup>。 如需範例，請參閱[建立複合圖案](how-to-create-a-composite-shape.md)。  
  
 因為它們不會執行合併作業，所以使用 <xref:System.Windows.Media.GeometryGroup> 物件可提供使用 <xref:System.Windows.Media.CombinedGeometry> 物件或 <xref:System.Windows.Media.Geometry.Combine%2A> 方法的效能優勢。  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>合併幾何  
 上一節提到了 <xref:System.Windows.Media.CombinedGeometry> 物件，而 <xref:System.Windows.Media.Geometry.Combine%2A> 方法結合了其所包含之幾何所定義的區域。 <xref:System.Windows.Media.GeometryCombineMode> 列舉會指定如何結合幾何。 <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> 屬性的可能值為： <xref:System.Windows.Media.GeometryCombineMode.Union>、<xref:System.Windows.Media.GeometryCombineMode.Intersect>、<xref:System.Windows.Media.GeometryCombineMode.Exclude>和 <xref:System.Windows.Media.GeometryCombineMode.Xor>。  
  
 在下列範例中，會使用 Union 的合併模式來定義 <xref:System.Windows.Media.CombinedGeometry>。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但中心位移為50。  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![聯集合並模式的結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry> 是以 <xref:System.Windows.Media.GeometryCombineMode.Xor>的合併模式所定義。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但中心位移為50。  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 如需其他範例，請參閱[建立複合圖案](how-to-create-a-composite-shape.md)和[建立合併幾何](how-to-create-a-combined-geometry.md)。  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable 功能  
 因為它繼承自 <xref:System.Windows.Freezable> 類別，所以 <xref:System.Windows.Media.Geometry> 類別提供數個特殊功能： <xref:System.Windows.Media.Geometry> 物件可以宣告為[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)，在多個物件之間共用，使其成為唯讀以改善效能、複製和進行安全線程。 如需 <xref:System.Windows.Freezable> 物件所提供之不同功能的詳細資訊，請參閱可[凍結物件的總覽](../advanced/freezable-objects-overview.md)。  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>其他幾何功能  
 <xref:System.Windows.Media.Geometry> 類別也提供有用的公用程式方法，如下所示：  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>-取得 <xref:System.Windows.Media.Geometry>的區域。  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>-判斷幾何是否包含另一個 <xref:System.Windows.Media.Geometry>。  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>-判斷 <xref:System.Windows.Media.Geometry> 的筆劃是否包含指定的點。  
  
 如需其方法的完整清單，請參閱 <xref:System.Windows.Media.Geometry> 類別。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [路徑標記語法](path-markup-syntax.md)
- [「如何」主題](geometries-how-to-topics.md)
- [動畫概觀](animation-overview.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [繪圖物件概觀](drawing-objects-overview.md)
