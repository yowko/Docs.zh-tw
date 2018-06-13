---
title: select 子句 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 6e7277b5d714e48059fe1ed7e8b85e46a14a840c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279980"
---
# <a name="select-clause-c-reference"></a>select 子句 (C# 參考)
在查詢運算式中，`select` 子句指定將在執行查詢時產生之值的類型。 結果是根據評估所有先前子句以及 `select` 子句本身中的任何運算式而來。 查詢運算式必須以 `select` 子句或 [group](../../../csharp/language-reference/keywords/group-clause.md) 子句來終止。  
  
 下列範例示範查詢運算式中的簡單 `select` 子句。  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 `select` 子句所產生的序列類型可決定查詢變數 `queryHighScores` 的類型。 在最簡單的情況下，`select` 子句只會指定範圍變數。 這會導致傳回的序列將相同類型的項目包含為資料來源。 如需詳細資訊，請參閱 [LINQ 查詢作業中的類型關聯性](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。 不過，`select` 子句也提供功能強大的機制，將來源資料轉換 (或「投影」) 為新的類型。 如需詳細資訊，請參閱[使用 LINQ 轉換資料 (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)。  
  
## <a name="example"></a>範例  
 下列範例示範 `select` 子句可接受的所有不同形式。 在每個查詢中，請注意 `select` 子句與「查詢變數」類型之間的關聯性 (`studentQuery1`、`studentQuery2`，依此類推)。  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 如前一個範例中的 `studentQuery8` 所示，您有時可能想要所傳回序列的項目只包含來源項目的屬性子集。 盡量保持最少的所傳回序列，以降低記憶體需求，並提高查詢的執行速度。 做法是在 `select` 子句中建立匿名型別，並使用物件初始設定式以利用來源項目中的適當屬性來初始化它。 如需如何執行此作業的範例，請參閱[物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
## <a name="remarks"></a>備註  
 在編譯時間，`select` 子句會轉譯為 <xref:System.Linq.Enumerable.Select%2A> 標準查詢運算子的方法呼叫。  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [查詢關鍵字 (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [from 子句](../../../csharp/language-reference/keywords/from-clause.md)  
 [partial (方法) (C# 參考)](../../../csharp/language-reference/keywords/partial-method.md)  
 [匿名類型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [開始使用 C# 中的 LINQ](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
