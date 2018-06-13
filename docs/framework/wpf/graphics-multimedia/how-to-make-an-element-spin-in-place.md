---
title: 如何：使項目就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a37952af621c79d231b45a247c92d3576a533580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562507"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="828a2-102">如何：使項目就地旋轉</span><span class="sxs-lookup"><span data-stu-id="828a2-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="828a2-103">這個範例示範如何讓項目使用微調<xref:System.Windows.Media.RotateTransform>和<xref:System.Windows.Media.Animation.DoubleAnimation>。</span><span class="sxs-lookup"><span data-stu-id="828a2-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="828a2-104">下列範例會套用<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="828a2-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="828a2-105">此範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫方式顯示<xref:System.Windows.Media.RotateTransform.Angle%2A>的<xref:System.Windows.Media.RotateTransform>。</span><span class="sxs-lookup"><span data-stu-id="828a2-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="828a2-106">若要進行微調位置中的項目，範例會設定<xref:System.Windows.UIElement.RenderTransformOrigin%2A>點 （0.5，0.5） 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="828a2-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="828a2-107">範例</span><span class="sxs-lookup"><span data-stu-id="828a2-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="828a2-108">如需完整的範例中，包含多個轉換的範例，請參閱[2d 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="828a2-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828a2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="828a2-109">See Also</span></span>  
 [<span data-ttu-id="828a2-110">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="828a2-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="828a2-111">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="828a2-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
