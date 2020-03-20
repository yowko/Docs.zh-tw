---
title: 操作說明：使用幾何路徑旋轉物件 (矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187419"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="3dad0-102">操作說明：使用幾何路徑旋轉物件 (矩陣動畫)</span><span class="sxs-lookup"><span data-stu-id="3dad0-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="3dad0-103">此示例演示如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>和 a<xref:System.Windows.Media.MatrixTransform>沿<xref:System.Windows.Media.PathGeometry>物件定義的幾何路徑旋轉（透視）物件。</span><span class="sxs-lookup"><span data-stu-id="3dad0-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dad0-104">範例</span><span class="sxs-lookup"><span data-stu-id="3dad0-104">Example</span></span>  
 <span data-ttu-id="3dad0-105">下面的示例使用 物件<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>為 屬性<xref:System.Windows.Media.MatrixTransform>設置<xref:System.Windows.Media.MatrixTransform.Matrix%2A>動畫。</span><span class="sxs-lookup"><span data-stu-id="3dad0-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="3dad0-106"><xref:System.Windows.Media.MatrixTransform>應用於按鈕，使其沿曲線路徑移動。</span><span class="sxs-lookup"><span data-stu-id="3dad0-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="3dad0-107">由於<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設置為`true`，矩形沿路徑的切線旋轉。</span><span class="sxs-lookup"><span data-stu-id="3dad0-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="3dad0-108">有關完整示例，請參閱[路徑動畫示例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。</span><span class="sxs-lookup"><span data-stu-id="3dad0-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="3dad0-109">前面的示例的代碼版本使用<xref:System.Windows.Media.Animation.Storyboard>為<xref:System.Windows.Media.EllipseGeometry>（） 設置動畫，即使只應用了一個動畫。</span><span class="sxs-lookup"><span data-stu-id="3dad0-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="3dad0-110">將單個動畫應用於代碼中的屬性的一種更簡單的方法是使用 方法<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>。</span><span class="sxs-lookup"><span data-stu-id="3dad0-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="3dad0-111">例如，請參閱[在不使用分鏡腳本的情況下為屬性設置動畫](how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="3dad0-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dad0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dad0-112">See also</span></span>

- [<span data-ttu-id="3dad0-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="3dad0-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="3dad0-114">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="3dad0-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="3dad0-115">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="3dad0-115">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
