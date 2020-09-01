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
ms.openlocfilehash: 76578b0ad7e2b969609fbf50df1f9ab7de6e5097
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128435"
---
# <a name="continue-c-reference"></a><span data-ttu-id="ab784-103">continue (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ab784-103">continue (C# Reference)</span></span>

<span data-ttu-id="ab784-104">`continue` 陳述式會將控制權轉移給其所在的封閉式 [while](./while.md)、[do](./do.md)、[for](./for.md) 或 [foreach](./foreach-in.md) 陳述式的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="ab784-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="ab784-105">範例</span><span class="sxs-lookup"><span data-stu-id="ab784-105">Example</span></span>

<span data-ttu-id="ab784-106">在此範例中，計數器會初始化為從 1 計算到 10。</span><span class="sxs-lookup"><span data-stu-id="ab784-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="ab784-107">搭配使用 `continue` 陳述式與 `(i < 9)` 運算式，會略過 `continue` 與 `for` 主體結尾之間的陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab784-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="ab784-108">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ab784-108">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ab784-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab784-109">See also</span></span>

- [<span data-ttu-id="ab784-110">C # 參考</span><span class="sxs-lookup"><span data-stu-id="ab784-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ab784-111">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ab784-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ab784-112">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ab784-112">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="ab784-113">break 語句</span><span class="sxs-lookup"><span data-stu-id="ab784-113">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
