---
title: 深入了解非同步
description: 了解如何使用 .NET 工作架構非同步模型，直接撰寫 I/O 繫結和 CPU 繫結非同步程式碼。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 0c098d0697dff3e1e772c348597a84ac9d262104
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085312"
---
# <a name="async-in-depth"></a><span data-ttu-id="374ee-103">深入了解非同步</span><span class="sxs-lookup"><span data-stu-id="374ee-103">Async in depth</span></span>

<span data-ttu-id="374ee-104">撰寫 I/O-bound 和 CPU-bound 非同步程式碼的直接做法，就是使用以 .NET 工作為基礎的非同步模型。</span><span class="sxs-lookup"><span data-stu-id="374ee-104">Writing I/O- and CPU-bound asynchronous code is straightforward using the .NET Task-based async model.</span></span> <span data-ttu-id="374ee-105">在 C# 和 Visual Basic 中，此模型是由 `Task` 和 `Task<T>` 類型以及 `async` 和 `await` 關鍵字所公開。</span><span class="sxs-lookup"><span data-stu-id="374ee-105">The model is exposed by the `Task` and `Task<T>` types and the `async` and `await` keywords in C# and Visual Basic.</span></span> <span data-ttu-id="374ee-106">(您可以在[另請參閱](#see-also)一節中找到特定語言資源)。本文說明如何使用 .NET 非同步，並深入解析幕後所使用的非同步架構。</span><span class="sxs-lookup"><span data-stu-id="374ee-106">(Language-specific resources are found in the [See also](#see-also) section.) This article explains how to use .NET async and provides insight into the async framework used under the covers.</span></span>

## <a name="task-and-tasklttgt"></a><span data-ttu-id="374ee-107">Task 與 Task&lt;T&gt;</span><span class="sxs-lookup"><span data-stu-id="374ee-107">Task and Task&lt;T&gt;</span></span>

