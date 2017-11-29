---
title: "如何：繪製包含線條帽緣的線條"
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
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e2d5a5aba4a7634e0ea8480aa9744a5a7b9721d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="41c85-102">如何：繪製包含線條帽緣的線條</span><span class="sxs-lookup"><span data-stu-id="41c85-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="41c85-103">您可以繪製開頭或行尾的其中一種稱為線條頭尾圖案的數個圖形。</span><span class="sxs-lookup"><span data-stu-id="41c85-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="41c85-104">支援數個線條頭尾圖案，例如循、 正方形、 菱形和箭頭。</span><span class="sxs-lookup"><span data-stu-id="41c85-104"> supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41c85-105">範例</span><span class="sxs-lookup"><span data-stu-id="41c85-105">Example</span></span>  
 <span data-ttu-id="41c85-106">您可以指定開始行 (開始 cap)，最後一行 （結束端點） 或虛線 (虛線 cap) 的虛線的線條端點。</span><span class="sxs-lookup"><span data-stu-id="41c85-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="41c85-107">下列範例會繪製直線箭頭一端與另一端的圓端點。</span><span class="sxs-lookup"><span data-stu-id="41c85-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="41c85-108">圖例中顯示產生的列：</span><span class="sxs-lookup"><span data-stu-id="41c85-108">The illustration shows the resulting line:</span></span>  
  
 <span data-ttu-id="41c85-109">![畫筆](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span><span class="sxs-lookup"><span data-stu-id="41c85-109">![Pens](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41c85-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="41c85-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="41c85-111">建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="41c85-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="41c85-112">將範例程式碼到<xref:System.Windows.Forms.Control.Paint>傳遞的事件處理常式`e`為<xref:System.Windows.Forms.PaintEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="41c85-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c85-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41c85-113">See Also</span></span>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [<span data-ttu-id="41c85-114">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="41c85-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="41c85-115">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="41c85-115">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
