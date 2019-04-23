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
ms.openlocfilehash: f4f109b51ed566d1996b0c59b4ecbe51caa022cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179994"
---
# <a name="geometry-overview"></a>幾何概觀
本概觀說明如何使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Media.Geometry>類別來描繪圖形。 本主題也會對照之間的差異<xref:System.Windows.Media.Geometry>物件和<xref:System.Windows.Shapes.Shape>項目。  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>什麼是幾何？  
 <xref:System.Windows.Media.Geometry>類別和類別衍生，例如<xref:System.Windows.Media.EllipseGeometry>， <xref:System.Windows.Media.PathGeometry>，和<xref:System.Windows.Media.CombinedGeometry>，讓您描繪 2d 圖形的幾何。 這些幾何描繪有許多用途，像是定義圖形來繪製到螢幕或定義點擊測試和裁剪區域。 您甚至可以使用幾何來定義動畫路徑。  
  
 <xref:System.Windows.Media.Geometry> 物件可以簡單，例如矩形和圓形或複合，建立從兩個或多個 geometry 物件。  使用也可以建立更複雜的幾何<xref:System.Windows.Media.PathGeometry>和<xref:System.Windows.Media.StreamGeometry>類別，可讓您描繪弧線和曲線。  
  
 因為<xref:System.Windows.Media.Geometry>是一種<xref:System.Windows.Freezable>，<xref:System.Windows.Media.Geometry>物件提供數個特殊功能︰ 它們可以宣告為[資源](../advanced/xaml-resources.md)、 多個物件，成為唯讀，以改善效能，複製，在共用和變更為安全執行緒。 如需詳細資訊，所提供的不同功能的相關<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>幾何與圖形  
 <xref:System.Windows.Media.Geometry>並<xref:System.Windows.Shapes.Shape>在於兩者都描繪 2d 圖形類別看起來很類似 (比較<xref:System.Windows.Media.EllipseGeometry>和<xref:System.Windows.Shapes.Ellipse>例如)，但有重要的差異。  
  
 第一，<xref:System.Windows.Media.Geometry>類別繼承自<xref:System.Windows.Freezable>類別同時<xref:System.Windows.Shapes.Shape>類別繼承自<xref:System.Windows.FrameworkElement>。 因為它們是項目，<xref:System.Windows.Shapes.Shape>物件可轉譯本身，並參與版面配置系統，而<xref:System.Windows.Media.Geometry>物件則否。  
  
 雖然<xref:System.Windows.Shapes.Shape>物件會更容易使用比<xref:System.Windows.Media.Geometry>物件，<xref:System.Windows.Media.Geometry>物件具有更多功能。 雖然<xref:System.Windows.Shapes.Shape>物件用來轉譯 2d 圖形<xref:System.Windows.Media.Geometry>物件可用來定義 2d 圖形的幾何區域、 定義裁剪區域或定義的區域進行點擊測試，例如。  
  
### <a name="the-path-shape"></a>路徑圖形  
 一<xref:System.Windows.Shapes.Shape>，則<xref:System.Windows.Shapes.Path>類別，實際上會使用<xref:System.Windows.Media.Geometry>來描述其內容。 藉由設定<xref:System.Windows.Shapes.Path.Data%2A>屬性<xref:System.Windows.Shapes.Path>具有<xref:System.Windows.Media.Geometry>並設定其<xref:System.Windows.Shapes.Shape.Fill%2A>並<xref:System.Windows.Shapes.Shape.Stroke%2A>屬性，您可以轉譯<xref:System.Windows.Media.Geometry>。  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>採用幾何的通用屬性  
 如前幾節所述，Geometry 物件可以與其他物件一起用於許多用途，例如繪製圖形、動畫以及裁剪。 下表列出數個類別具有採用屬性<xref:System.Windows.Media.Geometry>物件。  
  
|類型|屬性|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>簡單幾何類型  
 所有幾何的基底類別是抽象類別<xref:System.Windows.Media.Geometry>。  衍生自類別<xref:System.Windows.Media.Geometry>類別可大致分為三個類別： 簡單的幾何、 路徑幾何及複合幾何。  
  
 簡單幾何類別包括<xref:System.Windows.Media.LineGeometry>， <xref:System.Windows.Media.RectangleGeometry>，和<xref:System.Windows.Media.EllipseGeometry>，並用來建立基本的幾何圖形，例如線條、 矩形和圓形。  
  
-   A<xref:System.Windows.Media.LineGeometry>定義藉由指定列和結束點的起始點。  
  