<span data-ttu-id="374ee-108">Task 是用來實作稱為 [Promise 並行存取模型](https://en.wikipedia.org/wiki/Futures_and_promises)的建構。</span><span class="sxs-lookup"><span data-stu-id="374ee-108">Tasks are constructs used to implement what is known as the [Promise Model of Concurrency](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>  <span data-ttu-id="374ee-109">簡單地說，它們會對您「承諾」工作將於稍後完成，讓您以無障礙的 API 來協調此承諾。</span><span class="sxs-lookup"><span data-stu-id="374ee-109">In short, they offer you a "promise" that work will be completed at a later point, letting you coordinate with the promise with a clean API.</span></span>

*   <span data-ttu-id="374ee-110">`Task` 代表不會傳回值的單一作業。</span><span class="sxs-lookup"><span data-stu-id="374ee-110">`Task` represents a single operation which does not return a value.</span></span>
*   <span data-ttu-id="374ee-111">`Task<T>` 代表會傳回類型為 `T` 之值的單一作業。</span><span class="sxs-lookup"><span data-stu-id="374ee-111">`Task<T>` represents a single operation which returns a value of type `T`.</span></span>

<span data-ttu-id="374ee-112">您必須了解 Task 是以非同步方式執行工作的抽象層，而「不是」透過執行緒的抽象層。</span><span class="sxs-lookup"><span data-stu-id="374ee-112">It’s important to reason about tasks as abstractions of work happening asynchronously, and *not* an abstraction over threading.</span></span> <span data-ttu-id="374ee-113">根據預設，Task 會在目前的執行緒上執行，並視需要將工作委派給作業系統。</span><span class="sxs-lookup"><span data-stu-id="374ee-113">By default, tasks execute on the current thread and delegate work to the Operating System, as appropriate.</span></span> <span data-ttu-id="374ee-114">您可以選擇明確要求透過 `Task.Run` API 在個別執行緒上執行工作。</span><span class="sxs-lookup"><span data-stu-id="374ee-114">Optionally, tasks can be explicitly requested to run on a separate thread via the `Task.Run` API.</span></span>

<span data-ttu-id="374ee-115">Task 會公開 API 通訊協定，以監視、等候及存取 Task 的結果值 (如果是 `Task<T>`)。</span><span class="sxs-lookup"><span data-stu-id="374ee-115">Tasks expose an API protocol for monitoring, waiting upon and accessing the result value (in the case of `Task<T>`) of a task.</span></span> <span data-ttu-id="374ee-116">與 `await` 關鍵字的語言整合提供更高層級的抽象層來使用 Task。</span><span class="sxs-lookup"><span data-stu-id="374ee-116">Language integration, with the `await` keyword, provides a higher-level abstraction for using tasks.</span></span> 

<span data-ttu-id="374ee-117">使用 `await` 可在某個 Task 正在執行時，藉由將控制權轉讓給其呼叫端直到該 Task 完成為止，來允許您的應用程式或服務執行有用的工作。</span><span class="sxs-lookup"><span data-stu-id="374ee-117">Using `await` allows your application or service to perform useful work while a task is running by yielding control to its caller until the task is done.</span></span> <span data-ttu-id="374ee-118">您的程式碼不需要依賴回呼或事件，就能在 Task 完成之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="374ee-118">Your code does not need to rely on callbacks or events to continue execution after the task has been completed.</span></span> <span data-ttu-id="374ee-119">語言和工作 API 整合會為您執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="374ee-119">The language and task API integration does that for you.</span></span> <span data-ttu-id="374ee-120">如果您使用 `Task<T>`，`await` 關鍵字會另外將工作完成時所傳回的值「解除包裝」。</span><span class="sxs-lookup"><span data-stu-id="374ee-120">If you’re using `Task<T>`, the `await` keyword will additionally "unwrap" the value returned when the Task is complete.</span></span>  <span data-ttu-id="374ee-121">以下將進一步說明其運作方式的細節。</span><span class="sxs-lookup"><span data-stu-id="374ee-121">The details of how this works are explained further below.</span></span>

<span data-ttu-id="374ee-122">如需工作及與其互動之不同方式的詳細資訊，請參閱[工作架構非同步模式 (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="374ee-122">You can learn more about tasks and the different ways to interact with them in the [Task-based Asynchronous Pattern (TAP)](~/docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) topic.</span></span>

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a><span data-ttu-id="374ee-123">更深入了解 I/O-Bound 作業的 Task</span><span class="sxs-lookup"><span data-stu-id="374ee-123">Deeper Dive into Tasks for an I/O-Bound Operation</span></span>

<span data-ttu-id="374ee-124">下一節將概要描述使用一般非同步 I/O 呼叫會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="374ee-124">The following section describes a 10,000 foot view of what happens with a typical async I/O call.</span></span> <span data-ttu-id="374ee-125">首先讓我們示範兩個範例。</span><span class="sxs-lookup"><span data-stu-id="374ee-125">Let's start with a couple examples.</span></span>

<span data-ttu-id="374ee-126">第一個範例會呼叫非同步方法，並傳回作用中但可能尚未完成的 Task。</span><span class="sxs-lookup"><span data-stu-id="374ee-126">The first example calls an async method and returns an active task, likely yet to complete.</span></span>

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    return client.GetStringAsync("http://www.dotnetfoundation.org");
}
```

<span data-ttu-id="374ee-127">第二個範例會新增 `async` 和 `await` 關鍵字的使用，以在工作上運作。</span><span class="sxs-lookup"><span data-stu-id="374ee-127">The second example adds the use of the `async` and `await` keywords to operate on the task.</span></span>

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();
    
    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("http://www.dotnetfoundation.org");
    
    // Execution resumes when the client.GetStringAsync task completes,
    // becoming synchronous again.
    
    if (count > page.Length)
    {
        return page;
    }
    else
    {
        return page.Substring(0, count);
    }
}
```

<span data-ttu-id="374ee-128">對 `GetStringAsync()` 的呼叫會在較低層級的 .NET 程式庫中進行 (也可能會呼叫其他非同步方法)，直到抵達原生網路程式庫中的 P/Invoke Interop 呼叫。</span><span class="sxs-lookup"><span data-stu-id="374ee-128">The call to `GetStringAsync()` calls through lower-level .NET libraries (perhaps calling other async methods) until it reaches a P/Invoke interop call into a native networking library.</span></span> <span data-ttu-id="374ee-129">接著可能會在系統 API 呼叫中呼叫原生程式庫 (例如對 Linux 上的通訊端呼叫 `write()`)。</span><span class="sxs-lookup"><span data-stu-id="374ee-129">The native library may subsequently call into a System API call (such as `write()` to a socket on Linux).</span></span> <span data-ttu-id="374ee-130">系統可能會使用 [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)) 在原生/Managed 界限處建立 Task 物件。</span><span class="sxs-lookup"><span data-stu-id="374ee-130">A task object will be created at the native/managed boundary, possibly using [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)).</span></span> <span data-ttu-id="374ee-131">此 Task 物件會向上傳遞給所有層級，可能在其上運作或直接傳回，最後將傳回給初始呼叫端。</span><span class="sxs-lookup"><span data-stu-id="374ee-131">The task object will be passed up through the layers, possibly operated on or directly returned, eventually returned to the initial caller.</span></span> 

