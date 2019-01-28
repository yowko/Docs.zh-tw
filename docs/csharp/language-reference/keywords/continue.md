---
title: continue 陳述式 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 0b3baf6eb4843ff67a3d76af06ca86ca9ec2db03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690588"
---
# <a name="continue-c-reference"></a><span data-ttu-id="565c3-102">continue (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="565c3-102">continue (C# Reference)</span></span>

<span data-ttu-id="565c3-103">`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](../../../csharp/language-reference/keywords/while.md)、[do](../../../csharp/language-reference/keywords/do.md)、[for](../../../csharp/language-reference/keywords/for.md) 或 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="565c3-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="565c3-104">範例</span><span class="sxs-lookup"><span data-stu-id="565c3-104">Example</span></span>

<span data-ttu-id="565c3-105">在此範例中，計數器會初始化為從 1 計算到 10。</span><span class="sxs-lookup"><span data-stu-id="565c3-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="565c3-106">搭配使用 `continue` 陳述式與 `(i < 9)` 運算式，會略過 `continue` 與 `for` 主體結尾之間的陳述式。</span><span class="sxs-lookup"><span data-stu-id="565c3-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="565c3-107">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="565c3-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="565c3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="565c3-108">See also</span></span>

- [<span data-ttu-id="565c3-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="565c3-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="565c3-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="565c3-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="565c3-111">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="565c3-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="565c3-112">break 陳述式</span><span class="sxs-lookup"><span data-stu-id="565c3-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
- [<span data-ttu-id="565c3-113">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="565c3-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
