---
title: 在 C# 中撰寫 LINQ 查詢
description: 了解如何在 C# 中撰寫 LINQ 查詢。
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: 5003d1a5e15e17bea4204941d1c43895e3fb91f4
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403930"
---
# <a name="write-linq-queries-in-c"></a>在 C# 中撰寫 LINQ 查詢 #

本文示範您可以在 C# 中撰寫 LINQ 查詢的三種方式：

1. 使用查詢語法。

2. 使用方法語法。

3. 合併使用查詢語法與方法語法。

下列範例會使用先前列出的每種方法，來示範一些簡單 LINQ 查詢。 一般而言，規則會在可能時使用 (1)，並在需要時使用 (2) 和 (3)。

> [!NOTE]
> 這些查詢是在簡單記憶體內部集合上運作，但，基本語法與用於 LINQ to Entities 和 LINQ to XML 的語法完全相同。

## <a name="example---query-syntax"></a>範例 - 查詢語法

撰寫大部分查詢的建議方式是使用「查詢語法」來建立「查詢運算式」。 下列範例示範三個查詢運算式。 第一個查詢運算式示範如何使用 `where` 子句套用條件來篩選或限制結果。 它會傳回值大於 7 或小於 3 的來源序列中的所有項目。 第二個運算式示範如何排序傳回的結果。 第三個運算式示範如何根據索引鍵來分組結果。 此查詢會根據單字的第一個字母來傳回兩個群組。

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

請注意，查詢類型是 <xref:System.Collections.Generic.IEnumerable%601>。 使用 `var` 可以撰寫所有這些查詢，如下列範例所示︰

`var query = from num in numbers...`

在每個上述範例中，除非您逐一查看 `foreach` 陳述式或其他陳述式中的查詢變數，否則不會實際執行查詢。 如需詳細資訊，請參閱 [LINQ 查詢簡介](../programming-guide/concepts/linq/introduction-to-linq-queries.md)。

## <a name="example---method-syntax"></a>範例 - 方法語法

某些查詢作業必須以方法呼叫形式表示。 這類最常見的方法會傳回單一數值，例如 <xref:System.Linq.Enumerable.Sum%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Average%2A> 等等。 一律必須在任何查詢中最後才呼叫這些方法，因為它們只代表單一值，並不能作為其他查詢作業的來源。 下列範例示範查詢運算式中的方法呼叫：

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

如果方法具有 Action 或 Func 參數，則這些項目是以 [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) 運算式形式提供，如下列範例所示：

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

在先前的查詢中，只會立即執行查詢 #4。 這是因為它會傳回單一值，而不是泛型 <xref:System.Collections.Generic.IEnumerable%601> 集合。 方法本身必須使用 `foreach`，才能計算其值。

搭配使用隱含類型與 [var](../language-reference/keywords/var.md)，可以撰寫每個先前的查詢，如下列範例所示︰

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>範例 - 混合查詢和方法語法

這個範例示範如何在查詢子句結果上使用方法語法。 只需要用括號括住查詢運算式，然後套用點運算子並呼叫方法。 在下列範例中，查詢 #7 會傳回其值介於 3 與 7 之間的數字計數。 不過，一般而言，最好使用第二個變數來儲存方法呼叫的結果。 如此一來，查詢就比較不容易與查詢結果混淆。

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

因為查詢 #7 會傳回單一值，而不是集合，所以會立即執行查詢。

搭配使用隱含類型與 `var`，可以撰寫前一個查詢，如下列所示︰

```csharp
var numCount = (from num in numbers...
```

它可以撰寫於方法語法中，如下所示：

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

它可以使用明確類型進行撰寫，如下所示：

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>另請參閱

[逐步解說：在 C# 中撰寫查詢](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
[Language Integrated Query (LINQ)](index.md)
[where 子句](../language-reference/keywords/where-clause.md)