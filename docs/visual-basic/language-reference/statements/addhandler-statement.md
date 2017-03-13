---
title: "AddHandler Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AddHandlerMethod"
  - "addhandler"
  - "vb.addhandler"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddHandler statement"
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# AddHandler Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在執行階段使事件與事件處理常式產生關聯。  
  
## 語法  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## 組件  
 `event`  
 待處理的事件名稱。  
  
 `eventhandler`  
 處理事件的程序名稱。  
  
## 備註  
 `AddHandler` 和 `RemoveHandler` 陳述式允許您在程式執行的任何時間內啟動和停止事件處理。  
  
 `eventhandler` 程序的簽章必須符合事件 `event` 的簽章。  
  
 `Handles` 關鍵字和 `AddHandler` 陳述式都可供您指定特殊程序處理特殊事件，但兩者有所差異。  `AddHandler` 陳述式會在執行階段將程序連接至事件。  當定義程序以指定它處理特殊事件時，請使用 `Handles` 關鍵字。  如需詳細資訊，請參閱 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)。  
  
> [!NOTE]
>  使用自訂事件時，`AddHandler` 陳述式會叫用事件的 `AddHandler` 存取子。  如需自訂事件的詳細資訊，請參閱[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## 範例  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## 請參閱  
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)