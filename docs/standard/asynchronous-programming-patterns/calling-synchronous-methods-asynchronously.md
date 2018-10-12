---
title: 以非同步的方式呼叫同步方法
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET Framework], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 371e958aca87c922c902d8efd945d94d611672d9
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46702877"
---
# <a name="calling-synchronous-methods-asynchronously"></a><span data-ttu-id="8d590-102">以非同步的方式呼叫同步方法</span><span class="sxs-lookup"><span data-stu-id="8d590-102">Calling Synchronous Methods Asynchronously</span></span>

<span data-ttu-id="8d590-103">.NET Framework 可讓您以非同步方式呼叫任何方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-103">The .NET Framework enables you to call any method asynchronously.</span></span> <span data-ttu-id="8d590-104">若要這樣做，您使用相同簽章定義委派，做為您要呼叫的方法；Common Language Runtime 則會自動以適當簽章定義此委派的 `BeginInvoke` 和 `EndInvoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-104">To do this you define a delegate with the same signature as the method you want to call; the common language runtime automatically defines `BeginInvoke` and `EndInvoke` methods for this delegate, with the appropriate signatures.</span></span>

> [!NOTE]
> <span data-ttu-id="8d590-105">在 .NET Compact Framework 中不會支援非同步委派呼叫，尤其是 `BeginInvoke` 和 `EndInvoke` 方法</span><span class="sxs-lookup"><span data-stu-id="8d590-105">Asynchronous delegate calls, specifically the `BeginInvoke` and `EndInvoke` methods, are not supported in the .NET Compact Framework.</span></span>

<span data-ttu-id="8d590-106">`BeginInvoke` 方法會起始非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="8d590-106">The `BeginInvoke` method initiates the asynchronous call.</span></span> <span data-ttu-id="8d590-107">它有相同參數做為您要非同步執行的方法，再加上兩個額外的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="8d590-107">It has the same parameters as the method that you want to execute asynchronously, plus two additional optional parameters.</span></span> <span data-ttu-id="8d590-108">第一個參數是 <xref:System.AsyncCallback> 委派，參考非同步呼叫完成時所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-108">The first parameter is an <xref:System.AsyncCallback> delegate that references a method to be called when the asynchronous call completes.</span></span> <span data-ttu-id="8d590-109">第二個參數使用者定義的物件，可將資訊傳遞至回呼方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-109">The second parameter is a user-defined object that passes information into the callback method.</span></span> <span data-ttu-id="8d590-110">`BeginInvoke` 會立即傳回且不等候非同步呼叫完成。</span><span class="sxs-lookup"><span data-stu-id="8d590-110">`BeginInvoke` returns immediately and does not wait for the asynchronous call to complete.</span></span> <span data-ttu-id="8d590-111">`BeginInvoke` 傳回 <xref:System.IAsyncResult>，可用來監視非同步呼叫的進度。</span><span class="sxs-lookup"><span data-stu-id="8d590-111">`BeginInvoke` returns an <xref:System.IAsyncResult>, which can be used to monitor the progress of the asynchronous call.</span></span>

<span data-ttu-id="8d590-112">`EndInvoke` 方法會擷取非同步呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="8d590-112">The `EndInvoke` method retrieves the results of the asynchronous call.</span></span> <span data-ttu-id="8d590-113">在 `BeginInvoke`之後隨時可以呼叫它。</span><span class="sxs-lookup"><span data-stu-id="8d590-113">It can be called any time after `BeginInvoke`.</span></span> <span data-ttu-id="8d590-114">如果非同步呼叫尚未完成，在完成前 `EndInvoke` 會封鎖呼叫執行緒。</span><span class="sxs-lookup"><span data-stu-id="8d590-114">If the asynchronous call has not completed, `EndInvoke` blocks the calling thread until it completes.</span></span> <span data-ttu-id="8d590-115">`EndInvoke` 的參數包括您要非同步執行之方法的 `out` 和 `ref` 參數 (Visual Basic 為 `<Out>` `ByRef` 和 `ByRef`)，再加上 `BeginInvoke` 所傳回的 <xref:System.IAsyncResult>。</span><span class="sxs-lookup"><span data-stu-id="8d590-115">The parameters of `EndInvoke` include the `out` and `ref` parameters (`<Out>` `ByRef` and `ByRef` in Visual Basic) of the method that you want to execute asynchronously, plus the <xref:System.IAsyncResult> returned by `BeginInvoke`.</span></span>

