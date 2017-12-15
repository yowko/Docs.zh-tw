---
title: "如何：在指定的位置繪製文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe6e8563b19ef18b89ad970f3ca35bf5f0782a32
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="b66ff-102">如何：在指定的位置繪製文字</span><span class="sxs-lookup"><span data-stu-id="b66ff-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="b66ff-103">當您執行自訂繪圖時，您可以在單一的水平列，從指定的點開始繪製文字。</span><span class="sxs-lookup"><span data-stu-id="b66ff-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="b66ff-104">您也可以使用這種方式繪製文字<xref:System.Drawing.Graphics.DrawString%2A>多載方法的<xref:System.Drawing.Graphics>類別接受<xref:System.Drawing.Point>或<xref:System.Drawing.PointF>參數。</span><span class="sxs-lookup"><span data-stu-id="b66ff-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="b66ff-105"><xref:System.Drawing.Graphics.DrawString%2A>方法也需要<xref:System.Drawing.Brush>和<xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="b66ff-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="b66ff-106">您也可以使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>多載方法的<xref:System.Windows.Forms.TextRenderer>採用<xref:System.Drawing.Point>。</span><span class="sxs-lookup"><span data-stu-id="b66ff-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="b66ff-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A>也需要<xref:System.Drawing.Color>和<xref:System.Drawing.Font>。</span><span class="sxs-lookup"><span data-stu-id="b66ff-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="b66ff-108">下圖顯示當您使用時，在指定的點繪製的文字輸出<xref:System.Drawing.Graphics.DrawString%2A>多載的方法。</span><span class="sxs-lookup"><span data-stu-id="b66ff-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 <span data-ttu-id="b66ff-109">![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span><span class="sxs-lookup"><span data-stu-id="b66ff-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span></span>  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="b66ff-110">若要繪製的一行文字 GDI +</span><span class="sxs-lookup"><span data-stu-id="b66ff-110">To draw a line of text with GDI+</span></span>  
  
1.  <span data-ttu-id="b66ff-111">使用<xref:System.Drawing.Graphics.DrawString%2A>方法，傳遞您想要的選項，的文字<xref:System.Drawing.Point>或<xref:System.Drawing.PointF>， <xref:System.Drawing.Font>，和<xref:System.Drawing.Brush>。</span><span class="sxs-lookup"><span data-stu-id="b66ff-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="b66ff-112">若要繪製的一行文字 GDI</span><span class="sxs-lookup"><span data-stu-id="b66ff-112">To draw a line of text with GDI</span></span>  
  
1.  <span data-ttu-id="b66ff-113">使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法，傳遞您想要的選項，的文字<xref:System.Drawing.Point>， <xref:System.Drawing.Font>，和<xref:System.Drawing.Color>。</span><span class="sxs-lookup"><span data-stu-id="b66ff-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b66ff-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b66ff-114">Compiling the Code</span></span>  
 <span data-ttu-id="b66ff-115">先前的範例需要：</span><span class="sxs-lookup"><span data-stu-id="b66ff-115">The previous examples require:</span></span>  
  
-   <span data-ttu-id="b66ff-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="b66ff-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b66ff-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b66ff-117">See Also</span></span>  
 [<span data-ttu-id="b66ff-118">操作說明：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="b66ff-118">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="b66ff-119">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="b66ff-119">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="b66ff-120">操作說明：建構字型系列和字型</span><span class="sxs-lookup"><span data-stu-id="b66ff-120">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [<span data-ttu-id="b66ff-121">操作說明：在矩形中繪製被包圍的文字</span><span class="sxs-lookup"><span data-stu-id="b66ff-121">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
