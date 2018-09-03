---
title: 如何：使項目就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 56385d7c31465e25f19486ea5cdaa8876cdb30ff
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461627"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="167bb-102">如何：使項目就地旋轉</span><span class="sxs-lookup"><span data-stu-id="167bb-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="167bb-103">此範例示範如何讓組織使用的項目<xref:System.Windows.Media.RotateTransform>和<xref:System.Windows.Media.Animation.DoubleAnimation>。</span><span class="sxs-lookup"><span data-stu-id="167bb-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="167bb-104">下列範例會套用<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="167bb-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="167bb-105">此範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>來建立動畫<xref:System.Windows.Media.RotateTransform.Angle%2A>的<xref:System.Windows.Media.RotateTransform>。</span><span class="sxs-lookup"><span data-stu-id="167bb-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="167bb-106">此範例會設定讓項目就地微調， <xref:System.Windows.UIElement.RenderTransformOrigin%2A> （0.5，0.5） 的點項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="167bb-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="167bb-107">範例</span><span class="sxs-lookup"><span data-stu-id="167bb-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="167bb-108">如需完整的範例中，包含更多轉換範例，請參閱[2d 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="167bb-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167bb-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="167bb-109">See Also</span></span>  
 [<span data-ttu-id="167bb-110">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="167bb-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="167bb-111">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="167bb-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
