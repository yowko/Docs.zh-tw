---
title: "如何：遞增和遞減指標 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "指標運算式 [C#], 遞增和遞減"
  - "指標 [C#], 遞增和遞減"
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：遞增和遞減指標 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

使用遞增和遞減運算子 \(`++` 和 `--`\)，可以藉由 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) \(`pointer-type`\) 變更指標型別 \* 指標的位置。  遞增和遞減運算式的格式如下：  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 遞增和遞減運算子可以套用於型別 `void*` 以外任何型別的指標。  
  
 將遞增運算子套用至 `pointer-type` 型別指標時，會將 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) \(`pointer-type`\) 加入包含在指標變數中的位址。  
  
 將遞減運算子套用至 `pointer-type` 型別指標時，則會將 `sizeof` \(`pointer-type`\) 從指標變數包含的位址中減去。  
  
 當作業造成指標定義域溢位時，不會產生例外狀況，而且結果會視實作情況而定。  
  
## 範例  
 在這個範例中，您會依 `int` 的大小遞增指標，以逐步執行陣列。  陣列元素的位址和內容會隨著每個步驟顯示。  
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
  **Value:0 @ Address:12860272**  
**Value:1 @ Address:12860276**  
**Value:2 @ Address:12860280**  
**Value:3 @ Address:12860284**  
**Value:4 @ Address:12860288**   
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)   
 [指標操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)