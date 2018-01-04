---
title: "操作說明：沿著路徑建立物件的動畫 (矩陣動畫)"
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
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb1bbe43c7e1797d5943bf3da6b4aca22a11c3a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="e8489-102">操作說明：沿著路徑建立物件的動畫 (矩陣動畫)</span><span class="sxs-lookup"><span data-stu-id="e8489-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="e8489-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>以動畫方式顯示物件沿著路徑所定義的類別<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="e8489-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8489-104">範例</span><span class="sxs-lookup"><span data-stu-id="e8489-104">Example</span></span>  
 <span data-ttu-id="e8489-105">下列範例會執行下列動作，沿著路徑以動畫顯示的物件︰</span><span class="sxs-lookup"><span data-stu-id="e8489-105">The following example animates an object along a path by doing the following:</span></span>  
  
-   <span data-ttu-id="e8489-106">適用於<xref:System.Windows.Media.MatrixTransform>以便移動該物件。</span><span class="sxs-lookup"><span data-stu-id="e8489-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
-   <span data-ttu-id="e8489-107">使用定義的路徑<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="e8489-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
-   <span data-ttu-id="e8489-108">建立<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>並使用它來建立動畫<xref:System.Windows.Media.Matrix>屬性<xref:System.Windows.Media.MatrixTransform>。</span><span class="sxs-lookup"><span data-stu-id="e8489-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="e8489-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>採用<xref:System.Windows.Media.PathGeometry>並用來產生<xref:System.Windows.Media.Matrix>值。</span><span class="sxs-lookup"><span data-stu-id="e8489-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="e8489-110">如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="e8489-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="e8489-111">如需幾何路徑的詳細資訊，請參閱[幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e8489-111">For more information about geometric paths, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8489-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e8489-112">See Also</span></span>  
 [<span data-ttu-id="e8489-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="e8489-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e8489-114">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="e8489-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="e8489-115">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="e8489-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
