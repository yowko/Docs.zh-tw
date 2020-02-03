---
title: Timer 元件概觀
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742777"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="93746-102">Timer 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="93746-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="93746-103">Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。</span><span class="sxs-lookup"><span data-stu-id="93746-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="93746-104">這個元件是專為 Windows Form 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="93746-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="93746-105">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="93746-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="93746-106">索引鍵屬性、方法和事件</span><span class="sxs-lookup"><span data-stu-id="93746-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="93746-107">間隔的長度是由 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性所定義，其值以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="93746-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="93746-108">啟用元件時，會在每個間隔引發 <xref:System.Windows.Forms.Timer.Tick> 事件。</span><span class="sxs-lookup"><span data-stu-id="93746-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="93746-109">這是您要在其中加入要執行之程式碼的位置。</span><span class="sxs-lookup"><span data-stu-id="93746-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="93746-110">如需詳細資訊，請參閱 how [to：使用 Windows Forms 計時器元件以設定的間隔執行程式](run-procedures-at-set-intervals-with-wf-timer-component.md)。</span><span class="sxs-lookup"><span data-stu-id="93746-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="93746-111"><xref:System.Windows.Forms.Timer> 元件的主要方法是 <xref:System.Windows.Forms.Timer.Start%2A> 和 <xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟和關閉計時器。</span><span class="sxs-lookup"><span data-stu-id="93746-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="93746-112">當計時器切換為關閉時，它會重設;沒有任何方法可以暫停 <xref:System.Windows.Forms.Timer> 元件。</span><span class="sxs-lookup"><span data-stu-id="93746-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93746-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93746-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="93746-114">Timer 元件</span><span class="sxs-lookup"><span data-stu-id="93746-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="93746-115">Windows Forms Timer 元件的 Interval 屬性限制</span><span class="sxs-lookup"><span data-stu-id="93746-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
