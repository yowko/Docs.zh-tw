---
title: "?: 運算子 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3e60516d1f443528c357eb12612b6149f34c1f7e
ms.lasthandoff: 03/13/2017

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
  
```  
  
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
 [!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)   
 [if-else](../../../csharp/language-reference/keywords/if-else.md)   
 [?. 和 ? 運算子](../../../csharp/language-reference/operators/null-conditional-operators.md)   
 [??運算子](../../../csharp/language-reference/operators/null-conditional-operator.md)
