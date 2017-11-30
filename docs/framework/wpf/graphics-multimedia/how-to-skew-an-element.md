---
title: "操作說明：扭曲元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5c46b8c64a26d83ba6d8f018b9a1f8ca8250a57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-skew-an-element"></a><span data-ttu-id="ac868-102">操作說明：扭曲元素</span><span class="sxs-lookup"><span data-stu-id="ac868-102">How to: Skew an Element</span></span>
<span data-ttu-id="ac868-103">這個範例示範如何使用<xref:System.Windows.Media.SkewTransform>扭曲項目。</span><span class="sxs-lookup"><span data-stu-id="ac868-103">This example shows how to use a <xref:System.Windows.Media.SkewTransform> to skew an element.</span></span> <span data-ttu-id="ac868-104">扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。</span><span class="sxs-lookup"><span data-stu-id="ac868-104">A skew, which is also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="ac868-105">一般用途之一<xref:System.Windows.Media.SkewTransform>是模擬[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]深度[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="ac868-105">One typical use of a <xref:System.Windows.Media.SkewTransform> is for simulating [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] depth in [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] objects.</span></span>  
  
 <span data-ttu-id="ac868-106">使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>和<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性，以指定中心點的<xref:System.Windows.Media.SkewTransform>。</span><span class="sxs-lookup"><span data-stu-id="ac868-106">Use the <xref:System.Windows.Media.SkewTransform.CenterX%2A> and <xref:System.Windows.Media.SkewTransform.CenterY%2A> properties to specify the center point of the <xref:System.Windows.Media.SkewTransform>.</span></span>  
  
 <span data-ttu-id="ac868-107">使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定的 x 軸和 y 軸扭曲角度以及扭曲目前座標系統沿著這些座標軸。</span><span class="sxs-lookup"><span data-stu-id="ac868-107">Use the <xref:System.Windows.Media.SkewTransform.AngleX%2A> and <xref:System.Windows.Media.SkewTransform.AngleY%2A> properties to specify the skew angle of the x-axis and y-axis, and to skew the current coordinate system along these axes.</span></span>  
  
 <span data-ttu-id="ac868-108">若要預測的傾斜轉換效果，請考慮，<xref:System.Windows.Media.SkewTransform.AngleX%2A>扭曲相對於原始座標系統的 x 軸值。</span><span class="sxs-lookup"><span data-stu-id="ac868-108">To predict the effect of a skew transformation, consider that <xref:System.Windows.Media.SkewTransform.AngleX%2A> skews x-axis values relative to the original coordinate system.</span></span> <span data-ttu-id="ac868-109">因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>是 30，y 軸旋轉 30 度透過原點，扭曲 x-30 度從該來源的值。</span><span class="sxs-lookup"><span data-stu-id="ac868-109">Therefore, for an <xref:System.Windows.Media.SkewTransform.AngleX%2A> of 30, the y-axis rotates 30 degrees through the origin and skews the values in x- by 30 degrees from that origin.</span></span> <span data-ttu-id="ac868-110">同樣地，<xref:System.Windows.Media.SkewTransform.AngleY%2A>為 30 從原點 30 度扭曲圖形的 y 值。</span><span class="sxs-lookup"><span data-stu-id="ac868-110">Likewise, an <xref:System.Windows.Media.SkewTransform.AngleY%2A> of 30 skews the y- values of the shape by 30 degrees from the origin.</span></span> <span data-ttu-id="ac868-111">請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。</span><span class="sxs-lookup"><span data-stu-id="ac868-111">Note that this is not the same effect as translating (moving) the coordinate system by 30 degrees in x- or y-.</span></span>  
  
 <span data-ttu-id="ac868-112">下列範例會套用至 45 度的水平傾斜<xref:System.Windows.Shapes.Rectangle>從中心點為 (0，0)。</span><span class="sxs-lookup"><span data-stu-id="ac868-112">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (0,0).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac868-113">範例</span><span class="sxs-lookup"><span data-stu-id="ac868-113">Example</span></span>  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <span data-ttu-id="ac868-114">下列範例會套用至 45 度的水平傾斜<xref:System.Windows.Shapes.Rectangle>從中心點的 (25,25)。</span><span class="sxs-lookup"><span data-stu-id="ac868-114">The following example applies a horizontal skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <span data-ttu-id="ac868-115">下列範例會套用至 45 度的垂直傾斜<xref:System.Windows.Shapes.Rectangle>從中心點的 (25,25)。</span><span class="sxs-lookup"><span data-stu-id="ac868-115">The following example applies a vertical skew of 45 degrees to a <xref:System.Windows.Shapes.Rectangle> from a center point of (25,25).</span></span>  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 <span data-ttu-id="ac868-116">下圖顯示本範例所使用的不同扭曲。</span><span class="sxs-lookup"><span data-stu-id="ac868-116">The following illustration shows the different skews that are used in this example.</span></span>  
  
 <span data-ttu-id="ac868-117">![SkewTransform 範例](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span><span class="sxs-lookup"><span data-stu-id="ac868-117">![SkewTransform examples](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")</span></span>  
<span data-ttu-id="ac868-118">三個 SkewTransform 範例的示意圖</span><span class="sxs-lookup"><span data-stu-id="ac868-118">The three SkewTransform examples illustrated</span></span>  
  
 <span data-ttu-id="ac868-119">如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="ac868-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac868-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac868-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [<span data-ttu-id="ac868-121">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="ac868-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="ac868-122">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ac868-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
