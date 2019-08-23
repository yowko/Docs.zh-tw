---
title: 作法：建立和使用畫布
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964225"
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="12344-102">HOW TO：建立和使用畫布</span><span class="sxs-lookup"><span data-stu-id="12344-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="12344-103">這個範例會示範如何建立和使用的實例<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="12344-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12344-104">範例</span><span class="sxs-lookup"><span data-stu-id="12344-104">Example</span></span>  
 <span data-ttu-id="12344-105">下列範例會<xref:System.Windows.Controls.Canvas.SetTop%2A>使用的和<xref:System.Windows.Controls.TextBlock>方法<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.Canvas.SetLeft%2A>明確地放置兩個元素。</span><span class="sxs-lookup"><span data-stu-id="12344-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="12344-106">此範例也會將<xref:System.Windows.Controls.Control.Background%2A>的`LightSteelBlue`色彩指派給<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="12344-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12344-107">當您使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來定位<xref:System.Windows.Controls.TextBlock>元素時, 請<xref:System.Windows.Controls.Canvas.Top%2A>使用<xref:System.Windows.Controls.Canvas.Left%2A>和屬性。</span><span class="sxs-lookup"><span data-stu-id="12344-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="12344-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12344-108">See also</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [<span data-ttu-id="12344-109">面板概觀</span><span class="sxs-lookup"><span data-stu-id="12344-109">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="12344-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="12344-110">How-to Topics</span></span>](canvas-how-to-topics.md)
