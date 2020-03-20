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
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187330"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="f7ce7-102">操作說明：轉換筆刷</span><span class="sxs-lookup"><span data-stu-id="f7ce7-102">How to: Transform a Brush</span></span>
<span data-ttu-id="f7ce7-103">此示例演示如何使用物件的兩個<xref:System.Windows.Media.Brush>轉換屬性：<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>轉換來轉換物件。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="f7ce7-104">以下示例使用<xref:System.Windows.Media.RotateTransform>將 內容<xref:System.Windows.Media.ImageBrush>旋轉 45 度。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="f7ce7-105">下圖顯示了<xref:System.Windows.Media.ImageBrush>無<xref:System.Windows.Media.RotateTransform>的 ，其中<xref:System.Windows.Media.RotateTransform>應用於<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，並<xref:System.Windows.Media.RotateTransform>應用於 屬性。 <xref:System.Windows.Media.Brush.Transform%2A></span><span class="sxs-lookup"><span data-stu-id="f7ce7-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="f7ce7-106">![筆刷的 RelativeTransform 和 Transform 設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="f7ce7-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7ce7-107">範例</span><span class="sxs-lookup"><span data-stu-id="f7ce7-107">Example</span></span>  
 <span data-ttu-id="f7ce7-108">第一個示例將<xref:System.Windows.Media.RotateTransform>應用於<xref:System.Windows.Media.Brush.RelativeTransform%2A>的屬性<xref:System.Windows.Media.ImageBrush>。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="f7ce7-109">物件的 和<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性都設置為 0.5，這是此內容的中心點的相對座標。 <xref:System.Windows.Media.RotateTransform></span><span class="sxs-lookup"><span data-stu-id="f7ce7-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="f7ce7-110">因此，<xref:System.Windows.Media.ImageBrush>內容圍繞其中心旋轉。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="f7ce7-111">第二個<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.ImageBrush>示例還應用於但是，此示例使用 屬性<xref:System.Windows.Media.Brush.Transform%2A>而不是 屬性<xref:System.Windows.Media.Brush.RelativeTransform%2A>。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="f7ce7-112">要圍繞其中心旋轉畫筆，該示例將<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A><xref:System.Windows.Media.RotateTransform>物件的 和 屬性設置為絕對座標。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="f7ce7-113">由於筆刷會繪製大小為 175 x 90 像素的矩形，矩形的中心點將會是 (87.5, 45)。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="f7ce7-114">有關<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>屬性工作方式的說明，請參閱[筆刷轉換概述](brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="f7ce7-115">如需完整的範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-115">For the complete sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="f7ce7-116">如需筆刷的詳細資訊，請參閱[使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ce7-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ce7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7ce7-117">See also</span></span>

- [<span data-ttu-id="f7ce7-118">筆刷轉換概觀</span><span class="sxs-lookup"><span data-stu-id="f7ce7-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="f7ce7-119">使用純色和漸層繪製的概觀</span><span class="sxs-lookup"><span data-stu-id="f7ce7-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="f7ce7-120">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="f7ce7-120">Transforms Overview</span></span>](transforms-overview.md)
