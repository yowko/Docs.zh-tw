---
title: continue 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713666"
---
# <a name="continue-c-reference"></a>continue (C# 參考)

`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](./while.md)、[do](./do.md)、[for](./for.md) 或 [foreach](./foreach-in.md) 陳述式的下一個反覆項目。

## <a name="example"></a>範例

在此範例中，計數器會初始化為從 1 計算到 10。 搭配使用 `continue` 陳述式與 `(i < 9)` 運算式，會略過 `continue` 與 `for` 主體結尾之間的陳述式。

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](./index.md)
- [中斷語句](/cpp/cpp/break-statement-cpp)
