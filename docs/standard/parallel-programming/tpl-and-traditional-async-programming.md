---
title: TPL 和傳統 .NET 非同步程式設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
ms.openlocfilehash: 498bde82d05259bdc561d08819d024090b0417f0
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92688016"
---
# <a name="tpl-and-traditional-net-asynchronous-programming"></a><span data-ttu-id="1b097-102">TPL 和傳統 .NET 非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="1b097-102">TPL and traditional .NET asynchronous programming</span></span>

<span data-ttu-id="1b097-103">.NET 提供下列兩個標準模式來執行 i/o 系結和計算系結的非同步作業：</span><span class="sxs-lookup"><span data-stu-id="1b097-103">.NET provides the following two standard patterns for performing I/O-bound and compute-bound asynchronous operations:</span></span>  
  
- <span data-ttu-id="1b097-104">非同步程式設計模型 (APM) ，其中非同步作業會以一對 begin/end 方法來表示。</span><span class="sxs-lookup"><span data-stu-id="1b097-104">Asynchronous Programming Model (APM), in which asynchronous operations are represented by a pair of begin/end methods.</span></span> <span data-ttu-id="1b097-105">例如：<xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1b097-105">For example: <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="1b097-106">以事件為基礎的非同步模式 (EAP) ，其中非同步作業是以名為和的方法/事件組來表示 `<OperationName>Async` `<OperationName>Completed` 。</span><span class="sxs-lookup"><span data-stu-id="1b097-106">Event-based asynchronous pattern (EAP), in which asynchronous operations are represented by a method/event pair that are named `<OperationName>Async` and `<OperationName>Completed`.</span></span> <span data-ttu-id="1b097-107">例如：<xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="1b097-107">For example: <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> and <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>.</span></span>
  
<span data-ttu-id="1b097-108">工作平行程式庫 (TPL) 可以用各種方式搭配非同步模式的其中一種。</span><span class="sxs-lookup"><span data-stu-id="1b097-108">The Task Parallel Library (TPL) can be used in various ways in conjunction with either of the asynchronous patterns.</span></span> <span data-ttu-id="1b097-109">您可以將 APM 和 EAP 作業公開為連結 `Task` 庫取用者的物件，也可以公開 apm 模式，但使用 `Task` 物件在內部執行。</span><span class="sxs-lookup"><span data-stu-id="1b097-109">You can expose both APM and EAP operations as `Task` objects to library consumers, or you can expose the APM patterns but use `Task` objects to implement them internally.</span></span> <span data-ttu-id="1b097-110">在這兩種情況下，藉由使用 `Task` 物件，您可以簡化程式碼，並利用下列有用的功能：</span><span class="sxs-lookup"><span data-stu-id="1b097-110">In both scenarios, by using `Task` objects, you can simplify the code and take advantage of the following useful functionality:</span></span>  
  
- <span data-ttu-id="1b097-111">在啟動工作的任何時間之後，註冊工作接續形式的回呼。</span><span class="sxs-lookup"><span data-stu-id="1b097-111">Register callbacks, in the form of task continuations, at any time after the task has started.</span></span>  
  
- <span data-ttu-id="1b097-112">使用和方法來協調執行的多個作業，以回應 `Begin_` 方法 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> ，或是 <xref:System.Threading.Tasks.Task.WaitAll%2A> 和 <xref:System.Threading.Tasks.Task.WaitAny%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1b097-112">Coordinate multiple operations that execute in response to a `Begin_` method by using the <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> and <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> methods, or the <xref:System.Threading.Tasks.Task.WaitAll%2A> and <xref:System.Threading.Tasks.Task.WaitAny%2A> methods.</span></span>  
  
- <span data-ttu-id="1b097-113">封裝相同物件中的非同步 i/o 系結和計算系結作業 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="1b097-113">Encapsulate asynchronous I/O-bound and compute-bound operations in the same `Task` object.</span></span>  
  
