---
title: "幾何概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a10e74342141f8ef6664cc424552dc173d9b0f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="geometry-overview"></a>幾何概觀
本概觀說明如何使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Media.Geometry>類別來描述圖形。 本主題也會對照之間的差異<xref:System.Windows.Media.Geometry>物件和<xref:System.Windows.Shapes.Shape>項目。  
  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>什麼是幾何？  
 <xref:System.Windows.Media.Geometry>類別及類別衍生自它，例如<xref:System.Windows.Media.EllipseGeometry>， <xref:System.Windows.Media.PathGeometry>，和<xref:System.Windows.Media.CombinedGeometry>，讓您描述 2d 圖案的幾何。 這些幾何描繪有許多用途，像是定義圖形來繪製到螢幕或定義點擊測試和裁剪區域。 您甚至可以使用幾何來定義動畫路徑。  
  
 <xref:System.Windows.Media.Geometry>物件可以是簡單，例如矩形和圓形或複合，建立的兩個或多個幾何物件。  可以使用來建立更複雜的幾何<xref:System.Windows.Media.PathGeometry>和<xref:System.Windows.Media.StreamGeometry>類別，可讓您描述弧形和曲線。  
  
 因為<xref:System.Windows.Media.Geometry>是一種<xref:System.Windows.Freezable>，<xref:System.Windows.Media.Geometry>物件提供數個特殊功能： 它們可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、 變成唯讀，以改善效能，複製的多個物件之間共用，進行安全執行緒。 如需有關所提供的不同功能<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>幾何與圖形  
 <xref:System.Windows.Media.Geometry>和<xref:System.Windows.Shapes.Shape>類別似乎類似，因為它們都描述 2d 圖案 (比較<xref:System.Windows.Media.EllipseGeometry>和<xref:System.Windows.Shapes.Ellipse>例如)，但有一些重要的差異。  
  
 例如，<xref:System.Windows.Media.Geometry>類別繼承自<xref:System.Windows.Freezable>類別時<xref:System.Windows.Shapes.Shape>類別繼承自<xref:System.Windows.FrameworkElement>。 因為它們是項目，<xref:System.Windows.Shapes.Shape>物件可以呈現自己，並參與配置系統，而<xref:System.Windows.Media.Geometry>物件不能。  
  
 雖然<xref:System.Windows.Shapes.Shape>物件可更輕易地比<xref:System.Windows.Media.Geometry>物件<xref:System.Windows.Media.Geometry>物件是更多功能。 雖然<xref:System.Windows.Shapes.Shape>物件用來轉譯 2d 圖形<xref:System.Windows.Media.Geometry>物件可以用來定義的 2d 圖形幾何的區域、 定義區域的剪輯，或定義的區域點擊測試，例如。  
  
### <a name="the-path-shape"></a>路徑圖形  
 一個<xref:System.Windows.Shapes.Shape>、<xref:System.Windows.Shapes.Path>類別，實際上會使用<xref:System.Windows.Media.Geometry>來描述其內容。 藉由設定<xref:System.Windows.Shapes.Path.Data%2A>屬性<xref:System.Windows.Shapes.Path>與<xref:System.Windows.Media.Geometry>並設定其<xref:System.Windows.Shapes.Shape.Fill%2A>和<xref:System.Windows.Shapes.Shape.Stroke%2A>屬性，您可以轉譯<xref:System.Windows.Media.Geometry>。  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>採用幾何的通用屬性  
 如前幾節所述，Geometry 物件可以與其他物件一起用於許多用途，例如繪製圖形、動畫以及裁剪。 下表列出數個類別，其屬性可接受<xref:System.Windows.Media.Geometry>物件。  
  
|類型|屬性|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>簡單幾何類型  
 所有的幾何的基底類別是抽象類別<xref:System.Windows.Media.Geometry>。  衍生自類別<xref:System.Windows.Media.Geometry>類別可以大致分為三個類別： 簡單的幾何、 路徑幾何和複合幾何。  
  
 簡單的幾何類別包括<xref:System.Windows.Media.LineGeometry>， <xref:System.Windows.Media.RectangleGeometry>，和<xref:System.Windows.Media.EllipseGeometry>，並用來建立基本的幾何圖案，例如線條、 矩形和圓形。  
  
-   A<xref:System.Windows.Media.LineGeometry>由指定線條和點的起始點。  
  
