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
ms.openlocfilehash: 3fa60d4e7546fc88ac2a2ffea45ae69b0da7a6a6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130897"
---
# <a name="select-clause-c-reference"></a>select 子句 (C# 參考)

在查詢運算式中，`select` 子句指定將在執行查詢時產生之值的類型。 結果是根據評估所有先前子句以及 `select` 子句本身中的任何運算式而來。 查詢運算式必須以 `select` 子句或 [group](group-clause.md) 子句來終止。

下列範例示範查詢運算式中的簡單 `select` 子句。

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

`select` 子句所產生的序列類型可決定查詢變數 `queryHighScores` 的類型。 在最簡單的情況下，`select` 子句只會指定範圍變數。 這會導致傳回的序列將相同類型的項目包含為資料來源。 如需詳細資訊，請參閱 [LINQ 查詢作業中的類型關聯性](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。 不過，`select` 子句也提供功能強大的機制，將來源資料轉換 (或「投影」) 為新的類型。 如需詳細資訊，請參閱[使用 LINQ 轉換資料 (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md)。

## <a name="example"></a>範例

下列範例示範 `select` 子句可接受的所有不同形式。 在每個查詢中，請注意 `select` 子句與「查詢變數」類型之間的關聯性 (`studentQuery1`、`studentQuery2`，依此類推)。

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

如前一個範例中的 `studentQuery8` 所示，您有時可能想要所傳回序列的項目只包含來源項目的屬性子集。 盡量保持最少的所傳回序列，以降低記憶體需求，並提高查詢的執行速度。 做法是在 `select` 子句中建立匿名型別，並使用物件初始設定式以利用來源項目中的適當屬性來初始化它。 如需如何執行此作業的範例，請參閱[物件和集合初始設定式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)。

## <a name="remarks"></a>備註

在編譯時間，`select` 子句會轉譯為 <xref:System.Linq.Enumerable.Select%2A> 標準查詢運算子的方法呼叫。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [查詢關鍵字 (LINQ)](query-keywords.md)
- [from 子句](from-clause.md)
- [partial (方法) (C# 參考)](partial-method.md)
- [匿名類型](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ 查詢運算式](../../programming-guide/linq-query-expressions/index.md)
- [開始使用 C# 中的 LINQ](../../programming-guide/concepts/linq/getting-started-with-linq.md)