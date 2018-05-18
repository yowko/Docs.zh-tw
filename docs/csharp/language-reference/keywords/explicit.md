---
title: explicit (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: c8a05aef3318eb34242ed1268ea26663592e4d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="explicit-c-reference"></a>explicit (C# 參考)
`explicit` 關鍵字會宣告必須使用轉換叫用的使用者定義型別轉換運算子。 例如，此運算子會將稱為華氏的類別轉換成稱為攝氏的類別︰  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 此轉換運算子可以這樣叫用︰  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 轉換運算子會將來源類型轉換成目標型別。 來源類型提供轉換運算子。 不同於隱含轉換，明確轉換運算子必須透過轉換來叫用。 如果轉換作業會造成例外狀況或遺失資訊，您應將其標記為 `explicit`。 如此可避免編譯器以無訊息方式叫用轉換作業，發生難以預料的後果。  
  
 省略轉換會導致編譯時期錯誤 CS0266。  
  
 如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。  
  
## <a name="example"></a>範例  
 下例提供 `Fahrenheit` 和 `Celsius` 類別，它們互相提供明確轉換運算子。  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>範例  
 下例定義 `Digit` 結構，表示單一十進位數字。 已定義將 `byte` 轉換成 `Digit` 的運算子，但是因為並非所有位元組都可轉換成 `Digit`，所以是明確轉換。  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)  
 [如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [C# 中鏈結的使用者定義明確轉換](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
