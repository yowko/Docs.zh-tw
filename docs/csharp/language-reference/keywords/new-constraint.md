---
title: new 條件約束 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="new-constraint-c-reference"></a>new 條件約束 (C# 參考)
`new` 條件約束指定泛型類別宣告中的任何型別引數都必須有公用的無參數建構函式。 若要使用新的條件約束，型別不能為抽象。  
  
## <a name="example"></a>範例  
 當泛型類別建立新的型別執行個體時，將 `new` 條件約束套用至型別參數，如下例所示︰  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a>範例  
 當您使用 `new()` 條件約束與其他條件約束時，它必須是最後一個指定的︰  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 如需詳細資訊，請參閱[型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Collections.Generic>  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [泛型](../../../csharp/programming-guide/generics/index.md)
