---
title: HOW TO：繪製順序的 B&#233;zier 曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 1de2f44be189cb2ff874a748ae6093c945120178
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711784"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="3cc37-102">HOW TO：繪製順序的 B&#233;zier 曲線</span><span class="sxs-lookup"><span data-stu-id="3cc37-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="3cc37-103">您可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法的<xref:System.Drawing.Graphics>類別用來繪製一系列連接的貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="3cc37-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc37-104">範例</span><span class="sxs-lookup"><span data-stu-id="3cc37-104">Example</span></span>  
 <span data-ttu-id="3cc37-105">下列範例會繪製曲線，其中包含的兩個連接的貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="3cc37-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="3cc37-106">第一個貝茲曲線的結束點是第二個貝茲曲線的起始點。</span><span class="sxs-lookup"><span data-stu-id="3cc37-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="3cc37-107">下圖顯示連接的曲線，以及在七個點。</span><span class="sxs-lookup"><span data-stu-id="3cc37-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="3cc37-108">![Bezier Spline](./media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="3cc37-108">![Bezier Spline](./media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cc37-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3cc37-109">Compiling the Code</span></span>  
 <span data-ttu-id="3cc37-110">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="3cc37-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc37-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cc37-111">See also</span></span>
- [<span data-ttu-id="3cc37-112">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="3cc37-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="3cc37-113">GDI+ 中的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="3cc37-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="3cc37-114">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="3cc37-114">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
