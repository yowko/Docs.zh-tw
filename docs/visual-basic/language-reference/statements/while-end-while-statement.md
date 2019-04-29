---
title: While...End While 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934221"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="3486e-102">While...End While 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3486e-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="3486e-103">在執行一系列的陳述式，只要指定的條件是`True`。</span><span class="sxs-lookup"><span data-stu-id="3486e-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3486e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3486e-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="3486e-105">組件</span><span class="sxs-lookup"><span data-stu-id="3486e-105">Parts</span></span>  
  
|<span data-ttu-id="3486e-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="3486e-106">Term</span></span>|<span data-ttu-id="3486e-107">定義</span><span class="sxs-lookup"><span data-stu-id="3486e-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="3486e-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="3486e-108">Required.</span></span> <span data-ttu-id="3486e-109">`Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="3486e-109">`Boolean` expression.</span></span> <span data-ttu-id="3486e-110">如果`condition`已`Nothing`，Visual Basic 會將其視為`False`。</span><span class="sxs-lookup"><span data-stu-id="3486e-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="3486e-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3486e-111">Optional.</span></span> <span data-ttu-id="3486e-112">一或多個陳述式的下列`While`，每次執行所在`condition`是`True`。</span><span class="sxs-lookup"><span data-stu-id="3486e-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="3486e-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3486e-113">Optional.</span></span> <span data-ttu-id="3486e-114">將控制權轉移到下一個反覆運算`While`區塊。</span><span class="sxs-lookup"><span data-stu-id="3486e-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="3486e-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3486e-115">Optional.</span></span> <span data-ttu-id="3486e-116">控制權轉移共`While`區塊。</span><span class="sxs-lookup"><span data-stu-id="3486e-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="3486e-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="3486e-117">Required.</span></span> <span data-ttu-id="3486e-118">終止 `While` 區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="3486e-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3486e-119">備註</span><span class="sxs-lookup"><span data-stu-id="3486e-119">Remarks</span></span>  
 <span data-ttu-id="3486e-120">使用`While...End While`結構，當您想要重複執行一組陳述式的不限數目的次數，只要在條件仍`True`。</span><span class="sxs-lookup"><span data-stu-id="3486e-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="3486e-121">如果您想要更多的彈性，與您用來測試條件或何種結果測試它，您可能會偏好[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3486e-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="3486e-122">如果您想要重複陳述式的次數，固定數目[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="3486e-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3486e-123">`While`關鍵字也會在[執行...迴圈陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)，則[Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)並[Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="3486e-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="3486e-124">如果`condition`已`True`，則所有的`statements`執行直到`End While`遇到陳述式。</span><span class="sxs-lookup"><span data-stu-id="3486e-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="3486e-125">控制然後返回`While`陳述式，和`condition`再次檢查。</span><span class="sxs-lookup"><span data-stu-id="3486e-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="3486e-126">如果`condition`仍然是`True`，程序會重複。</span><span class="sxs-lookup"><span data-stu-id="3486e-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="3486e-127">如果有`False`，控制傳遞到後面的陳述式`End While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3486e-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="3486e-128">`While`陳述式一律會檢查條件，再開始迴圈。</span><span class="sxs-lookup"><span data-stu-id="3486e-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="3486e-129">迴圈會繼續條件維持`True`。</span><span class="sxs-lookup"><span data-stu-id="3486e-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="3486e-130">如果`condition`是`False`時第一次，就會進入迴圈，它不會執行一次。</span><span class="sxs-lookup"><span data-stu-id="3486e-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="3486e-131">`condition`通常比較的兩個值，但它的結果可以是任何運算式，評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。</span><span class="sxs-lookup"><span data-stu-id="3486e-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="3486e-132">這個運算式可以包含其他資料類型，已轉換成數值類型，例如值`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="3486e-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="3486e-133">您可以巢狀`While`加上另一個迴圈內的迴圈。</span><span class="sxs-lookup"><span data-stu-id="3486e-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="3486e-134">您也可以巢狀不同類型的另一個控制結構。</span><span class="sxs-lookup"><span data-stu-id="3486e-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="3486e-135">如需詳細資訊，請參閱 <<c0> [ 巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="3486e-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="3486e-136">結束時</span><span class="sxs-lookup"><span data-stu-id="3486e-136">Exit While</span></span>  
 <span data-ttu-id="3486e-137">[結束時](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供另一種方式結束`While`迴圈。</span><span class="sxs-lookup"><span data-stu-id="3486e-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="3486e-138">`Exit While` 立即將控制權傳輸至後面的陳述式`End While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3486e-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="3486e-139">您通常會使用`Exit While`某些條件會評估之後 (例如，在`If...Then...Else`結構)。</span><span class="sxs-lookup"><span data-stu-id="3486e-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="3486e-140">您可能想要結束迴圈，如果偵測到的條件，就不需要或無法繼續反覆執行，例如錯誤的數值或終止要求。</span><span class="sxs-lookup"><span data-stu-id="3486e-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="3486e-141">您可以使用`Exit While`當您測試的條件，可能會導致*永無止盡的迴圈*，即無法執行極大或甚至是無限次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="3486e-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="3486e-142">您可以接著使用`Exit While`來逸出迴圈。</span><span class="sxs-lookup"><span data-stu-id="3486e-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="3486e-143">您可以將任意數目的放`Exit While`任何一處陳述式中的`While`迴圈。</span><span class="sxs-lookup"><span data-stu-id="3486e-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="3486e-144">使用時內巢狀`While`迴圈，`Exit While`控制權出最內層的迴圈並進入下一個較高的層級，巢狀。</span><span class="sxs-lookup"><span data-stu-id="3486e-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="3486e-145">`Continue While`陳述式立即將控制權轉移到迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="3486e-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="3486e-146">如需詳細資訊，請參閱 < [Continue 陳述式](../../../visual-basic/language-reference/statements/continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3486e-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3486e-147">範例</span><span class="sxs-lookup"><span data-stu-id="3486e-147">Example</span></span>  
 <span data-ttu-id="3486e-148">下列範例中，在迴圈中的陳述式會繼續執行，直到`index`變數是否大於 10。</span><span class="sxs-lookup"><span data-stu-id="3486e-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="3486e-149">範例</span><span class="sxs-lookup"><span data-stu-id="3486e-149">Example</span></span>  
 <span data-ttu-id="3486e-150">下列範例示範如何將`Continue While`和`Exit While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3486e-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="3486e-151">範例</span><span class="sxs-lookup"><span data-stu-id="3486e-151">Example</span></span>  
 <span data-ttu-id="3486e-152">下列範例會讀取文字檔案中的所有行。</span><span class="sxs-lookup"><span data-stu-id="3486e-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="3486e-153"><xref:System.IO.File.OpenText%2A>方法會開啟檔案，並傳回<xref:System.IO.StreamReader>讀取字元。</span><span class="sxs-lookup"><span data-stu-id="3486e-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="3486e-154">在 `While`條件<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷檔案是否包含額外的字元。</span><span class="sxs-lookup"><span data-stu-id="3486e-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="3486e-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3486e-155">See also</span></span>

- [<span data-ttu-id="3486e-156">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="3486e-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="3486e-157">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="3486e-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="3486e-158">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="3486e-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3486e-159">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="3486e-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="3486e-160">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="3486e-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="3486e-161">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="3486e-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="3486e-162">Continue 陳述式</span><span class="sxs-lookup"><span data-stu-id="3486e-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
