---
title: 計時器元件間隔屬性的限制
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745240"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="d1d40-102">Windows Form Timer 元件的 Interval 屬性限制</span><span class="sxs-lookup"><span data-stu-id="d1d40-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="d1d40-103">Windows Forms <xref:System.Windows.Forms.Timer> 元件具有 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性，可指定在一個計時器事件和下一次之間傳遞的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="d1d40-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="d1d40-104">除非停用此元件，否則計時器會繼續以大約相等的時間間隔接收 <xref:System.Windows.Forms.Timer.Tick> 事件。</span><span class="sxs-lookup"><span data-stu-id="d1d40-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="d1d40-105">這個元件是專為 Windows Form 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="d1d40-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="d1d40-106">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="d1d40-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="d1d40-107">Interval 屬性</span><span class="sxs-lookup"><span data-stu-id="d1d40-107">The Interval Property</span></span>  
 <span data-ttu-id="d1d40-108">當您進行 <xref:System.Windows.Forms.Timer> 元件的程式設計時，<xref:System.Windows.Forms.Timer.Interval%2A> 屬性有幾個需要考慮的限制：</span><span class="sxs-lookup"><span data-stu-id="d1d40-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="d1d40-109">如果您的應用程式或其他應用程式在系統上進行繁重的需求（例如長迴圈、密集計算，或磁片磁碟機、網路或埠存取），您的應用程式可能不會在 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性指定的情況下，經常取得計時器事件。</span><span class="sxs-lookup"><span data-stu-id="d1d40-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="d1d40-110">此間隔不保證會剛好準時經過。</span><span class="sxs-lookup"><span data-stu-id="d1d40-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="d1d40-111">為確保正確性，計時器應該視需要檢查系統時鐘，而不是嘗試在內部追蹤累積的時間。</span><span class="sxs-lookup"><span data-stu-id="d1d40-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="d1d40-112"><xref:System.Windows.Forms.Timer.Interval%2A> 屬性的有效位數（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="d1d40-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="d1d40-113">有些電腦提供高解析度的計數器，其解析度高於毫秒。</span><span class="sxs-lookup"><span data-stu-id="d1d40-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="d1d40-114">這類計數器的可用性取決於您電腦的處理器硬體。</span><span class="sxs-lookup"><span data-stu-id="d1d40-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d1d40-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1d40-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="d1d40-116">Timer 元件</span><span class="sxs-lookup"><span data-stu-id="d1d40-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="d1d40-117">Timer 元件概觀</span><span class="sxs-lookup"><span data-stu-id="d1d40-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
