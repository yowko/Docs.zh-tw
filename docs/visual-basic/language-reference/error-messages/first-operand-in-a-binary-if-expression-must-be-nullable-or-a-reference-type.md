---
title: "First operand in a binary &#39;If&#39; expression must be nullable or a reference type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc33107"
  - "vbc33107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC33107"
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# First operand in a binary &#39;If&#39; expression must be nullable or a reference type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`If` 運算式可接受兩個或三個參數。  當您只傳送兩個引數時，第一個引數必須是參考型別或可為 Null 的型別 \(Nullable Type\)。  如果第一個引數評估為 `Nothing` 以外的任何值，就會傳回其值。  如果第一個引數評估為 `Nothing`，會評估和傳回第二個引數。  
  
 例如，下列程式碼包含兩個 `If` 運算式，第一個運算式有三個引數，而第二個運算式有兩個引數。  這兩個運算式會計算並傳回相同的值。  
  
```vb#  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 下列運算式會造成此錯誤：  
  
```vb#  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **錯誤 ID：**BC33107  
  
### 若要更正這個錯誤  
  
-   如果您無法變更程式碼，使第一個引數成為可為 Null 的型別或參考型別，請考慮轉換為有三個引數的 `If` 運算式，或轉換為 `If...Then...Else` 陳述式。  
  
    ```vb#  
    Console.WriteLine(If(choice1 < choice2, 1, 2))  
    Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
    ```  
  
## 請參閱  
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)