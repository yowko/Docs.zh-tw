---
title: as - C# 參考
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 84e599340877ce52dc6242ea259c69672915c546
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422024"
---
# <a name="as-c-reference"></a>as (C# 參考)
您可以使用 `as` 運算子，以在相容的參考型別或[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)之間執行特定轉換類型。 下列程式碼示範範例。  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

如範例所示，您需要將 `as` 陳述式的結果與 `null` 比較，以檢查轉換是否成功。 從 C# 7.0 開始，您可以使用 [is](is.md) 陳述式來測試轉換是否成功，以及當轉換成功時有條件地指派變數。 在許多情況下，這比使用 `as` 運算子更精簡。 如需詳細資訊，請參閱 [`is` 運算子](is.md)一文的[類型模式](is.md#type)小節。
  
## <a name="remarks"></a>備註  
 `as` 運算子就像轉型運算。 不過，如果無法進行轉換，則 `as` 會傳回 `null`，而不是引發例外狀況。 參考下列範例：  
  
```csharp  
expression as type  
```  
  
 這個程式碼相當於下列運算式，差異在於只會評估 `expression` 變數一次。  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 請注意，`as` 運算子只會執行參考轉換、可為 Null 的轉換以及 Boxing 轉換。 `as` 運算子無法執行其他轉換，例如使用者定義的轉換，就應該改為使用轉換運算式來執行。  
  
## <a name="example"></a>範例  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [as 運算子](~/_csharplang/spec/expressions.md#the-as-operator)。 語言規格是 C# 語法及用法的限定來源。
 
## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
- [is](../../../csharp/language-reference/keywords/is.md)
- [?:運算子](../../../csharp/language-reference/operators/conditional-operator.md)