<span data-ttu-id="374ee-132">在上述第二個範例中，會從 `GetStringAsync` 傳回 `Task<T>` 物件。</span><span class="sxs-lookup"><span data-stu-id="374ee-132">In the second example above, a `Task<T>` object will be returned from `GetStringAsync`.</span></span> <span data-ttu-id="374ee-133">使用 `await` 關鍵字會導致方法傳回新建立的 Task 物件。</span><span class="sxs-lookup"><span data-stu-id="374ee-133">The use of the `await` keyword causes the method to return a newly created task object.</span></span> <span data-ttu-id="374ee-134">控制權會從 `GetFirstCharactersCountAsync` 方法的此位置返回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="374ee-134">Control returns to the caller from this location in the `GetFirstCharactersCountAsync` method.</span></span> <span data-ttu-id="374ee-135">[Task&lt;T&gt;](xref:System.Threading.Tasks.Task%601) 物件的方法和屬性可讓呼叫端監視 Task 的進度，此 Task 將在 GetFirstCharactersCountAsync 中的其餘程式碼都已執行之後完成。</span><span class="sxs-lookup"><span data-stu-id="374ee-135">The methods and properties of the [Task&lt;T&gt;](xref:System.Threading.Tasks.Task%601) object enable callers to monitor the progress of the task, which will complete when the remaining code in GetFirstCharactersCountAsync has executed.</span></span>

<span data-ttu-id="374ee-136">系統 API 呼叫之後，要求現在會在核心空間，直到抵達 OS 的網路子系統 (例如 Linux 核心中的 `/net`)。</span><span class="sxs-lookup"><span data-stu-id="374ee-136">After the System API call, the request is now in kernel space, making its way to the networking subsystem of the OS (such as `/net` in the Linux Kernel).</span></span>  <span data-ttu-id="374ee-137">OS 將在此「以非同步方式」處理網路要求。</span><span class="sxs-lookup"><span data-stu-id="374ee-137">Here the OS will handle the networking request *asynchronously*.</span></span>  <span data-ttu-id="374ee-138">相關細節可能會因使用的 OS 而有所不同 (裝置驅動程式呼叫可能會排程作為傳回執行階段的信號，或裝置驅動程式呼叫可能會發出「再」傳回信號)，但最後都會通知執行階段此網路要求正在進行中。</span><span class="sxs-lookup"><span data-stu-id="374ee-138">Details may be different depending on the OS used (the device driver call may be scheduled as a signal sent back to the runtime, or a device driver call may be made and *then* a signal sent back), but eventually the runtime will be informed that the networking request is in progress.</span></span>  <span data-ttu-id="374ee-139">此時，裝置驅動程式的工作將會是已排程、進行中或已完成 (要求已「透過網路」送出)，但由於全部都會以非同步方式進行，因此裝置驅動程式能夠立即處理其他工作！</span><span class="sxs-lookup"><span data-stu-id="374ee-139">At this time, the work for the device driver will either be scheduled, in-progress, or already finished (the request is already out "over the wire") - but because this is all happening asynchronously, the device driver is able to immediately handle something else!</span></span>

