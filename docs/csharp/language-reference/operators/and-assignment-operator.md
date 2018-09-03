---
title: '&amp;= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406731"
---
# <a name="amp-operator-c-reference"></a>&amp;= 運算子 (C# 參考)
AND 指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `&=` 指派運算子的運算式，例如  
  
```csharp  
x &= y  
```  
  
 相當於  
  
```csharp  
x = x & y  
```  
  
 但只會評估 `x` 一次。 [& 運算子](../../../csharp/language-reference/operators/and-operator.md)在整數運算元上執行位元邏輯 AND 運算，在 `bool` 運算元上執行邏輯 AND。  
  
 無法直接多載 `&=` 運算子，但使用者定義型別可以多載二進位 [& 運算子](../../../csharp/language-reference/operators/and-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
