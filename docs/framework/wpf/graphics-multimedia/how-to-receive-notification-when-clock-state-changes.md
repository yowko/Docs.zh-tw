---
title: 如何： 接收通知時時鐘&#39;s 狀態變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: d0eaca4d2a05d01e686efc15dfceebb6de4f4b64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561169"
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="9c6c4-102">如何： 接收通知時時鐘&#39;s 狀態變更</span><span class="sxs-lookup"><span data-stu-id="9c6c4-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="9c6c4-103">時鐘的<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>就會發生事件時其<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>就變成無效，例如當時鐘啟動或停止。</span><span class="sxs-lookup"><span data-stu-id="9c6c4-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="9c6c4-104">您可以直接使用這個事件註冊<xref:System.Windows.Media.Animation.Clock>，也可以註冊使用<xref:System.Windows.Media.Animation.Timeline>。</span><span class="sxs-lookup"><span data-stu-id="9c6c4-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="9c6c4-105">在下列範例中，<xref:System.Windows.Media.Animation.Storyboard>和兩個<xref:System.Windows.Media.Animation.DoubleAnimation>物件用來繪製兩個矩形的寬度。</span><span class="sxs-lookup"><span data-stu-id="9c6c4-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="9c6c4-106"><xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> 」 事件可用來接聽的時鐘狀態變更。</span><span class="sxs-lookup"><span data-stu-id="9c6c4-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c6c4-107">範例</span><span class="sxs-lookup"><span data-stu-id="9c6c4-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="9c6c4-108">下圖顯示不同的狀態動畫輸入做為父時間軸 (*分鏡腳本*) 進行。</span><span class="sxs-lookup"><span data-stu-id="9c6c4-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="9c6c4-109">![具有兩個動畫分鏡腳本的時鐘狀態](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="9c6c4-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="9c6c4-110">下表顯示時間的*Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>事件引發：</span><span class="sxs-lookup"><span data-stu-id="9c6c4-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="9c6c4-111">時間 （秒）</span><span class="sxs-lookup"><span data-stu-id="9c6c4-111">Time (Seconds)</span></span>|<span data-ttu-id="9c6c4-112">1</span><span class="sxs-lookup"><span data-stu-id="9c6c4-112">1</span></span>|<span data-ttu-id="9c6c4-113">10</span><span class="sxs-lookup"><span data-stu-id="9c6c4-113">10</span></span>|<span data-ttu-id="9c6c4-114">19</span><span class="sxs-lookup"><span data-stu-id="9c6c4-114">19</span></span>|<span data-ttu-id="9c6c4-115">21</span><span class="sxs-lookup"><span data-stu-id="9c6c4-115">21</span></span>|<span data-ttu-id="9c6c4-116">30</span><span class="sxs-lookup"><span data-stu-id="9c6c4-116">30</span></span>|<span data-ttu-id="9c6c4-117">39</span><span class="sxs-lookup"><span data-stu-id="9c6c4-117">39</span></span>|  
|<span data-ttu-id="9c6c4-118">狀況</span><span class="sxs-lookup"><span data-stu-id="9c6c4-118">State</span></span>|<span data-ttu-id="9c6c4-119">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-119">Active</span></span>|<span data-ttu-id="9c6c4-120">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-120">Active</span></span>|<span data-ttu-id="9c6c4-121">已停止</span><span class="sxs-lookup"><span data-stu-id="9c6c4-121">Stopped</span></span>|<span data-ttu-id="9c6c4-122">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-122">Active</span></span>|<span data-ttu-id="9c6c4-123">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-123">Active</span></span>|<span data-ttu-id="9c6c4-124">已停止</span><span class="sxs-lookup"><span data-stu-id="9c6c4-124">Stopped</span></span>|  
  
 <span data-ttu-id="9c6c4-125">下表顯示時間的*Animation2*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>事件引發：</span><span class="sxs-lookup"><span data-stu-id="9c6c4-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="9c6c4-126">時間 （秒）</span><span class="sxs-lookup"><span data-stu-id="9c6c4-126">Time (Seconds)</span></span>|<span data-ttu-id="9c6c4-127">1</span><span class="sxs-lookup"><span data-stu-id="9c6c4-127">1</span></span>|<span data-ttu-id="9c6c4-128">9</span><span class="sxs-lookup"><span data-stu-id="9c6c4-128">9</span></span>|<span data-ttu-id="9c6c4-129">11</span><span class="sxs-lookup"><span data-stu-id="9c6c4-129">11</span></span>|<span data-ttu-id="9c6c4-130">19</span><span class="sxs-lookup"><span data-stu-id="9c6c4-130">19</span></span>|<span data-ttu-id="9c6c4-131">21</span><span class="sxs-lookup"><span data-stu-id="9c6c4-131">21</span></span>|<span data-ttu-id="9c6c4-132">29</span><span class="sxs-lookup"><span data-stu-id="9c6c4-132">29</span></span>|<span data-ttu-id="9c6c4-133">31</span><span class="sxs-lookup"><span data-stu-id="9c6c4-133">31</span></span>|<span data-ttu-id="9c6c4-134">39</span><span class="sxs-lookup"><span data-stu-id="9c6c4-134">39</span></span>|  
|<span data-ttu-id="9c6c4-135">狀況</span><span class="sxs-lookup"><span data-stu-id="9c6c4-135">State</span></span>|<span data-ttu-id="9c6c4-136">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-136">Active</span></span>|<span data-ttu-id="9c6c4-137">填滿</span><span class="sxs-lookup"><span data-stu-id="9c6c4-137">Filling</span></span>|<span data-ttu-id="9c6c4-138">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-138">Active</span></span>|<span data-ttu-id="9c6c4-139">已停止</span><span class="sxs-lookup"><span data-stu-id="9c6c4-139">Stopped</span></span>|<span data-ttu-id="9c6c4-140">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-140">Active</span></span>|<span data-ttu-id="9c6c4-141">填滿</span><span class="sxs-lookup"><span data-stu-id="9c6c4-141">Filling</span></span>|<span data-ttu-id="9c6c4-142">作用中</span><span class="sxs-lookup"><span data-stu-id="9c6c4-142">Active</span></span>|<span data-ttu-id="9c6c4-143">已停止</span><span class="sxs-lookup"><span data-stu-id="9c6c4-143">Stopped</span></span>|  
  
 <span data-ttu-id="9c6c4-144">請注意， *Animation1*的<xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>就會引發事件在 10 秒，即使其狀態會維持<xref:System.Windows.Media.Animation.ClockState.Active>。</span><span class="sxs-lookup"><span data-stu-id="9c6c4-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="9c6c4-145">這是因為其狀態變更在 10 秒，但其變更從<xref:System.Windows.Media.Animation.ClockState.Active>至<xref:System.Windows.Media.Animation.ClockState.Filling>然後再設回<xref:System.Windows.Media.Animation.ClockState.Active>中相同的刻度。</span><span class="sxs-lookup"><span data-stu-id="9c6c4-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
