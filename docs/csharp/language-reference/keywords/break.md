---
title: break 陳述式 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 18be5171329dd43c419e977a1799e2e72c32404d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727569"
---
# <a name="break-c-reference"></a><span data-ttu-id="d32d0-102">break (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d32d0-102">break (C# Reference)</span></span>

<span data-ttu-id="d32d0-103">`break` 陳述式會終止其所在的最接近封閉式迴圈或 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d32d0-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="d32d0-104">控制權會轉移到已終止陳述式之後的陳述式 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="d32d0-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="d32d0-105">範例</span><span class="sxs-lookup"><span data-stu-id="d32d0-105">Example</span></span>

<span data-ttu-id="d32d0-106">在此範例中，條件式陳述式包含假設從 1 計算到 100 的計數器；不過，`break` 陳述式會在計算 4 次之後終止迴圈。</span><span class="sxs-lookup"><span data-stu-id="d32d0-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="d32d0-107">範例</span><span class="sxs-lookup"><span data-stu-id="d32d0-107">Example</span></span>

<span data-ttu-id="d32d0-108">在此範例中，`break` 陳述式是用來破壞內部巢狀迴圈，並將控制權返回外部迴圈。</span><span class="sxs-lookup"><span data-stu-id="d32d0-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="d32d0-109">範例</span><span class="sxs-lookup"><span data-stu-id="d32d0-109">Example</span></span>

<span data-ttu-id="d32d0-110">這個範例示範如何在 [switch](../../../csharp/language-reference/keywords/switch.md) 陳述式中使用 `break`。</span><span class="sxs-lookup"><span data-stu-id="d32d0-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="d32d0-111">如果您已輸入 `4`，則輸出會是︰</span><span class="sxs-lookup"><span data-stu-id="d32d0-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="d32d0-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d32d0-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d32d0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d32d0-113">See also</span></span>

- [<span data-ttu-id="d32d0-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d32d0-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d32d0-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d32d0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d32d0-116">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d32d0-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="d32d0-117">switch</span><span class="sxs-lookup"><span data-stu-id="d32d0-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
- [<span data-ttu-id="d32d0-118">跳躍陳述式</span><span class="sxs-lookup"><span data-stu-id="d32d0-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
- [<span data-ttu-id="d32d0-119">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="d32d0-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
