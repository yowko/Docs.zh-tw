---
title: / 運算子 (C# 參考)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: bddf6d234f3536ad64f0cd876cc7ade4494916d9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43800751"
---
# <a name="-operator-c-reference"></a>/ 運算子 (C# 參考)
除法運算子 (`/`) 會將它的第一個運算元除以第二個運算元。 所有數字類型都有預先定義的除法運算子。
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `/` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 多載 `/` 運算子會隱含地多載 [/= 運算子](division-assignment-operator.md)。  
  
 分割兩個整數時，結果一律會是整數。 例如，7/3 的結果是 2。 當 `/` 運算子趨近於零時，這不會與浮點除法相混淆：-7 / 3 為 -2。  
  
 若要取得商數為有理數，請使用 `float`、`double` 或 `decimal` 類型。 在[內建數值類型](../../../csharp/language-reference/keywords/reference-tables-for-types.md)之間轉換有很多方法。  
  
 若要判斷餘數，請使用[餘數運算子](../../../csharp/language-reference/operators/remainder-operator.md) `%`。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
