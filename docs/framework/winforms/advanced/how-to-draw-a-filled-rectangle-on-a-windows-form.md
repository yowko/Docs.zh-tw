---
title: HOW TO：Windows Form 上繪製實心的矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: a9722b2939e77282453743a4dea165a340412a21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587030"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="e5c6b-102">HOW TO：Windows Form 上繪製實心的矩形</span><span class="sxs-lookup"><span data-stu-id="e5c6b-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="e5c6b-103">此範例會在表單上繪製實心的矩形。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5c6b-104">範例</span><span class="sxs-lookup"><span data-stu-id="e5c6b-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5c6b-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e5c6b-105">Compiling the Code</span></span>  
 <span data-ttu-id="e5c6b-106">您不能呼叫這個方法<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="e5c6b-107">如果調整大小或遮蔽另一種形式的表單時，將不會重新繪製的繪製的內容。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="e5c6b-108">若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e5c6b-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="e5c6b-109">Robust Programming</span></span>  
 <span data-ttu-id="e5c6b-110">您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Brush>和<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c6b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5c6b-111">See also</span></span>
- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="e5c6b-112">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="e5c6b-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="e5c6b-113">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="e5c6b-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="e5c6b-114">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="e5c6b-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="e5c6b-115">GDI+ 中的筆刷和填滿的形狀</span><span class="sxs-lookup"><span data-stu-id="e5c6b-115">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