<span data-ttu-id="374ee-140">例如，在 Windows 中，OS 執行緒會呼叫網路裝置驅動程式，並要求它透過代表網路作業的插斷要求封包 (IRP) 來執行此作業。</span><span class="sxs-lookup"><span data-stu-id="374ee-140">For example, in Windows an OS thread makes a call to the network device driver and asks it to perform the networking operation via an Interrupt Request Packet (IRP) which represents the operation.</span></span>  <span data-ttu-id="374ee-141">裝置驅動程式會接收 IRP、對網路進行呼叫、將 IRP 標記為「擱置」，然後傳回給 OS。</span><span class="sxs-lookup"><span data-stu-id="374ee-141">The device driver receives the IRP, makes the call to the network, marks the IRP as "pending", and returns back to the OS.</span></span>  <span data-ttu-id="374ee-142">因為 OS 執行緒現在知道 IRP 處於「擱置」狀態，所以沒有任何要讓此作業執行的工作，並且會「傳回」以便用來執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="374ee-142">Because the OS thread now knows that the IRP is "pending", it doesn't have any more work to do for this job and "returns" back so that it can be used to perform other work.</span></span>

<span data-ttu-id="374ee-143">要求完成並透過裝置驅動程式傳回資料之後，它會通知 CPU 透過插斷收到的新資料。</span><span class="sxs-lookup"><span data-stu-id="374ee-143">When the request is fulfilled and data comes back through the device driver, it notifies the CPU of new data received via an interrupt.</span></span>  <span data-ttu-id="374ee-144">此插斷的處理方式會因 OS 而有所不同，但最後會將資料傳遞通過 OS，直到抵達系統 Interop 呼叫 (例如在 Linux 中，插斷處理常式會排程 IRQ 的後半部，以非同步方式將資料上傳通過 OS)。</span><span class="sxs-lookup"><span data-stu-id="374ee-144">How this interrupt gets handled will vary depending on the OS, but eventually the data will be passed through the OS until it reaches a system interop call (for example, in Linux an interrupt handler will schedule the bottom half of the IRQ to pass the data up through the OS asynchronously).</span></span>  <span data-ttu-id="374ee-145">請注意，這「也是」以非同步方式進行！</span><span class="sxs-lookup"><span data-stu-id="374ee-145">Note that this *also* happens asynchronously!</span></span>  <span data-ttu-id="374ee-146">此結果會排入佇列，等候下一個可用的執行緒能夠執行非同步方法並將已完成 Task 的結果「解除包裝」。</span><span class="sxs-lookup"><span data-stu-id="374ee-146">The result is queued up until the next available thread is able execute the async method and "unwrap" the result of the completed task.</span></span>

<span data-ttu-id="374ee-147">這整個過程的重點是**沒有專門用來執行 Task 的執行緒**。</span><span class="sxs-lookup"><span data-stu-id="374ee-147">Throughout this entire process, a key takeaway is that **no thread is dedicated to running the task**.</span></span>  <span data-ttu-id="374ee-148">雖然在某些情況下會執行工作 (也就是，OS 必須將資料傳遞給裝置驅動程式並回應插斷)，但沒有專門用來「等候」所要求資料傳回的執行緒。</span><span class="sxs-lookup"><span data-stu-id="374ee-148">Although work is executed in some context (that is, the OS does have to pass data to a device driver and respond to an interrupt), there is no thread dedicated to *waiting* for data from the request to come back.</span></span>  <span data-ttu-id="374ee-149">比起等候一些 I/O 呼叫完成，這樣做可讓系統處理更大量的工作。</span><span class="sxs-lookup"><span data-stu-id="374ee-149">This allows the system to handle a much larger volume of work rather than waiting for some I/O call to finish.</span></span>

