---
title: HOW TO：分鏡腳本開始後進行控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161482"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="da2b6-102">HOW TO：分鏡腳本開始後進行控制</span><span class="sxs-lookup"><span data-stu-id="da2b6-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="da2b6-103">此範例示範如何使用程式碼，以控制<xref:System.Windows.Media.Animation.Storyboard>啟動之後。</span><span class="sxs-lookup"><span data-stu-id="da2b6-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="da2b6-104">若要控制在分鏡腳本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Trigger>並<xref:System.Windows.TriggerAction>物件; 如需範例，請參閱[使用事件觸發程序來控制分鏡腳本開始後](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。</span><span class="sxs-lookup"><span data-stu-id="da2b6-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="da2b6-105">若要啟動分鏡腳本，您使用其<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法，將它們建立動畫，並啟動分鏡腳本的屬性的分鏡腳本的動畫。</span><span class="sxs-lookup"><span data-stu-id="da2b6-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="da2b6-106">要控制分鏡腳本，請使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法並指定 **，則為 true**做為第二個參數。</span><span class="sxs-lookup"><span data-stu-id="da2b6-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="da2b6-107">您接著可以使用分鏡腳本的互動方法來暫停、 繼續、 搜尋、 停止、 加速，或分鏡腳本，變慢或前進到其填滿期間。</span><span class="sxs-lookup"><span data-stu-id="da2b6-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="da2b6-108">以下是一份分鏡腳本的互動方法：</span><span class="sxs-lookup"><span data-stu-id="da2b6-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A><span data-ttu-id="da2b6-109">:暫停分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="da2b6-109">: Pauses the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A><span data-ttu-id="da2b6-110">:繼續已暫停的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="da2b6-110">: Resumes a paused storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A><span data-ttu-id="da2b6-111">:設定分鏡腳本的互動速度。</span><span class="sxs-lookup"><span data-stu-id="da2b6-111">: Sets the storyboard's interactive speed.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A><span data-ttu-id="da2b6-112">:搜尋分鏡腳本的指定位置。</span><span class="sxs-lookup"><span data-stu-id="da2b6-112">: Seeks the storyboard the specified location.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A><span data-ttu-id="da2b6-113">:搜尋分鏡腳本，以指定的位置。</span><span class="sxs-lookup"><span data-stu-id="da2b6-113">: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="da2b6-114">不同於<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法，這項作業會處理下一個刻度之前。</span><span class="sxs-lookup"><span data-stu-id="da2b6-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A><span data-ttu-id="da2b6-115">:如果有的話，請前進到其填滿期間，將分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="da2b6-115">: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A><span data-ttu-id="da2b6-116">:停止分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="da2b6-116">: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="da2b6-117">在下列範例中，數個分鏡腳本的方法來以互動方式控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="da2b6-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="da2b6-118">**注意：** 若要控制使用觸發程序及分鏡腳本的範例，請參閱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，請參閱 <<c2> [ 來控制分鏡腳本開始後使用事件觸發程序](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。</span><span class="sxs-lookup"><span data-stu-id="da2b6-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da2b6-119">範例</span><span class="sxs-lookup"><span data-stu-id="da2b6-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="da2b6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da2b6-120">See also</span></span>

- [<span data-ttu-id="da2b6-121">在分鏡腳本開始後使用事件觸發程序進行控制</span><span class="sxs-lookup"><span data-stu-id="da2b6-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
