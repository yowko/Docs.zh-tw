---
title: HOW TO：變更時鐘的速度而不變更其時間表的速度
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 19e6874b9b472cb4a5f716677f99af03f2b73b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010185"
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a><span data-ttu-id="aa3ff-102">HOW TO：變更時鐘的速度而不變更其時間表的速度</span><span class="sxs-lookup"><span data-stu-id="aa3ff-102">How to: Change the Speed of a Clock Without Changing the Speed of Its Timeline</span></span>
<span data-ttu-id="aa3ff-103">A<xref:System.Windows.Media.Animation.ClockController>物件的<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>屬性可讓您變更的速度<xref:System.Windows.Media.Animation.Clock>而不需要改變<xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>時鐘的<xref:System.Windows.Media.Animation.Timeline>。</span><span class="sxs-lookup"><span data-stu-id="aa3ff-103">A <xref:System.Windows.Media.Animation.ClockController> object's <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> property enables you to change the speed of a <xref:System.Windows.Media.Animation.Clock> without altering the <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> of the clock's <xref:System.Windows.Media.Animation.Timeline>.</span></span> <span data-ttu-id="aa3ff-104">在下列範例中，<xref:System.Windows.Media.Animation.ClockController>用來以互動方式修改<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>的時鐘。</span><span class="sxs-lookup"><span data-stu-id="aa3ff-104">In the following example, a <xref:System.Windows.Media.Animation.ClockController> is used to interactively modify the <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> of a clock.</span></span> <span data-ttu-id="aa3ff-105"><xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated>事件和時鐘<xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A>屬性用來顯示時鐘的目前的整體速度每次在其互動式<xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A>變更。</span><span class="sxs-lookup"><span data-stu-id="aa3ff-105">The <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> event and the clock's <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> property are used to display the clock's current global speed each time its interactive <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> is changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa3ff-106">範例</span><span class="sxs-lookup"><span data-stu-id="aa3ff-106">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
