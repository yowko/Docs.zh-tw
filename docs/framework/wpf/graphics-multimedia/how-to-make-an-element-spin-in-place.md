---
title: 如何：使項目就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452788"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="d4e68-102">如何：使項目就地旋轉</span><span class="sxs-lookup"><span data-stu-id="d4e68-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="d4e68-103">這個範例示範如何使用 <xref:System.Windows.Media.RotateTransform> 和 <xref:System.Windows.Media.Animation.DoubleAnimation>，讓元素微調。</span><span class="sxs-lookup"><span data-stu-id="d4e68-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="d4e68-104">下列範例會將 <xref:System.Windows.Media.RotateTransform> 套用至元素的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d4e68-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="d4e68-105">此範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 來建立 <xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.Angle%2A> 的動畫。</span><span class="sxs-lookup"><span data-stu-id="d4e68-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="d4e68-106">為了讓元素就地旋轉，此範例會將元素的 <xref:System.Windows.UIElement.RenderTransformOrigin%2A> 屬性設定為點（0.5、0.5）。</span><span class="sxs-lookup"><span data-stu-id="d4e68-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4e68-107">範例</span><span class="sxs-lookup"><span data-stu-id="d4e68-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="d4e68-108">如需包含更多轉換範例的完整範例，請參閱[2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。</span><span class="sxs-lookup"><span data-stu-id="d4e68-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e68-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4e68-109">See also</span></span>

- [<span data-ttu-id="d4e68-110">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="d4e68-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="d4e68-111">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="d4e68-111">Transforms Overview</span></span>](transforms-overview.md)