- <span data-ttu-id="1b097-114">監視物件的狀態 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="1b097-114">Monitor the status of the `Task` object.</span></span>  
  
- <span data-ttu-id="1b097-115">使用將作業的狀態封送處理至 `Task` 物件 <xref:System.Threading.Tasks.TaskCompletionSource%601> 。</span><span class="sxs-lookup"><span data-stu-id="1b097-115">Marshal the status of an operation to a `Task` object by using <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span>  
  
## <a name="wrap-apm-operations-in-a-task"></a><span data-ttu-id="1b097-116">將 APM 作業包裝在工作中</span><span class="sxs-lookup"><span data-stu-id="1b097-116">Wrap APM operations in a Task</span></span>  

 <span data-ttu-id="1b097-117"><xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>和 <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> 類別提供數個多載的 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> 方法，可讓您在一個或多個實例中封裝 APM begin/end 方法組 <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="1b097-117">Both the <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> and <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> classes provide several overloads of the <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> methods that let you encapsulate an APM begin/end method pair in one <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> instance.</span></span> <span data-ttu-id="1b097-118">不同的多載會容納具有零至三個輸入參數的任何 begin/end 方法組。</span><span class="sxs-lookup"><span data-stu-id="1b097-118">The various overloads accommodate any begin/end method pair that have from zero to three input parameters.</span></span>  
  
 <span data-ttu-id="1b097-119">對於具有傳回 `End` 值 (Visual Basic) 中之方法的配對 `Function` ，請使用中的方法 <xref:System.Threading.Tasks.TaskFactory%601> 來建立 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="1b097-119">For pairs that have `End` methods that return a value (a `Function` in Visual Basic), use the methods in <xref:System.Threading.Tasks.TaskFactory%601> that create a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1b097-120">針對傳回 `End` void (`Sub` 中 Visual Basic) 的方法，請使用中的方法 <xref:System.Threading.Tasks.TaskFactory> 來建立 <xref:System.Threading.Tasks.Task> 。</span><span class="sxs-lookup"><span data-stu-id="1b097-120">For `End` methods that return void (a `Sub` in Visual Basic), use the methods in <xref:System.Threading.Tasks.TaskFactory> that create a <xref:System.Threading.Tasks.Task>.</span></span>  
  
 <span data-ttu-id="1b097-121">在 `Begin` 方法有三個以上的參數，或是包含 `ref` 或 `out` 參數的少數情況下，會提供其他僅封裝 `End` 方法的 `FromAsync` 多載。</span><span class="sxs-lookup"><span data-stu-id="1b097-121">For those few cases in which the `Begin` method has more than three parameters or contains `ref` or `out` parameters, additional `FromAsync` overloads that encapsulate only the `End` method are provided.</span></span>  
  
 <span data-ttu-id="1b097-122">下列範例示範 `FromAsync` 多載的簽章，該多載會比對 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1b097-122">The following example shows the signature for the `FromAsync` overload that matches the <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> methods.</span></span>
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
<span data-ttu-id="1b097-123">這個多載會採用三個輸入參數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="1b097-123">This overload takes three input parameters, as follows.</span></span> <span data-ttu-id="1b097-124">第一個參數是 <xref:System.Func%606> 委派，這與 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法的簽章相符。</span><span class="sxs-lookup"><span data-stu-id="1b097-124">The first parameter is a <xref:System.Func%606> delegate that matches the signature of the <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1b097-125">第二個參數是 <xref:System.Func%602> 委派，會取得 <xref:System.IAsyncResult> 並傳回 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="1b097-125">The second parameter is a <xref:System.Func%602> delegate that takes an <xref:System.IAsyncResult> and returns a `TResult`.</span></span> <span data-ttu-id="1b097-126">因為 <xref:System.IO.FileStream.EndRead%2A> 會傳回整數，所以編譯器會推斷 `TResult` 的類型為 <xref:System.Int32>，並且推斷工作的類型為 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="1b097-126">Because <xref:System.IO.FileStream.EndRead%2A> returns an integer, the compiler infers the type of `TResult` as <xref:System.Int32> and the type of the task as <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="1b097-127">最後四個參數和在 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法中的相同：</span><span class="sxs-lookup"><span data-stu-id="1b097-127">The last four parameters are identical to those in the <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> method:</span></span>  
  
