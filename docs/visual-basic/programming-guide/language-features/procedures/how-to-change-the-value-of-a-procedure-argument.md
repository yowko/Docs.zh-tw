---
title: "How to: Change the Value of a Procedure Argument (Visual Basic) | Microsoft Docs"
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
  - "arguments [Visual Basic], ByRef"
  - "arguments [Visual Basic], changing value"
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Change the Value of a Procedure Argument (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

在呼叫程序時，您提供的每個引數都會對應到程序中所定義的其中一個參數。  在某些情況下，程序程式碼可在呼叫程式碼中變更引數所對應的值。  在其他情況下，程序只可變更引數的本機複本。  
  
 呼叫程序時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會產生以 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 方式傳遞之每個引數的本機複本。  對於每個以 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 方式傳遞的引數，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會在呼叫程式碼中將引數對應的程式設計項目的直接參考提供給程序程式碼。  
  
 如果呼叫程式碼中的對應項目是可修改的項目，且引數是以 `ByRef` 方式傳遞，則程序程式碼可使用直接參考來變更呼叫程式碼中的項目值。  
  
## 變更對應值  
  
#### 若要變更呼叫程式碼中程序引數的對應值  
  
1.  在程序宣告中，針對與引數對應的參數指定 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  
  
2.  在呼叫程式碼中，將可修改的程式設計項目做為引數傳遞。  
  
3.  在呼叫程式碼中，不要在引數清單中將引數封入括號中。  
  
4.  在程序程式碼中，使用參數名稱來指派呼叫程式碼中對應項目的值。  
  
 請參閱以下範例中的說明。  
  
## 變更本機複本  
 如果呼叫程式碼中的對應項目是不可修改的項目，或如果引數是以 `ByVal` 方式傳遞，則程序無法變更它在呼叫程式碼中的值。  不過，程序可變更這類引數的本機複本。  
  
#### 若要變更程序程式碼中程序引數的複本  
  
1.  在程序宣告中，針對與引數對應的參數指定 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。  
  
     \-或\-  
  
     在呼叫程式碼中，在引數清單中將引數封入括號中。  這會強制 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 以傳值 \(By Value\) 方式傳遞引數，即使對應的參數指定 `ByRef` 也一樣。  
  
2.  在程序程式碼中，使用參數名稱來指派引數本機複本的值。  呼叫程式碼中的對應值不會變更。  
  
## 範例  
 下列範例會顯示兩個取得陣列變數，並在其元素上作業的程序。  `increase` 程序只會將每個元素加一。  `replace` 程序會將新陣列指派給參數 `a()`，然後每個元素都加一。  
  
 [!code-vb[VbVbcnProcedures#35](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-change-the-value-_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-change-the-value-_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-change-the-value-_3.vb)]  
  
 第一個 `MsgBox` 呼叫顯示 "After increase\(n\): 11, 21, 31, 41"。  因為陣列  `n`  是參考型別，所以  `replace`  可變更其成員，即使傳遞機制是 `ByVal` 也一樣。  
  
 第二個 `MsgBox` 呼叫顯示 "After replace\(n\): 101, 201, 301"。  因為 `n` 是以 `ByRef` 方式傳遞，所以 `replace`  可修改呼叫程式碼中的變數  `n` ，並指派新陣列給它。  因為  `n`  是參考型別，所以  `replace`  也可變更其成員。  
  
 您可防止程序在呼叫程式碼中修改變數本身。  請參閱 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)。  
  
## 編譯程式碼  
 當您以傳址方式來傳遞變數時，您必須用 `ByRef` 關鍵字指定這個機制。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的預設值是以值來傳遞引數。  但是，在每一個宣告的參數中包括 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 或 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 關鍵字是很好的程式設計方式。  這樣會讓您的程式碼更容易閱讀。  
  
## .NET Framework 安全性  
 允許程序在呼叫程式碼中變更引數對應的值，一定會有潛在風險。  請確定您預期會變更這個值，並在使用它之前，準備好檢查它的有效性。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)