---
title: HOW TO：在時鐘的狀態變更時接收通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: dc3fffb88ce59ceb908d6febd2f078820513b641
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942128"
---
# <a name="how-to-receive-notification-when-a-clocks-state-changes"></a><span data-ttu-id="5f3b8-102">HOW TO：在時鐘的狀態變更時接收通知</span><span class="sxs-lookup"><span data-stu-id="5f3b8-102">How to: Receive Notification When a Clock's State Changes</span></span>
<span data-ttu-id="5f3b8-103">時鐘<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>就會發生事件時其<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>就會變成無效，例如當時鐘啟動或停止。</span><span class="sxs-lookup"><span data-stu-id="5f3b8-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="5f3b8-104">您可以直接使用這個事件註冊<xref:System.Windows.Media.Animation.Clock>，或您可以註冊使用<xref:System.Windows.Media.Animation.Timeline>。</span><span class="sxs-lookup"><span data-stu-id="5f3b8-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="5f3b8-105">在下列範例中，<xref:System.Windows.Media.Animation.Storyboard>並將兩個<xref:System.Windows.Media.Animation.DoubleAnimation>物件用來以動畫顯示兩個矩形的寬度。</span><span class="sxs-lookup"><span data-stu-id="5f3b8-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="5f3b8-106"><xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>事件用來接聽的時鐘狀態變更。</span><span class="sxs-lookup"><span data-stu-id="5f3b8-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f3b8-107">範例</span><span class="sxs-lookup"><span data-stu-id="5f3b8-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="5f3b8-108">下圖顯示動畫的不同狀態輸入為父時間軸 (*分鏡腳本*) 進行。</span><span class="sxs-lookup"><span data-stu-id="5f3b8-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="5f3b8-109">![具有兩個動畫的分鏡腳本的時鐘狀態](./media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="5f3b8-109">![Clock states for a Storyboard with two animations](./media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="5f3b8-110">下表顯示時間處*Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>引發事件：</span><span class="sxs-lookup"><span data-stu-id="5f3b8-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="5f3b8-111">時間 （秒）</span><span class="sxs-lookup"><span data-stu-id="5f3b8-111">Time (Seconds)</span></span>|<span data-ttu-id="5f3b8-112">1</span><span class="sxs-lookup"><span data-stu-id="5f3b8-112">1</span></span>|<span data-ttu-id="5f3b8-113">10</span><span class="sxs-lookup"><span data-stu-id="5f3b8-113">10</span></span>|<span data-ttu-id="5f3b8-114">19</span><span class="sxs-lookup"><span data-stu-id="5f3b8-114">19</span></span>|<span data-ttu-id="5f3b8-115">21</span><span class="sxs-lookup"><span data-stu-id="5f3b8-115">21</span></span>|<span data-ttu-id="5f3b8-116">30</span><span class="sxs-lookup"><span data-stu-id="5f3b8-116">30</span></span>|<span data-ttu-id="5f3b8-117">39</span><span class="sxs-lookup"><span data-stu-id="5f3b8-117">39</span></span>|  
|<span data-ttu-id="5f3b8-118">狀況</span><span class="sxs-lookup"><span data-stu-id="5f3b8-118">State</span></span>|<span data-ttu-id="5f3b8-119">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-119">Active</span></span>|<span data-ttu-id="5f3b8-120">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-120">Active</span></span>|<span data-ttu-id="5f3b8-121">已停止</span><span class="sxs-lookup"><span data-stu-id="5f3b8-121">Stopped</span></span>|<span data-ttu-id="5f3b8-122">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-122">Active</span></span>|<span data-ttu-id="5f3b8-123">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-123">Active</span></span>|<span data-ttu-id="5f3b8-124">已停止</span><span class="sxs-lookup"><span data-stu-id="5f3b8-124">Stopped</span></span>|  
  
 <span data-ttu-id="5f3b8-125">下表顯示時間處*Animation2*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>引發事件：</span><span class="sxs-lookup"><span data-stu-id="5f3b8-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="5f3b8-126">時間 （秒）</span><span class="sxs-lookup"><span data-stu-id="5f3b8-126">Time (Seconds)</span></span>|<span data-ttu-id="5f3b8-127">1</span><span class="sxs-lookup"><span data-stu-id="5f3b8-127">1</span></span>|<span data-ttu-id="5f3b8-128">9</span><span class="sxs-lookup"><span data-stu-id="5f3b8-128">9</span></span>|<span data-ttu-id="5f3b8-129">11</span><span class="sxs-lookup"><span data-stu-id="5f3b8-129">11</span></span>|<span data-ttu-id="5f3b8-130">19</span><span class="sxs-lookup"><span data-stu-id="5f3b8-130">19</span></span>|<span data-ttu-id="5f3b8-131">21</span><span class="sxs-lookup"><span data-stu-id="5f3b8-131">21</span></span>|<span data-ttu-id="5f3b8-132">29</span><span class="sxs-lookup"><span data-stu-id="5f3b8-132">29</span></span>|<span data-ttu-id="5f3b8-133">31</span><span class="sxs-lookup"><span data-stu-id="5f3b8-133">31</span></span>|<span data-ttu-id="5f3b8-134">39</span><span class="sxs-lookup"><span data-stu-id="5f3b8-134">39</span></span>|  
|<span data-ttu-id="5f3b8-135">狀況</span><span class="sxs-lookup"><span data-stu-id="5f3b8-135">State</span></span>|<span data-ttu-id="5f3b8-136">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-136">Active</span></span>|<span data-ttu-id="5f3b8-137">填滿</span><span class="sxs-lookup"><span data-stu-id="5f3b8-137">Filling</span></span>|<span data-ttu-id="5f3b8-138">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-138">Active</span></span>|<span data-ttu-id="5f3b8-139">已停止</span><span class="sxs-lookup"><span data-stu-id="5f3b8-139">Stopped</span></span>|<span data-ttu-id="5f3b8-140">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-140">Active</span></span>|<span data-ttu-id="5f3b8-141">填滿</span><span class="sxs-lookup"><span data-stu-id="5f3b8-141">Filling</span></span>|<span data-ttu-id="5f3b8-142">作用中</span><span class="sxs-lookup"><span data-stu-id="5f3b8-142">Active</span></span>|<span data-ttu-id="5f3b8-143">已停止</span><span class="sxs-lookup"><span data-stu-id="5f3b8-143">Stopped</span></span>|  
  
 <span data-ttu-id="5f3b8-144">請注意， *Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>就會引發事件在 10 秒，即使其狀態會維持<xref:System.Windows.Media.Animation.ClockState.Active>。</span><span class="sxs-lookup"><span data-stu-id="5f3b8-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="5f3b8-145">這是因為其狀態變更在 10 秒，但從變更<xref:System.Windows.Media.Animation.ClockState.Active>要<xref:System.Windows.Media.Animation.ClockState.Filling>，然後再回到<xref:System.Windows.Media.Animation.ClockState.Active>中相同的刻度。</span><span class="sxs-lookup"><span data-stu-id="5f3b8-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
