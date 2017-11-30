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
ms.openlocfilehash: 2abce54905f0bb06bf983c065e064ce2dfeba932
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="cda74-102">如何：指定時刻表是否會自動反轉</span><span class="sxs-lookup"><span data-stu-id="cda74-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="cda74-103">時間軸的<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性會決定是否它在後反向播放完成向前反覆項目。</span><span class="sxs-lookup"><span data-stu-id="cda74-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="cda74-104">下列範例顯示相同的持續時間和目標值，但具有不同的數個動畫<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="cda74-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="cda74-105">若要示範如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性具有不同的行為<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>設定，某些動畫會設定為重複。</span><span class="sxs-lookup"><span data-stu-id="cda74-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="cda74-106">最後一個動畫顯示如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性巢狀的時間軸上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="cda74-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cda74-107">範例</span><span class="sxs-lookup"><span data-stu-id="cda74-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
