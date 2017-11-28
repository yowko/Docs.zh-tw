---
title: "/ 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/ 運算子 (C# 參考)
除法運算子 (`/`) 會將它的第一個運算元除以第二個運算元。 所有數字類型都有預先定義的除法運算子。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `/` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 多載 `/` 運算子會隱含地多載 [/= 運算子](division-assignment-operator.md)。  
  
 分割兩個整數時，結果一律會是整數。 例如，7/3 的結果是 2。 若要判斷 7/3 的餘數，請使用餘數運算子 ([%](../../../csharp/language-reference/operators/modulus-operator.md))。 若要取得商數作為有理數或分數，則會提供被除數或除數類型 `float` 或 `double` 類型。 如果您將數字放在小數點右邊以將被除數或除數表示為小數，則可以隱含地指派類型，如下列範例所示。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
