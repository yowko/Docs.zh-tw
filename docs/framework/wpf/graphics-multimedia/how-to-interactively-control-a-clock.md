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
ms.openlocfilehash: 05989b6a03e03fb5723a70c9c36d5e32f9117049
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947234"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="0b361-102">HOW TO：以互動方式控制時鐘</span><span class="sxs-lookup"><span data-stu-id="0b361-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="0b361-103">A<xref:System.Windows.Media.Animation.Clock>物件的<xref:System.Windows.Media.Animation.ClockController>屬性可讓您以互動方式啟動、 暫停、 繼續、 搜尋、 前進到其填滿期間中，時鐘及停止時鐘。</span><span class="sxs-lookup"><span data-stu-id="0b361-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="0b361-104">您可以以互動方式控制只計時樹狀結構的根時鐘。</span><span class="sxs-lookup"><span data-stu-id="0b361-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b361-105">還有其他方式來以互動方式控制動畫，而不需要直接使用時鐘： 您也可以使用分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="0b361-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="0b361-106">分鏡腳本支援標記和程式碼。</span><span class="sxs-lookup"><span data-stu-id="0b361-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="0b361-107">如需範例，請參閱[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)或[動畫概觀](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0b361-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="0b361-108">在下列範例中，數個按鈕用來以互動方式控制動畫時鐘。</span><span class="sxs-lookup"><span data-stu-id="0b361-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b361-109">範例</span><span class="sxs-lookup"><span data-stu-id="0b361-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="0b361-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b361-110">See also</span></span>

- [<span data-ttu-id="0b361-111">使用分鏡腳本建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="0b361-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="0b361-112">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="0b361-112">Animation Overview</span></span>](animation-overview.md)
