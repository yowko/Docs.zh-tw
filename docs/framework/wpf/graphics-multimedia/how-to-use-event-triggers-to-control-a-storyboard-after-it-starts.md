---
title: HOW TO：在分鏡腳本開始後使用事件觸發程序進行控制
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: d444349f8bc9236e1d15f484f35b1326c77e2425
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170647"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="a3f97-102">HOW TO：在分鏡腳本開始後使用事件觸發程序進行控制</span><span class="sxs-lookup"><span data-stu-id="a3f97-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="a3f97-103">此範例示範如何控制<xref:System.Windows.Media.Animation.Storyboard>啟動之後。</span><span class="sxs-lookup"><span data-stu-id="a3f97-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="a3f97-104">若要啟動<xref:System.Windows.Media.Animation.Storyboard>利用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用<xref:System.Windows.Media.Animation.BeginStoryboard>，這會對物件和屬性，它們建立動畫，然後啟動 分鏡腳本將動畫的散發。</span><span class="sxs-lookup"><span data-stu-id="a3f97-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="a3f97-105">如果您賦予<xref:System.Windows.Media.Animation.BeginStoryboard>藉由指定的名稱及其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>屬性，讓它可控制的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a3f97-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="a3f97-106">然後您可以以互動方式控制分鏡腳本開始後。</span><span class="sxs-lookup"><span data-stu-id="a3f97-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="a3f97-107">使用下列的分鏡腳本動作，並搭配<xref:System.Windows.EventTrigger>物件來控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a3f97-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard><span data-ttu-id="a3f97-108">:暫停分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a3f97-108">: Pauses the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard><span data-ttu-id="a3f97-109">:繼續已暫停的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a3f97-109">: Resumes a paused storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio><span data-ttu-id="a3f97-110">:變更分鏡腳本的速度。</span><span class="sxs-lookup"><span data-stu-id="a3f97-110">: Changes the storyboard speed.</span></span>  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill><span data-ttu-id="a3f97-111">:如果有的話，請前進到其填滿期間中，結尾的分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a3f97-111">: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard><span data-ttu-id="a3f97-112">:停止分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a3f97-112">: Stops the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard><span data-ttu-id="a3f97-113">:移除分鏡腳本，釋放資源。</span><span class="sxs-lookup"><span data-stu-id="a3f97-113">: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3f97-114">範例</span><span class="sxs-lookup"><span data-stu-id="a3f97-114">Example</span></span>  
 <span data-ttu-id="a3f97-115">下列範例會使用可控制的分鏡腳本動作以互動方式控制分鏡腳本。</span><span class="sxs-lookup"><span data-stu-id="a3f97-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="a3f97-116">**注意：** 若要查看使用程式碼來控制分鏡腳本的範例，請參閱[控制分鏡腳本之後它會開始使用其互動方法](how-to-control-a-storyboard-after-it-starts.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f97-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="a3f97-117">如需其他範例，請參閱 <<c0> [ 動畫範例圖庫](https://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="a3f97-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f97-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f97-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="a3f97-119">在分鏡腳本開始後，使用其互動方法來進行控制</span><span class="sxs-lookup"><span data-stu-id="a3f97-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="a3f97-120">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="a3f97-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="a3f97-121">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="a3f97-121">Storyboards Overview</span></span>](storyboards-overview.md)
