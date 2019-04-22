---
title: HOW TO：繪製外框形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.DrawEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- drawing [Windows Forms], shapes
- circular shapes
- forms [Windows Forms], drawing circular shapes
- circles
- outlined shapes [Windows Forms], examples
- outlined shapes [Windows Forms], drawing
- drawing [Windows Forms], circular shapes
- shapes [Windows Forms], drawing
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
ms.openlocfilehash: 019bbc19cc4b26c42f8539eccd93ec4ff87fab12
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192197"
---
# <a name="how-to-draw-an-outlined-shape"></a><span data-ttu-id="49978-102">HOW TO：繪製外框形狀</span><span class="sxs-lookup"><span data-stu-id="49978-102">How to: Draw an Outlined Shape</span></span>
<span data-ttu-id="49978-103">此範例會在表單上繪製外框的橢圓形和矩形。</span><span class="sxs-lookup"><span data-stu-id="49978-103">This example draws outlined ellipses and rectangles on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49978-104">範例</span><span class="sxs-lookup"><span data-stu-id="49978-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49978-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="49978-105">Compiling the Code</span></span>  
 <span data-ttu-id="49978-106">您不能呼叫這個方法<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="49978-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="49978-107">如果調整大小或遮蔽另一種形式的表單時，將不會重新繪製的繪製的內容。</span><span class="sxs-lookup"><span data-stu-id="49978-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="49978-108">若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="49978-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="49978-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="49978-109">Robust Programming</span></span>  
 <span data-ttu-id="49978-110">您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Pen>和<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="49978-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49978-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49978-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawEllipse%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Graphics.DrawRectangle%2A>
- [<span data-ttu-id="49978-112">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="49978-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="49978-113">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="49978-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="49978-114">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="49978-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
