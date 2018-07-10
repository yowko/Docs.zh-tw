---
title: continue 陳述式 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 6a409fe8c7fd07342138eac11bfd1766014da1bd
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948351"
---
# <a name="continue-c-reference"></a>continue (C# 參考)

`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](../../../csharp/language-reference/keywords/while.md)、[do](../../../csharp/language-reference/keywords/do.md)、[for](../../../csharp/language-reference/keywords/for.md) 或 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式的下一個反覆項目。

## <a name="example"></a>範例

在此範例中，計數器會初始化為從 1 計算到 10。 搭配使用 `continue` 陳述式與 `(i < 9)` 運算式，會略過 `continue` 與 `for` 主體結尾之間的陳述式。

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

[C# 參考](../../../csharp/language-reference/index.md)  
[C# 程式設計指南](../../../csharp/programming-guide/index.md)  
[C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
[break 陳述式](/cpp/cpp/break-statement-cpp)  
[跳躍陳述式](../../../csharp/language-reference/keywords/jump-statements.md)