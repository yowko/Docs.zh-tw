---
title: 如何：在腳本開始後使用事件觸發程式進行控制
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186707"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="8f98f-102">如何：在腳本開始後使用事件觸發程式進行控制</span><span class="sxs-lookup"><span data-stu-id="8f98f-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="8f98f-103">此示例演示如何在 啟動後控制<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="8f98f-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="8f98f-104">要使用<xref:System.Windows.Media.Animation.Storyboard>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]開始 ，<xref:System.Windows.Media.Animation.BeginStoryboard>使用 ， 將動畫分發到它們為物件和屬性設置動畫，然後啟動分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="8f98f-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="8f98f-105">如果通過指定<xref:System.Windows.Media.Animation.BeginStoryboard>名稱<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>的屬性來命名，則可以將其製作為可控制的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="8f98f-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="8f98f-106">然後，您可以在分鏡腳本啟動後以對話模式控制它。</span><span class="sxs-lookup"><span data-stu-id="8f98f-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="8f98f-107">將以下分鏡腳本操作與<xref:System.Windows.EventTrigger>物件一起使用來控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="8f98f-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="8f98f-108"><xref:System.Windows.Media.Animation.PauseStoryboard>：暫停分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="8f98f-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="8f98f-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>：恢復暫停的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="8f98f-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="8f98f-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>：更改分鏡腳本速度。</span><span class="sxs-lookup"><span data-stu-id="8f98f-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="8f98f-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>：將分鏡腳本提前到填充期結束時（如果有）。</span><span class="sxs-lookup"><span data-stu-id="8f98f-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="8f98f-112"><xref:System.Windows.Media.Animation.StopStoryboard>：停止分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="8f98f-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="8f98f-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>：刪除分鏡腳本，釋放資源。</span><span class="sxs-lookup"><span data-stu-id="8f98f-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="8f98f-114">範例</span><span class="sxs-lookup"><span data-stu-id="8f98f-114">Example</span></span>

<span data-ttu-id="8f98f-115">下面的示例使用可控的分鏡腳本操作來交互控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="8f98f-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="8f98f-116">要查看使用代碼控制分鏡腳本的示例，請參閱[在分鏡腳本開始使用其交互方法後對其進行控制](how-to-control-a-storyboard-after-it-starts.md)。</span><span class="sxs-lookup"><span data-stu-id="8f98f-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="8f98f-117">有關其他示例，請參閱[動畫示例庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。</span><span class="sxs-lookup"><span data-stu-id="8f98f-117">For additional examples, see the [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f98f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f98f-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="8f98f-119">在分鏡腳本開始後，使用其互動方法來進行控制</span><span class="sxs-lookup"><span data-stu-id="8f98f-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="8f98f-120">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="8f98f-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="8f98f-121">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="8f98f-121">Storyboards Overview</span></span>](storyboards-overview.md)
