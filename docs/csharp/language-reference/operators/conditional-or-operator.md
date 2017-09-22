---
title: "|| 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 57bcb25b0d453fa59855f40c3189eb4af2bb8b7f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>|| 運算子 (C# 參考)
條件式 OR 運算子 (`||`) 會執行其 `bool` 運算元的邏輯 OR。 如果第一個運算元評估值為 `true`，就不會評估第二個運算元。 如果第一個運算元評估值為 `false`，第二個運算子會判斷整個 OR 運算式是評估為`true` 或 `false`。  
  
## <a name="remarks"></a>備註  
 作業  
  
```  
x || y  
```  
  
 對應至作業  
  
```  
x | y  
```  
  
 差異在於，如果 `x` 是 `true`，則不會評估 `y`，因為不論 `y` 的值為何，OR 運算都是 `true`。 這個概念稱為「最少運算」求值。  
  
 無法多載條件式 OR 運算子，但規則邏輯運算子與 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 運算子的多載具有某些限制，也會視為條件式邏輯運算子的多載。  
  
## <a name="example"></a>範例  
 在下列範例中，使用 `||` 的運算式只會評估第一個運算元。 使用 `|` 的運算式則評估這兩個運算元。 在第二個範例中，如果評估這兩個運算元，就會發生執行階段例外狀況。  
  
 [!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)

