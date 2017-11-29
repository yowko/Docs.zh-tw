---
title: "如何： 繪製一連串的 B &#233; zier 曲線"
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
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76a0ab96f40c1b8d9db6f61d19ece82066b63eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="9a4a3-102">如何： 繪製一連串的 B &#233; zier 曲線</span><span class="sxs-lookup"><span data-stu-id="9a4a3-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="9a4a3-103">您可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法<xref:System.Drawing.Graphics>類別繪製一系列連接的貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="9a4a3-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a4a3-104">範例</span><span class="sxs-lookup"><span data-stu-id="9a4a3-104">Example</span></span>  
 <span data-ttu-id="9a4a3-105">下列範例會繪製包含兩個連接的貝茲曲線的曲線。</span><span class="sxs-lookup"><span data-stu-id="9a4a3-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="9a4a3-106">第一個貝茲曲線的結束點是第二個貝茲曲線開始點。</span><span class="sxs-lookup"><span data-stu-id="9a4a3-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="9a4a3-107">下圖顯示連接的曲線，和七個點。</span><span class="sxs-lookup"><span data-stu-id="9a4a3-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="9a4a3-108">![貝茲曲線](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="9a4a3-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a4a3-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9a4a3-109">Compiling the Code</span></span>  
 <span data-ttu-id="9a4a3-110">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="9a4a3-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a4a3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a4a3-111">See Also</span></span>  
 [<span data-ttu-id="9a4a3-112">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="9a4a3-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="9a4a3-113">GDI+ 中的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="9a4a3-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="9a4a3-114">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="9a4a3-114">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
