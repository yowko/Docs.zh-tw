---
title: "限制的 Windows Form Timer 元件 &#39; s [間隔] 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9c42a0946cf29415f7bb12345da6784e0c276d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="15d30-102">限制的 Windows Form Timer 元件 &#39; s [間隔] 屬性</span><span class="sxs-lookup"><span data-stu-id="15d30-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="15d30-103">Windows Form<xref:System.Windows.Forms.Timer>元件有<xref:System.Windows.Forms.Timer.Interval%2A>屬性，指定一個計時器事件和下之間所經過的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="15d30-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="15d30-104">除非已停用該元件，計時器會繼續接收<xref:System.Windows.Forms.Timer.Tick>大致相等間隔的時間的事件。</span><span class="sxs-lookup"><span data-stu-id="15d30-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="15d30-105">這個元件是專為 Windows Form 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="15d30-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="15d30-106">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。</span><span class="sxs-lookup"><span data-stu-id="15d30-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="15d30-107">[間隔] 屬性</span><span class="sxs-lookup"><span data-stu-id="15d30-107">The Interval Property</span></span>  
 <span data-ttu-id="15d30-108"><xref:System.Windows.Forms.Timer.Interval%2A>屬性有幾項限制來進行程式設計時，請考慮<xref:System.Windows.Forms.Timer>元件：</span><span class="sxs-lookup"><span data-stu-id="15d30-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="15d30-109">如果您的應用程式或其他應用程式在系統上進行大量的需求 — 例如長迴圈、 需要大量計算，或磁碟機、 網路或通訊埠存取，您的應用程式可能不會得到計時器事件，通常為<xref:System.Windows.Forms.Timer.Interval%2A>屬性會指定。</span><span class="sxs-lookup"><span data-stu-id="15d30-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="15d30-110">間隔不保證在時間上完全停用。</span><span class="sxs-lookup"><span data-stu-id="15d30-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="15d30-111">若要確保精確度，計時器應該檢查系統時鐘，如有需要而嘗試追蹤的累積的時間在內部。</span><span class="sxs-lookup"><span data-stu-id="15d30-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="15d30-112">有效位數<xref:System.Windows.Forms.Timer.Interval%2A>屬性是以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="15d30-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="15d30-113">某些電腦提供高解析度的計數器高於毫秒的解析度。</span><span class="sxs-lookup"><span data-stu-id="15d30-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="15d30-114">這類計數器的可用性取決於您的電腦的處理器硬體。</span><span class="sxs-lookup"><span data-stu-id="15d30-114">The availability of such a counter depends on the processor hardware of your computer.</span></span> <span data-ttu-id="15d30-115">如需詳細資訊，請參閱 172338，」 方式來使用 QueryPerformanceCounter 到時間程式碼，"在 Microsoft 知識庫文件在 http://support.microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="15d30-115">For more information, see article 172338, "How To Use QueryPerformanceCounter to Time Code," in the Microsoft Knowledge Base at http://support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d30-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="15d30-116">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="15d30-117">Timer 元件</span><span class="sxs-lookup"><span data-stu-id="15d30-117">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="15d30-118">Timer 元件概觀</span><span class="sxs-lookup"><span data-stu-id="15d30-118">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
