---
title: 如何：建立 BorderThickness 值的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124659"
---
# <a name="how-to-animate-a-borderthickness-value"></a><span data-ttu-id="a3cad-102">如何：建立 BorderThickness 值的動畫</span><span class="sxs-lookup"><span data-stu-id="a3cad-102">How to: Animate a BorderThickness Value</span></span>
<span data-ttu-id="a3cad-103">這個範例示範如何使用 <xref:System.Windows.Media.Animation.ThicknessAnimation> 類別，以動畫顯示框線粗細的變更。</span><span class="sxs-lookup"><span data-stu-id="a3cad-103">This example shows how to animate changes to the thickness of a border by using the <xref:System.Windows.Media.Animation.ThicknessAnimation> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3cad-104">範例</span><span class="sxs-lookup"><span data-stu-id="a3cad-104">Example</span></span>  
 <span data-ttu-id="a3cad-105">下列範例會使用 <xref:System.Windows.Media.Animation.ThicknessAnimation>以動畫呈現框線的粗細。</span><span class="sxs-lookup"><span data-stu-id="a3cad-105">The following example animates the thickness of a border by using <xref:System.Windows.Media.Animation.ThicknessAnimation>.</span></span> <span data-ttu-id="a3cad-106">此範例使用 <xref:System.Windows.Controls.Border>的 <xref:System.Windows.Controls.Border.BorderThickness%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a3cad-106">The example uses the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 <span data-ttu-id="a3cad-107">如需完整範例，請參閱[動畫範例庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。</span><span class="sxs-lookup"><span data-stu-id="a3cad-107">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cad-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3cad-108">See also</span></span>

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [<span data-ttu-id="a3cad-109">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a3cad-109">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="a3cad-110">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="a3cad-110">Animation and Timing How-to Topics</span></span>](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="a3cad-111">使用主要畫面格建立框線粗細的動畫</span><span class="sxs-lookup"><span data-stu-id="a3cad-111">Animate the Thickness of a Border by Using Key Frames</span></span>](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
