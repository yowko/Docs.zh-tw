---
title: "操作說明：沿著路徑建立物件的動畫 (點動畫)"
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
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399d6b8028b8715f38335089a723707657df4a98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="a186d-102">操作說明：沿著路徑建立物件的動畫 (點動畫)</span><span class="sxs-lookup"><span data-stu-id="a186d-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="a186d-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>要繪製動畫物件<xref:System.Windows.Point>沿著曲線的路徑。</span><span class="sxs-lookup"><span data-stu-id="a186d-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a186d-104">範例</span><span class="sxs-lookup"><span data-stu-id="a186d-104">Example</span></span>  
 <span data-ttu-id="a186d-105">下列範例會移動<xref:System.Windows.Media.EllipseGeometry>沿著路徑所定義<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="a186d-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a186d-106">橢圓形的幾何<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性，其中需要<xref:System.Windows.Point>值，指定其位置; 將橢圓形的幾何，您以動畫顯示其<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a186d-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="a186d-107">此範例會使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry>物件的<xref:System.Windows.Media.EllipseGeometry.Center%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a186d-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="a186d-108">如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="a186d-108">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="a186d-109">使用上述範例的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry>，即使只有一個動畫已套用。</span><span class="sxs-lookup"><span data-stu-id="a186d-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="a186d-110">A<xref:System.Windows.Media.Animation.Storyboard>通常是最簡單的方式套用多個動畫，因為這些動畫可以控制相同<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="a186d-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="a186d-111">不過，使用程式碼時，單一的動畫套用至屬性的簡單方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a186d-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="a186d-112">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="a186d-112">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a186d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="a186d-113">See Also</span></span>  
 [<span data-ttu-id="a186d-114">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="a186d-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="a186d-115">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a186d-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a186d-116">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="a186d-116">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
