---
title: '&gt; 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 1589c5e785b33db6106a0ef0a58202e771db9fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="gt-operator-c-reference"></a>&gt; 運算子 (C# 參考)
如果第一個運算元大於第二個運算元，則所有數值和列舉類型都會定義「大於」關係運算子 (`>`) 以傳回 `true`，否則為 `false`。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `>` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 如果多載 `>`，也必須多載 [<](../../../csharp/language-reference/operators/less-than-operator.md)。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)