> [!NOTE]
> <span data-ttu-id="8d590-116">Visual Studio 中的 IntelliSense 功能會顯示 `BeginInvoke` 和 `EndInvoke` 的參數。</span><span class="sxs-lookup"><span data-stu-id="8d590-116">The IntelliSense feature in Visual Studio displays the parameters of `BeginInvoke` and `EndInvoke`.</span></span> <span data-ttu-id="8d590-117">假如您並非使用 Visual Studio 或類似工具，或您使用 C# 搭配 Visual Studio，請參閱[非同步程式設計模型 (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)，以取得針對這些方法所定義的參數說明。</span><span class="sxs-lookup"><span data-stu-id="8d590-117">If you're not using Visual Studio or a similar tool, or if you're using C# with Visual Studio, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) for a description of the parameters defined for these methods.</span></span>

<span data-ttu-id="8d590-118">本主題中的程式碼範例將示範四個使用 `BeginInvoke` 和 `EndInvoke` 進行非同步呼叫的常用方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-118">The code examples in this topic demonstrate four common ways to use `BeginInvoke` and `EndInvoke` to make asynchronous calls.</span></span> <span data-ttu-id="8d590-119">呼叫 `BeginInvoke` 之後您可執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="8d590-119">After calling `BeginInvoke` you can do the following:</span></span>

-   <span data-ttu-id="8d590-120">執行一些工作，然後呼叫 `EndInvoke` 進行封鎖，直到呼叫完成。</span><span class="sxs-lookup"><span data-stu-id="8d590-120">Do some work and then call `EndInvoke` to block until the call completes.</span></span>

-   <span data-ttu-id="8d590-121">取得使用 <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> 屬性的 <xref:System.Threading.WaitHandle>，利用其 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法封鎖執行，直到 <xref:System.Threading.WaitHandle> 收到信號，接著呼叫 `EndInvoke`。</span><span class="sxs-lookup"><span data-stu-id="8d590-121">Obtain a <xref:System.Threading.WaitHandle> using the <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> property, use its <xref:System.Threading.WaitHandle.WaitOne%2A> method to block execution until the <xref:System.Threading.WaitHandle> is signaled, and then call `EndInvoke`.</span></span>

-   <span data-ttu-id="8d590-122">輪詢 <xref:System.IAsyncResult> 所傳回的 `BeginInvoke` ，判斷非同步呼叫完成的時間，然後再呼叫 `EndInvoke`。</span><span class="sxs-lookup"><span data-stu-id="8d590-122">Poll the <xref:System.IAsyncResult> returned by `BeginInvoke` to determine when the asynchronous call has completed, and then call `EndInvoke`.</span></span>

-   <span data-ttu-id="8d590-123">將回呼方法的委派傳遞至 `BeginInvoke`。</span><span class="sxs-lookup"><span data-stu-id="8d590-123">Pass a delegate for a callback method to `BeginInvoke`.</span></span> <span data-ttu-id="8d590-124">非同步呼叫完成之時，會在 <xref:System.Threading.ThreadPool> 執行緒上執行此方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-124">The method is executed on a <xref:System.Threading.ThreadPool> thread when the asynchronous call completes.</span></span> <span data-ttu-id="8d590-125">回呼方法會呼叫 `EndInvoke`。</span><span class="sxs-lookup"><span data-stu-id="8d590-125">The callback method calls `EndInvoke`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d590-126">不論您使用哪一種技術，請務必呼叫 `EndInvoke` 完成非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="8d590-126">No matter which technique you use, always call `EndInvoke` to complete your asynchronous call.</span></span>

