---
title: "as (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
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
ms.openlocfilehash: 7a55c696ac295eee8d5d35ed56038f3c4a90b215
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="as-c-reference"></a>as (C# 參考)
您可以使用 `as` 運算子，以在相容的參考型別或[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)之間執行特定轉換類型。 下列程式碼示範範例。  
  
 [!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>備註  
 `as` 運算子就像轉型運算。 不過，如果無法進行轉換，則 `as` 會傳回 `null`，而不是引發例外狀況。 參考下列範例：  
  
```  
expression as type  
```  
  
 這個程式碼相當於下列運算式，差異在於只會評估 `expression` 變數一次。  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 請注意，`as` 運算子只會執行參考轉換、可為 Null 的轉換以及 Boxing 轉換。 `as` 運算子無法執行其他轉換，例如使用者定義的轉換，就應該改為使用轉換運算式來執行。  
  
## <a name="example"></a>範例  
 [!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [?: 運算子](../../../csharp/language-reference/operators/conditional-operator.md)   
 [運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md)

