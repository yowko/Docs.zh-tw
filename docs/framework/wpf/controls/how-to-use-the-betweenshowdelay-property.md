---
title: "如何：使用 BetweenShowDelay 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dca6dc7c6238ef4accc921818090237d17ce1cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="0436a-102">如何：使用 BetweenShowDelay 屬性</span><span class="sxs-lookup"><span data-stu-id="0436a-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="0436a-103">這個範例示範如何使用<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>時間屬性，如此工具提示會顯示快速 — 有少量或沒有延遲，當使用者將從一個工具提示直接到另一個滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="0436a-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0436a-104">範例</span><span class="sxs-lookup"><span data-stu-id="0436a-104">Example</span></span>  
 <span data-ttu-id="0436a-105">在下列範例中，<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>屬性設定為一秒 （1000年毫秒為單位） 和<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>設為兩秒 （2000年毫秒為單位），兩者的工具提示<xref:System.Windows.Shapes.Ellipse>控制項。</span><span class="sxs-lookup"><span data-stu-id="0436a-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="0436a-106">如果您顯示其中一個橢圓形的工具提示，然後在其上移動至另一個橢圓形兩秒暫停中將滑鼠指標，第二個橢圓形的工具提示會立即顯示。</span><span class="sxs-lookup"><span data-stu-id="0436a-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="0436a-107">下列案例中，任一<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>套用，因而導致等候 1 秒，才會出現第二個橢圓形的工具提示：</span><span class="sxs-lookup"><span data-stu-id="0436a-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="0436a-108">移至所花費的時間，如果第二個按鈕是超過兩秒。</span><span class="sxs-lookup"><span data-stu-id="0436a-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="0436a-109">如果在第一個橢圓形的時間間隔的開頭看不到工具提示。</span><span class="sxs-lookup"><span data-stu-id="0436a-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="0436a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0436a-110">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="0436a-111">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="0436a-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="0436a-112">工具提示概觀</span><span class="sxs-lookup"><span data-stu-id="0436a-112">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
