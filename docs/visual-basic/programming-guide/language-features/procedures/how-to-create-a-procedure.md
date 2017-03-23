---
title: "How to: Create a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "Visual Basic code, reusing"
  - "procedure declarations"
  - "procedures, about procedures"
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# How to: Create a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

封入開始宣告陳述式 \(`Sub` 或 `Function`\) 與結束宣告陳述式 \(`End Sub` 或 `End Function`\) 之間的程序。  所有程序的程式碼都位於這些陳述式之間。  
  
 程序不可包含另一個程序，因此它的開始和結束陳述式都必須在任何其他程序之外。  
  
 如果您的程式碼會在不同位置執行相同工作，則只要將工作撰寫成程序一次，然後就可在程式碼的不同位置呼叫它。  
  
### 若要建立不傳回值的程序  
  
1.  在任何其他程序之外，使用後面緊接 `End Sub` 陳述式的 `Sub` 陳述式。  
  
2.  在 `Sub` 陳述式中，請在 `Sub` 關鍵字後面緊接著程序名稱，然後是以括號括住的參數清單。  
  
3.  將程序的程式碼陳述式放在 `Sub` 與 `End Sub` 陳述式之間。  
  
### 若要建立傳回值的程序  
  
1.  在任何其他程序之外，使用後面緊接 `End Function` 陳述式 \(Statement\) 的 `Function` 陳述式。  
  
2.  在 `Function` 陳述式中，請在 `Function` 關鍵字後面依序緊接著程序名稱、以括號括住的參數清單，然後是指定傳回值之資料型別的 `As` 子句。  
  
3.  將程序的程式碼陳述式放在 `Function` 與 `End Function` 陳述式之間。  
  
4.  使用 `Return` 陳述式，將值傳回給呼叫程式碼。  
  
### 若要連接新程序與程式碼的舊重複區塊  
  
1.  確定在舊程式碼可存取的位置定義新程序。  
  
2.  在舊的重複程式碼區塊中，請將執行重複工作的陳述式替換為呼叫 `Sub` 或 `Function` 程序的單一陳述式。  
  
3.  如果程序是傳回值的 `Function`，請確定呼叫陳述式是以傳回的值來執行動作 \(例如將它儲存在變數中\)，否則該值會遺失。  
  
## 範例  
 下列 `Function` 程序會在已知其他兩邊值的情況下，計算直角三角形的最長邊 \(也稱為斜邊\)。  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [物件導向程式設計](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)