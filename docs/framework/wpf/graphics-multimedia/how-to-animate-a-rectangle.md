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
ms.openlocfilehash: 7f7cf24f7883553329de3761ff0670e8e3a09463
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151004"
---
# <a name="how-to-animate-a-rectangle"></a><span data-ttu-id="c56b4-102">HOW TO：建立矩形動畫</span><span class="sxs-lookup"><span data-stu-id="c56b4-102">How to: Animate a Rectangle</span></span>
<span data-ttu-id="c56b4-103">這個範例示範如何以動畫顯示矩形的大小和位置變更。</span><span class="sxs-lookup"><span data-stu-id="c56b4-103">This example shows how to animate changes to the size and position of a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c56b4-104">範例</span><span class="sxs-lookup"><span data-stu-id="c56b4-104">Example</span></span>  
 <span data-ttu-id="c56b4-105">下列範例使用的執行個體<xref:System.Windows.Media.Animation.RectAnimation>類別以動畫顯示<xref:System.Windows.Media.RectangleGeometry.Rect%2A>屬性<xref:System.Windows.Media.RectangleGeometry>，其中以動畫顯示矩形的位置和大小的變更。</span><span class="sxs-lookup"><span data-stu-id="c56b4-105">The following example uses an instance of the <xref:System.Windows.Media.Animation.RectAnimation> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>, which animates changes to the size and position of the rectangle.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c56b4-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c56b4-106">See also</span></span>

- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [<span data-ttu-id="c56b4-107">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="c56b4-107">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="c56b4-108">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="c56b4-108">Graphics and Multimedia</span></span>](index.md)
- [<span data-ttu-id="c56b4-109">圖形 how to 主題</span><span class="sxs-lookup"><span data-stu-id="c56b4-109">Graphics How-to Topics</span></span>](graphics-how-to-topics.md)
- [<span data-ttu-id="c56b4-110">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="c56b4-110">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
