---
title: C# 運算式 - C# 語言教學課程
description: 運算式、運算元及運算子是 C# 語言的構成要素
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4ffe947a4cb8c36a5925a4b3846486e44a9d8ec4
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480751"
---
# <a name="expressions"></a><span data-ttu-id="226a6-103">運算式</span><span class="sxs-lookup"><span data-stu-id="226a6-103">Expressions</span></span>

<span data-ttu-id="226a6-104">「運算式」是由「運算元」和「運算子」建構而成。</span><span class="sxs-lookup"><span data-stu-id="226a6-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="226a6-105">運算式的運算子會指出要將哪些運算套用到運算元。</span><span class="sxs-lookup"><span data-stu-id="226a6-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="226a6-106">運算子範例包括 `+`、`-`、`*`、`/` 及 `new`。</span><span class="sxs-lookup"><span data-stu-id="226a6-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="226a6-107">運算元範例包括常值、欄位、區域變數及運算式。</span><span class="sxs-lookup"><span data-stu-id="226a6-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="226a6-108">當運算式包含多個運算子時，運算子的「優先順序」會控制評估個別運算子的順序。</span><span class="sxs-lookup"><span data-stu-id="226a6-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="226a6-109">例如，運算式 `x + y * z` 會評估為 `x + (y * z)`，因為 `*` 運算子的優先順序高於 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="226a6-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="226a6-110">當兩個優先順序相同的運算子之間有運算元時，運算子的「關聯性」會控制執行運算的順序：</span><span class="sxs-lookup"><span data-stu-id="226a6-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="226a6-111">除了指派運算子之外，所有二元運算子都具有「左關聯性」，亦即會由左到右執行運算。</span><span class="sxs-lookup"><span data-stu-id="226a6-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="226a6-112">例如，`x + y + z` 會判斷值為 `(x + y) + z`。</span><span class="sxs-lookup"><span data-stu-id="226a6-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="226a6-113">指派運算子和條件運算子 (`?:`) 具有「右關聯性」，亦即會由右到左執行運算。</span><span class="sxs-lookup"><span data-stu-id="226a6-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="226a6-114">例如，`x = y = z` 會判斷值為 `x = (y = z)`。</span><span class="sxs-lookup"><span data-stu-id="226a6-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="226a6-115">您可以使用括弧來控制優先順序和關聯性。</span><span class="sxs-lookup"><span data-stu-id="226a6-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="226a6-116">例如，`x + y * z` 會先將 `y` 乘以 `z`，然後再將結果加到 `x`，而 `(x + y) * z` 則會先將 `x` 與 `y` 相加，然後再將結果乘以 `z`。</span><span class="sxs-lookup"><span data-stu-id="226a6-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="226a6-117">大多數運算子都是可以「多載」的運算子。</span><span class="sxs-lookup"><span data-stu-id="226a6-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="226a6-118">運算子多載可允許針對一個運算元屬於 (或兩個運算元都屬於) 使用者定義之類別或結構型別的運算式，指定使用者定義的運算子實作。</span><span class="sxs-lookup"><span data-stu-id="226a6-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="226a6-119">以下摘要說明 C# 運算子，其中依優先順序從最高到最低列出運算子分類。</span><span class="sxs-lookup"><span data-stu-id="226a6-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="226a6-120">相同分類中的運算子具有相等的優先順序。</span><span class="sxs-lookup"><span data-stu-id="226a6-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="226a6-121">每個分類底下是該分類中的運算式清單，以及該運算式型別的描述。</span><span class="sxs-lookup"><span data-stu-id="226a6-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="226a6-122">主要</span><span class="sxs-lookup"><span data-stu-id="226a6-122">Primary</span></span>
  - `x.m`<span data-ttu-id="226a6-123">:成員存取</span><span class="sxs-lookup"><span data-stu-id="226a6-123">: Member access</span></span>
  - `x(...)`<span data-ttu-id="226a6-124">:方法和委派叫用</span><span class="sxs-lookup"><span data-stu-id="226a6-124">: Method and delegate invocation</span></span>
  - `x[...]`<span data-ttu-id="226a6-125">:陣列和索引子存取</span><span class="sxs-lookup"><span data-stu-id="226a6-125">: Array and indexer access</span></span>
  - `x++`<span data-ttu-id="226a6-126">:後置遞增</span><span class="sxs-lookup"><span data-stu-id="226a6-126">: Post-increment</span></span>
  - `x--`<span data-ttu-id="226a6-127">:後置遞減</span><span class="sxs-lookup"><span data-stu-id="226a6-127">: Post-decrement</span></span>
  - `new T(...)`<span data-ttu-id="226a6-128">:建立物件和委派</span><span class="sxs-lookup"><span data-stu-id="226a6-128">: Object and delegate creation</span></span>
  - `new T(...){...}`<span data-ttu-id="226a6-129">:使用初始設定式來建立物件</span><span class="sxs-lookup"><span data-stu-id="226a6-129">: Object creation with initializer</span></span>
  - `new {...}`<span data-ttu-id="226a6-130">:匿名物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="226a6-130">:  Anonymous object initializer</span></span>
  - `new T[...]`<span data-ttu-id="226a6-131">:建立陣列</span><span class="sxs-lookup"><span data-stu-id="226a6-131">: Array creation</span></span>
  - `typeof(T)`<span data-ttu-id="226a6-132">:取得下列項目的 <xref:System.Type> 物件：</span><span class="sxs-lookup"><span data-stu-id="226a6-132">: Obtain <xref:System.Type> object for</span></span> `T`
  - `checked(x)`<span data-ttu-id="226a6-133">:在核取的內容中評估運算式</span><span class="sxs-lookup"><span data-stu-id="226a6-133">: Evaluate expression in checked context</span></span>
  - `unchecked(x)`<span data-ttu-id="226a6-134">:在未核取的內容中評估運算式</span><span class="sxs-lookup"><span data-stu-id="226a6-134">: Evaluate expression in unchecked context</span></span>
  - `default(T)`<span data-ttu-id="226a6-135">:取得下列型別的預設值：</span><span class="sxs-lookup"><span data-stu-id="226a6-135">: Obtain default value of type</span></span> `T`
  - `delegate {...}`<span data-ttu-id="226a6-136">:匿名函式 (匿名方法)</span><span class="sxs-lookup"><span data-stu-id="226a6-136">: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="226a6-137">一元</span><span class="sxs-lookup"><span data-stu-id="226a6-137">Unary</span></span>
  - `+x`<span data-ttu-id="226a6-138">:身分識別</span><span class="sxs-lookup"><span data-stu-id="226a6-138">: Identity</span></span>
  - `-x`<span data-ttu-id="226a6-139">:否定</span><span class="sxs-lookup"><span data-stu-id="226a6-139">: Negation</span></span>
  - `!x`<span data-ttu-id="226a6-140">:邏輯否定</span><span class="sxs-lookup"><span data-stu-id="226a6-140">: Logical negation</span></span>
  - `~x`<span data-ttu-id="226a6-141">:位元否定</span><span class="sxs-lookup"><span data-stu-id="226a6-141">: Bitwise negation</span></span>
  - `++x`<span data-ttu-id="226a6-142">:前置遞增</span><span class="sxs-lookup"><span data-stu-id="226a6-142">: Pre-increment</span></span>
  - `--x`<span data-ttu-id="226a6-143">:前置遞減</span><span class="sxs-lookup"><span data-stu-id="226a6-143">: Pre-decrement</span></span>
  - `(T)x`<span data-ttu-id="226a6-144">:明確地將 `x` 轉換為型別</span><span class="sxs-lookup"><span data-stu-id="226a6-144">: Explicitly convert `x` to type</span></span> `T`
  - `await x`<span data-ttu-id="226a6-145">:以非同步方式等候 `x` 完成</span><span class="sxs-lookup"><span data-stu-id="226a6-145">: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="226a6-146">乘法類 (Multiplicative)</span><span class="sxs-lookup"><span data-stu-id="226a6-146">Multiplicative</span></span>
  - `x * y`<span data-ttu-id="226a6-147">:乘法</span><span class="sxs-lookup"><span data-stu-id="226a6-147">: Multiplication</span></span>
  - `x / y`<span data-ttu-id="226a6-148">:除號</span><span class="sxs-lookup"><span data-stu-id="226a6-148">: Division</span></span>
  - `x % y`<span data-ttu-id="226a6-149">:餘數</span><span class="sxs-lookup"><span data-stu-id="226a6-149">: Remainder</span></span>
