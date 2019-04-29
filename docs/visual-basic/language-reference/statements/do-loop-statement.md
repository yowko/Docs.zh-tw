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
ms.openlocfilehash: 3ff3d67f38f510b798da3e470de066cff1e98f29
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638771"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="5576d-102">Do...Loop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5576d-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="5576d-103">重複出現時的陳述式區塊`Boolean`條件`True`或直到條件變成`True`。</span><span class="sxs-lookup"><span data-stu-id="5576d-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5576d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5576d-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="5576d-105">組件</span><span class="sxs-lookup"><span data-stu-id="5576d-105">Parts</span></span>  
  
|<span data-ttu-id="5576d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="5576d-106">Term</span></span>|<span data-ttu-id="5576d-107">定義</span><span class="sxs-lookup"><span data-stu-id="5576d-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="5576d-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="5576d-108">Required.</span></span> <span data-ttu-id="5576d-109">定義的開頭`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="5576d-110">除非使用 `Until`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="5576d-110">Required unless `Until` is used.</span></span> <span data-ttu-id="5576d-111">重複此迴圈，直到`condition`是`False`。</span><span class="sxs-lookup"><span data-stu-id="5576d-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="5576d-112">除非使用 `While`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="5576d-112">Required unless `While` is used.</span></span> <span data-ttu-id="5576d-113">重複此迴圈，直到`condition`是`True`。</span><span class="sxs-lookup"><span data-stu-id="5576d-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="5576d-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5576d-114">Optional.</span></span> <span data-ttu-id="5576d-115">`Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="5576d-115">`Boolean` expression.</span></span> <span data-ttu-id="5576d-116">如果`condition`已`Nothing`，Visual Basic 會將其視為`False`。</span><span class="sxs-lookup"><span data-stu-id="5576d-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="5576d-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5576d-117">Optional.</span></span> <span data-ttu-id="5576d-118">一或多個陳述式時，或直到，會重複`condition`是`True`。</span><span class="sxs-lookup"><span data-stu-id="5576d-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="5576d-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5576d-119">Optional.</span></span> <span data-ttu-id="5576d-120">將控制權轉移到下一個反覆運算`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="5576d-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5576d-121">Optional.</span></span> <span data-ttu-id="5576d-122">控制權轉移共`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="5576d-123">必要項。</span><span class="sxs-lookup"><span data-stu-id="5576d-123">Required.</span></span> <span data-ttu-id="5576d-124">結束的定義`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5576d-125">備註</span><span class="sxs-lookup"><span data-stu-id="5576d-125">Remarks</span></span>  
 <span data-ttu-id="5576d-126">使用`Do...Loop`結構，當您想要重複執行一組陳述式的不限數目的次數，直到滿足條件。</span><span class="sxs-lookup"><span data-stu-id="5576d-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="5576d-127">如果您想要重複陳述式的次數，固定數目[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="5576d-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="5576d-128">您可以使用`While`或是`Until`指定`condition`，但非兩者。</span><span class="sxs-lookup"><span data-stu-id="5576d-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="5576d-129">您可以測試`condition`一次，在開始或結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="5576d-130">如果您在測試`condition`開頭的迴圈 (在`Do`陳述式)，迴圈可能不會執行甚至一次。</span><span class="sxs-lookup"><span data-stu-id="5576d-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="5576d-131">如果您在迴圈結束測試 (在`Loop`陳述式)，迴圈永遠執行至少一次。</span><span class="sxs-lookup"><span data-stu-id="5576d-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="5576d-132">條件通常的結果比較的兩個值，但它可以是任何運算式評估為[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。</span><span class="sxs-lookup"><span data-stu-id="5576d-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="5576d-133">這包括的其他資料類型，例如數值類型，已轉換成值`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="5576d-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="5576d-134">您可以巢狀`Do`放在另一個迴圈的迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="5576d-135">您也可以巢狀不同種類的控制結構彼此。</span><span class="sxs-lookup"><span data-stu-id="5576d-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="5576d-136">如需詳細資訊，請參閱 <<c0> [ 巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="5576d-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5576d-137">`Do...Loop`結構可讓您更大的彈性比[時...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)因為它可讓您決定是否要結束迴圈時`condition`會停止正在`True`或是當它首次變成`True`。</span><span class="sxs-lookup"><span data-stu-id="5576d-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="5576d-138">它也可讓您測試`condition`開頭或結尾的迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="5576d-139">結束執行</span><span class="sxs-lookup"><span data-stu-id="5576d-139">Exit Do</span></span>  
 <span data-ttu-id="5576d-140">[Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)陳述式可以提供替代的方式，來結束`Do…Loop`。</span><span class="sxs-lookup"><span data-stu-id="5576d-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="5576d-141">`Exit Do` 立即將控制權傳輸至後面的陳述式`Loop`陳述式。</span><span class="sxs-lookup"><span data-stu-id="5576d-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="5576d-142">`Exit Do` 通常用於評估某項條件，例如在之後`If...Then...Else`結構。</span><span class="sxs-lookup"><span data-stu-id="5576d-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="5576d-143">您可能想要結束迴圈，如果偵測到的條件，就不需要或無法繼續反覆執行，例如錯誤的數值或終止要求。</span><span class="sxs-lookup"><span data-stu-id="5576d-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="5576d-144">其中一種用法`Exit Do`就是要測試的條件，可能會導致*永無止盡的迴圈*，即無法執行大型或甚至是無限次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="5576d-145">您可以使用`Exit Do`來逸出迴圈。</span><span class="sxs-lookup"><span data-stu-id="5576d-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="5576d-146">您可以包含任意數目的`Exit Do`任何一處陳述式中的`Do…Loop`。</span><span class="sxs-lookup"><span data-stu-id="5576d-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="5576d-147">使用時內巢狀`Do`迴圈，`Exit Do`控制權出最內層的迴圈並進入下一個較高的層級，巢狀。</span><span class="sxs-lookup"><span data-stu-id="5576d-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5576d-148">範例</span><span class="sxs-lookup"><span data-stu-id="5576d-148">Example</span></span>  
 <span data-ttu-id="5576d-149">下列範例中，在迴圈中的陳述式會繼續執行，直到`index`變數是否大於 10。</span><span class="sxs-lookup"><span data-stu-id="5576d-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="5576d-150">`Until`子句是在迴圈的結尾。</span><span class="sxs-lookup"><span data-stu-id="5576d-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="5576d-151">範例</span><span class="sxs-lookup"><span data-stu-id="5576d-151">Example</span></span>  
 <span data-ttu-id="5576d-152">下列範例會使用`While`子句，而不是`Until`子句，和`condition`測試的迴圈，而不是結尾開頭。</span><span class="sxs-lookup"><span data-stu-id="5576d-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="5576d-153">範例</span><span class="sxs-lookup"><span data-stu-id="5576d-153">Example</span></span>  
 <span data-ttu-id="5576d-154">在下列範例中，`condition`停止迴圈時`index`變數是否大於 100。</span><span class="sxs-lookup"><span data-stu-id="5576d-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="5576d-155">`If`陳述式在迴圈中，不過，會導致`Exit Do`索引變數大於 10 時停止迴圈的陳述式。</span><span class="sxs-lookup"><span data-stu-id="5576d-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="5576d-156">範例</span><span class="sxs-lookup"><span data-stu-id="5576d-156">Example</span></span>  
 <span data-ttu-id="5576d-157">下列範例會讀取文字檔案中的所有行。</span><span class="sxs-lookup"><span data-stu-id="5576d-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="5576d-158"><xref:System.IO.File.OpenText%2A>方法會開啟檔案，並傳回<xref:System.IO.StreamReader>讀取字元。</span><span class="sxs-lookup"><span data-stu-id="5576d-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="5576d-159">在 `Do...Loop`條件<xref:System.IO.StreamReader.Peek%2A>方法`StreamReader`判斷是否有任何額外的字元。</span><span class="sxs-lookup"><span data-stu-id="5576d-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="5576d-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5576d-160">See also</span></span>

- [<span data-ttu-id="5576d-161">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="5576d-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="5576d-162">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="5576d-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="5576d-163">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="5576d-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="5576d-164">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="5576d-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="5576d-165">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="5576d-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="5576d-166">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="5576d-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
