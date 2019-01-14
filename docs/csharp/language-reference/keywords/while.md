---
title: while - C# 參考
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 6e485bc80a213be6a5d0da8a00c8ca718f867efb
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222932"
---
# <a name="while-c-reference"></a>while (C# 參考)

當指定的布林運算式評估為 `true` 時，`while` 陳述式會執行某個陳述式或陳述式區塊。 運算式是在每次執行迴圈之前評估，因此 `while` 迴圈會執行零次以上。 這與 [do](do.md) 迴圈不同，此迴圈會執行一次或多次。

您可以使用 [break](break.md) 陳述式在 `while` 陳述式區塊的任一點中斷迴圈。

您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。 如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。 否則會在迴圈之後的第一個陳述式繼續執行。

您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `while` 迴圈。

## <a name="example"></a>範例

下列範例會示範 `while` 陳述式的用法。 選取 [執行] 執行範例程式碼。 之後，您可以修改程式碼，然後再次執行它。

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [while 陳述式](~/_csharplang/spec/statements.md#the-while-statement)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [反覆運算陳述式](iteration-statements.md)
- [do 陳述式](do.md)