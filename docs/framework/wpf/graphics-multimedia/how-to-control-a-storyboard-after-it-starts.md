---
title: "如何：在腳本開始後進行控制"
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
helpviewer_keywords: Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 051ac6fea73b207fb5ef4d6293c5e996552f1281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="9245e-102">如何：在腳本開始後進行控制</span><span class="sxs-lookup"><span data-stu-id="9245e-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="9245e-103">這個範例示範如何使用程式碼控制<xref:System.Windows.Media.Animation.Storyboard>啟動它之後。</span><span class="sxs-lookup"><span data-stu-id="9245e-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="9245e-104">若要控制中的腳本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Trigger>和<xref:System.Windows.TriggerAction>物件; 如需範例，請參閱[使用事件觸發程序來控制分鏡腳本之後啟動](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。</span><span class="sxs-lookup"><span data-stu-id="9245e-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="9245e-105">若要啟動分鏡腳本，您使用其<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法，將發佈分鏡腳本動畫的屬性，它們以動畫顯示，並啟動分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="9245e-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="9245e-106">要從此分鏡腳本，請使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法並指定**true**做為第二個參數。</span><span class="sxs-lookup"><span data-stu-id="9245e-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="9245e-107">您接著可以使用分鏡腳本的互動式方法來暫停、 繼續、 搜尋、 停止、 加速，或分鏡腳本，變慢或前進到其填滿期間。</span><span class="sxs-lookup"><span data-stu-id="9245e-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="9245e-108">一份分鏡腳本的互動的方法如下：</span><span class="sxs-lookup"><span data-stu-id="9245e-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <span data-ttu-id="9245e-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>： 暫停分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="9245e-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="9245e-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>： 繼續暫停的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="9245e-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="9245e-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>： 設定分鏡腳本的互動速度。</span><span class="sxs-lookup"><span data-stu-id="9245e-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
-   <span data-ttu-id="9245e-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>： 搜尋分鏡腳本的指定位置。</span><span class="sxs-lookup"><span data-stu-id="9245e-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
-   <span data-ttu-id="9245e-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>： 搜尋至指定的位置分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="9245e-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="9245e-114">不同於<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法，這項作業會處理之前的下一個刻度。</span><span class="sxs-lookup"><span data-stu-id="9245e-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <span data-ttu-id="9245e-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>： 如果有的話，往前移到其填滿期間，分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="9245e-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="9245e-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>： 停止分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="9245e-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="9245e-117">在下列範例中，數個分鏡腳本方法可用來以互動方式控制 分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="9245e-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="9245e-118">**注意：**控制使用觸發程序與分鏡腳本的範例，請參閱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，請參閱[使用事件觸發程序來控制分鏡腳本之後啟動](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。</span><span class="sxs-lookup"><span data-stu-id="9245e-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9245e-119">範例</span><span class="sxs-lookup"><span data-stu-id="9245e-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9245e-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="9245e-120">See Also</span></span>  
 [<span data-ttu-id="9245e-121">在分鏡腳本開始後使用事件觸發程式進行控制</span><span class="sxs-lookup"><span data-stu-id="9245e-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
