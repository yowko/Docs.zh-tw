---
title: HOW TO：設定畫筆寬度和對齊方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: d1a465fb7c1cd6d4064a077e592daefebf590714
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564821"
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="558dd-102">HOW TO：設定畫筆寬度和對齊方式</span><span class="sxs-lookup"><span data-stu-id="558dd-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="558dd-103">當您建立<xref:System.Drawing.Pen>，您可以提供畫筆寬度作為建構函式的引數之一。</span><span class="sxs-lookup"><span data-stu-id="558dd-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="558dd-104">您也可以變更畫筆寬度<xref:System.Drawing.Pen.Width%2A>屬性<xref:System.Drawing.Pen>類別。</span><span class="sxs-lookup"><span data-stu-id="558dd-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="558dd-105">假設線條的寬度為 0。</span><span class="sxs-lookup"><span data-stu-id="558dd-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="558dd-106">當您繪製一條線是 1 個像素寬時，像素會在假設線條上置中對齊。</span><span class="sxs-lookup"><span data-stu-id="558dd-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="558dd-107">如果您繪製多個像素寬的線條，像素為單位可能是在假設線條上置中或出現在假設線的一端。</span><span class="sxs-lookup"><span data-stu-id="558dd-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="558dd-108">您可以設定的畫筆對齊屬性<xref:System.Drawing.Pen>來判斷如何使用該畫筆繪製的像素會放置相對於理論的行。</span><span class="sxs-lookup"><span data-stu-id="558dd-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="558dd-109">值<xref:System.Drawing.Drawing2D.PenAlignment.Center>， <xref:System.Drawing.Drawing2D.PenAlignment.Outset>，並<xref:System.Drawing.Drawing2D.PenAlignment.Inset>出現在下列程式碼範例屬於<xref:System.Drawing.Drawing2D.PenAlignment>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="558dd-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="558dd-110">下列程式碼範例會繪製一條線兩次： 一次使用黑色畫筆的寬度為 1，另一次以綠色畫筆的寬度為 10。</span><span class="sxs-lookup"><span data-stu-id="558dd-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="558dd-111">變更畫筆的寬度</span><span class="sxs-lookup"><span data-stu-id="558dd-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="558dd-112">設定的值<xref:System.Drawing.Pen.Alignment%2A>屬性設<xref:System.Drawing.Drawing2D.PenAlignment.Center>（預設值），指定將在假設線條上置中以綠色的畫筆繪製的像素為單位。</span><span class="sxs-lookup"><span data-stu-id="558dd-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="558dd-113">下圖顯示產生的列。</span><span class="sxs-lookup"><span data-stu-id="558dd-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="558dd-114">![畫筆](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="558dd-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="558dd-115">下列程式碼範例會繪製矩形兩次： 一次使用黑色畫筆的寬度為 1，另一次以綠色畫筆的寬度為 10。</span><span class="sxs-lookup"><span data-stu-id="558dd-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="558dd-116">若要變更畫筆的對齊方式</span><span class="sxs-lookup"><span data-stu-id="558dd-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="558dd-117">設定的值<xref:System.Drawing.Pen.Alignment%2A>屬性設<xref:System.Drawing.Drawing2D.PenAlignment.Center>來指定將在矩形的界限上置中以綠色的畫筆繪製的像素。</span><span class="sxs-lookup"><span data-stu-id="558dd-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="558dd-118">下圖顯示產生的矩形。</span><span class="sxs-lookup"><span data-stu-id="558dd-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="558dd-119">![畫筆](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="558dd-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="558dd-120">若要建立插頁畫筆</span><span class="sxs-lookup"><span data-stu-id="558dd-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="558dd-121">變更綠色手寫筆的對齊方式，藉由修改上述的程式碼範例中的第三個陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="558dd-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="558dd-122">現在的像素寬的綠色列中會出現在矩形內部如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="558dd-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="558dd-123">![畫筆](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="558dd-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="558dd-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="558dd-124">See also</span></span>
- [<span data-ttu-id="558dd-125">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="558dd-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="558dd-126">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="558dd-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
