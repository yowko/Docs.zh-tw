---
title: "Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32053"
  - "vbc32053"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32053"
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

呼叫程序時會使用擴展至對應參數型別的引數，而進行從參數到引數的轉換時，則會進行縮小轉換。  
  
 當您定義類別或結構時，可以定義一或多個將該類別或結構型別轉換為其他型別的轉換運算子。  也可以定義反向的轉換運算子，將其他型別轉換回您的類別或結構型別。  當您在程序呼叫中使用類別或結構型別時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會使用這些轉換運算子，將引數的型別轉換為對應參數的型別。  
  
 如果您傳遞引數 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 有時會將引數值複製到程序中的區域變數，而不是傳遞參考。  在這種狀況下，當程序傳回時，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 必須接著將區域變數值複製回呼叫程式碼中的引數。  
  
 如果 `ByRef` 引數值已複製到程序，並且引數和參數屬於相同型別，便不需要轉換。  但是，如果型別不同，則 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 必須以兩個方向轉換。  如果其中一個型別是您的類別或結構型別，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 即需在它與另一個型別之間來回轉換。  如果其中一個轉換是擴展轉換，反向轉換便是縮小轉換。  
  
 **錯誤 ID：**BC32053  
  
### 若要更正這個錯誤  
  
-   請盡可能使用與程序參數相同型別的呼叫引數，這樣 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 便不需要執行任何轉換。  
  
-   如果您需要以不同於參數型別的引數型別呼叫程序，但不需要傳回值至此呼叫引數，則參數必須定義為 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) 而不是 `ByRef`。  
  
-   如果您需要將值傳回呼叫的引數，請盡可能將反向的轉換運算子定義為 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)。  
  
## 請參閱  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)