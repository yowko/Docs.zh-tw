---
title: 圖形和基本繪圖總覽
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
ms.openlocfilehash: dfdbf67d35cbb13e80d0c5184f165b0cc660e2ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731617"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="cac16-102">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="cac16-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="cac16-103">本主題概述如何使用 <xref:System.Windows.Shapes.Shape> 物件繪製。</span><span class="sxs-lookup"><span data-stu-id="cac16-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="cac16-104"><xref:System.Windows.Shapes.Shape> 是一種 <xref:System.Windows.UIElement> 類型，可讓您在螢幕上繪製圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="cac16-105">因為它們是 UI 元素，所以 <xref:System.Windows.Shapes.Shape> 物件可以在 <xref:System.Windows.Controls.Panel> 元素和大部分控制項內使用。</span><span class="sxs-lookup"><span data-stu-id="cac16-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="cac16-106">提供了數層的圖形和轉譯服務存取權。</span><span class="sxs-lookup"><span data-stu-id="cac16-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="cac16-107">在最上層，<xref:System.Windows.Shapes.Shape> 物件很容易使用，並提供許多有用的功能，例如 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 事件系統中的版面配置和參與。</span><span class="sxs-lookup"><span data-stu-id="cac16-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="cac16-108">Shape 物件</span><span class="sxs-lookup"><span data-stu-id="cac16-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="cac16-109">提供許多現成可用的 <xref:System.Windows.Shapes.Shape> 物件。</span><span class="sxs-lookup"><span data-stu-id="cac16-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="cac16-110">所有繪圖物件都繼承自 <xref:System.Windows.Shapes.Shape> 類別。</span><span class="sxs-lookup"><span data-stu-id="cac16-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="cac16-111">可用的繪圖物件包括 <xref:System.Windows.Shapes.Ellipse>、<xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Path>、<xref:System.Windows.Shapes.Polygon>、<xref:System.Windows.Shapes.Polyline>和 <xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="cac16-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="cac16-112"><xref:System.Windows.Shapes.Shape> 物件共用下列通用屬性。</span><span class="sxs-lookup"><span data-stu-id="cac16-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="cac16-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>：描述圖形的外框繪製方式。</span><span class="sxs-lookup"><span data-stu-id="cac16-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="cac16-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>：描述圖形外框的粗細。</span><span class="sxs-lookup"><span data-stu-id="cac16-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="cac16-115"><xref:System.Windows.Shapes.Shape.Fill%2A>：描述圖形內部的繪製方式。</span><span class="sxs-lookup"><span data-stu-id="cac16-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="cac16-116">用來指定座標和頂點的資料屬性，以裝置獨立像素為單位。</span><span class="sxs-lookup"><span data-stu-id="cac16-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="cac16-117">因為它們是從 <xref:System.Windows.UIElement>衍生而來，所以繪圖物件可以在面板和大部分控制項內使用。</span><span class="sxs-lookup"><span data-stu-id="cac16-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="cac16-118">[<xref:System.Windows.Controls.Canvas> 面板] 特別適合用來建立複雜的繪圖，因為它支援其子物件的絕對位置。</span><span class="sxs-lookup"><span data-stu-id="cac16-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="cac16-119"><xref:System.Windows.Shapes.Line> 類別可讓您在兩個點之間繪製線條。</span><span class="sxs-lookup"><span data-stu-id="cac16-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="cac16-120">下列範例示範用來指定線段座標和筆觸屬性的數種方法。</span><span class="sxs-lookup"><span data-stu-id="cac16-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="cac16-121">下圖顯示呈現的 <xref:System.Windows.Shapes.Line>。</span><span class="sxs-lookup"><span data-stu-id="cac16-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="cac16-122">![線條圖例](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="cac16-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="cac16-123">雖然 <xref:System.Windows.Shapes.Line> 類別確實提供 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性，但設定不會有任何作用，因為 <xref:System.Windows.Shapes.Line> 沒有區域。</span><span class="sxs-lookup"><span data-stu-id="cac16-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="cac16-124">另一個常見的圖形是 <xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="cac16-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="cac16-125">藉由定義圖形的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性來建立 <xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="cac16-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="cac16-126">若要繪製圓形，請指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 值相等的 <xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="cac16-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="cac16-127">下圖顯示轉譯 <xref:System.Windows.Shapes.Ellipse>的範例。</span><span class="sxs-lookup"><span data-stu-id="cac16-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="cac16-128">![橢圓形圖例](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="cac16-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="cac16-129">使用路徑和幾何</span><span class="sxs-lookup"><span data-stu-id="cac16-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="cac16-130">[<xref:System.Windows.Shapes.Path>] 類別可讓您繪製曲線和複雜的圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="cac16-131">這些曲線和圖形會使用 <xref:System.Windows.Media.Geometry> 物件加以描述。</span><span class="sxs-lookup"><span data-stu-id="cac16-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="cac16-132">若要使用 <xref:System.Windows.Shapes.Path>，您可以建立 <xref:System.Windows.Media.Geometry>，並使用它來設定 <xref:System.Windows.Shapes.Path> 物件的 <xref:System.Windows.Shapes.Path.Data%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cac16-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="cac16-133">有各種不同的 <xref:System.Windows.Media.Geometry> 物件可供選擇。</span><span class="sxs-lookup"><span data-stu-id="cac16-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="cac16-134"><xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.RectangleGeometry>和 <xref:System.Windows.Media.EllipseGeometry> 類別會描述相當簡單的圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="cac16-135">若要建立更複雜的圖形或建立曲線，請使用 <xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="cac16-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="cac16-136">PathGeometry 和 PathSegments</span><span class="sxs-lookup"><span data-stu-id="cac16-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="cac16-137"><xref:System.Windows.Media.PathGeometry> 物件是由一或多個 <xref:System.Windows.Media.PathFigure> 物件所組成;每個 <xref:System.Windows.Media.PathFigure> 都代表不同的「圖形」或圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="cac16-138">每個 <xref:System.Windows.Media.PathFigure> 本身都是由一或多個 <xref:System.Windows.Media.PathSegment> 物件所組成，每個都代表圖表或圖形的連接部分。</span><span class="sxs-lookup"><span data-stu-id="cac16-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="cac16-139">區段類型包括下列各項： <xref:System.Windows.Media.LineSegment>、<xref:System.Windows.Media.BezierSegment>和 <xref:System.Windows.Media.ArcSegment>。</span><span class="sxs-lookup"><span data-stu-id="cac16-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="cac16-140">在下列範例中，會使用 <xref:System.Windows.Shapes.Path> 來繪製二次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="cac16-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="cac16-141">下列影像顯示轉譯的圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="cac16-142">![路徑圖例](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="cac16-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="cac16-143">如需 <xref:System.Windows.Media.PathGeometry> 和其他 <xref:System.Windows.Media.Geometry> 類別的詳細資訊，請參閱[幾何總覽](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cac16-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="cac16-144">XAML 縮寫語法</span><span class="sxs-lookup"><span data-stu-id="cac16-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="cac16-145">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，您也可以使用特殊的縮寫語法來描述 <xref:System.Windows.Shapes.Path>。</span><span class="sxs-lookup"><span data-stu-id="cac16-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="cac16-146">在下列範例中，縮寫語法是用來繪製複雜的圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="cac16-147">下圖顯示呈現的 <xref:System.Windows.Shapes.Path>。</span><span class="sxs-lookup"><span data-stu-id="cac16-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="cac16-148">![路徑圖例](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="cac16-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="cac16-149"><xref:System.Windows.Shapes.Path.Data%2A> 屬性字串的開頭是 "moveto" 命令，以 M 表示，這會在 <xref:System.Windows.Controls.Canvas>的座標系統中建立路徑的起點。</span><span class="sxs-lookup"><span data-stu-id="cac16-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="cac16-150"><xref:System.Windows.Shapes.Path> 資料參數會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="cac16-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="cac16-151">大寫 M 表示新目前點的絕對位置。</span><span class="sxs-lookup"><span data-stu-id="cac16-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="cac16-152">小寫 m 則表示相對座標。</span><span class="sxs-lookup"><span data-stu-id="cac16-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="cac16-153">第一個線段是三次方貝茲曲線，開始於 (100,200) 並結束於 (400,175)，使用 (100,25) 和 (400,350) 這兩個控制點繪製。</span><span class="sxs-lookup"><span data-stu-id="cac16-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="cac16-154">這個區段是由 <xref:System.Windows.Shapes.Path.Data%2A> 屬性字串中的 C 命令所表示。</span><span class="sxs-lookup"><span data-stu-id="cac16-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="cac16-155">同樣地，大寫 C 表示絕對路徑；小寫 c 表示相對路徑。</span><span class="sxs-lookup"><span data-stu-id="cac16-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="cac16-156">第二個線段的開頭為絕對水平 "lineto" 命令 H，它會指定從前面的子路徑的端點 (400,175) 到新端點 (280,175) 繪製的線段。</span><span class="sxs-lookup"><span data-stu-id="cac16-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="cac16-157">因為它是水準的 "lineto" 命令，指定的值是*x*座標。</span><span class="sxs-lookup"><span data-stu-id="cac16-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="cac16-158">如需完整的路徑語法，請參閱 <xref:System.Windows.Shapes.Path.Data%2A> 參考，並[使用 System.windows.media.pathgeometry> 建立圖形](how-to-create-a-shape-by-using-a-pathgeometry.md)。</span><span class="sxs-lookup"><span data-stu-id="cac16-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="cac16-159">繪製圖形</span><span class="sxs-lookup"><span data-stu-id="cac16-159">Painting Shapes</span></span>  
 <span data-ttu-id="cac16-160"><xref:System.Windows.Media.Brush> 物件是用來繪製圖形的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="cac16-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="cac16-161">在下列範例中，會指定 <xref:System.Windows.Shapes.Ellipse> 的筆劃和填滿。</span><span class="sxs-lookup"><span data-stu-id="cac16-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="cac16-162">請注意，筆刷屬性的有效輸入可以是關鍵字或十六進位色彩值。</span><span class="sxs-lookup"><span data-stu-id="cac16-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="cac16-163">如需可用的色彩關鍵字的詳細資訊，請參閱 <xref:System.Windows.Media> 命名空間中 <xref:System.Windows.Media.Colors> 類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="cac16-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
```xaml
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
  
 <span data-ttu-id="cac16-164">下圖顯示呈現的 <xref:System.Windows.Shapes.Ellipse>。</span><span class="sxs-lookup"><span data-stu-id="cac16-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="cac16-165">![橢圓形](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="cac16-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="cac16-166">或者，您可以使用屬性專案語法來明確建立 <xref:System.Windows.Media.SolidColorBrush> 物件，以純色繪製圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
```xaml
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
  
 <span data-ttu-id="cac16-167">下圖顯示轉譯的圖形。</span><span class="sxs-lookup"><span data-stu-id="cac16-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="cac16-168">![SolidColorBrush 圖例](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="cac16-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="cac16-169">您也可以使用漸層、影像、圖樣等等繪製圖形的筆觸或填滿。</span><span class="sxs-lookup"><span data-stu-id="cac16-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="cac16-170">如需詳細資訊，請參閱[使用純色和](painting-with-solid-colors-and-gradients-overview.md)漸層繪製的色彩。</span><span class="sxs-lookup"><span data-stu-id="cac16-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="cac16-171">可縮放的圖形</span><span class="sxs-lookup"><span data-stu-id="cac16-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="cac16-172"><xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Path>、<xref:System.Windows.Shapes.Polygon>、<xref:System.Windows.Shapes.Polyline>和 <xref:System.Windows.Shapes.Rectangle> 類別都有一個 <xref:System.Windows.Shapes.Shape.Stretch%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cac16-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="cac16-173">這個屬性會決定如何延展 <xref:System.Windows.Shapes.Shape> 物件的內容（要繪製的圖形），以填滿 <xref:System.Windows.Shapes.Shape> 物件的版面配置空間。</span><span class="sxs-lookup"><span data-stu-id="cac16-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="cac16-174"><xref:System.Windows.Shapes.Shape> 物件的配置空間（layout）是配置系統組態 <xref:System.Windows.Shapes.Shape> 的空間量，因為明確 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 設定，或是因為其 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 設定。</span><span class="sxs-lookup"><span data-stu-id="cac16-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="cac16-175">如需 Windows Presentation Foundation 中版面配置的詳細資訊，請參閱[版面](../advanced/layout.md)配置總覽。</span><span class="sxs-lookup"><span data-stu-id="cac16-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="cac16-176">Stretch 屬性可接受下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="cac16-176">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="cac16-177"><xref:System.Windows.Media.Stretch.None>： <xref:System.Windows.Shapes.Shape> 物件的內容不會伸展。</span><span class="sxs-lookup"><span data-stu-id="cac16-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="cac16-178"><xref:System.Windows.Media.Stretch.Fill>： <xref:System.Windows.Shapes.Shape> 物件的內容會伸展以填滿其版面配置空間。</span><span class="sxs-lookup"><span data-stu-id="cac16-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="cac16-179">不會維持外觀比例。</span><span class="sxs-lookup"><span data-stu-id="cac16-179">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="cac16-180"><xref:System.Windows.Media.Stretch.Uniform>： <xref:System.Windows.Shapes.Shape> 物件的內容會盡可能伸展以填滿其版面配置空間，同時保留原始的外觀比例。</span><span class="sxs-lookup"><span data-stu-id="cac16-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="cac16-181"><xref:System.Windows.Media.Stretch.UniformToFill>： <xref:System.Windows.Shapes.Shape> 物件的內容會伸展以完全填滿其版面配置空間，同時保留原始的外觀比例。</span><span class="sxs-lookup"><span data-stu-id="cac16-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="cac16-182">請注意，當 <xref:System.Windows.Shapes.Shape> 物件的內容擴展時，<xref:System.Windows.Shapes.Shape> 物件的大綱會在延展之後繪製。</span><span class="sxs-lookup"><span data-stu-id="cac16-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="cac16-183">在下列範例中，<xref:System.Windows.Shapes.Polygon> 用來繪製從（0，0）到（0，1）到（1，1）的極小三角形。</span><span class="sxs-lookup"><span data-stu-id="cac16-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="cac16-184"><xref:System.Windows.Shapes.Polygon> 物件的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 會設定為100，且其 stretch 屬性會設定為 Fill。</span><span class="sxs-lookup"><span data-stu-id="cac16-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="cac16-185">因此，<xref:System.Windows.Shapes.Polygon> 物件的內容（三角形）會伸展以填滿較大的空間。</span><span class="sxs-lookup"><span data-stu-id="cac16-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
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
```

<a name="transforms"></a>   
## <a name="transforming-shapes"></a><span data-ttu-id="cac16-186">轉換圖形</span><span class="sxs-lookup"><span data-stu-id="cac16-186">Transforming Shapes</span></span>  
 <span data-ttu-id="cac16-187"><xref:System.Windows.Media.Transform> 類別提供在二維平面中轉換圖形的方法。</span><span class="sxs-lookup"><span data-stu-id="cac16-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="cac16-188">不同類型的轉換包括旋轉（<xref:System.Windows.Media.RotateTransform>）、縮放（<xref:System.Windows.Media.ScaleTransform>）、扭曲（<xref:System.Windows.Media.SkewTransform>）和轉譯（<xref:System.Windows.Media.TranslateTransform>）。</span><span class="sxs-lookup"><span data-stu-id="cac16-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="cac16-189">套用至圖形的一種常用轉換就是旋轉。</span><span class="sxs-lookup"><span data-stu-id="cac16-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="cac16-190">若要旋轉圖形，請建立 <xref:System.Windows.Media.RotateTransform> 並指定其 <xref:System.Windows.Media.RotateTransform.Angle%2A>。</span><span class="sxs-lookup"><span data-stu-id="cac16-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="cac16-191">45的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 會順時針旋轉元素45度;90角度會順時針旋轉元素90度;以此類推。</span><span class="sxs-lookup"><span data-stu-id="cac16-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="cac16-192">如果您想要控制要旋轉元素的點，請設定 [<xref:System.Windows.Media.RotateTransform.CenterX%2A>] 和 [<xref:System.Windows.Media.RotateTransform.CenterY%2A> 屬性]。</span><span class="sxs-lookup"><span data-stu-id="cac16-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="cac16-193">這些屬性值會以轉換之元素的座標空間表示。</span><span class="sxs-lookup"><span data-stu-id="cac16-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="cac16-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> 和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 的預設值為零。</span><span class="sxs-lookup"><span data-stu-id="cac16-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="cac16-195">最後，將 <xref:System.Windows.Media.RotateTransform> 套用至元素。</span><span class="sxs-lookup"><span data-stu-id="cac16-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="cac16-196">如果您不想要轉換影響版面配置，請設定圖形的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cac16-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="cac16-197">在下列範例中，<xref:System.Windows.Media.RotateTransform> 用來將圖形的左上角（0，0）旋轉圖形45度。</span><span class="sxs-lookup"><span data-stu-id="cac16-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="cac16-198">在下一個範例中，另一個圖形也旋轉 45 度，但這次是從點 (25,50) 旋轉。</span><span class="sxs-lookup"><span data-stu-id="cac16-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="cac16-199">下圖顯示套用兩種轉換的結果。</span><span class="sxs-lookup"><span data-stu-id="cac16-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="cac16-200">![採用不同中心點的 45 度旋轉](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="cac16-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="cac16-201">在上一個範例中，已將單一轉換套用至每個圖形物件。</span><span class="sxs-lookup"><span data-stu-id="cac16-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="cac16-202">若要將多個轉換套用至圖形（或任何其他 UI 元素），請使用 <xref:System.Windows.Media.TransformGroup>。</span><span class="sxs-lookup"><span data-stu-id="cac16-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac16-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cac16-203">See also</span></span>

- [<span data-ttu-id="cac16-204">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="cac16-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="cac16-205">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="cac16-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="cac16-206">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="cac16-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="cac16-207">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="cac16-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="cac16-208">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="cac16-208">Animation Overview</span></span>](animation-overview.md)
