---
title: 操作說明：轉換筆刷
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: ebc8d4c6cb36d76b70691cce183f9e6070d19822
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507043"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="ec2f6-102">操作說明：轉換筆刷</span><span class="sxs-lookup"><span data-stu-id="ec2f6-102">How to: Transform a Brush</span></span>
<span data-ttu-id="ec2f6-103">此範例示範如何轉換<xref:System.Windows.Media.Brush>物件使用其兩個轉換屬性：<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="ec2f6-104">下列範例會使用<xref:System.Windows.Media.RotateTransform>若要旋轉的內容<xref:System.Windows.Media.ImageBrush>旋轉 45 度。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="ec2f6-105">如下圖所示<xref:System.Windows.Media.ImageBrush>而不需要<xref:System.Windows.Media.RotateTransform>，使用<xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，且<xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.Media.Brush.Transform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="ec2f6-106">![筆刷的 RelativeTransform 和 Transform 設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="ec2f6-106">![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec2f6-107">範例</span><span class="sxs-lookup"><span data-stu-id="ec2f6-107">Example</span></span>  
 <span data-ttu-id="ec2f6-108">第一個範例會套用<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性<xref:System.Windows.Media.ImageBrush>。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="ec2f6-109"><xref:System.Windows.Media.RotateTransform.CenterX%2A>並<xref:System.Windows.Media.RotateTransform.CenterY%2A>的屬性<xref:System.Windows.Media.RotateTransform>物件都設為 0.5，這是此內容的中心點的相對座標。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="ec2f6-110">如此一來，<xref:System.Windows.Media.ImageBrush>旋轉中心的內容。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="ec2f6-111">第二個範例也適用於<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.Media.ImageBrush>; 不過，此範例會使用<xref:System.Windows.Media.Brush.Transform%2A>屬性而非<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="ec2f6-112">若要旋轉筆刷的中心，此範例會設定<xref:System.Windows.Media.RotateTransform.CenterX%2A>並<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性的<xref:System.Windows.Media.RotateTransform>為絕對座標的物件。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="ec2f6-113">由於筆刷會繪製大小為 175 x 90 像素的矩形，矩形的中心點將會是 (87.5, 45)。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="ec2f6-114">如需說明如何<xref:System.Windows.Media.Brush.RelativeTransform%2A>並<xref:System.Windows.Media.Brush.Transform%2A>屬性運作，請參閱[筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="ec2f6-115">如需完整的範例，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-115">For the complete sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="ec2f6-116">如需筆刷的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ec2f6-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2f6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec2f6-117">See Also</span></span>  
 [<span data-ttu-id="ec2f6-118">筆刷轉換概觀</span><span class="sxs-lookup"><span data-stu-id="ec2f6-118">Brush Transformation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [<span data-ttu-id="ec2f6-119">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="ec2f6-119">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="ec2f6-120">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="ec2f6-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
