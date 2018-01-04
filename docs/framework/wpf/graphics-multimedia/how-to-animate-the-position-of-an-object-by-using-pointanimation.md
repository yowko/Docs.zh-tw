---
title: "操作說明：使用 PointAnimation 建立物件位置的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baa412a889ee82c9bf20ff1d6420d8a86f339ca6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="d6aae-102">操作說明：使用 PointAnimation 建立物件位置的動畫</span><span class="sxs-lookup"><span data-stu-id="d6aae-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="d6aae-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimation>類別以動畫方式顯示物件沿著<xref:System.Windows.Shapes.Path>。</span><span class="sxs-lookup"><span data-stu-id="d6aae-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6aae-104">範例</span><span class="sxs-lookup"><span data-stu-id="d6aae-104">Example</span></span>  
 <span data-ttu-id="d6aae-105">下列範例會沿著移動橢圓形<xref:System.Windows.Shapes.Path>從另一個螢幕上的一個點。</span><span class="sxs-lookup"><span data-stu-id="d6aae-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="d6aae-106">此範例的位置以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry>使用<xref:System.Windows.Media.Animation.PointAnimation>以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d6aae-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d6aae-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6aae-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [<span data-ttu-id="d6aae-108">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="d6aae-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="d6aae-109">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="d6aae-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [<span data-ttu-id="d6aae-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="d6aae-110">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [<span data-ttu-id="d6aae-111">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="d6aae-111">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="d6aae-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="d6aae-112">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
