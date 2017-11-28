---
title: "%= 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>%= 運算子 (C# 參考)
餘數指派運算子。  
  
## <a name="remarks"></a>備註  
 使用 `%=` 指派運算子的運算式，例如  
  
```  
x %= y  
```  
  
 相當於  
  
```  
x = x % y  
```  
  
 但只會評估 `x` 一次。 對於要計算除法運算後餘數的數值類型，已預先定義 [/ 運算子](../../../csharp/language-reference/operators/modulus-operator.md)。  
  
 無法直接多載 `%=` 運算子，但使用者定義型別可以多載 [% 運算子](../../../csharp/language-reference/operators/modulus-operator.md) (請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
