---
title: "如何：建立和使用 Canvas"
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
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 562531f75d6a800ff93a02709a053b790de52ea2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-use-a-canvas"></a><span data-ttu-id="a5316-102">如何：建立和使用 Canvas</span><span class="sxs-lookup"><span data-stu-id="a5316-102">How to: Create and Use a Canvas</span></span>
<span data-ttu-id="a5316-103">這個範例示範如何建立和使用的執行個體<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="a5316-103">This example shows how to create and use an instance of <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5316-104">範例</span><span class="sxs-lookup"><span data-stu-id="a5316-104">Example</span></span>  
 <span data-ttu-id="a5316-105">下列範例明確放置兩個<xref:System.Windows.Controls.TextBlock>所使用的項目<xref:System.Windows.Controls.Canvas.SetTop%2A>和<xref:System.Windows.Controls.Canvas.SetLeft%2A>方法<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="a5316-105">The following example explicitly positions two <xref:System.Windows.Controls.TextBlock> elements by using the <xref:System.Windows.Controls.Canvas.SetTop%2A> and <xref:System.Windows.Controls.Canvas.SetLeft%2A> methods of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="a5316-106">此範例也會將指派<xref:System.Windows.Controls.Control.Background%2A>色彩`LightSteelBlue`至<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="a5316-106">The example also assigns a <xref:System.Windows.Controls.Control.Background%2A> color of `LightSteelBlue` to the <xref:System.Windows.Controls.Canvas>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5316-107">當您使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]位置<xref:System.Windows.Controls.TextBlock>項目，使用<xref:System.Windows.Controls.Canvas.Top%2A>和<xref:System.Windows.Controls.Canvas.Left%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a5316-107">When you use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to position <xref:System.Windows.Controls.TextBlock> elements, use the <xref:System.Windows.Controls.Canvas.Top%2A> and <xref:System.Windows.Controls.Canvas.Left%2A> properties.</span></span>  
  
 [!code-csharp[CanvasCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a5316-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5316-108">See Also</span></span>  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.TextBlock>  
 <xref:System.Windows.Controls.Canvas.SetTop%2A>  
 <xref:System.Windows.Controls.Canvas.SetLeft%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 [<span data-ttu-id="a5316-109">面板概觀</span><span class="sxs-lookup"><span data-stu-id="a5316-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="a5316-110">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="a5316-110">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)
