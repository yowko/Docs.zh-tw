---
title: 如何：在 Windows Form 上繪製實心矩形
description: 瞭解如何以程式設計方式在 Windows Form 上繪製填滿的矩形。 同時瞭解如何編譯您的程式碼。
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
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621635"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="1c7dd-104">如何：在 Windows Form 上繪製實心矩形</span><span class="sxs-lookup"><span data-stu-id="1c7dd-104">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="1c7dd-105">這個範例會在表單上繪製填滿的矩形。</span><span class="sxs-lookup"><span data-stu-id="1c7dd-105">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c7dd-106">範例</span><span class="sxs-lookup"><span data-stu-id="1c7dd-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c7dd-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1c7dd-107">Compiling the Code</span></span>  
 <span data-ttu-id="1c7dd-108">您無法在事件處理常式中呼叫這個方法 <xref:System.Windows.Forms.Form.Load> 。</span><span class="sxs-lookup"><span data-stu-id="1c7dd-108">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="1c7dd-109">如果表單已調整大小或遮蔽另一個表單，則不會重新繪製所繪製的內容。</span><span class="sxs-lookup"><span data-stu-id="1c7dd-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="1c7dd-110">若要自動重新繪製您的內容，您應該覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c7dd-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1c7dd-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1c7dd-111">Robust Programming</span></span>  
 <span data-ttu-id="1c7dd-112">您應該一律 <xref:System.IDisposable.Dispose%2A> 在取用系統資源的任何物件上呼叫，例如 <xref:System.Drawing.Brush> 和 <xref:System.Drawing.Graphics> 物件。</span><span class="sxs-lookup"><span data-stu-id="1c7dd-112">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7dd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c7dd-113">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="1c7dd-114">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="1c7dd-114">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="1c7dd-115">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="1c7dd-115">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1c7dd-116">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="1c7dd-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="1c7dd-117">GDI+ 中的筆刷和填滿的形狀</span><span class="sxs-lookup"><span data-stu-id="1c7dd-117">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
