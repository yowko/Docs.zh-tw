---
title: "Timer 元件概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Timer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Timer 元件 [Windows Form], 關於 Timer 元件"
  - "計時器, 關於計時器"
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Timer 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.Timer> 是定期引發事件的元件。  這個元件是專為 Windows Form 環境而設計的。  如需適用於伺服器環境的計時器，請參閱[Introduction to Server\-Based Timers](http://msdn.microsoft.com/zh-tw/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
## 主要屬性、方法和事件  
 間隔的長短由 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性定義，其值是以毫秒為單位。  當啟用這個元件時，每個間隔都會引發 <xref:System.Windows.Forms.Timer.Tick> 事件。  這是您加入要執行程式碼的地方。  如需詳細資訊，請參閱 [如何：使用 Windows Form Timer 元件以設定的間隔執行程序](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md)。  <xref:System.Windows.Forms.Timer> 元件的主要方法是開啟和關閉計時器的 <xref:System.Windows.Forms.Timer.Start%2A> 和 <xref:System.Windows.Forms.Timer.Stop%2A>。  當關閉計時器時，計時器就會重設，沒有任何方法可以暫停 <xref:System.Windows.Forms.Timer> 元件。  
  
## 請參閱  
 <xref:System.Windows.Forms.Timer>   
 [Timer 元件](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)   
 [Windows Form Timer 元件的 Interval 屬性限制](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)