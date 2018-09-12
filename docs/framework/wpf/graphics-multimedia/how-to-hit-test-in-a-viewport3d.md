---
title: 如何：Viewport3D 中的點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 297fe17b8844f7542255afcfe442fbf9b7a0d59d
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44698493"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="a8b76-102">如何：Viewport3D 中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="a8b76-102">How to: Hit Test in a Viewport3D</span></span>
<span data-ttu-id="a8b76-103">此範例示範如何進行點擊測試中的 3D 視覺效果<xref:System.Windows.Controls.Viewport3D>。</span><span class="sxs-lookup"><span data-stu-id="a8b76-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>  
  
 <span data-ttu-id="a8b76-104">因為<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>2D 和 3D 的資訊，會傳回可逐一查看測試結果，以讀取只 3D 的結果。</span><span class="sxs-lookup"><span data-stu-id="a8b76-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <span data-ttu-id="a8b76-105"><xref:System.Windows.Media.HitTestResultBehavior>在下列程式碼會決定點擊的測試結果的處理方式。</span><span class="sxs-lookup"><span data-stu-id="a8b76-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span>  <span data-ttu-id="a8b76-106">`UpdateResultInfo` 和`UpdateMaterial`本機定義的方法。</span><span class="sxs-lookup"><span data-stu-id="a8b76-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a><span data-ttu-id="a8b76-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b76-107">See Also</span></span>  
 [<span data-ttu-id="a8b76-108">3d 點擊測試範例</span><span class="sxs-lookup"><span data-stu-id="a8b76-108">3-D Hit Testing Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159959)
