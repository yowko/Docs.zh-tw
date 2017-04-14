---
title: "幾何概觀 | Microsoft Docs"
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
  - "類別, 幾何"
  - "CombinedGeometry 類別"
  - "EllipseGeometry 類別"
  - "幾何類別"
  - "圖形, 幾何類別"
  - "LineGeometry 類別"
  - "PathGeometry 類別"
  - "RectangleGeometry 類別"
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 幾何概觀
本概觀會說明如何使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> 類別描述圖案。  本主題也會比較 <xref:System.Windows.Media.Geometry> 物件與 <xref:System.Windows.Shapes.Shape> 項目之間的差異。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## 什麼是 Geometry？  
 <xref:System.Windows.Media.Geometry> 類別及其衍生類別 \(例如 <xref:System.Windows.Media.EllipseGeometry>、<xref:System.Windows.Media.PathGeometry> 以及 <xref:System.Windows.Media.CombinedGeometry>\) 讓您可以描述 2\-D 圖案的幾何。  這些幾何描述有許多用途，例如定義要繪製至螢幕的圖案或者定義點擊測試和裁剪區域。  您甚至可以使用幾何定義動畫路徑。  
  
 <xref:System.Windows.Media.Geometry> 物件可以是簡單的，例如矩形和圓形，或從兩個以上幾何物件建立的複合圖案。  <xref:System.Windows.Media.PathGeometry> 和 <xref:System.Windows.Media.StreamGeometry> 類別可以讓您描述弧線和曲線，因此可以用來建立更複雜的幾何。  
  
 因為 <xref:System.Windows.Media.Geometry> 是一種 <xref:System.Windows.Freezable>，所以 <xref:System.Windows.Media.Geometry> 物件可提供數項特殊功能：可以宣告為[資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、供多個物件共用、設成唯讀以提升效能、複製以及設成安全執行緒 \(Thread\-Safe\)。  如需 <xref:System.Windows.Freezable> 物件提供之不同功能的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## 比較幾何與形狀  
 <xref:System.Windows.Media.Geometry> 和 <xref:System.Windows.Shapes.Shape> 類別看似相同，因為它們都描述 2\-D 圖案 \(例如可以比較 <xref:System.Windows.Media.EllipseGeometry> 和 <xref:System.Windows.Shapes.Ellipse>\)，但是其實有相當重要的差別。  
  
 其中一個就是 <xref:System.Windows.Media.Geometry> 類別是繼承自 <xref:System.Windows.Freezable> 類別，而 <xref:System.Windows.Shapes.Shape> 類別則是繼承自 <xref:System.Windows.FrameworkElement>。  <xref:System.Windows.Shapes.Shape> 物件因為是項目，所以可以自行呈現並參與配置系統，但是 <xref:System.Windows.Media.Geometry> 物件不行。  
  
 雖然 <xref:System.Windows.Shapes.Shape> 物件比 <xref:System.Windows.Media.Geometry> 物件更實用，但是 <xref:System.Windows.Media.Geometry> 物件用途較廣。  <xref:System.Windows.Shapes.Shape> 物件是用於呈現 2\-D 圖形，而 <xref:System.Windows.Media.Geometry> 物件則可以用於定義 2\-D 圖形的幾何區域、定義裁剪的區域，或定義點擊測試 \(Hit Testing\) 區域等等。  
  
### 路徑圖案  
 有一個 <xref:System.Windows.Shapes.Shape> \(<xref:System.Windows.Shapes.Path> 類別\) 實際上會使用 <xref:System.Windows.Media.Geometry> 描述其內容。  藉由以 <xref:System.Windows.Media.Geometry> 設定 <xref:System.Windows.Shapes.Path> 的 <xref:System.Windows.Shapes.Path.Data%2A> 屬性，並且設定其 <xref:System.Windows.Shapes.Shape.Fill%2A> 和 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性，您可以呈現 <xref:System.Windows.Media.Geometry>。  
  
<a name="commonproperties"></a>   
## 常見接受 Geometry 的屬性  
 前面幾節曾提到 Geometry 物件可以與其他物件搭配用於各種目的，例如繪製圖案、建立動畫及裁剪。  下表列出數個類別，這些類別都具有會接受 <xref:System.Windows.Media.Geometry> 物件的屬性。  
  
|型別|屬性|  
|--------|--------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## 簡單幾何型別  
 所有幾何的基底類別都是抽象類別 <xref:System.Windows.Media.Geometry>。  從 <xref:System.Windows.Media.Geometry> 類別衍生的類別可以大略分為三類：簡單幾何、路徑幾何和複合幾何。  
  
 簡單幾何類別包括 <xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.RectangleGeometry> 和 <xref:System.Windows.Media.EllipseGeometry>，可用於建立基本幾何圖案，例如線條、矩形和圓形。  
  
-   定義 <xref:System.Windows.Media.LineGeometry> 的方法是指定線條的起始點和結束點。  
  
-   <xref:System.Windows.Media.RectangleGeometry> 是以 <xref:System.Windows.Rect> 結構定義，這個結構指定它的相對位置和高度與寬度。  您可以設定 <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> 和 <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> 屬性來建立圓角矩形。  
  
-   <xref:System.Windows.Media.EllipseGeometry> 是以中心點、X 半徑和 Y 半徑定義。  下列範例顯示如何建立用於呈現及裁剪的簡單幾何。  
  
 這些相同的圖案以及更複雜的圖案，可以透過 <xref:System.Windows.Media.PathGeometry> 來建立，或合併幾何物件來建立，但是這些類別可以提供簡單的方法來產生這些基本幾何圖案。  
  
 下列範例顯示如何建立和呈現 <xref:System.Windows.Media.LineGeometry>。  如同先前提及的，<xref:System.Windows.Media.Geometry> 物件本身無法進行繪製，所以範例使用 <xref:System.Windows.Shapes.Path> 圖案呈現線條。  因為線條沒有面積，所以設定 <xref:System.Windows.Shapes.Path> 的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性不會有效果，只要指定 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性即可。  下圖顯示的是範例的輸出。  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.png "graphicsmm\_line")  
