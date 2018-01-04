---
title: "如何：使用畫筆繪製矩形"
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
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7257fa21432ec5d849a257f4a5e412515f474363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a><span data-ttu-id="26770-102">如何：使用畫筆繪製矩形</span><span class="sxs-lookup"><span data-stu-id="26770-102">How to: Use a Pen to Draw Rectangles</span></span>
<span data-ttu-id="26770-103">若要繪製的矩形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="26770-103">To draw rectangles, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="26770-104"><xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.DrawRectangle%2A>方法，而<xref:System.Drawing.Pen>物件儲存的行，例如色彩和寬度的功能。</span><span class="sxs-lookup"><span data-stu-id="26770-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26770-105">範例</span><span class="sxs-lookup"><span data-stu-id="26770-105">Example</span></span>  
 <span data-ttu-id="26770-106">下列範例會繪製在其左上角的矩形 （10，10）。</span><span class="sxs-lookup"><span data-stu-id="26770-106">The following example draws a rectangle with its upper-left corner at (10, 10).</span></span> <span data-ttu-id="26770-107">矩形的寬度為 100，高度為 50。</span><span class="sxs-lookup"><span data-stu-id="26770-107">The rectangle has a width of 100 and a height of 50.</span></span> <span data-ttu-id="26770-108">第二個引數傳遞給<xref:System.Drawing.Pen.%23ctor%2A>建構函式表示畫筆寬度為 5 像素。</span><span class="sxs-lookup"><span data-stu-id="26770-108">The second argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor indicates that the pen width is 5 pixels.</span></span>  
  
 <span data-ttu-id="26770-109">繪製矩形，畫筆內置矩形的界限上。</span><span class="sxs-lookup"><span data-stu-id="26770-109">When the rectangle is drawn, the pen is centered on the rectangle's boundary.</span></span> <span data-ttu-id="26770-110">矩形的側邊的畫筆寬度為 5，因為會繪製 5 像素寬、 這類繪製 1 個像素界限，2 個像素繪製在內部和外部繪製 2 像素為單位。</span><span class="sxs-lookup"><span data-stu-id="26770-110">Because the pen width is 5, the sides of the rectangle are drawn 5 pixels wide, such that 1 pixel is drawn on the boundary itself, 2 pixels are drawn on the inside, and 2 pixels are drawn on the outside.</span></span> <span data-ttu-id="26770-111">如需有關畫筆對齊的詳細資訊，請參閱[How to： 設定畫筆寬度和對齊](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)。</span><span class="sxs-lookup"><span data-stu-id="26770-111">For more details on pen alignment, see [How to: Set Pen Width and Alignment](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).</span></span>  
  
 <span data-ttu-id="26770-112">下圖顯示產生的矩形。</span><span class="sxs-lookup"><span data-stu-id="26770-112">The following illustration shows the resulting rectangle.</span></span> <span data-ttu-id="26770-113">虛線顯示，其中會有已繪製矩形如果畫筆寬度便是一個像素。</span><span class="sxs-lookup"><span data-stu-id="26770-113">The dotted lines show where the rectangle would have been drawn if the pen width had been one pixel.</span></span> <span data-ttu-id="26770-114">矩形左上角的放大的檢視顯示黑色粗線會置於虛線。</span><span class="sxs-lookup"><span data-stu-id="26770-114">The enlarged view of the upper-left corner of the rectangle shows that the thick black lines are centered on those dotted lines.</span></span>  
  
 <span data-ttu-id="26770-115">![畫筆](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span><span class="sxs-lookup"><span data-stu-id="26770-115">![Pens](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26770-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="26770-116">Compiling the Code</span></span>  
 <span data-ttu-id="26770-117">上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="26770-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26770-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="26770-118">See Also</span></span>  
 [<span data-ttu-id="26770-119">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="26770-119">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
