---
title: Windows Form Timer 元件的限制&#39;s [間隔] 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 9710568c3c21878aa6aad626e3152168a2f0c2fe
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836390"
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="95e96-102">Windows Form Timer 元件的限制&#39;s [間隔] 屬性</span><span class="sxs-lookup"><span data-stu-id="95e96-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="95e96-103">Windows Forms<xref:System.Windows.Forms.Timer>元件有<xref:System.Windows.Forms.Timer.Interval%2A>屬性，指定一個計時器事件和下一步 之間傳遞的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="95e96-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="95e96-104">除非已停用元件，計時器會繼續接收<xref:System.Windows.Forms.Timer.Tick>大致相等間隔的時間的事件。</span><span class="sxs-lookup"><span data-stu-id="95e96-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="95e96-105">這個元件是專為 Windows Form 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="95e96-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="95e96-106">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。</span><span class="sxs-lookup"><span data-stu-id="95e96-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="95e96-107">[間隔] 屬性</span><span class="sxs-lookup"><span data-stu-id="95e96-107">The Interval Property</span></span>  
 <span data-ttu-id="95e96-108"><xref:System.Windows.Forms.Timer.Interval%2A>屬性有幾項限制來進行程式設計時，請考慮<xref:System.Windows.Forms.Timer>元件：</span><span class="sxs-lookup"><span data-stu-id="95e96-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="95e96-109">如果您的應用程式或其他應用程式正在大量耗用系統上 — 例如長迴圈、 需要大量計算，或磁碟機、 網路或連接埠存取 — 您的應用程式可能不會取得計時器事件，通常為<xref:System.Windows.Forms.Timer.Interval%2A>屬性指定。</span><span class="sxs-lookup"><span data-stu-id="95e96-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="95e96-110">不保證經過完全在時間間隔。</span><span class="sxs-lookup"><span data-stu-id="95e96-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="95e96-111">若要確保精確度，計時器應該檢查系統時鐘，如有需要而嘗試追蹤的累積的時間在內部。</span><span class="sxs-lookup"><span data-stu-id="95e96-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="95e96-112">有效位數<xref:System.Windows.Forms.Timer.Interval%2A>屬性是以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="95e96-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="95e96-113">某些電腦提供的高解析度計數器高於微秒的解析度。</span><span class="sxs-lookup"><span data-stu-id="95e96-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="95e96-114">這種計數器的可用性取決於您的電腦的處理器硬體。</span><span class="sxs-lookup"><span data-stu-id="95e96-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="95e96-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e96-115">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="95e96-116">Timer 元件</span><span class="sxs-lookup"><span data-stu-id="95e96-116">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="95e96-117">Timer 元件概觀</span><span class="sxs-lookup"><span data-stu-id="95e96-117">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
