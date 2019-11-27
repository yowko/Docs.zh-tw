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
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="0f84f-102">For...Next 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f84f-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="0f84f-103">重複指定次數的語句群組。</span><span class="sxs-lookup"><span data-stu-id="0f84f-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f84f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f84f-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="0f84f-105">組件</span><span class="sxs-lookup"><span data-stu-id="0f84f-105">Parts</span></span>

|<span data-ttu-id="0f84f-106">組件</span><span class="sxs-lookup"><span data-stu-id="0f84f-106">Part</span></span>|<span data-ttu-id="0f84f-107">描述</span><span class="sxs-lookup"><span data-stu-id="0f84f-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="0f84f-108">在 `For` 語句中是必要的。</span><span class="sxs-lookup"><span data-stu-id="0f84f-108">Required in the `For` statement.</span></span> <span data-ttu-id="0f84f-109">數值變數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-109">Numeric variable.</span></span> <span data-ttu-id="0f84f-110">迴圈的控制變數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-110">The control variable for the loop.</span></span> <span data-ttu-id="0f84f-111">如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。</span><span class="sxs-lookup"><span data-stu-id="0f84f-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="0f84f-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0f84f-112">Optional.</span></span> <span data-ttu-id="0f84f-113">`counter`的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0f84f-113">Data type of `counter`.</span></span> <span data-ttu-id="0f84f-114">如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。</span><span class="sxs-lookup"><span data-stu-id="0f84f-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="0f84f-115">必要。</span><span class="sxs-lookup"><span data-stu-id="0f84f-115">Required.</span></span> <span data-ttu-id="0f84f-116">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="0f84f-116">Numeric expression.</span></span> <span data-ttu-id="0f84f-117">`counter` 的初始值。</span><span class="sxs-lookup"><span data-stu-id="0f84f-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="0f84f-118">必要。</span><span class="sxs-lookup"><span data-stu-id="0f84f-118">Required.</span></span> <span data-ttu-id="0f84f-119">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="0f84f-119">Numeric expression.</span></span> <span data-ttu-id="0f84f-120">`counter`的最終值。</span><span class="sxs-lookup"><span data-stu-id="0f84f-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="0f84f-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0f84f-121">Optional.</span></span> <span data-ttu-id="0f84f-122">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="0f84f-122">Numeric expression.</span></span> <span data-ttu-id="0f84f-123">每次執行迴圈時，`counter` 的遞增量。</span><span class="sxs-lookup"><span data-stu-id="0f84f-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="0f84f-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0f84f-124">Optional.</span></span> <span data-ttu-id="0f84f-125">`For` 和 `Next` 之間的一個或多個語句執行指定的次數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="0f84f-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0f84f-126">Optional.</span></span> <span data-ttu-id="0f84f-127">將控制權轉移至下一個迴圈反復專案。</span><span class="sxs-lookup"><span data-stu-id="0f84f-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="0f84f-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0f84f-128">Optional.</span></span> <span data-ttu-id="0f84f-129">將控制權轉移 `For` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="0f84f-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="0f84f-130">必要。</span><span class="sxs-lookup"><span data-stu-id="0f84f-130">Required.</span></span> <span data-ttu-id="0f84f-131">結束 `For` 迴圈的定義。</span><span class="sxs-lookup"><span data-stu-id="0f84f-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="0f84f-132">這個語句中會使用 `To` 關鍵字來指定計數器的範圍。</span><span class="sxs-lookup"><span data-stu-id="0f84f-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="0f84f-133">您也可以在 [選取 ...] 中使用此關鍵字[Case 語句](../../../visual-basic/language-reference/statements/select-case-statement.md)和陣列宣告。</span><span class="sxs-lookup"><span data-stu-id="0f84f-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="0f84f-134">如需陣列宣告的詳細資訊，請參閱[Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0f84f-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="0f84f-135">簡單範例</span><span class="sxs-lookup"><span data-stu-id="0f84f-135">Simple Examples</span></span>

<span data-ttu-id="0f84f-136">當您想要以設定的次數重複一組語句時，您可以使用 `For`...`Next` 結構。</span><span class="sxs-lookup"><span data-stu-id="0f84f-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="0f84f-137">在下列範例中，`index` 變數的開頭為1的值，而且會隨著迴圈的每個反復專案而遞增，並在 `index` 的值到達5之後結束。</span><span class="sxs-lookup"><span data-stu-id="0f84f-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="0f84f-138">在下列範例中，`number` 變數會從2開始，並在迴圈的每次反覆運算時減少0.25，並在 `number` 的值到達0之後結束。</span><span class="sxs-lookup"><span data-stu-id="0f84f-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="0f84f-139">`-.25` 的 `Step` 引數會在迴圈的每個反覆運算上減少0.25 的值。</span><span class="sxs-lookup"><span data-stu-id="0f84f-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="0f84f-140">A [While .。。End While 語句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)或[Do .。。](../../../visual-basic/language-reference/statements/do-loop-statement.md)當您事先不知道要在迴圈中執行語句的次數時，Loop 語句的運作效果很好。</span><span class="sxs-lookup"><span data-stu-id="0f84f-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="0f84f-141">不過，當您預期會執行特定次數的迴圈時，`For`...`Next` 迴圈是較佳的選擇。</span><span class="sxs-lookup"><span data-stu-id="0f84f-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="0f84f-142">您會在第一次進入迴圈時判斷反覆運算次數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="0f84f-143">嵌套迴圈</span><span class="sxs-lookup"><span data-stu-id="0f84f-143">Nesting Loops</span></span>

<span data-ttu-id="0f84f-144">您可以藉由將一個迴圈放在另一個迴圈中，來將 `For` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="0f84f-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="0f84f-145">下列範例示範具有不同步驟值的 nested `For`...`Next` 結構。</span><span class="sxs-lookup"><span data-stu-id="0f84f-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="0f84f-146">外部迴圈會為迴圈的每個反覆運算建立一個字串。</span><span class="sxs-lookup"><span data-stu-id="0f84f-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="0f84f-147">內部迴圈會針對迴圈的每個反覆運算遞減迴圈計數器變數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="0f84f-148">當嵌套迴圈時，每個迴圈都必須有唯一的 `counter` 變數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="0f84f-149">您也可以將不同類型的控制結構分別放在其中。</span><span class="sxs-lookup"><span data-stu-id="0f84f-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="0f84f-150">如需詳細資訊，請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="0f84f-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="0f84f-151">結束並繼續進行</span><span class="sxs-lookup"><span data-stu-id="0f84f-151">Exit For and Continue For</span></span>

<span data-ttu-id="0f84f-152">`Exit For` 語句會立即離開 `For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="0f84f-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="0f84f-153">迴圈，並將控制權轉移至 `Next` 語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="0f84f-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="0f84f-154">`Continue For` 語句會立即將控制權轉移到迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="0f84f-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="0f84f-155">如需詳細資訊，請參閱[Continue 語句](../../../visual-basic/language-reference/statements/continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0f84f-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>

<span data-ttu-id="0f84f-156">下列範例說明如何使用 `Continue For` 和 `Exit For` 語句。</span><span class="sxs-lookup"><span data-stu-id="0f84f-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="0f84f-157">您可以將任意數目的 `Exit For` 語句放在 `For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="0f84f-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="0f84f-158">loop：</span><span class="sxs-lookup"><span data-stu-id="0f84f-158">loop.</span></span> <span data-ttu-id="0f84f-159">在 nested `For`中使用時 ...`Next`</span><span class="sxs-lookup"><span data-stu-id="0f84f-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="0f84f-160">迴圈，`Exit For` 會結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="0f84f-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="0f84f-161">在您評估某個條件（例如，在 `If`...`Then`...`Else` 結構）之後，通常會使用 `Exit For`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="0f84f-162">在下列情況中，您可能會想要使用 `Exit For`：</span><span class="sxs-lookup"><span data-stu-id="0f84f-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="0f84f-163">繼續進行反覆運算是不必要或不可能的。</span><span class="sxs-lookup"><span data-stu-id="0f84f-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="0f84f-164">錯誤值或終止要求可能會建立此條件。</span><span class="sxs-lookup"><span data-stu-id="0f84f-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="0f84f-165">`Try`...`Catch`...`Finally` 語句會攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f84f-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="0f84f-166">您可以使用 `Finally` 區塊結尾處的 `Exit For`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="0f84f-167">您有一個無止盡的迴圈，這是一種迴圈，可能會執行很長或甚至無限次數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="0f84f-168">如果您偵測到這種情況，您可以使用 `Exit For` 來對迴圈進行 escape。</span><span class="sxs-lookup"><span data-stu-id="0f84f-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="0f84f-169">如需詳細資訊，請參閱[Do .。。Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="0f84f-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="0f84f-170">技術實作</span><span class="sxs-lookup"><span data-stu-id="0f84f-170">Technical Implementation</span></span>

<span data-ttu-id="0f84f-171">當 `For`...`Next` 迴圈啟動時，Visual Basic 會評估 `start`、`end`和 `step`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="0f84f-172">Visual Basic 只會在這段時間評估這些值，然後將 `start` 指派給 `counter`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="0f84f-173">在執行語句區塊之前，Visual Basic 會比較 `counter` 與 `end`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="0f84f-174">如果 `counter` 已經大於 `end` 值（如果 `step` 是負數，則較小），`For` 迴圈就會結束，並將控制權傳遞至緊接在 `Next` 語句之後的語句。</span><span class="sxs-lookup"><span data-stu-id="0f84f-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="0f84f-175">否則，會執行語句區塊。</span><span class="sxs-lookup"><span data-stu-id="0f84f-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="0f84f-176">每次 Visual Basic 遇到 `Next` 語句時，它會以 `step` 遞增 `counter`，並返回 `For` 語句。</span><span class="sxs-lookup"><span data-stu-id="0f84f-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="0f84f-177">同樣地，它會比較 `counter` 與 `end`，然後根據結果，執行區塊或結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="0f84f-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="0f84f-178">此程式會繼續進行，直到 `counter` 通過 `end` 或遇到 `Exit For` 語句為止。</span><span class="sxs-lookup"><span data-stu-id="0f84f-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="0f84f-179">直到 `counter` 傳遞 `end`後，迴圈才會停止。</span><span class="sxs-lookup"><span data-stu-id="0f84f-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="0f84f-180">如果 `counter` 等於 `end`，迴圈就會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="0f84f-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="0f84f-181">如果 `step` 為正數，則決定是否要執行區塊的比較 `counter` <= `end` 如果 `counter`為負數，則  >= `end` `step`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="0f84f-182">如果您在迴圈內變更 `counter` 的值，您的程式碼可能會更容易讀取和 debug。</span><span class="sxs-lookup"><span data-stu-id="0f84f-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="0f84f-183">變更 `start`、`end`或 `step` 的值，並不會影響第一次進入迴圈時所決定的反復專案值。</span><span class="sxs-lookup"><span data-stu-id="0f84f-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="0f84f-184">如果您嵌套迴圈，編譯器在內部層級的 `Next` 語句之前遇到外部嵌套層級的 `Next` 語句時，會發出錯誤信號。</span><span class="sxs-lookup"><span data-stu-id="0f84f-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="0f84f-185">不過，只有當您在每個 `Next` 語句中指定 `counter` 時，編譯器才能夠偵測到這個重迭的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f84f-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="0f84f-186">Step 引數</span><span class="sxs-lookup"><span data-stu-id="0f84f-186">Step Argument</span></span>

<span data-ttu-id="0f84f-187">`step` 的值可以是正數或負數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="0f84f-188">這個參數會根據下表來決定迴圈處理：</span><span class="sxs-lookup"><span data-stu-id="0f84f-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="0f84f-189">**步驟值**</span><span class="sxs-lookup"><span data-stu-id="0f84f-189">**Step value**</span></span>|<span data-ttu-id="0f84f-190">**迴圈執行（如果**</span><span class="sxs-lookup"><span data-stu-id="0f84f-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="0f84f-191">正數或零</span><span class="sxs-lookup"><span data-stu-id="0f84f-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="0f84f-192">負</span><span class="sxs-lookup"><span data-stu-id="0f84f-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="0f84f-193">`step` 的預設值為1。</span><span class="sxs-lookup"><span data-stu-id="0f84f-193">The default value of `step` is 1.</span></span>

### <a name="BKMK_Counter"></a><span data-ttu-id="0f84f-194">Counter 引數</span><span class="sxs-lookup"><span data-stu-id="0f84f-194">Counter Argument</span></span>

<span data-ttu-id="0f84f-195">下表指出 `counter` 是否定義範圍設定為整個 `For…Next` 迴圈的新區域變數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="0f84f-196">這項決定取決於是否存在 `datatype`，以及 `counter` 是否已定義。</span><span class="sxs-lookup"><span data-stu-id="0f84f-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="0f84f-197">`datatype` 存在嗎？</span><span class="sxs-lookup"><span data-stu-id="0f84f-197">Is `datatype` present?</span></span>|<span data-ttu-id="0f84f-198">`counter` 已經定義了嗎？</span><span class="sxs-lookup"><span data-stu-id="0f84f-198">Is `counter` already defined?</span></span>|<span data-ttu-id="0f84f-199">Result （`counter` 是否定義範圍設定為整個 `For...Next` 迴圈的新區域變數）</span><span class="sxs-lookup"><span data-stu-id="0f84f-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="0f84f-200">否</span><span class="sxs-lookup"><span data-stu-id="0f84f-200">No</span></span>|<span data-ttu-id="0f84f-201">[是]</span><span class="sxs-lookup"><span data-stu-id="0f84f-201">Yes</span></span>|<span data-ttu-id="0f84f-202">否，因為已定義 `counter`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="0f84f-203">如果 `counter` 的範圍不是程式的本機，就會發生編譯時期警告。</span><span class="sxs-lookup"><span data-stu-id="0f84f-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="0f84f-204">否</span><span class="sxs-lookup"><span data-stu-id="0f84f-204">No</span></span>|<span data-ttu-id="0f84f-205">否</span><span class="sxs-lookup"><span data-stu-id="0f84f-205">No</span></span>|<span data-ttu-id="0f84f-206">可以。</span><span class="sxs-lookup"><span data-stu-id="0f84f-206">Yes.</span></span> <span data-ttu-id="0f84f-207">資料類型是從 [`start`]、[`end`] 和 [`step`] 運算式推斷而來。</span><span class="sxs-lookup"><span data-stu-id="0f84f-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="0f84f-208">如需型別推斷的詳細資訊，請參閱[Option 推斷語句](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區欄位型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="0f84f-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="0f84f-209">[是]</span><span class="sxs-lookup"><span data-stu-id="0f84f-209">Yes</span></span>|<span data-ttu-id="0f84f-210">[是]</span><span class="sxs-lookup"><span data-stu-id="0f84f-210">Yes</span></span>|<span data-ttu-id="0f84f-211">是，但只有在程式之外定義了現有的 `counter` 變數時。</span><span class="sxs-lookup"><span data-stu-id="0f84f-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="0f84f-212">該變數會保持不變。</span><span class="sxs-lookup"><span data-stu-id="0f84f-212">That variable remains separate.</span></span> <span data-ttu-id="0f84f-213">如果現有 `counter` 變數的範圍是程式的本機，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f84f-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="0f84f-214">[是]</span><span class="sxs-lookup"><span data-stu-id="0f84f-214">Yes</span></span>|<span data-ttu-id="0f84f-215">否</span><span class="sxs-lookup"><span data-stu-id="0f84f-215">No</span></span>|<span data-ttu-id="0f84f-216">可以。</span><span class="sxs-lookup"><span data-stu-id="0f84f-216">Yes.</span></span>|

<span data-ttu-id="0f84f-217">`counter` 的資料類型會決定反復專案的類型，必須是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="0f84f-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="0f84f-218">`Byte`、`SByte`、`UShort`、`Short`、`UInteger`、`Integer`、`ULong`、`Long`、`Decimal`、`Single`或 `Double`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="0f84f-219">使用[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)宣告的列舉。</span><span class="sxs-lookup"><span data-stu-id="0f84f-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

- <span data-ttu-id="0f84f-220">`Object`。</span><span class="sxs-lookup"><span data-stu-id="0f84f-220">An `Object`.</span></span>

- <span data-ttu-id="0f84f-221">具有下列運算子的類型 `T`，其中 `B` 是可用於 `Boolean` 運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="0f84f-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="0f84f-222">您可以選擇性地在 `Next` 語句中指定 `counter` 變數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="0f84f-223">此語法可改善程式的可讀性，特別是如果您有嵌套的 `For` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="0f84f-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="0f84f-224">您必須指定出現在對應的 `For` 語句中的變數。</span><span class="sxs-lookup"><span data-stu-id="0f84f-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="0f84f-225">`start`、`end`和 `step` 運算式可以評估為任何擴大至 `counter`類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0f84f-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="0f84f-226">如果您使用 `counter`的使用者定義型別，您可能必須定義 `CType` 轉換運算子，以將 `start`、`end`或 `step` 的類型轉換成 `counter`的類型。</span><span class="sxs-lookup"><span data-stu-id="0f84f-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="0f84f-227">範例</span><span class="sxs-lookup"><span data-stu-id="0f84f-227">Example</span></span>

<span data-ttu-id="0f84f-228">下列範例會從泛型清單中移除所有元素。</span><span class="sxs-lookup"><span data-stu-id="0f84f-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="0f84f-229">而不是[針對每個 .。。下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)，此範例會顯示以遞減順序逐一查看的 `For`...`Next` 語句。</span><span class="sxs-lookup"><span data-stu-id="0f84f-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="0f84f-230">此範例會使用這項技術，因為 `removeAt` 方法會使已移除專案之後的元素具有較低的索引值。</span><span class="sxs-lookup"><span data-stu-id="0f84f-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="0f84f-231">範例</span><span class="sxs-lookup"><span data-stu-id="0f84f-231">Example</span></span>

<span data-ttu-id="0f84f-232">下列範例會逐一查看使用[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)宣告的列舉。</span><span class="sxs-lookup"><span data-stu-id="0f84f-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="0f84f-233">範例</span><span class="sxs-lookup"><span data-stu-id="0f84f-233">Example</span></span>

<span data-ttu-id="0f84f-234">在下列範例中，語句參數使用的類別具有 `+`、`-`、`>=`和 `<=` 運算子的運算子多載。</span><span class="sxs-lookup"><span data-stu-id="0f84f-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="0f84f-235">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f84f-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="0f84f-236">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="0f84f-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="0f84f-237">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f84f-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="0f84f-238">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f84f-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="0f84f-239">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="0f84f-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="0f84f-240">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="0f84f-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="0f84f-241">集合</span><span class="sxs-lookup"><span data-stu-id="0f84f-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
