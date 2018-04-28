---
title: Boolean 運算子 (F#)
description: '深入了解 F # 程式語言中可用的布林運算子。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0b11b5133b02b6f507c7886b2fbaebf30abf46cb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="boolean-operators"></a><span data-ttu-id="7a366-103">Boolean 運算子</span><span class="sxs-lookup"><span data-stu-id="7a366-103">Boolean Operators</span></span>

<span data-ttu-id="7a366-104">本主題說明在 F # 語言中布林運算子的支援。</span><span class="sxs-lookup"><span data-stu-id="7a366-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="7a366-105">布林運算子的摘要</span><span class="sxs-lookup"><span data-stu-id="7a366-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="7a366-106">下表摘要說明在 F # 語言中使用布林運算子。</span><span class="sxs-lookup"><span data-stu-id="7a366-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="7a366-107">唯一支援的這些運算子的類型是`bool`型別。</span><span class="sxs-lookup"><span data-stu-id="7a366-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="7a366-108">運算子</span><span class="sxs-lookup"><span data-stu-id="7a366-108">Operator</span></span>|<span data-ttu-id="7a366-109">描述</span><span class="sxs-lookup"><span data-stu-id="7a366-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="7a366-110">布林值的否定</span><span class="sxs-lookup"><span data-stu-id="7a366-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="7a366-111">布林值 OR</span><span class="sxs-lookup"><span data-stu-id="7a366-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="7a366-112">布林值 AND</span><span class="sxs-lookup"><span data-stu-id="7a366-112">Boolean AND</span></span>|

<span data-ttu-id="7a366-113">布林值 AND 和 OR 運算子執行*最短路徑評估*，也就是評估運算子的右運算式只在必要時若要判斷整體運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="7a366-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="7a366-114">第二個運算式的`&&`運算子會評估，只有第一個運算式評估為`true`; 的第二個運算式`||`運算子會評估，只有第一個運算式評估為`false`。</span><span class="sxs-lookup"><span data-stu-id="7a366-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a366-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a366-115">See Also</span></span>
[<span data-ttu-id="7a366-116">位元運算子</span><span class="sxs-lookup"><span data-stu-id="7a366-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="7a366-117">算術運算子</span><span class="sxs-lookup"><span data-stu-id="7a366-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="7a366-118">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="7a366-118">Symbol and Operator Reference</span></span>](index.md)