<span data-ttu-id="374ee-150">雖然上述做法似乎需要完成許多工作，但以時鐘時間測量時，它所花費的時間相較於實際 I/O 工作簡直是小巫見大巫。</span><span class="sxs-lookup"><span data-stu-id="374ee-150">Although the above may seem like a lot of work to be done, when measured in terms of wall clock time, it’s miniscule compared to the time it takes to do the actual I/O work.</span></span> <span data-ttu-id="374ee-151">雖然不完全精確，但這類呼叫的時間軸可能類似如下：</span><span class="sxs-lookup"><span data-stu-id="374ee-151">Although not at all precise, a potential timeline for such a call would look like this:</span></span>

<span data-ttu-id="374ee-152">0-1————————————————————————————————————————————————–2-3</span><span class="sxs-lookup"><span data-stu-id="374ee-152">0-1————————————————————————————————————————————————–2-3</span></span>

*   <span data-ttu-id="374ee-153">從點 `0` 至 `1` 所花費的時間，會用在非同步方法將控制權轉讓給其呼叫端之前的所有工作。</span><span class="sxs-lookup"><span data-stu-id="374ee-153">Time spent from points `0` to `1` is everything up until an async method yields control to its caller.</span></span>
*   <span data-ttu-id="374ee-154">從點 `1` 至 `2` 所花費的時間，是 I/O 上所花費的時間 (不含 CPU 成本)。</span><span class="sxs-lookup"><span data-stu-id="374ee-154">Time spent from points `1` to `2` is the time spent on I/O, with no CPU cost.</span></span>
*   <span data-ttu-id="374ee-155">最後，從點 `2` 至 `3` 所花費的時間，會用在將控制權 (可能還有值) 交回給非同步方法，然後再次執行。</span><span class="sxs-lookup"><span data-stu-id="374ee-155">Finally, time spent from points `2` to `3` is passing control back (and potentially a value) to the async method, at which point it is executing again.</span></span>

### <a name="what-does-this-mean-for-a-server-scenario"></a><span data-ttu-id="374ee-156">這對伺服器案例有何意義？</span><span class="sxs-lookup"><span data-stu-id="374ee-156">What does this mean for a server scenario?</span></span>

<span data-ttu-id="374ee-157">此模型適用於一般伺服器案例的工作負載。</span><span class="sxs-lookup"><span data-stu-id="374ee-157">This model works well with a typical server scenario workload.</span></span>  <span data-ttu-id="374ee-158">因為沒有封鎖未完成 Task 的專用執行緒，所以伺服器執行緒集區可以服務更大量的 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="374ee-158">Because there are no threads dedicated to blocking on unfinished tasks, the server threadpool can service a much higher volume of web requests.</span></span>

<span data-ttu-id="374ee-159">以兩部伺服器為例︰一部執行非同步程式碼，另一部不執行。</span><span class="sxs-lookup"><span data-stu-id="374ee-159">Consider two servers: one that runs async code, and one that does not.</span></span>  <span data-ttu-id="374ee-160">在此範例中，每部伺服器只有 5 個執行緒可用來服務要求。</span><span class="sxs-lookup"><span data-stu-id="374ee-160">For the purpose of this example, each server only has 5 threads available to service requests.</span></span>  <span data-ttu-id="374ee-161">請注意，此數目比想像中的小，僅供示範內容使用。</span><span class="sxs-lookup"><span data-stu-id="374ee-161">Note that these numbers are imaginarily small and serve only in a demonstrative context.</span></span>

