---
title: "&lt;&lt; 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt; 運算子 (C# 參考)
左移運算子 (`<<`) 會向其第一個運算元左移第二個運算元所指定的位元數。 第二個運算元的類型必須是 [int](../../../csharp/language-reference/keywords/int.md) 或對 `int` 進行預先定義隱含數值轉換的類型。  
  
## <a name="remarks"></a>備註  
 如果第一個運算元是 [int](../../../csharp/language-reference/keywords/int.md) 或 [uint](../../../csharp/language-reference/keywords/uint.md) (32 位元數量)，則是由第二個運算元的低序位五位元指定移位計數。 也就是，實際移位計數是 0 到 31 位元。  
  
 如果第一個運算元是 [long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) (64 位元數量)，則是由第二個運算元的低序位六位元指定移位計數。 也就是，實際移位計數是 0 到 63 位元。  
  
 會捨棄移位後面不在第一個運算元類型範圍內的任何高序位位元，而且低序位空位元都會填入零。 移位作業絕不會造成溢位。  
  
 使用者定義型別可以多載 `<<` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))；第一個運算元的類型必須是使用者定義型別，而第二個運算元的類型必須是 `int`。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>註解  
 請注意，`i<<1` 和 `i<<33` 提供相同的結果，因為 1 和 33 有相同的低序位五位元。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
