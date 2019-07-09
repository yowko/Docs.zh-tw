---
title: HOW TO：扭曲元素
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: cf770a284238826852e788e27f3b3f329ed0269f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664090"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="2ec66-102">作法：扭曲元素</span><span class="sxs-lookup"><span data-stu-id="2ec66-102">How to: Skew an Element</span></span>
<span data-ttu-id="2ec66-103">此範例示範如何使用<xref:System.Windows.Media.SkewTransform>來扭曲元素。</span><span class="sxs-lookup"><span data-stu-id="2ec66-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="2ec66-104">扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。</span><span class="sxs-lookup"><span data-stu-id="2ec66-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="2ec66-105">典型的用途之一<xref:System.Windows.Media.SkewTransform>會模擬 3d 2d 物件中的深度。</span><span class="sxs-lookup"><span data-stu-id="2ec66-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3-D depth in 2-D objects.</span></span>  
  
 <span data-ttu-id="2ec66-106">使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>並<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性，以指定中心點的<xref:System.Windows.Media.SkewTransform>。</span><span class="sxs-lookup"><span data-stu-id="2ec66-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="2ec66-107">使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定的 x 軸和 y 軸扭曲角度，以及目前座標系統沿著這些軸的扭曲。</span><span class="sxs-lookup"><span data-stu-id="2ec66-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="2ec66-108">若要預測扭曲轉換的效果，請考慮，<xref:System.Windows.Media.SkewTransform.AngleX%2A>扭曲 x 軸值相對於原始座標系統。</span><span class="sxs-lookup"><span data-stu-id="2ec66-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="2ec66-109">因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>是 30，y 軸旋轉 30 度穿過原點，x-從該原點 30 度的值扭曲。</span><span class="sxs-lookup"><span data-stu-id="2ec66-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="2ec66-110">同樣地， <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 個圖形的 y 值扭曲 30 度，從原始伺服器。</span><span class="sxs-lookup"><span data-stu-id="2ec66-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="2ec66-111">請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。</span><span class="sxs-lookup"><span data-stu-id="2ec66-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="2ec66-112">下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (0，0)。</span><span class="sxs-lookup"><span data-stu-id="2ec66-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ec66-113">範例</span><span class="sxs-lookup"><span data-stu-id="2ec66-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="2ec66-114">下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。</span><span class="sxs-lookup"><span data-stu-id="2ec66-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="2ec66-115">下列範例會以 45 度的垂直扭曲套用<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。</span><span class="sxs-lookup"><span data-stu-id="2ec66-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="2ec66-116">下圖顯示本範例所使用的不同扭曲。</span><span class="sxs-lookup"><span data-stu-id="2ec66-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="2ec66-117">![SkewTransform 範例](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="2ec66-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="2ec66-118">三個 SkewTransform 範例的示意圖</span><span class="sxs-lookup"><span data-stu-id="2ec66-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="2ec66-119">如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="2ec66-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec66-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ec66-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="2ec66-121">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="2ec66-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="2ec66-122">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="2ec66-122">How-to Topics</span></span>](transformations-how-to-topics.md)
