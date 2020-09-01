---
description: break 陳述式 - C# 參考
title: break 陳述式 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134740"
---
# <a name="break-c-reference"></a><span data-ttu-id="b6160-103">break (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b6160-103">break (C# Reference)</span></span>

<span data-ttu-id="b6160-104">`break` 陳述式會終止其所在的最接近封閉式迴圈或 [switch](./switch.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b6160-104">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="b6160-105">控制權會轉移到已終止陳述式之後的陳述式 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="b6160-105">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="b6160-106">範例</span><span class="sxs-lookup"><span data-stu-id="b6160-106">Example</span></span>

<span data-ttu-id="b6160-107">在此範例中，條件式陳述式包含假設從 1 計算到 100 的計數器；不過，`break` 陳述式會在計算 4 次之後終止迴圈。</span><span class="sxs-lookup"><span data-stu-id="b6160-107">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="b6160-108">範例</span><span class="sxs-lookup"><span data-stu-id="b6160-108">Example</span></span>

<span data-ttu-id="b6160-109">這個範例示範如何在 [switch](./switch.md) 陳述式中使用 `break`。</span><span class="sxs-lookup"><span data-stu-id="b6160-109">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="b6160-110">如果您已輸入 `4`，則輸出會是︰</span><span class="sxs-lookup"><span data-stu-id="b6160-110">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="b6160-111">範例</span><span class="sxs-lookup"><span data-stu-id="b6160-111">Example</span></span>

<span data-ttu-id="b6160-112">在此範例中，`break` 陳述式是用來破壞內部巢狀迴圈，並將控制權返回外部迴圈。</span><span class="sxs-lookup"><span data-stu-id="b6160-112">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="b6160-113">在嵌套的迴圈中， _只_ 會傳回一個層級給控制項。</span><span class="sxs-lookup"><span data-stu-id="b6160-113">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="b6160-114">範例</span><span class="sxs-lookup"><span data-stu-id="b6160-114">Example</span></span>

<span data-ttu-id="b6160-115">在此範例中， `break` 語句只會在迴圈的每次反覆運算期間用來中斷目前的分支。</span><span class="sxs-lookup"><span data-stu-id="b6160-115">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="b6160-116">迴圈本身不會受到 `break` 屬於 nested [switch](./switch.md) 語句之實例的影響。</span><span class="sxs-lookup"><span data-stu-id="b6160-116">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="b6160-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b6160-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b6160-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6160-118">See also</span></span>

- [<span data-ttu-id="b6160-119">C # 參考</span><span class="sxs-lookup"><span data-stu-id="b6160-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b6160-120">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b6160-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b6160-121">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b6160-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b6160-122">switch</span><span class="sxs-lookup"><span data-stu-id="b6160-122">switch</span></span>](./switch.md)
