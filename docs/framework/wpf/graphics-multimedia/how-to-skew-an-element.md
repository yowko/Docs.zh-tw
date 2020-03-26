---
title: 操作說明：扭曲元素
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112020"
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="1b1d5-102">操作說明：扭曲元素</span><span class="sxs-lookup"><span data-stu-id="1b1d5-102">How to: Skew an Element</span></span>
<span data-ttu-id="1b1d5-103">此示例演示如何使用<xref:System.Windows.Media.SkewTransform>傾斜元素。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="1b1d5-104">扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="1b1d5-105">一<xref:System.Windows.Media.SkewTransform>個典型的用途是類比 2D 物件中的 3D 深度。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating 3D depth in 2D objects.</span></span>  
  
 <span data-ttu-id="1b1d5-106">使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>和<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性指定 的中心<xref:System.Windows.Media.SkewTransform>點。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="1b1d5-107">使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定 X 軸和 y 軸的傾斜角度，並沿這些軸傾斜當前坐標系。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="1b1d5-108">要預測偏斜變換的效果，請考慮傾斜<xref:System.Windows.Media.SkewTransform.AngleX%2A>X 軸值相對於原始坐標系。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="1b1d5-109">因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>30，y 軸通過原點旋轉 30 度，並將該原點以 x- 30 度表示值。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="1b1d5-110">同樣，30 的 y<xref:System.Windows.Media.SkewTransform.AngleY%2A>值從原點偏斜 30 度。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="1b1d5-111">請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="1b1d5-112">下面的示例將 45 度的水準偏斜從中心<xref:System.Windows.Shapes.Rectangle>點 （0，0） 應用於 a。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b1d5-113">範例</span><span class="sxs-lookup"><span data-stu-id="1b1d5-113">Example</span></span>  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="1b1d5-114">下面的示例將 45 度的水準偏斜從中心<xref:System.Windows.Shapes.Rectangle>點 （25，25） 應用於 a。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="1b1d5-115">下面的示例將 45 度的垂直傾斜從中心點<xref:System.Windows.Shapes.Rectangle>（25，25） 應用於 a。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="1b1d5-116">下圖顯示本範例所使用的不同扭曲。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="1b1d5-117">![SkewTransform 範例](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="1b1d5-117">![SkewTransform examples](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="1b1d5-118">三個 SkewTransform 範例的示意圖</span><span class="sxs-lookup"><span data-stu-id="1b1d5-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="1b1d5-119">有關完整示例，請參閱[2D 變換示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。</span><span class="sxs-lookup"><span data-stu-id="1b1d5-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1d5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b1d5-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [<span data-ttu-id="1b1d5-121">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="1b1d5-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="1b1d5-122">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="1b1d5-122">How-to Topics</span></span>](transformations-how-to-topics.md)
