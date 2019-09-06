---
title: 作法：Viewport3D 中的點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 6eb68f4668c6ea5aa8728a81fac98409896f3fd2
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373262"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="2b02d-102">作法：Viewport3D 中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="2b02d-102">How to: Hit Test in a Viewport3D</span></span>

<span data-ttu-id="2b02d-103">這個範例示範如何對中<xref:System.Windows.Controls.Viewport3D>的3d 視覺效果進行點擊測試。</span><span class="sxs-lookup"><span data-stu-id="2b02d-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>

<span data-ttu-id="2b02d-104">因為<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>會傳回2d 和3d 的資訊，所以可以逐一查看測試結果，唯讀取3d 結果。</span><span class="sxs-lookup"><span data-stu-id="2b02d-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
[!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]

<span data-ttu-id="2b02d-105">下列<xref:System.Windows.Media.HitTestResultBehavior>程式碼中的會決定如何處理點擊測試結果。</span><span class="sxs-lookup"><span data-stu-id="2b02d-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span> <span data-ttu-id="2b02d-106">`UpdateResultInfo`和`UpdateMaterial`是本機定義的方法。</span><span class="sxs-lookup"><span data-stu-id="2b02d-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
[!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]
