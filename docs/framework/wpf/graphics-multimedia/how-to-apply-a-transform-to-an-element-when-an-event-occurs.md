---
title: HOW TO：在事件發生時套用轉換至項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 3862ffcb8e0dcabd2de67c495204470ac9fa6c14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726386"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="969b9-102">HOW TO：在事件發生時套用轉換至項目</span><span class="sxs-lookup"><span data-stu-id="969b9-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="969b9-103">此範例示範如何套用<xref:System.Windows.Media.ScaleTransform>事件發生時。</span><span class="sxs-lookup"><span data-stu-id="969b9-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="969b9-104">這裡所示範的概念，與您用來套用其他類型轉換的概念相同。</span><span class="sxs-lookup"><span data-stu-id="969b9-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="969b9-105">如需可用的轉換類型的詳細資訊，請參閱<xref:System.Windows.Media.Transform>類別或[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="969b9-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
 <span data-ttu-id="969b9-106">您可以透過下列兩種方式其中之一，將轉換套用至元素：</span><span class="sxs-lookup"><span data-stu-id="969b9-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
-   <span data-ttu-id="969b9-107">如果您這樣做*未*希望轉換影響版面配置，請使用<xref:System.Windows.UIElement.RenderTransform%2A>項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="969b9-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
-   <span data-ttu-id="969b9-108">如果您希望轉換影響版面配置，使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="969b9-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="969b9-109">下列範例會套用<xref:System.Windows.Media.ScaleTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>按鈕的屬性。</span><span class="sxs-lookup"><span data-stu-id="969b9-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="969b9-110">當滑鼠移至按鈕，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>並<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>的屬性<xref:System.Windows.Media.ScaleTransform>設定為`2`，這會使按鈕變得越來越大。</span><span class="sxs-lookup"><span data-stu-id="969b9-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="969b9-111">當滑鼠移動按鈕，關閉<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>並<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>設定為`1`，這會使按鈕回到其原始大小。</span><span class="sxs-lookup"><span data-stu-id="969b9-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="969b9-112">範例</span><span class="sxs-lookup"><span data-stu-id="969b9-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="969b9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="969b9-113">See also</span></span>
- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="969b9-114">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="969b9-114">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="969b9-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="969b9-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
- [<span data-ttu-id="969b9-116">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="969b9-116">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
