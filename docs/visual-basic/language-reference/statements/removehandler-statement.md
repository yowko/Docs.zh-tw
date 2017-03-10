---
title: "RemoveHandler Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.RemoveHandlerMethod"
  - "vb.RemoveHandler"
  - "RemoveHandler"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "RemoveHandler keyword"
  - "RemoveHandler statement"
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# RemoveHandler Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

移除事件與事件處理常式之間的關聯。  
  
## 語法  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`event`|正在處理的事件名稱。|  
|`eventhandler`|目前正在處理事件的程序名稱。|  
  
## 備註  
 `AddHandler` 和 `RemoveHandler` 陳述式允許您在程式執行的任何時間內啟動和停止特定事的事件處理。  
  
> [!NOTE]
>  使用自訂事件時，`RemoveHandler` 陳述式會叫用事件的 `RemoveHandler` 存取子。  如需自訂事件的詳細資訊，請參閱[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## 範例  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#17)]  
  
## 請參閱  
 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)