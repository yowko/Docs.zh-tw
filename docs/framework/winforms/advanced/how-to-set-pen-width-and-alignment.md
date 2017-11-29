---
title: "如何：設定畫筆寬度和對齊"
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
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ed2a28c49554c686abb5e2635ab35b746b83465
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="c0a56-102">如何：設定畫筆寬度和對齊</span><span class="sxs-lookup"><span data-stu-id="c0a56-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="c0a56-103">當您建立<xref:System.Drawing.Pen>，您可以做為其中一個建構函式的引數提供的畫筆寬度。</span><span class="sxs-lookup"><span data-stu-id="c0a56-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="c0a56-104">您也可以變更畫筆寬度<xref:System.Drawing.Pen.Width%2A>屬性<xref:System.Drawing.Pen>類別。</span><span class="sxs-lookup"><span data-stu-id="c0a56-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="c0a56-105">理論上的線條的寬度為 0。</span><span class="sxs-lookup"><span data-stu-id="c0a56-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="c0a56-106">當您繪製一條線來 1 個像素寬時，像素會置於理論的線條。</span><span class="sxs-lookup"><span data-stu-id="c0a56-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="c0a56-107">如果您繪製一條線來為多個像素寬，像素為單位是置於理論的線條，或顯示理論上一行的另一端。</span><span class="sxs-lookup"><span data-stu-id="c0a56-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="c0a56-108">您可以設定的畫筆對齊屬性<xref:System.Drawing.Pen>來決定如何將使用該畫筆繪製的像素放置相對於理論的行。</span><span class="sxs-lookup"><span data-stu-id="c0a56-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="c0a56-109">值<xref:System.Drawing.Drawing2D.PenAlignment.Center>， <xref:System.Drawing.Drawing2D.PenAlignment.Outset>，和<xref:System.Drawing.Drawing2D.PenAlignment.Inset>會出現在下列程式碼範例屬於<xref:System.Drawing.Drawing2D.PenAlignment>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="c0a56-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="c0a56-110">下列程式碼範例會繪製一條線兩次： 一次使用黑色畫筆寬度為 1，另一次使用的綠色的畫筆寬度為 10。</span><span class="sxs-lookup"><span data-stu-id="c0a56-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="c0a56-111">若要改變的畫筆寬度</span><span class="sxs-lookup"><span data-stu-id="c0a56-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="c0a56-112">值設定<xref:System.Drawing.Pen.Alignment%2A>屬性<xref:System.Drawing.Drawing2D.PenAlignment.Center>（預設值） 來指定將在該行理論上置中以綠色的畫筆繪製的像素為單位。</span><span class="sxs-lookup"><span data-stu-id="c0a56-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="c0a56-113">下圖顯示產生的線條。</span><span class="sxs-lookup"><span data-stu-id="c0a56-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="c0a56-114">![畫筆](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="c0a56-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="c0a56-115">下列程式碼範例會繪製矩形兩次： 一次使用黑色畫筆寬度為 1，另一次使用的綠色的畫筆寬度為 10。</span><span class="sxs-lookup"><span data-stu-id="c0a56-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="c0a56-116">若要變更畫筆對齊</span><span class="sxs-lookup"><span data-stu-id="c0a56-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="c0a56-117">值設定<xref:System.Drawing.Pen.Alignment%2A>屬性<xref:System.Drawing.Drawing2D.PenAlignment.Center>來指定將在矩形的界限上置中以綠色的畫筆繪製的像素。</span><span class="sxs-lookup"><span data-stu-id="c0a56-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="c0a56-118">下圖顯示產生的矩形。</span><span class="sxs-lookup"><span data-stu-id="c0a56-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="c0a56-119">![畫筆](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="c0a56-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="c0a56-120">若要建立內凹畫筆</span><span class="sxs-lookup"><span data-stu-id="c0a56-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="c0a56-121">變更綠色畫筆的對齊方式，藉由修改上述的程式碼範例中的第三個陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c0a56-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="c0a56-122">現在的像素寬的綠色列中會出現在矩形內部下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c0a56-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="c0a56-123">![畫筆](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="c0a56-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0a56-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0a56-124">See Also</span></span>  
 [<span data-ttu-id="c0a56-125">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="c0a56-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="c0a56-126">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="c0a56-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
