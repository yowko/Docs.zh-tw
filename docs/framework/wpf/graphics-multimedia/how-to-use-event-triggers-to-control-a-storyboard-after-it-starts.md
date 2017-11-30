---
title: "如何：在腳本開始後使用事件觸發程式進行控制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="e0484-102">如何：在腳本開始後使用事件觸發程式進行控制</span><span class="sxs-lookup"><span data-stu-id="e0484-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="e0484-103">這個範例示範如何控制<xref:System.Windows.Media.Animation.Storyboard>之後啟動。</span><span class="sxs-lookup"><span data-stu-id="e0484-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="e0484-104">若要啟動<xref:System.Windows.Media.Animation.Storyboard>使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Media.Animation.BeginStoryboard>，這會發佈這些物件和屬性，其以動畫顯示，然後啟動 分鏡腳本動畫。</span><span class="sxs-lookup"><span data-stu-id="e0484-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="e0484-105">如果您提供<xref:System.Windows.Media.Animation.BeginStoryboard>藉由指定的名稱及其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>屬性，使其可控制的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="e0484-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="e0484-106">您可以再以互動方式控制分鏡腳本之後啟動。</span><span class="sxs-lookup"><span data-stu-id="e0484-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="e0484-107">使用下列分鏡腳本動作搭配<xref:System.Windows.EventTrigger>物件來控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="e0484-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="e0484-108"><xref:System.Windows.Media.Animation.PauseStoryboard>： 暫停分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="e0484-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="e0484-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>： 繼續暫停的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="e0484-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="e0484-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>： 變更分鏡腳本速度。</span><span class="sxs-lookup"><span data-stu-id="e0484-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="e0484-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>： 如果有的話，往前移到其填滿期結束分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="e0484-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="e0484-112"><xref:System.Windows.Media.Animation.StopStoryboard>： 停止分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="e0484-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="e0484-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>： 移除分鏡腳本，釋放資源。</span><span class="sxs-lookup"><span data-stu-id="e0484-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0484-114">範例</span><span class="sxs-lookup"><span data-stu-id="e0484-114">Example</span></span>  
 <span data-ttu-id="e0484-115">下列範例會使用可控制的分鏡腳本的動作，以互動方式控制 分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="e0484-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="e0484-116">**注意：**若要查看使用程式碼控制分鏡腳本的範例，請參閱[控制分鏡腳本之後它啟動使用其互動方法](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)。</span><span class="sxs-lookup"><span data-stu-id="e0484-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="e0484-117">如需其他範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="e0484-117">For additional examples, see the [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0484-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0484-118">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [<span data-ttu-id="e0484-119">在分鏡腳本開始後，使用其互動方法來進行控制</span><span class="sxs-lookup"><span data-stu-id="e0484-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [<span data-ttu-id="e0484-120">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="e0484-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e0484-121">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="e0484-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
