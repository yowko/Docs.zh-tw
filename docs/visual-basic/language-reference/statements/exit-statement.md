---
title: Exit 陳述式
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
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345930"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="8c66f-102">Exit 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c66f-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="8c66f-103">結束程式或區塊，並立即將控制權轉移至程序呼叫或區塊定義之後的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c66f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c66f-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="8c66f-105">陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="8c66f-106">立即結束它所顯示的 `Do` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="8c66f-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="8c66f-107">執行會繼續進行 `Loop` 語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="8c66f-108">`Exit Do` 只能用在 `Do` 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="8c66f-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="8c66f-109">在 nested `Do` 迴圈中使用時，`Exit Do` 結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="8c66f-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="8c66f-110">立即結束它所顯示的 `For` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="8c66f-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="8c66f-111">執行會繼續進行 `Next` 語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="8c66f-112">`Exit For` 只能用在 `For`...`Next` 或 `For Each`...`Next` 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="8c66f-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="8c66f-113">在 nested `For` 迴圈中使用時，`Exit For` 結束最內層的迴圈，並將控制權轉移至下一個較高層級的嵌套。</span><span class="sxs-lookup"><span data-stu-id="8c66f-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="8c66f-114">立即結束它所顯示的 `Function` 程式。</span><span class="sxs-lookup"><span data-stu-id="8c66f-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="8c66f-115">執行會繼續進行呼叫 `Function` 程式之語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="8c66f-116">`Exit Function` 只能在 `Function` 程式內使用。</span><span class="sxs-lookup"><span data-stu-id="8c66f-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="8c66f-117">若要指定傳回值，您可以在 `Exit Function` 語句之前的一行上，將值指派給函數名稱。</span><span class="sxs-lookup"><span data-stu-id="8c66f-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="8c66f-118">若要指派傳回值並在一個語句中結束函式，您可以改為使用[Return 語句](return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8c66f-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="8c66f-119">立即結束它所顯示的 `Property` 程式。</span><span class="sxs-lookup"><span data-stu-id="8c66f-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="8c66f-120">執行作業會繼續使用呼叫 `Property` 程式的語句，也就是要求或設定屬性值的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="8c66f-121">`Exit Property` 只能在屬性的 `Get` 或 `Set` 程式內使用。</span><span class="sxs-lookup"><span data-stu-id="8c66f-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="8c66f-122">若要在 `Get` 程式中指定傳回值，您可以在 `Exit Property` 語句之前，將值指派給函數名稱。</span><span class="sxs-lookup"><span data-stu-id="8c66f-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="8c66f-123">若要指派傳回值並結束一個語句中的 `Get` 程式，您可以改為使用 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="8c66f-124">在 `Set` 程式中，`Exit Property` 語句相當於 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="8c66f-125">立即結束出現的 `Select Case` 區塊。</span><span class="sxs-lookup"><span data-stu-id="8c66f-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="8c66f-126">執行會繼續進行 `End Select` 語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="8c66f-127">`Exit Select` 只能用在 `Select Case` 語句內。</span><span class="sxs-lookup"><span data-stu-id="8c66f-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="8c66f-128">立即結束它所顯示的 `Sub` 程式。</span><span class="sxs-lookup"><span data-stu-id="8c66f-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="8c66f-129">執行會繼續進行呼叫 `Sub` 程式之語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="8c66f-130">`Exit Sub` 只能在 `Sub` 程式內使用。</span><span class="sxs-lookup"><span data-stu-id="8c66f-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="8c66f-131">在 `Sub` 程式中，`Exit Sub` 語句相當於 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="8c66f-132">立即結束出現 `Try` 或 `Catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="8c66f-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="8c66f-133">如果有 `Finally` 區塊，則會繼續執行，否則會以 `End Try` 語句之後的語句進行。</span><span class="sxs-lookup"><span data-stu-id="8c66f-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="8c66f-134">`Exit Try` 只能用在 `Try` 或 `Catch` 區塊內，而不能用在 `Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="8c66f-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="8c66f-135">立即結束它所顯示的 `While` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="8c66f-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="8c66f-136">執行會繼續進行 `End While` 語句後面的語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="8c66f-137">`Exit While` 只能用在 `While` 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="8c66f-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="8c66f-138">在嵌套的 `While` 迴圈中使用時，`Exit While` 會將控制權轉移至迴圈，這是在發生 `Exit While` 的迴圈上方的一個嵌套層級。</span><span class="sxs-lookup"><span data-stu-id="8c66f-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c66f-139">備註</span><span class="sxs-lookup"><span data-stu-id="8c66f-139">Remarks</span></span>

<span data-ttu-id="8c66f-140">請勿混淆 `Exit` 語句與 `End` 語句。</span><span class="sxs-lookup"><span data-stu-id="8c66f-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="8c66f-141">`Exit` 不會定義語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="8c66f-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="8c66f-142">範例</span><span class="sxs-lookup"><span data-stu-id="8c66f-142">Example</span></span>

<span data-ttu-id="8c66f-143">在下列範例中，當 `index` 變數大於100時，迴圈條件會停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="8c66f-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="8c66f-144">不過，迴圈中的 `If` 語句會導致 `Exit Do` 語句在索引變數大於10時停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="8c66f-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="8c66f-145">範例</span><span class="sxs-lookup"><span data-stu-id="8c66f-145">Example</span></span>

<span data-ttu-id="8c66f-146">下列範例會將傳回值指派給函數名稱 `myFunction`，然後使用 `Exit Function` 從函式傳回：</span><span class="sxs-lookup"><span data-stu-id="8c66f-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="8c66f-147">範例</span><span class="sxs-lookup"><span data-stu-id="8c66f-147">Example</span></span>

<span data-ttu-id="8c66f-148">下列範例會使用[Return 語句](return-statement.md)來指派傳回值並結束函式：</span><span class="sxs-lookup"><span data-stu-id="8c66f-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="8c66f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c66f-149">See also</span></span>

- [<span data-ttu-id="8c66f-150">Continue 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="8c66f-151">Do...Loop 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="8c66f-152">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="8c66f-153">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="8c66f-154">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="8c66f-155">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="8c66f-156">Return 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="8c66f-157">Stop 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="8c66f-158">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="8c66f-159">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="8c66f-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
