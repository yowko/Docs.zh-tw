---
title: "Do...Loop 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- "conditional statements [Visual Basic], Do�Loop"
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- "loop structures [Visual Basic], Do�Loop statements"
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79d25dce963f383a84b56ce2c9b600fc2d5a7937
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="f9dee-102">Do...Loop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9dee-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="f9dee-103">持續重複陳述式時區塊`Boolean`條件是`True`或直到條件變成`True`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9dee-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9dee-104">Syntax</span></span>  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="f9dee-105">組件</span><span class="sxs-lookup"><span data-stu-id="f9dee-105">Parts</span></span>  
  
|<span data-ttu-id="f9dee-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f9dee-106">Term</span></span>|<span data-ttu-id="f9dee-107">定義</span><span class="sxs-lookup"><span data-stu-id="f9dee-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="f9dee-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="f9dee-108">Required.</span></span> <span data-ttu-id="f9dee-109">定義的開頭`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="f9dee-110">除非使用 `Until`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="f9dee-110">Required unless `Until` is used.</span></span> <span data-ttu-id="f9dee-111">重複此迴圈直到`condition`是`False`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="f9dee-112">除非使用 `While`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="f9dee-112">Required unless `While` is used.</span></span> <span data-ttu-id="f9dee-113">重複此迴圈直到`condition`是`True`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="f9dee-114">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f9dee-114">Optional.</span></span> <span data-ttu-id="f9dee-115">`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="f9dee-115">`Boolean` expression.</span></span> <span data-ttu-id="f9dee-116">如果`condition`是`Nothing`，Visual Basic 會將它視為`False`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="f9dee-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f9dee-117">Optional.</span></span> <span data-ttu-id="f9dee-118">一或多個陳述式時，或直到，重複的`condition`是`True`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="f9dee-119">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f9dee-119">Optional.</span></span> <span data-ttu-id="f9dee-120">將控制項傳送至下一個反覆運算`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="f9dee-121">選擇項。</span><span class="sxs-lookup"><span data-stu-id="f9dee-121">Optional.</span></span> <span data-ttu-id="f9dee-122">控制權轉移出`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="f9dee-123">必要項。</span><span class="sxs-lookup"><span data-stu-id="f9dee-123">Required.</span></span> <span data-ttu-id="f9dee-124">結束的定義`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9dee-125">備註</span><span class="sxs-lookup"><span data-stu-id="f9dee-125">Remarks</span></span>  
 <span data-ttu-id="f9dee-126">使用`Do...Loop`結構時您想要重複一組不定陳述式的次數，直到滿足條件為止。</span><span class="sxs-lookup"><span data-stu-id="f9dee-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="f9dee-127">如果您想要重複陳述式的次數， [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是比較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="f9dee-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="f9dee-128">您可以使用`While`或`Until`指定`condition`，但非兩者。</span><span class="sxs-lookup"><span data-stu-id="f9dee-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="f9dee-129">您可以測試`condition`僅一次，開頭或結尾的迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="f9dee-130">如果您在測試`condition`迴圈的開頭 (在`Do`陳述式)，在迴圈執行可能甚至一次。</span><span class="sxs-lookup"><span data-stu-id="f9dee-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="f9dee-131">如果您在迴圈結束測試 (在`Loop`陳述式)，迴圈永遠執行至少一次。</span><span class="sxs-lookup"><span data-stu-id="f9dee-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="f9dee-132">條件通常來自兩個值的比較，但它可以是任何運算式評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。</span><span class="sxs-lookup"><span data-stu-id="f9dee-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="f9dee-133">這包括其他資料類型，例如的已轉換成數值類型的值`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="f9dee-134">您可以巢狀`Do`將放入另一個迴圈內的迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="f9dee-135">您也可以巢狀不同類型的其他控制結構。</span><span class="sxs-lookup"><span data-stu-id="f9dee-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="f9dee-136">如需詳細資訊，請參閱[巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="f9dee-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9dee-137">`Do...Loop`結構可讓您更大的彈性比[時...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)因為它可讓您決定是否要結束迴圈時`condition`停止`True`或當它第一次變成`True`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="f9dee-138">它也可讓您測試`condition`開頭或結尾的迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="f9dee-139">結束執行</span><span class="sxs-lookup"><span data-stu-id="f9dee-139">Exit Do</span></span>  
 <span data-ttu-id="f9dee-140">[結束執行](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供替代方式，以結束`Do…Loop`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="f9dee-141">`Exit Do`立即將控制權傳輸至之後的陳述式`Loop`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f9dee-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="f9dee-142">`Exit Do`通常是評估某項條件，例如在之後`If...Then...Else`結構。</span><span class="sxs-lookup"><span data-stu-id="f9dee-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="f9dee-143">您可能想要結束迴圈，若您偵測到的條件，使得不必要或不可能繼續重複執行，例如錯誤的數值或終止要求。</span><span class="sxs-lookup"><span data-stu-id="f9dee-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="f9dee-144">使用一`Exit Do`就是要測試的條件，可能會導致*無止盡迴圈*，即無法執行大型或甚至無限次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="f9dee-145">您可以使用`Exit Do`來逸出迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="f9dee-146">您可以包含任意數目的`Exit Do`隨處陳述式中的`Do…Loop`。</span><span class="sxs-lookup"><span data-stu-id="f9dee-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="f9dee-147">使用時內巢狀`Do`迴圈`Exit Do`控制權從最內層的迴圈移至下一個高的層級的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="f9dee-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dee-148">範例</span><span class="sxs-lookup"><span data-stu-id="f9dee-148">Example</span></span>  
 <span data-ttu-id="f9dee-149">在下列範例中，在迴圈中的陳述式繼續執行直到`index`變數值大於 10。</span><span class="sxs-lookup"><span data-stu-id="f9dee-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="f9dee-150">`Until`子句是在迴圈的結尾。</span><span class="sxs-lookup"><span data-stu-id="f9dee-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="f9dee-151">範例</span><span class="sxs-lookup"><span data-stu-id="f9dee-151">Example</span></span>  
 <span data-ttu-id="f9dee-152">下列範例會使用`While`子句，而不要`Until`子句，和`condition`測試的迴圈，而不是結尾的開頭。</span><span class="sxs-lookup"><span data-stu-id="f9dee-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="f9dee-153">範例</span><span class="sxs-lookup"><span data-stu-id="f9dee-153">Example</span></span>  
 <span data-ttu-id="f9dee-154">在下列範例中，`condition`停止迴圈時`index`變數大於 100。</span><span class="sxs-lookup"><span data-stu-id="f9dee-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="f9dee-155">`If`陳述式在迴圈中，不過，會導致`Exit Do`陳述式來索引變數大於 10 時停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="f9dee-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="f9dee-156">範例</span><span class="sxs-lookup"><span data-stu-id="f9dee-156">Example</span></span>  
 <span data-ttu-id="f9dee-157">下列範例會讀取文字檔案中的所有行。</span><span class="sxs-lookup"><span data-stu-id="f9dee-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="f9dee-158"><xref:System.IO.File.OpenText%2A>方法開啟的檔案，並傳回<xref:System.IO.StreamReader>讀取的字元。</span><span class="sxs-lookup"><span data-stu-id="f9dee-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="f9dee-159">在`Do...Loop`條件，<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷是否有任何額外的字元。</span><span class="sxs-lookup"><span data-stu-id="f9dee-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f9dee-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9dee-160">See Also</span></span>  
 [<span data-ttu-id="f9dee-161">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="f9dee-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="f9dee-162">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="f9dee-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="f9dee-163">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="f9dee-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="f9dee-164">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="f9dee-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="f9dee-165">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="f9dee-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="f9dee-166">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="f9dee-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