- <span data-ttu-id="1b097-128">用來儲存檔案資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1b097-128">The buffer in which to store the file data.</span></span>  
  
- <span data-ttu-id="1b097-129">開始寫入資料的緩衝區之位移。</span><span class="sxs-lookup"><span data-stu-id="1b097-129">The offset in the buffer at which to begin writing data.</span></span>  
  
- <span data-ttu-id="1b097-130">從檔案讀取的資料數量上限。</span><span class="sxs-lookup"><span data-stu-id="1b097-130">The maximum amount of data to read from the file.</span></span>  
  
- <span data-ttu-id="1b097-131">選擇性的物件，其中儲存要傳遞至回呼的使用者定義狀態資料。</span><span class="sxs-lookup"><span data-stu-id="1b097-131">An optional object that stores user-defined state data to pass to the callback.</span></span>  
  
### <a name="use-continuewith-for-the-callback-functionality"></a><span data-ttu-id="1b097-132">使用 System.threading.tasks.task.continuewith 作為回呼功能</span><span class="sxs-lookup"><span data-stu-id="1b097-132">Use ContinueWith for the callback functionality</span></span>

 <span data-ttu-id="1b097-133">如果您需要在檔案中資料的存取權，而不只是需要位元組數，則 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法仍不足夠。</span><span class="sxs-lookup"><span data-stu-id="1b097-133">If you require access to the data in the file, as opposed to just the number of bytes, the <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method is not sufficient.</span></span> <span data-ttu-id="1b097-134">請改用 <xref:System.Threading.Tasks.Task>，其 `Result` 屬性包含檔案資料。</span><span class="sxs-lookup"><span data-stu-id="1b097-134">Instead, use <xref:System.Threading.Tasks.Task>, whose `Result` property contains the file data.</span></span> <span data-ttu-id="1b097-135">您可將接續加入原始工作來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="1b097-135">You can do this by adding a continuation to the original task.</span></span> <span data-ttu-id="1b097-136">接續會執行通常由 <xref:System.AsyncCallback> 委派所執行的工作。</span><span class="sxs-lookup"><span data-stu-id="1b097-136">The continuation performs the work that would typically be performed by the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="1b097-137">當前項完成，而且資料緩衝區已滿時，則會叫用它。</span><span class="sxs-lookup"><span data-stu-id="1b097-137">It is invoked when the antecedent completes, and the data buffer has been filled.</span></span> <span data-ttu-id="1b097-138">(<xref:System.IO.FileStream> 物件應該在傳回之前關閉。)</span><span class="sxs-lookup"><span data-stu-id="1b097-138">(The <xref:System.IO.FileStream> object should be closed before returning.)</span></span>  
  
 <span data-ttu-id="1b097-139">下列範例顯示如何傳回 <xref:System.Threading.Tasks.Task> 封裝 `BeginRead` / `EndRead` 類別配對的 <xref:System.IO.FileStream> 。</span><span class="sxs-lookup"><span data-stu-id="1b097-139">The following example shows how to return a <xref:System.Threading.Tasks.Task> that encapsulates the `BeginRead`/`EndRead` pair of the <xref:System.IO.FileStream> class.</span></span>  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 <span data-ttu-id="1b097-140">然後可以呼叫此方法，如下所示。</span><span class="sxs-lookup"><span data-stu-id="1b097-140">The method can then be called, as follows.</span></span>  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="provide-custom-state-data"></a><span data-ttu-id="1b097-141">提供自訂狀態資料</span><span class="sxs-lookup"><span data-stu-id="1b097-141">Provide custom state data</span></span>

 <span data-ttu-id="1b097-142">在一般 <xref:System.IAsyncResult> 作業中，如果您的 <xref:System.AsyncCallback> 委派需要一些自訂狀態資料，則您必須透過 `Begin` 方法中的最後一個參數傳遞它，以便資料可以封裝到 <xref:System.IAsyncResult> 物件，而該物件最終會傳遞至回呼方法。</span><span class="sxs-lookup"><span data-stu-id="1b097-142">In typical <xref:System.IAsyncResult> operations, if your <xref:System.AsyncCallback> delegate requires some custom state data, you have to pass it in through the last parameter in the `Begin` method, so that the data can be packaged into the <xref:System.IAsyncResult> object that is eventually passed to the callback method.</span></span> <span data-ttu-id="1b097-143">當使用 `FromAsync` 方法時，這通常不必要。</span><span class="sxs-lookup"><span data-stu-id="1b097-143">This is typically not required when the `FromAsync` methods are used.</span></span> <span data-ttu-id="1b097-144">如果自訂資料對接續為已知，則可以直接在接續委派中擷取。</span><span class="sxs-lookup"><span data-stu-id="1b097-144">If the custom data is known to the continuation, then it can be captured directly in the continuation delegate.</span></span> <span data-ttu-id="1b097-145">下列範例類似上述範例，但不檢查前項的 `Result` 屬性，接續會檢查自訂狀態資料，此為接續的使用者委派所直接存取。</span><span class="sxs-lookup"><span data-stu-id="1b097-145">The following example resembles the previous example, but instead of examining the `Result` property of the antecedent, the continuation examines the custom state data that is directly accessible to the user delegate of the continuation.</span></span>  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronize-multiple-fromasync-tasks"></a><span data-ttu-id="1b097-146">同步處理多個 System.threading.tasks.taskfactory.fromasync 工作</span><span class="sxs-lookup"><span data-stu-id="1b097-146">Synchronize multiple FromAsync tasks</span></span>

 <span data-ttu-id="1b097-147">當搭配 `FromAsync` 方法使用時，靜態 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法會提供額外的彈性。</span><span class="sxs-lookup"><span data-stu-id="1b097-147">The static <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> and <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> methods provide added flexibility when used in conjunction with the `FromAsync` methods.</span></span> <span data-ttu-id="1b097-148">下列範例示範如何初始化多個非同步 I/O 作業，然後等候它們全部完成，才執行接續。</span><span class="sxs-lookup"><span data-stu-id="1b097-148">The following example shows how to initiate multiple asynchronous I/O operations, and then wait for all of them to complete before you execute the continuation.</span></span>  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a><span data-ttu-id="1b097-149">僅 System.threading.tasks.taskfactory.fromasync End 方法的工作</span><span class="sxs-lookup"><span data-stu-id="1b097-149">FromAsync tasks for only the End method</span></span>

 <span data-ttu-id="1b097-150">在 `Begin` 方法需要三個以上的輸入參數或具有或參數的少數情況下， `ref` `out` 您可以使用多載 `FromAsync` ，例如， <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType> 只代表 `End` 方法。</span><span class="sxs-lookup"><span data-stu-id="1b097-150">For those few cases in which the `Begin` method requires more than three input parameters or has `ref` or `out` parameters, you can use the `FromAsync` overloads, for example, <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, that represent only the `End` method.</span></span> <span data-ttu-id="1b097-151">這些方法也可以在您傳遞的任何案例中使用 <xref:System.IAsyncResult> ，而且想要將它封裝在工作中。</span><span class="sxs-lookup"><span data-stu-id="1b097-151">These methods can also be used in any scenario in which you're passed an <xref:System.IAsyncResult> and want to encapsulate it in a Task.</span></span>  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="start-and-cancel-fromasync-tasks"></a><span data-ttu-id="1b097-152">啟動和取消 System.threading.tasks.taskfactory.fromasync 工作</span><span class="sxs-lookup"><span data-stu-id="1b097-152">Start and cancel FromAsync tasks</span></span>

 <span data-ttu-id="1b097-153">方法所傳回的工作 `FromAsync` 具有的狀態 `WaitingForActivation` ，並且會在工作建立之後的某個時間點啟動系統。</span><span class="sxs-lookup"><span data-stu-id="1b097-153">The task returned by a `FromAsync` method has a status of `WaitingForActivation` and will be started by the system at some point after the task is created.</span></span> <span data-ttu-id="1b097-154">如果您嘗試呼叫這類工作上的 Start，就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1b097-154">If you attempt to call Start on such a task, an exception will be raised.</span></span>  
  
 <span data-ttu-id="1b097-155">`FromAsync`因為基礎 .Net api 目前不支援檔案或網路 i/o 的進行中取消，所以無法取消工作。</span><span class="sxs-lookup"><span data-stu-id="1b097-155">You cannot cancel a `FromAsync` task, because the underlying .NET APIs currently do not support in-progress cancellation of file or network I/O.</span></span> <span data-ttu-id="1b097-156">您可以加入取消功能到封裝 `FromAsync` 呼叫的方法，但是您只可以在 `FromAsync` 呼叫之前或完成之後回應取消 (例如在接續工作中)。</span><span class="sxs-lookup"><span data-stu-id="1b097-156">You can add cancellation functionality to a method that encapsulates a `FromAsync` call, but you can only respond to the cancellation before `FromAsync` is called or after it completed (for example, in a continuation task).</span></span>  
  
 <span data-ttu-id="1b097-157">有些類別支援 EAP，例如 <xref:System.Net.WebClient> 支援取消，您可以使用取消語彙基元整合該原生的取消功能。</span><span class="sxs-lookup"><span data-stu-id="1b097-157">Some classes that support EAP, for example, <xref:System.Net.WebClient>, do support cancellation, and you can integrate that native cancellation functionality by using cancellation tokens.</span></span>  
  
