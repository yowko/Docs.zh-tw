---
description: continue 陳述式 - C# 參考
title: continue 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 6c70934c3b861e1a1433e5c0b95bb32e9d717c53
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877648"
---
# <a name="continue-c-reference"></a>continue (C# 參考)

`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](./while.md)、[do](./do.md)、[for](./for.md) 或 [foreach](./foreach-in.md) 陳述式的下一個反覆項目。

## <a name="example"></a>範例

在此範例中，計數器會初始化為從 1 計算到 10。 藉由 `continue` 搭配使用語句與運算式 `(i < 9)` ，就會 `continue` `for` 在小於9的反覆運算中略過和主體結尾的語句 `i` 。 在迴圈的最後兩個反覆運算 `for` (其中 i = = 9 和 i = = 10) ， `continue` 不會執行語句，而且的值 `i` 會列印至主控台。

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](./index.md)
- [break 語句](/cpp/cpp/break-statement-cpp)
