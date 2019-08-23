---
title: 作法：使用 GDI 繪製文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956547"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="3809f-102">作法：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="3809f-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="3809f-103">透過<xref:System.Windows.Forms.TextRenderer.DrawText%2A> 類別<xref:System.Windows.Forms.TextRenderer>中的方法, 您可以存取 GDI 功能, 以在表單或控制項上繪製文字。</span><span class="sxs-lookup"><span data-stu-id="3809f-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="3809f-104">GDI 文字轉譯通常提供比 GDI + 更佳的效能和更精確的文字測量。</span><span class="sxs-lookup"><span data-stu-id="3809f-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3809f-105">列印時不支援<xref:System.Windows.Forms.TextRenderer>類別的方法。<xref:System.Windows.Forms.TextRenderer.DrawText%2A></span><span class="sxs-lookup"><span data-stu-id="3809f-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="3809f-106">列印時, 請一律使用<xref:System.Drawing.Graphics.DrawString%2A> <xref:System.Drawing.Graphics>類別的方法。</span><span class="sxs-lookup"><span data-stu-id="3809f-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3809f-107">範例</span><span class="sxs-lookup"><span data-stu-id="3809f-107">Example</span></span>  
 <span data-ttu-id="3809f-108">下列程式碼範例示範如何使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法, 在矩形內的多行上繪製文字。</span><span class="sxs-lookup"><span data-stu-id="3809f-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="3809f-109">若要使用<xref:System.Windows.Forms.TextRenderer>類別轉譯文字, 您<xref:System.Drawing.IDeviceContext>需要, 例如<xref:System.Drawing.Graphics>和 a <xref:System.Drawing.Font>、繪製文字的位置, 以及應該繪製的色彩。</span><span class="sxs-lookup"><span data-stu-id="3809f-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="3809f-110">(選擇性) 您可以使用<xref:System.Windows.Forms.TextFormatFlags>列舉來指定文字格式。</span><span class="sxs-lookup"><span data-stu-id="3809f-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="3809f-111">如需取得的<xref:System.Drawing.Graphics>詳細資訊, 請參閱[如何:建立繪圖](how-to-create-graphics-objects-for-drawing.md)的繪圖物件。</span><span class="sxs-lookup"><span data-stu-id="3809f-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="3809f-112">如需有關如何建立的<xref:System.Drawing.Font>詳細資訊[, 請參閱如何:結構字型家族和](how-to-construct-font-families-and-fonts.md)字型。</span><span class="sxs-lookup"><span data-stu-id="3809f-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3809f-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3809f-113">Compiling the Code</span></span>  
 <span data-ttu-id="3809f-114">上述程式碼範例的設計目的是要與 Windows Forms 搭配使用, 而且<xref:System.Windows.Forms.PaintEventArgs>它需要`e`, <xref:System.Windows.Forms.PaintEventHandler>這是的參數。</span><span class="sxs-lookup"><span data-stu-id="3809f-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3809f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3809f-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="3809f-116">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="3809f-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
