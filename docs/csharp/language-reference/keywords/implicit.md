---
title: "implicit (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "implicit"
  - "implicit_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "implicit 關鍵字 [C#]"
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# implicit (C# 參考)
`implicit` 關鍵字是用來宣告隱含的使用者定義型別轉換運算子。  使用它可啟用使用者定義型別和其他型別之間的隱含轉換，但前提是要保證轉換作業不會導致資料的遺失。  
  
## 範例  
 [!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/csharp/implicit_1.cs)]  
  
 藉由消除不必要的轉換 \(Cast\)，隱含轉換 \(Conversion\) 可提高原始程式碼的可讀性。  不過，因為隱含轉換 \(Conversion\) 不需要程式設計人員明確轉換 \(Cast\) 其型別，因此必須謹慎使用，以避免產生非預期的結果。  一般說來，隱含轉換運算子應該不會擲回例外狀況 \(Exception\) 也不會遺失資訊，所以即使程式設計人員沒有注意也可以安全地使用。  若轉換運算子無法符合這些條件，應將其標記為 `explicit`。  如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)