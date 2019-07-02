---
title: GDI+ 中的畫筆、線條和矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 06d2351ffa7d7f009d7b049f4689df7038b4d202
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505347"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a><span data-ttu-id="b4230-102">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="b4230-102">Pens, Lines, and Rectangles in GDI+</span></span>
<span data-ttu-id="b4230-103">若要使用 GDI + 您需要建立繪製線條<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="b4230-103">To draw lines with GDI+ you need to create a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="b4230-104"><xref:System.Drawing.Graphics>物件提供的方法，實際進行繪製，而<xref:System.Drawing.Pen>物件會儲存屬性，例如線條色彩、 寬度和樣式。</span><span class="sxs-lookup"><span data-stu-id="b4230-104">The <xref:System.Drawing.Graphics> object provides the methods that actually do the drawing, and the <xref:System.Drawing.Pen> object stores attributes, such as line color, width, and style.</span></span>  
  
## <a name="drawing-a-line"></a><span data-ttu-id="b4230-105">繪製一條線</span><span class="sxs-lookup"><span data-stu-id="b4230-105">Drawing a Line</span></span>  
 <span data-ttu-id="b4230-106">若要繪製一條線，請呼叫<xref:System.Drawing.Graphics.DrawLine%2A>方法的<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="b4230-106">To draw a line, call the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="b4230-107"><xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawLine%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b4230-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="b4230-108">下列範例會繪製一條線從點 （4，2） 到點 （12，6）：</span><span class="sxs-lookup"><span data-stu-id="b4230-108">The following example draws a line from the point (4, 2) to the point (12, 6):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <span data-ttu-id="b4230-109"><xref:System.Drawing.Graphics.DrawLine%2A> 一個多載方法的<xref:System.Drawing.Graphics>類別中，因此有幾種方式，您可以提供引數。</span><span class="sxs-lookup"><span data-stu-id="b4230-109"><xref:System.Drawing.Graphics.DrawLine%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="b4230-110">例如，您可以建構兩個<xref:System.Drawing.Point>物件並傳遞<xref:System.Drawing.Point>物件做為引數<xref:System.Drawing.Graphics.DrawLine%2A>方法：</span><span class="sxs-lookup"><span data-stu-id="b4230-110">For example, you can construct two <xref:System.Drawing.Point> objects and pass the <xref:System.Drawing.Point> objects as arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a><span data-ttu-id="b4230-111">建構的畫筆</span><span class="sxs-lookup"><span data-stu-id="b4230-111">Constructing a Pen</span></span>  
 <span data-ttu-id="b4230-112">您可以指定特定屬性，當您建構<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="b4230-112">You can specify certain attributes when you construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="b4230-113">例如，一個`Pen`建構函式可讓您指定的色彩和寬度。</span><span class="sxs-lookup"><span data-stu-id="b4230-113">For example, one `Pen` constructor allows you to specify color and width.</span></span> <span data-ttu-id="b4230-114">下列範例會繪製藍線的寬度為 2 從 （0，0） 到 （60，30）：</span><span class="sxs-lookup"><span data-stu-id="b4230-114">The following example draws a blue line of width 2 from (0, 0) to (60, 30):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a><span data-ttu-id="b4230-115">虛線和線條端點</span><span class="sxs-lookup"><span data-stu-id="b4230-115">Dashed Lines and Line Caps</span></span>  
 <span data-ttu-id="b4230-116"><xref:System.Drawing.Pen>物件也會公開屬性，例如<xref:System.Drawing.Pen.DashStyle%2A>，可用來指定線條的功能。</span><span class="sxs-lookup"><span data-stu-id="b4230-116">The <xref:System.Drawing.Pen> object also exposes properties, such as <xref:System.Drawing.Pen.DashStyle%2A>, that you can use to specify features of the line.</span></span> <span data-ttu-id="b4230-117">下列範例會繪製一條虛線從 （100，50） 到 300 (80）：</span><span class="sxs-lookup"><span data-stu-id="b4230-117">The following example draws a dashed line from (100, 50) to (300, 80):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <span data-ttu-id="b4230-118">您可以使用的屬性<xref:System.Drawing.Pen>設定列的許多其他屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="b4230-118">You can use the properties of the <xref:System.Drawing.Pen> object to set many more attributes of the line.</span></span> <span data-ttu-id="b4230-119"><xref:System.Drawing.Pen.StartCap%2A>和<xref:System.Drawing.Pen.EndCap%2A>屬性指定線結束部分的外觀，端點可以是一般、 正方形、 圓角、 三角，或自訂的圖形。</span><span class="sxs-lookup"><span data-stu-id="b4230-119">The <xref:System.Drawing.Pen.StartCap%2A> and <xref:System.Drawing.Pen.EndCap%2A> properties specify the appearance of the ends of the line; the ends can be flat, square, rounded, triangular, or a custom shape.</span></span> <span data-ttu-id="b4230-120"><xref:System.Drawing.Pen.LineJoin%2A>屬性可讓您指定連接的直線是斜接 （加入具有銳利的角）、 斜、 捨入，或裁剪。</span><span class="sxs-lookup"><span data-stu-id="b4230-120">The <xref:System.Drawing.Pen.LineJoin%2A> property lets you specify whether connected lines are mitered (joined with sharp corners), beveled, rounded, or clipped.</span></span> <span data-ttu-id="b4230-121">下圖顯示具有各種不同的端點和聯結樣式的行。</span><span class="sxs-lookup"><span data-stu-id="b4230-121">The following illustration shows lines with various cap and join styles.</span></span>  
  
 <span data-ttu-id="b4230-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span><span class="sxs-lookup"><span data-stu-id="b4230-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span></span>  
  
## <a name="drawing-a-rectangle"></a><span data-ttu-id="b4230-123">繪製矩形</span><span class="sxs-lookup"><span data-stu-id="b4230-123">Drawing a Rectangle</span></span>  
 <span data-ttu-id="b4230-124">繪製矩形 GDI + 會類似於繪製線條。</span><span class="sxs-lookup"><span data-stu-id="b4230-124">Drawing rectangles with GDI+ is similar to drawing lines.</span></span> <span data-ttu-id="b4230-125">若要繪製矩形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="b4230-125">To draw a rectangle, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="b4230-126"><xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawRectangle%2A>方法，而<xref:System.Drawing.Pen>物件會儲存屬性，例如線條寬度和色彩。</span><span class="sxs-lookup"><span data-stu-id="b4230-126">The <xref:System.Drawing.Graphics> object provides a <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as line width and color.</span></span> <span data-ttu-id="b4230-127"><xref:System.Drawing.Pen>物件會傳遞做為其中一個引數<xref:System.Drawing.Graphics.DrawRectangle%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b4230-127">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method.</span></span> <span data-ttu-id="b4230-128">下列範例會繪製在其左上角的矩形 （100，50），寬度為 80，以及高度為 40:</span><span class="sxs-lookup"><span data-stu-id="b4230-128">The following example draws a rectangle with its upper-left corner at (100, 50), a width of 80, and a height of 40:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <span data-ttu-id="b4230-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> 一個多載方法的<xref:System.Drawing.Graphics>類別中，因此有幾種方式，您可以提供引數。</span><span class="sxs-lookup"><span data-stu-id="b4230-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="b4230-130">例如，您可以建構<xref:System.Drawing.Rectangle>物件，並傳遞<xref:System.Drawing.Rectangle>物件到<xref:System.Drawing.Graphics.DrawRectangle%2A>做為引數的方法：</span><span class="sxs-lookup"><span data-stu-id="b4230-130">For example, you can construct a <xref:System.Drawing.Rectangle> object and pass the <xref:System.Drawing.Rectangle> object to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <span data-ttu-id="b4230-131">A<xref:System.Drawing.Rectangle>物件具有方法和屬性來操作和收集矩形的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b4230-131">A <xref:System.Drawing.Rectangle> object has methods and properties for manipulating and gathering information about the rectangle.</span></span> <span data-ttu-id="b4230-132">例如，<xref:System.Drawing.Rectangle.Inflate%2A>和<xref:System.Drawing.Rectangle.Offset%2A>方法變更的大小和位置的矩形。</span><span class="sxs-lookup"><span data-stu-id="b4230-132">For example, the <xref:System.Drawing.Rectangle.Inflate%2A> and <xref:System.Drawing.Rectangle.Offset%2A> methods change the size and position of the rectangle.</span></span> <span data-ttu-id="b4230-133"><xref:System.Drawing.Rectangle.IntersectsWith%2A>方法會告訴您該矩形是否與另一個指定的矩形，而<xref:System.Drawing.Rectangle.Contains%2A>方法會告訴您指定的點是否在矩形內部。</span><span class="sxs-lookup"><span data-stu-id="b4230-133">The <xref:System.Drawing.Rectangle.IntersectsWith%2A> method tells you whether the rectangle intersects another given rectangle, and the <xref:System.Drawing.Rectangle.Contains%2A> method tells you whether a given point is inside the rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4230-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4230-134">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [<span data-ttu-id="b4230-135">如何：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="b4230-135">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="b4230-136">如何：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="b4230-136">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)
- [<span data-ttu-id="b4230-137">如何：繪製外框的形狀</span><span class="sxs-lookup"><span data-stu-id="b4230-137">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
