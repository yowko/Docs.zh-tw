---
title: '&gt;&gt;= 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6bd0a61860c35a485d61585a90ba297f75d8cf1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= 運算子 (C# 參考)
右移指派運算子。  
  
## <a name="remarks"></a>備註  
 以下格式的運算式  
  
```  
x >>= y  
```  
  
 評估為  
  
```  
x = x >> y  
```  
  
 但只會評估 `x` 一次。 [>> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md)會將 `x` 右移 `y` 所指定的數量。  
  
 無法直接多載 >>= 運算子，但使用者定義型別可以多載 [>> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
