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
ms.openlocfilehash: 783785f2a078b6ad8f975846c44ee4e716a12773
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866505"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="91e55-102">Yield 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91e55-102">Yield Statement (Visual Basic)</span></span>

<span data-ttu-id="91e55-103">將集合的下一個元素傳送至 `For Each...Next` 語句。</span><span class="sxs-lookup"><span data-stu-id="91e55-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e55-104">語法</span><span class="sxs-lookup"><span data-stu-id="91e55-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="91e55-105">參數</span><span class="sxs-lookup"><span data-stu-id="91e55-105">Parameters</span></span>  
  
|<span data-ttu-id="91e55-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="91e55-106">Term</span></span>|<span data-ttu-id="91e55-107">定義</span><span class="sxs-lookup"><span data-stu-id="91e55-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="91e55-108">必要。</span><span class="sxs-lookup"><span data-stu-id="91e55-108">Required.</span></span> <span data-ttu-id="91e55-109">可隱含轉換成反覆運算器函式類型的運算式，或 `Get` 包含語句的存取子 `Yield` 。</span><span class="sxs-lookup"><span data-stu-id="91e55-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91e55-110">備註</span><span class="sxs-lookup"><span data-stu-id="91e55-110">Remarks</span></span>  

 <span data-ttu-id="91e55-111">`Yield`語句會一次傳回集合的一個元素。</span><span class="sxs-lookup"><span data-stu-id="91e55-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="91e55-112">`Yield`語句包含在反覆運算器函數或 `Get` 存取子中，它會對集合執行自訂反復專案。</span><span class="sxs-lookup"><span data-stu-id="91e55-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="91e55-113">您可以使用 For Each 的來取用 iterator 函數 ... [Next 語句](for-each-next-statement.md) 或 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="91e55-113">You consume an iterator function by using a [For Each...Next Statement](for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="91e55-114">迴圈的每個反復專案都會 `For Each` 呼叫 iterator 函數。</span><span class="sxs-lookup"><span data-stu-id="91e55-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="91e55-115">當 `Yield` 反覆運算器函式中到達語句時， `expression` 會傳回，而且會保留程式碼中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="91e55-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="91e55-116">下一次呼叫 Iterator 函式時，便會從這個位置重新開始執行。</span><span class="sxs-lookup"><span data-stu-id="91e55-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="91e55-117">從語句的類型 `expression` `Yield` 到反覆運算器的傳回型別都必須有隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="91e55-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="91e55-118">您可以使用 `Exit Function` 或 `Return` 語句來結束反復專案。</span><span class="sxs-lookup"><span data-stu-id="91e55-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="91e55-119">"Yield" 不是保留字，只有在函式或存取子中使用時，才具有特殊意義 `Iterator` `Get` 。</span><span class="sxs-lookup"><span data-stu-id="91e55-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="91e55-120">如需 iterator 函數和存取子的詳細資訊 `Get` ，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="91e55-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="91e55-121">Iterator 函數和 Get 存取子</span><span class="sxs-lookup"><span data-stu-id="91e55-121">Iterator Functions and Get Accessors</span></span>  

 <span data-ttu-id="91e55-122">反覆運算器函數或存取子的宣告 `Get` 必須符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="91e55-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="91e55-123">它必須包含 [Iterator](../modifiers/iterator.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="91e55-123">It must include an [Iterator](../modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="91e55-124">傳回類型必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="91e55-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="91e55-125">它不能有任何 `ByRef` 參數。</span><span class="sxs-lookup"><span data-stu-id="91e55-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="91e55-126">反覆運算器函數不能出現在事件、實例的函式、靜態函式或靜態的函式中。</span><span class="sxs-lookup"><span data-stu-id="91e55-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="91e55-127">Iterator 函數可以是匿名函數。</span><span class="sxs-lookup"><span data-stu-id="91e55-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="91e55-128">如需詳細資訊，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="91e55-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="91e55-129">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="91e55-129">Exception Handling</span></span>  

 <span data-ttu-id="91e55-130">`Yield`語句可以在 `Try` Try 的區塊內 ... [抓住。。。Finally 語句](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="91e55-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span> <span data-ttu-id="91e55-131">`Try`具有語句的區塊 `Yield` 可以有 `Catch` 區塊，而且可以有 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="91e55-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="91e55-132">`Yield`語句不能在 `Catch` 區塊或 `Finally` 區塊內。</span><span class="sxs-lookup"><span data-stu-id="91e55-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="91e55-133">如果在 `For Each` 反覆運算器函式之外 (主體) 擲回例外狀況， `Catch` 則不會執行 iterator 函數中的區塊，但 `Finally` 會執行 iterator 函數中的區塊。</span><span class="sxs-lookup"><span data-stu-id="91e55-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="91e55-134">`Catch`反覆運算器函式內的區塊只會捕捉反覆運算器函式內發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91e55-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="91e55-135">技術實作</span><span class="sxs-lookup"><span data-stu-id="91e55-135">Technical Implementation</span></span>  

 <span data-ttu-id="91e55-136">下列程式碼會 `IEnumerable (Of String)` 從 iterator 函數傳回，然後逐一查看的元素 `IEnumerable (Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="91e55-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="91e55-137">的呼叫 `MyIteratorFunction` 不會執行函數的主體。</span><span class="sxs-lookup"><span data-stu-id="91e55-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="91e55-138">呼叫會改為將 `IEnumerable(Of String)` 傳回至 `elements` 變數中。</span><span class="sxs-lookup"><span data-stu-id="91e55-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="91e55-139">在 `For Each` 迴圈的反覆項目上，會針對 <xref:System.Collections.IEnumerator.MoveNext%2A> 呼叫 `elements` 方法。</span><span class="sxs-lookup"><span data-stu-id="91e55-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="91e55-140">這個呼叫會執行 `MyIteratorFunction` 的主體，直到下一個 `Yield` 陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="91e55-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="91e55-141">語句會傳回 `Yield` 運算式，該運算式不僅會判斷 `element` 迴圈主體所耗用量的變數值，也會決定專案的 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 屬性，也就是 `IEnumerable (Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="91e55-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="91e55-142">在 `For Each` 迴圈的每個後續反覆項目上，迭代器主體會從上次停止的位置繼續執行，並且在到達 `Yield` 陳述式時再次停止。</span><span class="sxs-lookup"><span data-stu-id="91e55-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="91e55-143">`For Each`當到達 iterator 函數或或語句的結尾時，迴圈 `Return` `Exit Function` 就會完成。</span><span class="sxs-lookup"><span data-stu-id="91e55-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91e55-144">範例</span><span class="sxs-lookup"><span data-stu-id="91e55-144">Example</span></span>  

 <span data-ttu-id="91e55-145">下列範例 `Yield` 中的語句位於 [For .。。Next](for-next-statement.md) 迴圈。</span><span class="sxs-lookup"><span data-stu-id="91e55-145">The following example has a `Yield` statement that is inside a [For…Next](for-next-statement.md) loop.</span></span> <span data-ttu-id="91e55-146">[每個語句主體](for-each-next-statement.md)的每個反復專案 `Main` 都會建立 `Power` iterator 函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="91e55-146">Each iteration of the [For Each](for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="91e55-147">每次呼叫 Iterator 函式都會執行下一個 `Yield` 陳述式，這會在 `For…Next` 迴圈的下一個反覆項目期間發生。</span><span class="sxs-lookup"><span data-stu-id="91e55-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="91e55-148">Iterator 方法的傳回型別是 <xref:System.Collections.Generic.IEnumerable%601> ，iterator 介面型別。</span><span class="sxs-lookup"><span data-stu-id="91e55-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="91e55-149">呼叫 Iterator 方法時，它會傳回包含數字乘冪的可列舉物件。</span><span class="sxs-lookup"><span data-stu-id="91e55-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="91e55-150">範例</span><span class="sxs-lookup"><span data-stu-id="91e55-150">Example</span></span>  

 <span data-ttu-id="91e55-151">下列範例將示範本身為迭代器的 `Get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="91e55-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="91e55-152">屬性宣告包含修飾詞 `Iterator` 。</span><span class="sxs-lookup"><span data-stu-id="91e55-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="91e55-153">如需其他範例，請參閱 [反覆運算](../../programming-guide/concepts/iterators.md)器。</span><span class="sxs-lookup"><span data-stu-id="91e55-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e55-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e55-154">See also</span></span>

- [<span data-ttu-id="91e55-155">陳述式</span><span class="sxs-lookup"><span data-stu-id="91e55-155">Statements</span></span>](index.md)
