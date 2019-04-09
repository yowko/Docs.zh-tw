---
title: Timer 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 5bef0ba87d6a496acf7575965128be2b20b437ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074205"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="beea5-102">Timer 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="beea5-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="beea5-103">Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。</span><span class="sxs-lookup"><span data-stu-id="beea5-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="beea5-104">這個元件是專為 Windows Form 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="beea5-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="beea5-105">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="beea5-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="beea5-106">索引鍵屬性、 方法和事件</span><span class="sxs-lookup"><span data-stu-id="beea5-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="beea5-107">所定義的間隔長度<xref:System.Windows.Forms.Timer.Interval%2A>屬性，其值是以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="beea5-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="beea5-108">啟用此元件時，<xref:System.Windows.Forms.Timer.Tick>就會引發事件在每個間隔。</span><span class="sxs-lookup"><span data-stu-id="beea5-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="beea5-109">這是您會在此加入要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="beea5-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="beea5-110">如需詳細資訊，請參閱[如何：使用 Windows Form Timer 元件集間隔執行程序](run-procedures-at-set-intervals-with-wf-timer-component.md)。</span><span class="sxs-lookup"><span data-stu-id="beea5-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="beea5-111">主要方法<xref:System.Windows.Forms.Timer>元件<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟計時器，開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="beea5-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="beea5-112">當計時器關閉時，它會重設;沒有任何方法來暫停<xref:System.Windows.Forms.Timer>元件。</span><span class="sxs-lookup"><span data-stu-id="beea5-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beea5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beea5-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="beea5-114">Timer 元件</span><span class="sxs-lookup"><span data-stu-id="beea5-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="beea5-115">Windows Form Timer 元件的 Interval 屬性限制</span><span class="sxs-lookup"><span data-stu-id="beea5-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
