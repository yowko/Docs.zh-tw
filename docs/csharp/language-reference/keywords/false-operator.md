---
title: "false 運算子 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: 21
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 22aaef73efc1d3327774336bf5b2c5475950ce25
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="false-operator-c-reference"></a>false 運算子 (C# 參考)
若運算元為 `false` 即傳回 [bool](../../../csharp/language-reference/keywords/bool.md) 值 `true`；否則傳回 `false`。  
  
 在 C# 2.0 之前，`true` 和 `false` 運算子是用來建立使用者定義之可為 Null 的實值型別，該類型與 `SqlBool` 等類型相容。 不過，該語言現在針對可為 Null 的型別提供內建支援，因此您應盡可能使用這些類型，而不是多載 `true` 和 `false` 運算子。 如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。  
  
 使用可為 Null 的布林值時，運算式 `a != b` 不一定等於 `!(a == b)`，因為其中一個或兩個值可能為 Null。 您必須分別多載 `true` 和 `false` 運算子，以正確處理運算式中的 Null 值。 下列範例示範如何多載和使用 `true` 和 `false` 運算子。  
  
 [!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 多載 `true` 和 `false` 運算子的類型可用於 [if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md) 和 [for](../../../csharp/language-reference/keywords/for.md) 陳述式以及[條件運算式](../../../csharp/language-reference/operators/conditional-operator.md)中的控制運算式。  
  
 如果類型定義了運算子 `false`，則必須同時定義運算子 [true](../../../csharp/language-reference/keywords/true.md)。  
  
 類型不能直接多載條件邏輯運算子 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 和 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)，但藉由多載一般邏輯運算子以及 `true` 和 `false` 運算子，也可達到同樣效果。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)   
 [true](../../../csharp/language-reference/keywords/true.md)
