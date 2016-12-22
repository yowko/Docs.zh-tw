---
title: "指標轉換 (C# 程式設計手冊) | Microsoft Docs"
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
  - "指標 [C#], 轉換"
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 指標轉換 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下表顯示預先定義的隱含指標轉換。  隱含轉換可能發生在許多狀況，包括方法叫用和指派陳述式。  
  
## 隱含指標轉換  
  
|From|若要|  
|----------|--------|  
|任何指標型別|void\*|  
|null|任何指標型別|  
  
 明確指標轉換是指當沒有隱含轉換時，使用 cast 運算式來執行轉換。  下表顯示這些轉換。  
  
## 明確指標轉換  
  
|From|若要|  
|----------|--------|  
|任何指標型別|其他任何指標型別|  
|sbyte、byte、short、ushort、int、uint、long 或 ulong|任何指標型別|  
|任何指標型別|sbyte、byte、short、ushort、int、uint、long 或 ulong|  
  
## 範例  
 在下列程式碼中，`int` 的指標會轉換成 `byte` 的指標。  請注意，指標會指向變數的最低定址位元組。  當您連續遞增結果時，最大會到 `int` 的大小 \(4 個位元組\)，而您可以顯示變數的剩餘位元組。  
  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-cs[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)