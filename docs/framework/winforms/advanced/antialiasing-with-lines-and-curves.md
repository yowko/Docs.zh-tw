---
title: 線條和曲線的反鋸齒功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
ms.openlocfilehash: 871c5cb3cd9356f677633acb04fe82021a9787c5
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506145"
---
# <a name="antialiasing-with-lines-and-curves"></a><span data-ttu-id="def55-102">線條和曲線的反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="def55-102">Antialiasing with Lines and Curves</span></span>
<span data-ttu-id="def55-103">當您使用 GDI + 繪製一條線時，您提供的起點和結束點的行，但您沒有提供任何資訊的個別像素，該行。</span><span class="sxs-lookup"><span data-stu-id="def55-103">When you use GDI+ to draw a line, you provide the starting point and ending point of the line, but you do not have to provide any information about the individual pixels on the line.</span></span> <span data-ttu-id="def55-104">GDI + 顯示驅動程式軟體，以判斷哪一個像素為單位將會開啟至特定顯示裝置上顯示的列一起運作。</span><span class="sxs-lookup"><span data-stu-id="def55-104">GDI+ works in conjunction with the display driver software to determine which pixels will be turned on to show the line on a particular display device.</span></span>  
  
## <a name="aliasing"></a><span data-ttu-id="def55-105">別名</span><span class="sxs-lookup"><span data-stu-id="def55-105">Aliasing</span></span>  
 <span data-ttu-id="def55-106">請考慮直接紅線從點 （4，2） 進入點 （16，10）。</span><span class="sxs-lookup"><span data-stu-id="def55-106">Consider the straight red line that goes from the point (4, 2) to the point (16, 10).</span></span> <span data-ttu-id="def55-107">假設座標系統的原點位於左上角和測量單位為像素。</span><span class="sxs-lookup"><span data-stu-id="def55-107">Assume the coordinate system has its origin in the upper-left corner and that the unit of measure is the pixel.</span></span> <span data-ttu-id="def55-108">也假設，x 軸指向右側，而 y 軸往下。</span><span class="sxs-lookup"><span data-stu-id="def55-108">Also assume that the x-axis points to the right and the y-axis points down.</span></span> <span data-ttu-id="def55-109">下圖顯示彩色背景上繪製的紅線放大的的檢視。</span><span class="sxs-lookup"><span data-stu-id="def55-109">The following illustration shows an enlarged view of the red line drawn on a multicolored background.</span></span>  
  
 <span data-ttu-id="def55-110">![行，不使用反鋸齒](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span><span class="sxs-lookup"><span data-stu-id="def55-110">![Line, no antialiasing](./media/aboutgdip02-art33.gif "AboutGdip02_Art33")</span></span>  
  
 <span data-ttu-id="def55-111">紅色的像素，用來轉譯線條是不透明的。</span><span class="sxs-lookup"><span data-stu-id="def55-111">The red pixels used to render the line are opaque.</span></span> <span data-ttu-id="def55-112">行中有任何半透明的像素為單位。</span><span class="sxs-lookup"><span data-stu-id="def55-112">There are no partially transparent pixels in the line.</span></span> <span data-ttu-id="def55-113">這種類型的一行轉譯所產生的線條有不規則的外觀和該行看起來有點像階梯。</span><span class="sxs-lookup"><span data-stu-id="def55-113">This type of line rendering gives the line a jagged appearance, and the line looks somewhat like a staircase.</span></span> <span data-ttu-id="def55-114">這項技術會代表某一行的階梯稱為別名;階梯是在假設線的別名。</span><span class="sxs-lookup"><span data-stu-id="def55-114">This technique of representing a line with a staircase is called aliasing; the staircase is an alias for the theoretical line.</span></span>  
  
## <a name="antialiasing"></a><span data-ttu-id="def55-115">消除鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="def55-115">Antialiasing</span></span>  
 <span data-ttu-id="def55-116">繪製線條的更複雜的技術牽涉到使用不透明的像素為單位以及部分透明像素為單位。</span><span class="sxs-lookup"><span data-stu-id="def55-116">A more sophisticated technique for rendering a line involves using partially transparent pixels along with opaque pixels.</span></span> <span data-ttu-id="def55-117">像素為單位設定為純紅色或紅色和背景色彩的混合體，以根據接近行。</span><span class="sxs-lookup"><span data-stu-id="def55-117">Pixels are set to pure red, or to some blend of red and the background color, depending on how close they are to the line.</span></span> <span data-ttu-id="def55-118">這種類型的轉譯稱為反鋸齒功能，而導致人們的眼睛視為較平滑的列。</span><span class="sxs-lookup"><span data-stu-id="def55-118">This type of rendering is called antialiasing and results in a line that the human eye perceives as more smooth.</span></span> <span data-ttu-id="def55-119">下圖顯示如何將特定的像素為單位混合與背景以產生反鋸齒線條。</span><span class="sxs-lookup"><span data-stu-id="def55-119">The following illustration shows how certain pixels are blended with the background to produce an antialiased line.</span></span>  
  
 <span data-ttu-id="def55-120">![消除鋸齒線條](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span><span class="sxs-lookup"><span data-stu-id="def55-120">![Antialiasing a Line](./media/aboutgdip02-art34.gif "AboutGdip02_Art34")</span></span>  
  
 <span data-ttu-id="def55-121">消除鋸齒功能，也稱為 平滑處理，也可以套用至曲線。</span><span class="sxs-lookup"><span data-stu-id="def55-121">Antialiasing, also called smoothing, can also be applied to curves.</span></span> <span data-ttu-id="def55-122">下圖顯示平滑的橢圓形的放大的檢視。</span><span class="sxs-lookup"><span data-stu-id="def55-122">The following illustration shows an enlarged view of a smoothed ellipse.</span></span>  
  
 <span data-ttu-id="def55-123">![消除鋸齒曲線](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span><span class="sxs-lookup"><span data-stu-id="def55-123">![Antialiasing Curves](./media/aboutgdip02-art35.gif "AboutGdip02_Art35")</span></span>  
  
 <span data-ttu-id="def55-124">下圖顯示相同的橢圓形的實際大小，一次沒有反鋸齒功能，另一次使用反鋸齒功能。</span><span class="sxs-lookup"><span data-stu-id="def55-124">The following illustration shows the same ellipse in its actual size, once without antialiasing and once with antialiasing.</span></span>  
  
 <span data-ttu-id="def55-125">![反鋸齒功能範例](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span><span class="sxs-lookup"><span data-stu-id="def55-125">![Antialiasing example](./media/aboutgdip02-art36.gif "AboutGdip02_Art36")</span></span>  
  
 <span data-ttu-id="def55-126">若要繪製的直線和曲線，使用反鋸齒功能，建立的執行個體<xref:System.Drawing.Graphics>類別，並設定其<xref:System.Drawing.Graphics.SmoothingMode%2A>屬性設<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>或<xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>。</span><span class="sxs-lookup"><span data-stu-id="def55-126">To draw lines and curves that use antialiasing, create an instance of the <xref:System.Drawing.Graphics> class and set its <xref:System.Drawing.Graphics.SmoothingMode%2A> property to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> or <xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>.</span></span> <span data-ttu-id="def55-127">然後呼叫其中一個繪圖的方法相同<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="def55-127">Then call one of the drawing methods of that same <xref:System.Drawing.Graphics> class.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#81](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a><span data-ttu-id="def55-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="def55-128">See also</span></span>

- <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>
- [<span data-ttu-id="def55-129">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="def55-129">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="def55-130">如何：使用文字反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="def55-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)