* <span data-ttu-id="226a6-150">加法類 (Additive)</span><span class="sxs-lookup"><span data-stu-id="226a6-150">Additive</span></span>
  - `x + y`<span data-ttu-id="226a6-151">:加法、字串串連、委派組合</span><span class="sxs-lookup"><span data-stu-id="226a6-151">: Addition, string concatenation, delegate combination</span></span>
  - `x – y`<span data-ttu-id="226a6-152">:減法、委派移除</span><span class="sxs-lookup"><span data-stu-id="226a6-152">: Subtraction, delegate removal</span></span>
* <span data-ttu-id="226a6-153">Shift</span><span class="sxs-lookup"><span data-stu-id="226a6-153">Shift</span></span>
  - `x << y`<span data-ttu-id="226a6-154">:左移</span><span class="sxs-lookup"><span data-stu-id="226a6-154">: Shift left</span></span>
  - `x >> y`<span data-ttu-id="226a6-155">:右移</span><span class="sxs-lookup"><span data-stu-id="226a6-155">: Shift right</span></span>
* <span data-ttu-id="226a6-156">關係和型別測試</span><span class="sxs-lookup"><span data-stu-id="226a6-156">Relational and type testing</span></span>
  - `x < y`<span data-ttu-id="226a6-157">:小於</span><span class="sxs-lookup"><span data-stu-id="226a6-157">: Less than</span></span>
  - `x > y`<span data-ttu-id="226a6-158">:大於</span><span class="sxs-lookup"><span data-stu-id="226a6-158">: Greater than</span></span>
  - `x <= y`<span data-ttu-id="226a6-159">:小於或等於</span><span class="sxs-lookup"><span data-stu-id="226a6-159">: Less than or equal</span></span>
  - `x >= y`<span data-ttu-id="226a6-160">:大於或等於</span><span class="sxs-lookup"><span data-stu-id="226a6-160">: Greater than or equal</span></span>
  - `x is T`<span data-ttu-id="226a6-161">:如果 `x` 是 `T`，便傳回 `true`，否則傳回 `false`</span><span class="sxs-lookup"><span data-stu-id="226a6-161">: Return `true` if `x` is a `T`, `false` otherwise</span></span>
  - `x as T`<span data-ttu-id="226a6-162">:傳回型別設定為 `T` 的 `x`，或傳回 `null` (若 `x` 不等於</span><span class="sxs-lookup"><span data-stu-id="226a6-162">: Return `x` typed as `T`, or `null` if `x` is not a</span></span> `T`
* <span data-ttu-id="226a6-163">相等</span><span class="sxs-lookup"><span data-stu-id="226a6-163">Equality</span></span>
  - `x == y`<span data-ttu-id="226a6-164">:等於</span><span class="sxs-lookup"><span data-stu-id="226a6-164">: Equal</span></span>
  - `x != y`<span data-ttu-id="226a6-165">:不等於</span><span class="sxs-lookup"><span data-stu-id="226a6-165">: Not equal</span></span>
* <span data-ttu-id="226a6-166">邏輯 AND</span><span class="sxs-lookup"><span data-stu-id="226a6-166">Logical AND</span></span>
  - `x & y`<span data-ttu-id="226a6-167">:整數位元 AND、布林邏輯 AND</span><span class="sxs-lookup"><span data-stu-id="226a6-167">: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="226a6-168">邏輯 XOR</span><span class="sxs-lookup"><span data-stu-id="226a6-168">Logical XOR</span></span>
  - `x ^ y`<span data-ttu-id="226a6-169">:整數位元 XOR、布林邏輯 XOR</span><span class="sxs-lookup"><span data-stu-id="226a6-169">: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="226a6-170">邏輯 OR</span><span class="sxs-lookup"><span data-stu-id="226a6-170">Logical OR</span></span>
  - `x | y`<span data-ttu-id="226a6-171">:整數位元 OR、布林邏輯 OR</span><span class="sxs-lookup"><span data-stu-id="226a6-171">: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="226a6-172">條件式 AND</span><span class="sxs-lookup"><span data-stu-id="226a6-172">Conditional AND</span></span>
  - `x && y`<span data-ttu-id="226a6-173">:只有在 `x` 不等於下列項目的情況下才評估 `y`</span><span class="sxs-lookup"><span data-stu-id="226a6-173">: Evaluates `y` only if `x` is not</span></span> `false`
* <span data-ttu-id="226a6-174">條件式 OR</span><span class="sxs-lookup"><span data-stu-id="226a6-174">Conditional OR</span></span>
  - `x || y`<span data-ttu-id="226a6-175">:只有在 `x` 不等於下列項目的情況下才評估 `y`</span><span class="sxs-lookup"><span data-stu-id="226a6-175">: Evaluates `y` only if `x` is not</span></span> `true`
* <span data-ttu-id="226a6-176">Null 聯合</span><span class="sxs-lookup"><span data-stu-id="226a6-176">Null coalescing</span></span>
  - `x ?? y`<span data-ttu-id="226a6-177">:如果 `x` 是 null，便評估為 `y`，否則評估為 `x`</span><span class="sxs-lookup"><span data-stu-id="226a6-177">: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="226a6-178">條件式</span><span class="sxs-lookup"><span data-stu-id="226a6-178">Conditional</span></span>
  - `x ? y : z`<span data-ttu-id="226a6-179">:評估 `y` (若 `x` 為 `true`)，或評估 `z` (若 `x` 為下列值：</span><span class="sxs-lookup"><span data-stu-id="226a6-179">: Evaluates `y` if `x` is `true`, `z` if `x` is</span></span> `false`
* <span data-ttu-id="226a6-180">指派或匿名函式</span><span class="sxs-lookup"><span data-stu-id="226a6-180">Assignment or anonymous function</span></span>
  - `x = y`<span data-ttu-id="226a6-181">:指派</span><span class="sxs-lookup"><span data-stu-id="226a6-181">: Assignment</span></span>
  - `x op= y`<span data-ttu-id="226a6-182">:複合指派；支援的運算子包括</span><span class="sxs-lookup"><span data-stu-id="226a6-182">: Compound assignment; supported operators are</span></span>
    - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
  - `(T x) => y`<span data-ttu-id="226a6-183">:匿名函式 (Lambda 運算式)</span><span class="sxs-lookup"><span data-stu-id="226a6-183">: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="226a6-184">[上一頁](types-and-variables.md)
> [下一頁](statements.md)</span><span class="sxs-lookup"><span data-stu-id="226a6-184">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
