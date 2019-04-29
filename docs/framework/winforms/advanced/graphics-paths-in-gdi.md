---
title: GDI+ 中的圖形路徑
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: c9a43065210f5ef0fffcae01cc7eb88349696b6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938130"
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="5bd98-102">GDI+ 中的圖形路徑</span><span class="sxs-lookup"><span data-stu-id="5bd98-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="5bd98-103">路徑被形成藉由結合線條、 矩形和簡單的曲線。</span><span class="sxs-lookup"><span data-stu-id="5bd98-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="5bd98-104">回想一下[向量圖形概觀](vector-graphics-overview.md)是最適合繪製圖片證明了下列的基本建置組塊：</span><span class="sxs-lookup"><span data-stu-id="5bd98-104">Recall from the [Vector Graphics Overview](vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
- <span data-ttu-id="5bd98-105">線條</span><span class="sxs-lookup"><span data-stu-id="5bd98-105">Lines</span></span>  
  
- <span data-ttu-id="5bd98-106">矩形</span><span class="sxs-lookup"><span data-stu-id="5bd98-106">Rectangles</span></span>  
  
- <span data-ttu-id="5bd98-107">省略符號</span><span class="sxs-lookup"><span data-stu-id="5bd98-107">Ellipses</span></span>  
  
- <span data-ttu-id="5bd98-108">Arcs</span><span class="sxs-lookup"><span data-stu-id="5bd98-108">Arcs</span></span>  
  
- <span data-ttu-id="5bd98-109">多邊形</span><span class="sxs-lookup"><span data-stu-id="5bd98-109">Polygons</span></span>  
  
- <span data-ttu-id="5bd98-110">基線曲線</span><span class="sxs-lookup"><span data-stu-id="5bd98-110">Cardinal splines</span></span>  
  
- <span data-ttu-id="5bd98-111">貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="5bd98-111">Bézier splines</span></span>  
  
 <span data-ttu-id="5bd98-112">在 GDI + 中，<xref:System.Drawing.Drawing2D.GraphicsPath>物件可讓您收集成一個單位的一連串的這些建置組塊。</span><span class="sxs-lookup"><span data-stu-id="5bd98-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="5bd98-113">然後可以有一個呼叫繪製一連串完整的線條、 矩形、 多邊形和曲線<xref:System.Drawing.Graphics.DrawPath%2A>方法的<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="5bd98-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="5bd98-114">下圖顯示一條線，弧形、 貝茲曲線的基線曲線相結合所產生的路徑。</span><span class="sxs-lookup"><span data-stu-id="5bd98-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="5bd98-115">![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="5bd98-115">![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="5bd98-116">使用路徑</span><span class="sxs-lookup"><span data-stu-id="5bd98-116">Using a Path</span></span>  
 <span data-ttu-id="5bd98-117"><xref:System.Drawing.Drawing2D.GraphicsPath>類別提供下列方法來建立一連串要繪製的項目： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> （適用於基本曲線），和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>。</span><span class="sxs-lookup"><span data-stu-id="5bd98-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="5bd98-118">每一種方法多載;也就是說，每一種方法支援數個不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="5bd98-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="5bd98-119">比方說，一個變化<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法會收到四個整數，與另一個變化<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法會接收兩個<xref:System.Drawing.Point>物件。</span><span class="sxs-lookup"><span data-stu-id="5bd98-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="5bd98-120">加入路徑的線條、 矩形和貝茲曲線的方法有數個項目新增至單一呼叫中的路徑的複數隨附方法： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>，和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>。</span><span class="sxs-lookup"><span data-stu-id="5bd98-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="5bd98-121">此外，<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>並<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>方法有隨附方法<xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A>和<xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>，將關閉的曲線或圓形圖新增至路徑。</span><span class="sxs-lookup"><span data-stu-id="5bd98-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="5bd98-122">若要繪製的路徑，您需要<xref:System.Drawing.Graphics>物件，<xref:System.Drawing.Pen>物件，和<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="5bd98-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="5bd98-123"><xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawPath%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如 寬度 和 用來呈現的路徑線條的色彩。</span><span class="sxs-lookup"><span data-stu-id="5bd98-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="5bd98-124"><xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一連串的直線和曲線路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="5bd98-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="5bd98-125"><xref:System.Drawing.Pen>物件和<xref:System.Drawing.Drawing2D.GraphicsPath>物件會當做參數傳遞給<xref:System.Drawing.Graphics.DrawPath%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5bd98-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="5bd98-126">下列範例會繪製包含線條、 橢圓形和貝茲曲線的路徑：</span><span class="sxs-lookup"><span data-stu-id="5bd98-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="5bd98-127">下圖顯示的路徑。</span><span class="sxs-lookup"><span data-stu-id="5bd98-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="5bd98-128">![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="5bd98-128">![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="5bd98-129">除了新增至路徑的線條、 矩形和曲線，您可以新增至路徑的路徑。</span><span class="sxs-lookup"><span data-stu-id="5bd98-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="5bd98-130">這可讓您結合現有的路徑，以形成大型且複雜的路徑。</span><span class="sxs-lookup"><span data-stu-id="5bd98-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="5bd98-131">您可以將它新增至路徑的其他兩個項目： 字串和派形。</span><span class="sxs-lookup"><span data-stu-id="5bd98-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="5bd98-132">圓形圖會是橢圓形的一部分內部。</span><span class="sxs-lookup"><span data-stu-id="5bd98-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="5bd98-133">下列範例會建立從弧線、 的基本曲線、 字串和圓形路徑：</span><span class="sxs-lookup"><span data-stu-id="5bd98-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="5bd98-134">下圖顯示的路徑。</span><span class="sxs-lookup"><span data-stu-id="5bd98-134">The following illustration shows the path.</span></span> <span data-ttu-id="5bd98-135">請注意，路徑可能沒有連線;弧線、 基線曲線、 字串和圓形圖會分隔。</span><span class="sxs-lookup"><span data-stu-id="5bd98-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="5bd98-136">![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="5bd98-136">![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd98-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bd98-137">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [<span data-ttu-id="5bd98-138">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="5bd98-138">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="5bd98-139">如何：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="5bd98-139">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="5bd98-140">建構和繪製路徑</span><span class="sxs-lookup"><span data-stu-id="5bd98-140">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