## <a name="defining-the-test-method-and-asynchronous-delegate"></a><span data-ttu-id="8d590-127">定義測試方法和非同步委派</span><span class="sxs-lookup"><span data-stu-id="8d590-127">Defining the Test Method and Asynchronous Delegate</span></span>
 <span data-ttu-id="8d590-128">以下程式碼範例示範非同步呼叫同一個長時間執行之方法 `TestMethod`的各種方式。</span><span class="sxs-lookup"><span data-stu-id="8d590-128">The code examples that follow demonstrate various ways of calling the same long-running method, `TestMethod`, asynchronously.</span></span> <span data-ttu-id="8d590-129">`TestMethod` 方法會顯示主控台訊息，告訴您它已經開始處理、睡眠數秒鐘，然後結束。</span><span class="sxs-lookup"><span data-stu-id="8d590-129">The `TestMethod` method displays a console message to show that it has begun processing, sleeps for a few seconds, and then ends.</span></span> <span data-ttu-id="8d590-130">`TestMethod` 具有 `out` 參數，以示範這類參數加入 `BeginInvoke` 和 `EndInvoke`簽章的方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-130">`TestMethod` has an `out` parameter to demonstrate the way such parameters are added to the signatures of `BeginInvoke` and `EndInvoke`.</span></span> <span data-ttu-id="8d590-131">您可以用類似方式處理 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="8d590-131">You can handle `ref` parameters similarly.</span></span>

 <span data-ttu-id="8d590-132">下列程式碼範例顯示 `TestMethod` 的定義及名為 `AsyncMethodCaller` 且可用來非同步呼叫 `TestMethod` 的委派。</span><span class="sxs-lookup"><span data-stu-id="8d590-132">The following code example shows the definition of `TestMethod` and the delegate named `AsyncMethodCaller` that can be used to call `TestMethod` asynchronously.</span></span> <span data-ttu-id="8d590-133">若要編譯程式碼範例，您必須包含 `TestMethod` 的定義和 `AsyncMethodCaller` 委派。</span><span class="sxs-lookup"><span data-stu-id="8d590-133">To compile the code examples, you must include the definitions for `TestMethod` and the `AsyncMethodCaller` delegate.</span></span>

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a><span data-ttu-id="8d590-134">使用 EndInvoke 等候非同步呼叫</span><span class="sxs-lookup"><span data-stu-id="8d590-134">Waiting for an Asynchronous Call with EndInvoke</span></span>
 <span data-ttu-id="8d590-135">以非同步方式執行方法最簡單的方式，就是以呼叫委派的 `BeginInvoke` 方法來開始執行方法，在主執行緒上執行相同的工作，然後呼叫委派的 `EndInvoke` 方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-135">The simplest way to execute a method asynchronously is to start executing the method by calling the delegate's `BeginInvoke` method, do some work on the main thread, and then call the delegate's `EndInvoke` method.</span></span> <span data-ttu-id="8d590-136">`EndInvoke` 有可能會封鎖呼叫執行緒，因為它在非同赴呼叫完成之前都不會傳回。</span><span class="sxs-lookup"><span data-stu-id="8d590-136">`EndInvoke` might block the calling thread because it does not return until the asynchronous call completes.</span></span> <span data-ttu-id="8d590-137">這個技術非常適合運用於檔案或網路作業。</span><span class="sxs-lookup"><span data-stu-id="8d590-137">This is a good technique to use with file or network operations.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d590-138">由於 `EndInvoke` 可能會進行封鎖，因此請您千萬不要從服役於使用者介面的執行緒中呼叫它。</span><span class="sxs-lookup"><span data-stu-id="8d590-138">Because `EndInvoke` might block, you should never call it from threads that service the user interface.</span></span>

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a><span data-ttu-id="8d590-139">使用 WaitHandle 等候非同步呼叫</span><span class="sxs-lookup"><span data-stu-id="8d590-139">Waiting for an Asynchronous Call with WaitHandle</span></span>
 <span data-ttu-id="8d590-140">您可以使用取得 <xref:System.Threading.WaitHandle> 所傳回之 <xref:System.IAsyncResult.AsyncWaitHandle%2A> 的 <xref:System.IAsyncResult> 屬性，取得 `BeginInvoke`</span><span class="sxs-lookup"><span data-stu-id="8d590-140">You can obtain a <xref:System.Threading.WaitHandle> by using the <xref:System.IAsyncResult.AsyncWaitHandle%2A> property of the <xref:System.IAsyncResult> returned by `BeginInvoke`.</span></span> <span data-ttu-id="8d590-141">非同步呼叫完成時， <xref:System.Threading.WaitHandle> 會收到信號，且您可以呼叫 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法來等候它。</span><span class="sxs-lookup"><span data-stu-id="8d590-141">The <xref:System.Threading.WaitHandle> is signaled when the asynchronous call completes, and you can wait for it by calling the <xref:System.Threading.WaitHandle.WaitOne%2A> method.</span></span>

 <span data-ttu-id="8d590-142">如果您使用 <xref:System.Threading.WaitHandle>，您可以在非同步呼叫完成之前或之後，且在呼叫 `EndInvoke` 擷取結果之前，執行其他的處理。</span><span class="sxs-lookup"><span data-stu-id="8d590-142">If you use a <xref:System.Threading.WaitHandle>, you can perform additional processing before or after the asynchronous call completes, but before calling `EndInvoke` to retrieve the results.</span></span>

