---
title: "使用 ref 和 out 傳遞陣列 (C# 程式設計手冊) | Microsoft Docs"
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
  - "陣列 [C#], 使用 ref 和 out 傳遞"
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 使用 ref 和 out 傳遞陣列 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

如同所有的 [out](../../../csharp/language-reference/keywords/out.md) 參數，陣列類型的 `out` 參數必須先指派才能使用，也就是說，被呼叫端必須先指派這個參數。  例如：  
  
 [!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 如同所有的 [ref](../../../csharp/language-reference/keywords/ref.md) 參數，陣列類型的 `ref` 參數也必須由呼叫端明確指派。  因此，被呼叫端就不需要明確指派該參數。  呼叫的結果可能會修改陣列類型的 `ref` 參數。  例如，陣列可以擁有指派的 [null](../../../csharp/language-reference/keywords/null.md) 值，或是初始化為不同的陣列。  例如：  
  
 [!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 下列兩個範例將示範在陣列傳遞至方法時使用 `out` 和 `ref` 之間的差異。  
  
## 範例  
 在這個範例中，`theArray` 陣列是在呼叫端 \(`Main` 方法\) 宣告，並且在 `FillArray` 方法中進行初始化。  接著陣列元素會傳回呼叫端並顯示。  
  
 [!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## 範例  
 在這個範例中，`theArray` 陣列是在呼叫端 \(`Main` 方法\) 進行初始化，並且會使用 `ref` 參數將該陣列傳遞至 `FillArray` 方法。  有些陣列元素會在 `FillArray` 方法中更新。  接著陣列元素會傳回呼叫端並顯示。  
  
 [!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## 請參閱  
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [out 參數修飾詞](../../../csharp/language-reference/keywords/out-parameter-modifier.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)