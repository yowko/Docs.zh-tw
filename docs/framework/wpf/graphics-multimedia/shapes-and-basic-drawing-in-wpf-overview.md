---
title: WPF 中圖案和基本繪圖概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: adbf982da25ff445d277b7c1b5911217d9825c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566307"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="01494-102">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="01494-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="01494-103">本主題概要說明如何繪製具有<xref:System.Windows.Shapes.Shape>物件。</span><span class="sxs-lookup"><span data-stu-id="01494-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="01494-104">A<xref:System.Windows.Shapes.Shape>是一種<xref:System.Windows.UIElement>，可讓您繪製圖形至螢幕。</span><span class="sxs-lookup"><span data-stu-id="01494-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="01494-105">UI 項目，因為<xref:System.Windows.Shapes.Shape>物件可以用內<xref:System.Windows.Controls.Panel>項目和大部分的控制項。</span><span class="sxs-lookup"><span data-stu-id="01494-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="01494-106"> 提供了數層的圖形和轉譯服務存取權。</span><span class="sxs-lookup"><span data-stu-id="01494-106"> offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="01494-107">位於最上層<xref:System.Windows.Shapes.Shape>物件很容易使用，並提供許多有用的功能，例如版面配置和參與[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]事件系統。</span><span class="sxs-lookup"><span data-stu-id="01494-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="01494-108">Shape 物件</span><span class="sxs-lookup"><span data-stu-id="01494-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="01494-109"> 提供數個已備妥要使用<xref:System.Windows.Shapes.Shape>物件。</span><span class="sxs-lookup"><span data-stu-id="01494-109"> provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="01494-110">圖形的所有物件都繼承自<xref:System.Windows.Shapes.Shape>類別。</span><span class="sxs-lookup"><span data-stu-id="01494-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="01494-111">可用的圖形物件包括<xref:System.Windows.Shapes.Ellipse>， <xref:System.Windows.Shapes.Line>， <xref:System.Windows.Shapes.Path>， <xref:System.Windows.Shapes.Polygon>， <xref:System.Windows.Shapes.Polyline>，和<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="01494-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="01494-112"><xref:System.Windows.Shapes.Shape> 物件共用的下列通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="01494-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
-   <span data-ttu-id="01494-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>： 描述如何繪製圖形外框。</span><span class="sxs-lookup"><span data-stu-id="01494-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
-   <span data-ttu-id="01494-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>： 描述圖形外框粗細。</span><span class="sxs-lookup"><span data-stu-id="01494-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
-   <span data-ttu-id="01494-115"><xref:System.Windows.Shapes.Shape.Fill%2A>： 描述的圖案內部的繪製方式。</span><span class="sxs-lookup"><span data-stu-id="01494-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
-   <span data-ttu-id="01494-116">用來指定座標和頂點的資料屬性，以裝置獨立像素為單位。</span><span class="sxs-lookup"><span data-stu-id="01494-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="01494-117">因為它們衍生自<xref:System.Windows.UIElement>，圖形物件都可以使用面板中，大部分的控制項。</span><span class="sxs-lookup"><span data-stu-id="01494-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="01494-118"><xref:System.Windows.Controls.Canvas>面板是特別是不錯的選擇來建立複雜的繪圖，因為它支援絕對定位子物件。</span><span class="sxs-lookup"><span data-stu-id="01494-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="01494-119"><xref:System.Windows.Shapes.Line>類別可讓您在兩個點之間繪製一條線。</span><span class="sxs-lookup"><span data-stu-id="01494-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="01494-120">下列範例示範用來指定線段座標和筆觸屬性的數種方法。</span><span class="sxs-lookup"><span data-stu-id="01494-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="01494-121">下圖顯示轉譯<xref:System.Windows.Shapes.Line>。</span><span class="sxs-lookup"><span data-stu-id="01494-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="01494-122">![線段圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="01494-122">![Line illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="01494-123">雖然<xref:System.Windows.Shapes.Line>類別並提供<xref:System.Windows.Shapes.Shape.Fill%2A>屬性，並將它沒有任何作用，因為<xref:System.Windows.Shapes.Line>不有任何區域。</span><span class="sxs-lookup"><span data-stu-id="01494-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="01494-124">另一個常見的圖案會<xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="01494-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="01494-125">建立<xref:System.Windows.Shapes.Ellipse>藉由定義圖形的<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="01494-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="01494-126">若要繪製圓形，指定<xref:System.Windows.Shapes.Ellipse>其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>值是否相等。</span><span class="sxs-lookup"><span data-stu-id="01494-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="01494-127">下圖顯示的轉譯範例<xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="01494-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="01494-128">![橢圓形圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="01494-128">![Ellipse illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="01494-129">使用路徑和幾何</span><span class="sxs-lookup"><span data-stu-id="01494-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="01494-130"><xref:System.Windows.Shapes.Path>類別可讓您繪製曲線，以及複雜的圖形。</span><span class="sxs-lookup"><span data-stu-id="01494-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="01494-131">這些曲線和形狀說明使用<xref:System.Windows.Media.Geometry>物件。</span><span class="sxs-lookup"><span data-stu-id="01494-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="01494-132">若要使用<xref:System.Windows.Shapes.Path>，您建立<xref:System.Windows.Media.Geometry>並用它來設定<xref:System.Windows.Shapes.Path>物件的<xref:System.Windows.Shapes.Path.Data%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="01494-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="01494-133">有各種不同的<xref:System.Windows.Media.Geometry>可從中選擇的物件。</span><span class="sxs-lookup"><span data-stu-id="01494-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="01494-134"><xref:System.Windows.Media.LineGeometry>， <xref:System.Windows.Media.RectangleGeometry>，和<xref:System.Windows.Media.EllipseGeometry>類別描述相當簡單的圖形。</span><span class="sxs-lookup"><span data-stu-id="01494-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="01494-135">若要建立更複雜的圖形，或建立的曲線，使用<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="01494-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="01494-136">PathGeometry 和 PathSegments</span><span class="sxs-lookup"><span data-stu-id="01494-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="01494-137"><xref:System.Windows.Media.PathGeometry> 物件會組成一或多個<xref:System.Windows.Media.PathFigure>物件; 每一個<xref:System.Windows.Media.PathFigure>代表不同的 「 圖 」 或圖形。</span><span class="sxs-lookup"><span data-stu-id="01494-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="01494-138">每個<xref:System.Windows.Media.PathFigure>本身包含一或多個<xref:System.Windows.Media.PathSegment>物件，分別代表連接圖或形狀圖的一部分。</span><span class="sxs-lookup"><span data-stu-id="01494-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="01494-139">區段類型包括下列： <xref:System.Windows.Media.LineSegment>， <xref:System.Windows.Media.BezierSegment>，和<xref:System.Windows.Media.ArcSegment>。</span><span class="sxs-lookup"><span data-stu-id="01494-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="01494-140">在下列範例中，<xref:System.Windows.Shapes.Path>用來繪製二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="01494-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="01494-141">下列影像顯示轉譯的圖形。</span><span class="sxs-lookup"><span data-stu-id="01494-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="01494-142">![路徑圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="01494-142">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="01494-143">如需有關<xref:System.Windows.Media.PathGeometry>和其他<xref:System.Windows.Media.Geometry>類別，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="01494-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="01494-144">XAML 縮寫語法</span><span class="sxs-lookup"><span data-stu-id="01494-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="01494-145">在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您也可以使用特殊的縮寫的語法來描述<xref:System.Windows.Shapes.Path>。</span><span class="sxs-lookup"><span data-stu-id="01494-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="01494-146">在下列範例中，縮寫語法是用來繪製複雜的圖形。</span><span class="sxs-lookup"><span data-stu-id="01494-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="01494-147">下圖顯示轉譯<xref:System.Windows.Shapes.Path>。</span><span class="sxs-lookup"><span data-stu-id="01494-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="01494-148">![路徑圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="01494-148">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="01494-149"><xref:System.Windows.Shapes.Path.Data%2A>屬性字串開頭為"moveto"命令，以建立路徑的起點座標系統中的指示，m， <xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="01494-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="01494-150"><xref:System.Windows.Shapes.Path> 資料參數會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="01494-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="01494-151">大寫 M 表示新的目前端點的絕對位置。</span><span class="sxs-lookup"><span data-stu-id="01494-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="01494-152">小寫 m 則表示相對座標。</span><span class="sxs-lookup"><span data-stu-id="01494-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="01494-153">第一個線段是三次方貝茲曲線，開始於 (100,200) 並結束於 (400,175)，使用 (100,25) 和 (400,350) 這兩個控制點繪製。</span><span class="sxs-lookup"><span data-stu-id="01494-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="01494-154">此區段會以 C 命令中<xref:System.Windows.Shapes.Path.Data%2A>屬性字串。</span><span class="sxs-lookup"><span data-stu-id="01494-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="01494-155">同樣地，大寫 C 表示絕對路徑；小寫 c 表示相對路徑。</span><span class="sxs-lookup"><span data-stu-id="01494-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="01494-156">第二個線段的開頭為絕對水平 "lineto" 命令 H，它會指定從前面的子路徑的端點 (400,175) 到新端點 (280,175) 繪製的線段。</span><span class="sxs-lookup"><span data-stu-id="01494-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="01494-157">指定的值是水平 「 lineto"命令，因為是*x*-協調。</span><span class="sxs-lookup"><span data-stu-id="01494-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="01494-158">如需完整的路徑語法，請參閱<xref:System.Windows.Shapes.Path.Data%2A>參考和[建立圖形使用 PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)。</span><span class="sxs-lookup"><span data-stu-id="01494-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="01494-159">繪製圖形</span><span class="sxs-lookup"><span data-stu-id="01494-159">Painting Shapes</span></span>  
 <span data-ttu-id="01494-160"><xref:System.Windows.Media.Brush> 物件用來繪製圖形的<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="01494-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="01494-161">在下列範例，筆觸與填滿的<xref:System.Windows.Shapes.Ellipse>所指定。</span><span class="sxs-lookup"><span data-stu-id="01494-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="01494-162">請注意，筆刷屬性的有效輸入可以是關鍵字或十六進位色彩值。</span><span class="sxs-lookup"><span data-stu-id="01494-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="01494-163">如需可用的色彩關鍵字的詳細資訊，請參閱屬性<xref:System.Windows.Media.Colors>類別<xref:System.Windows.Media>命名空間。</span><span class="sxs-lookup"><span data-stu-id="01494-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
```  
<Canvas Background="LightGray">   
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 <span data-ttu-id="01494-164">下圖顯示轉譯<xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="01494-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="01494-165">![橢圓形](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="01494-165">![An ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="01494-166">或者，您可以使用屬性項目語法明確建立<xref:System.Windows.Media.SolidColorBrush>來繪製圖形使用純色的物件。</span><span class="sxs-lookup"><span data-stu-id="01494-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
```  
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"   
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 <span data-ttu-id="01494-167">下圖顯示轉譯的圖形。</span><span class="sxs-lookup"><span data-stu-id="01494-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="01494-168">![SolidColorBrush 圖例](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="01494-168">![SolidColorBrush illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="01494-169">您也可以使用漸層、影像、圖樣等等繪製圖形的筆觸或填滿。</span><span class="sxs-lookup"><span data-stu-id="01494-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="01494-170">如需詳細資訊，請參閱[使用單色和漸層概觀繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="01494-170">For more information, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="01494-171">可縮放的圖形</span><span class="sxs-lookup"><span data-stu-id="01494-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="01494-172"><xref:System.Windows.Shapes.Line>， <xref:System.Windows.Shapes.Path>， <xref:System.Windows.Shapes.Polygon>， <xref:System.Windows.Shapes.Polyline>，和<xref:System.Windows.Shapes.Rectangle>類別都有<xref:System.Windows.Shapes.Shape.Stretch%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="01494-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="01494-173">此屬性會決定如何<xref:System.Windows.Shapes.Shape>物件的內容 （要繪製的圖形） 延伸以填滿<xref:System.Windows.Shapes.Shape>物件的配置空間。</span><span class="sxs-lookup"><span data-stu-id="01494-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="01494-174">A<xref:System.Windows.Shapes.Shape>物件的配置空間是空間數量<xref:System.Windows.Shapes.Shape>配置版面配置系統，是因為明確<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>設定或因為其<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="01494-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="01494-175">如需有關 Windows Presentation Foundation 中的版面配置的詳細資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)概觀。</span><span class="sxs-lookup"><span data-stu-id="01494-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../../../../docs/framework/wpf/advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="01494-176">Stretch 屬性可接受下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="01494-176">The Stretch property takes one of the following values:</span></span>  
  
-   <span data-ttu-id="01494-177"><xref:System.Windows.Media.Stretch.None>:<xref:System.Windows.Shapes.Shape>物件的內容不會自動縮放。</span><span class="sxs-lookup"><span data-stu-id="01494-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
-   <span data-ttu-id="01494-178"><xref:System.Windows.Media.Stretch.Fill>:<xref:System.Windows.Shapes.Shape>物件的內容則會伸展以填滿其配置空間。</span><span class="sxs-lookup"><span data-stu-id="01494-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="01494-179">不會維持外觀比例。</span><span class="sxs-lookup"><span data-stu-id="01494-179">Aspect ratio is not preserved.</span></span>  
  
-   <span data-ttu-id="01494-180"><xref:System.Windows.Media.Stretch.Uniform>:<xref:System.Windows.Shapes.Shape>物件的內容則會伸展盡可能以填滿其配置空間，同時維持原始外觀比例。</span><span class="sxs-lookup"><span data-stu-id="01494-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
-   <span data-ttu-id="01494-181"><xref:System.Windows.Media.Stretch.UniformToFill>:<xref:System.Windows.Shapes.Shape>物件的內容則會伸展成完全填滿其配置空間，同時維持原始外觀比例。</span><span class="sxs-lookup"><span data-stu-id="01494-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="01494-182">請注意，當<xref:System.Windows.Shapes.Shape>物件的內容則會伸展，<xref:System.Windows.Shapes.Shape>之後自動縮放物件的外框繪製。</span><span class="sxs-lookup"><span data-stu-id="01494-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="01494-183">在下列範例中，<xref:System.Windows.Shapes.Polygon>用來繪製 (0，1) 非常小三角形 (0，0) 到 (1，1)。</span><span class="sxs-lookup"><span data-stu-id="01494-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="01494-184"><xref:System.Windows.Shapes.Polygon>物件的<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>設為 100，和其 stretch 屬性設定為填滿。</span><span class="sxs-lookup"><span data-stu-id="01494-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="01494-185">如此一來，<xref:System.Windows.Shapes.Polygon>物件的內容 （三角形） 則會伸展以填滿較大的空間。</span><span class="sxs-lookup"><span data-stu-id="01494-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
...  
```  
  
<a name="transforms"></a>   
## <a name="transforming-shapes"></a><span data-ttu-id="01494-186">轉換圖形</span><span class="sxs-lookup"><span data-stu-id="01494-186">Transforming Shapes</span></span>  
 <span data-ttu-id="01494-187"><xref:System.Windows.Media.Transform>類別會提供方法來轉換二維平面中的圖形。</span><span class="sxs-lookup"><span data-stu-id="01494-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="01494-188">不同類型的轉換包含旋轉 (<xref:System.Windows.Media.RotateTransform>)，小數位數 (<xref:System.Windows.Media.ScaleTransform>)、 扭曲 (<xref:System.Windows.Media.SkewTransform>)，和轉譯 (<xref:System.Windows.Media.TranslateTransform>)。</span><span class="sxs-lookup"><span data-stu-id="01494-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="01494-189">套用至圖形的一種常用轉換就是旋轉。</span><span class="sxs-lookup"><span data-stu-id="01494-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="01494-190">若要旋轉圖形，請建立<xref:System.Windows.Media.RotateTransform>並指定其<xref:System.Windows.Media.RotateTransform.Angle%2A>。</span><span class="sxs-lookup"><span data-stu-id="01494-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="01494-191"><xref:System.Windows.Media.RotateTransform.Angle%2A> 45 的項目旋轉 45 度旋轉; 角度為 90 項目方向旋轉 90 度順時針旋轉，則為，依此類推。</span><span class="sxs-lookup"><span data-stu-id="01494-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="01494-192">設定<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性，如果您想要控制哪些項目會旋轉的點。</span><span class="sxs-lookup"><span data-stu-id="01494-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="01494-193">這些屬性值會以轉換之元素的座標空間表示。</span><span class="sxs-lookup"><span data-stu-id="01494-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="01494-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> 和<xref:System.Windows.Media.RotateTransform.CenterY%2A>有預設值為零。</span><span class="sxs-lookup"><span data-stu-id="01494-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="01494-195">最後，套用<xref:System.Windows.Media.RotateTransform>的項目。</span><span class="sxs-lookup"><span data-stu-id="01494-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="01494-196">如果您不想要影響版面配置的轉換，將圖形的<xref:System.Windows.UIElement.RenderTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="01494-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="01494-197">在下列範例中，<xref:System.Windows.Media.RotateTransform>用於圖形的左上角 (0，0) 的相關圖形 45 度旋轉。</span><span class="sxs-lookup"><span data-stu-id="01494-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="01494-198">在下一個範例中，另一個圖形也旋轉 45 度，但這次是從點 (25,50) 旋轉。</span><span class="sxs-lookup"><span data-stu-id="01494-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="01494-199">下圖顯示套用兩種轉換的結果。</span><span class="sxs-lookup"><span data-stu-id="01494-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="01494-200">![不同中心點的 45 度旋轉](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="01494-200">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="01494-201">在上一個範例中，已將單一轉換套用至每個圖形物件。</span><span class="sxs-lookup"><span data-stu-id="01494-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="01494-202">若要將多個轉換套用至圖形 （或其他 UI 項目），使用<xref:System.Windows.Media.TransformGroup>。</span><span class="sxs-lookup"><span data-stu-id="01494-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01494-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01494-203">See Also</span></span>  
 [<span data-ttu-id="01494-204">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="01494-204">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="01494-205">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="01494-205">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="01494-206">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="01494-206">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="01494-207">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="01494-207">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [<span data-ttu-id="01494-208">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="01494-208">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
