---
title: HOW TO：建立複合繪圖
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 0af7fbca593627ebe8cd102a02617a27eac50aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132466"
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="7c728-102">HOW TO：建立複合繪圖</span><span class="sxs-lookup"><span data-stu-id="7c728-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="7c728-103">此範例示範如何使用<xref:System.Windows.Media.DrawingGroup>來建立複雜的繪圖結合多個<xref:System.Windows.Media.Drawing>單一複合繪圖的物件。</span><span class="sxs-lookup"><span data-stu-id="7c728-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c728-104">範例</span><span class="sxs-lookup"><span data-stu-id="7c728-104">Example</span></span>  
 <span data-ttu-id="7c728-105">下列範例會使用<xref:System.Windows.Media.DrawingGroup>若要建立從繪製複合<xref:System.Windows.Media.GeometryDrawing>和<xref:System.Windows.Media.ImageDrawing>物件。</span><span class="sxs-lookup"><span data-stu-id="7c728-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="7c728-106">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="7c728-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="7c728-107">![包含多個圖形的 DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="7c728-107">![A DrawingGroup with multiple drawings](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="7c728-108">利用 DrawingGroup 建立複合圖形</span><span class="sxs-lookup"><span data-stu-id="7c728-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="7c728-109">請注意灰色框線，其中顯示繪圖的界限。</span><span class="sxs-lookup"><span data-stu-id="7c728-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="7c728-110">您可以使用<xref:System.Windows.Media.DrawingGroup>套用<xref:System.Windows.Media.DrawingGroup.Transform%2A>，<xref:System.Windows.Media.DrawingGroup.Opacity%2A>設定，請<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>， <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>， <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>，或<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>至它所包含的繪圖。</span><span class="sxs-lookup"><span data-stu-id="7c728-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="7c728-111">因為<xref:System.Windows.Media.DrawingGroup>還有<xref:System.Windows.Media.Drawing>，它可以包含其他<xref:System.Windows.Media.DrawingGroup>物件。</span><span class="sxs-lookup"><span data-stu-id="7c728-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="7c728-112">下列範例是類似於上述範例中，不同之處在於它會使用其他<xref:System.Windows.Media.DrawingGroup>將點陣圖效果和不透明度遮罩套用至某些其繪圖的物件。</span><span class="sxs-lookup"><span data-stu-id="7c728-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="7c728-113">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="7c728-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="7c728-114">![包含多個圖形的 DrawingGroup](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="7c728-114">![A DrawingGroup with multiple drawings](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="7c728-115">複合繪圖，具有多個 DrawingGroup 物件</span><span class="sxs-lookup"><span data-stu-id="7c728-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="7c728-116">請注意灰色框線，其中顯示繪圖的界限。</span><span class="sxs-lookup"><span data-stu-id="7c728-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="7c728-117">如需詳細資訊<xref:System.Windows.Media.Drawing>物件，請參閱[繪圖物件概觀](drawing-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7c728-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c728-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c728-118">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [<span data-ttu-id="7c728-119">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="7c728-119">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
