---
title: '&amp;= 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;= 運算子 (C# 參考)
AND 指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `&=` 指派運算子的運算式，例如  
  
```  
x &= y  
```  
  
 相當於  
  
```  
x = x & y  
```  
  
 但只會評估 `x` 一次。 [& 運算子](../../../csharp/language-reference/operators/and-operator.md)在整數運算元上執行位元邏輯 AND 運算，在 `bool` 運算元上執行邏輯 AND。  
  
 無法直接多載 `&=` 運算子，但使用者定義型別可以多載二進位 [& 運算子](../../../csharp/language-reference/operators/and-operator.md) (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
