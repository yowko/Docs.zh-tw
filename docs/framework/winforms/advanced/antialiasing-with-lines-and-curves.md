---
title: "線條和曲線的反鋸齒功能"
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="b9d55-102">線條和曲線的反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="b9d55-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="b9d55-103">當您使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪製一條線，您提供的起點和結束點的行，但您沒有提供在列上的任何資訊的個別像素。</span><span class="sxs-lookup"><span data-stu-id="b9d55-103">When you use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="b9d55-104">顯示驅動程式軟體，以判斷哪一個像素為單位將會開啟以特定顯示裝置上顯示線與搭配運作。</span><span class="sxs-lookup"><span data-stu-id="b9d55-104"> works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="b9d55-105">別名</span><span class="sxs-lookup"><span data-stu-id="b9d55-105">Aliasing</span></span>  
 <span data-ttu-id="b9d55-106">請考慮直接紅線，會從點 （4，2） 移至的點 （16，10）。</span><span class="sxs-lookup"><span data-stu-id="b9d55-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="b9d55-107">假設座標系統的原點位於左上角和度量單位為像素。</span><span class="sxs-lookup"><span data-stu-id="b9d55-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="b9d55-108">也假設，x 軸指向右側，而 y 軸向下。</span><span class="sxs-lookup"><span data-stu-id="b9d55-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="b9d55-109">下圖顯示彩色的背景上繪製紅線放大的的檢視。</span><span class="sxs-lookup"><span data-stu-id="b9d55-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="b9d55-110">![線條，無反鋸齒](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="b9d55-110">![Line, no antialiasing](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="b9d55-111">用來呈現線條的紅色像素是不透明的。</span><span class="sxs-lookup"><span data-stu-id="b9d55-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="b9d55-112">行中有不透明的像素。</span><span class="sxs-lookup"><span data-stu-id="b9d55-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="b9d55-113">這種類型的行呈現所產生的線條不規則的外觀，並看起來有點像階梯。</span><span class="sxs-lookup"><span data-stu-id="b9d55-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="b9d55-114">代表的階梯線條的這項技術稱為別名。階梯是理論行的別名。</span><span class="sxs-lookup"><span data-stu-id="b9d55-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="b9d55-115">反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="b9d55-115">Antialiasing</span></span>  
 <span data-ttu-id="b9d55-116">繪製線條更趨精密完美的技術包含使用透明的像素，以及不透明的像素為單位。</span><span class="sxs-lookup"><span data-stu-id="b9d55-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="b9d55-117">像素為單位設定為純紅色，或紅和背景色彩混合體，根據如何關閉它們是列。</span><span class="sxs-lookup"><span data-stu-id="b9d55-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="b9d55-118">這種類型的呈現稱為反鋸齒功能，而導致人類的眼睛感知為更平滑線。</span><span class="sxs-lookup"><span data-stu-id="b9d55-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="b9d55-119">下圖顯示如何在背景產生鋸齒線條與混合特定像素為單位。</span><span class="sxs-lookup"><span data-stu-id="b9d55-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="b9d55-120">![消除鋸齒線條](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="b9d55-120">![Antialiasing a Line](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="b9d55-121">反鋸齒功能，也稱為 平滑，也可以套用至曲線。</span><span class="sxs-lookup"><span data-stu-id="b9d55-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="b9d55-122">下圖顯示放大平滑的橢圓形的檢視。</span><span class="sxs-lookup"><span data-stu-id="b9d55-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="b9d55-123">![消除鋸齒曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="b9d55-123">![Antialiasing Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="b9d55-124">下圖顯示相同的橢圓形的實際大小，一次進行反鋸齒處理而一次使用反鋸齒功能。</span><span class="sxs-lookup"><span data-stu-id="b9d55-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="b9d55-125">![反鋸齒功能範例](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="b9d55-125">![Antialiasing example](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="b9d55-126">若要繪製的直線和曲線使用消除鋸齒，建立的執行個體<xref:System.Drawing.Graphics>類別並設定其<xref:System.Drawing.Graphics.SmoothingMode%2A>屬性<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>或<xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>。</span><span class="sxs-lookup"><span data-stu-id="b9d55-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="b9d55-127">然後呼叫其中一個繪圖的方法相同<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="b9d55-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="b9d55-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d55-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [<span data-ttu-id="b9d55-129">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="b9d55-129">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="b9d55-130">操作說明：使用文字反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="b9d55-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
