---
title: C# 運算式 - C# 語言教學課程
description: 運算式、運算元及運算子是 C# 語言的建置組塊
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 2553730d495942730c53d3646f35e80759a4d168
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609324"
---
# <a name="expressions"></a><span data-ttu-id="9c5e9-103">運算式</span><span class="sxs-lookup"><span data-stu-id="9c5e9-103">Expressions</span></span>

<span data-ttu-id="9c5e9-104">「運算式」  是由「運算元」  和「運算子」  建構而成。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="9c5e9-105">運算式的運算子會指出要將哪些運算套用到運算元。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="9c5e9-106">運算子範例包括 `+`、`-`、`*`、`/` 及 `new`。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="9c5e9-107">運算元範例包括常值、欄位、區域變數及運算式。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="9c5e9-108">當運算式包含多個運算子時，運算子的「優先順序」  會控制評估個別運算子的順序。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="9c5e9-109">例如，運算式 `x + y * z` 會評估為 `x + (y * z)`，因為 `*` 運算子的優先順序高於 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="9c5e9-110">當兩個優先順序相同的運算子之間有運算元時，運算子的「關聯性」  會控制執行運算的順序：</span><span class="sxs-lookup"><span data-stu-id="9c5e9-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="9c5e9-111">除了指派運算子之外，所有二元運算子都具有「左關聯性」  ，亦即會由左到右執行運算。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="9c5e9-112">例如，`x + y + z` 會判斷值為 `(x + y) + z`。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="9c5e9-113">指派運算子和條件運算子 (`?:`) 具有「右關聯性」  ，亦即會由右到左執行運算。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="9c5e9-114">例如，`x = y = z` 會判斷值為 `x = (y = z)`。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="9c5e9-115">您可以使用括弧來控制優先順序和關聯性。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="9c5e9-116">例如，`x + y * z` 會先將 `y` 乘以 `z`，然後再將結果加到 `x`，而 `(x + y) * z` 則會先將 `x` 與 `y` 相加，然後再將結果乘以 `z`。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="9c5e9-117">大部分的運算子都可以[「多載」  ](../language-reference/operators/operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-117">Most operators can be [*overloaded*](../language-reference/operators/operator-overloading.md).</span></span> <span data-ttu-id="9c5e9-118">運算子多載可允許針對一個運算元屬於 (或兩個運算元都屬於) 使用者定義之類別或結構型別的運算式，指定使用者定義的運算子實作。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="9c5e9-119">C# 提供數個運算子，用於執行[算術](../language-reference/operators/arithmetic-operators.md)、[邏輯](../language-reference/operators/boolean-logical-operators.md)、[位元和移位](../language-reference/operators/bitwise-and-shift-operators.md)作業以及[相等](../language-reference/operators/equality-operators.md)和[順序](../language-reference/operators/comparison-operators.md)比較。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-119">C# provides a number of operators to perform [arithmetic](../language-reference/operators/arithmetic-operators.md), [logical](../language-reference/operators/boolean-logical-operators.md), [bitwise and shift](../language-reference/operators/bitwise-and-shift-operators.md) operations and [equality](../language-reference/operators/equality-operators.md) and [order](../language-reference/operators/comparison-operators.md) comparisons.</span></span>

<span data-ttu-id="9c5e9-120">如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](../language-reference/operators/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9c5e9-120">For the complete list of C# operators ordered by precedence level, see [C# operators](../language-reference/operators/index.md).</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="9c5e9-121">[上一頁](types-and-variables.md)
> [下一頁](statements.md)</span><span class="sxs-lookup"><span data-stu-id="9c5e9-121">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
