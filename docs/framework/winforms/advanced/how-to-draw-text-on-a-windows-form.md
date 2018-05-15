---
title: 如何：在 Windows Form 上繪製文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: 9369a4ed26107bdc395d455ba6fb8420fd895d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-text-on-a-windows-form"></a><span data-ttu-id="72106-102">如何：在 Windows Form 上繪製文字</span><span class="sxs-lookup"><span data-stu-id="72106-102">How to: Draw Text on a Windows Form</span></span>
<span data-ttu-id="72106-103">下列程式碼範例示範如何使用<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>表單上繪製文字。</span><span class="sxs-lookup"><span data-stu-id="72106-103">The following code example shows how to use the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> to draw text on a form.</span></span> <span data-ttu-id="72106-104">或者，您可以使用<xref:System.Windows.Forms.TextRenderer>的表單上繪製文字。</span><span class="sxs-lookup"><span data-stu-id="72106-104">Alternatively, you can use <xref:System.Windows.Forms.TextRenderer> for drawing text on a form.</span></span> <span data-ttu-id="72106-105">如需詳細資訊，請參閱[How to： 使用 GDI 繪製的文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)。</span><span class="sxs-lookup"><span data-stu-id="72106-105">For more information, see [How to: Draw Text with GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72106-106">範例</span><span class="sxs-lookup"><span data-stu-id="72106-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72106-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="72106-107">Compiling the Code</span></span>  
 <span data-ttu-id="72106-108">您不能呼叫<xref:System.Drawing.Graphics.DrawString%2A>方法中的<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="72106-108">You cannot call the <xref:System.Drawing.Graphics.DrawString%2A> method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="72106-109">如果調整大小或遮蔽另一種形式的形式，將不會重新繪製內容。</span><span class="sxs-lookup"><span data-stu-id="72106-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="72106-110">若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="72106-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="72106-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="72106-111">Robust Programming</span></span>  
 <span data-ttu-id="72106-112">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="72106-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="72106-113">新細明體字型未安裝。</span><span class="sxs-lookup"><span data-stu-id="72106-113">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72106-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72106-114">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="72106-115">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="72106-115">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="72106-116">操作說明：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="72106-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
