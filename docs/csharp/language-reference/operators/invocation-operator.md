---
title: "() 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "()_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "() 運算子 [C#]"
  - "轉型運算子 [C#]"
  - "類型轉換 [C#], () 運算子"
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# () 運算子 (C# 參考)
除了用來指定運算式中運算的順序，括號也可用來執行下列工作：  
  
1.  指定轉型 \(cast\) 或型別轉換。  
  
     [!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#1)]  
  
2.  叫用方法或委派。  
  
     [!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#2)]  
  
## 備註  
 轉型會明確叫用轉換運算子，將一個型別轉換為其他型別；若沒有定義這類的轉換運算子，轉型就會失敗。  若要定義轉換運算子，請參閱 [explicit](../../../csharp/language-reference/keywords/explicit.md) 和 [implicit](../../../csharp/language-reference/keywords/implicit.md)。  
  
 `()` 運算子無法多載。  
  
 如需詳細資訊，請參閱 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。  
  
 cast 運算式可能會造成模稜兩可的語法。  例如，`(x)–y` 運算式可以解譯成 cast 運算式 \(由 –y 至 x 型別的轉型\)，或是被當做結合了括號運算式的加法運算式 \(該括號運算式會計算 x – y 的值\)。  
  
 如需方法叫用的詳細資訊，請參閱[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)