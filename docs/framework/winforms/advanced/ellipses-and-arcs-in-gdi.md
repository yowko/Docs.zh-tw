---
title: "GDI+ 中的橢圓形和弧形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71126942f4cde37cc5d26bfba029c5f50f1065a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="78de4-102">GDI+ 中的橢圓形和弧形</span><span class="sxs-lookup"><span data-stu-id="78de4-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="78de4-103">您可以輕鬆地繪製橢圓形和弧形使用<xref:System.Drawing.Graphics.DrawEllipse%2A>和<xref:System.Drawing.Graphics.DrawArc%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="78de4-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="78de4-104">繪製橢圓形</span><span class="sxs-lookup"><span data-stu-id="78de4-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="78de4-105">若要繪製橢圓形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="78de4-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="78de4-106"><xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如寬度和色彩，用來呈現橢圓形的行。</span><span class="sxs-lookup"><span data-stu-id="78de4-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="78de4-107"><xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="78de4-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="78de4-108">其餘的引數傳遞至<xref:System.Drawing.Graphics.DrawEllipse%2A>方法指定的橢圓形之周框。</span><span class="sxs-lookup"><span data-stu-id="78de4-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="78de4-109">下圖顯示以及其周框的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="78de4-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="78de4-110">![橢圓形和弧形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="78de4-110">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="78de4-111">下列範例會繪製橢圓形。周框的寬度為 80，為 40，高度和的左上角 （100，50）：</span><span class="sxs-lookup"><span data-stu-id="78de4-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="78de4-112"><xref:System.Drawing.Graphics.DrawEllipse%2A>是一種多載的方法<xref:System.Drawing.Graphics>類別中，因此您可以提供引數的數種方式。</span><span class="sxs-lookup"><span data-stu-id="78de4-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="78de4-113">例如，您可以建構<xref:System.Drawing.Rectangle>並傳遞<xref:System.Drawing.Rectangle>至<xref:System.Drawing.Graphics.DrawEllipse%2A>做為引數的方法：</span><span class="sxs-lookup"><span data-stu-id="78de4-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="78de4-114">繪製弧形，</span><span class="sxs-lookup"><span data-stu-id="78de4-114">Drawing an Arc</span></span>  
 <span data-ttu-id="78de4-115">弧線是橢圓形的一部分。</span><span class="sxs-lookup"><span data-stu-id="78de4-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="78de4-116">若要繪製弧形，呼叫<xref:System.Drawing.Graphics.DrawArc%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="78de4-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="78de4-117">參數的<xref:System.Drawing.Graphics.DrawArc%2A>方法和步驟完全相同的參數<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，不同處在於<xref:System.Drawing.Graphics.DrawArc%2A>需要開始角度和掃掠角度。</span><span class="sxs-lookup"><span data-stu-id="78de4-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="78de4-118">下列範例會繪製弧形，30 度開始角度與掃掠角度為 180 度：</span><span class="sxs-lookup"><span data-stu-id="78de4-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="78de4-119">下圖顯示弧線、 橢圓形和週框矩形。</span><span class="sxs-lookup"><span data-stu-id="78de4-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="78de4-120">![橢圓形和弧形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="78de4-120">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78de4-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="78de4-121">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="78de4-122">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="78de4-122">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="78de4-123">操作說明：建立繪圖的圖形物件</span><span class="sxs-lookup"><span data-stu-id="78de4-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="78de4-124">操作說明：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="78de4-124">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="78de4-125">操作說明：繪製外框形狀</span><span class="sxs-lookup"><span data-stu-id="78de4-125">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
