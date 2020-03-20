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
ms.openlocfilehash: 1329f26e588b90fcd25052fb805058915b8825e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186466"
---
# <a name="geometry-overview"></a>幾何概觀
本概述介紹如何使用類[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Media.Geometry>來描述形狀。 本主題還對比物件和<xref:System.Windows.Media.Geometry><xref:System.Windows.Shapes.Shape>元素之間的差異。  

<a name="wcpsdk_graphics_geometry_introduction"></a>
## <a name="what-is-a-geometry"></a>什麼是幾何？  
 類<xref:System.Windows.Media.Geometry>和派生自它的類（如<xref:System.Windows.Media.EllipseGeometry>、<xref:System.Windows.Media.PathGeometry>和<xref:System.Windows.Media.CombinedGeometry>）使您能夠描述二維形狀的幾何體。 這些幾何描繪有許多用途，像是定義圖形來繪製到螢幕或定義點擊測試和裁剪區域。 您甚至可以使用幾何來定義動畫路徑。  
  
 <xref:System.Windows.Media.Geometry>物件可以是簡單的，例如矩形和圓，或從兩個或多個幾何物件創建的綜合物件。  可以使用<xref:System.Windows.Media.PathGeometry>和<xref:System.Windows.Media.StreamGeometry>類創建更複雜的幾何體，這使您能夠描述弧和曲線。  
  
 因為<xref:System.Windows.Media.Geometry>是 一種<xref:System.Windows.Freezable> <xref:System.Windows.Media.Geometry> ，物件提供了幾個特殊功能：它們可以聲明為[資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)，在多個物件之間共用，使唯讀以提高性能，克隆，並使執行緒安全。 有關<xref:System.Windows.Freezable>物件提供的不同要素的詳細資訊，請參閱[可凍結物件概述](../advanced/freezable-objects-overview.md)。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>
## <a name="geometries-vs-shapes"></a>幾何形狀與形狀  
 <xref:System.Windows.Media.Geometry>和<xref:System.Windows.Shapes.Shape>類看起來相似，因為它們都描述了二維形狀（例如比較<xref:System.Windows.Media.EllipseGeometry>和<xref:System.Windows.Shapes.Ellipse>，但存在重要差異）。  
  
 首先，<xref:System.Windows.Media.Geometry>類從<xref:System.Windows.Freezable>類繼承，<xref:System.Windows.Shapes.Shape>而類從<xref:System.Windows.FrameworkElement>繼承。 由於它們是元素，<xref:System.Windows.Shapes.Shape>因此物件可以渲染自己並參與佈局系統，而<xref:System.Windows.Media.Geometry>物件不能。  
  
 儘管<xref:System.Windows.Shapes.Shape>物件比<xref:System.Windows.Media.Geometry>物件更容易使用，但<xref:System.Windows.Media.Geometry>物件更通用。 當<xref:System.Windows.Shapes.Shape>物件用於渲染二維圖形時，<xref:System.Windows.Media.Geometry>物件可用於定義二維圖形的幾何區域、定義用於剪切的區域或定義用於點擊測試的區域。  
  
### <a name="the-path-shape"></a>路徑圖形  
 一<xref:System.Windows.Shapes.Shape>個，<xref:System.Windows.Shapes.Path>類，實際上使用來描述<xref:System.Windows.Media.Geometry>其內容。 通過設置<xref:System.Windows.Shapes.Path.Data%2A><xref:System.Windows.Shapes.Path>的 屬性<xref:System.Windows.Media.Geometry>和<xref:System.Windows.Shapes.Shape.Fill%2A>和<xref:System.Windows.Shapes.Shape.Stroke%2A>屬性，可以呈現 。 <xref:System.Windows.Media.Geometry>  
  
<a name="commonproperties"></a>
## <a name="common-properties-that-take-a-geometry"></a>採用幾何的通用屬性  
 如前幾節所述，Geometry 物件可以與其他物件一起用於許多用途，例如繪製圖形、動畫以及裁剪。 下表列出了具有獲取<xref:System.Windows.Media.Geometry>物件的屬性的幾個類。  
  
|類型|屬性|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>
## <a name="simple-geometry-types"></a>簡單幾何類型  
 所有幾何體的基類都是抽象類別<xref:System.Windows.Media.Geometry>。  從類派生的<xref:System.Windows.Media.Geometry>類大致可以分為三類：簡單幾何體、路徑幾何體和複合幾何體。  
  
 簡單幾何類包括<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.RectangleGeometry><xref:System.Windows.Media.EllipseGeometry>， 用於創建基本幾何形狀，如線條、矩形和圓。  
  
- 通過<xref:System.Windows.Media.LineGeometry>指定行的起始點和終點來定義。  
  
- 定義<xref:System.Windows.Media.RectangleGeometry>與一個<xref:System.Windows.Rect>結構，指定其相對位置及其高度和寬度。 您可以通過設置 和<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A><xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性來創建圓角矩形。  
  
- <xref:System.Windows.Media.EllipseGeometry>由中心點、x 半徑和 y 半徑定義。  下列範例示範如何建立簡單的幾何以用於轉譯和裁剪。  
  
 這些相同的形狀以及更複雜的形狀可以使用 或 通過將幾何物件組合在一<xref:System.Windows.Media.PathGeometry>起創建，但這些類為生成這些基本幾何形狀提供了更簡單的方法。  
  
 下面的示例演示如何創建和呈現 。 <xref:System.Windows.Media.LineGeometry>  如前所述，<xref:System.Windows.Media.Geometry>物件無法繪製自身，因此該示例使用<xref:System.Windows.Shapes.Path>形狀來渲染線條。  因為一條線沒有區域，設置<xref:System.Windows.Shapes.Shape.Fill%2A>的屬性<xref:System.Windows.Shapes.Path>將不起作用;相反，僅指定<xref:System.Windows.Shapes.Shape.Stroke%2A><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>和 屬性。 下圖顯示範例的輸出。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
從 (10,20) 繪製到 (100,130) 的 LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 下一個示例演示如何創建和呈現 。 <xref:System.Windows.Media.EllipseGeometry>  示例<xref:System.Windows.Media.EllipseGeometry.Center%2A>將<xref:System.Windows.Media.EllipseGeometry>的 設置為 的 設置為`50,50`點，x 半徑和 y 半徑都設置為`50`，這將創建直徑為 100 的圓。  橢圓的內部通過為 Path 元素的 Fill 屬性（本例<xref:System.Windows.Media.Brushes.Gold%2A>中）分配值來繪製。 下圖顯示範例的輸出。  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
在 (50,50) 繪製的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 下面的示例演示如何創建和呈現 。 <xref:System.Windows.Media.RectangleGeometry>  矩形的位置和尺寸由<xref:System.Windows.Rect>結構定義。 這個位置是`50,50`，而高度和寬度都是 `25`，可建立一個正方形。 下圖顯示範例的輸出。  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
在 50,50 繪製的 RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 下面的示例演示如何將 用作<xref:System.Windows.Media.EllipseGeometry>圖像的剪輯區域。  物件<xref:System.Windows.Controls.Image>定義的物件為<xref:System.Windows.FrameworkElement.Width%2A>200 和 150。 <xref:System.Windows.FrameworkElement.Height%2A>  <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.UIElement.Clip%2A>值為 100、值 75 和值 100，75 的 設置為圖像的屬性。 <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A>  只有橢圓形區域內的影像部分才會顯示。 下圖顯示範例的輸出。  
  
 ![遭裁剪和未遭裁剪的影像](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
用來裁剪影像控制項的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>
## <a name="path-geometries"></a>路徑幾何  
 類<xref:System.Windows.Media.PathGeometry>及其羽量級等效項<xref:System.Windows.Media.StreamGeometry>類提供了描述由弧、曲線和線組成的多個複雜圖形的方法。  
  
 在 的核心是<xref:System.Windows.Media.PathGeometry><xref:System.Windows.Media.PathFigure>物件的集合，因此之所以命名，是因為每個圖形描述 中的<xref:System.Windows.Media.PathGeometry>離散形狀。 每個<xref:System.Windows.Media.PathFigure>物件本身由一個或多個<xref:System.Windows.Media.PathSegment>物件組成，每個物件都描述了圖形的一段。  
  
 區段的類型繁多。  
  
|區段類型|描述|範例|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|在兩個點之間建立橢圓形弧線。|[創建橢圓弧](how-to-create-an-elliptical-arc.md)。|  
|<xref:System.Windows.Media.BezierSegment>|在兩個點之間建立三次方貝茲曲線。|[建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)。|  
|<xref:System.Windows.Media.LineSegment>|在兩個點之間建立線條。|[在 PathGeometry 中建立 LineSegment](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|建立一系列三次方貝茲曲線。|請參閱<xref:System.Windows.Media.PolyBezierSegment>類型頁。|  
|<xref:System.Windows.Media.PolyLineSegment>|建立一系列的線條。|請參閱<xref:System.Windows.Media.PolyLineSegment>類型頁。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|建立一系列二次方貝茲曲線。|請參閱頁面<xref:System.Windows.Media.PolyQuadraticBezierSegment>。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|建立二次方貝茲曲線。|[創建一個二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)。|  
  
 中的線段<xref:System.Windows.Media.PathFigure>合併為單個幾何形狀，每個段的端點是下一個段的起點。 的屬性<xref:System.Windows.Media.PathFigure.StartPoint%2A><xref:System.Windows.Media.PathFigure>指定從中繪製第一個段的點。 每個後續區段都會從前一個區段的結束點開始。 例如，`10,50``10,150`可以通過將<xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性設置為 和`10,50`創建<xref:System.Windows.Media.LineSegment>屬性<xref:System.Windows.Media.LineSegment.Point%2A>設置為 的`10,150`  
  
 下面的示例創建一個包含<xref:System.Windows.Media.PathGeometry>的帶有 的<xref:System.Windows.Media.PathFigure><xref:System.Windows.Media.LineSegment>單個的簡單組成的，並使用<xref:System.Windows.Shapes.Path>元素顯示它。 物件的<xref:System.Windows.Media.PathFigure><xref:System.Windows.Media.PathFigure.StartPoint%2A>設置為`10,20`和<xref:System.Windows.Media.LineSegment> `100,130` 下圖顯示了此示例<xref:System.Windows.Media.PathGeometry>創建的示例。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
包含單一 LineSegment 的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 值得將此示例與前面的<xref:System.Windows.Media.LineGeometry>示例進行對比。  用於<xref:System.Windows.Media.PathGeometry>的語法比用於<xref:System.Windows.Media.LineGeometry>簡單語法的語法要詳細得多，在這種情況下，使用<xref:System.Windows.Media.LineGeometry>類可能更有意義，但 詳細<xref:System.Windows.Media.PathGeometry>語法允許極其複雜和複雜的幾何區域。  
  
 可以使用<xref:System.Windows.Media.PathSegment>物件的組合創建更複雜的幾何體。  
  
 下一個<xref:System.Windows.Media.BezierSegment>示例使用 、<xref:System.Windows.Media.LineSegment>和<xref:System.Windows.Media.ArcSegment>創建形狀。 該示例首先創建一個立方 Bezier 曲線是通過定義四個點：起始點，即上一段的終點、一個端點<xref:System.Windows.Media.BezierSegment.Point3%2A>（） 和兩個<xref:System.Windows.Media.BezierSegment.Point1%2A>控制<xref:System.Windows.Media.BezierSegment.Point2%2A>點 （和 ）。  三次方貝茲曲線的兩個控制點作用類似磁鐵，吸引原本為直線的部分，產生曲線。 第一個控制點<xref:System.Windows.Media.BezierSegment.Point1%2A>， 影響曲線的開始部分;第二個<xref:System.Windows.Media.BezierSegment.Point2%2A>控制點 ， 影響曲線的結束部分。  
  
 然後，該示例添加<xref:System.Windows.Media.LineSegment>一個 ，該點在之前的<xref:System.Windows.Media.BezierSegment>終點之間繪製到其<xref:System.Windows.Media.LineSegment>屬性指定的點。  
  
 然後，該示例添加<xref:System.Windows.Media.ArcSegment>一個 ，該點從前面的<xref:System.Windows.Media.LineSegment>端點繪製到其<xref:System.Windows.Media.ArcSegment.Point%2A>屬性指定的點。 該示例還指定圓弧的 x 和 y 半徑<xref:System.Windows.Media.ArcSegment.Size%2A>（）、旋轉角度<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>（）、指示結果弧角角度應大的標誌 （），<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>以及指示弧方向繪製方向的值 （）。<xref:System.Windows.Media.ArcSegment.SweepDirection%2A> 下圖顯示此範例所建立的圖形。  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 使用 中的多個<xref:System.Windows.Media.PathFigure>物件可以創建更複雜的幾何體。 <xref:System.Windows.Media.PathGeometry>  
  
 下面的示例創建具有兩<xref:System.Windows.Media.PathGeometry>個<xref:System.Windows.Media.PathFigure>物件的 ，每個物件包含多個<xref:System.Windows.Media.PathSegment>物件。  使用<xref:System.Windows.Media.PathFigure>上例中的 和<xref:System.Windows.Media.PathFigure>a<xref:System.Windows.Media.PolyLineSegment>和<xref:System.Windows.Media.QuadraticBezierSegment>a。  A<xref:System.Windows.Media.PolyLineSegment>使用點陣列定義，<xref:System.Windows.Media.QuadraticBezierSegment>使用控制點和端點定義 。 下圖顯示此範例所建立的圖形。  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
有多個圖形的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 與類<xref:System.Windows.Media.PathGeometry>一樣，<xref:System.Windows.Media.StreamGeometry>定義可能包含曲線、圓弧和線條的複雜幾何形狀。 與<xref:System.Windows.Media.PathGeometry>不同，的內容<xref:System.Windows.Media.StreamGeometry>不支援資料繫結、動畫或修改。 當您需要<xref:System.Windows.Media.StreamGeometry>描述複雜的幾何體，但不希望支援資料繫結、動畫或修改時，請使用 。 由於其效率，<xref:System.Windows.Media.StreamGeometry>該類是描述裝飾器的好選擇。  
  
 如需範例，請參閱[使用 StreamGeometry 建立圖形](how-to-create-a-shape-using-a-streamgeometry.md)。  
  
### <a name="path-markup-syntax"></a>路徑標記語法  
 和 類型支援使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]一系列特殊的移動和繪製命令的屬性語法。 <xref:System.Windows.Media.StreamGeometry> <xref:System.Windows.Media.PathGeometry> 如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>
## <a name="composite-geometries"></a>複合幾何  
 可以使用<xref:System.Windows.Media.GeometryGroup>、或<xref:System.Windows.Media.CombinedGeometry>調用靜態<xref:System.Windows.Media.Geometry>方法<xref:System.Windows.Media.Geometry.Combine%2A>創建複合幾何物件。  
  
- 物件<xref:System.Windows.Media.CombinedGeometry>和方法<xref:System.Windows.Media.Geometry.Combine%2A>執行布林操作以組合由兩個幾何體定義的區域。 <xref:System.Windows.Media.Geometry>沒有區域的物件將被丟棄。 只能組合<xref:System.Windows.Media.Geometry>兩個物件（儘管這兩個幾何體也可以是複合幾何體）。  
  
- 類<xref:System.Windows.Media.GeometryGroup>創建它包含<xref:System.Windows.Media.Geometry>的物件的合併，而不合並其區域。 任意數量的<xref:System.Windows.Media.Geometry>物件都可以添加到 。 <xref:System.Windows.Media.GeometryGroup> 如需範例，請參閱[建立複合圖案](how-to-create-a-composite-shape.md)。  
  
 因為它們不執行組合操作，因此使用<xref:System.Windows.Media.GeometryGroup>物件比使用<xref:System.Windows.Media.CombinedGeometry>物件或<xref:System.Windows.Media.Geometry.Combine%2A>方法具有性能優勢。  
  
<a name="combindgeometriessection"></a>
## <a name="combined-geometries"></a>合併幾何  
 上一節提到<xref:System.Windows.Media.CombinedGeometry>物件，<xref:System.Windows.Media.Geometry.Combine%2A>該方法組合了由它們包含的幾何體定義的區域。 枚<xref:System.Windows.Media.GeometryCombineMode>舉指定幾何體的組合方式。 屬性<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>的可能值為<xref:System.Windows.Media.GeometryCombineMode.Union>： 、、<xref:System.Windows.Media.GeometryCombineMode.Intersect><xref:System.Windows.Media.GeometryCombineMode.Exclude>和<xref:System.Windows.Media.GeometryCombineMode.Xor>。  
  
 在下面的示例中，使用聯合<xref:System.Windows.Media.CombinedGeometry>聯合模式定義 。  和<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>定義為<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>半徑相同的圓，但中心偏移 50。  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Union 合併模式的結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 在下面的示例中，使用<xref:System.Windows.Media.CombinedGeometry><xref:System.Windows.Media.GeometryCombineMode.Xor>的組合模式 定義 。  和<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>定義為<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>半徑相同的圓，但中心偏移 50。  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 如需其他範例，請參閱[建立複合圖案](how-to-create-a-composite-shape.md)和[建立合併幾何](how-to-create-a-combined-geometry.md)。  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Freezable 功能  
 <xref:System.Windows.Freezable>由於該<xref:System.Windows.Media.Geometry>類從類繼承，因此提供了幾個特殊功能：<xref:System.Windows.Media.Geometry>物件可以聲明為[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)，在多個物件之間共用，使唯讀以提高性能、克隆和使執行緒安全。 有關<xref:System.Windows.Freezable>物件提供的不同要素的詳細資訊，請參閱[可凍結物件概述](../advanced/freezable-objects-overview.md)。  
  
<a name="othergeometryfeatures"></a>
## <a name="other-geometry-features"></a>其他幾何功能  
 該<xref:System.Windows.Media.Geometry>類還提供有用的實用程式方法，例如：  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>- 獲取 的區域<xref:System.Windows.Media.Geometry>。  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>- 確定幾何圖形是否包含另一<xref:System.Windows.Media.Geometry>個 。  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>- 確定 的描邊<xref:System.Windows.Media.Geometry>是否包含指定的點。  
  
 有關其<xref:System.Windows.Media.Geometry>方法的完整清單，請參閱 類。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [路徑標記語法](path-markup-syntax.md)
- [如何使用主題](geometries-how-to-topics.md)
- [動畫概觀](animation-overview.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [繪圖物件概觀](drawing-objects-overview.md)
