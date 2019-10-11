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
ms.openlocfilehash: 2628da73364cf94a52e2862d349243c100d4afaf
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179927"
---
# <a name="break-c-reference"></a><span data-ttu-id="c5188-102">break (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c5188-102">break (C# Reference)</span></span>

<span data-ttu-id="c5188-103">`break` 陳述式會終止其所在的最接近封閉式迴圈或 [switch](./switch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c5188-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="c5188-104">控制權會轉移到已終止陳述式之後的陳述式 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="c5188-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="c5188-105">範例</span><span class="sxs-lookup"><span data-stu-id="c5188-105">Example</span></span>

<span data-ttu-id="c5188-106">在此範例中，條件式陳述式包含假設從 1 計算到 100 的計數器；不過，`break` 陳述式會在計算 4 次之後終止迴圈。</span><span class="sxs-lookup"><span data-stu-id="c5188-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="c5188-107">範例</span><span class="sxs-lookup"><span data-stu-id="c5188-107">Example</span></span>

<span data-ttu-id="c5188-108">這個範例示範如何在 [switch](./switch.md) 陳述式中使用 `break`。</span><span class="sxs-lookup"><span data-stu-id="c5188-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="c5188-109">如果您已輸入 `4`，則輸出會是︰</span><span class="sxs-lookup"><span data-stu-id="c5188-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="c5188-110">範例</span><span class="sxs-lookup"><span data-stu-id="c5188-110">Example</span></span>

<span data-ttu-id="c5188-111">在此範例中，`break` 陳述式是用來破壞內部巢狀迴圈，並將控制權返回外部迴圈。</span><span class="sxs-lookup"><span data-stu-id="c5188-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="c5188-112">控制項_只_會在嵌套迴圈中傳回一個層級。</span><span class="sxs-lookup"><span data-stu-id="c5188-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="c5188-113">範例</span><span class="sxs-lookup"><span data-stu-id="c5188-113">Example</span></span>

<span data-ttu-id="c5188-114">在此範例中，`break` 語句只會在迴圈的每個反覆運算期間用來中斷最新分支。</span><span class="sxs-lookup"><span data-stu-id="c5188-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="c5188-115">迴圈本身不會受到屬於嵌套[switch](./switch.md)語句之 @no__t 0 的實例所影響。</span><span class="sxs-lookup"><span data-stu-id="c5188-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="c5188-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c5188-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c5188-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5188-117">See also</span></span>

- [<span data-ttu-id="c5188-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c5188-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5188-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c5188-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c5188-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c5188-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c5188-121">switch</span><span class="sxs-lookup"><span data-stu-id="c5188-121">switch</span></span>](./switch.md)
