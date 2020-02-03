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
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Windows Form Timer 元件的 Interval 屬性限制
Windows Forms <xref:System.Windows.Forms.Timer> 元件具有 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性，可指定在一個計時器事件和下一次之間傳遞的毫秒數。 除非停用此元件，否則計時器會繼續以大約相等的時間間隔接收 <xref:System.Windows.Forms.Timer.Tick> 事件。  
  
 這個元件是專為 Windows Form 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。  
  
## <a name="the-interval-property"></a>Interval 屬性  
 當您進行 <xref:System.Windows.Forms.Timer> 元件的程式設計時，<xref:System.Windows.Forms.Timer.Interval%2A> 屬性有幾個需要考慮的限制：  
  
- 如果您的應用程式或其他應用程式在系統上進行繁重的需求（例如長迴圈、密集計算，或磁片磁碟機、網路或埠存取），您的應用程式可能不會在 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性指定的情況下，經常取得計時器事件。  
  
- 此間隔不保證會剛好準時經過。 為確保正確性，計時器應該視需要檢查系統時鐘，而不是嘗試在內部追蹤累積的時間。  
  
- <xref:System.Windows.Forms.Timer.Interval%2A> 屬性的有效位數（以毫秒為單位）。 有些電腦提供高解析度的計數器，其解析度高於毫秒。 這類計數器的可用性取決於您電腦的處理器硬體。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Timer>
- [Timer 元件](timer-component-windows-forms.md)
- [Timer 元件概觀](timer-component-overview-windows-forms.md)