## <a name="expose-complex-eap-operations-as-tasks"></a><span data-ttu-id="1b097-158">將複雜的 EAP 作業公開為工作</span><span class="sxs-lookup"><span data-stu-id="1b097-158">Expose complex EAP operations As tasks</span></span>

 <span data-ttu-id="1b097-159">TPL 不提供任何專門用來封裝事件架構非同步作業的方法，和 `FromAsync` 系列方法包裝 <xref:System.IAsyncResult> 模式的方式相同。</span><span class="sxs-lookup"><span data-stu-id="1b097-159">The TPL does not provide any methods that are specifically designed to encapsulate an event-based asynchronous operation in the same way that the `FromAsync` family of methods wrap the <xref:System.IAsyncResult> pattern.</span></span> <span data-ttu-id="1b097-160">但是，TPL 並不提供 <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> 類別，這可用來代表任意一組作業為 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="1b097-160">However, the TPL does provide the <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> class, which can be used to represent any arbitrary set of operations as a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1b097-161">此作業可能為同步或非同步，而且可能為 I/O 繫結或計算繫結，或兩者兼具。</span><span class="sxs-lookup"><span data-stu-id="1b097-161">The operations may be synchronous or asynchronous, and may be I/O bound or compute-bound, or both.</span></span>  
  
 <span data-ttu-id="1b097-162">下列範例示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>來公開一組非同步 <xref:System.Net.WebClient> 作業給用戶端程式碼做為基本的 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="1b097-162">The following example shows how to use a <xref:System.Threading.Tasks.TaskCompletionSource%601> to expose a set of asynchronous <xref:System.Net.WebClient> operations to client code as a basic <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1b097-163">此方法可讓您輸入 Web URL 和要搜尋的詞彙或名稱之陣列，然後傳回在每個網站出現搜尋詞彙的次數。</span><span class="sxs-lookup"><span data-stu-id="1b097-163">The method lets you enter an array of Web URLs, and a term or name to search for, and then returns the number of times the search term occurs on each site.</span></span>  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 <span data-ttu-id="1b097-164">如需更完整的範例，其中包含其他例外狀況處理，並示範如何從用戶端程式碼呼叫方法，請參閱[如何：將 EAP 模式包裝在工作中](how-to-wrap-eap-patterns-in-a-task.md)。</span><span class="sxs-lookup"><span data-stu-id="1b097-164">For a more complete example, which includes additional exception handling and shows how to call the method from client code, see [How to: Wrap EAP Patterns in a Task](how-to-wrap-eap-patterns-in-a-task.md).</span></span>  
  
 <span data-ttu-id="1b097-165">請記住，由所建立的任何工作 <xref:System.Threading.Tasks.TaskCompletionSource%601> 都會由該啟動， `TaskCompletionSource` 因此，使用者程式碼不應該 `Start` 在該工作上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1b097-165">Remember that any task that's created by a <xref:System.Threading.Tasks.TaskCompletionSource%601> will be started by that `TaskCompletionSource` and, therefore, user code should not call the `Start` method on that task.</span></span>  
  
