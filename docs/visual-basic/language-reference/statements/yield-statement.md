---
title: "Yield 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99f5129d5cb43cddfb17731f337a72fae22d3626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="476ad-102">Yield 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="476ad-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="476ad-103">傳送至集合的下一個項目`For Each...Next`陳述式。</span><span class="sxs-lookup"><span data-stu-id="476ad-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="476ad-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="476ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="476ad-105">Parameters</span></span>  
  
|<span data-ttu-id="476ad-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="476ad-106">Term</span></span>|<span data-ttu-id="476ad-107">定義</span><span class="sxs-lookup"><span data-stu-id="476ad-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="476ad-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="476ad-108">Required.</span></span> <span data-ttu-id="476ad-109">隱含轉換為迭代器函式類型的運算式或`Get`存取子，其包含`Yield`陳述式。</span><span class="sxs-lookup"><span data-stu-id="476ad-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="476ad-110">備註</span><span class="sxs-lookup"><span data-stu-id="476ad-110">Remarks</span></span>  
 <span data-ttu-id="476ad-111">`Yield`陳述式會傳回一次集合中的一個項目。</span><span class="sxs-lookup"><span data-stu-id="476ad-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="476ad-112">`Yield`陳述式會包含在迭代器函式或`Get`存取子，在集合上執行自訂反覆項目。</span><span class="sxs-lookup"><span data-stu-id="476ad-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="476ad-113">您可以使用迭代器函式使用[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)或 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="476ad-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="476ad-114">每個反覆項目`For Each`迴圈就會呼叫 iterator 函式。</span><span class="sxs-lookup"><span data-stu-id="476ad-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="476ad-115">當`Yield`iterator 函式，在到達陳述式時`expression`傳回，並保留程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="476ad-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="476ad-116">下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="476ad-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="476ad-117">類型必須有隱含的轉換`expression`中`Yield`陳述式的傳回類型迭代器。</span><span class="sxs-lookup"><span data-stu-id="476ad-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="476ad-118">您可以使用`Exit Function`或`Return`陳述式結束反覆項目。</span><span class="sxs-lookup"><span data-stu-id="476ad-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="476ad-119">」 產生 「 不是保留的字，而且只有在使用中時，具有特殊意義`Iterator`函式或`Get`存取子。</span><span class="sxs-lookup"><span data-stu-id="476ad-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="476ad-120">如需有關迭代器函式和`Get`存取子中，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="476ad-120">For more information about iterator functions and `Get` accessors, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="476ad-121">Iterator 函式和 Get 存取子</span><span class="sxs-lookup"><span data-stu-id="476ad-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="476ad-122">迭代器函式宣告或`Get`存取子必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="476ad-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="476ad-123">它必須包括[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)修飾詞。</span><span class="sxs-lookup"><span data-stu-id="476ad-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="476ad-124">傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="476ad-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="476ad-125">它不能有任何`ByRef`參數。</span><span class="sxs-lookup"><span data-stu-id="476ad-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="476ad-126">Iterator 函式不能出現在事件、 執行個體建構函式、 靜態的建構函式或靜態的解構函式。</span><span class="sxs-lookup"><span data-stu-id="476ad-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="476ad-127">Iterator 函式可以是匿名函式。</span><span class="sxs-lookup"><span data-stu-id="476ad-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="476ad-128">如需詳細資訊，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="476ad-128">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="476ad-129">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="476ad-129">Exception Handling</span></span>  
 <span data-ttu-id="476ad-130">A`Yield`陳述式可以是內部`Try`區塊[再試一次...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="476ad-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="476ad-131">A`Try`區塊具有`Yield`陳述式可以有`Catch`封鎖了，而且可以有`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="476ad-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="476ad-132">A`Yield`陳述式不能在`Catch`區塊或`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="476ad-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="476ad-133">如果`For Each`（之外的迭代器函式） 的主體就會擲回例外狀況， `Catch` iterator 函式中的區塊不會執行，但`Finally`就會執行 iterator 函式中的區塊。</span><span class="sxs-lookup"><span data-stu-id="476ad-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="476ad-134">A`Catch`迭代器函式內的區塊會攔截迭代器函式內發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="476ad-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="476ad-135">技術實作</span><span class="sxs-lookup"><span data-stu-id="476ad-135">Technical Implementation</span></span>  
 <span data-ttu-id="476ad-136">下列程式碼會傳回`IEnumerable (Of String)`從 iterator 函式，然後逐一查看的項目`IEnumerable (Of String)`。</span><span class="sxs-lookup"><span data-stu-id="476ad-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="476ad-137">若要呼叫`MyIteratorFunction`不會執行函式主體。</span><span class="sxs-lookup"><span data-stu-id="476ad-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="476ad-138">呼叫會改為將 `IEnumerable(Of String)` 傳回至 `elements` 變數中。</span><span class="sxs-lookup"><span data-stu-id="476ad-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="476ad-139">在 `For Each` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。</span><span class="sxs-lookup"><span data-stu-id="476ad-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="476ad-140">這個呼叫會執行 `MyIteratorFunction` 的主體，直到下一個 `Yield` 陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="476ad-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="476ad-141">`Yield`陳述式傳回決定不僅值的運算式`element`迴圈主體所消耗的變數，但也<xref:System.Collections.Generic.IEnumerator%601.Current%2A>屬性的項目，這是`IEnumerable (Of String)`。</span><span class="sxs-lookup"><span data-stu-id="476ad-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="476ad-142">在 `For Each` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `Yield` 陳述式時再次停止。</span><span class="sxs-lookup"><span data-stu-id="476ad-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="476ad-143">`For Each`迴圈完成時的結尾迭代器函式或`Return`或`Exit Function`陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="476ad-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="476ad-144">範例</span><span class="sxs-lookup"><span data-stu-id="476ad-144">Example</span></span>  
 <span data-ttu-id="476ad-145">下列範例具有`Yield`陳述式內[For...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)迴圈。</span><span class="sxs-lookup"><span data-stu-id="476ad-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="476ad-146">每個反覆項目[每個](../../../visual-basic/language-reference/statements/for-each-next-statement.md)陳述式主體中的`Main`建立呼叫`Power`iterator 函式。</span><span class="sxs-lookup"><span data-stu-id="476ad-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="476ad-147">每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。</span><span class="sxs-lookup"><span data-stu-id="476ad-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="476ad-148">Iterator 方法的傳回型別是<xref:System.Collections.Generic.IEnumerable%601>，迭代器介面類型。</span><span class="sxs-lookup"><span data-stu-id="476ad-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="476ad-149">呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。</span><span class="sxs-lookup"><span data-stu-id="476ad-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="476ad-150">範例</span><span class="sxs-lookup"><span data-stu-id="476ad-150">Example</span></span>  
 <span data-ttu-id="476ad-151">下列範例將示範本身為迭代器的 `Get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="476ad-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="476ad-152">屬性宣告包含`Iterator`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="476ad-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 <span data-ttu-id="476ad-153">如需其他範例，請參閱[迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)。</span><span class="sxs-lookup"><span data-stu-id="476ad-153">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476ad-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="476ad-154">See Also</span></span>  
 [<span data-ttu-id="476ad-155">迭代器</span><span class="sxs-lookup"><span data-stu-id="476ad-155">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="476ad-156">陳述式</span><span class="sxs-lookup"><span data-stu-id="476ad-156">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
