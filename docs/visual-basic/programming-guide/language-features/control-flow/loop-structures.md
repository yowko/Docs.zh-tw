---
title: "Loop Structures (Visual Basic) | Microsoft Docs"
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
  - "control flow, loops"
  - "For keyword [Visual Basic], loop structures"
  - "loops"
  - "loop structures"
  - "statements [Visual Basic], loop"
  - "Do statement, Do loops"
  - "conditional statements, loop structures"
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Loop Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 迴圈結構可以讓您重複執行一或多行程式碼。  您可以重複迴圈結構中的陳述式，直到條件為 `True`、條件為 `False`、達到特定的次數，或是集合中的每個項目都執行過一次。  
  
 下圖將示範一個迴圈結構，此結構會執行一組陳述式直到條件成為 true 為止。  
  
 ![Do...Until 迴圈流程圖](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")  
執行一組陳述式直到條件成為 true 為止  
  
## While 迴圈  
 只要在 `While` 陳述式中指定的條件為 `True`，`While`...`End While` 結構就會執行一組陳述式。  如需詳細資訊，請參閱 [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)。  
  
## Do 迴圈  
 `Do`...`Loop` 結構允許您在迴圈結構開始或結束時測試條件。  您也可以指定條件是要保持 `True` 或直到條件變成 `True` 時，才重複迴圈。  如需詳細資訊，請參閱 [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## For 迴圈  
 `For`...`Next` 結構可以執行迴圈數次。  這種結構使用迴圈控制變數 \(也稱為「*計數器*」\(Counter\)\) 來控制重複的次數。  您可以指定這個計數器的開始值和結束值，並且可以選擇性指定重複時所增加的數值。  如需詳細資訊，請參閱 [For...Next 陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)。  
  
## For Each 迴圈  
 `For Each`...`Next` 結構會為集合中的每個項目執行一組陳述式，每個項目都執行一次。  您可以指定迴圈控制項變數，但不必決定其開始值或結束值。  如需詳細資訊，請參閱 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
## 請參閱  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)