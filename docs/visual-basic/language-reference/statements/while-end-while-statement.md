---
title: While...End While 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: e3ab95f43e101a9ad8abe6fa61b94ae7542e409c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869483"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="9419a-102">While...End While 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9419a-102">While...End While Statement (Visual Basic)</span></span>

<span data-ttu-id="9419a-103">只要指定的條件為，就會執行一連串的語句 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9419a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9419a-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="9419a-105">組件</span><span class="sxs-lookup"><span data-stu-id="9419a-105">Parts</span></span>  
  
|<span data-ttu-id="9419a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="9419a-106">Term</span></span>|<span data-ttu-id="9419a-107">定義</span><span class="sxs-lookup"><span data-stu-id="9419a-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="9419a-108">必要。</span><span class="sxs-lookup"><span data-stu-id="9419a-108">Required.</span></span> <span data-ttu-id="9419a-109">`Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="9419a-109">`Boolean` expression.</span></span> <span data-ttu-id="9419a-110">如果 `condition` 為 `Nothing` ，Visual Basic 會將其視為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="9419a-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9419a-111">Optional.</span></span> <span data-ttu-id="9419a-112">下列一或多個語句 `While` 會在每次執行 `condition` 時執行 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="9419a-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9419a-113">Optional.</span></span> <span data-ttu-id="9419a-114">將控制權傳輸至區塊的下一個反復專案 `While` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="9419a-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9419a-115">Optional.</span></span> <span data-ttu-id="9419a-116">將控制權傳輸至 `While` 區塊。</span><span class="sxs-lookup"><span data-stu-id="9419a-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="9419a-117">必要。</span><span class="sxs-lookup"><span data-stu-id="9419a-117">Required.</span></span> <span data-ttu-id="9419a-118">終止 `While` 區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="9419a-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9419a-119">備註</span><span class="sxs-lookup"><span data-stu-id="9419a-119">Remarks</span></span>  

 <span data-ttu-id="9419a-120">`While...End While`當您想要重複一組語句，但只要條件仍然存在，請使用結構 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="9419a-121">如果您想要在測試條件或測試結果的位置有更大的彈性，您可能會想要 [.。。迴圈語句](do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9419a-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](do-loop-statement.md).</span></span> <span data-ttu-id="9419a-122">如果您想要重複執行語句的次數， [請將下一個語句](for-next-statement.md) 通常是較佳的選擇。</span><span class="sxs-lookup"><span data-stu-id="9419a-122">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9419a-123">`While`關鍵字也可用於[Do .。。Loop 語句](do-loop-statement.md)、 [Skip while 子句](../queries/skip-while-clause.md)和[Take while 子句](../queries/take-while-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="9419a-123">The `While` keyword is also used in the [Do...Loop Statement](do-loop-statement.md), the [Skip While Clause](../queries/skip-while-clause.md) and the [Take While Clause](../queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="9419a-124">如果 `condition` 為 `True` ，則所有 `statements` 執行直到 `End While` 遇到語句為止。</span><span class="sxs-lookup"><span data-stu-id="9419a-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="9419a-125">然後，控制權會返回 `While` 語句，然後 `condition` 再次選取。</span><span class="sxs-lookup"><span data-stu-id="9419a-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="9419a-126">如果 `condition` 仍為 `True` ，則會重複處理常式。</span><span class="sxs-lookup"><span data-stu-id="9419a-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="9419a-127">如果是 `False` ，控制權會傳遞給語句後面的語句 `End While` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="9419a-128">`While`語句在開始迴圈之前，一律會檢查條件。</span><span class="sxs-lookup"><span data-stu-id="9419a-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="9419a-129">當條件維持時，迴圈會繼續 `True` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="9419a-130">如果 `condition` 是 `False` 當您第一次進入迴圈，則不會執行一次。</span><span class="sxs-lookup"><span data-stu-id="9419a-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="9419a-131">`condition`通常會比較兩個值，但它可以是任何評估為[布林資料類型](../data-types/boolean-data-type.md)值的運算式 (`True` 或 `False`) 。</span><span class="sxs-lookup"><span data-stu-id="9419a-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="9419a-132">此運算式可以包含已轉換成之另一個資料類型的值，例如數數值型別 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="9419a-133">您可以藉 `While` 由在另一個迴圈內放置迴圈，來將迴圈嵌套。</span><span class="sxs-lookup"><span data-stu-id="9419a-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="9419a-134">您也可以在彼此之間嵌套不同類型的控制結構。</span><span class="sxs-lookup"><span data-stu-id="9419a-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="9419a-135">如需詳細資訊，請參閱 [嵌套控制項結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="9419a-135">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="9419a-136">離開</span><span class="sxs-lookup"><span data-stu-id="9419a-136">Exit While</span></span>  

 <span data-ttu-id="9419a-137">[Exit While](exit-statement.md)語句可以提供另一種方式來結束 `While` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="9419a-137">The [Exit While](exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="9419a-138">`Exit While` 立即將控制權傳輸至語句後面的語句 `End While` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="9419a-139">您通常 `Exit While` 會在評估某些條件之後使用 (例如，在 `If...Then...Else` 結構) 中。</span><span class="sxs-lookup"><span data-stu-id="9419a-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="9419a-140">如果您偵測到導致不必要或無法繼續反覆運算的條件（例如錯誤值或終止要求），您可能會想要結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="9419a-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="9419a-141">`Exit While`當您測試可能造成無止盡*迴圈*的條件時，可以使用，這是可能執行極大或甚至無限次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="9419a-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="9419a-142">然後，您可以使用 `Exit While` 來對迴圈進行換用。</span><span class="sxs-lookup"><span data-stu-id="9419a-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="9419a-143">您可以將任意數目的 `Exit While` 語句放在迴圈中的任何位置 `While` 。</span><span class="sxs-lookup"><span data-stu-id="9419a-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="9419a-144">在嵌套迴圈中使用時 `While` ，會 `Exit While` 將控制權從最內層的迴圈傳送到下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="9419a-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="9419a-145">`Continue While`語句會立即將控制權轉移到迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="9419a-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="9419a-146">如需詳細資訊，請參閱 [Continue 語句](continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9419a-146">For more information, see [Continue Statement](continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9419a-147">範例</span><span class="sxs-lookup"><span data-stu-id="9419a-147">Example</span></span>  

 <span data-ttu-id="9419a-148">在下列範例中，迴圈中的語句會繼續執行，直到 `index` 變數大於10為止。</span><span class="sxs-lookup"><span data-stu-id="9419a-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="9419a-149">範例</span><span class="sxs-lookup"><span data-stu-id="9419a-149">Example</span></span>  

 <span data-ttu-id="9419a-150">下列範例說明如何使用 `Continue While` 和 `Exit While` 語句。</span><span class="sxs-lookup"><span data-stu-id="9419a-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="9419a-151">範例</span><span class="sxs-lookup"><span data-stu-id="9419a-151">Example</span></span>  

 <span data-ttu-id="9419a-152">下列範例會讀取文字檔中的所有行。</span><span class="sxs-lookup"><span data-stu-id="9419a-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="9419a-153"><xref:System.IO.File.OpenText%2A>方法會開啟檔案，並傳回 <xref:System.IO.StreamReader> 讀取字元的。</span><span class="sxs-lookup"><span data-stu-id="9419a-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="9419a-154">在 `While` 條件中，的 <xref:System.IO.StreamReader.Peek%2A> 方法會判斷檔案 `StreamReader` 是否包含額外的字元。</span><span class="sxs-lookup"><span data-stu-id="9419a-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="9419a-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9419a-155">See also</span></span>

- [<span data-ttu-id="9419a-156">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="9419a-156">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="9419a-157">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="9419a-157">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="9419a-158">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="9419a-158">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="9419a-159">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="9419a-159">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="9419a-160">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="9419a-160">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="9419a-161">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="9419a-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="9419a-162">Continue 陳述式</span><span class="sxs-lookup"><span data-stu-id="9419a-162">Continue Statement</span></span>](continue-statement.md)
