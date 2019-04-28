---
title: Boolean 運算子
description: 深入了解可用於布林運算子F#程式設計語言。
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925810"
---
# <a name="boolean-operators"></a><span data-ttu-id="1176f-103">Boolean 運算子</span><span class="sxs-lookup"><span data-stu-id="1176f-103">Boolean Operators</span></span>

<span data-ttu-id="1176f-104">本主題說明中的布林運算子的支援F#語言。</span><span class="sxs-lookup"><span data-stu-id="1176f-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="1176f-105">布林運算子的摘要</span><span class="sxs-lookup"><span data-stu-id="1176f-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="1176f-106">下表摘要說明可用於布林運算子F#語言。</span><span class="sxs-lookup"><span data-stu-id="1176f-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="1176f-107">唯一支援這些運算子的類型是`bool`型別。</span><span class="sxs-lookup"><span data-stu-id="1176f-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="1176f-108">運算子</span><span class="sxs-lookup"><span data-stu-id="1176f-108">Operator</span></span>|<span data-ttu-id="1176f-109">描述</span><span class="sxs-lookup"><span data-stu-id="1176f-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="1176f-110">布林值的否定運算</span><span class="sxs-lookup"><span data-stu-id="1176f-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="1176f-111">布林值 OR</span><span class="sxs-lookup"><span data-stu-id="1176f-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="1176f-112">布林值 AND</span><span class="sxs-lookup"><span data-stu-id="1176f-112">Boolean AND</span></span>|

<span data-ttu-id="1176f-113">布林值 AND 和 OR 運算子執行*最少運算評估*，也就是它們評估運算式運算子的右側時才需要判斷整體運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="1176f-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="1176f-114">第二個運算式`&&`運算子會評估第一個運算式評估為時，才`true`; 的第二個運算式`||`運算子會評估，只有第一個運算式評估為`false`。</span><span class="sxs-lookup"><span data-stu-id="1176f-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1176f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1176f-115">See also</span></span>

- [<span data-ttu-id="1176f-116">位元運算子</span><span class="sxs-lookup"><span data-stu-id="1176f-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="1176f-117">算術運算子</span><span class="sxs-lookup"><span data-stu-id="1176f-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="1176f-118">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="1176f-118">Symbol and Operator Reference</span></span>](index.md)