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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965804"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="df937-102">While...End While 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df937-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="df937-103">只要指定的條件為, 就會`True`執行一連串的語句。</span><span class="sxs-lookup"><span data-stu-id="df937-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df937-104">語法</span><span class="sxs-lookup"><span data-stu-id="df937-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="df937-105">組件</span><span class="sxs-lookup"><span data-stu-id="df937-105">Parts</span></span>  
  
|<span data-ttu-id="df937-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="df937-106">Term</span></span>|<span data-ttu-id="df937-107">定義</span><span class="sxs-lookup"><span data-stu-id="df937-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="df937-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="df937-108">Required.</span></span> <span data-ttu-id="df937-109">`Boolean`運算式.</span><span class="sxs-lookup"><span data-stu-id="df937-109">`Boolean` expression.</span></span> <span data-ttu-id="df937-110">如果`condition`為`Nothing` ,VisualBasic會`False`將它視為。</span><span class="sxs-lookup"><span data-stu-id="df937-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="df937-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="df937-111">Optional.</span></span> <span data-ttu-id="df937-112">後面`While`的一或多個語句, 每次`condition`都會`True`執行。</span><span class="sxs-lookup"><span data-stu-id="df937-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="df937-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="df937-113">Optional.</span></span> <span data-ttu-id="df937-114">將控制權轉移到`While`區塊的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="df937-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="df937-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="df937-115">Optional.</span></span> <span data-ttu-id="df937-116">將`While`控制權傳輸至區塊。</span><span class="sxs-lookup"><span data-stu-id="df937-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="df937-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="df937-117">Required.</span></span> <span data-ttu-id="df937-118">終止 `While` 區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="df937-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df937-119">備註</span><span class="sxs-lookup"><span data-stu-id="df937-119">Remarks</span></span>  
 <span data-ttu-id="df937-120">當您想要重複一組語句而不限次數時 (只要條件仍然存在`True`), 請使用結構。`While...End While`</span><span class="sxs-lookup"><span data-stu-id="df937-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="df937-121">如果您想要在測試條件的位置或測試它的結果時擁有更大的彈性, 您可能會想要 ... [Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="df937-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="df937-122">如果您想要重複語句設定的次數, 請將 ... [下一個語句](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="df937-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df937-123">`While`關鍵字也用於 [...] [Loop 語句](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip while 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)和[Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="df937-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="df937-124">如果`condition` `statements` `End While`為`True`, 則所有執行直到遇到語句為止。</span><span class="sxs-lookup"><span data-stu-id="df937-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="df937-125">控制項接著會回到`While`語句, 並`condition`再次檢查。</span><span class="sxs-lookup"><span data-stu-id="df937-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="df937-126">如果`condition` 仍然`True`是, 則會重複處理常式。</span><span class="sxs-lookup"><span data-stu-id="df937-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="df937-127">如果是`False`, 則控制權會傳遞至`End While`語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="df937-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="df937-128">`While`語句在啟動迴圈之前, 一律會檢查條件。</span><span class="sxs-lookup"><span data-stu-id="df937-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="df937-129">當條件保留`True`時, 迴圈就會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="df937-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="df937-130">`condition` 當您第一次進入迴圈時,它不`False`會執行一次。</span><span class="sxs-lookup"><span data-stu-id="df937-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="df937-131">通常`condition`是兩個值的比較所得到的結果, 但它可以是任何會評估為[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`) 的運算式。</span><span class="sxs-lookup"><span data-stu-id="df937-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="df937-132">這個運算式可以包含另一個資料類型的值, 例如已轉換成`Boolean`的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="df937-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="df937-133">您可以藉`While`由在另一個迴圈內放置迴圈來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="df937-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="df937-134">您也可以將不同種類的控制結構嵌套在另一種。</span><span class="sxs-lookup"><span data-stu-id="df937-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="df937-135">如需詳細資訊, 請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="df937-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="df937-136">結束</span><span class="sxs-lookup"><span data-stu-id="df937-136">Exit While</span></span>  
 <span data-ttu-id="df937-137">[Exit While](../../../visual-basic/language-reference/statements/exit-statement.md)語句可以提供另一個結束迴圈的`While`方式。</span><span class="sxs-lookup"><span data-stu-id="df937-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="df937-138">`Exit While`會立即將`End While`控制權轉移至語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="df937-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="df937-139">您通常會`Exit While`在評估某些條件 (例如, `If...Then...Else`在結構中) 時使用。</span><span class="sxs-lookup"><span data-stu-id="df937-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="df937-140">如果您偵測到不必要或無法繼續反覆運算的條件 (例如錯誤值或終止要求), 您可能會想要結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="df937-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="df937-141">當您測試`Exit While`的條件可能會造成無止盡的*迴圈*時, 您可以使用, 這是一種迴圈, 可以執行極大或甚至無限的次數。</span><span class="sxs-lookup"><span data-stu-id="df937-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="df937-142">然後, 您可以`Exit While`使用來對迴圈進行 escape。</span><span class="sxs-lookup"><span data-stu-id="df937-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="df937-143">您可以將任意數目的`Exit While`語句放`While`在迴圈中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="df937-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="df937-144">在嵌套`While`迴圈中使用時`Exit While` , 會將控制項從最內層的迴圈轉移到下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="df937-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="df937-145">`Continue While`語句會立即將控制權轉移到迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="df937-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="df937-146">如需詳細資訊, 請參閱[Continue 語句](../../../visual-basic/language-reference/statements/continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="df937-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df937-147">範例</span><span class="sxs-lookup"><span data-stu-id="df937-147">Example</span></span>  
 <span data-ttu-id="df937-148">在下列範例中, 迴圈中的語句會繼續執行, 直到`index`變數大於10為止。</span><span class="sxs-lookup"><span data-stu-id="df937-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="df937-149">範例</span><span class="sxs-lookup"><span data-stu-id="df937-149">Example</span></span>  
 <span data-ttu-id="df937-150">下列範例說明如何使用`Continue While`和`Exit While`語句。</span><span class="sxs-lookup"><span data-stu-id="df937-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="df937-151">範例</span><span class="sxs-lookup"><span data-stu-id="df937-151">Example</span></span>  
 <span data-ttu-id="df937-152">下列範例會讀取文字檔中的所有行。</span><span class="sxs-lookup"><span data-stu-id="df937-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="df937-153">方法會開啟檔案, 並<xref:System.IO.StreamReader>傳回讀取字元的。 <xref:System.IO.File.OpenText%2A></span><span class="sxs-lookup"><span data-stu-id="df937-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="df937-154">在條件中<xref:System.IO.StreamReader.Peek%2A> , 的方法`StreamReader`會判斷檔案是否包含額外的字元。 `While`</span><span class="sxs-lookup"><span data-stu-id="df937-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="df937-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df937-155">See also</span></span>

- [<span data-ttu-id="df937-156">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="df937-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="df937-157">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="df937-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="df937-158">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="df937-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="df937-159">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="df937-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="df937-160">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="df937-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="df937-161">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="df937-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="df937-162">Continue 陳述式</span><span class="sxs-lookup"><span data-stu-id="df937-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
