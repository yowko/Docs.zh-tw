---
title: "While...End While 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f831f233eaa4f1c38d56f3a89bda9b0cf1bccaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="28028-102">While...End While 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28028-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="28028-103">執行一系列的陳述式，只要指定的條件為`True`。</span><span class="sxs-lookup"><span data-stu-id="28028-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28028-104">語法</span><span class="sxs-lookup"><span data-stu-id="28028-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="28028-105">組件</span><span class="sxs-lookup"><span data-stu-id="28028-105">Parts</span></span>  
  
|<span data-ttu-id="28028-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="28028-106">Term</span></span>|<span data-ttu-id="28028-107">定義</span><span class="sxs-lookup"><span data-stu-id="28028-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="28028-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="28028-108">Required.</span></span> <span data-ttu-id="28028-109">`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="28028-109">`Boolean` expression.</span></span> <span data-ttu-id="28028-110">如果`condition`是`Nothing`，Visual Basic 會將它視為`False`。</span><span class="sxs-lookup"><span data-stu-id="28028-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="28028-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="28028-111">Optional.</span></span> <span data-ttu-id="28028-112">一或多個陳述式下列`While`，每次執行的`condition`是`True`。</span><span class="sxs-lookup"><span data-stu-id="28028-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="28028-113">選擇項。</span><span class="sxs-lookup"><span data-stu-id="28028-113">Optional.</span></span> <span data-ttu-id="28028-114">將控制項傳送至下一個反覆運算`While`區塊。</span><span class="sxs-lookup"><span data-stu-id="28028-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="28028-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="28028-115">Optional.</span></span> <span data-ttu-id="28028-116">控制權轉移出`While`區塊。</span><span class="sxs-lookup"><span data-stu-id="28028-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="28028-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="28028-117">Required.</span></span> <span data-ttu-id="28028-118">終止 `While` 區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="28028-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28028-119">備註</span><span class="sxs-lookup"><span data-stu-id="28028-119">Remarks</span></span>  
 <span data-ttu-id="28028-120">使用`While...End While`結構時您想要重複一組不定陳述式的次數，只要條件維持`True`。</span><span class="sxs-lookup"><span data-stu-id="28028-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="28028-121">如果您想要更多的彈性與您用來測試條件或何種結果測試它，您可能會偏好[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="28028-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="28028-122">如果您想要重複陳述式的次數， [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是比較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="28028-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28028-123">`While`關鍵字也用於[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)和[Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="28028-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="28028-124">如果`condition`是`True`，則所有的`statements`執行直到`End While`遇到陳述式。</span><span class="sxs-lookup"><span data-stu-id="28028-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="28028-125">控制然後返回`While`陳述式，和`condition`再次檢查。</span><span class="sxs-lookup"><span data-stu-id="28028-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="28028-126">如果`condition`仍然是`True`，程序會重複。</span><span class="sxs-lookup"><span data-stu-id="28028-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="28028-127">如果有`False`，控制傳遞到之後的陳述式`End While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="28028-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="28028-128">`While`陳述式一律會檢查該條件，再開始迴圈。</span><span class="sxs-lookup"><span data-stu-id="28028-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="28028-129">迴圈就會繼續條件維持`True`。</span><span class="sxs-lookup"><span data-stu-id="28028-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="28028-130">如果`condition`是`False`當您第一次輸入迴圈時，它不會執行一次。</span><span class="sxs-lookup"><span data-stu-id="28028-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="28028-131">`condition`通常比較結果的兩個值，但它可以是任何運算式評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。</span><span class="sxs-lookup"><span data-stu-id="28028-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="28028-132">這個運算式可以包含其他資料類型已轉換成數值類型，例如值`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="28028-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="28028-133">您可以巢狀`While`放入另一個迴圈內的迴圈。</span><span class="sxs-lookup"><span data-stu-id="28028-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="28028-134">您也可以巢狀不同類型的另一個控制結構。</span><span class="sxs-lookup"><span data-stu-id="28028-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="28028-135">如需詳細資訊，請參閱[巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="28028-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="28028-136">結束時</span><span class="sxs-lookup"><span data-stu-id="28028-136">Exit While</span></span>  
 <span data-ttu-id="28028-137">[結束時](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供另一種方式結束`While`迴圈。</span><span class="sxs-lookup"><span data-stu-id="28028-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="28028-138">`Exit While`立即將控制權傳輸至之後的陳述式`End While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="28028-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="28028-139">您通常會使用`Exit While`評估某項條件之後 (例如，在`If...Then...Else`結構)。</span><span class="sxs-lookup"><span data-stu-id="28028-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="28028-140">您可能想要結束迴圈，若您偵測到的條件，使得不必要或不可能繼續重複執行，例如錯誤的數值或終止要求。</span><span class="sxs-lookup"><span data-stu-id="28028-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="28028-141">您可以使用`Exit While`當您測試的條件，可能會導致*無止盡迴圈*，即無法執行極大或甚至無限次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="28028-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="28028-142">然後您可以使用`Exit While`來逸出迴圈。</span><span class="sxs-lookup"><span data-stu-id="28028-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="28028-143">您可以將任意數目的`Exit While`隨處陳述式中的`While`迴圈。</span><span class="sxs-lookup"><span data-stu-id="28028-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="28028-144">使用時內巢狀`While`迴圈`Exit While`控制權從最內層的迴圈移至下一個高的層級的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="28028-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="28028-145">`Continue While`陳述式立即將控制權傳輸至迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="28028-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="28028-146">如需詳細資訊，請參閱[Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="28028-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28028-147">範例</span><span class="sxs-lookup"><span data-stu-id="28028-147">Example</span></span>  
 <span data-ttu-id="28028-148">在下列範例中，在迴圈中的陳述式繼續執行直到`index`變數值大於 10。</span><span class="sxs-lookup"><span data-stu-id="28028-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="28028-149">範例</span><span class="sxs-lookup"><span data-stu-id="28028-149">Example</span></span>  
 <span data-ttu-id="28028-150">下列範例說明使用`Continue While`和`Exit While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="28028-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="28028-151">範例</span><span class="sxs-lookup"><span data-stu-id="28028-151">Example</span></span>  
 <span data-ttu-id="28028-152">下列範例會讀取文字檔案中的所有行。</span><span class="sxs-lookup"><span data-stu-id="28028-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="28028-153"><xref:System.IO.File.OpenText%2A>方法開啟的檔案，並傳回<xref:System.IO.StreamReader>讀取的字元。</span><span class="sxs-lookup"><span data-stu-id="28028-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="28028-154">在`While`條件，<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷檔案是否包含額外的字元。</span><span class="sxs-lookup"><span data-stu-id="28028-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="28028-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28028-155">See Also</span></span>  
 [<span data-ttu-id="28028-156">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="28028-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="28028-157">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="28028-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="28028-158">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="28028-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="28028-159">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="28028-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="28028-160">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="28028-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="28028-161">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="28028-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="28028-162">Continue 陳述式</span><span class="sxs-lookup"><span data-stu-id="28028-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
