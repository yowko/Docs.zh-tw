---
title: "如何：繪製基本曲線"
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
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c47ff269cb1c367abee0be197fdc80485fb37b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="4a027-102">如何：繪製基本曲線</span><span class="sxs-lookup"><span data-stu-id="4a027-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="4a027-103">基本曲線是曲線順利通過指定的點集合。</span><span class="sxs-lookup"><span data-stu-id="4a027-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="4a027-104">若要繪製基本曲線，建立<xref:System.Drawing.Graphics>物件，並傳遞至點陣列位址<xref:System.Drawing.Graphics.DrawCurve%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="4a027-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="4a027-105">繪製鐘型曲線</span><span class="sxs-lookup"><span data-stu-id="4a027-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="4a027-106">下列範例會繪製鐘型曲線通過五個指定點。</span><span class="sxs-lookup"><span data-stu-id="4a027-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="4a027-107">下圖顯示曲線和五個點。</span><span class="sxs-lookup"><span data-stu-id="4a027-107">The following illustration shows the curve and five points.</span></span>  
  
     <span data-ttu-id="4a027-108">![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span><span class="sxs-lookup"><span data-stu-id="4a027-108">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="4a027-109">繪製封閉的基線曲線</span><span class="sxs-lookup"><span data-stu-id="4a027-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="4a027-110">使用<xref:System.Drawing.Graphics.DrawClosedCurve%2A>方法<xref:System.Drawing.Graphics>繪製封閉的基線曲線的類別。</span><span class="sxs-lookup"><span data-stu-id="4a027-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="4a027-111">封閉的基線曲線的曲線會持續進行陣列中的最後一個點，並連接陣列中的第一個點。</span><span class="sxs-lookup"><span data-stu-id="4a027-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="4a027-112">下列範例會繪製封閉的基線曲線通過六個指定的點。</span><span class="sxs-lookup"><span data-stu-id="4a027-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="4a027-113">下圖顯示六個點以及曲線已關閉。</span><span class="sxs-lookup"><span data-stu-id="4a027-113">The following illustration shows the closed spline along with the six points.</span></span>  
  
 <span data-ttu-id="4a027-114">![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span><span class="sxs-lookup"><span data-stu-id="4a027-114">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="4a027-115">變更的彎曲的基本曲線</span><span class="sxs-lookup"><span data-stu-id="4a027-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="4a027-116">變更的方式所傳遞的張力引數的彎曲的基線曲線<xref:System.Drawing.Graphics.DrawCurve%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="4a027-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="4a027-117">下列範例會繪製通過相同的一組點的三個基本曲線。</span><span class="sxs-lookup"><span data-stu-id="4a027-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="4a027-118">下圖顯示三個曲線與其張力值。</span><span class="sxs-lookup"><span data-stu-id="4a027-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="4a027-119">請注意張力為 0 時，點會連接的直線。</span><span class="sxs-lookup"><span data-stu-id="4a027-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 <span data-ttu-id="4a027-120">![基本曲線](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span><span class="sxs-lookup"><span data-stu-id="4a027-120">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4a027-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4a027-121">Compiling the Code</span></span>  
 <span data-ttu-id="4a027-122">前面的範例專為搭配 Windows Form 使用，而且會要求<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4a027-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a027-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a027-123">See Also</span></span>  
 [<span data-ttu-id="4a027-124">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="4a027-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="4a027-125">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="4a027-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
