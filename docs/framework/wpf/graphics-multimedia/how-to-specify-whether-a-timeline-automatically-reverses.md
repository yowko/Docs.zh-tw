---
title: "如何：指定時刻表是否會自動反轉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da1330a8513f43e7543f97838ef8e9be788af396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="97f0e-102">如何：指定時刻表是否會自動反轉</span><span class="sxs-lookup"><span data-stu-id="97f0e-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="97f0e-103">時間軸的<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性會決定是否它在後反向播放完成向前反覆項目。</span><span class="sxs-lookup"><span data-stu-id="97f0e-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="97f0e-104">下列範例顯示相同的持續時間和目標值，但具有不同的數個動畫<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="97f0e-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="97f0e-105">若要示範如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性具有不同的行為<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>設定，某些動畫會設定為重複。</span><span class="sxs-lookup"><span data-stu-id="97f0e-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="97f0e-106">最後一個動畫顯示如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性巢狀的時間軸上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="97f0e-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97f0e-107">範例</span><span class="sxs-lookup"><span data-stu-id="97f0e-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
