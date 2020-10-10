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
# <a name="continue-c-reference"></a><span data-ttu-id="85653-103">continue (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="85653-103">continue (C# Reference)</span></span>

<span data-ttu-id="85653-104">`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](./while.md)、[do](./do.md)、[for](./for.md) 或 [foreach](./foreach-in.md) 陳述式的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="85653-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="85653-105">範例</span><span class="sxs-lookup"><span data-stu-id="85653-105">Example</span></span>

<span data-ttu-id="85653-106">在此範例中，計數器會初始化為從 1 計算到 10。</span><span class="sxs-lookup"><span data-stu-id="85653-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="85653-107">藉由 `continue` 搭配使用語句與運算式 `(i < 9)` ，就會 `continue` `for` 在小於9的反覆運算中略過和主體結尾的語句 `i` 。</span><span class="sxs-lookup"><span data-stu-id="85653-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped in the iterations where `i` is less than 9.</span></span> <span data-ttu-id="85653-108">在迴圈的最後兩個反覆運算 `for` (其中 i = = 9 和 i = = 10) ， `continue` 不會執行語句，而且的值 `i` 會列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="85653-108">In the last two iterations of the `for` loop (where i == 9 and i == 10), the `continue` statement is not executed and the value of `i` is printed to the console.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="85653-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="85653-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="85653-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85653-110">See also</span></span>

- [<span data-ttu-id="85653-111">C # 參考</span><span class="sxs-lookup"><span data-stu-id="85653-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="85653-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="85653-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="85653-113">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="85653-113">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="85653-114">break 語句</span><span class="sxs-lookup"><span data-stu-id="85653-114">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
