---
title: "&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32022"
  - "vbc32022"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32022"
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

'\<`eventname`\>' 是個事件，因此不可直接呼叫。  請使用 `RaiseEvent` 陳述式引發事件。  
  
 程序呼叫指定了程序名稱的事件。  事件處理常式是一個程序，但是事件本身則是必須引發和處理的信號裝置。  
  
 **錯誤 ID**︰BC32022  
  
### 若要更正這個錯誤  
  
1.  請使用 `RaiseEvent` 陳述式向事件發出信號，並叫用 \(Invoke\) 處理事件的程序。  
  
## 請參閱  
 [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)