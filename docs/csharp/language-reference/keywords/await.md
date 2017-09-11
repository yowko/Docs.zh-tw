---
title: "await (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- await_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 79ba9d49d7650eb0183b52704c4cefd736260343
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="await-c-reference"></a><span data-ttu-id="61a0e-102">await (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="61a0e-102">await (C# Reference)</span></span>
<span data-ttu-id="61a0e-103">`await` 運算子會套用至非同步方法中的工作以暫停執行方法，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="61a0e-103">The `await` operator is applied to a task in an asynchronous method to suspend the execution of the method until the awaited task completes.</span></span> <span data-ttu-id="61a0e-104">工作代表進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="61a0e-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="61a0e-105">在其中使用 `await` 的非同步方法必須由 [async](../../../csharp/language-reference/keywords/async.md) 關鍵字修改。</span><span class="sxs-lookup"><span data-stu-id="61a0e-105">The asynchronous method in which `await` is used must be modified by the [async](../../../csharp/language-reference/keywords/async.md) keyword.</span></span> <span data-ttu-id="61a0e-106">這種方法是使用 `async` 修飾詞所定義，且通常包含一或多個 `await` 運算式，我們稱之為「非同步方法」。</span><span class="sxs-lookup"><span data-stu-id="61a0e-106">Such a method, defined by using the `async` modifier, and usually containing one or more `await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61a0e-107">`async` 和 `await` 關鍵字是在 Visual Studio 2012 中引入。</span><span class="sxs-lookup"><span data-stu-id="61a0e-107">The `async` and `await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="61a0e-108">如需非同步程式設計的簡介，請參閱[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="61a0e-108">For an introduction to async programming, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="61a0e-109">套用 `await` 運算子的工作，通常是呼叫實作[工作式非同步模式](http://go.microsoft.com/fwlink/?LinkId=204847)的方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="61a0e-109">The task to which the `await` operator is applied typically is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847).</span></span> <span data-ttu-id="61a0e-110">範例包括 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 類型的值。</span><span class="sxs-lookup"><span data-stu-id="61a0e-110">Examples include values of type <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="61a0e-111">在下列程式碼中，<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 會傳回 `Task\<byte[]>`、`getContentsTask`。</span><span class="sxs-lookup"><span data-stu-id="61a0e-111">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns a `Task\<byte[]>`, `getContentsTask`.</span></span> <span data-ttu-id="61a0e-112">這個工作可保證工作完成時，一定會產生實際位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="61a0e-112">The task is a promise to produce the actual byte array when the task is complete.</span></span> <span data-ttu-id="61a0e-113">`await` 運算子會套用至 `getContentsTask` 以暫停在 `SumPageSizesAsync` 中執行，直到 `getContentsTask` 完成。</span><span class="sxs-lookup"><span data-stu-id="61a0e-113">The `await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="61a0e-114">同時，控制權會返回 `SumPageSizesAsync` 的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="61a0e-114">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="61a0e-115">當 `getContentsTask` 完成之後，`await` 運算式會評估為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="61a0e-115">When `getContentsTask` is finished, the `await` expression evaluates to a byte array.</span></span>  
  
```csharp  
private async Task SumPageSizesAsync()  
{  
    // To use the HttpClient type in desktop apps, you must include a using directive and add a   
    // reference for the System.Net.Http namespace.  
    HttpClient client = new HttpClient();  
    // . . .  
    Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
    byte[] urlContents = await getContentsTask;  
  
    // Equivalently, now that you see how it works, you can write the same thing in a single line.  
    //byte[] urlContents = await client.GetByteArrayAsync(url);  
    // . . .  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="61a0e-116">如需完整範例，請參閱[逐步解說：使用 async 和 await 存取 Web](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="61a0e-116">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="61a0e-117">您可以從 Microsoft 網站的[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) 下載此範例。</span><span class="sxs-lookup"><span data-stu-id="61a0e-117">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="61a0e-118">此範例位於 AsyncWalkthrough_HttpClient 專案中。</span><span class="sxs-lookup"><span data-stu-id="61a0e-118">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="61a0e-119">如先前範例所示，如果將 `await` 套用至傳回 `Task<TResult>` 之方法呼叫的結果，則 `await` 運算式的類型為 TResult。</span><span class="sxs-lookup"><span data-stu-id="61a0e-119">As shown in the previous example, if `await` is applied to the result of a method call that returns a `Task<TResult>`, then the type of the `await` expression is TResult.</span></span> <span data-ttu-id="61a0e-120">如果將 `await` 套用至傳回 `Task` 之方法呼叫的結果，則 `await` 運算式的類型為 void。</span><span class="sxs-lookup"><span data-stu-id="61a0e-120">If `await` is applied to the result of a method call that returns a `Task`, then the type of the `await` expression is void.</span></span> <span data-ttu-id="61a0e-121">下列範例會說明其間的差異。</span><span class="sxs-lookup"><span data-stu-id="61a0e-121">The following example illustrates the difference.</span></span>  
  
```csharp  
// Keyword await used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// Keyword await used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  
```  
  
 <span data-ttu-id="61a0e-122">`await` 運算式不會封鎖其執行所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="61a0e-122">An `await` expression does not block the thread on which it is executing.</span></span> <span data-ttu-id="61a0e-123">但是它會造成編譯器將其餘非同步方法註冊為所等候工作的接續。</span><span class="sxs-lookup"><span data-stu-id="61a0e-123">Instead, it causes the compiler to sign up the rest of the async method as a continuation on the awaited task.</span></span> <span data-ttu-id="61a0e-124">控制權接著會返回非同步方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="61a0e-124">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="61a0e-125">當工作完成時，它會叫用其接續，並從中斷處繼續執行非同步方法。</span><span class="sxs-lookup"><span data-stu-id="61a0e-125">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="61a0e-126">`await` 運算式可能只會在 `async` 修飾詞所標示之立即封入方法、Lambda 運算式或匿名方法的主體中發生。</span><span class="sxs-lookup"><span data-stu-id="61a0e-126">An `await` expression can occur only in the body of an immediately enclosing method, lambda expression, or anonymous method that is marked by an `async` modifier.</span></span> <span data-ttu-id="61a0e-127">*await* 這個詞彙只在該內容中作為關鍵字。</span><span class="sxs-lookup"><span data-stu-id="61a0e-127">The term *await* serves as a keyword only in that context.</span></span> <span data-ttu-id="61a0e-128">在其他內容中，它會解譯為識別項。</span><span class="sxs-lookup"><span data-stu-id="61a0e-128">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="61a0e-129">在方法、Lambda 運算式或匿名方法中，`await` 運算式不能出現在同步函式、查詢運算式、[lock 陳述式](../../../csharp/language-reference/keywords/lock-statement.md)的區塊，或是 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容中。</span><span class="sxs-lookup"><span data-stu-id="61a0e-129">Within the method, lambda expression, or anonymous method, an `await` expression cannot occur in the body of a synchronous function, in a query expression,, in the block of a [lock statement](../../../csharp/language-reference/keywords/lock-statement.md), or in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="61a0e-130">例外狀況</span><span class="sxs-lookup"><span data-stu-id="61a0e-130">Exceptions</span></span>  
 <span data-ttu-id="61a0e-131">大部分的非同步方法會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="61a0e-131">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="61a0e-132">傳回的工作屬性會隨附其狀態和記錄的相關資訊，例如工作是否完成、非同步方法是否造成例外狀況或已取消，以及最終結果為何。</span><span class="sxs-lookup"><span data-stu-id="61a0e-132">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="61a0e-133">`await` 運算子存取這些屬性。</span><span class="sxs-lookup"><span data-stu-id="61a0e-133">The `await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="61a0e-134">如果您在等候工作傳回非同步方法時導致例外狀況，`await` 運算子會重新擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61a0e-134">If you await a task-returning async method that causes an exception, the  `await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="61a0e-135">如果您等候已取消的工作傳回非同步方法，則 `await` 運算子會重新擲回 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="61a0e-135">If you await a task-returning async method that's canceled, the `await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="61a0e-136">處於錯誤狀態的單一工作可能反映多個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61a0e-136">A single task that is in a faulted state can reflect multiple exceptions.</span></span> <span data-ttu-id="61a0e-137">例如，工作可能是 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> 呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="61a0e-137">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="61a0e-138">當您等候這類工作時，await 作業只會重新擲回其中一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61a0e-138">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="61a0e-139">不過，您無法預測重新擲回哪個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="61a0e-139">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="61a0e-140">如需非同步方法中錯誤處理的範例，請參閱 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)。</span><span class="sxs-lookup"><span data-stu-id="61a0e-140">For examples of error handling in async methods, see [try-catch](../../../csharp/language-reference/keywords/try-catch.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61a0e-141">範例</span><span class="sxs-lookup"><span data-stu-id="61a0e-141">Example</span></span>  
 <span data-ttu-id="61a0e-142">下列 Windows Form 範例說明如何在非同步方法 `WaitAsynchronouslyAsync` 中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="61a0e-142">The following Windows Forms example illustrates the use of `await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="61a0e-143">請對照該方法的行為與 `WaitSynchronously` 的行為。</span><span class="sxs-lookup"><span data-stu-id="61a0e-143">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="61a0e-144">若未將 `await` 運算子套用至工作，儘管在定義中使用 `async` 修飾詞並在主體中呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>，`WaitSynchronously` 仍會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="61a0e-144">Without an `await` operator applied to a task, `WaitSynchronously` runs synchronously despite the use of the `async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> in its body.</span></span>  
  
```csharp  
private async void button1_Click(object sender, EventArgs e)  
{  
    // Call the method that runs asynchronously.  
    string result = await WaitAsynchronouslyAsync();  
  
    // Call the method that runs synchronously.  
    //string result = await WaitSynchronously ();  
  
    // Display the result.  
    textBox1.Text += result;  
}  
  
// The following method runs asynchronously. The UI thread is not  
// blocked during the delay. You can move or resize the Form1 window   
// while Task.Delay is running.  
public async Task<string> WaitAsynchronouslyAsync()  
{  
    await Task.Delay(10000);  
    return "Finished";  
}  
  
// The following method runs synchronously, despite the use of async.  
// You cannot move or resize the Form1 window while Thread.Sleep  
// is running because the UI thread is blocked.  
public async Task<string> WaitSynchronously()  
{  
    // Add a using directive for System.Threading.  
    Thread.Sleep(10000);  
    return "Finished";  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="61a0e-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61a0e-145">See Also</span></span>  
 <span data-ttu-id="61a0e-146">[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="61a0e-146">[Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="61a0e-147"> [逐步解說：使用 async 和 await 存取 Web](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="61a0e-147"> [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="61a0e-148"> [async](../../../csharp/language-reference/keywords/async.md)</span><span class="sxs-lookup"><span data-stu-id="61a0e-148"> [async](../../../csharp/language-reference/keywords/async.md)</span></span>

