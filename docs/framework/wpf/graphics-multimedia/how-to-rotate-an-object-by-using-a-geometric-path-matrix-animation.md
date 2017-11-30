---
title: "操作說明：使用幾何路徑旋轉物件 (矩陣動畫)"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c624b221c1e4c122728887a9d592a3275d8f8e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="3d3ce-102">操作說明：使用幾何路徑旋轉物件 (矩陣動畫)</span><span class="sxs-lookup"><span data-stu-id="3d3ce-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="3d3ce-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>和<xref:System.Windows.Media.MatrixTransform>旋轉 (pivot) 的物件所定義的幾何路徑<xref:System.Windows.Media.PathGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d3ce-104">範例</span><span class="sxs-lookup"><span data-stu-id="3d3ce-104">Example</span></span>  
 <span data-ttu-id="3d3ce-105">下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>要繪製動畫物件<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="3d3ce-106"><xref:System.Windows.Media.MatrixTransform>套用至按鈕，並讓它沿著曲線路徑移動。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="3d3ce-107">因為<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設定為`true`，矩形會沿著路徑的正切函數旋轉。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="3d3ce-108">如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-108">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="3d3ce-109">使用上述範例的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>以動畫方式顯示<xref:System.Windows.Media.EllipseGeometry>，即使只有一個動畫已套用。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="3d3ce-110">將單一動畫套用至程式碼中屬性的簡單方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="3d3ce-111">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="3d3ce-111">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3ce-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d3ce-112">See Also</span></span>  
 [<span data-ttu-id="3d3ce-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="3d3ce-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="3d3ce-114">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="3d3ce-114">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)  
 [<span data-ttu-id="3d3ce-115">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="3d3ce-115">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)
