---
title: 操作說明：使用幾何路徑旋轉物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186868"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="af5ed-102">操作說明：使用幾何路徑旋轉物件</span><span class="sxs-lookup"><span data-stu-id="af5ed-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="af5ed-103">此示例演示如何沿<xref:System.Windows.Media.PathGeometry>由物件定義的幾何路徑旋轉（透視）物件。</span><span class="sxs-lookup"><span data-stu-id="af5ed-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af5ed-104">範例</span><span class="sxs-lookup"><span data-stu-id="af5ed-104">Example</span></span>  
 <span data-ttu-id="af5ed-105">下面的示例使用三<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>個物件沿幾何路徑移動矩形。</span><span class="sxs-lookup"><span data-stu-id="af5ed-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
- <span data-ttu-id="af5ed-106">第一<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>個<xref:System.Windows.Media.RotateTransform>動畫為應用於矩形的 。</span><span class="sxs-lookup"><span data-stu-id="af5ed-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="af5ed-107">動畫會產生角度值。</span><span class="sxs-lookup"><span data-stu-id="af5ed-107">The animation generates angle values.</span></span> <span data-ttu-id="af5ed-108">它會使矩形沿著路徑的輪廓旋轉 (繞樞軸轉動)。</span><span class="sxs-lookup"><span data-stu-id="af5ed-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
- <span data-ttu-id="af5ed-109">其他兩個物件為<xref:System.Windows.Media.TranslateTransform.X%2A>應用於<xref:System.Windows.Media.TranslateTransform.Y%2A>矩形的<xref:System.Windows.Media.TranslateTransform>和 值設置動畫。</span><span class="sxs-lookup"><span data-stu-id="af5ed-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="af5ed-110">它們使矩形沿著路徑水平及垂直移動。</span><span class="sxs-lookup"><span data-stu-id="af5ed-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="af5ed-111">使用幾何路徑旋轉物件的另一種方法是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件並將其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="af5ed-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="af5ed-112">有關詳細資訊和示例，請參閱[使用幾何路徑旋轉物件（矩陣動畫）。](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)</span><span class="sxs-lookup"><span data-stu-id="af5ed-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="af5ed-113">有關完整示例，請參閱[路徑動畫示例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。</span><span class="sxs-lookup"><span data-stu-id="af5ed-113">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5ed-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af5ed-114">See also</span></span>

- [<span data-ttu-id="af5ed-115">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="af5ed-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="af5ed-116">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="af5ed-116">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="af5ed-117">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="af5ed-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
