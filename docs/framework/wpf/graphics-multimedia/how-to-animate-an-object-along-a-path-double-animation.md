---
title: "操作說明：沿著路徑建立物件的動畫 (Double 動畫)"
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
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a461b741675a18ac1e3544b17a9bbe9a8d18547
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="b59ff-102">操作說明：沿著路徑建立物件的動畫 (Double 動畫)</span><span class="sxs-lookup"><span data-stu-id="b59ff-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="b59ff-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>移動物件沿著路徑所定義的類別<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="b59ff-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b59ff-104">範例</span><span class="sxs-lookup"><span data-stu-id="b59ff-104">Example</span></span>  
 <span data-ttu-id="b59ff-105">下列範例會使用兩個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>物件來移動矩形幾何路徑：</span><span class="sxs-lookup"><span data-stu-id="b59ff-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="b59ff-106">第一個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>繪製<xref:System.Windows.Media.TranslateTransform.X%2A>的<xref:System.Windows.Media.TranslateTransform>套用至矩形。</span><span class="sxs-lookup"><span data-stu-id="b59ff-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="b59ff-107">它會使矩形沿著路徑水平移動。</span><span class="sxs-lookup"><span data-stu-id="b59ff-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="b59ff-108">第二個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>繪製<xref:System.Windows.Media.TranslateTransform.Y%2A>的<xref:System.Windows.Media.TranslateTransform>套用至矩形。</span><span class="sxs-lookup"><span data-stu-id="b59ff-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="b59ff-109">它會使矩形沿著路徑垂直移動。</span><span class="sxs-lookup"><span data-stu-id="b59ff-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="b59ff-110">如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="b59ff-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="b59ff-111">若要使用幾何路徑移動物件的另一種方式是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件。</span><span class="sxs-lookup"><span data-stu-id="b59ff-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="b59ff-112">如需範例，請參閱[動畫物件沿著路徑 （矩陣動畫）](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)。</span><span class="sxs-lookup"><span data-stu-id="b59ff-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b59ff-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b59ff-113">See Also</span></span>  
 [<span data-ttu-id="b59ff-114">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="b59ff-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b59ff-115">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="b59ff-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
