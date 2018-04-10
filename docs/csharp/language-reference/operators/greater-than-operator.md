---
title: '&gt; 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc7c173ecc97bd3ca3b76a92ccbabc0f40062ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gt-operator-c-reference"></a>&gt; 運算子 (C# 參考)
如果第一個運算元大於第二個運算元，則所有數值和列舉類型都會定義「大於」關係運算子 (`>`) 以傳回 `true`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `>` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 如果多載 `>`，也必須多載 [<](../../../csharp/language-reference/operators/less-than-operator.md)。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)
