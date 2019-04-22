---
title: Exit 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 1f386694bd7425ee530b9305ab684b730f9b73c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832628"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="9af11-102">Exit 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9af11-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="9af11-103">結束程序或區塊，並立即將控制權轉移到接在程序呼叫或區塊定義。</span><span class="sxs-lookup"><span data-stu-id="9af11-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af11-104">語法</span><span class="sxs-lookup"><span data-stu-id="9af11-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="9af11-105">陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="9af11-106">立即結束`Do`迴圈中會出現。</span><span class="sxs-lookup"><span data-stu-id="9af11-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="9af11-107">之後的陳述式會繼續執行`Loop`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="9af11-108">`Exit Do` 可以使用只在`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="9af11-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="9af11-109">當用在巢狀`Do`迴圈，`Exit Do`結束最內層的迴圈，並將控制權傳輸至下一個較高的層級，巢狀。</span><span class="sxs-lookup"><span data-stu-id="9af11-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="9af11-110">立即結束`For`迴圈中會出現。</span><span class="sxs-lookup"><span data-stu-id="9af11-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="9af11-111">之後的陳述式會繼續執行`Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="9af11-112">`Exit For` 可以使用只在`For`...`Next`或`For Each`...`Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="9af11-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="9af11-113">當用在巢狀`For`迴圈，`Exit For`結束最內層的迴圈，並將控制權傳輸至下一個較高的層級，巢狀。</span><span class="sxs-lookup"><span data-stu-id="9af11-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="9af11-114">立即結束`Function`出現的程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="9af11-115">執行會繼續進行下列呼叫的陳述式的陳述式`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="9af11-116">`Exit Function` 可以使用只在`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="9af11-117">若要指定傳回的值，可以將值指派給前一行中的函式`Exit Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="9af11-118">若要指派傳回值，並結束一個陳述式中的函式，您可以改為使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9af11-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="9af11-119">立即結束`Property`出現的程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="9af11-120">執行會繼續進行呼叫的陳述式`Property`程序，也就是利用陳述式要求或設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9af11-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="9af11-121">`Exit Property` 可以使用僅在屬性的內部`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="9af11-122">若要指定傳回值`Get`程序中，您可以將值指派給前一行中的函式`Exit Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="9af11-123">若要將指派傳回值和結束`Get`一個陳述式中的程序，您可以改為使用`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="9af11-124">在 `Set`程序中，`Exit Property`陳述式相當於`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="9af11-125">立即結束`Select Case`中出現的區塊。</span><span class="sxs-lookup"><span data-stu-id="9af11-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="9af11-126">之後的陳述式會繼續執行`End Select`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="9af11-127">`Exit Select` 可以使用只在`Select Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="9af11-128">立即結束`Sub`出現的程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="9af11-129">執行會繼續進行下列呼叫的陳述式的陳述式`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="9af11-130">`Exit Sub` 可以使用只在`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="9af11-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="9af11-131">在 `Sub`程序中，`Exit Sub`陳述式相當於`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="9af11-132">立即結束`Try`或`Catch`中出現的區塊。</span><span class="sxs-lookup"><span data-stu-id="9af11-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="9af11-133">執行會繼續進行`Finally`封鎖如果有的話，或之後的陳述式與`End Try`否則陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="9af11-134">`Exit Try` 可用於只`Try`或`Catch`區塊中，並不深入探討`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="9af11-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="9af11-135">立即結束`While`迴圈中會出現。</span><span class="sxs-lookup"><span data-stu-id="9af11-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="9af11-136">之後的陳述式會繼續執行`End While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="9af11-137">`Exit While` 可以使用只在`While`迴圈。</span><span class="sxs-lookup"><span data-stu-id="9af11-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="9af11-138">使用時內巢狀`While`迴圈`Exit While`控制權轉移到迴圈上一層的巢狀迴圈其中`Exit While`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="9af11-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9af11-139">備註</span><span class="sxs-lookup"><span data-stu-id="9af11-139">Remarks</span></span>  
 <span data-ttu-id="9af11-140">請勿混淆`Exit`陳述式與`End`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="9af11-141">`Exit` 未定義陳述式結尾。</span><span class="sxs-lookup"><span data-stu-id="9af11-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9af11-142">範例</span><span class="sxs-lookup"><span data-stu-id="9af11-142">Example</span></span>  
 <span data-ttu-id="9af11-143">下列範例中，在迴圈條件會停止迴圈時`index`變數是否大於 100。</span><span class="sxs-lookup"><span data-stu-id="9af11-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="9af11-144">`If`陳述式在迴圈中，不過，會導致`Exit Do`索引變數大於 10 時停止迴圈的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9af11-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="9af11-145">範例</span><span class="sxs-lookup"><span data-stu-id="9af11-145">Example</span></span>  
 <span data-ttu-id="9af11-146">下列範例會將傳回的值指派給函式名稱`myFunction`，然後使用`Exit Function`從函式傳回。</span><span class="sxs-lookup"><span data-stu-id="9af11-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a><span data-ttu-id="9af11-147">範例</span><span class="sxs-lookup"><span data-stu-id="9af11-147">Example</span></span>  
 <span data-ttu-id="9af11-148">下列範例會使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)指派傳回值，並結束函式。</span><span class="sxs-lookup"><span data-stu-id="9af11-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="9af11-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9af11-149">See also</span></span>

- [<span data-ttu-id="9af11-150">Continue 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
- [<span data-ttu-id="9af11-151">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="9af11-152">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
- [<span data-ttu-id="9af11-153">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="9af11-154">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="9af11-155">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="9af11-156">Return 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="9af11-157">Stop 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="9af11-158">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="9af11-159">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="9af11-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
