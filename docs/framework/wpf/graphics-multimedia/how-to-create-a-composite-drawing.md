---
title: "如何：建立複合圖形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 424f77b076344ad86db992614175243d1473886d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="b722f-102">如何：建立複合圖形</span><span class="sxs-lookup"><span data-stu-id="b722f-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="b722f-103">這個範例示範如何使用<xref:System.Windows.Media.DrawingGroup>結合以建立複雜的繪圖多<xref:System.Windows.Media.Drawing>變成單一的複合繪圖的物件。</span><span class="sxs-lookup"><span data-stu-id="b722f-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b722f-104">範例</span><span class="sxs-lookup"><span data-stu-id="b722f-104">Example</span></span>  
 <span data-ttu-id="b722f-105">下列範例會使用<xref:System.Windows.Media.DrawingGroup>來建立繪圖從複合<xref:System.Windows.Media.GeometryDrawing>和<xref:System.Windows.Media.ImageDrawing>物件。</span><span class="sxs-lookup"><span data-stu-id="b722f-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="b722f-106">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="b722f-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="b722f-107">![多個圖形的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="b722f-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="b722f-108">建立使用 DrawingGroup 複合繪圖</span><span class="sxs-lookup"><span data-stu-id="b722f-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="b722f-109">請注意灰色框線，繪圖的界限。</span><span class="sxs-lookup"><span data-stu-id="b722f-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="b722f-110">您可以使用<xref:System.Windows.Media.DrawingGroup>套用<xref:System.Windows.Media.DrawingGroup.Transform%2A>，<xref:System.Windows.Media.DrawingGroup.Opacity%2A>設定， <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>， <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>， <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>，或<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>至它所包含的繪圖。</span><span class="sxs-lookup"><span data-stu-id="b722f-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="b722f-111">因為<xref:System.Windows.Media.DrawingGroup>也<xref:System.Windows.Media.Drawing>，它可以包含其他<xref:System.Windows.Media.DrawingGroup>物件。</span><span class="sxs-lookup"><span data-stu-id="b722f-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="b722f-112">下列範例是類似於上述範例中，不同之處在於它會使用其他<xref:System.Windows.Media.DrawingGroup>將點陣圖效果和不透明度遮罩套用至其繪圖部份的物件。</span><span class="sxs-lookup"><span data-stu-id="b722f-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="b722f-113">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="b722f-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="b722f-114">![多個圖形的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="b722f-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="b722f-115">複合繪製，具有多個 DrawingGroup 物件</span><span class="sxs-lookup"><span data-stu-id="b722f-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="b722f-116">請注意灰色框線，繪圖的界限。</span><span class="sxs-lookup"><span data-stu-id="b722f-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="b722f-117">如需有關<xref:System.Windows.Media.Drawing>物件，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b722f-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b722f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="b722f-118">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [<span data-ttu-id="b722f-119">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="b722f-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
