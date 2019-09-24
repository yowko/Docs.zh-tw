---
title: 迴圈：while...do 運算式
description: 查看 while .。。當指定的測試條件為 true 時，會使用 do expression 來執行反復執行（迴圈）。
ms.date: 05/16/2016
ms.openlocfilehash: 73526279358db101f8d07721a200920f1e87f119
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216630"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="62fc0-103">迴圈：while...do 運算式</span><span class="sxs-lookup"><span data-stu-id="62fc0-103">Loops: while...do Expression</span></span>

<span data-ttu-id="62fc0-104">當`while...do`指定的測試條件為 true 時，會使用運算式來執行反復執行（迴圈）。</span><span class="sxs-lookup"><span data-stu-id="62fc0-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="62fc0-105">語法</span><span class="sxs-lookup"><span data-stu-id="62fc0-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="62fc0-106">備註</span><span class="sxs-lookup"><span data-stu-id="62fc0-106">Remarks</span></span>

<span data-ttu-id="62fc0-107">*測試運算式*會進行評估;如果為`true`，則會執行本文*運算式*，並再次評估測試運算式。</span><span class="sxs-lookup"><span data-stu-id="62fc0-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="62fc0-108">內文*運算式*的類型`unit`必須是。</span><span class="sxs-lookup"><span data-stu-id="62fc0-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="62fc0-109">如果測試運算式為， `false`則反復專案會結束。</span><span class="sxs-lookup"><span data-stu-id="62fc0-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="62fc0-110">下列範例說明`while...do`運算式的用法。</span><span class="sxs-lookup"><span data-stu-id="62fc0-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="62fc0-111">先前程式碼的輸出是介於1到20之間的亂數字資料流程，最後一個是10。</span><span class="sxs-lookup"><span data-stu-id="62fc0-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```console
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="62fc0-112">您可以在`while...do`序列運算式和其他計算運算式中使用，在此情況下會使用自`while...do`定義版本的運算式。</span><span class="sxs-lookup"><span data-stu-id="62fc0-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="62fc0-113">如需詳細資訊，請參閱[序列](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="62fc0-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62fc0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62fc0-114">See also</span></span>

- [<span data-ttu-id="62fc0-115">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="62fc0-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="62fc0-116">環回`for...in`運算式</span><span class="sxs-lookup"><span data-stu-id="62fc0-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="62fc0-117">環回`for...to`運算式</span><span class="sxs-lookup"><span data-stu-id="62fc0-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
