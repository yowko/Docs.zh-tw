---
title: implicit (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a>implicit (C# 參考)
`implicit` 關鍵字是用來宣告隱含的使用者定義型別轉換運算子。 使用它可啟用使用者定義型別和其他型別之間的隱含轉換，但前提是要保證轉換作業不會導致資料的遺失。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 隱含轉換藉由消除不必要的轉換，來改善原始程式碼的可讀性。 不過，由於隱含轉換不需要程式設計人員將某個類型明確轉換為另一個類型，因此必須謹慎使用，以避免產生非預期的結果。 一般而言，隱含轉換運算子絕對不會擲回例外狀況，也絕對不會遺失資訊，因此即使程式設計人員沒有注意也可以安全地使用。 如果轉換運算子無法符合這些準則，則應該將其標記為 `explicit`。 如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)  
 [如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