<span data-ttu-id="374ee-162">假設這兩部伺服器收到 6 個並行要求。</span><span class="sxs-lookup"><span data-stu-id="374ee-162">Assume both servers receive 6 concurrent requests.</span></span> <span data-ttu-id="374ee-163">每個要求會執行一個 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="374ee-163">Each request performs an I/O operation.</span></span>  <span data-ttu-id="374ee-164">「未使用」非同步程式碼的伺服器必須等到 5 個執行緒的其中一個已完成 I/O-bound 工作並寫入回應，才能將第 6 個要求排入佇列。</span><span class="sxs-lookup"><span data-stu-id="374ee-164">The server *without* async code has to queue up the 6th request until one of the 5 threads have finished the I/O-bound work and written a response.</span></span> <span data-ttu-id="374ee-165">排到第 20 個要求時，由於佇列變得太長，因此伺服器可能會開始變慢。</span><span class="sxs-lookup"><span data-stu-id="374ee-165">At the point that the 20th request comes in, the server might start to slow down, because the queue is getting too long.</span></span>

<span data-ttu-id="374ee-166">在其上「執行」非同步程式碼的伺服器仍可將第 6 個要求排入佇列，但因為它使用 `async` 和 `await`，所以當 I/O-bound 工作開始時 (而不是完成時)，將會釋放其所包含的每個執行緒。</span><span class="sxs-lookup"><span data-stu-id="374ee-166">The server *with* async code running on it still queues up the 6th request, but because it uses `async` and `await`, each of its threads are freed up when the I/O-bound work starts, rather than when it finishes.</span></span>  <span data-ttu-id="374ee-167">排到第 20 個要求時，傳入要求的佇列會很小 (如果有任何內容)，而且伺服器不會變慢。</span><span class="sxs-lookup"><span data-stu-id="374ee-167">By the time the 20th request comes in, the queue for incoming requests will be far smaller (if it has anything in it at all), and the server won't slow down.</span></span>

<span data-ttu-id="374ee-168">雖然這是虛擬範例，但其運作方式與真實世界非常類似。</span><span class="sxs-lookup"><span data-stu-id="374ee-168">Although this is a contrived example, it works in a very similar fashion in the real world.</span></span>  <span data-ttu-id="374ee-169">事實上，您可以預期伺服器使用 `async` 和 `await` 時，會比針對所收到的每個要求設定專用執行緒，能夠處理更大量的要求。</span><span class="sxs-lookup"><span data-stu-id="374ee-169">In fact, you can expect a server to be able to handle an order of magnitude more requests using `async` and `await` than if it were dedicating a thread for each request it receives.</span></span>

### <a name="what-does-this-mean-for-client-scenario"></a><span data-ttu-id="374ee-170">這對用戶端案例有何意義？</span><span class="sxs-lookup"><span data-stu-id="374ee-170">What does this mean for client scenario?</span></span>

<span data-ttu-id="374ee-171">針對用戶端應用程式使用 `async` 和 `await` 的最大好處在於加快回應速度。</span><span class="sxs-lookup"><span data-stu-id="374ee-171">The biggest gain for using `async` and `await` for a client app is an increase in responsiveness.</span></span>  <span data-ttu-id="374ee-172">雖然您可以透過手動繁衍執行緒來加快應用程式的回應速度，但相對於只使用 `async` 和 `await`，繁衍執行緒的做法是高度耗費資源的作業。</span><span class="sxs-lookup"><span data-stu-id="374ee-172">Although you can make an app responsive by spawning threads manually, the act of spawning a thread is an expensive operation relative to just using `async` and `await`.</span></span>  <span data-ttu-id="374ee-173">特別是針對重視 I/O 的項目 (例如行動遊戲)，請務必盡可能將 UI 執行緒的影響降到最低。</span><span class="sxs-lookup"><span data-stu-id="374ee-173">Especially for something like a mobile game, impacting the UI thread as little as possible where I/O is concerned is crucial.</span></span>

