---
title: "How to: Protect a Procedure Argument Against Value Changes (Visual Basic) | Microsoft Docs"
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
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "arguments [Visual Basic], passing by reference"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], ByVal"
  - "arguments [Visual Basic], passing by value"
  - "procedure parameters"
  - "procedures, calling"
  - "arguments [Visual Basic], ByRef"
  - "arguments [Visual Basic], changing value"
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Protect a Procedure Argument Against Value Changes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

如果程序將參數宣告成 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 就能讓程序程式碼直接參考程式設計項目 \(呼叫程式碼中的基礎引數\)。  這能讓程序變更呼叫程式碼中引數的基礎值。  在某些情況下，呼叫程式碼可能想防止這類變更。  
  
 您永遠都可以在程序中宣告對應參數 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 來防止變更引數。  如果想要在某些情況下變更指定的引數，其他情況下防止變更，則可將它宣告為 `ByRef`，並讓呼叫程式碼決定每一個呼叫的傳遞機制。  它會將對應引數以括號括住，依值來傳遞它，或不以括號括住，依參考來傳遞它，以完成這個動作。  如需詳細資訊，請參閱 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)。  
  
## 範例  
 下列範例會顯示兩個取得陣列變數，並在其元素上作業的程序。  `increase` 程序只會將每個元素加一。  `replace` 程序會將新陣列指派給參數 `a()`，然後每個元素都加一。  但是，重新指派並不會影響呼叫程式碼中的陣列變數。  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-protect-a-procedu_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-protect-a-procedu_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-protect-a-procedu_3.vb)]  
  
 第一個 `MsgBox` 呼叫顯示 "After increase\(n\): 11, 21, 31, 41"。  因為陣列  `n`  是參考型別，所以  `replace`  可變更其成員，即使傳遞機制是 `ByVal` 也一樣。  
  
 第二個 `MsgBox` 呼叫顯示 "After replace\(n\): 11, 21, 31, 41"。  由於  `n`  傳遞 `ByVal`，所以  `replace`  無法藉由將新陣列指派給呼叫程式碼中的變數  `n`  來修改該變數。  當  `replace`  建立新陣列執行個體  `k` ，並且將它指派給區域變數  `a` 時，會遺失呼叫程式碼所傳入之  `n`  的參考。  當它變更  `a` 的成員時，只會影響區域陣列  `k` 。  因此， `replace`  不會增加呼叫程式碼中陣列  `n`  的值。  
  
## 編譯程式碼  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的預設值是以值來傳遞引數。  但是，在每一個宣告的參數中包括 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 或 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 關鍵字是很好的程式設計方式。  這樣會讓您的程式碼更容易閱讀。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)