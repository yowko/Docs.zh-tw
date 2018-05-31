---
title: foreach、in (C# 參考)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: b6b7dc0a4d3970ddfbbb6635ccebbbd5b75671e4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549372"
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# 參考)

`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。 `foreach` 陳述式不限於那些型別，並且適用於滿足下列條件的任何型別執行個體：

- 具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。
- `GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。

您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 關鍵字跳出迴圈，或使用 [continue](continue.md) 關鍵字逐步執行到迴圈中的下一個反覆運算。 您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `foreach` 迴圈。

## <a name="examples"></a>範例

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

[foreach 陳述式 (C# 語言規格)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[搭配陣列使用 foreach](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[反覆運算陳述式](iteration-statements.md)  
[C# 關鍵字](index.md)  
[C# 參考](../index.md)  
[C# 程式設計指南](../../programming-guide/index.md)  