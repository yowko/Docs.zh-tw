---
title: For...Next 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 3cae44abb8e790542f11e6c5a5f1e317675ff988
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351190"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="61eef-102">For...Next 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61eef-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="61eef-103">Repeats a group of statements a specified number of times.</span><span class="sxs-lookup"><span data-stu-id="61eef-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="61eef-104">語法</span><span class="sxs-lookup"><span data-stu-id="61eef-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="61eef-105">組件</span><span class="sxs-lookup"><span data-stu-id="61eef-105">Parts</span></span>

|<span data-ttu-id="61eef-106">組件</span><span class="sxs-lookup"><span data-stu-id="61eef-106">Part</span></span>|<span data-ttu-id="61eef-107">描述</span><span class="sxs-lookup"><span data-stu-id="61eef-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="61eef-108">Required in the `For` statement.</span><span class="sxs-lookup"><span data-stu-id="61eef-108">Required in the `For` statement.</span></span> <span data-ttu-id="61eef-109">Numeric variable.</span><span class="sxs-lookup"><span data-stu-id="61eef-109">Numeric variable.</span></span> <span data-ttu-id="61eef-110">The control variable for the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-110">The control variable for the loop.</span></span> <span data-ttu-id="61eef-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span><span class="sxs-lookup"><span data-stu-id="61eef-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="61eef-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="61eef-112">Optional.</span></span> <span data-ttu-id="61eef-113">Data type of `counter`.</span><span class="sxs-lookup"><span data-stu-id="61eef-113">Data type of `counter`.</span></span> <span data-ttu-id="61eef-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span><span class="sxs-lookup"><span data-stu-id="61eef-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="61eef-115">必要項。</span><span class="sxs-lookup"><span data-stu-id="61eef-115">Required.</span></span> <span data-ttu-id="61eef-116">Numeric expression.</span><span class="sxs-lookup"><span data-stu-id="61eef-116">Numeric expression.</span></span> <span data-ttu-id="61eef-117">`counter` 的初始值。</span><span class="sxs-lookup"><span data-stu-id="61eef-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="61eef-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="61eef-118">Required.</span></span> <span data-ttu-id="61eef-119">Numeric expression.</span><span class="sxs-lookup"><span data-stu-id="61eef-119">Numeric expression.</span></span> <span data-ttu-id="61eef-120">The final value of `counter`.</span><span class="sxs-lookup"><span data-stu-id="61eef-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="61eef-121">選擇項。</span><span class="sxs-lookup"><span data-stu-id="61eef-121">Optional.</span></span> <span data-ttu-id="61eef-122">Numeric expression.</span><span class="sxs-lookup"><span data-stu-id="61eef-122">Numeric expression.</span></span> <span data-ttu-id="61eef-123">The amount by which `counter` is incremented each time through the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="61eef-124">選擇項。</span><span class="sxs-lookup"><span data-stu-id="61eef-124">Optional.</span></span> <span data-ttu-id="61eef-125">One or more statements between `For` and `Next` that run the specified number of times.</span><span class="sxs-lookup"><span data-stu-id="61eef-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="61eef-126">選擇項。</span><span class="sxs-lookup"><span data-stu-id="61eef-126">Optional.</span></span> <span data-ttu-id="61eef-127">Transfers control to the next loop iteration.</span><span class="sxs-lookup"><span data-stu-id="61eef-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="61eef-128">選擇項。</span><span class="sxs-lookup"><span data-stu-id="61eef-128">Optional.</span></span> <span data-ttu-id="61eef-129">Transfers control out of the `For` loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="61eef-130">必要項。</span><span class="sxs-lookup"><span data-stu-id="61eef-130">Required.</span></span> <span data-ttu-id="61eef-131">Terminates the definition of the `For` loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="61eef-132">The `To` keyword is used in this statement to specify the range for the counter.</span><span class="sxs-lookup"><span data-stu-id="61eef-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="61eef-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span><span class="sxs-lookup"><span data-stu-id="61eef-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="61eef-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61eef-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="61eef-135">Simple Examples</span><span class="sxs-lookup"><span data-stu-id="61eef-135">Simple Examples</span></span>

<span data-ttu-id="61eef-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span><span class="sxs-lookup"><span data-stu-id="61eef-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="61eef-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span><span class="sxs-lookup"><span data-stu-id="61eef-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="61eef-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span><span class="sxs-lookup"><span data-stu-id="61eef-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="61eef-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="61eef-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="61eef-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span><span class="sxs-lookup"><span data-stu-id="61eef-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="61eef-142">You determine the number of iterations when you first enter the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="61eef-143">Nesting Loops</span><span class="sxs-lookup"><span data-stu-id="61eef-143">Nesting Loops</span></span>

