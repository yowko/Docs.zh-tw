---
title: "?: 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9abfe4ca6be29b54edd591b503069c15e02c3532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>?: 運算子 (C# 參考)
條件運算子 (`?:`) 是根據布林運算式的值傳回兩個值的其中一個。 以下是條件運算子的語法。  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>備註  
 `condition` 必須判斷值為 `true` 或 `false`。 如果 `condition` 為 `true`，則會評估 `first_expression` 並產生結果。 如果 `condition` 為 `false`，則會評估 `second_expression` 並產生結果。 只會評估兩個運算式的其中一個。  
  
 `first_expression` 和 `second_expression` 必須屬於相同類型，否則必須從其中一種類型隱含轉換為另一種類型。  
  
 你可以使用條件運算子更精確地表示可能需要 `if-else` 建構的計算。 例如，下列程式碼會先使用 `if` 陳述式，再使用條件運算子將整數分類為正數或負數。  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 條件運算子是右向關聯。 運算式 `a ? b : c ? d : e` 會判斷值為 `a ? b : (c ? d : e)`，而不是 `(a ? b : c) ? d : e`。  
  
 條件運算子不能多載。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)  
 [if-else](../../../csharp/language-reference/keywords/if-else.md)  
 [?.和嗎？運算子](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [??運算子](../../../csharp/language-reference/operators/null-conditional-operator.md)
