---
title: 操作說明：使用幾何當做參數進行點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 57b04f7f8c9bcc21f6b970c2981c2bab51044c10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561251"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="1e4b8-102">操作說明：使用幾何當做參數進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="1e4b8-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="1e4b8-103">這個範例示範如何執行點擊的測試視覺化的物件，使用<xref:System.Windows.Media.Geometry>作為點擊測試參數。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e4b8-104">範例</span><span class="sxs-lookup"><span data-stu-id="1e4b8-104">Example</span></span>  
 <span data-ttu-id="1e4b8-105">下列範例示範如何設定使用點擊的測試<xref:System.Windows.Media.GeometryHitTestParameters>如<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="1e4b8-106"><xref:System.Windows.Point>值傳遞至`OnMouseDown`方法用來建立<xref:System.Windows.Media.Geometry>以展開的點擊測試範圍的物件。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="1e4b8-107"><xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>屬性<xref:System.Windows.Media.GeometryHitTestResult>提供資訊的使用點擊測試結果<xref:System.Windows.Media.Geometry>作為點擊測試參數。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="1e4b8-108">下圖顯示點擊測試幾何 (藍色圓形) 和目標視覺物件呈現內容 (紅色矩形) 之間的關係。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="1e4b8-109">![圖表中使用之 IntersectionDetail 的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="1e4b8-109">![Diagram of IntersectionDetail used in hit testing](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="1e4b8-110">點擊測試幾何和目標視覺物件之間的交集</span><span class="sxs-lookup"><span data-stu-id="1e4b8-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="1e4b8-111">下列範例示範如何實作點擊的測試回呼時<xref:System.Windows.Media.Geometry>作為點擊的測試參數。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="1e4b8-112">`result`參數轉換成<xref:System.Windows.Media.GeometryHitTestResult>才能擷取的值<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="1e4b8-113">屬性值可讓您判斷如果<xref:System.Windows.Media.Geometry>點擊的測試參數完全或部分包含在點擊的測試目標的呈現的內容。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="1e4b8-114">在此情況下，範例程式碼僅將點擊測試結果加入至完全包含在目標範圍內之視覺效果的清單中。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="1e4b8-115"><xref:System.Windows.Media.HitTestResult>交集詳細資料時，應該不會呼叫回呼<xref:System.Windows.Media.IntersectionDetail.Empty>。</span><span class="sxs-lookup"><span data-stu-id="1e4b8-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4b8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e4b8-116">See Also</span></span>  
 [<span data-ttu-id="1e4b8-117">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="1e4b8-117">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="1e4b8-118">對 Visual 中的幾何進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="1e4b8-118">Hit Test Geometry in a Visual</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
