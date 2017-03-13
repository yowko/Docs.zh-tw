---
title: "How to: Declare Custom Events To Avoid Blocking (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declaring events, custom"
  - "events [Visual Basic], custom"
  - "custom events"
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Declare Custom Events To Avoid Blocking (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

如果其中一個事件處理常式未封鎖後續事件處理常式是十分重要的，則會有數種情況。  自訂事件允許事件非同步呼叫它的事件處理常式。  
  
 事件宣告的支援存放區欄位預設是連續結合所有事件處理常式的多點傳送委派 \(Delegate\)。  這表示如果某個處理常式需要較長的時間才能完成，則它會封鎖另一個處理常式，直到完成為止   \(行為正確的事件處理常式絕不會長期執行或封鎖作業\)。  
  
 不使用 Visual Basic 所提供之事件的預設實作，而是使用自訂事件非同步地執行事件處理常式。  
  
## 範例  
 在這個範例中，`AddHandler` 存取子 \(Accessor\) 會將 `Click` 事件之每個處理常式的委派加入至儲存在 `EventHandlerList` 欄位中的 <xref:System.Collections.ArrayList>。  
  
 程式碼引發 `Click` 事件時，`RaiseEvent` 存取子會使用 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> 方法非同步叫用 \(Invoke\) 所有事件處理常式委派。  該方法會叫用背景工作執行緒 \(Worker Thread\) 上的每個處理常式並立即傳回，因此，處理常式無法互相封鎖。  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## 請參閱  
 <xref:System.Collections.ArrayList>   
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)