<span data-ttu-id="374ee-174">更重要的是，因為 I/O-bound 工作在 CPU 上花費的時間幾乎為零，所以讓整個 CPU 執行緒只用來執行極少的任何有用工作，並無法有效利用資源。</span><span class="sxs-lookup"><span data-stu-id="374ee-174">More importantly, because I/O-bound work spends virtually no time on the CPU, dedicating an entire CPU thread to perform barely any useful work would be a poor use of resources.</span></span>

<span data-ttu-id="374ee-175">此外，使用 `async` 方法可輕鬆地將工作分派給 UI 執行緒 (例如更新 UI)，而且不需要額外的工作 (例如呼叫安全執行緒委派)。</span><span class="sxs-lookup"><span data-stu-id="374ee-175">Additionally, dispatching work to the UI thread (such as updating a UI) is very simple with `async` methods, and does not require extra work (such as calling a thread-safe delegate).</span></span>

## <a name="deeper-dive-into-task-and-tasklttgt-for-a-cpu-bound-operation"></a><span data-ttu-id="374ee-176">更深入了解 CPU-Bound 作業的 Task 和 Task&lt;T&gt;</span><span class="sxs-lookup"><span data-stu-id="374ee-176">Deeper Dive into Task and Task&lt;T&gt; for a CPU-Bound Operation</span></span>

<span data-ttu-id="374ee-177">CPU-bound `async` 程式碼與 I/O-bound `async` 程式碼稍微不同。</span><span class="sxs-lookup"><span data-stu-id="374ee-177">CPU-bound `async` code is a bit different than I/O-bound `async` code.</span></span>  <span data-ttu-id="374ee-178">由於工作會在 CPU 上執行，因此必須指定專門用於計算的執行緒。</span><span class="sxs-lookup"><span data-stu-id="374ee-178">Because the work is done on the CPU, there's no way to get around dedicating a thread to the computation.</span></span>  <span data-ttu-id="374ee-179">使用 `async` 和 `await` 可讓您無障礙地與背景執行緒互動，並確保非同步方法的呼叫端保持回應。</span><span class="sxs-lookup"><span data-stu-id="374ee-179">The use of `async` and `await` provides you with a clean way to interact with a background thread and keep the caller of the async method responsive.</span></span>  <span data-ttu-id="374ee-180">請注意，這不會對共用資料提供任何保護。</span><span class="sxs-lookup"><span data-stu-id="374ee-180">Note that this does not provide any protection for shared data.</span></span>  <span data-ttu-id="374ee-181">如果您要使用共用資料，您仍然需要套用適當的同步處理策略。</span><span class="sxs-lookup"><span data-stu-id="374ee-181">If you are using shared data, you will still need to apply an appropriate synchronization strategy.</span></span>

<span data-ttu-id="374ee-182">CPU-bound 非同步呼叫的概觀如下：</span><span class="sxs-lookup"><span data-stu-id="374ee-182">Here's a 10,000 foot view of a CPU-bound async call:</span></span>

```csharp
public async Task<int> CalculateResult(InputData data)
{
    // This queues up the work on the threadpool.
    var expensiveResultTask = Task.Run(() => DoExpensiveCalculation(data));
    
    // Note that at this point, you can do some other work concurrently,
    // as CalculateResult() is still executing!
    
    // Execution of CalculateResult is yielded here!
    var result = await expensiveResultTask;
    
    return result;
}
```

