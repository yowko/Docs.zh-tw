---
title: "How to: Declare Custom Events To Conserve Memory (Visual Basic) | Microsoft Docs"
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
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Declare Custom Events To Conserve Memory (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

有幾種情況下，應用程式必須讓記憶體使用量保持最低。  自訂事件可以讓應用程式只針對所處理的事件使用記憶體。  
  
 根據預設，當類別 \(Class\) 宣告事件時，編譯器會為欄位配置記憶體，儲存事件資訊。  如果類別有許多未使用的事件，這些事件其實不需要使用記憶體。  
  
 您可以使用自訂事件更謹慎地管理記憶體使用量，而不要使用 Visual Basic 所提供的預設事件實作。  
  
## 範例  
 在這個範例中，類別會使用 <xref:System.ComponentModel.EventHandlerList> 類別的一個執行個體 \(儲存在 `Events` 欄位中\)，儲存使用中事件的相關資訊。  <xref:System.ComponentModel.EventHandlerList> 類別為專門設計用於存放委派 \(Delegate\) 的最佳化清單類別。  
  
 類別中的所有事件都會使用 `Events` 欄位，追蹤處理每個事件的方法為何。  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#22)]  
  
## 請參閱  
 <xref:System.ComponentModel.EventHandlerList>   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)