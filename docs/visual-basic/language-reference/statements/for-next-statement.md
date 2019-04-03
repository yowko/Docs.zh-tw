---
title: For...Next 陳述式 (Visual Basic)
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
ms.openlocfilehash: 5d47d57b75005d5c13dbf8633981dfb2d57d3e90
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826323"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="6b5d0-102">For...Next 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b5d0-102">For...Next Statement (Visual Basic)</span></span>
<span data-ttu-id="6b5d0-103">一組陳述式會重複指定的次數。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-103">Repeats a group of statements a specified number of times.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b5d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b5d0-104">Syntax</span></span>  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a><span data-ttu-id="6b5d0-105">組件</span><span class="sxs-lookup"><span data-stu-id="6b5d0-105">Parts</span></span>  
  
|<span data-ttu-id="6b5d0-106">組件</span><span class="sxs-lookup"><span data-stu-id="6b5d0-106">Part</span></span>|<span data-ttu-id="6b5d0-107">描述</span><span class="sxs-lookup"><span data-stu-id="6b5d0-107">Description</span></span>|  
|----------|-----------------|  
|`counter`|<span data-ttu-id="6b5d0-108">需要`For`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-108">Required in the `For` statement.</span></span> <span data-ttu-id="6b5d0-109">數值變數。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-109">Numeric variable.</span></span> <span data-ttu-id="6b5d0-110">For 迴圈控制變數。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-110">The control variable for the loop.</span></span> <span data-ttu-id="6b5d0-111">如需詳細資訊，請參閱 < [Counter 引數](#BKMK_Counter)本主題稍後的。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|  
|`datatype`|<span data-ttu-id="6b5d0-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-112">Optional.</span></span> <span data-ttu-id="6b5d0-113">資料類型的`counter`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-113">Data type of `counter`.</span></span> <span data-ttu-id="6b5d0-114">如需詳細資訊，請參閱 < [Counter 引數](#BKMK_Counter)本主題稍後的。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|  
|`start`|<span data-ttu-id="6b5d0-115">必要項。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-115">Required.</span></span> <span data-ttu-id="6b5d0-116">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-116">Numeric expression.</span></span> <span data-ttu-id="6b5d0-117">`counter` 的初始值。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-117">The initial value of `counter`.</span></span>|  
|`end`|<span data-ttu-id="6b5d0-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-118">Required.</span></span> <span data-ttu-id="6b5d0-119">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-119">Numeric expression.</span></span> <span data-ttu-id="6b5d0-120">最終值`counter`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-120">The final value of `counter`.</span></span>|  
|`step`|<span data-ttu-id="6b5d0-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-121">Optional.</span></span> <span data-ttu-id="6b5d0-122">數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-122">Numeric expression.</span></span> <span data-ttu-id="6b5d0-123">所用的數量`counter`會遞增每次執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-123">The amount by which `counter` is incremented each time through the loop.</span></span>|  
|`statements`|<span data-ttu-id="6b5d0-124">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-124">Optional.</span></span> <span data-ttu-id="6b5d0-125">一或多個陳述式之間`For`和`Next`執行指定重試次數。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|  
|`Continue For`|<span data-ttu-id="6b5d0-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-126">Optional.</span></span> <span data-ttu-id="6b5d0-127">將控制權傳輸至下一個迴圈反覆項目。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-127">Transfers control to the next loop iteration.</span></span>|  
|`Exit For`|<span data-ttu-id="6b5d0-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-128">Optional.</span></span> <span data-ttu-id="6b5d0-129">控制權轉移共`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-129">Transfers control out of the `For` loop.</span></span>|  
|`Next`|<span data-ttu-id="6b5d0-130">必要項。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-130">Required.</span></span> <span data-ttu-id="6b5d0-131">結束的定義`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-131">Terminates the definition of the `For` loop.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6b5d0-132">`To`關鍵字用以在此陳述式中指定計數器的範圍。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="6b5d0-133">您也可以使用這個關鍵字在[選取...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)和陣列宣告中。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="6b5d0-134">如需陣列宣告的詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="simple-examples"></a><span data-ttu-id="6b5d0-135">簡單的範例</span><span class="sxs-lookup"><span data-stu-id="6b5d0-135">Simple Examples</span></span>  
 <span data-ttu-id="6b5d0-136">您使用`For`...`Next`結構，當您想要重複執行陳述式的一組固定數目的時間。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>  
  
 <span data-ttu-id="6b5d0-137">在下列範例中，`index`變數的值為 1 以開頭，且會隨著每次反覆運算迴圈時，結束之後的值`index`達到 5。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 <span data-ttu-id="6b5d0-138">在下列範例中，`number`變數開始 2，並在每次反覆運算迴圈時，結束之後的值 0.25 可降低`number`到達 0。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="6b5d0-139">`Step`引數`-.25`減少 0.25 迴圈的每個反覆運算上的值。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  <span data-ttu-id="6b5d0-140">A[時...While 陳述式結束](../../../visual-basic/language-reference/statements/while-end-while-statement.md)或[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)非常適合在不知道事先多少次，在迴圈中執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="6b5d0-141">不過，當您預期要執行迴圈以特定次數， `For`...`Next`迴圈是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="6b5d0-142">當您第一次輸入迴圈時，您可以判斷反覆項目的數目。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-142">You determine the number of iterations when you first enter the loop.</span></span>  
  
