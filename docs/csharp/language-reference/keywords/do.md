---
title: do - C# 參考
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 4bdbd1c8efac0b7ba95d4c8d16dae3101fe6bcb0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239536"
---
# <a name="do-c-reference"></a>do (C# 參考)

當指定的布林運算式評估為 `true` 時，`do` 陳述式會執行某個陳述式或陳述式區塊。 運算式是在每次執行迴圈之後評估，因此 `do-while` 迴圈會執行一次以上。 這與 [while](while.md) 迴圈不同，此迴圈會執行零次以上。

您可以使用 [break](break.md) 陳述式在 `do` 陳述式區塊的任一點中斷迴圈。

您可以使用 [continue](continue.md) 陳述式直接逐步執行 `while` 運算式評估。 如果運算式評估為 `true`，即繼續執行迴圈中的第一個陳述式。 否則會在迴圈之後的第一個陳述式繼續執行。

您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `do-while` 迴圈。

## <a name="example"></a>範例

下列範例會示範 `do` 陳述式的用法。 選取 [執行] 執行範例程式碼。 之後，您可以修改程式碼，然後再次執行它。

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [do 陳述式](~/_csharplang/spec/statements.md#the-do-statement)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [反覆運算陳述式](iteration-statements.md)
- [while 陳述式](while.md)
