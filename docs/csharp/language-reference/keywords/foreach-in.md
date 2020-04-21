---
title: C# foreach 陳述式
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 188d909fd33b14755d9b121953b1fa434ecf536d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738820"
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# 參考)

`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。 `foreach` 陳述式不限於那些型別，並且適用於滿足下列條件的任何型別執行個體：

- 具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。
- `GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。

從 C# 7.3 開始,如果枚舉`Current`器的屬性傳回`ref T`[引用傳回值](ref.md#reference-return-values)(集合元素的`ref readonly`類型`T`),可以使用`ref`或修改器聲明反覆運算變數。

從 C# 8.0`await`開始,當`foreach`<xref:System.Collections.Generic.IAsyncEnumerable%601>集合類型實現 介面時,運算元可以應用於語句。 迴圈的每個反覆運算都可以在非同步檢索下一個元素時掛起。 默認情況元素在捕獲的上下文中處理。 如果要禁用上下文捕獲,請使用<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>擴展方法。 有關同步上下文和捕獲當前上下文的詳細資訊,請參閱有關[使用基於任務的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。

您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。 您還可以通過`foreach`[goto、](goto.md)[傳回](return.md)或[引發](throw.md)語句退出迴圈。

若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。 如果語句的`foreach`源集合為空,則不會執行和跳`foreach`過 迴圈的正文。

## <a name="examples"></a>範例

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

下列範例會使用 `ref` 反覆運算變數來設定 stackalloc 陣列中每個項目的值。 `ref readonly` 版本會逐一查看集合以列印所有值。 `readonly` 宣告會使用隱含的本機變數宣告。 您可以搭配使用隱含的變數宣告與 `ref` 或 `ref readonly` 宣告，也可以明確地鍵入變數宣告。

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

以下範例用於`await foreach`發代非同步產生每個元素的集合:

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 編程指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [將 foreach 與陣列一起使用](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [用於語句](for.md)
