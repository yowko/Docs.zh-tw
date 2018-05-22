---
title: '&gt;&gt;= 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: ccc3f688d985b9e35404550f0c53a7acf8095dd5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= 運算子 (C# 參考)
右移指派運算子。  
  
## <a name="remarks"></a>備註  
 以下格式的運算式  
  
```csharp  
x >>= y  
```  
  
 評估為  
  
```csharp  
x = x >> y  
```  
  
 但只會評估 `x` 一次。 [>> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md)會將 `x` 右移 `y` 所指定的數量。  
  
 無法直接多載 >>= 運算子，但使用者定義型別可以多載 [>> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
