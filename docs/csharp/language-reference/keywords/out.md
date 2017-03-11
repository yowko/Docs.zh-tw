---
title: "out (C# 參考) | Microsoft Docs"
ms.date: "2017-03-01"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "out_CSharpKeyword"
  - "out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "out [C#]"
  - "out 關鍵字 [C#]"
ms.assetid: 7e911a0c-3f98-4536-87be-d539b7536ca8
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# out (C# 參考)
您可以在兩個內容中 \(每個都是詳細資訊的連結\)，使用 `out` 內容關鍵字，做為[參數修飾詞](../../../csharp/language-reference/keywords/out-parameter-modifier.md)，或在介面和委派的[泛型類型參數宣告](../../../csharp/language-reference/keywords/out-generic-modifier.md)中，使用該關鍵字。  本主題探討參數修飾詞，但您可以查看[這個其他主題](../../../csharp/language-reference/keywords/out-generic-modifier.md)，以取得泛型類型參數宣告的相關資訊。  
  
 `out` 關鍵字會導致引數由參考傳遞。  這類似於 [ref](../../../csharp/language-reference/keywords/ref.md) 關鍵字，只是 `ref` 需要在傳遞之前，先初始化變數。  若要使用 `out` 參數，方法定義和呼叫方法都必須明確地使用 `out` 關鍵字。  例如：  
  
 [!code-cs[csrefKeywordsMethodParams#1](../../../csharp/language-reference/keywords/codesnippet/csharp/out_1.cs)]  
  
 雖然做為 `out` 引數傳遞的變數，不需要在傳遞之前先初始化，但需要被呼叫的方法，才能在方法傳回之前指派值。  
  
 雖然 `ref` 和 `out` 關鍵字會導致不同的執行階段行為，但在編譯階段，不會將其視為方法簽章的一部分。  因此，如果唯一的差別是一種方法採用 `ref` 引數，而另一種方法採用 `out` 引數，則不能多載方法。  例如，將不會編譯下列程式碼：  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/csharp/out_2.cs)]  
  
 不過，如果一種方法採用 `ref` 或 `out` 引數，而另一種方法都不採用，則可以完成多載，如下所示：  
  
 [!code-cs[csrefKeywordsMethodParams#3](../../../csharp/language-reference/keywords/codesnippet/csharp/out_3.cs)]  
  
 屬性不是變數，因此無法做為 `out` 參數傳遞。  
  
 如需傳遞陣列的詳細資訊，請參閱[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。  
  
 您不能將 `ref` 和 `out` 關鍵字用於下列幾種方法：  
  
-   使用 [async](../../../csharp/language-reference/keywords/async.md) 修飾詞定義的非同步方法。  
  
-   Iterator 方法，其包括 [yield return](../../../csharp/language-reference/keywords/yield.md) 或 `yield break` 陳述式。  
  
## 範例  
 當您想要方法傳回多個值時，宣告 `out` 方法很有用。  下列範例使用 `out`，在單一方法呼叫中，傳回三個變數。  請注意，第三個引數指派為 null。  這可讓方法能選擇性地傳回值。  
  
 [!code-cs[csrefKeywordsMethodParams#4](../../../csharp/language-reference/keywords/codesnippet/csharp/out_4.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)