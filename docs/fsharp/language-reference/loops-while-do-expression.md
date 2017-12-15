---
title: "迴圈：while...do 運算式 (F#)"
description: "請參閱如何時...執行運算式用來執行 （迴圈） 的反覆執行，而指定的測試條件為 true。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 5f10fda84a5e748856eb7b2c63ad46cc1fba44bb
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="e4ff6-104">迴圈：while...do 運算式</span><span class="sxs-lookup"><span data-stu-id="e4ff6-104">Loops: while...do Expression</span></span>

<span data-ttu-id="e4ff6-105">`while...do`運算式用來執行 （迴圈） 的反覆執行，而指定的測試條件為 true。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-105">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="e4ff6-106">語法</span><span class="sxs-lookup"><span data-stu-id="e4ff6-106">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="e4ff6-107">備註</span><span class="sxs-lookup"><span data-stu-id="e4ff6-107">Remarks</span></span>
<span data-ttu-id="e4ff6-108">*測試運算式*評估; 如果它是`true`、*主體運算式*執行和測試運算式會評估一次。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-108">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="e4ff6-109">*主體運算式*型別必須`unit`。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-109">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="e4ff6-110">如果測試運算式`false`，在反覆項目結束。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-110">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="e4ff6-111">下列範例說明使用`while...do`運算式。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-111">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="e4ff6-112">先前的程式碼的輸出是介於 1 到 20 之間的隨機數字的資料流的最後一個為 10。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-112">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="e4ff6-113">您可以使用`while...do`在循序項運算式和其他計算的運算式，在此情況下的自訂的版本`while...do`運算式使用。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-113">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="e4ff6-114">如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e4ff6-114">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="e4ff6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4ff6-115">See Also</span></span>
[<span data-ttu-id="e4ff6-116">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e4ff6-116">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e4ff6-117">迴圈：`for...in` 運算式</span><span class="sxs-lookup"><span data-stu-id="e4ff6-117">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="e4ff6-118">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="e4ff6-118">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
