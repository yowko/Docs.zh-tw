---
title: "Await 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="ba938-102">Await 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba938-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="ba938-103">您在非同步方法或 Lambda 運算式的運算元中套用 `Await` 運算子，讓方法暫停執行，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="ba938-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="ba938-104">工作代表進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="ba938-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="ba938-105">此方法用於`Await`用必須[非同步](../../../visual-basic/language-reference/modifiers/async.md)修飾詞。</span><span class="sxs-lookup"><span data-stu-id="ba938-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="ba938-106">這種方法，定義使用`Async`修飾詞，以及通常包含一或多個`Await`運算式中，稱為*非同步方法*。</span><span class="sxs-lookup"><span data-stu-id="ba938-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba938-107">`Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。</span><span class="sxs-lookup"><span data-stu-id="ba938-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="ba938-108">非同步程式設計的簡介，請參閱[使用 Async 和 Await 進行非同步程式設計](../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ba938-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="ba938-109">一般而言，您要套用的工作`Await`運算子是實作的方法呼叫的傳回值[工作架構非同步模式](http://go.microsoft.com/fwlink/?LinkId=204847)，亦即，<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="ba938-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="ba938-110">下列程式碼，<xref:System.Net.Http.HttpClient>方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>傳回`getContentsTask`、 `Task(Of Byte())`。</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="ba938-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="ba938-111">這個工作可保證作業完成時，一定會產生實際位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="ba938-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="ba938-112">`Await` 運算子會套用至 `getContentsTask` 以暫停在 `SumPageSizesAsync` 中執行，直到 `getContentsTask` 完成。</span><span class="sxs-lookup"><span data-stu-id="ba938-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="ba938-113">同時，控制權會返回 `SumPageSizesAsync` 的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="ba938-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="ba938-114">當 `getContentsTask` 完成之後，`Await` 運算式會評估為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="ba938-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
<span data-ttu-id="ba938-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ba938-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="ba938-116">完整的範例，請參閱[逐步解說︰ 存取 Web 使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="ba938-116">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="ba938-117">您可以下載從範例[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)Microsoft 網站上。</span><span class="sxs-lookup"><span data-stu-id="ba938-117">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="ba938-118">此範例位於 AsyncWalkthrough_HttpClient 專案中。</span><span class="sxs-lookup"><span data-stu-id="ba938-118">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="ba938-119">如果將 `Await` 套用至傳回 `Task(Of TResult)` 之方法呼叫的結果，則 `Await` 運算式的類型為 TResult。</span><span class="sxs-lookup"><span data-stu-id="ba938-119">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="ba938-120">如果 `Await` 套用至傳回 `Task` 之方法呼叫的結果，則 `Await` 運算式不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="ba938-120">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="ba938-121">下列範例會說明其間的差異。</span><span class="sxs-lookup"><span data-stu-id="ba938-121">The following example illustrates the difference.</span></span>  
  
<span data-ttu-id="ba938-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="ba938-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="ba938-123">`Await` 運算式或陳述式不會封鎖其執行所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ba938-123">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="ba938-124">但是它會造成編譯器將 `Await` 運算式之後的其餘非同步方法註冊為所等候工作的接續。</span><span class="sxs-lookup"><span data-stu-id="ba938-124">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="ba938-125">控制權接著會返回非同步方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="ba938-125">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="ba938-126">當工作完成時，它會叫用其接續，並從中斷處繼續執行非同步方法。</span><span class="sxs-lookup"><span data-stu-id="ba938-126">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="ba938-127">`Await` 運算式可能只會在 `Async` 修飾詞所標示之立即封入方法或 Lambda 運算式主體中發生。</span><span class="sxs-lookup"><span data-stu-id="ba938-127">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="ba938-128">這個詞彙*Await*做為關鍵字只在該內容。</span><span class="sxs-lookup"><span data-stu-id="ba938-128">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="ba938-129">在其他內容中，它會解譯為識別項。</span><span class="sxs-lookup"><span data-stu-id="ba938-129">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="ba938-130">在非同步方法或 lambda 運算式`Await`運算式不能出現在查詢運算式中，在`catch`或`finally`區塊[試...Catch...最後](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)的迴圈控制變數運算式中的陳述式，`For`或`For Each`迴圈，或在本文中[SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="ba938-130">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="ba938-131">例外狀況</span><span class="sxs-lookup"><span data-stu-id="ba938-131">Exceptions</span></span>  
 <span data-ttu-id="ba938-132">大部分的非同步方法會傳回<xref:System.Threading.Tasks.Task>或<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="ba938-132">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ba938-133">傳回的工作屬性會隨附其狀態和記錄的相關資訊，例如工作是否完成、非同步方法是否造成例外狀況或已取消，以及最終結果為何。</span><span class="sxs-lookup"><span data-stu-id="ba938-133">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="ba938-134">`Await` 運算子存取這些屬性。</span><span class="sxs-lookup"><span data-stu-id="ba938-134">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="ba938-135">如果您在等候工作傳回非同步方法時導致例外狀況，`Await` 運算子會重新擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ba938-135">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="ba938-136">如果您等候已取消的工作傳回非同步方法`Await`運算子會重新擲回<xref:System.OperationCanceledException>.</xref:System.OperationCanceledException></span><span class="sxs-lookup"><span data-stu-id="ba938-136">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="ba938-137">處於錯誤狀態的單一工作可能反映多個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ba938-137">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="ba938-138">例如，工作可能是<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>呼叫的結果</span><span class="sxs-lookup"><span data-stu-id="ba938-138">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="ba938-139">當您等候這類工作時，await 作業只會重新擲回其中一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ba938-139">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="ba938-140">不過，您無法預測重新擲回哪個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ba938-140">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="ba938-141">例如非同步方法中的錯誤處理的詳細資訊，請參閱[試...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ba938-141">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba938-142">範例</span><span class="sxs-lookup"><span data-stu-id="ba938-142">Example</span></span>  
 <span data-ttu-id="ba938-143">下列 Windows Form 範例說明如何在非同步方法 `WaitAsynchronouslyAsync` 中使用 `Await`。</span><span class="sxs-lookup"><span data-stu-id="ba938-143">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="ba938-144">請對照該方法的行為與 `WaitSynchronously` 的行為。</span><span class="sxs-lookup"><span data-stu-id="ba938-144">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="ba938-145">不含`Await`運算子，`WaitSynchronously`會同步執行，就算使用`Async`修飾詞，在其定義，以及呼叫<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>其主體中。</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ba938-145">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> in its body.</span></span>  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba938-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba938-146">See Also</span></span>  
 <span data-ttu-id="ba938-147">[非同步程式設計使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="ba938-147">[Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="ba938-148"> [逐步解說︰ 存取 Web 使用 Async 和 Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="ba938-148"> [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="ba938-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span><span class="sxs-lookup"><span data-stu-id="ba938-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span></span>
