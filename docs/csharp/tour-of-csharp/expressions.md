---
title: C# 運算式 - C# 語言教學課程
description: 運算式、運算元及運算子是 C# 語言的構成要素
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 682f98d51bf4eb3c1641297972afb86956e06d3e
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212088"
---
# <a name="expressions"></a><span data-ttu-id="72c5c-103">運算式</span><span class="sxs-lookup"><span data-stu-id="72c5c-103">Expressions</span></span>

<span data-ttu-id="72c5c-104">「運算式」是由「運算元」和「運算子」建構而成。</span><span class="sxs-lookup"><span data-stu-id="72c5c-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="72c5c-105">運算式的運算子會指出要將哪些運算套用到運算元。</span><span class="sxs-lookup"><span data-stu-id="72c5c-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="72c5c-106">運算子範例包括 `+`、`-`、`*`、`/` 及 `new`。</span><span class="sxs-lookup"><span data-stu-id="72c5c-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="72c5c-107">運算元範例包括常值、欄位、區域變數及運算式。</span><span class="sxs-lookup"><span data-stu-id="72c5c-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="72c5c-108">當運算式包含多個運算子時，運算子的「優先順序」會控制評估個別運算子的順序。</span><span class="sxs-lookup"><span data-stu-id="72c5c-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="72c5c-109">例如，運算式 `x + y * z` 會評估為 `x + (y * z)`，因為 `*` 運算子的優先順序高於 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="72c5c-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="72c5c-110">當兩個優先順序相同的運算子之間有運算元時，運算子的「關聯性」會控制執行運算的順序：</span><span class="sxs-lookup"><span data-stu-id="72c5c-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="72c5c-111">除了指派運算子之外，所有二元運算子都具有「左關聯性」，亦即會由左到右執行運算。</span><span class="sxs-lookup"><span data-stu-id="72c5c-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="72c5c-112">例如，`x + y + z` 會判斷值為 `(x + y) + z`。</span><span class="sxs-lookup"><span data-stu-id="72c5c-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="72c5c-113">指派運算子和條件運算子 (`?:`) 具有「右關聯性」，亦即會由右到左執行運算。</span><span class="sxs-lookup"><span data-stu-id="72c5c-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="72c5c-114">例如，`x = y = z` 會判斷值為 `x = (y = z)`。</span><span class="sxs-lookup"><span data-stu-id="72c5c-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="72c5c-115">您可以使用括弧來控制優先順序和關聯性。</span><span class="sxs-lookup"><span data-stu-id="72c5c-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="72c5c-116">例如，`x + y * z` 會先將 `y` 乘以 `z`，然後再將結果加到 `x`，而 `(x + y) * z` 則會先將 `x` 與 `y` 相加，然後再將結果乘以 `z`。</span><span class="sxs-lookup"><span data-stu-id="72c5c-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="72c5c-117">大多數運算子都是可以「多載」的運算子。</span><span class="sxs-lookup"><span data-stu-id="72c5c-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="72c5c-118">運算子多載可允許針對一個運算元屬於 (或兩個運算元都屬於) 使用者定義之類別或結構型別的運算式，指定使用者定義的運算子實作。</span><span class="sxs-lookup"><span data-stu-id="72c5c-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="72c5c-119">以下摘要說明 C# 運算子，其中依優先順序從最高到最低列出運算子分類。</span><span class="sxs-lookup"><span data-stu-id="72c5c-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="72c5c-120">相同分類中的運算子具有相等的優先順序。</span><span class="sxs-lookup"><span data-stu-id="72c5c-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="72c5c-121">每個分類底下是該分類中的運算式清單，以及該運算式型別的描述。</span><span class="sxs-lookup"><span data-stu-id="72c5c-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="72c5c-122">主要</span><span class="sxs-lookup"><span data-stu-id="72c5c-122">Primary</span></span>
    - <span data-ttu-id="72c5c-123">`x.m`：成員存取</span><span class="sxs-lookup"><span data-stu-id="72c5c-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="72c5c-124">`x(...)`：方法和委派叫用</span><span class="sxs-lookup"><span data-stu-id="72c5c-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="72c5c-125">`x[...]`：陣列和索引子存取</span><span class="sxs-lookup"><span data-stu-id="72c5c-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="72c5c-126">`x++`：後置遞增</span><span class="sxs-lookup"><span data-stu-id="72c5c-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="72c5c-127">`x--`：後置遞減</span><span class="sxs-lookup"><span data-stu-id="72c5c-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="72c5c-128">`new T(...)`：建立物件和委派</span><span class="sxs-lookup"><span data-stu-id="72c5c-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="72c5c-129">`new T(...){...}`：使用初始設定式來建立物件</span><span class="sxs-lookup"><span data-stu-id="72c5c-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="72c5c-130">`new {...}`：匿名物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="72c5c-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="72c5c-131">`new T[...]`：建立陣列</span><span class="sxs-lookup"><span data-stu-id="72c5c-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="72c5c-132">`typeof(T)`：取得 `T` 的 <xref:System.Type> 物件</span><span class="sxs-lookup"><span data-stu-id="72c5c-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="72c5c-133">`checked(x)`：在核取的內容中評估運算式</span><span class="sxs-lookup"><span data-stu-id="72c5c-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="72c5c-134">`unchecked(x)`：在未核取的內容中評估運算式</span><span class="sxs-lookup"><span data-stu-id="72c5c-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="72c5c-135">`default(T)`：取得類型 `T` 的預設值</span><span class="sxs-lookup"><span data-stu-id="72c5c-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="72c5c-136">`delegate {...}`：匿名函式 (匿名方法)</span><span class="sxs-lookup"><span data-stu-id="72c5c-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="72c5c-137">一元</span><span class="sxs-lookup"><span data-stu-id="72c5c-137">Unary</span></span>
    - <span data-ttu-id="72c5c-138">`+x`：身分識別</span><span class="sxs-lookup"><span data-stu-id="72c5c-138">`+x`: Identity</span></span>
    - <span data-ttu-id="72c5c-139">`-x`：否定</span><span class="sxs-lookup"><span data-stu-id="72c5c-139">`-x`: Negation</span></span>
    - <span data-ttu-id="72c5c-140">`!x`：邏輯否定</span><span class="sxs-lookup"><span data-stu-id="72c5c-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="72c5c-141">`~x`：位元否定</span><span class="sxs-lookup"><span data-stu-id="72c5c-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="72c5c-142">`++x`：前置遞增</span><span class="sxs-lookup"><span data-stu-id="72c5c-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="72c5c-143">`--x`：前置遞減</span><span class="sxs-lookup"><span data-stu-id="72c5c-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="72c5c-144">`(T)x`：將 `x` 明確轉換成類型 `T`</span><span class="sxs-lookup"><span data-stu-id="72c5c-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="72c5c-145">`await x`：以非同步方式等候 `x` 完成</span><span class="sxs-lookup"><span data-stu-id="72c5c-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="72c5c-146">乘法類 (Multiplicative)</span><span class="sxs-lookup"><span data-stu-id="72c5c-146">Multiplicative</span></span>
    - <span data-ttu-id="72c5c-147">`x * y`：乘法</span><span class="sxs-lookup"><span data-stu-id="72c5c-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="72c5c-148">`x / y`：除號</span><span class="sxs-lookup"><span data-stu-id="72c5c-148">`x / y`: Division</span></span>
    - <span data-ttu-id="72c5c-149">`x % y`：餘數</span><span class="sxs-lookup"><span data-stu-id="72c5c-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="72c5c-150">加法類 (Additive)</span><span class="sxs-lookup"><span data-stu-id="72c5c-150">Additive</span></span>
    - <span data-ttu-id="72c5c-151">`x + y`：加法、字串串連、委派組合</span><span class="sxs-lookup"><span data-stu-id="72c5c-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="72c5c-152">`x – y`：減法、委派移除</span><span class="sxs-lookup"><span data-stu-id="72c5c-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="72c5c-153">Shift</span><span class="sxs-lookup"><span data-stu-id="72c5c-153">Shift</span></span>
    - <span data-ttu-id="72c5c-154">`x << y`：左移</span><span class="sxs-lookup"><span data-stu-id="72c5c-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="72c5c-155">`x >> y`：右移</span><span class="sxs-lookup"><span data-stu-id="72c5c-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="72c5c-156">關係和型別測試</span><span class="sxs-lookup"><span data-stu-id="72c5c-156">Relational and type testing</span></span>
    - <span data-ttu-id="72c5c-157">`x < y`：小於</span><span class="sxs-lookup"><span data-stu-id="72c5c-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="72c5c-158">`x > y`：大於</span><span class="sxs-lookup"><span data-stu-id="72c5c-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="72c5c-159">`x <= y`：小於或等於</span><span class="sxs-lookup"><span data-stu-id="72c5c-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="72c5c-160">`x >= y`：大於或等於</span><span class="sxs-lookup"><span data-stu-id="72c5c-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="72c5c-161">`x is T`：如果 `x` 是 `T`，便傳回 `true`，否則傳回 `false`</span><span class="sxs-lookup"><span data-stu-id="72c5c-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="72c5c-162">`x as T`：傳回歸類為 `T` 類型的 `x`，或在 `x` 不是 `T` 的情況下傳回 `null`</span><span class="sxs-lookup"><span data-stu-id="72c5c-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="72c5c-163">相等</span><span class="sxs-lookup"><span data-stu-id="72c5c-163">Equality</span></span>
    - <span data-ttu-id="72c5c-164">`x == y`：等於</span><span class="sxs-lookup"><span data-stu-id="72c5c-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="72c5c-165">`x != y`：不等於</span><span class="sxs-lookup"><span data-stu-id="72c5c-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="72c5c-166">邏輯 AND</span><span class="sxs-lookup"><span data-stu-id="72c5c-166">Logical AND</span></span>
    - <span data-ttu-id="72c5c-167">`x & y`：整數位元 AND、布林邏輯 AND</span><span class="sxs-lookup"><span data-stu-id="72c5c-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="72c5c-168">邏輯 XOR</span><span class="sxs-lookup"><span data-stu-id="72c5c-168">Logical XOR</span></span>
    - <span data-ttu-id="72c5c-169">`x ^ y`：整數位元 XOR、布林邏輯 XOR</span><span class="sxs-lookup"><span data-stu-id="72c5c-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="72c5c-170">邏輯 OR</span><span class="sxs-lookup"><span data-stu-id="72c5c-170">Logical OR</span></span>
    - <span data-ttu-id="72c5c-171">`x | y`：整數位元 OR、布林邏輯 OR</span><span class="sxs-lookup"><span data-stu-id="72c5c-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="72c5c-172">條件式 AND</span><span class="sxs-lookup"><span data-stu-id="72c5c-172">Conditional AND</span></span>
    - <span data-ttu-id="72c5c-173">`x && y`：只有當 `x` 不是 `false` 時，才評估 `y`</span><span class="sxs-lookup"><span data-stu-id="72c5c-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="72c5c-174">條件式 OR</span><span class="sxs-lookup"><span data-stu-id="72c5c-174">Conditional OR</span></span>
    - <span data-ttu-id="72c5c-175">`x || y`：只有當 `x` 不是 `true` 時，才評估 `y`</span><span class="sxs-lookup"><span data-stu-id="72c5c-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="72c5c-176">Null 聯合</span><span class="sxs-lookup"><span data-stu-id="72c5c-176">Null coalescing</span></span>
    - <span data-ttu-id="72c5c-177">`x ?? y`：如果 `x` 是 null，便評估為 `y`，否則評估為 `x`</span><span class="sxs-lookup"><span data-stu-id="72c5c-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="72c5c-178">條件式</span><span class="sxs-lookup"><span data-stu-id="72c5c-178">Conditional</span></span>
    - <span data-ttu-id="72c5c-179">`x ? y : z`：如果 `x` 是 `true`，便評估 `y`，如果 `x` 是 `false`，則評估 `z`</span><span class="sxs-lookup"><span data-stu-id="72c5c-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="72c5c-180">指派或匿名函式</span><span class="sxs-lookup"><span data-stu-id="72c5c-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="72c5c-181">`x = y`：指派</span><span class="sxs-lookup"><span data-stu-id="72c5c-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="72c5c-182">`x op= y`：複合指派；支援的運算子包括</span><span class="sxs-lookup"><span data-stu-id="72c5c-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="72c5c-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="72c5c-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="72c5c-184">`(T x) => y`：匿名函式 (Lambda 運算式)</span><span class="sxs-lookup"><span data-stu-id="72c5c-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="72c5c-185">[上一頁](types-and-variables.md)
> [下一頁](statements.md)</span><span class="sxs-lookup"><span data-stu-id="72c5c-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>