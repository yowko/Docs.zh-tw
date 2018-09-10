---
title: from 子句 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: c8c124f44df292b8323560cce541cca2765e2790
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186405"
---
# <a name="from-clause-c-reference"></a>from 子句 (C# 參考)

查詢運算式的開頭必須是 `from` 子句。 此外，查詢運算式可以包含子查詢，也是以 `from` 子句開頭。 `from` 子句指定下列內容：

- 會執行查詢或子查詢的資料來源。

- 本機「範圍變數」，代表來源序列中的每個項目。

範圍變數和資料來源都是強型別。 `from` 子句中參考的資料來源，必須有 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601> 類型，或 <xref:System.Linq.IQueryable%601> 等衍生類型。

在下例中，`numbers` 是資料來源，而 `num` 是範圍變數。 請注意，即使使用 [var](var.md) 關鍵字，這兩個變數都是強型別。

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>範圍變數

當資料來源實作 <xref:System.Collections.Generic.IEnumerable%601> 時，編譯器會推斷範圍變數的類型。 例如，如果來源有類型 `IEnumerable<Customer>`，則範圍變數推斷為 `Customer`。 必須明確指定類型的時機，是當來源為非泛型的 `IEnumerable` 類型時，如 <xref:System.Collections.ArrayList>。 如需詳細資訊，請參閱[如何：使用 LINQ 查詢 ArrayList](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)。

在前例中，`num` 推斷為類型 `int`。 因為範圍變數是強型別，所以您可以對它呼叫方法，或在其他作業中使用它。 例如，不寫入 `select num`，而是可以寫入 `select num.ToString()` 讓查詢運算式傳回一串字串，不是整數序列。 或者可以寫入 `select n + 10` 讓運算式傳回 14、11、13、12、10 序列。 如需詳細資訊，請參閱 [select 子句](select-clause.md)。

範圍變數就像 [foreach](foreach-in.md) 陳述式中的反覆項目變數，但有一個非常重要的差異：範圍變數從不真正儲存來源的資料。 它只是讓查詢描述在執行查詢時會發生什麼的語法便利性。 如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md)。

## <a name="compound-from-clauses"></a>複合 from 子句

在某些情況下，來源序列中的每個項目自己本身可能就是序列或包含序列。 例如，您的資料來源可能是 `IEnumerable<Student>`，其中序列中的每個學生物件都包含測驗分數的清單。 若要存取每個 `Student` 項目內的內部清單，您可以使用複合 `from` 子句。 技巧就像使用巢狀的 [foreach](foreach-in.md) 陳述式一樣。 您可以將 [where](partial-method.md) 或 [orderby](orderby-clause.md) 子句新增至任一 `from` 子句來篩選結果。 下例顯示一系列 `Student` 物件，每個都包含代表測試分數的整數內部 `List`。 若要存取內部清單，請使用複合 `from` 子句。 如有必要，您可以在兩個 `from` 子句之間插入子句。

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>使用多個 from 子句執行聯結

複合 `from` 子句是用來存取單一資料來源中的內部集合。 不過，查詢也可以包含多個 `from` 子句，從獨立的資料來源產生增補查詢。 這項技術可讓您執行特定的聯結作業類型，這些是使用 [join 子句](join-clause.md)都不可能執行的類型。

下例示範如何使用兩個 `from` 子句形成兩個資料來源的完整交叉聯結。

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

如需使用多個 `from` 子句的聯結作業詳細資訊，請參閱[執行左方外部聯結](../../linq/perform-left-outer-joins.md)。

## <a name="see-also"></a>另請參閱

- [查詢關鍵字 (LINQ)](query-keywords.md)  
- [Language-Integrated Query (LINQ)](../../linq/index.md)  
