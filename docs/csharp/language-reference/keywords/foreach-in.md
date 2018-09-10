---
title: C# foreach 陳述式
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d84c68eb102d55b31ba20a6b6b5c01b96963924d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405846"
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# 參考)

`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。 `foreach` 陳述式不限於那些型別，並且適用於滿足下列條件的任何型別執行個體：

- 具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。
- `GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。

您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。 您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `foreach` 迴圈。

## <a name="examples"></a>範例

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

從 C# 7.3 開始，如果列舉值的 `Current` 屬性會傳回[參考傳回值](../../programming-guide/classes-and-structs/ref-returns.md) (`T` 是集合元素類型的 `ref T`)，您可以使用 `ref` 或 `ref readonly` 修飾詞宣告反覆運算變數。 下列範例會使用 `ref` 反覆運算變數來設定 stackalloc 陣列中每個項目的值。 `ref readonly` 版本會逐一查看集合以列印所有值。 `readonly` 宣告會使用隱含的本機變數宣告。 您可以搭配使用隱含的變數宣告與 `ref` 或 `ref readonly` 宣告，也可以明確地鍵入變數宣告。

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [foreach 陳述式 (C# 語言規格)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)
- [搭配陣列使用 foreach](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [for](for.md)
- [反覆運算陳述式](iteration-statements.md)
- [C# 關鍵字](index.md)
- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