> [!NOTE]
> <span data-ttu-id="8d590-143">當您呼叫 `EndInvoke` 時，等候控制代碼不會自動關閉。</span><span class="sxs-lookup"><span data-stu-id="8d590-143">The wait handle is not closed automatically when you call `EndInvoke`.</span></span> <span data-ttu-id="8d590-144">如果您釋放所有等候控制代碼的參考，當記憶體回收收回等候控制代碼時，系統資源就會釋放。</span><span class="sxs-lookup"><span data-stu-id="8d590-144">If you release all references to the wait handle, system resources are freed when garbage collection reclaims the wait handle.</span></span> <span data-ttu-id="8d590-145">若要在您使用完等候控制代碼後立即釋放系統資源，請呼叫 <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> 方法來加以配置。</span><span class="sxs-lookup"><span data-stu-id="8d590-145">To free the system resources as soon as you are finished using the wait handle, dispose of it by calling the <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8d590-146">明確配置可處置的物件之後，記憶體回收會更有效率。</span><span class="sxs-lookup"><span data-stu-id="8d590-146">Garbage collection works more efficiently when disposable objects are explicitly disposed.</span></span>

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a><span data-ttu-id="8d590-147">輪詢是否完成非同步呼叫</span><span class="sxs-lookup"><span data-stu-id="8d590-147">Polling for Asynchronous Call Completion</span></span>
 <span data-ttu-id="8d590-148">您可以使用 <xref:System.IAsyncResult.IsCompleted%2A> 所傳回之 <xref:System.IAsyncResult> 的 `BeginInvoke` 屬性，找出非同步呼叫完成的時間。</span><span class="sxs-lookup"><span data-stu-id="8d590-148">You can use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by `BeginInvoke` to discover when the asynchronous call completes.</span></span> <span data-ttu-id="8d590-149">從服役於使用者介面的執行緒進行非同步呼叫時，您有可能會執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="8d590-149">You might do this when making the asynchronous call from a thread that services the user interface.</span></span> <span data-ttu-id="8d590-150">輪詢完成這個動作，可在非同步呼叫於 <xref:System.Threading.ThreadPool> 執行緒上執行的同時，讓呼叫執行緒能夠繼續執行。</span><span class="sxs-lookup"><span data-stu-id="8d590-150">Polling for completion allows the calling thread to continue executing while the asynchronous call executes on a <xref:System.Threading.ThreadPool> thread.</span></span>

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a><span data-ttu-id="8d590-151">當非同步呼叫完成時執行回呼方法</span><span class="sxs-lookup"><span data-stu-id="8d590-151">Executing a Callback Method When an Asynchronous Call Completes</span></span>
 <span data-ttu-id="8d590-152">如果起始非同步呼叫的執行緒不一定非是處理結果的執行緒時，您可以在呼叫完成時執行回呼方法。</span><span class="sxs-lookup"><span data-stu-id="8d590-152">If the thread that initiates the asynchronous call does not need to be the thread that processes the results, you can execute a callback method when the call completes.</span></span> <span data-ttu-id="8d590-153">回呼方法是在 <xref:System.Threading.ThreadPool> 執行緒上執行的。</span><span class="sxs-lookup"><span data-stu-id="8d590-153">The callback method is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

 <span data-ttu-id="8d590-154">若要使用回呼方法，您必須對 `BeginInvoke` 傳遞表示回呼方法的 <xref:System.AsyncCallback> 委派。</span><span class="sxs-lookup"><span data-stu-id="8d590-154">To use a callback method, you must pass `BeginInvoke` an <xref:System.AsyncCallback> delegate that represents the callback method.</span></span> <span data-ttu-id="8d590-155">您也可以傳遞物件，包含回呼方法所使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d590-155">You can also pass an object that contains information to be used by the callback method.</span></span> <span data-ttu-id="8d590-156">在回呼方法中，您可以將 <xref:System.IAsyncResult>這個回呼方法唯一的參數，轉換成 <xref:System.Runtime.Remoting.Messaging.AsyncResult> 物件。</span><span class="sxs-lookup"><span data-stu-id="8d590-156">In the callback method, you can cast the <xref:System.IAsyncResult>, which is the only parameter of the callback method, to an <xref:System.Runtime.Remoting.Messaging.AsyncResult> object.</span></span> <span data-ttu-id="8d590-157">接著可以再使用 <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> 屬性來取得委派，用來起使呼叫，以便您呼叫 `EndInvoke`。</span><span class="sxs-lookup"><span data-stu-id="8d590-157">You can then use the <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> property to get the delegate that was used to initiate the call so that you can call `EndInvoke`.</span></span>

 <span data-ttu-id="8d590-158">此範例的注意事項如下：</span><span class="sxs-lookup"><span data-stu-id="8d590-158">Notes on the example:</span></span>

