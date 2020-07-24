---
title: C# foreach 陳述式
ms.date: 07/22/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 4af431d29e538c1516efeaad3008eaa3b2229ece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104246"
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# 參考)

`foreach`語句會針對實作為或介面之類型實例中的每個專案執行語句或語句區塊 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> ，如下列範例所示：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

`foreach`語句不限於那些類型。 您可以將它與符合下列條件的任何類型實例搭配使用：

- 型別具有公用無參數 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別，
- `GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。

下列範例 `foreach` 會使用語句 <xref:System.Span%601?displayProperty=nameWithType> 搭配類型的實例，而不會執行任何介面：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

從 c # 7.3 開始，如果枚舉器的 `Current` 屬性傳回[參考傳回值](ref.md#reference-return-values)（ `ref T` 其中 `T` 是集合元素的類型），您可以使用或修飾詞來宣告反覆運算變數 `ref` `ref readonly` ，如下列範例所示：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

從 c # 8.0 開始，您可以使用 `await foreach` 語句來取用非同步資料資料流程，也就是實作為介面的集合型別 <xref:System.Collections.Generic.IAsyncEnumerable%601> 。 當下一個元素以非同步方式抓取時，迴圈的每個反復專案都可能會暫停。 下列範例顯示如何使用 `await foreach` 語句：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

根據預設，資料流程元素會在已捕捉的內容中處理。 如果您想要停用內容的捕捉，請使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 擴充方法。 如需同步處理內容和捕捉目前內容的詳細資訊，請參閱[使用以工作為基礎的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)。 如需非同步資料流程的詳細資訊，請參閱[c # 8.0 的新功能](../../whats-new/csharp-8.md)一文中的[非同步資料流程](../../whats-new/csharp-8.md#asynchronous-streams)一節。

您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。 您也可以使用 `foreach` [goto](goto.md)、 [return](return.md)或[throw](throw.md)語句來結束迴圈。

若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。 如果語句的來源集合 `foreach` 是空的，則 `foreach` 不會執行和略過迴圈的主體。

## <a name="type-of-an-iteration-variable"></a>反復專案變數的類型

您可以使用 `var` 關鍵字，讓編譯器推斷語句中反覆運算變數的類型 `foreach` ，如下列程式碼所示：

```csharp
foreach (var item in collection) { }
```

您也可以明確指定反復專案變數的類型，如下列程式碼所示：

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

在上述表單中， `T` 集合元素的類型必須隱含或明確地轉換成 `V` 反覆運算變數的類型。 如果從到的明確 `T` 轉換 `V` 在執行時間失敗，則語句會擲回 `foreach` <xref:System.InvalidCastException> 。 例如，如果 `T` 是非密封的類別類型， `V` 可以是任何介面類別型，即使不是要執行的也一樣 `T` 。 在執行時間，集合元素的類型可能是衍生自並實際執行的專案 `T` `V` 。 如果不是這種情況， <xref:System.InvalidCastException> 就會擲回。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。

## <a name="see-also"></a>請參閱

- [C# 參考資料](../index.md)
- [C # 關鍵字](index.md)
- [搭配陣列使用 foreach](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for 陳述式](for.md)
