---
title: "true 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "true 運算子 [C#]"
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# true 運算子 (C# 參考)
若運算元為 true 則傳回 [bool](../../../csharp/language-reference/keywords/bool.md) 值 `true`，否則傳回 `false`。  
  
 在 C\# 2.0 之前，`true` 和 `false` 運算子是用來建立使用者定義之可為 Null 的型別，這些型別都與如 `SqlBool` 此類型別相容。  不過，該語言現在已針對可為 Null 的型別提供內建支援，您應盡量使用這些型別，而不是多載 `true` 和 `false` 運算子。  如需詳細資訊，請參閱 [可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)。  
  
 使用可為 Null 的布林值時，運算式 `a != b` 不一定等於 `!(a == b)`，因為其中一個或兩者的值可能為 null。  您必須分別多載 `true` 和 `false` 運算子，以正確識別運算式中的 null 值。  在下列範例中，會說明如何多載及使用 `true` 和 `false` 運算子。  
  
 [!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsOperator/csrefKeywordsOperators.cs#16)]  
  
 多載 `true` 和 `false` 運算子的型別可用於控制 [if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md) 和 [for](../../../csharp/language-reference/keywords/for.md) 陳述式中的運算式與[條件運算式](../../../csharp/language-reference/operators/conditional-operator.md)中的運算式。  
  
 如果型別定義了 `true` 運算子，就必須同時定義 [false](../../../csharp/language-reference/keywords/false.md) 運算子。  
  
 型別不能直接多載條件邏輯運算子 \([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 和 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)\)，但是藉由多載標準邏輯運算子與 `true` 和 `false` 兩個運算子，也可達到同等的效果。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)   
 [false](../../../csharp/language-reference/keywords/false.md)