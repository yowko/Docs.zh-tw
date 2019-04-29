---
title: 向量圖形概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: d424254839db6c403bafe779f475c0e344918a5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748422"
---
# <a name="vector-graphics-overview"></a><span data-ttu-id="d1728-102">向量圖形概觀</span><span class="sxs-lookup"><span data-stu-id="d1728-102">Vector Graphics Overview</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="d1728-103">座標系統上繪製線條、 矩形和其他形狀。</span><span class="sxs-lookup"><span data-stu-id="d1728-103">draws lines, rectangles, and other shapes on a coordinate system.</span></span> <span data-ttu-id="d1728-104">您可以選擇各式各樣的座標系統，但預設座標系統具有原點左上角的 x 軸指向右側和 y 軸指向下方。</span><span class="sxs-lookup"><span data-stu-id="d1728-104">You can choose from a variety of coordinate systems, but the default coordinate system has the origin in the upper-left corner with the x-axis pointing to the right and the y-axis pointing down.</span></span> <span data-ttu-id="d1728-105">預設座標系統中的測量單位為像素。</span><span class="sxs-lookup"><span data-stu-id="d1728-105">The unit of measure in the default coordinate system is the pixel.</span></span>  
  
## <a name="the-building-blocks-of-gdi"></a><span data-ttu-id="d1728-106">GDI + 的建置組塊</span><span class="sxs-lookup"><span data-stu-id="d1728-106">The Building Blocks of GDI+</span></span>  
 <span data-ttu-id="d1728-107">![向量圖形](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span><span class="sxs-lookup"><span data-stu-id="d1728-107">![Vector graphic](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")</span></span>  
  
 <span data-ttu-id="d1728-108">電腦監視器上稱為圖片項目或像素為單位的點的矩形陣列建立它的顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="d1728-108">A computer monitor creates its display on a rectangular array of dots called picture elements or pixels.</span></span> <span data-ttu-id="d1728-109">出現在螢幕的像素數目從一部監視器到下一步，以及設定而有所不同個別的監視器顯示的像素數目可以通常是在某個程度使用者。</span><span class="sxs-lookup"><span data-stu-id="d1728-109">The number of pixels that appear on the screen varies from one monitor to the next, and the number of pixels that appear on an individual monitor can usually be configured to some extent by the user.</span></span>  
  
 <span data-ttu-id="d1728-110">![向量圖形](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span><span class="sxs-lookup"><span data-stu-id="d1728-110">![Vector graphic](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")</span></span>  
  
 <span data-ttu-id="d1728-111">當您使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪製線條、 矩形或曲線時，您可以提供要繪製項目的特定索引鍵資訊。</span><span class="sxs-lookup"><span data-stu-id="d1728-111">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, rectangle, or curve, you provide certain key information about the item to be drawn.</span></span> <span data-ttu-id="d1728-112">比方說，您可以藉由提供兩個點，來指定一條線，而您可以藉由提供一個點、 高度和寬度指定矩形。</span><span class="sxs-lookup"><span data-stu-id="d1728-112">For example, you can specify a line by providing two points, and you can specify a rectangle by providing a point, a height, and a width.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="d1728-113">若要判斷哪一個像素為單位必須開啟，以顯示線條、 矩形或曲線的顯示驅動程式軟體一起運作。</span><span class="sxs-lookup"><span data-stu-id="d1728-113">works in conjunction with the display driver software to determine which pixels must be turned on to show the line, rectangle, or curve.</span></span> <span data-ttu-id="d1728-114">下圖顯示從點 （4，2） 顯示一條線，以點 （12，8） 開啟的像素。</span><span class="sxs-lookup"><span data-stu-id="d1728-114">The following illustration shows the pixels that are turned on to display a line from the point (4, 2) to the point (12, 8).</span></span>  
  
 <span data-ttu-id="d1728-115">![向量圖形](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span><span class="sxs-lookup"><span data-stu-id="d1728-115">![Vector graphic](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")</span></span>  
  
 <span data-ttu-id="d1728-116">經過一段時間，某些基本的建置組塊證明為十分最適用於建立二維的圖片。</span><span class="sxs-lookup"><span data-stu-id="d1728-116">Over time, certain basic building blocks have proven to be the most useful for creating two-dimensional pictures.</span></span> <span data-ttu-id="d1728-117">這些建置組塊，所有支援的[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]下, 面清單中指定：</span><span class="sxs-lookup"><span data-stu-id="d1728-117">These building blocks, which are all supported by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], are given in the following list:</span></span>  
  
- <span data-ttu-id="d1728-118">線條</span><span class="sxs-lookup"><span data-stu-id="d1728-118">Lines</span></span>  
  
- <span data-ttu-id="d1728-119">矩形</span><span class="sxs-lookup"><span data-stu-id="d1728-119">Rectangles</span></span>  
  
- <span data-ttu-id="d1728-120">省略符號</span><span class="sxs-lookup"><span data-stu-id="d1728-120">Ellipses</span></span>  
  
- <span data-ttu-id="d1728-121">Arcs</span><span class="sxs-lookup"><span data-stu-id="d1728-121">Arcs</span></span>  
  
- <span data-ttu-id="d1728-122">多邊形</span><span class="sxs-lookup"><span data-stu-id="d1728-122">Polygons</span></span>  
  
- <span data-ttu-id="d1728-123">基線曲線</span><span class="sxs-lookup"><span data-stu-id="d1728-123">Cardinal splines</span></span>  
  
- <span data-ttu-id="d1728-124">貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="d1728-124">Bezier splines</span></span>  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a><span data-ttu-id="d1728-125">繪製圖形物件的方法</span><span class="sxs-lookup"><span data-stu-id="d1728-125">Methods For Drawing with a Graphics Object</span></span>  
 <span data-ttu-id="d1728-126"><xref:System.Drawing.Graphics>類別內[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供下列方法來繪製上述清單中的項目： <xref:System.Drawing.Graphics.DrawLine%2A>， <xref:System.Drawing.Graphics.DrawRectangle%2A>， <xref:System.Drawing.Graphics.DrawEllipse%2A>， <xref:System.Drawing.Graphics.DrawPolygon%2A>， <xref:System.Drawing.Graphics.DrawArc%2A>， <xref:System.Drawing.Graphics.DrawCurve%2A> （適用於基本曲線），以及<xref:System.Drawing.Graphics.DrawBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1728-126">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for drawing the items in the previous list: <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawRectangle%2A>, <xref:System.Drawing.Graphics.DrawEllipse%2A>, <xref:System.Drawing.Graphics.DrawPolygon%2A>, <xref:System.Drawing.Graphics.DrawArc%2A>, <xref:System.Drawing.Graphics.DrawCurve%2A> (for cardinal splines), and <xref:System.Drawing.Graphics.DrawBezier%2A>.</span></span> <span data-ttu-id="d1728-127">每一種方法多載;也就是說，每一種方法支援數個不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="d1728-127">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="d1728-128">比方說，一個變化<xref:System.Drawing.Graphics.DrawLine%2A>方法會接收<xref:System.Drawing.Pen>物件和四個整數，另一種變化的同時<xref:System.Drawing.Graphics.DrawLine%2A>方法會接收<xref:System.Drawing.Pen>物件和兩個<xref:System.Drawing.Point>物件。</span><span class="sxs-lookup"><span data-stu-id="d1728-128">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers, while another variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="d1728-129">繪製線條、 矩形和貝茲曲線的方法有複數隨附的方法，繪製單一呼叫中的數個項目： <xref:System.Drawing.Graphics.DrawLines%2A>， <xref:System.Drawing.Graphics.DrawRectangles%2A>，和<xref:System.Drawing.Graphics.DrawBeziers%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1728-129">The methods for drawing lines, rectangles, and Bézier splines have plural companion methods that draw several items in a single call: <xref:System.Drawing.Graphics.DrawLines%2A>, <xref:System.Drawing.Graphics.DrawRectangles%2A>, and <xref:System.Drawing.Graphics.DrawBeziers%2A>.</span></span> <span data-ttu-id="d1728-130">此外，<xref:System.Drawing.Graphics.DrawCurve%2A>方法具有附屬方法<xref:System.Drawing.Graphics.DrawClosedCurve%2A>，關閉的曲線，藉由連接曲線的結束點的開始點。</span><span class="sxs-lookup"><span data-stu-id="d1728-130">Also, the <xref:System.Drawing.Graphics.DrawCurve%2A> method has a companion method, <xref:System.Drawing.Graphics.DrawClosedCurve%2A>, that closes a curve by connecting the ending point of the curve to the starting point.</span></span>  
  
 <span data-ttu-id="d1728-131">所有的繪圖方法<xref:System.Drawing.Graphics>類別搭配工作<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="d1728-131">All of the drawing methods of the <xref:System.Drawing.Graphics> class work in conjunction with a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="d1728-132">若要繪製的任何項目，您必須建立至少兩個物件：<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="d1728-132">To draw anything, you must create at least two objects: a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="d1728-133"><xref:System.Drawing.Pen>物件會儲存屬性，例如線條寬度和色彩，要繪製的項目。</span><span class="sxs-lookup"><span data-stu-id="d1728-133">The <xref:System.Drawing.Pen> object stores attributes, such as line width and color, of the item to be drawn.</span></span> <span data-ttu-id="d1728-134"><xref:System.Drawing.Pen>物件做為其中一個引數傳遞至繪圖的方法。</span><span class="sxs-lookup"><span data-stu-id="d1728-134">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the drawing method.</span></span> <span data-ttu-id="d1728-135">例如，一個變化<xref:System.Drawing.Graphics.DrawLine%2A>方法會接收<xref:System.Drawing.Pen>物件和四個整數，如下列的範例中，以繪製矩形的寬度為 100，高度為 50 和的左上角中所示 20 (10）：</span><span class="sxs-lookup"><span data-stu-id="d1728-135">For example, one variation of the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object and four integers as shown in the following example, which draws a rectangle with a width of 100, a height of 50 and an upper-left corner of (20, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="d1728-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1728-136">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="d1728-137">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="d1728-137">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="d1728-138">如何：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="d1728-138">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
