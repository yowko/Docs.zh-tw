---
title: 作法：在分鏡腳本開始後加以控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855859"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="27fbb-102">作法：在分鏡腳本開始後加以控制</span><span class="sxs-lookup"><span data-stu-id="27fbb-102">How to: Control a Storyboard After It Starts</span></span>

<span data-ttu-id="27fbb-103">這個範例示範如何使用程式碼來控制啟動<xref:System.Windows.Media.Animation.Storyboard>後的。</span><span class="sxs-lookup"><span data-stu-id="27fbb-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="27fbb-104">若要[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]在中控制分鏡腳本，請使用<xref:System.Windows.Trigger>和<xref:System.Windows.TriggerAction>物件; 如需範例，請參閱[使用事件觸發程式在啟動後控制分](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="27fbb-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

<span data-ttu-id="27fbb-105">若要啟動分鏡腳本，您<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>可以使用其方法，將分鏡腳本的動畫散發至其動畫和啟動分鏡腳本的屬性。</span><span class="sxs-lookup"><span data-stu-id="27fbb-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>

<span data-ttu-id="27fbb-106">若要將分鏡腳本設為可<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>控制，您可以使用方法，並將**true**指定為第二個參數。</span><span class="sxs-lookup"><span data-stu-id="27fbb-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="27fbb-107">接著，您可以使用分鏡腳本的互動方法來暫停、繼續、搜尋、停止、加速或減緩分鏡腳本，或將它移至其填滿期間。</span><span class="sxs-lookup"><span data-stu-id="27fbb-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="27fbb-108">以下是分鏡腳本的互動式方法清單：</span><span class="sxs-lookup"><span data-stu-id="27fbb-108">The following is a list of the storyboard's interactive methods:</span></span>

- <span data-ttu-id="27fbb-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>：暫停分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="27fbb-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>

- <span data-ttu-id="27fbb-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>：繼續已暫停的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="27fbb-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="27fbb-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>：設定分鏡腳本的互動速度。</span><span class="sxs-lookup"><span data-stu-id="27fbb-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>

- <span data-ttu-id="27fbb-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>：搜尋腳本指定的位置。</span><span class="sxs-lookup"><span data-stu-id="27fbb-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>

- <span data-ttu-id="27fbb-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>：搜尋分鏡腳本至指定的位置。</span><span class="sxs-lookup"><span data-stu-id="27fbb-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="27fbb-114">與方法<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>不同的是，這種作業會在下一個滴答之前處理。</span><span class="sxs-lookup"><span data-stu-id="27fbb-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>

- <span data-ttu-id="27fbb-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>：將分鏡腳本前進到其填滿期間（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="27fbb-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>

- <span data-ttu-id="27fbb-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>：停止分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="27fbb-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>

<span data-ttu-id="27fbb-117">在下列範例中，會使用數個分鏡腳本方法來以互動方式控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="27fbb-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="27fbb-118">若要查看使用觸發[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]程式來控制分鏡腳本的範例，請參閱在腳本[啟動後使用事件觸發程式來控制分](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="27fbb-118">To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

## <a name="example"></a><span data-ttu-id="27fbb-119">範例</span><span class="sxs-lookup"><span data-stu-id="27fbb-119">Example</span></span>

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a><span data-ttu-id="27fbb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27fbb-120">See also</span></span>

- [<span data-ttu-id="27fbb-121">在分鏡腳本開始後使用事件觸發程式進行控制</span><span class="sxs-lookup"><span data-stu-id="27fbb-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
