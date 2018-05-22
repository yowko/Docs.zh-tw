---
title: /= 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: c31ff374e6af4c08c329a971fdd8af169e239395
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>/= 運算子 (C# 參考)
除法指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `/=` 指派運算子的運算式，例如  
  
```csharp  
x /= y  
```  
  
 相當於  
  
```csharp  
x = x / y  
```  
  
 但只會評估 `x` 一次。 會針對要執行除法的數值類型，預先定義 [/ 運算子](../../../csharp/language-reference/operators/division-operator.md)。  
  
 無法直接多載 `/=` 運算子，但使用者定義型別可以多載 [/ 運算子](../../../csharp/language-reference/operators/division-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 在所有複合指派運算子上，多載二元運算子會隱含地多載對等的複合指派。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
