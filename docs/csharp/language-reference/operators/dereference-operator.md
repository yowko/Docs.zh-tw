---
title: -&gt; 運算子 (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c5918f56257feb29d2624ba29b8cebaaa4f4ebe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-gt-operator-c-reference"></a>-&gt; 運算子 (C# 參考)
`->` 運算子結合了指標取值和成員存取。  
  
## <a name="remarks"></a>備註  
 以下格式的運算式：  
  
```  
x->y  
```  
  
 (其中 `x` 是類型 `T*` 的指標，而 `y` 是 `T` 的成員) 相當於：  
  
```  
(*x).y  
```  
  
 `->` 運算子只能用於標記為 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 的程式碼。  
  
 `->` 運算子無法多載。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
