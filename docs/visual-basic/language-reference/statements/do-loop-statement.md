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
ms.openlocfilehash: 86a702aefeea1e5e359a579a3f29e9c06f1c619c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865933"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="39df3-102">Do...Loop 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39df3-102">Do...Loop Statement (Visual Basic)</span></span>

<span data-ttu-id="39df3-103">在條件 `Boolean` 為 `True` 或直到條件變成之前，重複語句區塊 `True` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39df3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="39df3-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="39df3-105">組件</span><span class="sxs-lookup"><span data-stu-id="39df3-105">Parts</span></span>  
  
|<span data-ttu-id="39df3-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="39df3-106">Term</span></span>|<span data-ttu-id="39df3-107">定義</span><span class="sxs-lookup"><span data-stu-id="39df3-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="39df3-108">必要。</span><span class="sxs-lookup"><span data-stu-id="39df3-108">Required.</span></span> <span data-ttu-id="39df3-109">開始迴圈的定義 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="39df3-110">除非使用 `Until`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="39df3-110">Required unless `Until` is used.</span></span> <span data-ttu-id="39df3-111">重複執行迴圈 `condition` ，直到為為止 `False` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="39df3-112">除非使用 `While`，否則為必要參數。</span><span class="sxs-lookup"><span data-stu-id="39df3-112">Required unless `While` is used.</span></span> <span data-ttu-id="39df3-113">重複執行迴圈 `condition` ，直到為為止 `True` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="39df3-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39df3-114">Optional.</span></span> <span data-ttu-id="39df3-115">`Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="39df3-115">`Boolean` expression.</span></span> <span data-ttu-id="39df3-116">如果 `condition` 為 `Nothing` ，Visual Basic 會將其視為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="39df3-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39df3-117">Optional.</span></span> <span data-ttu-id="39df3-118">一或多個重複的語句，或在中 `condition` 是 `True` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="39df3-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39df3-119">Optional.</span></span> <span data-ttu-id="39df3-120">將控制權轉移到迴圈的下一個反復專案 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="39df3-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39df3-121">Optional.</span></span> <span data-ttu-id="39df3-122">將控制權移交給 `Do` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="39df3-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="39df3-123">必要。</span><span class="sxs-lookup"><span data-stu-id="39df3-123">Required.</span></span> <span data-ttu-id="39df3-124">終止迴圈的定義 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39df3-125">備註</span><span class="sxs-lookup"><span data-stu-id="39df3-125">Remarks</span></span>  

 <span data-ttu-id="39df3-126">`Do...Loop`當您想要重複一組語句的次數不定時，請使用結構，直到滿足條件為止。</span><span class="sxs-lookup"><span data-stu-id="39df3-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="39df3-127">如果您想要重複執行語句的次數， [請將下一個語句](for-next-statement.md) 通常是較佳的選擇。</span><span class="sxs-lookup"><span data-stu-id="39df3-127">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="39df3-128">您可以使用 `While` 或 `Until` 來指定 `condition` ，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="39df3-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="39df3-129">您只能 `condition` 在迴圈的開頭或結尾測試一次。</span><span class="sxs-lookup"><span data-stu-id="39df3-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="39df3-130">如果您在 `condition` 語句)  (開始測試 `Do` ，迴圈可能無法執行一次。</span><span class="sxs-lookup"><span data-stu-id="39df3-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="39df3-131">如果您在迴圈的結尾處進行測試 (在 `Loop`) 語句中，迴圈一律會至少執行一次。</span><span class="sxs-lookup"><span data-stu-id="39df3-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="39df3-132">此條件通常是因為兩個值的比較所產生，但是可以是任何評估為 [布林資料類型](../data-types/boolean-data-type.md) 值 (`True` 或) 的運算式 `False` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="39df3-133">這包括已轉換成之其他資料類型的值，例如數數值型別 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="39df3-134">您可以藉 `Do` 由將迴圈放在另一個迴圈中，來嵌套迴圈。</span><span class="sxs-lookup"><span data-stu-id="39df3-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="39df3-135">您也可以在彼此之間嵌套不同類型的控制結構。</span><span class="sxs-lookup"><span data-stu-id="39df3-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="39df3-136">如需詳細資訊，請參閱 [嵌套控制項結構](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="39df3-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39df3-137">此 `Do...Loop` 結構可提供比 While 更多的彈性 ... [End While 語句](while-end-while-statement.md) ，因為它可讓您決定是否要在 `condition` 停止 `True` 或第一次變成時結束迴圈 `True` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="39df3-138">它也可讓您 `condition` 在迴圈的開頭或結尾進行測試。</span><span class="sxs-lookup"><span data-stu-id="39df3-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="39df3-139">Exit Do</span><span class="sxs-lookup"><span data-stu-id="39df3-139">Exit Do</span></span>  

 <span data-ttu-id="39df3-140">[Exit Do](exit-statement.md)語句可以提供退出的替代方法 `Do…Loop` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-140">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="39df3-141">`Exit Do` 將控制權立即傳輸至語句後面的語句 `Loop` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="39df3-142">`Exit Do` 通常用於評估某些條件之後，例如在 `If...Then...Else` 結構中。</span><span class="sxs-lookup"><span data-stu-id="39df3-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="39df3-143">如果您偵測到導致不必要或無法繼續反覆運算的條件（例如錯誤值或終止要求），您可能會想要結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="39df3-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="39df3-144">的其中一種用途 `Exit Do` 是測試可能造成無止盡 *迴圈*的狀況，也就是可以執行大型或甚至無限次數的迴圈。</span><span class="sxs-lookup"><span data-stu-id="39df3-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="39df3-145">您可以使用 `Exit Do` 來對迴圈進行換用。</span><span class="sxs-lookup"><span data-stu-id="39df3-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="39df3-146">您可以將任意數目的 `Exit Do` 語句包含在中的任何位置 `Do…Loop` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="39df3-147">在嵌套迴圈中使用時 `Do` ，會 `Exit Do` 將控制權從最內層的迴圈傳送到下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="39df3-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39df3-148">範例</span><span class="sxs-lookup"><span data-stu-id="39df3-148">Example</span></span>  

 <span data-ttu-id="39df3-149">在下列範例中，迴圈中的語句會繼續執行，直到 `index` 變數大於10為止。</span><span class="sxs-lookup"><span data-stu-id="39df3-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="39df3-150">`Until`子句位於迴圈的結尾。</span><span class="sxs-lookup"><span data-stu-id="39df3-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="39df3-151">範例</span><span class="sxs-lookup"><span data-stu-id="39df3-151">Example</span></span>  

 <span data-ttu-id="39df3-152">下列範例 `While` 會使用子句而非 `Until` 子句，並 `condition` 在迴圈開始時（而不是在結尾）進行測試。</span><span class="sxs-lookup"><span data-stu-id="39df3-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="39df3-153">範例</span><span class="sxs-lookup"><span data-stu-id="39df3-153">Example</span></span>  

 <span data-ttu-id="39df3-154">在下列範例中， `condition` 當變數大於100時，就會停止迴圈 `index` 。</span><span class="sxs-lookup"><span data-stu-id="39df3-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="39df3-155">`If`但是，迴圈中的語句會在 `Exit Do` 索引變數大於10時，讓語句停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="39df3-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="39df3-156">範例</span><span class="sxs-lookup"><span data-stu-id="39df3-156">Example</span></span>  

 <span data-ttu-id="39df3-157">下列範例會讀取文字檔中的所有行。</span><span class="sxs-lookup"><span data-stu-id="39df3-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="39df3-158"><xref:System.IO.File.OpenText%2A>方法會開啟檔案，並傳回 <xref:System.IO.StreamReader> 讀取字元的。</span><span class="sxs-lookup"><span data-stu-id="39df3-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="39df3-159">在 `Do...Loop` 條件中，的 <xref:System.IO.StreamReader.Peek%2A> 方法 `StreamReader` 會判斷是否有任何額外的字元。</span><span class="sxs-lookup"><span data-stu-id="39df3-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="39df3-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39df3-160">See also</span></span>

- [<span data-ttu-id="39df3-161">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="39df3-161">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="39df3-162">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="39df3-162">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="39df3-163">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="39df3-163">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="39df3-164">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="39df3-164">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="39df3-165">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="39df3-165">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="39df3-166">While...End While 陳述式</span><span class="sxs-lookup"><span data-stu-id="39df3-166">While...End While Statement</span></span>](while-end-while-statement.md)
