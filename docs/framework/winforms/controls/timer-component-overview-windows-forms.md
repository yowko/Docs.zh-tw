---
title: "Timer 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea78cadae6e033bc54274e5428ba5e8c6410259d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="c543a-102">Timer 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="c543a-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="c543a-103">Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。</span><span class="sxs-lookup"><span data-stu-id="c543a-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="c543a-104">這個元件是專為 Windows Form 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="c543a-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="c543a-105">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。</span><span class="sxs-lookup"><span data-stu-id="c543a-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="c543a-106">索引鍵屬性、 方法和事件</span><span class="sxs-lookup"><span data-stu-id="c543a-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="c543a-107">所定義的間隔長度<xref:System.Windows.Forms.Timer.Interval%2A>屬性，其值為以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="c543a-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="c543a-108">啟用此元件時，<xref:System.Windows.Forms.Timer.Tick>引發每個間隔。</span><span class="sxs-lookup"><span data-stu-id="c543a-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="c543a-109">這是您加入要執行的程式碼的地方。</span><span class="sxs-lookup"><span data-stu-id="c543a-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="c543a-110">如需詳細資訊，請參閱[How to： 在使用 Windows Form Timer 元件的設定時間間隔執行的程序](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c543a-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="c543a-111">主要方法<xref:System.Windows.Forms.Timer>元件是<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟計時器，開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="c543a-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="c543a-112">當計時器已關閉時，它會重設。沒有任何方法可以暫停<xref:System.Windows.Forms.Timer>元件。</span><span class="sxs-lookup"><span data-stu-id="c543a-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c543a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c543a-113">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="c543a-114">Timer 元件</span><span class="sxs-lookup"><span data-stu-id="c543a-114">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="c543a-115">Windows Forms Timer 元件的 Interval 屬性限制</span><span class="sxs-lookup"><span data-stu-id="c543a-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
