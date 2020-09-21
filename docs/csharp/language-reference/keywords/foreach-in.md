---
description: foreach、in (C# 參考)
title: C# foreach 陳述式
ms.date: 09/18/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: ea8a6f86595348a32b707caf9782f84147fefc87
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828886"
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# 參考)

`foreach`語句會針對實作為或介面之型別的實例中的每個專案，執行語句或語句區塊 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> ，如下列範例所示：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

`foreach`語句不限於這些類型。 您可以將它用於符合下列條件之任何類型的實例：

- 型別具有公用無參數 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。 從 c # 9.0 開始， `GetEnumerator` 方法可以是類型的 [擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。
- 方法的傳回型別 `GetEnumerator` 具有公用 `Current` 屬性，以及其傳回型別為的公用無參數 `MoveNext` 方法 <xref:System.Boolean> 。

下列範例 `foreach` 會使用語句 <xref:System.Span%601?displayProperty=nameWithType> 搭配類型的實例，而不會執行任何介面：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

從 c # 7.3 開始，如果列舉 `Current` 值的屬性傳回 [參考傳回值](ref.md#reference-return-values) (`ref T` 其中 `T` 是集合元素) 的型別，您可以使用或修飾詞來宣告反覆運算變數 `ref` `ref readonly` ，如下列範例所示：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

從 c # 8.0 開始，您可以使用 `await foreach` 語句來取用非同步資料資料流程，也就是實作為介面的集合型別 <xref:System.Collections.Generic.IAsyncEnumerable%601> 。 迴圈的每個反復專案可能會暫停，而下一個元素則以非同步方式抓取。 下列範例顯示如何使用 `await foreach` 語句：

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

根據預設，資料流程專案會在已捕捉的內容中處理。 如果您想要停用內容的捕捉，請使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 擴充方法。 如需同步處理內容和取得目前內容的詳細資訊，請參閱 [使用以工作為基礎的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)。 如需非同步資料流程的詳細資訊，請參閱[c # 8.0 的新功能文章中](../../whats-new/csharp-8.md)的[非同步資料流程](../../whats-new/csharp-8.md#asynchronous-streams)一節。

您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。 您也可以使用 `foreach` [goto](goto.md)、 [return](return.md)或 [throw](throw.md) 語句來結束迴圈。

若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。 如果語句的來源集合 `foreach` 是空的，則 `foreach` 不會執行和略過迴圈的主體。

## <a name="type-of-an-iteration-variable"></a>反覆運算變數的類型

您可以使用 `var` 關鍵字，讓編譯器推斷語句中反覆運算變數的類型 `foreach` ，如下列程式碼所示：

```csharp
foreach (var item in collection) { }
```

您也可以明確指定反覆運算變數的類型，如下列程式碼所示：

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

在上述的表單中，collection 元素的型別 `T` 必須隱含或明確地轉換成 `V` 反覆運算變數的型別。 如果 `T` 在執行時間從到的明確轉換 `V` 失敗，則語句會擲回 `foreach` <xref:System.InvalidCastException> 。 例如，如果 `T` 是非密封類別型別，則 `V` 可以是任何介面型別，甚至是不會執行的介面型 `T` 別。 在執行時間，collection 元素的型別可能是衍生自和實際執行的型別 `T` `V` 。 如果不是這種情況， <xref:System.InvalidCastException> 就會擲回。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。

如需有關 c # 8.0 和更新版本中新增之功能的詳細資訊，請參閱下列功能提案附注：

- [非同步資料流程 (c # 8.0) ](~/_csharplang/proposals/csharp-8.0/async-streams.md)
- [`GetEnumerator`支援迴圈的擴充功能 `foreach` (c # 9.0) ](~/_csharplang/proposals/csharp-9.0/extension-getenumerator.md)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [C# 關鍵字](index.md)
- [搭配陣列使用 foreach](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for 陳述式](for.md)
