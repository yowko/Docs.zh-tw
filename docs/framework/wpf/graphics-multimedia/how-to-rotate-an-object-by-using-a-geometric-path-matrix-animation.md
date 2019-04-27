---
title: HOW TO：使用幾何路徑旋轉物件 (矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 8f1b0ac42ea7509f8bc22b0bd2f50e2f96b5bee5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923392"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="211e8-102">HOW TO：使用幾何路徑旋轉物件 (矩陣動畫)</span><span class="sxs-lookup"><span data-stu-id="211e8-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="211e8-103">此範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>並<xref:System.Windows.Media.MatrixTransform>輪替 (powerpivot) 沿著幾何路徑所定義的物件<xref:System.Windows.Media.PathGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="211e8-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="211e8-104">範例</span><span class="sxs-lookup"><span data-stu-id="211e8-104">Example</span></span>  
 <span data-ttu-id="211e8-105">下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>來以動畫顯示的物件<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>。</span><span class="sxs-lookup"><span data-stu-id="211e8-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="211e8-106"><xref:System.Windows.Media.MatrixTransform>會套用至按鈕，使它沿著曲線路徑移動。</span><span class="sxs-lookup"><span data-stu-id="211e8-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="211e8-107">因為<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設定為`true`，矩形會沿著路徑的正切函數旋轉。</span><span class="sxs-lookup"><span data-stu-id="211e8-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="211e8-108">如需完整的範例，請參閱[路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="211e8-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="211e8-109">上述範例中使用的程式碼版本<xref:System.Windows.Media.Animation.Storyboard>來以動畫顯示<xref:System.Windows.Media.EllipseGeometry>，即使只有一張動畫已套用。</span><span class="sxs-lookup"><span data-stu-id="211e8-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="211e8-110">程式碼中的屬性套用單一動畫更簡單的方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="211e8-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="211e8-111">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="211e8-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211e8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="211e8-112">See also</span></span>

- [<span data-ttu-id="211e8-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="211e8-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="211e8-114">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="211e8-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="211e8-115">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="211e8-115">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
