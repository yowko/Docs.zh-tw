---
title: HOW TO：在矩形中繪製被包圍的文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 5c4e76cda37527d0167b21c0d206749ba6dab4a9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708856"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="5594a-102">HOW TO：在矩形中繪製被包圍的文字</span><span class="sxs-lookup"><span data-stu-id="5594a-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="5594a-103">您也可以使用在矩形中繪製換行的文字<xref:System.Drawing.Graphics.DrawString%2A>方法的多載化<xref:System.Drawing.Graphics>類別<xref:System.Drawing.Rectangle>或<xref:System.Drawing.RectangleF>參數。</span><span class="sxs-lookup"><span data-stu-id="5594a-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="5594a-104">您也會使用<xref:System.Drawing.Brush>和<xref:System.Drawing.Font>。</span><span class="sxs-lookup"><span data-stu-id="5594a-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="5594a-105">您也可以繪製的矩形中換行的文字，使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法的多載化<xref:System.Windows.Forms.TextRenderer>採用<xref:System.Drawing.Rectangle>和<xref:System.Windows.Forms.TextFormatFlags>參數。</span><span class="sxs-lookup"><span data-stu-id="5594a-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="5594a-106">您也會使用<xref:System.Drawing.Color>和<xref:System.Drawing.Font>。</span><span class="sxs-lookup"><span data-stu-id="5594a-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="5594a-107">下圖顯示當您使用的矩形中繪製的文字輸出<xref:System.Drawing.Graphics.DrawString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5594a-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method.</span></span>  
  
 <span data-ttu-id="5594a-108">![字型文字](./media/csfontstext2.png "csfontstext2")</span><span class="sxs-lookup"><span data-stu-id="5594a-108">![Fonts Text](./media/csfontstext2.png "csfontstext2")</span></span>  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="5594a-109">若要繪製被包圍的文字中使用 GDI + 的矩形</span><span class="sxs-lookup"><span data-stu-id="5594a-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="5594a-110">使用<xref:System.Drawing.Graphics.DrawString%2A>多載方法，傳遞您想要的文字<xref:System.Drawing.Rectangle>或是<xref:System.Drawing.RectangleF>，<xref:System.Drawing.Font>和<xref:System.Drawing.Brush>。</span><span class="sxs-lookup"><span data-stu-id="5594a-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="5594a-111">若要繪製被包圍的文字中使用 GDI 矩形</span><span class="sxs-lookup"><span data-stu-id="5594a-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="5594a-112">使用<xref:System.Windows.Forms.TextFormatFlags>列舉值，以指定的文字應該以包裝<xref:System.Windows.Forms.TextRenderer.DrawText%2A>多載方法，傳遞您想要的文字<xref:System.Drawing.Rectangle>，<xref:System.Drawing.Font>和<xref:System.Drawing.Color>。</span><span class="sxs-lookup"><span data-stu-id="5594a-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5594a-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5594a-113">Compiling the Code</span></span>  
 <span data-ttu-id="5594a-114">先前的範例需要：</span><span class="sxs-lookup"><span data-stu-id="5594a-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="5594a-115"><xref:System.Windows.Forms.PaintEventArgs> `e`這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="5594a-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5594a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5594a-116">See also</span></span>
- [<span data-ttu-id="5594a-117">如何：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="5594a-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="5594a-118">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="5594a-118">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="5594a-119">如何：建構字型系列和字型</span><span class="sxs-lookup"><span data-stu-id="5594a-119">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="5594a-120">如何：在指定的位置繪製文字</span><span class="sxs-lookup"><span data-stu-id="5594a-120">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)