## <a name="nesting-loops"></a><span data-ttu-id="6b5d0-143">巢狀迴圈</span><span class="sxs-lookup"><span data-stu-id="6b5d0-143">Nesting Loops</span></span>  
 <span data-ttu-id="6b5d0-144">您可以巢狀`For`放在另一個迴圈的迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="6b5d0-145">下列範例會示範巢狀`For`...`Next`具有不同步驟值的結構。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="6b5d0-146">外部迴圈會建立迴圈的每個反覆項目的字串。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="6b5d0-147">「 內部迴圈遞減迴圈計數器變數的迴圈的每個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 <span data-ttu-id="6b5d0-148">當建立巢狀迴圈，每個迴圈必須具有唯一`counter`變數。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>  
  
 <span data-ttu-id="6b5d0-149">您也可以巢狀內彼此不同種類的控制結構。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="6b5d0-150">如需詳細資訊，請參閱 <<c0> [ 巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-for-and-continue-for"></a><span data-ttu-id="6b5d0-151">針對結束後繼續</span><span class="sxs-lookup"><span data-stu-id="6b5d0-151">Exit For and Continue For</span></span>  
 <span data-ttu-id="6b5d0-152">`Exit For`陳述式會立即結束`For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="6b5d0-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="6b5d0-153">後面的陳述式的迴圈和傳輸控制項`Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>  
  
 <span data-ttu-id="6b5d0-154">`Continue For`陳述式控制將立即轉移到迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="6b5d0-155">如需詳細資訊，請參閱 < [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
 <span data-ttu-id="6b5d0-156">下列範例示範如何將`Continue For`和`Exit For`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 <span data-ttu-id="6b5d0-157">您可以將任意數目的放`Exit For`中的陳述式`For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="6b5d0-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="6b5d0-158">迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-158">loop.</span></span> <span data-ttu-id="6b5d0-159">當用在巢狀`For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="6b5d0-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="6b5d0-160">迴圈、`Exit For`結束最內層的迴圈，並將控制權傳輸至下一個較高的層級，巢狀。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="6b5d0-161">`Exit For` 通常用在您評估某些條件後 (例如，在`If`...`Then`...`Else`結構)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="6b5d0-162">您可能想要使用`Exit For`下列條件：</span><span class="sxs-lookup"><span data-stu-id="6b5d0-162">You might want to use `Exit For` for the following conditions:</span></span>  
  
-   <span data-ttu-id="6b5d0-163">繼續向逐一查看是不必要或不可能。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="6b5d0-164">錯誤的數值或終止要求可能會建立這種情況。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-164">An erroneous value or a termination request might create this condition.</span></span>  
  
-   <span data-ttu-id="6b5d0-165">A `Try`...`Catch`...`Finally`陳述式攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="6b5d0-166">您可以使用`Exit For`結尾的`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-166">You might use `Exit For` at the end of the `Finally` block.</span></span>  
  
-   <span data-ttu-id="6b5d0-167">您有無止盡的迴圈，也就是無法執行大型或甚至是無限次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="6b5d0-168">如果您偵測到這種情況，您可以使用`Exit For`來逸出迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="6b5d0-169">如需詳細資訊，請參閱[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="6b5d0-170">技術實作</span><span class="sxs-lookup"><span data-stu-id="6b5d0-170">Technical Implementation</span></span>  
 <span data-ttu-id="6b5d0-171">當`For`...`Next`迴圈開始，Visual Basic 會評估`start`， `end`，和`step`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="6b5d0-172">Visual Basic 會評估這些值只能在此時間，然後指派`start`至`counter`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="6b5d0-173">之前的陳述式區塊會執行，Visual Basic 比較`counter`至`end`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="6b5d0-174">如果`counter`已經是大於`end`值 (或較小的 if`step`為負數)，則`For`迴圈結束，並控制傳遞到後面的陳述式`Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="6b5d0-175">否則，會執行陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-175">Otherwise, the statement block runs.</span></span>  
  
 <span data-ttu-id="6b5d0-176">每次 Visual Basic 遇到`Next`陳述式，就會自動遞增`counter`由`step`，並返回`For`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="6b5d0-177">再次比較`counter`至`end`，和一次它執行的區塊或結束迴圈時，根據結果。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="6b5d0-178">此程序一直`counter`通過`end`或`Exit For`遇到陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>  
  
 <span data-ttu-id="6b5d0-179">迴圈不停止直到`counter`已經過`end`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="6b5d0-180">如果`counter`等於`end`，迴圈會繼續。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="6b5d0-181">比較，決定是否要執行區塊會`counter`  <=  `end`如果`step`正並`counter`  >=  `end`如果`step`為負數。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>  
  
 <span data-ttu-id="6b5d0-182">如果您變更的值`counter`在迴圈中，內您的程式碼可能會更難閱讀及偵錯。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="6b5d0-183">變更的值`start`， `end`，或`step`並不會影響所決定時初次進入迴圈的反覆項目值。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>  
  
 <span data-ttu-id="6b5d0-184">如果您使用巢狀迴圈，編譯器會發出錯誤信號如果遇到`Next`陳述式的外部的巢狀層級之前`Next`內部層級的陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="6b5d0-185">不過，編譯器可以偵測此重疊錯誤，只有當您指定`counter`在每個`Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>  
  
### <a name="step-argument"></a><span data-ttu-id="6b5d0-186">步驟引數</span><span class="sxs-lookup"><span data-stu-id="6b5d0-186">Step Argument</span></span>  
 <span data-ttu-id="6b5d0-187">值`step`可以是正數或負數。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="6b5d0-188">這個參數會決定迴圈處理，根據下表：</span><span class="sxs-lookup"><span data-stu-id="6b5d0-188">This parameter determines loop processing according to the following table:</span></span>  
  
|<span data-ttu-id="6b5d0-189">**間距值**</span><span class="sxs-lookup"><span data-stu-id="6b5d0-189">**Step value**</span></span>|<span data-ttu-id="6b5d0-190">**執行迴圈的條件**</span><span class="sxs-lookup"><span data-stu-id="6b5d0-190">**Loop executes if**</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="6b5d0-191">正數或零</span><span class="sxs-lookup"><span data-stu-id="6b5d0-191">Positive or zero</span></span>|`counter` <= `end`|  
|<span data-ttu-id="6b5d0-192">負</span><span class="sxs-lookup"><span data-stu-id="6b5d0-192">Negative</span></span>|`counter` >= `end`|  
  
 <span data-ttu-id="6b5d0-193">預設值`step`為 1。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-193">The default value of `step` is 1.</span></span>  
  
### <a name="BKMK_Counter"></a> <span data-ttu-id="6b5d0-194">Counter 引數</span><span class="sxs-lookup"><span data-stu-id="6b5d0-194">Counter Argument</span></span>  
 <span data-ttu-id="6b5d0-195">下表會指出是否`counter`定義新的本機變數的範圍是整個`For…Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="6b5d0-196">這個決定取決於是否`datatype`存在以及是否`counter`已經定義。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>  
  
|<span data-ttu-id="6b5d0-197">是`datatype`存在？</span><span class="sxs-lookup"><span data-stu-id="6b5d0-197">Is `datatype` present?</span></span>|<span data-ttu-id="6b5d0-198">是`counter`已經定義嗎？</span><span class="sxs-lookup"><span data-stu-id="6b5d0-198">Is `counter` already defined?</span></span>|<span data-ttu-id="6b5d0-199">結果 (是否`counter`定義新的本機變數的範圍是整個`For...Next`迴圈)</span><span class="sxs-lookup"><span data-stu-id="6b5d0-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="6b5d0-200">否</span><span class="sxs-lookup"><span data-stu-id="6b5d0-200">No</span></span>|<span data-ttu-id="6b5d0-201">是</span><span class="sxs-lookup"><span data-stu-id="6b5d0-201">Yes</span></span>|<span data-ttu-id="6b5d0-202">否，因為`counter`已經定義。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="6b5d0-203">如果範圍`counter`不是本機程序，就會發生編譯時期警告。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|  
|<span data-ttu-id="6b5d0-204">否</span><span class="sxs-lookup"><span data-stu-id="6b5d0-204">No</span></span>|<span data-ttu-id="6b5d0-205">否</span><span class="sxs-lookup"><span data-stu-id="6b5d0-205">No</span></span>|<span data-ttu-id="6b5d0-206">可以。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-206">Yes.</span></span> <span data-ttu-id="6b5d0-207">資料類型從推斷`start`， `end`，和`step`運算式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="6b5d0-208">型別推斷的相關資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)並[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|  
|<span data-ttu-id="6b5d0-209">是</span><span class="sxs-lookup"><span data-stu-id="6b5d0-209">Yes</span></span>|<span data-ttu-id="6b5d0-210">是</span><span class="sxs-lookup"><span data-stu-id="6b5d0-210">Yes</span></span>|<span data-ttu-id="6b5d0-211">可以，但只有當現有`counter`變數定義在程序之外。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="6b5d0-212">該變數會維持獨立的。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-212">That variable remains separate.</span></span> <span data-ttu-id="6b5d0-213">如果現有的範圍`counter`變數是本機程序，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="6b5d0-214">是</span><span class="sxs-lookup"><span data-stu-id="6b5d0-214">Yes</span></span>|<span data-ttu-id="6b5d0-215">否</span><span class="sxs-lookup"><span data-stu-id="6b5d0-215">No</span></span>|<span data-ttu-id="6b5d0-216">可以。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-216">Yes.</span></span>|  
  
 <span data-ttu-id="6b5d0-217">資料類型`counter`決定反覆項目，必須是下列類型的其中一種：</span><span class="sxs-lookup"><span data-stu-id="6b5d0-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>  
  
-   <span data-ttu-id="6b5d0-218">A `Byte`， `SByte`， `UShort`， `Short`， `UInteger`， `Integer`， `ULong`， `Long`， `Decimal`， `Single`，或`Double`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>  
  
-   <span data-ttu-id="6b5d0-219">您使用宣告列舉[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
-   <span data-ttu-id="6b5d0-220">`Object`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-220">An `Object`.</span></span>  
  
-   <span data-ttu-id="6b5d0-221">型別`T`具有下列的運算子，其中`B`是類型，可用於`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 <span data-ttu-id="6b5d0-222">您可以選擇性地指定`counter`變數中`Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="6b5d0-223">此語法可改善可讀性的程式碼，尤其是如果您有巢狀`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="6b5d0-224">您必須指定此變數會出現在對應`For`陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>  
  
 <span data-ttu-id="6b5d0-225">`start`， `end`，並`step`運算式可以評估為任何資料類型可擴展成的型別`counter`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="6b5d0-226">如果您使用的使用者定義類型`counter`，您可能必須定義`CType`轉換運算子的類型轉換成`start`， `end`，或`step`的型別`counter`。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b5d0-227">範例</span><span class="sxs-lookup"><span data-stu-id="6b5d0-227">Example</span></span>  
 <span data-ttu-id="6b5d0-228">下列範例會移除的泛型清單中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="6b5d0-229">而不是[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)，此範例將示範`For`...`Next`以遞減順序反覆運算的陳述式。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="6b5d0-230">此範例會使用這項技術，因為`removeAt`方法導致項目後面移除的項目具有較低的索引值。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a><span data-ttu-id="6b5d0-231">範例</span><span class="sxs-lookup"><span data-stu-id="6b5d0-231">Example</span></span>  
 <span data-ttu-id="6b5d0-232">下列範例會逐一宣告可透過列舉[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a><span data-ttu-id="6b5d0-233">範例</span><span class="sxs-lookup"><span data-stu-id="6b5d0-233">Example</span></span>  
 <span data-ttu-id="6b5d0-234">在下列範例中，陳述式參數使用類別，具有的運算子多載`+`， `-`， `>=`，和`<=`運算子。</span><span class="sxs-lookup"><span data-stu-id="6b5d0-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="6b5d0-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b5d0-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="6b5d0-236">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="6b5d0-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="6b5d0-237">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b5d0-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="6b5d0-238">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b5d0-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="6b5d0-239">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="6b5d0-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="6b5d0-240">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="6b5d0-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="6b5d0-241">集合</span><span class="sxs-lookup"><span data-stu-id="6b5d0-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
