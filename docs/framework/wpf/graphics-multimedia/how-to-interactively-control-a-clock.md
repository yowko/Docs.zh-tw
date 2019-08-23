---
title: HOW TO：以互動方式控制時鐘
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951340"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="842bc-102">作法：以互動方式控制時鐘</span><span class="sxs-lookup"><span data-stu-id="842bc-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="842bc-103"><xref:System.Windows.Media.Animation.Clock>物件的<xref:System.Windows.Media.Animation.ClockController>屬性可讓您以互動方式啟動、暫停、繼續、搜尋、將時鐘前移到其填滿期間, 以及停止時鐘。</span><span class="sxs-lookup"><span data-stu-id="842bc-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="842bc-104">只有時間樹狀結構的根時鐘可以透過互動方式進行控制。</span><span class="sxs-lookup"><span data-stu-id="842bc-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="842bc-105">還有其他方法可以互動方式控制不需要直接使用時鐘的動畫: 您也可以使用分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="842bc-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="842bc-106">標記和程式碼都支援分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="842bc-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="842bc-107">如需範例, 請參閱使用分鏡腳本或[動畫總覽](animation-overview.md)[來建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="842bc-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="842bc-108">在下列範例中, 有數個按鈕用來以互動方式控制動畫時鐘。</span><span class="sxs-lookup"><span data-stu-id="842bc-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="842bc-109">範例</span><span class="sxs-lookup"><span data-stu-id="842bc-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="842bc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="842bc-110">See also</span></span>

- [<span data-ttu-id="842bc-111">使用分鏡腳本建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="842bc-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="842bc-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="842bc-112">Animation Overview</span></span>](animation-overview.md)
