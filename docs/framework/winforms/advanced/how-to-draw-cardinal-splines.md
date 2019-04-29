---
title: HOW TO：繪製基本曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 2f03177bf97936a2ca9558972d4d82fa3e07463c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703710"
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="c047a-102">HOW TO：繪製基本曲線</span><span class="sxs-lookup"><span data-stu-id="c047a-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="c047a-103">基本曲線是一條曲線順利通過一組指定的點。</span><span class="sxs-lookup"><span data-stu-id="c047a-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="c047a-104">若要繪製基本曲線，建立<xref:System.Drawing.Graphics>物件，並指向陣列的位址傳遞<xref:System.Drawing.Graphics.DrawCurve%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c047a-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="c047a-105">繪製基本鐘型曲線</span><span class="sxs-lookup"><span data-stu-id="c047a-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
- <span data-ttu-id="c047a-106">下列範例會繪製的鐘型基線曲線通過五個指定的點。</span><span class="sxs-lookup"><span data-stu-id="c047a-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="c047a-107">下圖顯示曲線和五個點。</span><span class="sxs-lookup"><span data-stu-id="c047a-107">The following illustration shows the curve and five points.</span></span>  
  
     ![此圖顯示的鐘型的基本曲線。](./media/how-to-draw-cardinal-splines/bell-shaped-cardinal-spline.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="c047a-109">繪製封閉的基線曲線</span><span class="sxs-lookup"><span data-stu-id="c047a-109">Drawing a Closed Cardinal Spline</span></span>  
  
- <span data-ttu-id="c047a-110">使用<xref:System.Drawing.Graphics.DrawClosedCurve%2A>方法的<xref:System.Drawing.Graphics>類別用來繪製封閉的基線曲線。</span><span class="sxs-lookup"><span data-stu-id="c047a-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="c047a-111">在封閉的基線曲線曲線會繼續進行到陣列中的最後一個點，並在陣列中的第一個點會連線。</span><span class="sxs-lookup"><span data-stu-id="c047a-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="c047a-112">下列範例會繪製封閉的基線曲線通過六個指定的點。</span><span class="sxs-lookup"><span data-stu-id="c047a-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="c047a-113">下圖顯示已關閉的曲線，以及六個點：</span><span class="sxs-lookup"><span data-stu-id="c047a-113">The following illustration shows the closed spline along with the six points:</span></span>  
  
 ![此圖顯示的封閉的基線曲線。](./media/how-to-draw-cardinal-splines/closed-cardinal-spine.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="c047a-115">變更的彎曲的基線曲線</span><span class="sxs-lookup"><span data-stu-id="c047a-115">Changing the Bend of a Cardinal Spline</span></span>  
  
- <span data-ttu-id="c047a-116">變更的方式傳遞的張力引數的彎曲的基本曲線<xref:System.Drawing.Graphics.DrawCurve%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c047a-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="c047a-117">下列範例會繪製通過相同的一組點的三個基本曲線。</span><span class="sxs-lookup"><span data-stu-id="c047a-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="c047a-118">下圖顯示三個曲線，以及其張力值。</span><span class="sxs-lookup"><span data-stu-id="c047a-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="c047a-119">請注意，張力為 0 時，點是以直線來連接。</span><span class="sxs-lookup"><span data-stu-id="c047a-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 ![此圖顯示三個基本曲線。](./media/how-to-draw-cardinal-splines/three-cardinal-splines.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c047a-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c047a-121">Compiling the Code</span></span>  
 <span data-ttu-id="c047a-122">上述範例專為搭配 Windows Form 使用，而且它們需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c047a-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c047a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c047a-123">See also</span></span>

- [<span data-ttu-id="c047a-124">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="c047a-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="c047a-125">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="c047a-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
