---
title: group 子句 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 157bd07f3332883f010ef26ba920dae88276051b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003225"
---
# <a name="group-clause-c-reference"></a>group 子句 (C# 參考)

`group` 子句會傳回一系列的 <xref:System.Linq.IGrouping%602> 物件，而這些物件包含符合群組之索引鍵值的零或多個項目。 例如，您可以根據每個字串中的第一個字母來分組一序列的字串。 在此情況下，第一個字母是索引鍵、具有類型 [char](char.md)，並儲存在每個 <xref:System.Linq.IGrouping%602> 物件的 `Key` 屬性中。 編譯器會推斷索引鍵類型。

您可以使用 `group` 子句結束查詢運算式，如下列範例所示︰

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

如果您想要對每個群組執行其他查詢作業，則可以使用 [into](into.md) 內容關鍵字來指定暫時識別碼。 當您使用 `into` 時，必須繼續進行查詢，最後以 `select` 陳述式或另一個 `group` 子句結束，如下列摘錄所示︰

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

本文的＜範例＞一節中提供使用或未使用 `into` 之 `group` 的更完整範例。

## <a name="enumerating-the-results-of-a-group-query"></a>列舉群組查詢結果

因為 `group` 查詢所產生的 <xref:System.Linq.IGrouping%602> 物件基本上是清單的清單，所以您必須使用巢狀 [foreach](foreach-in.md) 迴圈來存取每個群組中的項目。 外部迴圈會逐一查看群組索引鍵，內部迴圈則會逐一查看群組本身中的每個項目。 群組可能具有索引鍵，但沒有項目。 下列 `foreach` 迴圈會執行先前程式碼範例中的查詢︰

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a>索引鍵類型

群組索引鍵可以是任何類型，例如字串、內建數值類型，或使用者定義的具名類型或匿名型別。

### <a name="grouping-by-string"></a>依字串群組

先前的程式碼範例已使用 `char`。 可以改為輕鬆地指定字串索引鍵，例如完整姓氏︰

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a>依 bool 群組

下列範例示範如何使用索引鍵的 bool 值，以將結果分成兩個群組。 請注意，值是由 `group` 子句中的子運算式所產生。

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a>依數字範圍群組

下一個範例使用運算式來建立代表百分位數範圍的數字群組索引鍵。 請注意會使用 [let](let-clause.md) 作為儲存方法呼叫結果的方便位置，因此不需要在 `group` 子句中呼叫方法兩次。 也請注意在 `group` 子句中，為了避免「除以零」例外狀況，程式碼會檢查以確定學生沒有平均值零。 如需如何在查詢運算式中安全地使用方法的詳細資訊，請參閱[如何：處理查詢運算式中的例外狀況](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)。

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a>依複合索引鍵群組

當您想要根據多個索引鍵來群組項目時，請使用複合索引鍵。 您可以使用匿名型別或具名類型來保存索引鍵項目，以建立複合索引鍵。 在下列範例中，假設已宣告 `Person` 類別具有名為 `surname` 和 `city` 的成員。 `group` 子句會為每一組具有相同姓氏和相同城市的人員，建立個別群組。

```csharp
group person by new {name = person.surname, city = person.city};
```

如果您必須將查詢變數傳遞給另一種方法，請使用具名類型。 請使用索引鍵的自動實作屬性建立特殊類別，然後覆寫 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 方法。 您也可以使用結構，在此情況下，您絕對不需要覆寫這些方法。 如需詳細資訊，請參閱[如何：使用自動實作的屬性來實作輕量型類別](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)和[如何：查詢目錄樹狀結構中的重複檔案](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)。 第二篇文章的程式碼範例示範如何使用含有具名類型的複合索引鍵。

## <a name="example"></a>範例

下列範例示範未將任何其他查詢邏輯套用到群組時，將來源資料排序成群組的標準模式。 這稱為無接續群組。 字串陣列中的項目是根據其第一個字母進行分組。 查詢的結果是包含 `char` 類型之公用 `Key` 屬性的 <xref:System.Linq.IGrouping%602> 類型，以及包含群組中各個項目的 <xref:System.Collections.Generic.IEnumerable%601> 集合。

`group` 子句的結果是一連串的序列。 因此，若要存取每個所傳回群組內的個別項目，請在重複執行群組索引鍵的迴圈內使用巢狀 `foreach` 迴圈，如下列範例所示。

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a>範例

這個範例示範如何搭配使用「接續」與 `into`，以在建立其他邏輯之後，對群組執行這些邏輯。 如需詳細資訊，請參閱 [into](into.md)。 下列範例會查詢每個群組，只選取其索引鍵值是母音的群組。

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a>備註

在編譯時期，`group` 子句會轉譯成 <xref:System.Linq.Enumerable.GroupBy%2A> 方法的呼叫。

## <a name="see-also"></a>另請參閱

- <xref:System.Linq.IGrouping%602>  
- <xref:System.Linq.Enumerable.GroupBy%2A>  
- <xref:System.Linq.Enumerable.ThenBy%2A>  
- <xref:System.Linq.Enumerable.ThenByDescending%2A>  
- [查詢關鍵字](query-keywords.md)  
- [Language-Integrated Query (LINQ)](../../linq/index.md)  
- [建立巢狀群組](../../linq/create-a-nested-group.md)  
- [將查詢結果分組](../../linq/group-query-results.md)  
- [在分組作業上執行子查詢](../../linq/perform-a-subquery-on-a-grouping-operation.md)