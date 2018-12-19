---
title: '&lt;&lt;= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: f49c6360d6fee3f6d612aee51446545f25cd7d18
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239169"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= 運算子 (C# 參考)
左移指派運算子。  
  
## <a name="remarks"></a>備註  
 以下格式的運算式  
  
```csharp  
x <<= y  
```  
  
 評估為  
  
```csharp  
x = x << y  
```  
  
 但只會評估 `x` 一次。 [<< 運算子](../../../csharp/language-reference/operators/left-shift-operator.md)會將 `x` 左移 `y` 所指定的位元數。  
  
 無法直接多載 `<<=` 運算子，但使用者定義型別可以多載 [<< 運算子](../../../csharp/language-reference/operators/left-shift-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
