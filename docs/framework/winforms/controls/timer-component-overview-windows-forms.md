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
ms.workload: dotnet
ms.openlocfilehash: 90296d2741a96e8788bf7a9b18bf3ea303ad2bae
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="timer-component-overview-windows-forms"></a>Timer 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。 這個元件是專為 Windows Form 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
## <a name="key-properties-methods-and-events"></a>索引鍵屬性、 方法和事件  
 所定義的間隔長度<xref:System.Windows.Forms.Timer.Interval%2A>屬性，其值為以毫秒為單位。 啟用此元件時，<xref:System.Windows.Forms.Timer.Tick>引發每個間隔。 這是您加入要執行的程式碼的地方。 如需詳細資訊，請參閱[How to： 在使用 Windows Form Timer 元件的設定時間間隔執行的程序](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)。 主要方法<xref:System.Windows.Forms.Timer>元件是<xref:System.Windows.Forms.Timer.Start%2A>和<xref:System.Windows.Forms.Timer.Stop%2A>，這會開啟計時器，開啟和關閉。 當計時器已關閉時，它會重設。沒有任何方法可以暫停<xref:System.Windows.Forms.Timer>元件。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Timer>  
 [Timer 元件](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Windows Forms Timer 元件的 Interval 屬性限制](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