-   A<xref:System.Windows.Media.RectangleGeometry>定義<xref:System.Windows.Rect>結構，指定其相對位置及其高度和寬度。 您可以設定來建立圓角的矩形<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性。  
  
-   <xref:System.Windows.Media.EllipseGeometry>由中心點、 x 半徑和 y 半徑。  下列範例示範如何建立簡單的幾何以用於轉譯和裁剪。  
  
 這些相同的圖形，以及更複雜的圖形，您可以使用建立<xref:System.Windows.Media.PathGeometry>或藉由合併幾何物件，但這些類別提供簡單的方式來產生這些基本的幾何圖形。  
  
 下列範例示範如何建立和轉譯<xref:System.Windows.Media.LineGeometry>。  如先前所述<xref:System.Windows.Media.Geometry>物件是無法繪製本身，所以此範例會使用<xref:System.Windows.Shapes.Path>圖形來轉譯線條。  由於線條沒有不含區域，設定<xref:System.Windows.Shapes.Shape.Fill%2A>的屬性<xref:System.Windows.Shapes.Path>會有任何作用; 相反地，只有<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>指定屬性。 下圖顯示範例的輸出。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
從 (10,20) 繪製到 (100,130) 的 LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 下一個範例示範如何建立和轉譯<xref:System.Windows.Media.EllipseGeometry>。  範例集合<xref:System.Windows.Media.EllipseGeometry.Center%2A>的<xref:System.Windows.Media.EllipseGeometry>設為點`50,50`和半徑 x 和 y 半徑都設定為`50`，可建立直徑為 100 的圓形。  在此情況下將值指派給路徑元素的填滿屬性，用於繪製橢圓形內部<xref:System.Windows.Media.Brushes.Gold%2A>。 下圖顯示範例的輸出。  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
在 (50,50) 繪製的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 下列範例示範如何建立和轉譯<xref:System.Windows.Media.RectangleGeometry>。  所定義的位置和維度的矩形<xref:System.Windows.Rect>結構。 這個位置是`50,50`，而高度和寬度都是 `25`，可建立一個正方形。 下圖顯示範例的輸出。  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
在 50,50 繪製的 RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 下列範例示範如何使用<xref:System.Windows.Media.EllipseGeometry>為影像的裁剪區域。  <xref:System.Windows.Controls.Image>物件定義的<xref:System.Windows.FrameworkElement.Width%2A>為 200 和<xref:System.Windows.FrameworkElement.Height%2A>150 個。  <xref:System.Windows.Media.EllipseGeometry>具有<xref:System.Windows.Media.EllipseGeometry.RadiusX%2A>值為 100，<xref:System.Windows.Media.EllipseGeometry.RadiusY%2A>值為 75，和<xref:System.Windows.Media.EllipseGeometry.Center%2A>100,75 的值設定為<xref:System.Windows.UIElement.Clip%2A>映像的屬性。  只有橢圓形區域內的影像部分才會顯示。 下圖顯示範例的輸出。  
  
 ![裁剪和未遭裁剪的影像](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
用來裁剪影像控制項的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>路徑幾何  
 <xref:System.Windows.Media.PathGeometry>類別和其輕量級對等項目，<xref:System.Windows.Media.StreamGeometry>類別中，提供方法來描繪多個複雜形狀組成的弧線、 曲線和線條。  
  
 核心<xref:System.Windows.Media.PathGeometry>是一堆<xref:System.Windows.Media.PathFigure>物件，如此命名是因為每個圖表都會描述中的特定圖形<xref:System.Windows.Media.PathGeometry>。 每個<xref:System.Windows.Media.PathFigure>本身包含一或多個<xref:System.Windows.Media.PathSegment>物件，其中每個描述圖的區段。  
  
 區段的類型繁多。  
  
|區段類型|描述|範例|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|在兩個點之間建立橢圓形弧線。|[建立橢圓形弧線](how-to-create-an-elliptical-arc.md)。|  
|<xref:System.Windows.Media.BezierSegment>|在兩個點之間建立三次方貝茲曲線。|[建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)。|  
|<xref:System.Windows.Media.LineSegment>|在兩個點之間建立線條。|[在 PathGeometry 中建立 LineSegment](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|建立一系列三次方貝茲曲線。|請參閱<xref:System.Windows.Media.PolyBezierSegment>類型 頁面。|  
|<xref:System.Windows.Media.PolyLineSegment>|建立一系列的線條。|請參閱<xref:System.Windows.Media.PolyLineSegment>類型 頁面。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|建立一系列二次方貝茲曲線。|請參閱<xref:System.Windows.Media.PolyQuadraticBezierSegment>頁面。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|建立二次方貝茲曲線。|[建立二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)。|  
  
 內的區段<xref:System.Windows.Media.PathFigure>會結合成單一幾何圖形，每個區段的下一個區段的起始點的結束點。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性<xref:System.Windows.Media.PathFigure>指定從中繪製的第一個區段的點。 每個後續區段都會從前一個區段的結束點開始。 比方說，從垂直線`10,50`要`10,150`可以藉由設定定義<xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性設`10,50`並建立<xref:System.Windows.Media.LineSegment>與<xref:System.Windows.Media.LineSegment.Point%2A>屬性設定`10,150`。  
  
 下列範例會建立簡易<xref:System.Windows.Media.PathGeometry>組成單一<xref:System.Windows.Media.PathFigure>具有<xref:System.Windows.Media.LineSegment>，並顯示使用<xref:System.Windows.Shapes.Path>項目。 <xref:System.Windows.Media.PathFigure>物件的<xref:System.Windows.Media.PathFigure.StartPoint%2A>設為`10,20`並<xref:System.Windows.Media.LineSegment>的結束點定義`100,130`。 下圖顯示<xref:System.Windows.Media.PathGeometry>此範例所建立。  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
包含單一 LineSegment 的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 值得對照此範例中的使用上述<xref:System.Windows.Media.LineGeometry>範例。  所使用的語法<xref:System.Windows.Media.PathGeometry>會比使用簡單的更詳細<xref:System.Windows.Media.LineGeometry>，並可能比較合理使用<xref:System.Windows.Media.LineGeometry>類別，在此情況下，但冗長的語法的<xref:System.Windows.Media.PathGeometry>允許非常錯綜複雜又複雜幾何區域。  
  
 可以使用的組合來建立更複雜的幾何<xref:System.Windows.Media.PathSegment>物件。  
  
 下一個範例會使用<xref:System.Windows.Media.BezierSegment>，則<xref:System.Windows.Media.LineSegment>，和<xref:System.Windows.Media.ArcSegment>來建立圖形。 此範例首先會建立三次方貝茲曲線是藉由定義四個點： 起始點，也就是上一個區段，也就是結束點的結束點 (<xref:System.Windows.Media.BezierSegment.Point3%2A>)，和兩個控制點 (<xref:System.Windows.Media.BezierSegment.Point1%2A>和<xref:System.Windows.Media.BezierSegment.Point2%2A>)。  三次方貝茲曲線的兩個控制點作用類似磁鐵，吸引原本為直線的部分，產生曲線。 第一個控制點<xref:System.Windows.Media.BezierSegment.Point1%2A>，會影響開頭曲線部分; 第二個控制點， <xref:System.Windows.Media.BezierSegment.Point2%2A>，會影響曲線的結束部分。  
  
 範例接著會新增<xref:System.Windows.Media.LineSegment>，其中前一個結束點之間繪製<xref:System.Windows.Media.BezierSegment>，以指定的點前面有其<xref:System.Windows.Media.LineSegment>屬性。  
  
 範例接著會新增<xref:System.Windows.Media.ArcSegment>，這會從先前的結束點繪製<xref:System.Windows.Media.LineSegment>所指定的點至其<xref:System.Windows.Media.ArcSegment.Point%2A>屬性。 此範例也會指定弧線的 x 半徑和 y-(<xref:System.Windows.Media.ArcSegment.Size%2A>)，旋轉角度 (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>)、 旗標，指出所產生弧線角度應該多大 (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>)，以及指出繪製弧形方向的值 (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). 下圖顯示此範例所建立的圖形。  
  
 ![A PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 使用多個也可以建立更複雜的幾何<xref:System.Windows.Media.PathFigure>物件內<xref:System.Windows.Media.PathGeometry>。  
  
 下列範例會建立<xref:System.Windows.Media.PathGeometry>具有兩個<xref:System.Windows.Media.PathFigure>物件，其中每一個包含多個<xref:System.Windows.Media.PathSegment>物件。  <xref:System.Windows.Media.PathFigure>從上述範例中，<xref:System.Windows.Media.PathFigure>具有<xref:System.Windows.Media.PolyLineSegment>和<xref:System.Windows.Media.QuadraticBezierSegment>使用。  A<xref:System.Windows.Media.PolyLineSegment>定義的點陣列和<xref:System.Windows.Media.QuadraticBezierSegment>定義一個控制點和結束點。 下圖顯示此範例所建立的圖形。  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
有多個圖形的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 像是<xref:System.Windows.Media.PathGeometry>類別，<xref:System.Windows.Media.StreamGeometry>定義可能包含曲線、 弧線和線條的複雜幾何圖形。 不同於<xref:System.Windows.Media.PathGeometry>，內容<xref:System.Windows.Media.StreamGeometry>不支援資料繫結、 動畫或修改。 使用<xref:System.Windows.Media.StreamGeometry>當您需要描繪複雜幾何，但不是想資料繫結、 動畫或修改的額外負荷。 其效率，因為<xref:System.Windows.Media.StreamGeometry>類別是不錯的選擇來描繪裝飾項。  
  
 如需範例，請參閱[使用 StreamGeometry 建立圖形](how-to-create-a-shape-using-a-streamgeometry.md)。  
  
### <a name="path-markup-syntax"></a>路徑標記語法  
 <xref:System.Windows.Media.PathGeometry>並<xref:System.Windows.Media.StreamGeometry>類型支援[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性語法使用特殊的一系列移動和繪製命令。 如需詳細資訊，請參閱[路徑標記語法](path-markup-syntax.md)。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>複合幾何  
 複合幾何物件可以使用建立<xref:System.Windows.Media.GeometryGroup>，則<xref:System.Windows.Media.CombinedGeometry>，或藉由呼叫靜態<xref:System.Windows.Media.Geometry>方法<xref:System.Windows.Media.Geometry.Combine%2A>。  
  
-   <xref:System.Windows.Media.CombinedGeometry>物件和<xref:System.Windows.Media.Geometry.Combine%2A>方法執行布林作業來結合兩個幾何所定義的區域。 <xref:System.Windows.Media.Geometry> 不含任何區域的物件會被捨棄。 只有兩個<xref:System.Windows.Media.Geometry>（雖然這兩個幾何也可能是複合幾何），就可以合併物件。  
  
-   <xref:System.Windows.Media.GeometryGroup>類別會建立，就可以合併<xref:System.Windows.Media.Geometry>物件包含不需要合併其區域。 任意數目的<xref:System.Windows.Media.Geometry>可以將物件加入至<xref:System.Windows.Media.GeometryGroup>。 如需範例，請參閱[建立複合圖案](how-to-create-a-composite-shape.md)。  
  
 由於它們不會執行合併作業，使用<xref:System.Windows.Media.GeometryGroup>物件提供的效能優於<xref:System.Windows.Media.CombinedGeometry>物件或<xref:System.Windows.Media.Geometry.Combine%2A>方法。  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>合併幾何  
 上一節所述<xref:System.Windows.Media.CombinedGeometry>物件和<xref:System.Windows.Media.Geometry.Combine%2A>方法合併其包含的幾何所定義的區域。 <xref:System.Windows.Media.GeometryCombineMode>列舉會指定如何合併幾何。 可能值<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>屬性： <xref:System.Windows.Media.GeometryCombineMode.Union>， <xref:System.Windows.Media.GeometryCombineMode.Intersect>， <xref:System.Windows.Media.GeometryCombineMode.Exclude>，和<xref:System.Windows.Media.GeometryCombineMode.Xor>。  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義使用 Union 合併模式。  兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Union 合併模式的結果](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義的合併模式<xref:System.Windows.Media.GeometryCombineMode.Xor>。  兩者<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>而<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>定義為圓形的半徑相同，但中心位移 50。  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 如需其他範例，請參閱[建立複合圖案](how-to-create-a-composite-shape.md)和[建立合併幾何](how-to-create-a-combined-geometry.md)。  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable 功能  
 因為它繼承自<xref:System.Windows.Freezable>類別，<xref:System.Windows.Media.Geometry>類別提供數個特殊功能︰<xref:System.Windows.Media.Geometry>物件可以宣告為[XAML 資源](../advanced/xaml-resources.md)、 多個物件，成為唯讀，以改善在共用效能、 複製，並變更為安全執行緒。 如需詳細資訊，所提供的不同功能的相關<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../advanced/freezable-objects-overview.md)。  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>其他幾何功能  
 <xref:System.Windows.Media.Geometry>類別也會提供實用的公用程式方法，如下所示：  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> -取得區域<xref:System.Windows.Media.Geometry>。  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> -判斷幾何是否包含另一個<xref:System.Windows.Media.Geometry>。  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> -決定是否筆劃的<xref:System.Windows.Media.Geometry>包含指定的點。  
  
 請參閱<xref:System.Windows.Media.Geometry>類別及其方法的完整清單。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D 圖形和影像處理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [路徑標記語法](path-markup-syntax.md)
- [HOW-TO 主題](geometries-how-to-topics.md)
- [動畫概觀](animation-overview.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [繪圖物件概觀](drawing-objects-overview.md)
