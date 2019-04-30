---
title: HOW TO：繪製包含線條頭尾圖案的線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: c4a78569f6c0b14c32154611412d6b3ccd8a84ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004196"
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="193be-102">HOW TO：繪製包含線條頭尾圖案的線條</span><span class="sxs-lookup"><span data-stu-id="193be-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="193be-103">您可以在其中一種稱為線條帽緣的數個圖形中繪製的開頭或行結尾。</span><span class="sxs-lookup"><span data-stu-id="193be-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="193be-104">支援數個線條端點，例如循、 正方形、 菱形、 和箭頭。</span><span class="sxs-lookup"><span data-stu-id="193be-104">supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="193be-105">範例</span><span class="sxs-lookup"><span data-stu-id="193be-105">Example</span></span>  
 <span data-ttu-id="193be-106">您可以指定開始的行 （開始端點），最後一行 （結束端點） 或以虛線 (dash cap) 的連字號的線條端點。</span><span class="sxs-lookup"><span data-stu-id="193be-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="193be-107">下列範例會繪製含有某一端點上的箭頭和圓形的帽緣，另一端的線條。</span><span class="sxs-lookup"><span data-stu-id="193be-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="193be-108">圖例中顯示產生的列：</span><span class="sxs-lookup"><span data-stu-id="193be-108">The illustration shows the resulting line:</span></span>  
  
 ![圖例會顯示一條具有圓端點。](./media/how-to-draw-a-line-with-line-caps/line-cap-arrowhead-example.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="193be-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="193be-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="193be-111">建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="193be-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="193be-112">範例程式碼到貼<xref:System.Windows.Forms.Control.Paint>傳遞的事件處理常式`e`做為<xref:System.Windows.Forms.PaintEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="193be-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193be-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="193be-113">See also</span></span>

- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [<span data-ttu-id="193be-114">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="193be-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="193be-115">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="193be-115">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
