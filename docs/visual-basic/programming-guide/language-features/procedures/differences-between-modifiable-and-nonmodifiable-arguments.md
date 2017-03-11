---
title: "Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic) | Microsoft Docs"
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
  - "procedure arguments"
  - "arguments [Visual Basic], nonmodifiable"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], modifiable"
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

呼叫程序時，一般會將一或多個引數傳遞給它。  每個引數都會對應到基礎程式設計項目，  基礎項目和引數本身都是可修改或不可修改的。  
  
## 可修改和不可修改的項目  
 程式設計項目可以是「*可修改的項目*」\(Modifiable Element\) \(可變更其值\) 或「*不可修改的項目*」\(Nonmodifiable Element\) \(建立後即有固定值\)。  
  
 下表列出了可修改和不可修改的程式設計項目。  
  
|可修改的項目|不可修改的項目|  
|------------|-------------|  
|區域變數 \(在程序內宣告\)，包含物件變數，但不包含唯讀項目|唯讀變數、欄位和屬性|  
|欄位 \(模組、類別和結構的成員變數\)，但不包含唯讀項目|常數和常值|  
|屬性，但不包含唯讀項目|列舉型別成員|  
|陣列元素|運算式 \(即使他們的項目是可修改的\)|  
  
## 可修改和不可修改的引數  
 「*可修改的引數*」\(Modifiable Argument\) 是具有可修改之基礎項目的引數。  呼叫程式碼可隨時儲存新值，而且，如果是以 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 方式傳遞引數，則程序中的程式碼也可以修改呼叫程式碼中的基礎項目。  
  
 「*不可修改的引數*」\(Nonmodifiable Argument\) 具有不可修改的基礎項目，或以 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 方式傳遞。  程序無法修改呼叫程式碼中的基礎項目，即使它是可修改的項目也一樣。  如果它是不可修改的項目，則呼叫程式碼本身便無法修改它。  
  
 呼叫的程序可以修正不可修改引數的本機複本，但是這樣的修正並不會影響呼叫程式碼中的基礎項目。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)