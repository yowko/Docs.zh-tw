---
title: "指標的算術運算 (C# 程式設計手冊) | Microsoft Docs"
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
  - "指標 [C#], 數學運算"
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 指標的算術運算 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

本主題將討論如何使用算術運算子 `+` 和 **\-** 來操作指標。  
  
> [!NOTE]
>  您無法在 void 指標上執行任何算術運算。  
  
## 指標如何加減數值  
 您可將 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) 等型別的 `n` 值加入至任何型別 `` \(除了 `void*` 以外\) 的指標 `p`。  結果 `p+n` 是加上 `n * sizeof(p) to the address of p` 所得出的指標。  同樣地，`p-n` 是從 `p` 的位址減去 `n * sizeof(p)` 得出的指標。  
  
## 減去指標  
 您也可以減去相同型別的指標。  所得結果的型別一定會是 `long`。  例如，如果 `p1` 和 `p2` 是 `pointer-type*` 型別的指標，則運算式 `p1-p2` 得出的結果為：  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 當算術運算造成指標的定義域溢位時，不會產生任何例外狀況，而且結果會視實作情況而定。  
  
## 範例  
 [!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)   
 [指標操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)