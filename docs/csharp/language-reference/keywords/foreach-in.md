---
title: C# foreach 陳述式
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401884"
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# 參考)

`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。 `foreach`語句不限於這些類型，而且可以套用至符合下列條件之任何類型的實例：

- 具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。
- `GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。

在大部分的情況下， `foreach` `IEnumerable<T>` 會逐一查看每個元素的類型為的運算式 `T` 。 不過，元素可能是任何具有從屬性類型隱含或明確轉換的類型 `Current` 。 如果 `Current` 屬性傳回 `SomeType` ，則元素的類型可能是：

- 的任何基類 `SomeType` 。
- 所執行的任何介面 `SomeType` 。

此外，如果 `SomeType` 是 `class` 或， `interface` 而不是 `sealed` ，則元素的類型可能包括：

- 衍生自的任何類型 `SomeType` 。
- 任何任意介面。 允許任何介面，因為任何介面都可以由衍生自或執行的類別來執行 `SomeType` 。

您可以使用符合上述規則的任何類型來宣告反復專案變數。 如果從轉換 `SomeType` 成反覆運算變數的類型需要明確轉換，該作業可能會 <xref:System.InvalidCastException> 在轉換失敗時擲回。

從 c # 7.3 開始，如果枚舉器的 `Current` 屬性傳回[參考傳回值](ref.md#reference-return-values)（ `ref T` 其中 `T` 是集合元素的類型），您可以使用或修飾詞來宣告反覆運算變數 `ref` `ref readonly` 。

從 c # 8.0 開始， `await` 當集合類型執行介面時，可以將運算子套用至 `foreach` 語句 <xref:System.Collections.Generic.IAsyncEnumerable%601> 。 當下一個元素以非同步方式抓取時，迴圈的每個反復專案都可能會暫停。 根據預設，資料流程元素會在已捕捉的內容中處理。 如果您想要停用內容的捕捉，請使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 擴充方法。 如需同步處理內容及取得目前內容的詳細資訊，請參閱有關[使用以工作為基礎的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。

您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。 您也可以使用 `foreach` [goto](goto.md)、 [return](return.md)或[throw](throw.md)語句來結束迴圈。

若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。 如果語句的來源集合 `foreach` 是空的，則 `foreach` 不會執行和略過迴圈的主體。

## <a name="examples"></a>範例

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

下列範例會使用 `ref` 反覆運算變數來設定 stackalloc 陣列中每個項目的值。 `ref readonly` 版本會逐一查看集合以列印所有值。 `readonly` 宣告會使用隱含的本機變數宣告。 您可以搭配使用隱含的變數宣告與 `ref` 或 `ref readonly` 宣告，也可以明確地鍵入變數宣告。

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

下列範例會使用 `await foreach` 來逐一查看會以非同步方式產生每個元素的集合：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
- [搭配陣列使用 foreach](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for 陳述式](for.md)
