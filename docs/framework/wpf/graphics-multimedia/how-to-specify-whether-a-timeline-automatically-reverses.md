---
title: HOW TO：指定時間表是否自動反轉
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024660"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="10bc9-102">HOW TO：指定時間表是否自動反轉</span><span class="sxs-lookup"><span data-stu-id="10bc9-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="10bc9-103">時間軸的<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性會決定是否就會在反向播放之後完成向前反覆項目。</span><span class="sxs-lookup"><span data-stu-id="10bc9-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="10bc9-104">下列範例示範使用相同的持續時間和目標值，但具有不同的數個動畫<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="10bc9-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="10bc9-105">若要示範如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性具有不同的行為<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>某些動畫的設定會設定為重複。</span><span class="sxs-lookup"><span data-stu-id="10bc9-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="10bc9-106">最後一個動畫顯示如何<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>屬性巢狀時間軸上的運作方式。</span><span class="sxs-lookup"><span data-stu-id="10bc9-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10bc9-107">範例</span><span class="sxs-lookup"><span data-stu-id="10bc9-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