<span data-ttu-id="374ee-183">`CalculateResult()` 會對所呼叫的執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="374ee-183">`CalculateResult()` executes on the thread it was called on.</span></span>  <span data-ttu-id="374ee-184">當它呼叫 `Task.Run` 時，它會將執行緒集區上高度耗費資源的 CPU-bound 作業 `DoExpensiveCalculation()` 排入佇列，並收到 `Task<int>` 控制代碼。</span><span class="sxs-lookup"><span data-stu-id="374ee-184">When it calls `Task.Run`, it queues the expensive CPU-bound operation, `DoExpensiveCalculation()`, on the thread pool and receives a `Task<int>` handle.</span></span>  <span data-ttu-id="374ee-185">`DoExpensiveCalculation()` 最終會對下一個可用的執行緒 (可能位於另一個 CPU 核心) 同時執行。</span><span class="sxs-lookup"><span data-stu-id="374ee-185">`DoExpensiveCalculation()` is eventually run concurrently on the next available thread, likely on another CPU core.</span></span>  <span data-ttu-id="374ee-186">您可以在另一個執行緒上的 `DoExpensiveCalculation()` 忙碌時，同時執行工作，因為稱為 `CalculateResult()` 的執行緒仍在執行中。</span><span class="sxs-lookup"><span data-stu-id="374ee-186">It's possible to do concurrent work while `DoExpensiveCalculation()` is busy on another thread, because the thread which called `CalculateResult()` is still executing.</span></span>

<span data-ttu-id="374ee-187">遇到 `await` 之後，`CalculateResult()` 的執行會轉讓給呼叫端，以允許其他工作可在 `DoExpensiveCalculation()` 大量產生結果同時，使用目前的執行緒來執行。</span><span class="sxs-lookup"><span data-stu-id="374ee-187">Once `await` is encountered, the execution of `CalculateResult()` is yielded to its caller, allowing other work to be done with the current thread while `DoExpensiveCalculation()` is churning out a result.</span></span>  <span data-ttu-id="374ee-188">完成後，結果會排入佇列，等候在主執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="374ee-188">Once it has finished, the result is queued up to run on the main thread.</span></span>  <span data-ttu-id="374ee-189">最後，主執行緒會返回正在執行的 `CalculateResult()`，此時它會有 `DoExpensiveCalculation()` 的結果。</span><span class="sxs-lookup"><span data-stu-id="374ee-189">Eventually, the main thread will return to executing `CalculateResult()`, at which point it will have the result of `DoExpensiveCalculation()`.</span></span>

### <a name="why-does-async-help-here"></a><span data-ttu-id="374ee-190">為什麼非同步有助於此作業？</span><span class="sxs-lookup"><span data-stu-id="374ee-190">Why does async help here?</span></span>

<span data-ttu-id="374ee-191">當您需要快速回應，`async` 與 `await` 是管理 CPU-bound 工作的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="374ee-191">`async` and `await` are the best practice managing CPU-bound work when you need responsiveness.</span></span> <span data-ttu-id="374ee-192">搭配 CPU-bound 工作使用 async 的模式有許多種。</span><span class="sxs-lookup"><span data-stu-id="374ee-192">There are multiple patterns for using async with CPU-bound work.</span></span> <span data-ttu-id="374ee-193">請務必注意使用 async 會耗費少量成本，而且不建議用於緊密迴圈。</span><span class="sxs-lookup"><span data-stu-id="374ee-193">It's important to note that there is a small cost to using async and it's not recommended for tight loops.</span></span>  <span data-ttu-id="374ee-194">您必須自行決定要如何撰寫以這項新功能為主的程式碼。</span><span class="sxs-lookup"><span data-stu-id="374ee-194">It's up to you to determine how you write your code around this new capability.</span></span>

## <a name="see-also"></a><span data-ttu-id="374ee-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="374ee-195">See also</span></span>

* [<span data-ttu-id="374ee-196">C# 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="374ee-196">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)   
* [<span data-ttu-id="374ee-197">使用 async 和 await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="374ee-197">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)  
* [<span data-ttu-id="374ee-198">F# 中的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="374ee-198">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
* [<span data-ttu-id="374ee-199">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="374ee-199">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