-   A<xref:System.Windows.Media.RectangleGeometry>定義<xref:System.Windows.Rect>結構會指定其相對位置，其高度和寬度。 您可以設定來建立圓角的矩形<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>屬性。  
  
-   <xref:System.Windows.Media.EllipseGeometry>中心點、 半徑 x 和 y 軸半徑所定義。  下列範例示範如何建立簡單的幾何以用於轉譯和裁剪。  
  
 這些相同的圖形，以及更複雜的圖形，您可以使用建立<xref:System.Windows.Media.PathGeometry>或藉由結合幾何物件放在一起，而這些類別提供簡單的方式來產生這些基本的幾何圖形。  
  
 下列範例示範如何建立及呈現<xref:System.Windows.Media.LineGeometry>。  如前所述，<xref:System.Windows.Media.Geometry>物件是無法繪製本身，所以此範例會使用<xref:System.Windows.Shapes.Path>來呈現線條的圖形。  由於一條線會不有任何區域，所以將<xref:System.Windows.Shapes.Shape.Fill%2A>屬性<xref:System.Windows.Shapes.Path>會有任何影響; 相反地，只有<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>指定屬性。 下圖顯示範例的輸出。  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
從 (10,20) 繪製到 (100,130) 的 LineGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 下一個範例示範如何建立及呈現<xref:System.Windows.Media.EllipseGeometry>。  範例集<xref:System.Windows.Media.EllipseGeometry.Center%2A>的<xref:System.Windows.Media.EllipseGeometry>設為點`50,50`和半徑 x 和 y 軸半徑都設定為`50`，可建立以 100 的直徑的圓形。  在此情況下將此值指派給路徑元素的填滿屬性，繪製橢圓形內部<xref:System.Windows.Media.Brushes.Gold%2A>。 下圖顯示範例的輸出。  
  
 ![EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
在 (50,50) 繪製的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 下列範例示範如何建立及呈現<xref:System.Windows.Media.RectangleGeometry>。  所定義的位置與矩形的維度<xref:System.Windows.Rect>結構。 這個位置是`50,50`，而高度和寬度都是 `25`，可建立一個正方形。 下圖顯示範例的輸出。  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
在 50,50 繪製的 RectangleGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 下列範例示範如何使用<xref:System.Windows.Media.EllipseGeometry>做為映像的裁剪區域。  <xref:System.Windows.Controls.Image>物件定義與<xref:System.Windows.FrameworkElement.Width%2A>為 200 和<xref:System.Windows.FrameworkElement.Height%2A>的 150。  <xref:System.Windows.Media.EllipseGeometry>與<xref:System.Windows.Media.EllipseGeometry.RadiusX%2A>值為 100，<xref:System.Windows.Media.EllipseGeometry.RadiusY%2A>值 75，和<xref:System.Windows.Media.EllipseGeometry.Center%2A>100,75 的值設定為<xref:System.Windows.UIElement.Clip%2A>映像的屬性。  只有橢圓形區域內的影像部分才會顯示。 下圖顯示範例的輸出。  
  
 ![映像，而不裁剪](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
用來裁剪影像控制項的 EllipseGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>路徑幾何  
 <xref:System.Windows.Media.PathGeometry>類別和其輕量級對等項目，<xref:System.Windows.Media.StreamGeometry>類別，提供方法來描述多個複雜的數字組成弧線、 曲線和行。  
  
 核心<xref:System.Windows.Media.PathGeometry>是一組<xref:System.Windows.Media.PathFigure>物件，因此如此命名，因為每個圖將說明中的離散圖形<xref:System.Windows.Media.PathGeometry>。 每個<xref:System.Windows.Media.PathFigure>本身包含一或多個<xref:System.Windows.Media.PathSegment>物件，其中每個描述圖的區段。  
  
 區段的類型繁多。  
  
|區段類型|描述|範例|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|在兩個點之間建立橢圓形弧線。|[建立橢圓形弧線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)。|  
|<xref:System.Windows.Media.BezierSegment>|在兩個點之間建立三次方貝茲曲線。|[建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)。|  
|<xref:System.Windows.Media.LineSegment>|在兩個點之間建立線條。|[在 PathGeometry 中建立 LineSegment](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|建立一系列三次方貝茲曲線。|請參閱<xref:System.Windows.Media.PolyBezierSegment>類型 頁面。|  
|<xref:System.Windows.Media.PolyLineSegment>|建立一系列的線條。|請參閱<xref:System.Windows.Media.PolyLineSegment>類型 頁面。|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|建立一系列二次方貝茲曲線。|請參閱<xref:System.Windows.Media.PolyQuadraticBezierSegment>頁面。|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|建立二次方貝茲曲線。|[建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)。|  
  
 內的區段<xref:System.Windows.Media.PathFigure>組合成單一的幾何形狀的下一個區段的開始點的每個區段的結束點。 <xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性<xref:System.Windows.Media.PathFigure>指定從中繪製的第一個區段的點。 每個後續區段都會從前一個區段的結束點開始。 比方說，從垂直線`10,50`至`10,150`可以藉由設定定義<xref:System.Windows.Media.PathFigure.StartPoint%2A>屬性`10,50`和建立<xref:System.Windows.Media.LineSegment>與<xref:System.Windows.Media.LineSegment.Point%2A>屬性設定為`10,150`。  
  
 下列範例會建立簡單<xref:System.Windows.Media.PathGeometry>組成單一<xref:System.Windows.Media.PathFigure>與<xref:System.Windows.Media.LineSegment>，並顯示使用<xref:System.Windows.Shapes.Path>項目。 <xref:System.Windows.Media.PathFigure>物件的<xref:System.Windows.Media.PathFigure.StartPoint%2A>設`10,20`和<xref:System.Windows.Media.LineSegment>的結束點定義`100,130`。 下圖顯示<xref:System.Windows.Media.PathGeometry>此範例所建立。  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
包含單一 LineSegment 的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 值得對照此範例與前一個<xref:System.Windows.Media.LineGeometry>範例。  所使用的語法<xref:System.Windows.Media.PathGeometry>會比使用簡單的更詳細資訊<xref:System.Windows.Media.LineGeometry>，以及它可能會比較合理使用<xref:System.Windows.Media.LineGeometry>在此情況下，類別的詳細語法但<xref:System.Windows.Media.PathGeometry>允許極複雜且複雜幾何的區域。  
  
 可以使用的組合來建立更複雜的幾何<xref:System.Windows.Media.PathSegment>物件。  
  
 下一個範例會使用<xref:System.Windows.Media.BezierSegment>、 <xref:System.Windows.Media.LineSegment>，和<xref:System.Windows.Media.ArcSegment>建立圖形。 此範例會先建立三次方貝茲曲線會藉由定義四個點： 起始點，也就是上一個區段結束點的結束點 (<xref:System.Windows.Media.BezierSegment.Point3%2A>)，和兩個控制點 (<xref:System.Windows.Media.BezierSegment.Point1%2A>和<xref:System.Windows.Media.BezierSegment.Point2%2A>)。  三次方貝茲曲線的兩個控制點作用類似磁鐵，吸引原本為直線的部分，產生曲線。 第一個控制點， <xref:System.Windows.Media.BezierSegment.Point1%2A>，會影響開頭曲線部分; 的第二個控制點<xref:System.Windows.Media.BezierSegment.Point2%2A>，會影響曲線的結束部分。  
  
 然後此範例會將<xref:System.Windows.Media.LineSegment>，這先前的結束點之間繪製<xref:System.Windows.Media.BezierSegment>的前面所指定的點上其<xref:System.Windows.Media.LineSegment>屬性。  
  
 此範例會接著將<xref:System.Windows.Media.ArcSegment>，這會從先前的結束點繪製<xref:System.Windows.Media.LineSegment>所指定的點其<xref:System.Windows.Media.ArcSegment.Point%2A>屬性。 此範例也會指定弧線的 x 和 y 半徑 (<xref:System.Windows.Media.ArcSegment.Size%2A>)，旋轉角度 (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>)、 旗標，指出產生弧線的角度應該大 (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>)，以及指出繪製弧形方向的值 (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). 下圖顯示此範例所建立的圖形。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 使用多個可以建立更複雜的幾何<xref:System.Windows.Media.PathFigure>物件內<xref:System.Windows.Media.PathGeometry>。  
  
 下列範例會建立<xref:System.Windows.Media.PathGeometry>具有兩個<xref:System.Windows.Media.PathFigure>物件，其中每一個都包含多個<xref:System.Windows.Media.PathSegment>物件。  <xref:System.Windows.Media.PathFigure>上述範例與<xref:System.Windows.Media.PathFigure>與<xref:System.Windows.Media.PolyLineSegment>和<xref:System.Windows.Media.QuadraticBezierSegment>可用。  A<xref:System.Windows.Media.PolyLineSegment>以點陣列所定義而<xref:System.Windows.Media.QuadraticBezierSegment>定義的控點與結束點。 下圖顯示此範例所建立的圖形。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.gif "graphicsmm_path")  
有多個圖形的 PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 像<xref:System.Windows.Media.PathGeometry>類別<xref:System.Windows.Media.StreamGeometry>定義曲線、 弧線和行可能包含複雜幾何圖案。 不同於<xref:System.Windows.Media.PathGeometry>，內容<xref:System.Windows.Media.StreamGeometry>不支援資料繫結、 動畫或修改。 使用<xref:System.Windows.Media.StreamGeometry>何時該添來描述複雜的幾何，但不是想支援資料繫結、 動畫或修改的額外負荷。 其效率，因為<xref:System.Windows.Media.StreamGeometry>類別是用來描述裝飾項不錯的選擇。  
  
 如需範例，請參閱[使用 StreamGeometry 建立圖形](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)。  
  
### <a name="path-markup-syntax"></a>路徑標記語法  
 <xref:System.Windows.Media.PathGeometry>和<xref:System.Windows.Media.StreamGeometry>型別支援[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]屬性使用特殊的一連串移動的語法，並繪製命令。 如需詳細資訊，請參閱[路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>複合幾何  
 您可以使用建立複合幾何物件<xref:System.Windows.Media.GeometryGroup>、 <xref:System.Windows.Media.CombinedGeometry>，或藉由呼叫靜態<xref:System.Windows.Media.Geometry>方法<xref:System.Windows.Media.Geometry.Combine%2A>。  
  
-   <xref:System.Windows.Media.CombinedGeometry>物件和<xref:System.Windows.Media.Geometry.Combine%2A>方法執行布林作業來結合兩個幾何所定義的區域。 <xref:System.Windows.Media.Geometry>物件具有不含區域都會被捨棄。 只有兩個<xref:System.Windows.Media.Geometry>物件可以組合 （雖然這些兩個幾何也可能是複合幾何）。  
  
-   <xref:System.Windows.Media.GeometryGroup>類別建立的 amalgamation<xref:System.Windows.Media.Geometry>而不將其區域的合併包含的物件。 任何數目的<xref:System.Windows.Media.Geometry>可以將物件加入至<xref:System.Windows.Media.GeometryGroup>。 如需範例，請參閱[建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)。  
  
 因為它們不會執行合併操作，使用<xref:System.Windows.Media.GeometryGroup>物件提供效能優勢，透過使用<xref:System.Windows.Media.CombinedGeometry>物件或<xref:System.Windows.Media.Geometry.Combine%2A>方法。  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>合併幾何  
 上一節中所述<xref:System.Windows.Media.CombinedGeometry>物件和<xref:System.Windows.Media.Geometry.Combine%2A>方法結合它們包含幾何所定義的區域。 <xref:System.Windows.Media.GeometryCombineMode>列舉值會指定如何結合幾何。 可能值<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>屬性： <xref:System.Windows.Media.GeometryCombineMode.Union>， <xref:System.Windows.Media.GeometryCombineMode.Intersect>， <xref:System.Windows.Media.GeometryCombineMode.Exclude>，和<xref:System.Windows.Media.GeometryCombineMode.Xor>。  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義使用 Union 合併模式。  同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Union 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry>定義合併模式<xref:System.Windows.Media.GeometryCombineMode.Xor>。  同時<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>和<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 所定義為圓形的半徑相同，但中心位移。  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 如需其他範例，請參閱[建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)和[建立合併幾何](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md)。  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable 功能  
 因為它繼承自<xref:System.Windows.Freezable>類別<xref:System.Windows.Media.Geometry>類別提供數個特殊功能：<xref:System.Windows.Media.Geometry>物件可以宣告為[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、 變成唯讀，以改善的多個物件之間共用效能考量，複製，而且進行安全執行緒。 如需有關所提供的不同功能<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>其他幾何功能  
 <xref:System.Windows.Media.Geometry>類別也提供有用的公用程式方法，如下所示：  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A>-取得的區域<xref:System.Windows.Media.Geometry>。  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A>-判斷 Geometry 是否包含另一個<xref:System.Windows.Media.Geometry>。  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A>-判斷是否的筆劃<xref:System.Windows.Media.Geometry>包含指定的點。  
  
 請參閱<xref:System.Windows.Media.Geometry>類別，其方法的完整清單。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Geometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
