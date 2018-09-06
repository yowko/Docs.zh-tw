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
# <a name="timer-component-overview-windows-forms"></a>Timer 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。 這個元件是專為 Windows Form 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
## <a name="key-properties-methods-and-events"></a>索引鍵屬性、 方法和事件  
 所定義的間隔長度<xref:System.Windows.Forms.Timer.Interval%2A>屬性，其值是以毫秒為單位。 啟用此元件時，<xref:System.Windows.Forms.Timer.Tick>就會引發事件在每個間隔。 這是您會在此加入要執行的程式碼。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用 Windows Form Timer 元件設定的間隔執行程序](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)。 主要方法<xref:System.Windows.Forms.Timer>元件<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟計時器，開啟和關閉。 當計時器關閉時，它會重設;沒有任何方法來暫停<xref:System.Windows.Forms.Timer>元件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Timer>  
 [Timer 元件](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Windows Forms Timer 元件的 Interval 屬性限制](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
