---
title: "Windows Form Timer 元件的 Interval 屬性限制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Interval 屬性, 限制"
  - "Timer 元件 [Windows Form], Interval 屬性的限制"
  - "計時器, 事件間隔"
  - "計時器, Windows 架構"
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows Form Timer 元件的 Interval 屬性限制
Windows Form <xref:System.Windows.Forms.Timer> 元件具有 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性，以指定計時器事件與下一個事件之間經過多少毫秒數。  除非元件被停用，否則計時器將持續在大約相等的時間間隔點，收到 <xref:System.Windows.Forms.Timer.Tick> 的事件。  
  
 這個元件是專為 Windows Form 環境而設計的。  如需適用於伺服器環境的計時器，請參閱[Introduction to Server\-Based Timers](http://msdn.microsoft.com/zh-tw/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
## Interval 屬性  
 當您在設計有關 <xref:System.Windows.Forms.Timer> 元件的程式時，必須考慮 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性的一些限制：  
  
-   如果您的應用程式或其他應用程式對系統有大量的需求 \(例如長迴圈、密集的計算或磁碟機、網路或連接埠存取\)，則您的應用程式可能不會依照 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性的指定取得計時器事件。  
  
-   間隔不保證經過時間的精確性。  若要確保正確性，計時器應該檢查系統時鐘，而不是在內部追蹤累積的時間。  
  
-   <xref:System.Windows.Forms.Timer.Interval%2A> 屬性的精確性為毫秒。  某些電腦提供高解析度的計數器，其解析度高於毫秒。  是否提供這類計數器則根據您電腦的處理器硬體而定。  如需詳細資訊，請參閱 http:\/\/support.microsoft.com 上的 Microsoft 知識庫文件 172338＜How To Use QueryPerformanceCounter to Time Code＞。  
  
## 請參閱  
 <xref:System.Windows.Forms.Timer>   
 [Timer 元件](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)   
 [Timer 元件概觀](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)