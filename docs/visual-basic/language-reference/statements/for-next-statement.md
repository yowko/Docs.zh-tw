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
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404637"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="38b83-102">For...Next 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38b83-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="38b83-103">重複指定次數的語句群組。</span><span class="sxs-lookup"><span data-stu-id="38b83-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="38b83-104">語法</span><span class="sxs-lookup"><span data-stu-id="38b83-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="38b83-105">組件</span><span class="sxs-lookup"><span data-stu-id="38b83-105">Parts</span></span>

|<span data-ttu-id="38b83-106">部分</span><span class="sxs-lookup"><span data-stu-id="38b83-106">Part</span></span>|<span data-ttu-id="38b83-107">描述</span><span class="sxs-lookup"><span data-stu-id="38b83-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="38b83-108">語句中的必要項 `For` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-108">Required in the `For` statement.</span></span> <span data-ttu-id="38b83-109">數值變數。</span><span class="sxs-lookup"><span data-stu-id="38b83-109">Numeric variable.</span></span> <span data-ttu-id="38b83-110">迴圈的控制變數。</span><span class="sxs-lookup"><span data-stu-id="38b83-110">The control variable for the loop.</span></span> <span data-ttu-id="38b83-111">如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。</span><span class="sxs-lookup"><span data-stu-id="38b83-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="38b83-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="38b83-112">Optional.</span></span> <span data-ttu-id="38b83-113">的資料類型 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-113">Data type of `counter`.</span></span> <span data-ttu-id="38b83-114">如需詳細資訊，請參閱本主題稍後的[計數器引數](#BKMK_Counter)。</span><span class="sxs-lookup"><span data-stu-id="38b83-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="38b83-115">必要。</span><span class="sxs-lookup"><span data-stu-id="38b83-115">Required.</span></span> <span data-ttu-id="38b83-116">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="38b83-116">Numeric expression.</span></span> <span data-ttu-id="38b83-117">`counter` 的初始值。</span><span class="sxs-lookup"><span data-stu-id="38b83-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="38b83-118">必要。</span><span class="sxs-lookup"><span data-stu-id="38b83-118">Required.</span></span> <span data-ttu-id="38b83-119">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="38b83-119">Numeric expression.</span></span> <span data-ttu-id="38b83-120">的最終值 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="38b83-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="38b83-121">Optional.</span></span> <span data-ttu-id="38b83-122">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="38b83-122">Numeric expression.</span></span> <span data-ttu-id="38b83-123">`counter`每次透過迴圈遞增的數量。</span><span class="sxs-lookup"><span data-stu-id="38b83-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="38b83-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="38b83-124">Optional.</span></span> <span data-ttu-id="38b83-125">`For`在和之間 `Next` 執行指定次數的一或多個語句。</span><span class="sxs-lookup"><span data-stu-id="38b83-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="38b83-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="38b83-126">Optional.</span></span> <span data-ttu-id="38b83-127">將控制權轉移至下一個迴圈反復專案。</span><span class="sxs-lookup"><span data-stu-id="38b83-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="38b83-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="38b83-128">Optional.</span></span> <span data-ttu-id="38b83-129">將控制權轉移給 `For` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="38b83-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="38b83-130">必要。</span><span class="sxs-lookup"><span data-stu-id="38b83-130">Required.</span></span> <span data-ttu-id="38b83-131">終止迴圈的定義 `For` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="38b83-132">`To`此語句中會使用關鍵字來指定計數器的範圍。</span><span class="sxs-lookup"><span data-stu-id="38b83-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="38b83-133">您也可以在 [選取 ...] 中使用此關鍵字[Case 語句](select-case-statement.md)和陣列宣告。</span><span class="sxs-lookup"><span data-stu-id="38b83-133">You can also use this keyword in the [Select...Case Statement](select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="38b83-134">如需陣列宣告的詳細資訊，請參閱[Dim 語句](dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="38b83-134">For more information about array declarations, see [Dim Statement](dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="38b83-135"> 簡單範例</span><span class="sxs-lookup"><span data-stu-id="38b83-135">Simple Examples</span></span>

<span data-ttu-id="38b83-136">`For` `Next` 當您想要以設定的次數重複一組語句時，可以使用 ... 結構。</span><span class="sxs-lookup"><span data-stu-id="38b83-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="38b83-137">在下列範例中， `index` 變數會以1的值開頭，並隨著迴圈的每個反復專案而遞增，並在的值 `index` 到達5之後結束。</span><span class="sxs-lookup"><span data-stu-id="38b83-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="38b83-138">在下列範例中， `number` 變數會從2開始，並在迴圈的每次反覆運算時減少0.25，並在的值 `number` 到達0之後結束。</span><span class="sxs-lookup"><span data-stu-id="38b83-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="38b83-139">的 `Step` 引數會 `-.25` 在迴圈的每個反復專案上，將值減少0.25。</span><span class="sxs-lookup"><span data-stu-id="38b83-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="38b83-140">A [While .。。End While 語句](while-end-while-statement.md)或[Do .。。](do-loop-statement.md)當您事先不知道要在迴圈中執行語句的次數時，Loop 語句的運作效果很好。</span><span class="sxs-lookup"><span data-stu-id="38b83-140">A [While...End While Statement](while-end-while-statement.md) or [Do...Loop Statement](do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="38b83-141">不過，如果您預期會執行迴圈特定次數，則 `For` ... `Next` 迴圈是較佳的選擇。</span><span class="sxs-lookup"><span data-stu-id="38b83-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="38b83-142">您會在第一次進入迴圈時判斷反覆運算次數。</span><span class="sxs-lookup"><span data-stu-id="38b83-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="38b83-143">嵌套迴圈</span><span class="sxs-lookup"><span data-stu-id="38b83-143">Nesting Loops</span></span>

<span data-ttu-id="38b83-144">您可以藉 `For` 由在另一個迴圈中放入迴圈來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="38b83-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="38b83-145">下列範例示範 `For` `Next` 具有不同步驟值的 nested 結構。</span><span class="sxs-lookup"><span data-stu-id="38b83-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="38b83-146">外部迴圈會為迴圈的每個反覆運算建立一個字串。</span><span class="sxs-lookup"><span data-stu-id="38b83-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="38b83-147">內部迴圈會針對迴圈的每個反覆運算遞減迴圈計數器變數。</span><span class="sxs-lookup"><span data-stu-id="38b83-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="38b83-148">當嵌套迴圈時，每個迴圈都必須有唯一的 `counter` 變數。</span><span class="sxs-lookup"><span data-stu-id="38b83-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="38b83-149">您也可以將不同類型的控制結構分別放在其中。</span><span class="sxs-lookup"><span data-stu-id="38b83-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="38b83-150">如需詳細資訊，請參閱[嵌套控制項結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="38b83-150">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="38b83-151">結束並繼續進行</span><span class="sxs-lookup"><span data-stu-id="38b83-151">Exit For and Continue For</span></span>

<span data-ttu-id="38b83-152">`Exit For`語句會立即結束 `For` .。。`Next`</span><span class="sxs-lookup"><span data-stu-id="38b83-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="38b83-153">迴圈，並將控制權轉移至語句後面的語句 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="38b83-154">`Continue For`語句會立即將控制權轉移到迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="38b83-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="38b83-155">如需詳細資訊，請參閱[Continue 語句](continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="38b83-155">For more information, see [Continue Statement](continue-statement.md).</span></span>

<span data-ttu-id="38b83-156">下列範例說明如何使用 `Continue For` 和 `Exit For` 語句。</span><span class="sxs-lookup"><span data-stu-id="38b83-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="38b83-157">您可以將任意數目的 `Exit For` 語句放在 `For` .。。`Next`</span><span class="sxs-lookup"><span data-stu-id="38b83-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="38b83-158">loop：</span><span class="sxs-lookup"><span data-stu-id="38b83-158">loop.</span></span> <span data-ttu-id="38b83-159">在 nested 中使用 `For` 時 .。。`Next`</span><span class="sxs-lookup"><span data-stu-id="38b83-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="38b83-160">迴圈，結束 `Exit For` 最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="38b83-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="38b83-161">`Exit For`通常是在評估某個條件之後使用（例如，在 `If` ... `Then`...`Else`結構）。</span><span class="sxs-lookup"><span data-stu-id="38b83-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="38b83-162">在下列情況下，您可能會想要使用 `Exit For` ：</span><span class="sxs-lookup"><span data-stu-id="38b83-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="38b83-163">繼續進行反覆運算是不必要或不可能的。</span><span class="sxs-lookup"><span data-stu-id="38b83-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="38b83-164">錯誤值或終止要求可能會建立此條件。</span><span class="sxs-lookup"><span data-stu-id="38b83-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="38b83-165">答 `Try` `Catch` ：...`Finally`語句會攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="38b83-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="38b83-166">您可以 `Exit For` 在區塊結尾使用 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="38b83-167">您有一個無止盡的迴圈，這是一種迴圈，可能會執行很長或甚至無限次數。</span><span class="sxs-lookup"><span data-stu-id="38b83-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="38b83-168">如果您偵測到這種情況，您可以使用 `Exit For` 來將迴圈轉義。</span><span class="sxs-lookup"><span data-stu-id="38b83-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="38b83-169">如需詳細資訊，請參閱[Do .。。Loop 語句](do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="38b83-169">For more information, see [Do...Loop Statement](do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="38b83-170">技術實作</span><span class="sxs-lookup"><span data-stu-id="38b83-170">Technical Implementation</span></span>

<span data-ttu-id="38b83-171">當 `For` ... `Next` 迴圈啟動時，Visual Basic 會評估 `start` 、 `end` 和 `step` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="38b83-172">Visual Basic 只會在此時評估這些值，然後將指派 `start` 給 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="38b83-173">在執行語句區塊之前，Visual Basic 會 `counter` 與進行比較 `end` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="38b83-174">如果 `counter` 已經大於 `end` 值（如果是負數，則為較小 `step` ），迴圈就會 `For` 結束，並將控制權傳遞至語句後面 `Next` 的語句。</span><span class="sxs-lookup"><span data-stu-id="38b83-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="38b83-175">否則，會執行語句區塊。</span><span class="sxs-lookup"><span data-stu-id="38b83-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="38b83-176">每次 Visual Basic 遇到 `Next` 語句時，它會 `counter` 遞增 `step` 並返回 `For` 語句。</span><span class="sxs-lookup"><span data-stu-id="38b83-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="38b83-177">同樣地，它會與進行比較 `counter` `end` ，並再次執行區塊或結束迴圈，視結果而定。</span><span class="sxs-lookup"><span data-stu-id="38b83-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="38b83-178">此程式會繼續 `counter` 進行，直到 `end` 遇到 pass 或語句為止 `Exit For` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="38b83-179">迴圈不會停止，直到 `counter` 通過為止 `end` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="38b83-180">如果 `counter` 等於 `end` ，迴圈就會繼續。</span><span class="sxs-lookup"><span data-stu-id="38b83-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="38b83-181">判斷是否要執行區塊的比較是正向 `counter`  <=  `end` `step` ，而且 `counter`  >=  `end` 如果 `step` 是負值，則為。</span><span class="sxs-lookup"><span data-stu-id="38b83-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="38b83-182">如果您在迴圈內變更的值 `counter` ，則您的程式碼可能會更容易讀取和 debug。</span><span class="sxs-lookup"><span data-stu-id="38b83-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="38b83-183">變更 `start` 、或的值， `end` `step` 並不會影響第一次進入迴圈時所決定的反復專案值。</span><span class="sxs-lookup"><span data-stu-id="38b83-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="38b83-184">如果您嵌套迴圈，編譯器在 `Next` 內部層級的語句之前遇到外部嵌套層級的語句時，會發出錯誤信號 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="38b83-185">不過，只有當您 `counter` 在每個語句中指定時，編譯器才會偵測到這個重迭的錯誤 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="38b83-186">Step 引數</span><span class="sxs-lookup"><span data-stu-id="38b83-186">Step Argument</span></span>

<span data-ttu-id="38b83-187">的值 `step` 可以是正數或負數。</span><span class="sxs-lookup"><span data-stu-id="38b83-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="38b83-188">這個參數會根據下表來決定迴圈處理：</span><span class="sxs-lookup"><span data-stu-id="38b83-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="38b83-189">**步驟值**</span><span class="sxs-lookup"><span data-stu-id="38b83-189">**Step value**</span></span>|<span data-ttu-id="38b83-190">**迴圈執行（如果**</span><span class="sxs-lookup"><span data-stu-id="38b83-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="38b83-191">正數或零</span><span class="sxs-lookup"><span data-stu-id="38b83-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="38b83-192">Neutral</span><span class="sxs-lookup"><span data-stu-id="38b83-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="38b83-193">`step` 的預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="38b83-193">The default value of `step` is 1.</span></span>

### <a name="counter-argument"></a><a name="BKMK_Counter"></a><span data-ttu-id="38b83-194">Counter 引數</span><span class="sxs-lookup"><span data-stu-id="38b83-194">Counter Argument</span></span>

<span data-ttu-id="38b83-195">下表指出是否 `counter` 定義範圍為整個迴圈的新本機變數 `For…Next` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="38b83-196">這項決定取決於是否 `datatype` 存在，以及是否 `counter` 已定義。</span><span class="sxs-lookup"><span data-stu-id="38b83-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="38b83-197">`datatype`存在嗎？</span><span class="sxs-lookup"><span data-stu-id="38b83-197">Is `datatype` present?</span></span>|<span data-ttu-id="38b83-198">`counter`已經定義了嗎？</span><span class="sxs-lookup"><span data-stu-id="38b83-198">Is `counter` already defined?</span></span>|<span data-ttu-id="38b83-199">Result （是否 `counter` 定義範圍設定為整個迴圈的新區域變數 `For...Next` ）</span><span class="sxs-lookup"><span data-stu-id="38b83-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="38b83-200">否</span><span class="sxs-lookup"><span data-stu-id="38b83-200">No</span></span>|<span data-ttu-id="38b83-201">是</span><span class="sxs-lookup"><span data-stu-id="38b83-201">Yes</span></span>|<span data-ttu-id="38b83-202">否，因為 `counter` 已經定義過。</span><span class="sxs-lookup"><span data-stu-id="38b83-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="38b83-203">如果的範圍 `counter` 不是程式的本機，就會發生編譯時期警告。</span><span class="sxs-lookup"><span data-stu-id="38b83-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="38b83-204">No</span><span class="sxs-lookup"><span data-stu-id="38b83-204">No</span></span>|<span data-ttu-id="38b83-205">否</span><span class="sxs-lookup"><span data-stu-id="38b83-205">No</span></span>|<span data-ttu-id="38b83-206">是。</span><span class="sxs-lookup"><span data-stu-id="38b83-206">Yes.</span></span> <span data-ttu-id="38b83-207">資料類型是從 `start` 、 `end` 和運算式推斷而來 `step` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="38b83-208">如需型別推斷的詳細資訊，請參閱[Option 推斷語句](option-infer-statement.md)和[區欄位型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="38b83-208">For information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="38b83-209">Yes</span><span class="sxs-lookup"><span data-stu-id="38b83-209">Yes</span></span>|<span data-ttu-id="38b83-210">Yes</span><span class="sxs-lookup"><span data-stu-id="38b83-210">Yes</span></span>|<span data-ttu-id="38b83-211">是，但只有在 `counter` 程式之外定義了現有的變數時。</span><span class="sxs-lookup"><span data-stu-id="38b83-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="38b83-212">該變數會保持不變。</span><span class="sxs-lookup"><span data-stu-id="38b83-212">That variable remains separate.</span></span> <span data-ttu-id="38b83-213">如果現有變數的範圍 `counter` 是程式的本機，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="38b83-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="38b83-214">是</span><span class="sxs-lookup"><span data-stu-id="38b83-214">Yes</span></span>|<span data-ttu-id="38b83-215">否</span><span class="sxs-lookup"><span data-stu-id="38b83-215">No</span></span>|<span data-ttu-id="38b83-216">是。</span><span class="sxs-lookup"><span data-stu-id="38b83-216">Yes.</span></span>|

<span data-ttu-id="38b83-217">的資料類型 `counter` 決定反復專案的類型，必須是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="38b83-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="38b83-218">、、、、、、、、、 `Byte` `SByte` `UShort` `Short` `UInteger` `Integer` `ULong` `Long` `Decimal` `Single` 或 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="38b83-219">使用[Enum 語句](enum-statement.md)宣告的列舉。</span><span class="sxs-lookup"><span data-stu-id="38b83-219">An enumeration that you declare by using an [Enum Statement](enum-statement.md).</span></span>

- <span data-ttu-id="38b83-220">`Object`。</span><span class="sxs-lookup"><span data-stu-id="38b83-220">An `Object`.</span></span>

- <span data-ttu-id="38b83-221">`T`具有下列運算子的類型，其中 `B` 是可以在運算式中使用的類型 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="38b83-222">您可以選擇性地指定 `counter` 語句中的變數 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="38b83-223">此語法可改善程式的可讀性，特別是當您有嵌套的 `For` 迴圈時。</span><span class="sxs-lookup"><span data-stu-id="38b83-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="38b83-224">您必須指定出現在對應語句中的變數 `For` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="38b83-225">`start`、 `end` 和 `step` 運算式可以評估為任何擴大至類型的資料類型 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="38b83-226">如果您使用的使用者定義型別 `counter` ，您可能必須定義 `CType` 轉換運算子，以將、或的類型轉換成的 `start` `end` `step` 類型 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="38b83-227">範例</span><span class="sxs-lookup"><span data-stu-id="38b83-227">Example</span></span>

<span data-ttu-id="38b83-228">下列範例會從泛型清單中移除所有元素。</span><span class="sxs-lookup"><span data-stu-id="38b83-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="38b83-229">而不是[針對每個 .。。下一個語句](for-each-next-statement.md)，此範例會顯示逐一查看 `For` `Next` 遞減順序的 ... 語句。</span><span class="sxs-lookup"><span data-stu-id="38b83-229">Instead of a [For Each...Next Statement](for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="38b83-230">此範例會使用這項技術，因為 `removeAt` 方法會使已移除專案之後的元素具有較低的索引值。</span><span class="sxs-lookup"><span data-stu-id="38b83-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="38b83-231">範例</span><span class="sxs-lookup"><span data-stu-id="38b83-231">Example</span></span>

<span data-ttu-id="38b83-232">下列範例會逐一查看使用[Enum 語句](enum-statement.md)宣告的列舉。</span><span class="sxs-lookup"><span data-stu-id="38b83-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="38b83-233">範例</span><span class="sxs-lookup"><span data-stu-id="38b83-233">Example</span></span>

<span data-ttu-id="38b83-234">在下列範例中，語句參數會使用具有 `+` 、 `-` 、 `>=` 和運算子之運算子多載的類別 `<=` 。</span><span class="sxs-lookup"><span data-stu-id="38b83-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="38b83-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38b83-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="38b83-236">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="38b83-236">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="38b83-237">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="38b83-237">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="38b83-238">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="38b83-238">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="38b83-239">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="38b83-239">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="38b83-240">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="38b83-240">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="38b83-241">集合</span><span class="sxs-lookup"><span data-stu-id="38b83-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
