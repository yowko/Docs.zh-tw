---
title: '&lt;&lt;= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: c689aeccdf3ad6cc6c672cc101a4f0aa92f19791
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43406970"
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
