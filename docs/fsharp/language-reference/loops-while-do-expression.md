---
title: 迴圈：while...do 運算式 (F#)
description: 請參閱如何時...執行運算式用來執行反覆執行 （迴圈），而指定的測試條件為 true。
ms.date: 05/16/2016
ms.openlocfilehash: 5cf4461669221f91cb50e238c25494f03a10bbc2
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44352553"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="d8f27-103">迴圈：while...do 運算式</span><span class="sxs-lookup"><span data-stu-id="d8f27-103">Loops: while...do Expression</span></span>

<span data-ttu-id="d8f27-104">`while...do`運算式用來執行反覆執行 （迴圈），而指定的測試條件為 true。</span><span class="sxs-lookup"><span data-stu-id="d8f27-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8f27-105">語法</span><span class="sxs-lookup"><span data-stu-id="d8f27-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="d8f27-106">備註</span><span class="sxs-lookup"><span data-stu-id="d8f27-106">Remarks</span></span>

<span data-ttu-id="d8f27-107">*測試運算式*評估; 如果`true`，則*主體運算式*執行和測試運算式會評估一次。</span><span class="sxs-lookup"><span data-stu-id="d8f27-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="d8f27-108">*主體運算式*型別必須`unit`。</span><span class="sxs-lookup"><span data-stu-id="d8f27-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="d8f27-109">如果測試運算式`false`，反覆項目結束。</span><span class="sxs-lookup"><span data-stu-id="d8f27-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="d8f27-110">下列範例示範如何將`while...do`運算式。</span><span class="sxs-lookup"><span data-stu-id="d8f27-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="d8f27-111">先前的程式碼的輸出是介於 1 到 20 之間的隨機數字的資料流的最後一個為 10。</span><span class="sxs-lookup"><span data-stu-id="d8f27-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE]
<span data-ttu-id="d8f27-112">您可以使用`while...do`循序項運算式和其他計算的運算式，在此情況下的自訂的版本`while...do`運算式的使用方式。</span><span class="sxs-lookup"><span data-stu-id="d8f27-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="d8f27-113">如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，並[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d8f27-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8f27-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8f27-114">See also</span></span>

- [<span data-ttu-id="d8f27-115">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="d8f27-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d8f27-116">迴圈：`for...in` 運算式</span><span class="sxs-lookup"><span data-stu-id="d8f27-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="d8f27-117">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="d8f27-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
