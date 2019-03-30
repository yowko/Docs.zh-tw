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
ms.openlocfilehash: 2b74b03137d5a450fb1e436a514877d1a17229ad
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654246"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="725e5-102">HOW TO：繪製順序的 B&#233;zier 曲線</span><span class="sxs-lookup"><span data-stu-id="725e5-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="725e5-103">您可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法的<xref:System.Drawing.Graphics>類別用來繪製一系列連接的貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="725e5-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="725e5-104">範例</span><span class="sxs-lookup"><span data-stu-id="725e5-104">Example</span></span>  
 <span data-ttu-id="725e5-105">下列範例會繪製曲線，其中包含的兩個連接的貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="725e5-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="725e5-106">第一個貝茲曲線的結束點是第二個貝茲曲線的起始點。</span><span class="sxs-lookup"><span data-stu-id="725e5-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="725e5-107">下圖顯示連接的曲線，以及在七個點：</span><span class="sxs-lookup"><span data-stu-id="725e5-107">The following illustration shows the connected splines along with the seven points:</span></span>  
  
 ![圖形： 顯示連接的曲線，以及七個點。](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="725e5-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="725e5-109">Compiling the Code</span></span>  
 <span data-ttu-id="725e5-110">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="725e5-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725e5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="725e5-111">See also</span></span>
- [<span data-ttu-id="725e5-112">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="725e5-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="725e5-113">GDI+ 中的貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="725e5-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="725e5-114">建構和繪製曲線</span><span class="sxs-lookup"><span data-stu-id="725e5-114">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
