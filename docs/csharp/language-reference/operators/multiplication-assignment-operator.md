---
title: '*= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 465cf37d38a989d5c1bf6f0d0242c295e55684f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>*= 運算子 (C# 參考)
二進位乘法指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `*=` 指派運算子的運算式，例如  
  
```  
x *= y  
```  
  
 相當於  
  
```  
x = x * y  
```  
  
 但只會評估 `x` 一次。 對於對要執行乘法的數值類型，已預先定義 [* 運算子](../../../csharp/language-reference/operators/multiplication-operator.md)。  
  
 無法直接多載 `*=` 運算子，但使用者定義型別可以多載 [* 運算子](../../../csharp/language-reference/operators/multiplication-operator.md) (請參閱[運算子](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
