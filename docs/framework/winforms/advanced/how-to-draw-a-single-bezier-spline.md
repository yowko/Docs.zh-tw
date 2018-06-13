---
title: 如何： 繪製單一 B&#233;zier 曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 9e91b63275c37fc0cdde5721fddd114e1bf2264e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521332"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="bc6f2-102">如何： 繪製單一 B&#233;zier 曲線</span><span class="sxs-lookup"><span data-stu-id="bc6f2-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="bc6f2-103">貝茲曲線由四個點所定義： 一個起始點，兩個控制點和端點。</span><span class="sxs-lookup"><span data-stu-id="bc6f2-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc6f2-104">範例</span><span class="sxs-lookup"><span data-stu-id="bc6f2-104">Example</span></span>  
 <span data-ttu-id="bc6f2-105">下列範例會繪製具有 （10，100） 的起點和終點 （200，100） 的貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="bc6f2-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="bc6f2-106">控制項點為 （100，10） 和 150 （150）。</span><span class="sxs-lookup"><span data-stu-id="bc6f2-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="bc6f2-107">下圖顯示產生的貝茲曲線，以及其起點、 控點和端點。</span><span class="sxs-lookup"><span data-stu-id="bc6f2-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="bc6f2-108">下圖也會顯示曲線的凸殼，也就是所連接的四個點之直線的多邊形。</span><span class="sxs-lookup"><span data-stu-id="bc6f2-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="bc6f2-109">![貝茲曲線](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="bc6f2-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc6f2-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bc6f2-110">Compiling the Code</span></span>  
 <span data-ttu-id="bc6f2-111">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="bc6f2-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6f2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc6f2-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [<span data-ttu-id="bc6f2-113">GDI+ 中的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="bc6f2-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="bc6f2-114">操作說明：繪製一連串的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="bc6f2-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
