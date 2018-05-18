---
title: '|= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: 2abfbcbabb4229049c97aa6827abef3a053d6992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>|= 運算子 (C# 參考)
OR 指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `|=` 指派運算子的運算式，例如  
  
```  
x |= y  
```  
  
 相當於  
  
```  
x = x | y  
```  
  
 但只會評估 `x` 一次。 [&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md) 在整數運算元上執行位元邏輯 OR 運算，在 bool 運算元上執行邏輯 OR。  
  
 無法直接多載 `|=` 運算子，但使用者定義型別可以多載 [&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