<span data-ttu-id="61eef-144">You can nest `For` loops by putting one loop within another.</span><span class="sxs-lookup"><span data-stu-id="61eef-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="61eef-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span><span class="sxs-lookup"><span data-stu-id="61eef-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="61eef-146">The outer loop creates a string for every iteration of the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="61eef-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="61eef-148">When nesting loops, each loop must have a unique `counter` variable.</span><span class="sxs-lookup"><span data-stu-id="61eef-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="61eef-149">You can also nest different kinds control structures within each other.</span><span class="sxs-lookup"><span data-stu-id="61eef-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="61eef-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="61eef-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="61eef-151">Exit For and Continue For</span><span class="sxs-lookup"><span data-stu-id="61eef-151">Exit For and Continue For</span></span>

<span data-ttu-id="61eef-152">The `Exit For` statement immediately exits the `For`…`Next`</span><span class="sxs-lookup"><span data-stu-id="61eef-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="61eef-153">loop and transfers control to the statement that follows the `Next` statement.</span><span class="sxs-lookup"><span data-stu-id="61eef-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="61eef-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="61eef-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61eef-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>

<span data-ttu-id="61eef-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span><span class="sxs-lookup"><span data-stu-id="61eef-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="61eef-157">You can put any number of `Exit For` statements in a `For`…`Next`</span><span class="sxs-lookup"><span data-stu-id="61eef-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="61eef-158">loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-158">loop.</span></span> <span data-ttu-id="61eef-159">When used within nested `For`…`Next`</span><span class="sxs-lookup"><span data-stu-id="61eef-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="61eef-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span><span class="sxs-lookup"><span data-stu-id="61eef-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="61eef-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span><span class="sxs-lookup"><span data-stu-id="61eef-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="61eef-162">You might want to use `Exit For` for the following conditions:</span><span class="sxs-lookup"><span data-stu-id="61eef-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="61eef-163">Continuing to iterate is unnecessary or impossible.</span><span class="sxs-lookup"><span data-stu-id="61eef-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="61eef-164">An erroneous value or a termination request might create this condition.</span><span class="sxs-lookup"><span data-stu-id="61eef-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="61eef-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span><span class="sxs-lookup"><span data-stu-id="61eef-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="61eef-166">You might use `Exit For` at the end of the `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="61eef-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="61eef-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span><span class="sxs-lookup"><span data-stu-id="61eef-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="61eef-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="61eef-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61eef-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="61eef-170">技術實作</span><span class="sxs-lookup"><span data-stu-id="61eef-170">Technical Implementation</span></span>

<span data-ttu-id="61eef-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span><span class="sxs-lookup"><span data-stu-id="61eef-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="61eef-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span><span class="sxs-lookup"><span data-stu-id="61eef-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="61eef-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span><span class="sxs-lookup"><span data-stu-id="61eef-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="61eef-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span><span class="sxs-lookup"><span data-stu-id="61eef-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="61eef-175">Otherwise, the statement block runs.</span><span class="sxs-lookup"><span data-stu-id="61eef-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="61eef-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span><span class="sxs-lookup"><span data-stu-id="61eef-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="61eef-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span><span class="sxs-lookup"><span data-stu-id="61eef-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="61eef-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span><span class="sxs-lookup"><span data-stu-id="61eef-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="61eef-179">The loop doesn't stop until `counter` has passed `end`.</span><span class="sxs-lookup"><span data-stu-id="61eef-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="61eef-180">If `counter` is equal to `end`, the loop continues.</span><span class="sxs-lookup"><span data-stu-id="61eef-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="61eef-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span><span class="sxs-lookup"><span data-stu-id="61eef-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="61eef-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span><span class="sxs-lookup"><span data-stu-id="61eef-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="61eef-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span><span class="sxs-lookup"><span data-stu-id="61eef-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="61eef-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span><span class="sxs-lookup"><span data-stu-id="61eef-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="61eef-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span><span class="sxs-lookup"><span data-stu-id="61eef-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="61eef-186">Step Argument</span><span class="sxs-lookup"><span data-stu-id="61eef-186">Step Argument</span></span>

<span data-ttu-id="61eef-187">The value of `step` can be either positive or negative.</span><span class="sxs-lookup"><span data-stu-id="61eef-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="61eef-188">This parameter determines loop processing according to the following table:</span><span class="sxs-lookup"><span data-stu-id="61eef-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="61eef-189">**Step value**</span><span class="sxs-lookup"><span data-stu-id="61eef-189">**Step value**</span></span>|<span data-ttu-id="61eef-190">**Loop executes if**</span><span class="sxs-lookup"><span data-stu-id="61eef-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="61eef-191">Positive or zero</span><span class="sxs-lookup"><span data-stu-id="61eef-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="61eef-192">負</span><span class="sxs-lookup"><span data-stu-id="61eef-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="61eef-193">The default value of `step` is 1.</span><span class="sxs-lookup"><span data-stu-id="61eef-193">The default value of `step` is 1.</span></span>

### <a name="BKMK_Counter"></a> <span data-ttu-id="61eef-194">Counter Argument</span><span class="sxs-lookup"><span data-stu-id="61eef-194">Counter Argument</span></span>

<span data-ttu-id="61eef-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span><span class="sxs-lookup"><span data-stu-id="61eef-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="61eef-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span><span class="sxs-lookup"><span data-stu-id="61eef-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="61eef-197">Is `datatype` present?</span><span class="sxs-lookup"><span data-stu-id="61eef-197">Is `datatype` present?</span></span>|<span data-ttu-id="61eef-198">Is `counter` already defined?</span><span class="sxs-lookup"><span data-stu-id="61eef-198">Is `counter` already defined?</span></span>|<span data-ttu-id="61eef-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span><span class="sxs-lookup"><span data-stu-id="61eef-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="61eef-200">否</span><span class="sxs-lookup"><span data-stu-id="61eef-200">No</span></span>|<span data-ttu-id="61eef-201">[是]</span><span class="sxs-lookup"><span data-stu-id="61eef-201">Yes</span></span>|<span data-ttu-id="61eef-202">No, because `counter` is already defined.</span><span class="sxs-lookup"><span data-stu-id="61eef-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="61eef-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span><span class="sxs-lookup"><span data-stu-id="61eef-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="61eef-204">否</span><span class="sxs-lookup"><span data-stu-id="61eef-204">No</span></span>|<span data-ttu-id="61eef-205">否</span><span class="sxs-lookup"><span data-stu-id="61eef-205">No</span></span>|<span data-ttu-id="61eef-206">可以。</span><span class="sxs-lookup"><span data-stu-id="61eef-206">Yes.</span></span> <span data-ttu-id="61eef-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span><span class="sxs-lookup"><span data-stu-id="61eef-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="61eef-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="61eef-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="61eef-209">[是]</span><span class="sxs-lookup"><span data-stu-id="61eef-209">Yes</span></span>|<span data-ttu-id="61eef-210">[是]</span><span class="sxs-lookup"><span data-stu-id="61eef-210">Yes</span></span>|<span data-ttu-id="61eef-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span><span class="sxs-lookup"><span data-stu-id="61eef-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="61eef-212">That variable remains separate.</span><span class="sxs-lookup"><span data-stu-id="61eef-212">That variable remains separate.</span></span> <span data-ttu-id="61eef-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="61eef-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="61eef-214">[是]</span><span class="sxs-lookup"><span data-stu-id="61eef-214">Yes</span></span>|<span data-ttu-id="61eef-215">否</span><span class="sxs-lookup"><span data-stu-id="61eef-215">No</span></span>|<span data-ttu-id="61eef-216">可以。</span><span class="sxs-lookup"><span data-stu-id="61eef-216">Yes.</span></span>|

<span data-ttu-id="61eef-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span><span class="sxs-lookup"><span data-stu-id="61eef-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="61eef-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span><span class="sxs-lookup"><span data-stu-id="61eef-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="61eef-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61eef-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

- <span data-ttu-id="61eef-220">`Object`。</span><span class="sxs-lookup"><span data-stu-id="61eef-220">An `Object`.</span></span>

- <span data-ttu-id="61eef-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span><span class="sxs-lookup"><span data-stu-id="61eef-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="61eef-222">You can optionally specify the `counter` variable in the `Next` statement.</span><span class="sxs-lookup"><span data-stu-id="61eef-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="61eef-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span><span class="sxs-lookup"><span data-stu-id="61eef-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="61eef-224">You must specify the variable that appears in the corresponding `For` statement.</span><span class="sxs-lookup"><span data-stu-id="61eef-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="61eef-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span><span class="sxs-lookup"><span data-stu-id="61eef-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="61eef-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span><span class="sxs-lookup"><span data-stu-id="61eef-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="61eef-227">範例</span><span class="sxs-lookup"><span data-stu-id="61eef-227">Example</span></span>

<span data-ttu-id="61eef-228">The following example removes all elements from a generic list.</span><span class="sxs-lookup"><span data-stu-id="61eef-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="61eef-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span><span class="sxs-lookup"><span data-stu-id="61eef-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="61eef-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span><span class="sxs-lookup"><span data-stu-id="61eef-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="61eef-231">範例</span><span class="sxs-lookup"><span data-stu-id="61eef-231">Example</span></span>

<span data-ttu-id="61eef-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61eef-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="61eef-233">範例</span><span class="sxs-lookup"><span data-stu-id="61eef-233">Example</span></span>

<span data-ttu-id="61eef-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span><span class="sxs-lookup"><span data-stu-id="61eef-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="61eef-235">請參閱</span><span class="sxs-lookup"><span data-stu-id="61eef-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="61eef-236">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="61eef-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="61eef-237">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="61eef-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="61eef-238">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="61eef-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="61eef-239">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="61eef-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="61eef-240">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="61eef-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="61eef-241">集合</span><span class="sxs-lookup"><span data-stu-id="61eef-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
