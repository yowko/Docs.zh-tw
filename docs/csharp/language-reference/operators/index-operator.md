---
title: "[] 運算子 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
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
ms.openlocfilehash: 4eaecd5cd70c396a62856087a7b37f38e02d2383
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>[] 運算子 (C# 參考)
方括號 (`[]`) 可用於陣列、索引子和屬性， 也可與指標搭配使用。  
  
## <a name="remarks"></a>備註  
 陣列類型是後面接著 `[]` 的類型：  
  
 [!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 若要存取某個陣列項目，請以方括號括住所需項目的索引：  
  
 [!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 如果陣列索引超出範圍，則會擲回例外狀況。  
  
 陣列索引運算子無法多載；不過，類型可以定義索引子，以及接受一或多個參數的屬性。 索引子參數會由方括號括住，就像陣列索引一樣；但索引子參數可以宣告為任何類型，而不像陣列索引必須是整數型別。  
  
 例如，.NET Framework 定義 `Hashtable` 類型，該類型會建立任意類型之索引鍵和值的關聯：  
  
 [!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 方括號也可用來指定[屬性](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 您可以使用方括號來指定指標的索引：  
  
 [!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 不會執行任何界限檢查。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [索引子](../../../csharp/programming-guide/indexers/index.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)

