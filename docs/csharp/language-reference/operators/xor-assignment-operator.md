---
title: ^= 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: b868f2cdbfa8a80f89a12e6194a30154481f0b07
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>^= 運算子 (C# 參考)
互斥 OR 指派運算子。  
  
## <a name="remarks"></a>備註  
 以下格式的運算式  
  
```csharp  
x ^= y  
```  
  
 評估為  
  
```csharp  
x = x ^ y  
```  
  
 但只會評估 `x` 一次。 [^ 運算子](../../../csharp/language-reference/operators/xor-operator.md)會在整數運算元上執行位元互斥 OR 運算，以及在 [bool](../../../csharp/language-reference/keywords/bool.md) 運算元上執行邏輯互斥 OR。  
  
 無法直接多載 ^= 運算子，但使用者定義型別可以多載 [^ 運算子](../../../csharp/language-reference/operators/xor-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
