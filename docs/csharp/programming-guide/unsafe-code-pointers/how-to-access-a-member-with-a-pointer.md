---
title: "如何：使用指標存取成員 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "指標 [C#], 成員存取"
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 如何：使用指標存取成員 (C# 程式設計手冊)
若要存取在 unsafe 內容中宣告的結構 \(Struct\) 成員，您可以使用成員存取運算子 \(Member Access Operator\)，如下列範例內的 `p` 即是一個指向包含 `x` 成員之[結構](../../../csharp/language-reference/keywords/struct.md)的指標。  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## 範例  
 在這個範例中，會宣告包含兩個座標 `x` 和 `y` 的[結構](../../../csharp/language-reference/keywords/struct.md) \(`CoOrds`\)，並加以具現化 \(Instantiated\)。  藉由使用成員存取運算子 `->` 和 `home` 執行個體指標，可以為 `x` 和 `y` 指定值。  
  
> [!NOTE]
>  請注意，運算式 `p->x` 相當於運算式 `(*p).x`，而且使用其中任何一個運算式都會得到相同的結果。  
  
 [!code-cs[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers2.cs#9)]  
  
 [!code-cs[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers.cs#10)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)