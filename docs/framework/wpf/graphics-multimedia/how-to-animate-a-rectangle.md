---
title: HOW TO：建立矩形動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], rectangles
- rectangles [WPF], animating
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
ms.openlocfilehash: dbff015bdc5f9ce56d2c366e0d348429efb7f4b5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305151"
---
# <a name="how-to-animate-a-rectangle"></a><span data-ttu-id="fc73f-102">HOW TO：建立矩形動畫</span><span class="sxs-lookup"><span data-stu-id="fc73f-102">How to: Animate a Rectangle</span></span>
<span data-ttu-id="fc73f-103">這個範例示範如何以動畫顯示矩形的大小和位置變更。</span><span class="sxs-lookup"><span data-stu-id="fc73f-103">This example shows how to animate changes to the size and position of a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc73f-104">範例</span><span class="sxs-lookup"><span data-stu-id="fc73f-104">Example</span></span>  
 <span data-ttu-id="fc73f-105">下列範例使用的執行個體<xref:System.Windows.Media.Animation.RectAnimation>類別以動畫顯示<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>，其中以動畫顯示矩形的位置和大小的變更。</span><span class="sxs-lookup"><span data-stu-id="fc73f-105">The following example uses an instance of the <xref:System.Windows.Media.Animation.RectAnimation> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>, which animates changes to the size and position of the rectangle.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fc73f-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc73f-106">See also</span></span>
- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [<span data-ttu-id="fc73f-107">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="fc73f-107">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="fc73f-108">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="fc73f-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="fc73f-109">圖形 how to 主題</span><span class="sxs-lookup"><span data-stu-id="fc73f-109">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="fc73f-110">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="fc73f-110">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
