---
title: GDI+ 中的橢圓形和弧形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 8bbc2eda6450128eac55576259880e83f07099ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117452"
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="e03a1-102">GDI+ 中的橢圓形和弧形</span><span class="sxs-lookup"><span data-stu-id="e03a1-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="e03a1-103">您可以輕鬆地繪製橢圓形和弧形使用<xref:System.Drawing.Graphics.DrawEllipse%2A>並<xref:System.Drawing.Graphics.DrawArc%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="e03a1-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="e03a1-104">繪製橢圓形</span><span class="sxs-lookup"><span data-stu-id="e03a1-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="e03a1-105">若要繪製橢圓形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="e03a1-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="e03a1-106"><xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如寬度和色彩，用來呈現橢圓形的行。</span><span class="sxs-lookup"><span data-stu-id="e03a1-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="e03a1-107"><xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e03a1-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="e03a1-108">其餘的引數傳遞至<xref:System.Drawing.Graphics.DrawEllipse%2A>方法指定的橢圓形的週框矩形。</span><span class="sxs-lookup"><span data-stu-id="e03a1-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="e03a1-109">下圖顯示以及其周框的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="e03a1-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="e03a1-110">![橢圓形和弧形](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="e03a1-110">![Ellipses and arcs](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="e03a1-111">下列範例會繪製橢圓形;週框矩形的寬度為 80，40，高度和的左上角 （100，50）：</span><span class="sxs-lookup"><span data-stu-id="e03a1-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> <span data-ttu-id="e03a1-112">一個多載方法的<xref:System.Drawing.Graphics>類別中，因此有幾種方式，您可以提供引數。</span><span class="sxs-lookup"><span data-stu-id="e03a1-112">is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="e03a1-113">例如，您可以建構<xref:System.Drawing.Rectangle>，並傳遞<xref:System.Drawing.Rectangle>到<xref:System.Drawing.Graphics.DrawEllipse%2A>做為引數的方法：</span><span class="sxs-lookup"><span data-stu-id="e03a1-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="e03a1-114">繪製弧形</span><span class="sxs-lookup"><span data-stu-id="e03a1-114">Drawing an Arc</span></span>  
 <span data-ttu-id="e03a1-115">弧形是橢圓形的一部分。</span><span class="sxs-lookup"><span data-stu-id="e03a1-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="e03a1-116">若要繪製弧形，請呼叫<xref:System.Drawing.Graphics.DrawArc%2A>方法的<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="e03a1-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="e03a1-117">參數<xref:System.Drawing.Graphics.DrawArc%2A>方法會做為參數的相同<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，不同之處在於<xref:System.Drawing.Graphics.DrawArc%2A>需要開始角度和掃掠角度。</span><span class="sxs-lookup"><span data-stu-id="e03a1-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="e03a1-118">下列範例會繪製具有 30 度的開始角度和掃掠角度為 180 度弧線：</span><span class="sxs-lookup"><span data-stu-id="e03a1-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="e03a1-119">下圖顯示弧線、 橢圓形和週框矩形。</span><span class="sxs-lookup"><span data-stu-id="e03a1-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="e03a1-120">![橢圓形和弧形](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="e03a1-120">![Ellipses and arcs](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03a1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e03a1-121">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="e03a1-122">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="e03a1-122">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="e03a1-123">HOW TO：建立繪製的圖形物件</span><span class="sxs-lookup"><span data-stu-id="e03a1-123">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="e03a1-124">HOW TO：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="e03a1-124">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="e03a1-125">HOW TO：繪製外框形狀</span><span class="sxs-lookup"><span data-stu-id="e03a1-125">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
