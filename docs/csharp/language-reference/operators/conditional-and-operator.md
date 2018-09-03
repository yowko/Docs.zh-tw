---
title: '&amp;&amp; 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388289"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; 運算子 (C# 參考)
條件式 AND 運算子 (`&&`) 會執行其 `bool` 運算元的邏輯 AND，但只有在必要時才會評估其第二個運算元。  
  
## <a name="remarks"></a>備註  
 作業  
  
```csharp  
x && y  
```  
  
 對應至作業  
  
```csharp  
x & y  
```  
  
 差異在於，如果 `x` 是 `false`，則不會評估 `y`因為不論 `y` 的值為何，AND 運算的結果都是 `false`。 這稱為「最少運算」求值。  
  
 無法多載條件式 AND 運算子，但規則邏輯運算子 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 的多載會具有某些限制，也會視為條件式邏輯運算子的多載。  
  
## <a name="example"></a>範例  
 在下列範例中，第二個 `if` 陳述式中的條件式運算式只會評估第一個運算元，因為運算元會傳回 `false`。  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
