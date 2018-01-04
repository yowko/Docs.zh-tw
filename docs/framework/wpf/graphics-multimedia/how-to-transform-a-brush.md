---
title: "操作說明：轉換筆刷"
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
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ee517eb76877bb4e02c021061055b328597c517
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="fb763-102">操作說明：轉換筆刷</span><span class="sxs-lookup"><span data-stu-id="fb763-102">How to: Transform a Brush</span></span>
<span data-ttu-id="fb763-103">此範例顯示如何將轉換<xref:System.Windows.Media.Brush>藉由使用其兩個轉換屬性的物件：<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>。</span><span class="sxs-lookup"><span data-stu-id="fb763-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="fb763-104">下列範例會使用<xref:System.Windows.Media.RotateTransform>旋轉的內容<xref:System.Windows.Media.ImageBrush>旋轉 45 度。</span><span class="sxs-lookup"><span data-stu-id="fb763-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="fb763-105">下圖顯示<xref:System.Windows.Media.ImageBrush>沒有<xref:System.Windows.Media.RotateTransform>，與<xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，與<xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.Media.Brush.Transform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="fb763-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="fb763-106">![筆刷的 RelativeTransform 和 Transform 設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="fb763-106">![Brush RelativeTransform and Transform settings](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb763-107">範例</span><span class="sxs-lookup"><span data-stu-id="fb763-107">Example</span></span>  
 <span data-ttu-id="fb763-108">第一個範例會在套用<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性<xref:System.Windows.Media.ImageBrush>。</span><span class="sxs-lookup"><span data-stu-id="fb763-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="fb763-109"><xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性<xref:System.Windows.Media.RotateTransform>物件都設定為 0.5，也就是此內容的中心點的相對座標。</span><span class="sxs-lookup"><span data-stu-id="fb763-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="fb763-110">如此一來，<xref:System.Windows.Media.ImageBrush>旋轉中心的內容。</span><span class="sxs-lookup"><span data-stu-id="fb763-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="fb763-111">第二個範例也適用於<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.Media.ImageBrush>; 不過，這個範例會使用<xref:System.Windows.Media.Brush.Transform%2A>屬性而非<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="fb763-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="fb763-112">若要旋轉中心的筆刷，這個範例會設定<xref:System.Windows.Media.RotateTransform.CenterX%2A>和<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性<xref:System.Windows.Media.RotateTransform>絕對座標的物件。</span><span class="sxs-lookup"><span data-stu-id="fb763-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="fb763-113">由於筆刷會繪製大小為 175 x 90 像素的矩形，矩形的中心點將會是 (87.5, 45)。</span><span class="sxs-lookup"><span data-stu-id="fb763-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="fb763-114">如需說明如何<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>屬性工作，請參閱[筆刷轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="fb763-115">如需完整的範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="fb763-115">For the complete sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="fb763-116">如需筆刷的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb763-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb763-117">See Also</span></span>  
 [<span data-ttu-id="fb763-118">筆刷轉換概觀</span><span class="sxs-lookup"><span data-stu-id="fb763-118">Brush Transformation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [<span data-ttu-id="fb763-119">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="fb763-119">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="fb763-120">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="fb763-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
