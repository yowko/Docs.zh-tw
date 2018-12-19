---
title: '*= 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: f8604cdadeda14a5761bc923bd966186fd258a6d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245346"
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

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
