---
title: '*= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 6bbf2142ca7e9e05010a29920da52e1439f6e882
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>*= 運算子 (C# 參考)
二進位乘法指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `*=` 指派運算子的運算式，例如  
  
```csharp  
x *= y  
```  
  
 相當於  
  
```csharp  
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
