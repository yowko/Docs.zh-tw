---
title: "如何：Viewport3D 中的點擊測試"
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
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dcc6d11eebc7758d0c5d4c6308bc56dfcc0fc31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="0ab31-102">如何：Viewport3D 中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="0ab31-102">How to: Hit Test in a Viewport3D</span></span>
<span data-ttu-id="0ab31-103">這個範例示範如何進行點擊測試的 3D 視覺效果中<xref:System.Windows.Controls.Viewport3D>。</span><span class="sxs-lookup"><span data-stu-id="0ab31-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>  
  
 <span data-ttu-id="0ab31-104">因為<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>2D 和 3D 資訊時，會傳回可逐一查看測試結果，以了解只有 3D 的結果。</span><span class="sxs-lookup"><span data-stu-id="0ab31-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <span data-ttu-id="0ab31-105"><xref:System.Windows.Media.HitTestResultBehavior>在下列程式碼會判斷點擊的測試結果的處理方式。</span><span class="sxs-lookup"><span data-stu-id="0ab31-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span>  <span data-ttu-id="0ab31-106">`UpdateResultInfo`和`UpdateMaterial`本機定義的方法。</span><span class="sxs-lookup"><span data-stu-id="0ab31-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a><span data-ttu-id="0ab31-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ab31-107">See Also</span></span>  
 [<span data-ttu-id="0ab31-108">3-D 點擊測試範例</span><span class="sxs-lookup"><span data-stu-id="0ab31-108">3-D Hit Testing Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159959)
