---
title: '| 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: d95fe29aa7ffab9938e8edc57999445268fe41a8
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001226"
---
# <a name="-operator-c-reference"></a>| 運算子 (C# 參考)
整數型別和 `bool` 會預先定義二元 `|` 運算子。 對於整數型別，`|` 會計算其運算元的位元 OR。 對於 `bool` 運算元，`|` 會計算其運算元的邏輯 OR；亦即，如果且唯有當其兩個運算元都是 `false` 時，結果會是 `false`。  
  
## <a name="remarks"></a>備註  
 二元 `|` 運算子會評估兩個運算元，不論第一個運算元的值為何，其與 [條件式-OR 運算子]     (conditional-or-operator.md) `||` 不同。
 
 使用者定義型別可以多載 `|` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
