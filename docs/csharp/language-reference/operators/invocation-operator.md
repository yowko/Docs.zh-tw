---
title: () 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 29097dc4aa0bf712b9b2beda4450820a66472ba7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44179665"
---
# <a name="-operator-c-reference"></a>() 運算子 (C# 參考)
除了用來指定運算式中運算的順序，括號也可用來執行下列工作：  
  
1.  指定轉換或型別轉換。  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  叫用方法或委派。  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>備註  
 轉換會明確叫用轉換運算子，將某個類型轉換為另一個類型；若沒有定義這類轉換運算子，轉換就會失敗。 若要定義轉換運算子，請參閱 [explicit](../../../csharp/language-reference/keywords/explicit.md) 和 [implicit](../../../csharp/language-reference/keywords/implicit.md)。  
  
 無法多載 `()` 運算子。  
  
 如需詳細資訊，請參閱[轉型和型別轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。  
  
 如需方法引動過程的詳細資訊，請參閱[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
