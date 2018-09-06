---
title: 操作說明：使用 PointAnimation 建立物件位置的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 91447685988d91dfe86707c2cf265deabeb717b9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036661"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="71521-102">操作說明：使用 PointAnimation 建立物件位置的動畫</span><span class="sxs-lookup"><span data-stu-id="71521-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="71521-103">此範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimation>類別以動畫顯示物件沿著<xref:System.Windows.Shapes.Path>。</span><span class="sxs-lookup"><span data-stu-id="71521-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71521-104">範例</span><span class="sxs-lookup"><span data-stu-id="71521-104">Example</span></span>  
 <span data-ttu-id="71521-105">下列範例會沿著移動橢圓形<xref:System.Windows.Shapes.Path>從另一個畫面上的一個點。</span><span class="sxs-lookup"><span data-stu-id="71521-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="71521-106">此範例以動畫顯示的位置<xref:System.Windows.Media.EllipseGeometry>利用<xref:System.Windows.Media.Animation.PointAnimation>來以動畫顯示<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="71521-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="71521-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71521-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [<span data-ttu-id="71521-108">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="71521-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="71521-109">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="71521-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [<span data-ttu-id="71521-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="71521-110">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [<span data-ttu-id="71521-111">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="71521-111">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="71521-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="71521-112">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
