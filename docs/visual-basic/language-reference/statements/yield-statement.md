---
title: Yield 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 72a8dafdc5aa834a644e1e70a309cfc0827b5fdf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352718"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="34f92-102">Yield 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34f92-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="34f92-103">Sends the next element of a collection to a `For Each...Next` statement.</span><span class="sxs-lookup"><span data-stu-id="34f92-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f92-104">語法</span><span class="sxs-lookup"><span data-stu-id="34f92-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="34f92-105">參數</span><span class="sxs-lookup"><span data-stu-id="34f92-105">Parameters</span></span>  
  
|<span data-ttu-id="34f92-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="34f92-106">Term</span></span>|<span data-ttu-id="34f92-107">定義</span><span class="sxs-lookup"><span data-stu-id="34f92-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="34f92-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="34f92-108">Required.</span></span> <span data-ttu-id="34f92-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span><span class="sxs-lookup"><span data-stu-id="34f92-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34f92-110">備註</span><span class="sxs-lookup"><span data-stu-id="34f92-110">Remarks</span></span>  
 <span data-ttu-id="34f92-111">The `Yield` statement returns one element of a collection at a time.</span><span class="sxs-lookup"><span data-stu-id="34f92-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="34f92-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span><span class="sxs-lookup"><span data-stu-id="34f92-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="34f92-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span><span class="sxs-lookup"><span data-stu-id="34f92-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="34f92-114">Each iteration of the `For Each` loop calls the iterator function.</span><span class="sxs-lookup"><span data-stu-id="34f92-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="34f92-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span><span class="sxs-lookup"><span data-stu-id="34f92-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="34f92-116">下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="34f92-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="34f92-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span><span class="sxs-lookup"><span data-stu-id="34f92-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="34f92-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span><span class="sxs-lookup"><span data-stu-id="34f92-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="34f92-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span><span class="sxs-lookup"><span data-stu-id="34f92-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="34f92-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="34f92-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="34f92-121">Iterator Functions and Get Accessors</span><span class="sxs-lookup"><span data-stu-id="34f92-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="34f92-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span><span class="sxs-lookup"><span data-stu-id="34f92-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="34f92-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span><span class="sxs-lookup"><span data-stu-id="34f92-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="34f92-124">傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="34f92-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="34f92-125">It cannot have any `ByRef` parameters.</span><span class="sxs-lookup"><span data-stu-id="34f92-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="34f92-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span><span class="sxs-lookup"><span data-stu-id="34f92-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="34f92-127">An iterator function can be an anonymous function.</span><span class="sxs-lookup"><span data-stu-id="34f92-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="34f92-128">如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="34f92-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="34f92-129">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="34f92-129">Exception Handling</span></span>  
 <span data-ttu-id="34f92-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34f92-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="34f92-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="34f92-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="34f92-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="34f92-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="34f92-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span><span class="sxs-lookup"><span data-stu-id="34f92-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="34f92-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span><span class="sxs-lookup"><span data-stu-id="34f92-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="34f92-135">技術實作</span><span class="sxs-lookup"><span data-stu-id="34f92-135">Technical Implementation</span></span>  
 <span data-ttu-id="34f92-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="34f92-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="34f92-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span><span class="sxs-lookup"><span data-stu-id="34f92-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="34f92-138">呼叫會改為將 `IEnumerable(Of String)` 傳回至 `elements` 變數中。</span><span class="sxs-lookup"><span data-stu-id="34f92-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="34f92-139">在 `For Each` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。</span><span class="sxs-lookup"><span data-stu-id="34f92-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="34f92-140">這個呼叫會執行 `MyIteratorFunction` 的主體，直到下一個 `Yield` 陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="34f92-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="34f92-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="34f92-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="34f92-142">在 `For Each` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `Yield` 陳述式時再次停止。</span><span class="sxs-lookup"><span data-stu-id="34f92-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="34f92-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span><span class="sxs-lookup"><span data-stu-id="34f92-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34f92-144">範例</span><span class="sxs-lookup"><span data-stu-id="34f92-144">Example</span></span>  
 <span data-ttu-id="34f92-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span><span class="sxs-lookup"><span data-stu-id="34f92-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="34f92-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span><span class="sxs-lookup"><span data-stu-id="34f92-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="34f92-147">每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。</span><span class="sxs-lookup"><span data-stu-id="34f92-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="34f92-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span><span class="sxs-lookup"><span data-stu-id="34f92-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="34f92-149">呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。</span><span class="sxs-lookup"><span data-stu-id="34f92-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="34f92-150">範例</span><span class="sxs-lookup"><span data-stu-id="34f92-150">Example</span></span>  
 <span data-ttu-id="34f92-151">下列範例將示範本身為迭代器的 `Get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="34f92-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="34f92-152">The property declaration includes an `Iterator` modifier.</span><span class="sxs-lookup"><span data-stu-id="34f92-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="34f92-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="34f92-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f92-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="34f92-154">See also</span></span>

- [<span data-ttu-id="34f92-155">陳述式</span><span class="sxs-lookup"><span data-stu-id="34f92-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