從 \(10,20\) 繪製至 \(100,130\) 的 LineGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 下一個範例會顯示如何建立和呈現 <xref:System.Windows.Media.EllipseGeometry>。  範例中 <xref:System.Windows.Media.EllipseGeometry> 的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 會設定為 `50,50` 這個點，且 x 半徑和 y 半徑都會設定為 `50`，此設定會建立直徑為 100 的圓形。  橢圓形的內部是藉由將值 \(在這個案例中是 <xref:System.Windows.Media.Brushes.Gold%2A>\) 指定至 Path 項目的 Fill 屬性來繪製。  下圖顯示的是範例的輸出。  
  
 ![EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.png "graphicsmm\_ellipse")  
繪製在 \(50,50\) 的 EllipseGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 下列範例顯示如何建立和轉譯 <xref:System.Windows.Media.RectangleGeometry>。  矩形的位置和維度是由 <xref:System.Windows.Rect> 結構定義。  位置是 `50,50`，而高度和寬度都是 `25`，以建立正方形。  下圖顯示的是範例的輸出。  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.png "graphicsmm\_rectangle")  
繪製在 \(50,50\) 的 RectangleGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 下列範例顯示如何使用 <xref:System.Windows.Media.EllipseGeometry> 做為影像的裁剪區域。  <xref:System.Windows.Controls.Image> 物件的 <xref:System.Windows.FrameworkElement.Width%2A> 定義為 200 且 <xref:System.Windows.FrameworkElement.Height%2A> 定義為 150。  <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 值為 100、<xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> 值為 75 且 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 值為 100,75 的 <xref:System.Windows.Media.EllipseGeometry> 會設定為影像的 <xref:System.Windows.UIElement.Clip%2A> 屬性。  只會顯示在橢圓區域中的影像部分。  下圖顯示的是範例的輸出。  
  
 ![遭裁剪和未遭裁剪的影像](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm\_clipexample")  
用以裁剪 Image 控制項的 EllipseGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## 路徑幾何  
 <xref:System.Windows.Media.PathGeometry> 類別及其輕量型對等用法 \(<xref:System.Windows.Media.StreamGeometry> 類別\) 提供方法來描述由弧線、曲線及線條組成的多個複雜圖形。  
  
 <xref:System.Windows.Media.PathGeometry> 的核心是 <xref:System.Windows.Media.PathFigure> 物件的集合，會如此命名是因為每個圖形都會描述 <xref:System.Windows.Media.PathGeometry> 中的不同圖案。  每個 <xref:System.Windows.Media.PathFigure> 本身都是由一個或多個 <xref:System.Windows.Media.PathSegment> 物件組成，而每個物件都描述圖形的某一個區段。  
  
 區段有許多種。  
  
|區段類型|描述|範例|  
|----------|--------|--------|  
|<xref:System.Windows.Media.ArcSegment>|在兩點之間建立橢圓弧線。|[建立橢圓弧形](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|在兩點之間建立立方貝茲曲線。|[建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|在兩點之間建立線條。|[在 PathGeometry 中建立 LineSegment](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|建立一系列的立方貝茲曲線。|請參閱 <xref:System.Windows.Media.PolyBezierSegment> 型別頁面|  
|<xref:System.Windows.Media.PolyLineSegment>|建立一系列線條。|請參閱 <xref:System.Windows.Media.PolyLineSegment> 型別頁面|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|建立一系列二次方貝茲曲線。|請參閱 <xref:System.Windows.Media.PolyQuadraticBezierSegment> 頁面|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|建立一條二次方貝茲曲線。|[建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 <xref:System.Windows.Media.PathFigure> 中的區段可以合併成單一幾何圖案，其中每個區段的結束點都是下一個區段的起始點。  <xref:System.Windows.Media.PathFigure> 的 <xref:System.Windows.Media.PathFigure.StartPoint%2A> 屬性會指定繪製第一個區段的起點。  後續的區段再從前一個區段的終點開始。  例如，要定義 `10,50` 到 `10,150` 的垂直線，可以將 <xref:System.Windows.Media.PathFigure.StartPoint%2A> 屬性設為 `10,50`，然後建立 <xref:System.Windows.Media.LineSegment>，並將其 <xref:System.Windows.Media.LineSegment.Point%2A> 屬性設為 `10,150`。  
  
 下列範例會建立由單一 <xref:System.Windows.Media.PathFigure> \(含 <xref:System.Windows.Media.LineSegment>\) 組成的簡單 <xref:System.Windows.Media.PathGeometry>，並使用 <xref:System.Windows.Shapes.Path> 項目加以顯示。  <xref:System.Windows.Media.PathFigure> 物件的 <xref:System.Windows.Media.PathFigure.StartPoint%2A> 是設為 `10,20`，<xref:System.Windows.Media.LineSegment> 的結束點是定義為 `100,130`。  下圖顯示這個範例所建立的 <xref:System.Windows.Media.PathGeometry>。  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.png "graphicsmm\_line")  
包含單一 LineSegment 的 PathGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 這個範例可以和前述 <xref:System.Windows.Media.LineGeometry> 範例進行對照。  用於 <xref:System.Windows.Media.PathGeometry> 的語法比用於簡單 <xref:System.Windows.Media.LineGeometry> 的語法更為詳細，因此在這個案例中使用 <xref:System.Windows.Media.LineGeometry> 類別較為合理，不過 <xref:System.Windows.Media.PathGeometry> 的詳細語法可以提供極為精細和複雜的幾何區域。  
  
 更複雜的幾何可以藉由合併 <xref:System.Windows.Media.PathSegment> 物件來建立。  
  
 下一個範例會使用 <xref:System.Windows.Media.BezierSegment>、<xref:System.Windows.Media.LineSegment> 和 <xref:System.Windows.Media.ArcSegment> 建立圖案。  這個範例會先以定義四個點的方式建立三次方貝茲曲線，這四個點分別為：起始點 \(前一個區段的結束點\)、結束點 \(<xref:System.Windows.Media.BezierSegment.Point3%2A>\) 以及兩個控制點 \(<xref:System.Windows.Media.BezierSegment.Point1%2A> 和 <xref:System.Windows.Media.BezierSegment.Point2%2A>\)。  三次方貝茲曲線的兩個控制點就跟磁鐵一樣，會將原本為直線的部分吸引往它們靠近，最後形成曲線。  第一個控制點 <xref:System.Windows.Media.BezierSegment.Point1%2A> 會影響曲線的開始部分，而第二個控制點 <xref:System.Windows.Media.BezierSegment.Point2%2A> 則會影響曲線的結束部分。  
  
 然後範例會加入 <xref:System.Windows.Media.LineSegment>，這條線段是從它前面的上一個 <xref:System.Windows.Media.BezierSegment> 的結束點，繪製至它的 <xref:System.Windows.Media.LineSegment> 屬性指定的點。  
  
 然後範例會加入 <xref:System.Windows.Media.ArcSegment>，這條弧線是從上述的 <xref:System.Windows.Media.LineSegment> 的結束點繪製至它的 <xref:System.Windows.Media.ArcSegment.Point%2A> 屬性指定的點。  範例也會指定弧線的 X 和 Y 半徑 \(<xref:System.Windows.Media.ArcSegment.Size%2A>\)、旋轉角度 \(<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>\)、指出結果弧線角度大小的旗標 \(<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>\)，以及指出弧線繪製方向的值 \(<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>\)。  下圖顯示這個範例建立的圖案。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.png "graphicsmm\_path2")  
PathGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 即使是更複雜的幾何，也可以透過在 <xref:System.Windows.Media.PathGeometry> 內使用多個 <xref:System.Windows.Media.PathFigure> 物件來建立。  
  
 下列範例會建立 <xref:System.Windows.Media.PathGeometry>，它具有兩個 <xref:System.Windows.Media.PathFigure> 物件，而這兩個物件都包含多個 <xref:System.Windows.Media.PathSegment> 物件。  使用的有上述範例中的 <xref:System.Windows.Media.PathFigure>、具有 <xref:System.Windows.Media.PolyLineSegment> 的 <xref:System.Windows.Media.PathFigure>，以及 <xref:System.Windows.Media.QuadraticBezierSegment>。  <xref:System.Windows.Media.PolyLineSegment> 是以點的陣列定義，<xref:System.Windows.Media.QuadraticBezierSegment> 則是以控制點和結束點定義。  下圖顯示這個範例建立的圖案。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.png "graphicsmm\_path")  
具有多個圖形的 PathGeometry  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### StreamGeometry  
 與 <xref:System.Windows.Media.PathGeometry> 類別類似，<xref:System.Windows.Media.StreamGeometry> 會定義可能包含曲線、弧線及線條的複雜幾何圖案。  與 <xref:System.Windows.Media.PathGeometry> 不同，<xref:System.Windows.Media.StreamGeometry> 的內容不支援資料繫結、動畫或修改。  當您需要描述複雜幾何圖案，但是不想要有支援資料繫結、動畫或修改的額外負荷時，請使用 <xref:System.Windows.Media.StreamGeometry>。  <xref:System.Windows.Media.StreamGeometry> 類別因為十分具有效率，所以是描述裝飾項的好選擇。  
  
 如需範例，請參閱 [使用 StreamGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)。  
  
### 路徑標記語法  
 <xref:System.Windows.Media.PathGeometry> 和 <xref:System.Windows.Media.StreamGeometry> 型別支援一種[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 屬性語法，該語法使用一系列特殊的移動和繪製命令。  如需詳細資訊，請參閱 [路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)。  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## 複合幾何  
 複合幾何物件可以透過 <xref:System.Windows.Media.GeometryGroup> \(一種 <xref:System.Windows.Media.CombinedGeometry>\) 建立，或藉由呼叫靜態 <xref:System.Windows.Media.Geometry> 方法 <xref:System.Windows.Media.Geometry.Combine%2A> 來建立。  
  
-   <xref:System.Windows.Media.CombinedGeometry> 物件和 <xref:System.Windows.Media.Geometry.Combine%2A> 方法會執行布林運算，以合併由兩個幾何定義的區域。  沒有區域的 <xref:System.Windows.Media.Geometry> 物件會加以捨棄。  只有兩個 <xref:System.Windows.Media.Geometry> 物件可以合併 \(雖然這兩個幾何也可能是複合幾何\)。  
  
-   <xref:System.Windows.Media.GeometryGroup> 類別會建立所含 <xref:System.Windows.Media.Geometry> 物件的彙總，但不合併其區域。  任意數目的 <xref:System.Windows.Media.Geometry> 物件都可以加入至 <xref:System.Windows.Media.GeometryGroup>。  如需範例，請參閱 [建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)。  
  
 <xref:System.Windows.Media.GeometryGroup> 物件不會執行合併作業，因此使用這些物件會比使用 <xref:System.Windows.Media.CombinedGeometry> 物件或 <xref:System.Windows.Media.Geometry.Combine%2A> 方法更具效能優點。  
  
<a name="combindgeometriessection"></a>   
## 合併後的幾何  
 前面一節曾提到 <xref:System.Windows.Media.CombinedGeometry> 物件和 <xref:System.Windows.Media.Geometry.Combine%2A> 方法會將所含幾何所定義的區域合併。  <xref:System.Windows.Media.GeometryCombineMode> 列舉型別會指定幾何合併的方式。  <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> 屬性可能的值為：<xref:System.Windows.Media.GeometryCombineMode>、<xref:System.Windows.Media.GeometryCombineMode>、<xref:System.Windows.Media.GeometryCombineMode> 和 <xref:System.Windows.Media.GeometryCombineMode>。  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry> 是以 Union 合併模式定義。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但是中心相差 50。  
  
 [!code-xml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Union 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.png "mil\_task\_combined\_geometry\_union")  
  
 在下列範例中，<xref:System.Windows.Media.CombinedGeometry> 是以 <xref:System.Windows.Media.GeometryCombineMode> 合併模式定義。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> 和 <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> 都定義為相同半徑的圓形，但是中心相差 50。  
  
 [!code-xml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 合併模式的結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.png "mil\_task\_combined\_geometry\_xor")  
  
 如需其他範例，請參閱 [建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)和 [建立合併幾何](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md)。  
  
<a name="freezable_features"></a>   
## Freezable 功能  
 <xref:System.Windows.Media.Geometry> 類別繼承自 <xref:System.Windows.Freezable> 類別，因此可以提供數項特殊功能：<xref:System.Windows.Media.Geometry> 物件可以宣告為[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)、供多個物件共用、設成唯讀以提升效能、複製以及設成安全執行緒 \(Thread\-Safe\)。  如需 <xref:System.Windows.Freezable> 物件提供之不同功能的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
<a name="othergeometryfeatures"></a>   
## 其他 Geometry 功能  
 <xref:System.Windows.Media.Geometry> 類別也會提供有用的公用程式方法，例如下列方法：  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> \- 取得 <xref:System.Windows.Media.Geometry> 的區域。  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> \- 判斷 Geometry 是否包含其他 <xref:System.Windows.Media.Geometry>。  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> \- 判斷 <xref:System.Windows.Media.Geometry> 的描邊是否包含指定點。  
  
 如需 Geometry 方法的完整清單，請參閱 <xref:System.Windows.Media.Geometry>。  
  
## 請參閱  
 <xref:System.Windows.Media.Geometry>   
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.GeometryDrawing>   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [路徑標記語法](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)