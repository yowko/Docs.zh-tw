---
title: "|= 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aac4fd6016b65daa15da4bd3a414f385edce7c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
