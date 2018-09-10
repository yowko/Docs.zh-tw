---
title: '[] 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 19283a795f8cfc444dfcb186dcecc0ea86eb27fd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467428"
---
# <a name="-operator-c-reference"></a>[] 運算子 (C# 參考)
方括號 (`[]`) 可用於陣列、索引子和屬性， 也可與指標搭配使用。  
  
## <a name="remarks"></a>備註  
 陣列類型是後面接著 `[]` 的類型：  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 若要存取某個陣列項目，請以方括號括住所需項目的索引：  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 如果陣列索引超出範圍，則會擲回例外狀況。  
  
 陣列索引運算子無法多載；不過，類型可以定義接受一或多個參數的索引子。 索引子參數會由方括號括住，就像陣列索引一樣；但索引子參數可以宣告為任何類型，而不像陣列索引必須是整數型別。  
  
 例如，.NET Framework 定義 `Hashtable` 類型，該類型會建立任意類型之索引鍵和值的關聯：  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 方括號也可用來指定[屬性](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 您可以使用方括號來指定指標的索引：  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 不會執行任何界限檢查。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)  
- [陣列](../../../csharp/programming-guide/arrays/index.md)  
- [索引子](../../../csharp/programming-guide/indexers/index.md)  
- [Unsafe.DangerousAPI](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)
