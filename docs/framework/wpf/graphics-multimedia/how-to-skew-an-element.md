---
title: HOW TO：扭曲元素
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 47f671f493e7b379c36f9bf4b50ec9d185d10b8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144959"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="34e3e-102">HOW TO：扭曲元素</span><span class="sxs-lookup"><span data-stu-id="34e3e-102">How to: Skew an Element</span></span>
<span data-ttu-id="34e3e-103">此範例示範如何使用<xref:System.Windows.Media.SkewTransform>來扭曲元素。</span><span class="sxs-lookup"><span data-stu-id="34e3e-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="34e3e-104">扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。</span><span class="sxs-lookup"><span data-stu-id="34e3e-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="34e3e-105">一般用途<xref:System.Windows.Media.SkewTransform>會模擬[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]深度[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="34e3e-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="34e3e-106">使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>並<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性，以指定中心點的<xref:System.Windows.Media.SkewTransform>。</span><span class="sxs-lookup"><span data-stu-id="34e3e-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="34e3e-107">使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定的 x 軸和 y 軸扭曲角度，以及目前座標系統沿著這些軸的扭曲。</span><span class="sxs-lookup"><span data-stu-id="34e3e-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="34e3e-108">若要預測扭曲轉換的效果，請考慮，<xref:System.Windows.Media.SkewTransform.AngleX%2A>扭曲 x 軸值相對於原始座標系統。</span><span class="sxs-lookup"><span data-stu-id="34e3e-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="34e3e-109">因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>是 30，y 軸旋轉 30 度穿過原點，x-從該原點 30 度的值扭曲。</span><span class="sxs-lookup"><span data-stu-id="34e3e-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="34e3e-110">同樣地， <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 個圖形的 y 值扭曲 30 度，從原始伺服器。</span><span class="sxs-lookup"><span data-stu-id="34e3e-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="34e3e-111">請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。</span><span class="sxs-lookup"><span data-stu-id="34e3e-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="34e3e-112">下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (0，0)。</span><span class="sxs-lookup"><span data-stu-id="34e3e-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e3e-113">範例</span><span class="sxs-lookup"><span data-stu-id="34e3e-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="34e3e-114">下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。</span><span class="sxs-lookup"><span data-stu-id="34e3e-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="34e3e-115">下列範例會以 45 度的垂直扭曲套用<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。</span><span class="sxs-lookup"><span data-stu-id="34e3e-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="34e3e-116">下圖顯示本範例所使用的不同扭曲。</span><span class="sxs-lookup"><span data-stu-id="34e3e-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="34e3e-117">![SkewTransform 範例](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="34e3e-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="34e3e-118">三個 SkewTransform 範例的示意圖</span><span class="sxs-lookup"><span data-stu-id="34e3e-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="34e3e-119">如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="34e3e-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e3e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34e3e-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="34e3e-121">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="34e3e-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="34e3e-122">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="34e3e-122">How-to Topics</span></span>](transformations-how-to-topics.md)
