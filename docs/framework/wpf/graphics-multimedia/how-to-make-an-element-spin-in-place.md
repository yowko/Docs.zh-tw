---
title: 如何：使項目就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112072"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="1cd28-102">如何：使項目就地旋轉</span><span class="sxs-lookup"><span data-stu-id="1cd28-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="1cd28-103">此示例演示如何使用 和<xref:System.Windows.Media.RotateTransform>使元素旋轉。 <xref:System.Windows.Media.Animation.DoubleAnimation></span><span class="sxs-lookup"><span data-stu-id="1cd28-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="1cd28-104">下面的示例將 應用於<xref:System.Windows.Media.RotateTransform><xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cd28-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="1cd28-105">該示例使用<xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform></span><span class="sxs-lookup"><span data-stu-id="1cd28-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="1cd28-106">要使元素就位旋轉，該示例將元素的屬性設置<xref:System.Windows.UIElement.RenderTransformOrigin%2A>到點 （0.5， 0.5）。</span><span class="sxs-lookup"><span data-stu-id="1cd28-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd28-107">範例</span><span class="sxs-lookup"><span data-stu-id="1cd28-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="1cd28-108">有關包含更多變換示例的完整示例，請參閱[2D 變換示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。</span><span class="sxs-lookup"><span data-stu-id="1cd28-108">For the complete sample, which includes more transformation examples, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd28-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cd28-109">See also</span></span>

- [<span data-ttu-id="1cd28-110">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="1cd28-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1cd28-111">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="1cd28-111">Transforms Overview</span></span>](transforms-overview.md)
