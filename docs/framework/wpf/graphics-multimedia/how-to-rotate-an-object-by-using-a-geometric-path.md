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
ms.openlocfilehash: 5a73ee967be0aae7dc3f1ef82229c2bcb2f9ade2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560712"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="9ac96-102">操作說明：使用幾何路徑旋轉物件</span><span class="sxs-lookup"><span data-stu-id="9ac96-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="9ac96-103">這個範例示範如何旋轉物件所定義的幾何路徑沿著<xref:System.Windows.Media.PathGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="9ac96-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ac96-104">範例</span><span class="sxs-lookup"><span data-stu-id="9ac96-104">Example</span></span>  
 <span data-ttu-id="9ac96-105">下列範例會使用三個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>物件來移動矩形幾何的路徑。</span><span class="sxs-lookup"><span data-stu-id="9ac96-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="9ac96-106">第一個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>繪製<xref:System.Windows.Media.RotateTransform>套用至矩形。</span><span class="sxs-lookup"><span data-stu-id="9ac96-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="9ac96-107">動畫會產生角度值。</span><span class="sxs-lookup"><span data-stu-id="9ac96-107">The animation generates angle values.</span></span> <span data-ttu-id="9ac96-108">它會使矩形沿著路徑的輪廓旋轉 (繞樞軸轉動)。</span><span class="sxs-lookup"><span data-stu-id="9ac96-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="9ac96-109">其他兩個物件以動畫顯示<xref:System.Windows.Media.TranslateTransform.X%2A>和<xref:System.Windows.Media.TranslateTransform.Y%2A>值<xref:System.Windows.Media.TranslateTransform>套用至矩形。</span><span class="sxs-lookup"><span data-stu-id="9ac96-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="9ac96-110">它們使矩形沿著路徑水平及垂直移動。</span><span class="sxs-lookup"><span data-stu-id="9ac96-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="9ac96-111">使用幾何路徑旋轉物件的另一種方式是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件，並設定其<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="9ac96-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="9ac96-112">如需詳細資訊和範例，請參閱[旋轉物件使用幾何的路徑 （矩陣動畫）](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)。</span><span class="sxs-lookup"><span data-stu-id="9ac96-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="9ac96-113">如需完整範例，請參閱[路徑動畫範例](http://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="9ac96-113">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac96-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ac96-114">See Also</span></span>  
 [<span data-ttu-id="9ac96-115">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="9ac96-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="9ac96-116">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="9ac96-116">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="9ac96-117">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="9ac96-117">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
