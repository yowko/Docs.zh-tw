---
title: HOW TO：在分鏡腳本開始後使用事件觸發程序進行控制
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855856"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="33126-102">作法：在分鏡腳本開始後使用事件觸發程序進行控制</span><span class="sxs-lookup"><span data-stu-id="33126-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="33126-103">這個範例示範如何在啟動<xref:System.Windows.Media.Animation.Storyboard>之後控制。</span><span class="sxs-lookup"><span data-stu-id="33126-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="33126-104">若要使用<xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]來啟動，請<xref:System.Windows.Media.Animation.BeginStoryboard>使用，它會將動畫散佈至物件和屬性的動畫，然後啟動分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="33126-105">如果您藉<xref:System.Windows.Media.Animation.BeginStoryboard>由指定其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>屬性來提供名稱，則會將它設為可控制的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="33126-106">接著，您可以在腳本開始之後，以互動方式進行控制。</span><span class="sxs-lookup"><span data-stu-id="33126-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="33126-107">將下列分鏡腳本動作與<xref:System.Windows.EventTrigger>物件一起使用，以控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="33126-108"><xref:System.Windows.Media.Animation.PauseStoryboard>：暫停分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="33126-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>：繼續已暫停的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="33126-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>：變更分鏡腳本的速度。</span><span class="sxs-lookup"><span data-stu-id="33126-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="33126-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>：將分鏡腳本前進到其填滿期間的結尾（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="33126-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="33126-112"><xref:System.Windows.Media.Animation.StopStoryboard>：停止分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="33126-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>：移除分鏡腳本，釋放資源。</span><span class="sxs-lookup"><span data-stu-id="33126-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="33126-114">範例</span><span class="sxs-lookup"><span data-stu-id="33126-114">Example</span></span>

<span data-ttu-id="33126-115">下列範例會使用可控制的分鏡腳本動作，以互動方式控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="33126-116">若要查看使用程式碼控制分鏡腳本的範例，請參閱[在腳本開始之後使用其互動方法來控制分](how-to-control-a-storyboard-after-it-starts.md)鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="33126-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="33126-117">如需其他範例，請參閱[動畫範例庫](https://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="33126-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

## <a name="see-also"></a><span data-ttu-id="33126-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33126-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="33126-119">在分鏡腳本開始後，使用其互動方法來進行控制</span><span class="sxs-lookup"><span data-stu-id="33126-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="33126-120">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="33126-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="33126-121">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="33126-121">Storyboards Overview</span></span>](storyboards-overview.md)
