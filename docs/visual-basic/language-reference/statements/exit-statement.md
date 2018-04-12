---
title: Exit 陳述式 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="f2799-102">Exit 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2799-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="f2799-103">結束程序或區塊，並立即將控制權傳輸至下列程序呼叫或區塊定義陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2799-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2799-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="f2799-105">陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="f2799-106">立即結束`Do`迴圈中會出現。</span><span class="sxs-lookup"><span data-stu-id="f2799-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="f2799-107">執行會繼續進行之後的陳述式`Loop`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="f2799-108">`Exit Do`可以使用僅在內部`Do`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2799-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="f2799-109">使用時內巢狀`Do`迴圈`Exit Do`結束最內層的迴圈，並將控制權傳輸至下一個高的層級的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="f2799-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="f2799-110">立即結束`For`迴圈中會出現。</span><span class="sxs-lookup"><span data-stu-id="f2799-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="f2799-111">執行會繼續進行之後的陳述式`Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="f2799-112">`Exit For`可以使用僅在內部`For`...`Next`或`For Each`...`Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2799-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="f2799-113">使用時內巢狀`For`迴圈`Exit For`結束最內層的迴圈，並將控制權傳輸至下一個高的層級的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="f2799-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="f2799-114">立即結束`Function`其出現位置中的程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="f2799-115">在呼叫的陳述式之後的陳述式會繼續執行`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="f2799-116">`Exit Function`可以使用僅在內部`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="f2799-117">若要指定傳回值，您可以將值指派給函式上的名稱前一行`Exit Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="f2799-118">若要指派傳回值，並結束一個陳述式中的函式，您可以改為使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f2799-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="f2799-119">立即結束`Property`其出現位置中的程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="f2799-120">執行會繼續進行呼叫的陳述式`Property`程序，也就是要求或設定屬性值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="f2799-121">`Exit Property`可以使用僅在屬性的內部`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="f2799-122">若要指定傳回值會在`Get`程序中，您可以指派值給函式上的名稱前一行`Exit Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="f2799-123">若要指派的傳回值和結束`Get`一個陳述式中的程序，您可以改為使用`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="f2799-124">在`Set`程序，`Exit Property`陳述式相當於`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="f2799-125">立即結束`Select Case`中出現的區塊。</span><span class="sxs-lookup"><span data-stu-id="f2799-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="f2799-126">執行會繼續進行之後的陳述式`End Select`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="f2799-127">`Exit Select`可以使用僅在內部`Select Case`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="f2799-128">立即結束`Sub`其出現位置中的程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="f2799-129">在呼叫的陳述式之後的陳述式會繼續執行`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="f2799-130">`Exit Sub`可以使用僅在內部`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="f2799-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="f2799-131">在`Sub`程序，`Exit Sub`陳述式相當於`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="f2799-132">立即結束`Try`或`Catch`中出現的區塊。</span><span class="sxs-lookup"><span data-stu-id="f2799-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="f2799-133">執行會繼續進行`Finally`封鎖如果有的話，或之後的陳述式與`End Try`否則陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="f2799-134">`Exit Try`可以使用僅在內部`Try`或`Catch`區塊，並不在`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="f2799-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="f2799-135">立即結束`While`迴圈中會出現。</span><span class="sxs-lookup"><span data-stu-id="f2799-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="f2799-136">執行會繼續進行之後的陳述式`End While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="f2799-137">`Exit While`可以使用僅在內部`While`迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2799-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="f2799-138">使用時內巢狀`While`迴圈`Exit While`控制權轉移到迴圈上一層的巢狀迴圈其中`Exit While`，就會發生。</span><span class="sxs-lookup"><span data-stu-id="f2799-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2799-139">備註</span><span class="sxs-lookup"><span data-stu-id="f2799-139">Remarks</span></span>  
 <span data-ttu-id="f2799-140">請勿混淆`Exit`陳述式與`End`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2799-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="f2799-141">`Exit`未定義陳述式結尾。</span><span class="sxs-lookup"><span data-stu-id="f2799-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2799-142">範例</span><span class="sxs-lookup"><span data-stu-id="f2799-142">Example</span></span>  
 <span data-ttu-id="f2799-143">在下列範例中，迴圈條件停止迴圈時`index`變數大於 100。</span><span class="sxs-lookup"><span data-stu-id="f2799-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="f2799-144">`If`陳述式在迴圈中，不過，會導致`Exit Do`陳述式來索引變數大於 10 時停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2799-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="f2799-145">範例</span><span class="sxs-lookup"><span data-stu-id="f2799-145">Example</span></span>  
 <span data-ttu-id="f2799-146">下列範例將傳回的值指派給函式名稱`myFunction`，然後使用`Exit Function`從函式傳回。</span><span class="sxs-lookup"><span data-stu-id="f2799-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="f2799-147">範例</span><span class="sxs-lookup"><span data-stu-id="f2799-147">Example</span></span>  
 <span data-ttu-id="f2799-148">下列範例會使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)指派傳回值，並結束函式。</span><span class="sxs-lookup"><span data-stu-id="f2799-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f2799-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2799-149">See Also</span></span>  
 [<span data-ttu-id="f2799-150">Continue 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [<span data-ttu-id="f2799-151">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="f2799-152">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="f2799-153">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="f2799-154">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="f2799-155">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="f2799-156">Return 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="f2799-157">Stop 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="f2799-158">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="f2799-159">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="f2799-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
