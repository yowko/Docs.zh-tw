---
title: Do...Loop 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 9384cbb355189be448fa4b8d274721b4a7ca6a20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351247"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="3c56b-102">Do...Loop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c56b-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="3c56b-103">當 `Boolean` 條件 `True` 或直到條件變成 `True`時，重複語句區塊。</span><span class="sxs-lookup"><span data-stu-id="3c56b-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c56b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c56b-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="3c56b-105">組件</span><span class="sxs-lookup"><span data-stu-id="3c56b-105">Parts</span></span>  
  
|<span data-ttu-id="3c56b-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="3c56b-106">Term</span></span>|<span data-ttu-id="3c56b-107">定義</span><span class="sxs-lookup"><span data-stu-id="3c56b-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="3c56b-108">必要。</span><span class="sxs-lookup"><span data-stu-id="3c56b-108">Required.</span></span> <span data-ttu-id="3c56b-109">啟動 `Do` 迴圈的定義。</span><span class="sxs-lookup"><span data-stu-id="3c56b-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="3c56b-110">除非使用 `Until`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="3c56b-110">Required unless `Until` is used.</span></span> <span data-ttu-id="3c56b-111">重複執行迴圈，直到 `False``condition` 為止。</span><span class="sxs-lookup"><span data-stu-id="3c56b-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="3c56b-112">除非使用 `While`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="3c56b-112">Required unless `While` is used.</span></span> <span data-ttu-id="3c56b-113">重複執行迴圈，直到 `True``condition` 為止。</span><span class="sxs-lookup"><span data-stu-id="3c56b-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="3c56b-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3c56b-114">Optional.</span></span> <span data-ttu-id="3c56b-115">`Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="3c56b-115">`Boolean` expression.</span></span> <span data-ttu-id="3c56b-116">如果 `Nothing``condition`，Visual Basic 會將它視為 `False`。</span><span class="sxs-lookup"><span data-stu-id="3c56b-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="3c56b-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3c56b-117">Optional.</span></span> <span data-ttu-id="3c56b-118">一或多個在 `condition` `True`時重複的語句。</span><span class="sxs-lookup"><span data-stu-id="3c56b-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="3c56b-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3c56b-119">Optional.</span></span> <span data-ttu-id="3c56b-120">將控制權轉移至 `Do` 迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="3c56b-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="3c56b-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3c56b-121">Optional.</span></span> <span data-ttu-id="3c56b-122">將控制權轉移 `Do` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="3c56b-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="3c56b-123">必要。</span><span class="sxs-lookup"><span data-stu-id="3c56b-123">Required.</span></span> <span data-ttu-id="3c56b-124">結束 `Do` 迴圈的定義。</span><span class="sxs-lookup"><span data-stu-id="3c56b-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c56b-125">備註</span><span class="sxs-lookup"><span data-stu-id="3c56b-125">Remarks</span></span>  
 <span data-ttu-id="3c56b-126">當您想要重複一組不限次數的語句，直到滿足條件為止，請使用 `Do...Loop` 結構。</span><span class="sxs-lookup"><span data-stu-id="3c56b-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="3c56b-127">如果您想要重複語句[設定的次數，請將 .。。下一個語句](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="3c56b-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="3c56b-128">您可以使用 `While` 或 `Until` 來指定 `condition`，而不是兩者。</span><span class="sxs-lookup"><span data-stu-id="3c56b-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="3c56b-129">您只能在迴圈的開頭或結尾測試一次 `condition`。</span><span class="sxs-lookup"><span data-stu-id="3c56b-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="3c56b-130">如果您在迴圈開始時測試 `condition` （在 `Do` 語句中），迴圈可能不會執行一次。</span><span class="sxs-lookup"><span data-stu-id="3c56b-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="3c56b-131">如果您在迴圈結尾（在 `Loop` 語句中）進行測試，迴圈一律至少會執行一次。</span><span class="sxs-lookup"><span data-stu-id="3c56b-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="3c56b-132">此條件的結果通常是兩個值的比較，但它可以是評估為[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值（`True` 或 `False`）的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="3c56b-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="3c56b-133">這包括已轉換成 `Boolean`之其他資料類型（例如數數值型別）的值。</span><span class="sxs-lookup"><span data-stu-id="3c56b-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="3c56b-134">您可以藉由將一個迴圈放在另一個迴圈中，來將 `Do` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="3c56b-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="3c56b-135">您也可以在彼此之間嵌套不同類型的控制結構。</span><span class="sxs-lookup"><span data-stu-id="3c56b-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="3c56b-136">如需詳細資訊，請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="3c56b-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c56b-137">`Do...Loop` 結構提供比 While 更大的彈性 ... [End While 語句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)，因為它可讓您決定在 `condition` 停止 `True` 或第一次變成 `True`時，是否要結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="3c56b-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="3c56b-138">它也可讓您測試迴圈開始或結束時的 `condition`。</span><span class="sxs-lookup"><span data-stu-id="3c56b-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="3c56b-139">Exit Do</span><span class="sxs-lookup"><span data-stu-id="3c56b-139">Exit Do</span></span>  
 <span data-ttu-id="3c56b-140">[Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)語句可以提供結束 `Do…Loop`的替代方式。</span><span class="sxs-lookup"><span data-stu-id="3c56b-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="3c56b-141">`Exit Do` 會立即將控制權轉移到 `Loop` 語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="3c56b-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="3c56b-142">在評估某些條件（例如在 `If...Then...Else` 結構中）時，通常會使用 `Exit Do`。</span><span class="sxs-lookup"><span data-stu-id="3c56b-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="3c56b-143">如果您偵測到不必要或無法繼續反覆運算的條件（例如錯誤值或終止要求），您可能會想要結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="3c56b-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="3c56b-144">`Exit Do` 的其中一種用途是測試可能導致無止盡*迴圈*的條件，這是一種迴圈，可能會執行很長或無限次的次數。</span><span class="sxs-lookup"><span data-stu-id="3c56b-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="3c56b-145">您可以使用 `Exit Do` 來 escape 迴圈。</span><span class="sxs-lookup"><span data-stu-id="3c56b-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="3c56b-146">您可以在 `Do…Loop`中的任何位置包含任意數目的 `Exit Do` 語句。</span><span class="sxs-lookup"><span data-stu-id="3c56b-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="3c56b-147">在嵌套 `Do` 迴圈中使用時，`Exit Do` 會將控制權從最內層的迴圈轉移到下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="3c56b-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c56b-148">範例</span><span class="sxs-lookup"><span data-stu-id="3c56b-148">Example</span></span>  
 <span data-ttu-id="3c56b-149">在下列範例中，迴圈中的語句會繼續執行，直到 `index` 變數大於10為止。</span><span class="sxs-lookup"><span data-stu-id="3c56b-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="3c56b-150">`Until` 子句位於迴圈的結尾。</span><span class="sxs-lookup"><span data-stu-id="3c56b-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="3c56b-151">範例</span><span class="sxs-lookup"><span data-stu-id="3c56b-151">Example</span></span>  
 <span data-ttu-id="3c56b-152">下列範例會使用 `While` 子句，而不是 `Until` 子句，而且 `condition` 會在迴圈開始時進行測試，而不是在結尾處進行測試。</span><span class="sxs-lookup"><span data-stu-id="3c56b-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="3c56b-153">範例</span><span class="sxs-lookup"><span data-stu-id="3c56b-153">Example</span></span>  
 <span data-ttu-id="3c56b-154">在下列範例中，當 `index` 變數大於100時，`condition` 停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="3c56b-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="3c56b-155">不過，迴圈中的 `If` 語句會導致 `Exit Do` 語句在索引變數大於10時停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="3c56b-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="3c56b-156">範例</span><span class="sxs-lookup"><span data-stu-id="3c56b-156">Example</span></span>  
 <span data-ttu-id="3c56b-157">下列範例會讀取文字檔中的所有行。</span><span class="sxs-lookup"><span data-stu-id="3c56b-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="3c56b-158"><xref:System.IO.File.OpenText%2A> 方法會開啟檔案，並傳回讀取字元的 <xref:System.IO.StreamReader>。</span><span class="sxs-lookup"><span data-stu-id="3c56b-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="3c56b-159">在 `Do...Loop` 條件中，`StreamReader` 的 <xref:System.IO.StreamReader.Peek%2A> 方法會決定是否有任何額外的字元。</span><span class="sxs-lookup"><span data-stu-id="3c56b-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="3c56b-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c56b-160">See also</span></span>

- [<span data-ttu-id="3c56b-161">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="3c56b-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="3c56b-162">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c56b-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3c56b-163">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="3c56b-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="3c56b-164">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="3c56b-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="3c56b-165">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c56b-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="3c56b-166">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c56b-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
