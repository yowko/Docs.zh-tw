---
title: "Other Control Structures (Visual Basic) | Microsoft Docs"
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
  - "statements [Visual Basic], control flow"
  - "control structures"
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Other Control Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供控制結構，這個控制結構會協助您處置 \(Dispose\) 資源或減少需要的重複物件參考次數。  
  
## Using...End Using 建構函式  
 `Using...End Using` 建構函式會建立可在其內使用資源 \(例如 SQL 連接\) 的陳述式 \(Statement\) 區塊。  可選擇性地使用 `Using` 陳述式取得資源。  結束 `Using` 區塊時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會自動處置資源，這樣其他程式碼就可使用這個資源。  資源必須是本機的，且是可處置的。  如需詳細資訊，請參閱 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## With...End With 建構函式  
 `With...End With` 語法建構可讓您指定一次物件參考，然後執行一連串用來存取其成員的陳述式。  因為 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 不必重新建立每個存取它之陳述式的參考，所以這可簡化程式碼並改善效能。  如需詳細資訊，請參閱 [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。  
  
## 請參閱  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)   
 [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)