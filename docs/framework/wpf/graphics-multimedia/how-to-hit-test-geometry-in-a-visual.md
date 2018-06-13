---
title: 操作說明：對 Visual 中的幾何進行點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 26e0119ee82646f466c3567881bf33350fe59d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560915"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="1a003-102">操作說明：對 Visual 中的幾何進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="1a003-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="1a003-103">這個範例示範如何在所組成的一或多個視覺物件上執行點擊的測試<xref:System.Windows.Media.Geometry>物件。</span><span class="sxs-lookup"><span data-stu-id="1a003-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a003-104">範例</span><span class="sxs-lookup"><span data-stu-id="1a003-104">Example</span></span>  
 <span data-ttu-id="1a003-105">下列範例示範如何擷取<xref:System.Windows.Media.DrawingGroup>從使用的 visual 物件<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="1a003-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="1a003-106">點擊的測試不會再對呈現內容的每個繪圖<xref:System.Windows.Media.DrawingGroup>來判斷點擊的幾何。</span><span class="sxs-lookup"><span data-stu-id="1a003-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a003-107">在大部分情況下，您會使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法，以判斷是否點相交的任何視覺效果呈現內容。</span><span class="sxs-lookup"><span data-stu-id="1a003-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="1a003-108"><xref:System.Windows.Media.Geometry.FillContains%2A>方法是多載的方法，可讓您藉由將指定進行點擊測試<xref:System.Windows.Point>或<xref:System.Windows.Media.Geometry>。</span><span class="sxs-lookup"><span data-stu-id="1a003-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="1a003-109">如果幾何是經過繪製，筆觸可延伸至填滿範圍外。</span><span class="sxs-lookup"><span data-stu-id="1a003-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="1a003-110">在此情況下，您可能想要呼叫<xref:System.Windows.Media.Geometry.StrokeContains%2A>除了<xref:System.Windows.Media.Geometry.FillContains%2A>。</span><span class="sxs-lookup"><span data-stu-id="1a003-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="1a003-111">您也可以提供<xref:System.Windows.Media.ToleranceType>用於目的貝茲扁平化。</span><span class="sxs-lookup"><span data-stu-id="1a003-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a003-112">這個範例不會將任何可能套用至幾何的轉換或裁剪列入考慮。</span><span class="sxs-lookup"><span data-stu-id="1a003-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="1a003-113">此外，這個範例無法搭配樣式化控制項運作，因為它不具備任何直接與其相關聯的圖案。</span><span class="sxs-lookup"><span data-stu-id="1a003-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a003-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a003-114">See Also</span></span>  
 [<span data-ttu-id="1a003-115">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="1a003-115">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="1a003-116">使用幾何做為參數進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="1a003-116">Hit Test Using Geometry as a Parameter</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
