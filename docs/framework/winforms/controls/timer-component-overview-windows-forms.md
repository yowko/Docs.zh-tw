---
title: Timer 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: a13afba026f1f9eed095817c65637bb6a091c7f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725281"
---
# <a name="timer-component-overview-windows-forms"></a>Timer 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。 這個元件是專為 Windows Form 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。  
  
## <a name="key-properties-methods-and-events"></a>索引鍵屬性、 方法和事件  
 所定義的間隔長度<xref:System.Windows.Forms.Timer.Interval%2A>屬性，其值是以毫秒為單位。 啟用此元件時，<xref:System.Windows.Forms.Timer.Tick>就會引發事件在每個間隔。 這是您會在此加入要執行的程式碼。 如需詳細資訊，請參閱[如何：使用 Windows Form Timer 元件集間隔執行程序](run-procedures-at-set-intervals-with-wf-timer-component.md)。 主要方法<xref:System.Windows.Forms.Timer>元件<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟計時器，開啟和關閉。 當計時器關閉時，它會重設;沒有任何方法來暫停<xref:System.Windows.Forms.Timer>元件。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Timer>
- [Timer 元件](timer-component-windows-forms.md)
- [Windows Forms Timer 元件的 Interval 屬性限制](limitations-of-the-timer-component-interval-property.md)
