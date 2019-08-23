---
title: Do...Loop 陳述式 (Visual Basic)
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
ms.openlocfilehash: 75a2129a9f332024831d97021e381f1b3d4fa048
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943002"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="441ab-102">Do...Loop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="441ab-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="441ab-103">在`Boolean`條件為`True`或直到條件變成`True`之前, 重複語句區塊。</span><span class="sxs-lookup"><span data-stu-id="441ab-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="441ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="441ab-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="441ab-105">組件</span><span class="sxs-lookup"><span data-stu-id="441ab-105">Parts</span></span>  
  
|<span data-ttu-id="441ab-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="441ab-106">Term</span></span>|<span data-ttu-id="441ab-107">定義</span><span class="sxs-lookup"><span data-stu-id="441ab-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="441ab-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="441ab-108">Required.</span></span> <span data-ttu-id="441ab-109">啟動`Do`迴圈的定義。</span><span class="sxs-lookup"><span data-stu-id="441ab-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="441ab-110">除非使用 `Until`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="441ab-110">Required unless `Until` is used.</span></span> <span data-ttu-id="441ab-111">重複執行迴圈, `condition`直到`False`為為止。</span><span class="sxs-lookup"><span data-stu-id="441ab-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="441ab-112">除非使用 `While`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="441ab-112">Required unless `While` is used.</span></span> <span data-ttu-id="441ab-113">重複執行迴圈, `condition`直到`True`為為止。</span><span class="sxs-lookup"><span data-stu-id="441ab-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="441ab-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="441ab-114">Optional.</span></span> <span data-ttu-id="441ab-115">`Boolean`運算式.</span><span class="sxs-lookup"><span data-stu-id="441ab-115">`Boolean` expression.</span></span> <span data-ttu-id="441ab-116">如果`condition`為`Nothing` ,VisualBasic會`False`將它視為。</span><span class="sxs-lookup"><span data-stu-id="441ab-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="441ab-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="441ab-117">Optional.</span></span> <span data-ttu-id="441ab-118">一或多個在或之前`condition`重複的語句為。 `True`</span><span class="sxs-lookup"><span data-stu-id="441ab-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="441ab-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="441ab-119">Optional.</span></span> <span data-ttu-id="441ab-120">將控制權轉移到`Do`迴圈的下一個反復專案。</span><span class="sxs-lookup"><span data-stu-id="441ab-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="441ab-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="441ab-121">Optional.</span></span> <span data-ttu-id="441ab-122">將`Do`控制權轉移給迴圈。</span><span class="sxs-lookup"><span data-stu-id="441ab-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="441ab-123">必要項。</span><span class="sxs-lookup"><span data-stu-id="441ab-123">Required.</span></span> <span data-ttu-id="441ab-124">終止`Do`迴圈的定義。</span><span class="sxs-lookup"><span data-stu-id="441ab-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="441ab-125">備註</span><span class="sxs-lookup"><span data-stu-id="441ab-125">Remarks</span></span>  
 <span data-ttu-id="441ab-126">當您想要重複一組語句而不限次數時, 請使用結構,直到滿足條件為止。`Do...Loop`</span><span class="sxs-lookup"><span data-stu-id="441ab-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="441ab-127">如果您想要重複語句設定的次數, 請將 ... [下一個語句](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="441ab-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="441ab-128">您可以使用`While`或`Until`來指定`condition`(而非兩者)。</span><span class="sxs-lookup"><span data-stu-id="441ab-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="441ab-129">您只能在`condition`迴圈的開始或結束時測試一次。</span><span class="sxs-lookup"><span data-stu-id="441ab-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="441ab-130">如果您在`condition`迴圈開始時`Do`進行測試 (在語句中), 迴圈可能不會執行一次。</span><span class="sxs-lookup"><span data-stu-id="441ab-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="441ab-131">如果您在迴圈結尾處進行測試 (在`Loop`語句中), 迴圈一律會至少執行一次。</span><span class="sxs-lookup"><span data-stu-id="441ab-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="441ab-132">條件通常是由兩個值的比較所產生, 但它可以是任何會評估為[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`) 的運算式。</span><span class="sxs-lookup"><span data-stu-id="441ab-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="441ab-133">這包括已轉換成`Boolean`的其他資料類型 (例如數數值型別) 的值。</span><span class="sxs-lookup"><span data-stu-id="441ab-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="441ab-134">您可以藉`Do`由在另一個迴圈中放入迴圈來加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="441ab-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="441ab-135">您也可以在彼此之間嵌套不同類型的控制結構。</span><span class="sxs-lookup"><span data-stu-id="441ab-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="441ab-136">如需詳細資訊, 請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="441ab-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="441ab-137">`Do...Loop`結構提供比 While 更多的彈性 ... [End While 語句](../../../visual-basic/language-reference/statements/while-end-while-statement.md), 因為它可讓您決定是否要在停止`condition` `True`時或第一次變成`True`時結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="441ab-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="441ab-138">它也可讓您在`condition`迴圈的開頭或結尾進行測試。</span><span class="sxs-lookup"><span data-stu-id="441ab-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="441ab-139">Exit Do</span><span class="sxs-lookup"><span data-stu-id="441ab-139">Exit Do</span></span>  
 <span data-ttu-id="441ab-140">[Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)語句可以提供另一個結束的`Do…Loop`方式。</span><span class="sxs-lookup"><span data-stu-id="441ab-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="441ab-141">`Exit Do`立即將控制權轉移至`Loop`語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="441ab-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="441ab-142">`Exit Do`通常會在評估部分條件之後使用, 例如在`If...Then...Else`結構中。</span><span class="sxs-lookup"><span data-stu-id="441ab-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="441ab-143">如果您偵測到不必要或無法繼續反覆運算的條件 (例如錯誤值或終止要求), 您可能會想要結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="441ab-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="441ab-144">的`Exit Do`其中一種用途是測試可能導致無止盡*迴圈*的條件, 這是一種迴圈, 可能會執行很長或甚至無限次數。</span><span class="sxs-lookup"><span data-stu-id="441ab-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="441ab-145">您可以使用`Exit Do`來轉義迴圈。</span><span class="sxs-lookup"><span data-stu-id="441ab-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="441ab-146">您可以在中的`Exit Do` `Do…Loop`任何位置包含任意數目的語句。</span><span class="sxs-lookup"><span data-stu-id="441ab-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="441ab-147">在嵌套`Do`迴圈中使用時`Exit Do` , 會將控制項從最內層的迴圈轉移到下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="441ab-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="441ab-148">範例</span><span class="sxs-lookup"><span data-stu-id="441ab-148">Example</span></span>  
 <span data-ttu-id="441ab-149">在下列範例中, 迴圈中的語句會繼續執行, 直到`index`變數大於10為止。</span><span class="sxs-lookup"><span data-stu-id="441ab-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="441ab-150">`Until`子句位於迴圈的結尾。</span><span class="sxs-lookup"><span data-stu-id="441ab-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="441ab-151">範例</span><span class="sxs-lookup"><span data-stu-id="441ab-151">Example</span></span>  
 <span data-ttu-id="441ab-152">下列範例會使用`While`子句 (而非`Until`子句), 並`condition`在迴圈開始時測試, 而不是在結尾處進行測試。</span><span class="sxs-lookup"><span data-stu-id="441ab-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="441ab-153">範例</span><span class="sxs-lookup"><span data-stu-id="441ab-153">Example</span></span>  
 <span data-ttu-id="441ab-154">在下列範例中, `condition` `index`當變數大於100時, 會停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="441ab-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="441ab-155">不過`If` , 迴圈中的語句`Exit Do`會導致語句在索引變數大於10時停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="441ab-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="441ab-156">範例</span><span class="sxs-lookup"><span data-stu-id="441ab-156">Example</span></span>  
 <span data-ttu-id="441ab-157">下列範例會讀取文字檔中的所有行。</span><span class="sxs-lookup"><span data-stu-id="441ab-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="441ab-158">方法會開啟檔案, 並<xref:System.IO.StreamReader>傳回讀取字元的。 <xref:System.IO.File.OpenText%2A></span><span class="sxs-lookup"><span data-stu-id="441ab-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="441ab-159">在條件中<xref:System.IO.StreamReader.Peek%2A> , 的方法`StreamReader`會決定是否有任何額外的字元。 `Do...Loop`</span><span class="sxs-lookup"><span data-stu-id="441ab-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="441ab-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="441ab-160">See also</span></span>

- [<span data-ttu-id="441ab-161">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="441ab-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="441ab-162">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="441ab-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="441ab-163">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="441ab-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="441ab-164">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="441ab-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="441ab-165">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="441ab-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="441ab-166">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="441ab-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
