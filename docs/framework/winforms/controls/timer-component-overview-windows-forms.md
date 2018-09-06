---
title: Timer 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 6e453f6b7718c6c5be3109f51153a3f5e4b5b6f4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733725"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="11b69-102">Timer 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="11b69-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="11b69-103">Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。</span><span class="sxs-lookup"><span data-stu-id="11b69-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="11b69-104">這個元件是專為 Windows Form 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="11b69-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="11b69-105">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。</span><span class="sxs-lookup"><span data-stu-id="11b69-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="11b69-106">索引鍵屬性、 方法和事件</span><span class="sxs-lookup"><span data-stu-id="11b69-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="11b69-107">所定義的間隔長度<xref:System.Windows.Forms.Timer.Interval%2A>屬性，其值是以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="11b69-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="11b69-108">啟用此元件時，<xref:System.Windows.Forms.Timer.Tick>就會引發事件在每個間隔。</span><span class="sxs-lookup"><span data-stu-id="11b69-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="11b69-109">這是您會在此加入要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="11b69-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="11b69-110">如需詳細資訊，請參閱 <<c0> [ 如何： 使用 Windows Form Timer 元件設定的間隔執行程序](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)。</span><span class="sxs-lookup"><span data-stu-id="11b69-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="11b69-111">主要方法<xref:System.Windows.Forms.Timer>元件<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟計時器，開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="11b69-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="11b69-112">當計時器關閉時，它會重設;沒有任何方法來暫停<xref:System.Windows.Forms.Timer>元件。</span><span class="sxs-lookup"><span data-stu-id="11b69-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b69-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11b69-113">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="11b69-114">Timer 元件</span><span class="sxs-lookup"><span data-stu-id="11b69-114">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="11b69-115">Windows Forms Timer 元件的 Interval 屬性限制</span><span class="sxs-lookup"><span data-stu-id="11b69-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
