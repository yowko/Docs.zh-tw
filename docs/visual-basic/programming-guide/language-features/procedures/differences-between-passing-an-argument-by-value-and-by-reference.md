---
title: "Differences Between Passing an Argument By Value and By Reference (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ByRef keyword, passing arguments by reference"
  - "Visual Basic code, procedures"
  - "procedures, passing arguments"
  - "ByVal keyword, passing arguments by value"
  - "arguments [Visual Basic], passing by value or by reference"
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Passing an Argument By Value and By Reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

將一或多個引數傳遞至程序時，每個引數都對應至呼叫程式碼中的相對程式設計項目。  您可傳遞這個對應項目的值或它的參考，  這就是所謂的「*傳遞機制*」\(Passing Mechanism\)。  
  
## 以傳值方式傳遞  
 在程序定義中指定對應參數的 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 關鍵字，即可以「*傳值方式*」\(By Value\) 傳遞引數。  使用這個傳遞機制時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會將對應程式設計項目的值複製到程序中的區域變數，  程序程式碼不會有對應項目的任何存取權。  
  
## 以傳址方式傳遞  
 在程序定義中指定對應參數的 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) 關鍵字，即可以「*傳址方式*」\(By Reference\) 傳遞引數。  使用這個傳遞機制時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會在呼叫程式碼中將對應程式設計項目的直接參考提供給程序。  
  
## 傳遞機制和項目型別  
 傳遞機制的選擇與對應項目型別的分類不同，  以傳值或傳址方式傳遞是指 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 提供給程序程式碼的內容。  實值型別 \(Value Type\) 或參考型別 \(Reference Type\) 指的是如何將程式設計項目儲存在記憶體中。  
  
 然而，傳遞機制與項目型別相互關連。  參考型別的值是記憶體中其他位置的資料指標，  這表示以傳值方式傳遞參考型別時，程序程式碼會有對應項目資料的指標，即使它無法存取對應項目本身。  例如，如果項目是陣列變數，則程序程式碼不會有變數本身的存取權，但它可存取陣列成員。  
  
## 修改的能力  
 當您將不可修改的項目當做引數傳遞時，無論此項目是以 `ByVal` 或 `ByRef` 方式傳遞，程序都不可以在呼叫程式碼中進行修改。  
  
 對於可修改的項目而言，下表彙總項目型別和傳遞機制之間的互動：  
  
|項目型別|透過 `ByVal` 傳遞|透過 `ByRef` 傳遞|  
|----------|-------------------|-------------------|  
|實值型別 \(只包含一個值\)|程序無法變更變數或其任何成員|程序可以變更變數或成員|  
|參考型別 \(包含指向類別或結構執行個體的指標\)|程序無法變更變數，但可以變更它所指向的執行個體之成員|程序可以變更變數和它所指向的執行個體之成員|  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../Topic/How%20to:%20Pass%20Arguments%20to%20a%20Procedure%20\(Visual%20Basic\).md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Differences Between Modifiable and Nonmodifiable Arguments](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [How to: Change the Value of a Procedure Argument](../../../../visual-basic/programming-guide/language-features/procedures/how-to-change-the-value-of-a-procedure-argument.md)   
 [How to: Protect a Procedure Argument Against Value Changes](../../../../visual-basic/programming-guide/language-features/procedures/how-to-protect-a-procedure-argument-against-value-changes.md)   
 [How to: Force an Argument to Be Passed by Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)