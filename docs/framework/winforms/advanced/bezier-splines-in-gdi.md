---
title: B&#233;zier GDI + 中的曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107324"
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="37373-102">B&#233;zier GDI + 中的曲線</span><span class="sxs-lookup"><span data-stu-id="37373-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="37373-103">貝茲曲線是由四個點指定曲線： 兩個結束點 （p1 和 p2） 和兩個控制點 （c1 和 c2）。</span><span class="sxs-lookup"><span data-stu-id="37373-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="37373-104">曲線開始 p1 和 p2 當做結尾。</span><span class="sxs-lookup"><span data-stu-id="37373-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="37373-105">曲線的控制點，透過未通過，但控制點作用類似磁鐵，曲線納入特定指示和影響曲線的彎曲的方式。</span><span class="sxs-lookup"><span data-stu-id="37373-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="37373-106">下圖顯示加上其端點和控制點貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="37373-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="37373-107">![貝茲曲線](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="37373-107">![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="37373-108">曲線開始 p1，並會朝控制點 c1 移動。</span><span class="sxs-lookup"><span data-stu-id="37373-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="37373-109">P1 曲線的切線是從 p1 到 c1 繪製的線條。</span><span class="sxs-lookup"><span data-stu-id="37373-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="37373-110">端點 p2 的切線是取自 c2 為 p2 的線條。</span><span class="sxs-lookup"><span data-stu-id="37373-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="37373-111">繪製貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="37373-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="37373-112">若要繪製貝茲曲線，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Pen>。</span><span class="sxs-lookup"><span data-stu-id="37373-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="37373-113">執行個體<xref:System.Drawing.Graphics>類別會提供<xref:System.Drawing.Graphics.DrawBezier%2A>方法，而<xref:System.Drawing.Pen>儲存屬性，例如寬度和色彩，用來呈現曲線的行。</span><span class="sxs-lookup"><span data-stu-id="37373-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="37373-114"><xref:System.Drawing.Pen>做為其中一個引數會傳遞<xref:System.Drawing.Graphics.DrawBezier%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="37373-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="37373-115">其餘的引數傳遞至<xref:System.Drawing.Graphics.DrawBezier%2A>方法還有端點的控點。</span><span class="sxs-lookup"><span data-stu-id="37373-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="37373-116">下列範例會繪製貝茲曲線的起始點 （0，0），控制點 （40，20） 和 （80，150） 和結束點 （100，10）：</span><span class="sxs-lookup"><span data-stu-id="37373-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="37373-117">下圖顯示曲線的控制點，，兩正切函數的行。</span><span class="sxs-lookup"><span data-stu-id="37373-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="37373-118">![貝茲曲線](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="37373-118">![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="37373-119">匹貝茲最初所開發的貝茲曲線在汽車的產業中設計的。</span><span class="sxs-lookup"><span data-stu-id="37373-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="37373-120">而因為證明為十分有用，許多電腦輔助設計的類型也用來定義字型的外框。</span><span class="sxs-lookup"><span data-stu-id="37373-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="37373-121">貝茲曲線，可能會產生各種不同的圖形，其中會顯示在下圖中。</span><span class="sxs-lookup"><span data-stu-id="37373-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="37373-122">![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="37373-122">![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37373-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37373-123">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="37373-124">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="37373-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="37373-125">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="37373-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
- [<span data-ttu-id="37373-126">HOW TO：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="37373-126">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="37373-127">HOW TO：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="37373-127">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
