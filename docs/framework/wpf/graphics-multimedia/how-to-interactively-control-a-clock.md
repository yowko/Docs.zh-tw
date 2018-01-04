---
title: "如何：以互動方式控制時鐘"
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
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24a5154607bf535cbf995705332092bb86ca02e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="30d55-102">如何：以互動方式控制時鐘</span><span class="sxs-lookup"><span data-stu-id="30d55-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="30d55-103">A<xref:System.Windows.Media.Animation.Clock>物件的<xref:System.Windows.Media.Animation.ClockController>屬性可讓您以互動方式啟動、 暫停、 繼續、 搜尋、 前進到其填滿期間，時鐘和停止時鐘。</span><span class="sxs-lookup"><span data-stu-id="30d55-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="30d55-104">只有根時鐘的時間樹狀結構可以以互動方式控制。</span><span class="sxs-lookup"><span data-stu-id="30d55-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30d55-105">還有其他方式來以互動方式控制動畫，而不需要直接處理時鐘： 您也可以使用分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="30d55-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="30d55-106">標記和程式碼中支援分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="30d55-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="30d55-107">如需範例，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)或[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="30d55-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="30d55-108">在下列範例中，數個按鈕可用來以互動方式控制動畫時鐘。</span><span class="sxs-lookup"><span data-stu-id="30d55-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30d55-109">範例</span><span class="sxs-lookup"><span data-stu-id="30d55-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="30d55-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="30d55-110">See Also</span></span>  
 [<span data-ttu-id="30d55-111">使用分鏡腳本建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="30d55-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="30d55-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="30d55-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