## <a name="implement-the-apm-pattern-by-using-tasks"></a><span data-ttu-id="1b097-166">使用工作來執行 APM 模式</span><span class="sxs-lookup"><span data-stu-id="1b097-166">Implement the APM pattern by using tasks</span></span>

 <span data-ttu-id="1b097-167">在某些情況下，您可能會想要 <xref:System.IAsyncResult> 在 API 中使用 begin/end 方法組來直接公開模式。</span><span class="sxs-lookup"><span data-stu-id="1b097-167">In some scenarios, it may be desirable to directly expose the <xref:System.IAsyncResult> pattern by using begin/end method pairs in an API.</span></span> <span data-ttu-id="1b097-168">例如，您可能想要維護現有 API 的一致性，或者您想要有需要此模式的自動化工具。</span><span class="sxs-lookup"><span data-stu-id="1b097-168">For example, you may want to maintain consistency with existing APIs, or you may have automated tools that require this pattern.</span></span> <span data-ttu-id="1b097-169">在這種情況下，您可以使用 `Task` 物件來簡化 APM 模式在內部的內部執行方式。</span><span class="sxs-lookup"><span data-stu-id="1b097-169">In such cases, you can use `Task` objects to simplify how the APM pattern is implemented internally.</span></span>  
  
 <span data-ttu-id="1b097-170">下列範例示範如何使用工作，針對長時間執行的計算系結方法，執行 APM begin/end 方法組。</span><span class="sxs-lookup"><span data-stu-id="1b097-170">The following example shows how to use tasks to implement an APM begin/end method pair for a long-running compute-bound method.</span></span>  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="use-the-streamextensions-sample-code"></a><span data-ttu-id="1b097-171">使用 StreamExtensions 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="1b097-171">Use the StreamExtensions sample code</span></span>

 <span data-ttu-id="1b097-172">*StreamExtensions.cs* 檔案在 [.NET Standard 平行擴充功能額外](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/)存放庫中，包含數個使用 `Task` 物件進行非同步檔案和網路 i/o 的參考。</span><span class="sxs-lookup"><span data-stu-id="1b097-172">The *StreamExtensions.cs* file, in the [.NET Standard parallel extensions extras](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/) repository, contains several reference implementations that use `Task` objects for asynchronous file and network I/O.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1b097-173">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b097-173">See also</span></span>

- [<span data-ttu-id="1b097-174">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="1b097-174">Task Parallel Library (TPL)</span></span>](task-parallel-library-tpl.md)
