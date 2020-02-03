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
# <a name="timer-component-overview-windows-forms"></a>Timer 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。 這個元件是專為 Windows Form 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。  
  
## <a name="key-properties-methods-and-events"></a>索引鍵屬性、方法和事件  
 間隔的長度是由 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性所定義，其值以毫秒為單位。 啟用元件時，會在每個間隔引發 <xref:System.Windows.Forms.Timer.Tick> 事件。 這是您要在其中加入要執行之程式碼的位置。 如需詳細資訊，請參閱 how [to：使用 Windows Forms 計時器元件以設定的間隔執行程式](run-procedures-at-set-intervals-with-wf-timer-component.md)。 <xref:System.Windows.Forms.Timer> 元件的主要方法是 <xref:System.Windows.Forms.Timer.Start%2A> 和 <xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟和關閉計時器。 當計時器切換為關閉時，它會重設;沒有任何方法可以暫停 <xref:System.Windows.Forms.Timer> 元件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Timer>
- [Timer 元件](timer-component-windows-forms.md)
- [Windows Forms Timer 元件的 Interval 屬性限制](limitations-of-the-timer-component-interval-property.md)
