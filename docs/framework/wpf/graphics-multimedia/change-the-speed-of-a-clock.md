---
title: "如何：變更時鐘的速度而不變更其時刻表的速度"
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
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98cfa63eac4bc697c5412616de71395624408c63
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a><span data-ttu-id="465c5-102">如何：變更時鐘的速度而不變更其時刻表的速度</span><span class="sxs-lookup"><span data-stu-id="465c5-102">How to: Change the Speed of a Clock Without Changing the Speed of Its Timeline</span></span>
<span data-ttu-id="465c5-103">A<xref:System.Windows.Media.Animation.ClockController>物件的<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>屬性可讓您變更的速度<xref:System.Windows.Media.Animation.Clock>而不用更改<xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>的時鐘的<xref:System.Windows.Media.Animation.Timeline>。</span><span class="sxs-lookup"><span data-stu-id="465c5-103">A <xref:System.Windows.Media.Animation.ClockController> object's <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> property enables you to change the speed of a <xref:System.Windows.Media.Animation.Clock> without altering the <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> of the clock's <xref:System.Windows.Media.Animation.Timeline>.</span></span> <span data-ttu-id="465c5-104">在下列範例中，<xref:System.Windows.Media.Animation.ClockController>用來以互動方式修改<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>的時鐘。</span><span class="sxs-lookup"><span data-stu-id="465c5-104">In the following example, a <xref:System.Windows.Media.Animation.ClockController> is used to interactively modify the <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> of a clock.</span></span> <span data-ttu-id="465c5-105"><xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated>事件與時鐘的<xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A>屬性用來顯示時鐘的目前全域速度每次它互動式<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>變更。</span><span class="sxs-lookup"><span data-stu-id="465c5-105">The <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> event and the clock's <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> property are used to display the clock's current global speed each time its interactive <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> is changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="465c5-106">範例</span><span class="sxs-lookup"><span data-stu-id="465c5-106">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
