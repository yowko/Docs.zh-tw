---
title: HOW TO：使用 GDI 繪製文字
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
ms.openlocfilehash: d4bf72998c798040451b814a7f0287bca65f5300
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781481"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="b433c-102">HOW TO：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="b433c-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="b433c-103">具有<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法中的<xref:System.Windows.Forms.TextRenderer>類別，您可以存取[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]表單或控制項上繪製文字的功能。</span><span class="sxs-lookup"><span data-stu-id="b433c-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] <span data-ttu-id="b433c-104">文字轉譯通常提供較佳的效能和更精確的文字比測量[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b433c-104">text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b433c-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法的<xref:System.Windows.Forms.TextRenderer>類別不支援列印。</span><span class="sxs-lookup"><span data-stu-id="b433c-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="b433c-106">列印時，一律使用<xref:System.Drawing.Graphics.DrawString%2A>方法的<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="b433c-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b433c-107">範例</span><span class="sxs-lookup"><span data-stu-id="b433c-107">Example</span></span>  
 <span data-ttu-id="b433c-108">下列程式碼範例示範如何在多行內的矩形，使用上繪製文字<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b433c-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="b433c-109">要呈現的文字<xref:System.Windows.Forms.TextRenderer>類別，您需要<xref:System.Drawing.IDeviceContext>，例如<xref:System.Drawing.Graphics>和<xref:System.Drawing.Font>，來繪製文字，並在其中它應該繪製的色彩的位置。</span><span class="sxs-lookup"><span data-stu-id="b433c-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="b433c-110">您可以選擇性地指定格式化所使用的文字<xref:System.Windows.Forms.TextFormatFlags>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b433c-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="b433c-111">如需取得詳細資訊<xref:System.Drawing.Graphics>，請參閱[How to:建立繪圖的圖形物件](how-to-create-graphics-objects-for-drawing.md)。</span><span class="sxs-lookup"><span data-stu-id="b433c-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="b433c-112">如需有關建構<xref:System.Drawing.Font>，請參閱[How to:建構字型系列和字型](how-to-construct-font-families-and-fonts.md)。</span><span class="sxs-lookup"><span data-stu-id="b433c-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b433c-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b433c-113">Compiling the Code</span></span>  
 <span data-ttu-id="b433c-114">上述程式碼範例專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="b433c-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b433c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b433c-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="b433c-116">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="b433c-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