-   <span data-ttu-id="8d590-159">`TestMethod` 的 `threadId` 參數是 `out` 參數 (在 Visual Basic 中為 [`<Out>` `ByRef`)，因此 `TestMethod` 絕對不會使用它的輸入值。</span><span class="sxs-lookup"><span data-stu-id="8d590-159">The `threadId` parameter of `TestMethod` is an `out` parameter ([`<Out>` `ByRef` in Visual Basic), so its input value is never used by `TestMethod`.</span></span> <span data-ttu-id="8d590-160">虛設變數會傳遞給 `BeginInvoke` 呼叫。</span><span class="sxs-lookup"><span data-stu-id="8d590-160">A dummy variable is passed to the `BeginInvoke` call.</span></span> <span data-ttu-id="8d590-161">如果 `threadId` 參數是 `ref` 參數 (Visual Basic 中的`ByRef` )，則變數必須是類別層級的欄位，才能同時傳遞至 `BeginInvoke` 和 `EndInvoke`。</span><span class="sxs-lookup"><span data-stu-id="8d590-161">If the `threadId` parameter were a `ref` parameter (`ByRef` in Visual Basic), the variable would have to be a class-level field so that it could be passed to both `BeginInvoke` and `EndInvoke`.</span></span>

-   <span data-ttu-id="8d590-162">傳遞至 `BeginInvoke` 的狀態資訊是格式字串，回呼方法會用它來格式化輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="8d590-162">The state information that is passed to `BeginInvoke` is a format string, which the callback method uses to format an output message.</span></span> <span data-ttu-id="8d590-163">由於狀態資訊傳遞時的型別是 <xref:System.Object>，因此必須先轉換成適當型別才能使用。</span><span class="sxs-lookup"><span data-stu-id="8d590-163">Because it is passed as type <xref:System.Object>, the state information must be cast to its proper type before it can be used.</span></span>

-   <span data-ttu-id="8d590-164">回呼是在 <xref:System.Threading.ThreadPool> 執行緒上執行的。</span><span class="sxs-lookup"><span data-stu-id="8d590-164">The callback is made on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="8d590-165"><xref:System.Threading.ThreadPool> 執行緒為背景執行緒，也就是說主執行緒結束之時，並不會讓應用程式繼續執行，因此此範例的主執行緒必須進入睡眠直到回呼完成為止。</span><span class="sxs-lookup"><span data-stu-id="8d590-165"><xref:System.Threading.ThreadPool> threads are background threads, which do not keep the application running if the main thread ends, so the main thread of the example has to sleep long enough for the callback to finish.</span></span>

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a><span data-ttu-id="8d590-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d590-166">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="8d590-167">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="8d590-167">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
