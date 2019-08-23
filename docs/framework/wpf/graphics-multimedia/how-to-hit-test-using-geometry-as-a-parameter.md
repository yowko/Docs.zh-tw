---
title: 作法：使用幾何作為參數進行點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923398"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="e096e-102">HOW TO：使用幾何作為參數進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="e096e-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="e096e-103">這個範例示範如何使用<xref:System.Windows.Media.Geometry>作為點擊測試參數, 在視覺物件上執行點擊測試。</span><span class="sxs-lookup"><span data-stu-id="e096e-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e096e-104">範例</span><span class="sxs-lookup"><span data-stu-id="e096e-104">Example</span></span>  
 <span data-ttu-id="e096e-105">下列範例示範如何使用<xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>來設定方法的點擊測試。</span><span class="sxs-lookup"><span data-stu-id="e096e-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="e096e-106">傳遞<xref:System.Windows.Point> <xref:System.Windows.Media.Geometry>至方法的值是用來建立物件, 以便擴充點擊測試的範圍。 `OnMouseDown`</span><span class="sxs-lookup"><span data-stu-id="e096e-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="e096e-107">的<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> <xref:System.Windows.Media.Geometry>屬性會提供使用作為點擊測試參數的點擊測試<xref:System.Windows.Media.GeometryHitTestResult>結果相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e096e-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="e096e-108">下圖顯示點擊測試幾何 (藍色圓形) 和目標視覺物件呈現內容 (紅色矩形) 之間的關係。</span><span class="sxs-lookup"><span data-stu-id="e096e-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 ![此圖顯示用於點擊測試的 IntersectionDetail。](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 <span data-ttu-id="e096e-110">下列範例示範如何在<xref:System.Windows.Media.Geometry>將當做點擊測試參數使用時, 執行點擊測試回呼。</span><span class="sxs-lookup"><span data-stu-id="e096e-110">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="e096e-111">參數會轉換<xref:System.Windows.Media.GeometryHitTestResult>成, 以便<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>取得屬性的值。 `result`</span><span class="sxs-lookup"><span data-stu-id="e096e-111">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="e096e-112">屬性值可讓您判斷<xref:System.Windows.Media.Geometry>點擊測試參數是完全或部分包含在點擊測試目標的呈現內容中。</span><span class="sxs-lookup"><span data-stu-id="e096e-112">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="e096e-113">在此情況下，範例程式碼僅將點擊測試結果加入至完全包含在目標範圍內之視覺效果的清單中。</span><span class="sxs-lookup"><span data-stu-id="e096e-113">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> <span data-ttu-id="e096e-114">當<xref:System.Windows.Media.HitTestResult>交集詳細資料是<xref:System.Windows.Media.IntersectionDetail.Empty>時, 不應呼叫回呼。</span><span class="sxs-lookup"><span data-stu-id="e096e-114">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e096e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e096e-115">See also</span></span>

- [<span data-ttu-id="e096e-116">視覺分層中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="e096e-116">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="e096e-117">對 Visual 中的幾何進行點擊測試</span><span class="sxs-lookup"><span data-stu-id="e096e-117">Hit Test Geometry in a Visual</span></span>](how-to-hit-test-geometry-in-a-visual.md)
