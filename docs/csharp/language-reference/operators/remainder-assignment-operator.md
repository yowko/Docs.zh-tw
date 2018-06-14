---
title: '%= 運算子 (C# 參考)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: aadcb5ef969ff408cc1e738fc0f5b67152fdc78b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171963"
---
# <a name="-operator-c-reference"></a>%= 運算子 (C# 參考)
餘數指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `%=` 指派運算子的運算式，例如  
  
```csharp  
x %= y  
```  
  
 相當於  
  
```csharp  
x = x % y  
```  
  
 但只會評估 `x` 一次。 對於要計算除法運算後餘數的數值類型，已預先定義 [/ 運算子](../../../csharp/language-reference/operators/remainder-operator.md)。  
  
 無法直接多載 `%=` 運算子，但使用者定義型別可以多載 [% 運算子](../../../csharp/language-reference/operators/remainder-operator.md) (請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
