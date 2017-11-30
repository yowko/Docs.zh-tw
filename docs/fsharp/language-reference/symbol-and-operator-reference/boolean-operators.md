---
title: "Boolean 運算子 (F#)"
description: "深入了解 F # 程式語言中可用的布林運算子。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a><span data-ttu-id="51b89-104">Boolean 運算子</span><span class="sxs-lookup"><span data-stu-id="51b89-104">Boolean Operators</span></span>

<span data-ttu-id="51b89-105">本主題說明在 F # 語言中布林運算子的支援。</span><span class="sxs-lookup"><span data-stu-id="51b89-105">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="51b89-106">布林運算子的摘要</span><span class="sxs-lookup"><span data-stu-id="51b89-106">Summary of Boolean Operators</span></span>
<span data-ttu-id="51b89-107">下表摘要說明在 F # 語言中使用布林運算子。</span><span class="sxs-lookup"><span data-stu-id="51b89-107">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="51b89-108">唯一支援的這些運算子的類型是`bool`型別。</span><span class="sxs-lookup"><span data-stu-id="51b89-108">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="51b89-109">運算子</span><span class="sxs-lookup"><span data-stu-id="51b89-109">Operator</span></span>|<span data-ttu-id="51b89-110">說明</span><span class="sxs-lookup"><span data-stu-id="51b89-110">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="51b89-111">布林值的否定</span><span class="sxs-lookup"><span data-stu-id="51b89-111">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="51b89-112">布林值 OR</span><span class="sxs-lookup"><span data-stu-id="51b89-112">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="51b89-113">布林值 AND</span><span class="sxs-lookup"><span data-stu-id="51b89-113">Boolean AND</span></span>|

<span data-ttu-id="51b89-114">布林值 AND 和 OR 運算子執行*最短路徑評估*，也就是評估運算子的右運算式只在必要時若要判斷整體運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="51b89-114">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="51b89-115">第二個運算式的`&&`運算子會評估，只有第一個運算式評估為`true`; 的第二個運算式`||`運算子會評估，只有第一個運算式評估為`false`。</span><span class="sxs-lookup"><span data-stu-id="51b89-115">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="51b89-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51b89-116">See Also</span></span>
[<span data-ttu-id="51b89-117">位元運算子</span><span class="sxs-lookup"><span data-stu-id="51b89-117">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="51b89-118">算術運算子</span><span class="sxs-lookup"><span data-stu-id="51b89-118">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="51b89-119">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="51b89-119">Symbol and Operator Reference</span></span>](index.md)
