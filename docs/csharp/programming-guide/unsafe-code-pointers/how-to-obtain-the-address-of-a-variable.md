---
title: "如何：取得變數位址 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "指標運算式 [C#], 傳址運算子"
  - "指標 [C#], & 運算子"
  - "變數 [C#], 傳址"
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 如何：取得變數位址 (C# 程式設計手冊)
若要取得評估為固定變數的一元 \(Unary\) 運算式位址，請使用傳址運算子：  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 傳址運算子只能套用至變數；  如果該變數是可移動的變數，您可以使用 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)，在取得其位址之前暫時固定該變數。  
  
 必須確定變數已初始化。  如果變數未初始化，則編譯器不會發出錯誤訊息。  
  
 就無法取得常數或值的位址。  
  
## 範例  
 在這個範例中，會宣告 `int` 的指標 `p`，並將指標設定為整數變數 `number` 的位址。  由於指派為 \*p，變數 `number` 便會予以初始化。  若在這個指派陳述式加上註解，將會移除變數 `number` 的初始化，但不會發出編譯時期錯誤。  請注意，這裡使用了[成員存取](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)運算子 `->`，來取得並顯示儲存在指標的位址。  
  
 [!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)