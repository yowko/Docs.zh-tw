---
title: HOW TO：對齊繪製的文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 0e77e4d8eeb9d7a07115b89525ac80074afeb6e8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323261"
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="8f2b8-102">HOW TO：對齊繪製的文字</span><span class="sxs-lookup"><span data-stu-id="8f2b8-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="8f2b8-103">當您執行自訂繪圖時，您通常可以在表單或控制項上的繪製的文字置中對齊。</span><span class="sxs-lookup"><span data-stu-id="8f2b8-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="8f2b8-104">您可以輕鬆地將以繪製文字的對齊<xref:System.Drawing.Graphics.DrawString%2A>或<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法藉由建立正確的格式物件，並設定適當的格式旗標。</span><span class="sxs-lookup"><span data-stu-id="8f2b8-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="8f2b8-105">若要繪製置中對齊文字使用 GDI + (DrawString)</span><span class="sxs-lookup"><span data-stu-id="8f2b8-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1. <span data-ttu-id="8f2b8-106">使用<xref:System.Drawing.StringFormat>與適當<xref:System.Drawing.Graphics.DrawString%2A>方法來指定置中對齊的文字。</span><span class="sxs-lookup"><span data-stu-id="8f2b8-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="8f2b8-107">若要繪製置中對齊文字使用 GDI (DrawText)</span><span class="sxs-lookup"><span data-stu-id="8f2b8-107">To draw centered text with GDI (DrawText)</span></span>  
  
1. <span data-ttu-id="8f2b8-108">使用<xref:System.Windows.Forms.TextFormatFlags>列舉型別換行，以及以垂直和水平置中與適當的文字<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8f2b8-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f2b8-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8f2b8-109">Compiling the Code</span></span>  
 <span data-ttu-id="8f2b8-110">上述程式碼範例專為搭配 Windows Form 使用，而且它們需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="8f2b8-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2b8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f2b8-111">See also</span></span>

- [<span data-ttu-id="8f2b8-112">HOW TO：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="8f2b8-112">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="8f2b8-113">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="8f2b8-113">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="8f2b8-114">HOW TO：建構字型家族和字型</span><span class="sxs-lookup"><span data-stu-id="8f2b8-114">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
