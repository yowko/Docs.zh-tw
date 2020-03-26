---
title: 如何：Viewport3D 中的點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D visuals [WPF], hit-testing for
- hit tests [WPF], for 3D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 34bc86349332293e40aca5743cbabb2a48634da6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112085"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="49032-102">如何：Viewport3D 中的點擊測試</span><span class="sxs-lookup"><span data-stu-id="49032-102">How to: Hit Test in a Viewport3D</span></span>

<span data-ttu-id="49032-103">此示例演示如何在 中命中 3D 視覺物件測試<xref:System.Windows.Controls.Viewport3D>。</span><span class="sxs-lookup"><span data-stu-id="49032-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>

<span data-ttu-id="49032-104">由於<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>返回 2D 和 3D 資訊，因此可以通過測試結果反覆運算以僅讀取 3D 結果。</span><span class="sxs-lookup"><span data-stu-id="49032-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
[!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]

<span data-ttu-id="49032-105">以下<xref:System.Windows.Media.HitTestResultBehavior>代碼中確定如何處理點擊測試結果。</span><span class="sxs-lookup"><span data-stu-id="49032-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span> <span data-ttu-id="49032-106">`UpdateResultInfo`是`UpdateMaterial`本地定義的方法。</span><span class="sxs-lookup"><span data-stu-id="49032-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>

[!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
[!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]
