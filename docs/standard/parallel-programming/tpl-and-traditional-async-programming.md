---
title: TPL 和傳統 .NET Framework 非同步程式設計
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2acfb9a564f3a7bc96ed303f49349afe56ca7fe4
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a><span data-ttu-id="81fc8-102">TPL 和傳統 .NET Framework 非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="81fc8-102">TPL and Traditional .NET Framework Asynchronous Programming</span></span>
<span data-ttu-id="81fc8-103">.NET Framework 提供下列兩個標準模式執行 I/O 繫結程序和計算繫結程序的非同步作業：</span><span class="sxs-lookup"><span data-stu-id="81fc8-103">The .NET Framework provides the following two standard patterns for performing I/O-bound and compute-bound asynchronous operations:</span></span>  
  
-   <span data-ttu-id="81fc8-104">非同步程式設計模型 (APM)，在這個模式中非同步作業會以一對 Begin/End 方法表示，例如 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="81fc8-104">Asynchronous Programming Model (APM), in which asynchronous operations are represented by a pair of Begin/End methods such as <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="81fc8-105">事件式非同步模式 (EAP)，在這個模式中非同步作業會以一對名為 *OperationName*Async 和 *OperationName*Completed 的方法/事件組表示，例如 <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> 和 <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="81fc8-105">Event-based asynchronous pattern (EAP), in which asynchronous operations are represented by a method/event pair that are named *OperationName*Async and *OperationName*Completed, for example, <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> and <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>.</span></span> <span data-ttu-id="81fc8-106">(EAP 是在 .NET Framework 2.0 版中引入的。)</span><span class="sxs-lookup"><span data-stu-id="81fc8-106">(EAP was introduced in the .NET Framework version 2.0.)</span></span>  
  
 <span data-ttu-id="81fc8-107">工作平行程式庫 (TPL) 可以用各種方式搭配非同步模式的其中一種。</span><span class="sxs-lookup"><span data-stu-id="81fc8-107">The Task Parallel Library (TPL) can be used in various ways in conjunction with either of the asynchronous patterns.</span></span> <span data-ttu-id="81fc8-108">您可以將 APM 和 EAP 作業做為工作公開給程式庫的取用者，或公開 APM 模式，但使用工作物件在內部實作它們。</span><span class="sxs-lookup"><span data-stu-id="81fc8-108">You can expose both APM and EAP operations as Tasks to library consumers, or you can expose the APM patterns but use Task objects to implement them internally.</span></span> <span data-ttu-id="81fc8-109">在這兩種案例，您可以使用工作物件簡化程式碼，並利用下列好用的功能：</span><span class="sxs-lookup"><span data-stu-id="81fc8-109">In both scenarios, by using Task objects, you can simplify the code and take advantage of the following useful functionality:</span></span>  
  
-   <span data-ttu-id="81fc8-110">在啟動工作的任何時間之後，註冊工作接續形式的回呼。</span><span class="sxs-lookup"><span data-stu-id="81fc8-110">Register callbacks, in the form of task continuations, at any time after the task has started.</span></span>  
  
-   <span data-ttu-id="81fc8-111">使用 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法，或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法、<xref:System.Threading.Tasks.Task.WaitAny%2A> 方法協調多項為回應 `Begin_` 方法而執行的作業。</span><span class="sxs-lookup"><span data-stu-id="81fc8-111">Coordinate multiple operations that execute in response to a `Begin_` method, by using the <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> and <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> methods, or the <xref:System.Threading.Tasks.Task.WaitAll%2A> method or the <xref:System.Threading.Tasks.Task.WaitAny%2A> method.</span></span>  
  
-   <span data-ttu-id="81fc8-112">在相同工作物件中封裝非同步 I/O 繫結和計算繫結的作業。</span><span class="sxs-lookup"><span data-stu-id="81fc8-112">Encapsulate asynchronous I/O-bound and compute-bound operations in the same Task object.</span></span>  
  
-   <span data-ttu-id="81fc8-113">監視工作物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="81fc8-113">Monitor the status of the Task object.</span></span>  
  
-   <span data-ttu-id="81fc8-114">使用 <xref:System.Threading.Tasks.TaskCompletionSource%601> 封送處理作業狀態給工作物件。</span><span class="sxs-lookup"><span data-stu-id="81fc8-114">Marshal the status of an operation to a Task object by using <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span>  
  
## <a name="wrapping-apm-operations-in-a-task"></a><span data-ttu-id="81fc8-115">在工作中包裝 APM 作業</span><span class="sxs-lookup"><span data-stu-id="81fc8-115">Wrapping APM Operations in a Task</span></span>  
 <span data-ttu-id="81fc8-116"><xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> 類別都會提供數個 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> 方法的多載，可讓您封裝 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 執行個體的其中一種 APM Begin/End 方法組。</span><span class="sxs-lookup"><span data-stu-id="81fc8-116">Both the <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> and <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> classes provide several overloads of the <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> methods that let you encapsulate an APM Begin/End method pair in one <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> instance.</span></span> <span data-ttu-id="81fc8-117">這幾種多載會容納具有零到三個輸入參數的任何 Begin/End 方法組。</span><span class="sxs-lookup"><span data-stu-id="81fc8-117">The various overloads accommodate any Begin/End method pair that have from zero to three input parameters.</span></span>  
  
 <span data-ttu-id="81fc8-118">對於具有會傳回值的 `End` 方法組 (在 Visual Basic 中為 `Function`)，請使用會建立 <xref:System.Threading.Tasks.Task%601> 之 <xref:System.Threading.Tasks.TaskFactory%601> 中的方法。</span><span class="sxs-lookup"><span data-stu-id="81fc8-118">For pairs that have `End` methods that return a value (`Function` in Visual Basic), use the methods in <xref:System.Threading.Tasks.TaskFactory%601> that create a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="81fc8-119">對於會傳回 void 的 `End` 方法 (在 Visual Basic 中為 `Sub`)，請使用會建立 <xref:System.Threading.Tasks.Task> 之 <xref:System.Threading.Tasks.TaskFactory> 中的方法。</span><span class="sxs-lookup"><span data-stu-id="81fc8-119">For `End` methods that return void (`Sub` in Visual Basic), use the methods in <xref:System.Threading.Tasks.TaskFactory> that create a <xref:System.Threading.Tasks.Task>.</span></span>  
  
 <span data-ttu-id="81fc8-120">在 `Begin` 方法有三個以上的參數，或是包含 `ref` 或 `out` 參數的少數情況下，會提供其他僅封裝 `End` 方法的 `FromAsync` 多載。</span><span class="sxs-lookup"><span data-stu-id="81fc8-120">For those few cases in which the `Begin` method has more than three parameters or contains `ref` or `out` parameters, additional `FromAsync` overloads that encapsulate only the `End` method are provided.</span></span>  
  
 <span data-ttu-id="81fc8-121">下列範例示範 `FromAsync` 多載的簽章，該多載會比對 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 和 <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="81fc8-121">The following example shows the signature for the `FromAsync` overload that matches the <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="81fc8-122">這個多載會採用三個輸入參數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="81fc8-122">This overload takes three input parameters, as follows.</span></span>  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 <span data-ttu-id="81fc8-123">第一個參數是 <xref:System.Func%606> 委派，這與 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法的簽章相符。</span><span class="sxs-lookup"><span data-stu-id="81fc8-123">The first parameter is a <xref:System.Func%606> delegate that matches the signature of the <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="81fc8-124">第二個參數是 <xref:System.Func%602> 委派，會取得 <xref:System.IAsyncResult> 並傳回 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="81fc8-124">The second parameter is a <xref:System.Func%602> delegate that takes an <xref:System.IAsyncResult> and returns a `TResult`.</span></span> <span data-ttu-id="81fc8-125">因為 <xref:System.IO.FileStream.EndRead%2A> 會傳回整數，所以編譯器會推斷 `TResult` 的類型為 <xref:System.Int32>，並且推斷工作的類型為 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="81fc8-125">Because <xref:System.IO.FileStream.EndRead%2A> returns an integer, the compiler infers the type of `TResult` as <xref:System.Int32> and the type of the task as <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="81fc8-126">最後四個參數和在 <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> 方法中的相同：</span><span class="sxs-lookup"><span data-stu-id="81fc8-126">The last four parameters are identical to those in the <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> method:</span></span>  
  
-   <span data-ttu-id="81fc8-127">用來儲存檔案資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="81fc8-127">The buffer in which to store the file data.</span></span>  
  
-   <span data-ttu-id="81fc8-128">開始寫入資料的緩衝區之位移。</span><span class="sxs-lookup"><span data-stu-id="81fc8-128">The offset in the buffer at which to begin writing data.</span></span>  
  
-   <span data-ttu-id="81fc8-129">從檔案讀取的資料數量上限。</span><span class="sxs-lookup"><span data-stu-id="81fc8-129">The maximum amount of data to read from the file.</span></span>  
  
-   <span data-ttu-id="81fc8-130">選擇性的物件，其中儲存要傳遞至回呼的使用者定義狀態資料。</span><span class="sxs-lookup"><span data-stu-id="81fc8-130">An optional object that stores user-defined state data to pass to the callback.</span></span>  
  
### <a name="using-continuewith-for-the-callback-functionality"></a><span data-ttu-id="81fc8-131">對於回呼功能使用 ContinueWith</span><span class="sxs-lookup"><span data-stu-id="81fc8-131">Using ContinueWith for the Callback Functionality</span></span>  
 <span data-ttu-id="81fc8-132">如果您需要在檔案中資料的存取權，而不只是需要位元組數，則 <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> 方法仍不足夠。</span><span class="sxs-lookup"><span data-stu-id="81fc8-132">If you require access to the data in the file, as opposed to just the number of bytes, the <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method is not sufficient.</span></span> <span data-ttu-id="81fc8-133">請改用 <xref:System.Threading.Tasks.Task>，其 `Result` 屬性包含檔案資料。</span><span class="sxs-lookup"><span data-stu-id="81fc8-133">Instead, use <xref:System.Threading.Tasks.Task>, whose `Result` property contains the file data.</span></span> <span data-ttu-id="81fc8-134">您可將接續加入原始工作來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="81fc8-134">You can do this by adding a continuation to the original task.</span></span> <span data-ttu-id="81fc8-135">接續會執行通常由 <xref:System.AsyncCallback> 委派所執行的工作。</span><span class="sxs-lookup"><span data-stu-id="81fc8-135">The continuation performs the work that would typically be performed by the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="81fc8-136">當前項完成，而且資料緩衝區已滿時，則會叫用它。</span><span class="sxs-lookup"><span data-stu-id="81fc8-136">It is invoked when the antecedent completes, and the data buffer has been filled.</span></span> <span data-ttu-id="81fc8-137">(<xref:System.IO.FileStream> 物件應該在傳回之前關閉。)</span><span class="sxs-lookup"><span data-stu-id="81fc8-137">(The <xref:System.IO.FileStream> object should be closed before returning.)</span></span>  
  
 <span data-ttu-id="81fc8-138">下列範例示範如何傳回 <xref:System.Threading.Tasks.Task>，這會封裝 <xref:System.IO.FileStream> 類別的 BeginRead/EndRead 組。</span><span class="sxs-lookup"><span data-stu-id="81fc8-138">The following example shows how to return a <xref:System.Threading.Tasks.Task> that encapsulates the BeginRead/EndRead pair of the <xref:System.IO.FileStream> class.</span></span>  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 <span data-ttu-id="81fc8-139">然後可以呼叫此方法，如下所示。</span><span class="sxs-lookup"><span data-stu-id="81fc8-139">The method can then be called, as follows.</span></span>  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a><span data-ttu-id="81fc8-140">提供自訂狀態資料</span><span class="sxs-lookup"><span data-stu-id="81fc8-140">Providing Custom State Data</span></span>  
 <span data-ttu-id="81fc8-141">在一般 <xref:System.IAsyncResult> 作業中，如果您的 <xref:System.AsyncCallback> 委派需要一些自訂狀態資料，則您必須透過 `Begin` 方法中的最後一個參數傳遞它，以便資料可以封裝到 <xref:System.IAsyncResult> 物件，而該物件最終會傳遞至回呼方法。</span><span class="sxs-lookup"><span data-stu-id="81fc8-141">In typical <xref:System.IAsyncResult> operations, if your <xref:System.AsyncCallback> delegate requires some custom state data, you have to pass it in through the last parameter in the `Begin` method, so that the data can be packaged into the <xref:System.IAsyncResult> object that is eventually passed to the callback method.</span></span> <span data-ttu-id="81fc8-142">當使用 `FromAsync` 方法時，這通常不必要。</span><span class="sxs-lookup"><span data-stu-id="81fc8-142">This is typically not required when the `FromAsync` methods are used.</span></span> <span data-ttu-id="81fc8-143">如果自訂資料對接續為已知，則可以直接在接續委派中擷取。</span><span class="sxs-lookup"><span data-stu-id="81fc8-143">If the custom data is known to the continuation, then it can be captured directly in the continuation delegate.</span></span> <span data-ttu-id="81fc8-144">下列範例類似上述範例，但不檢查前項的 `Result` 屬性，接續會檢查自訂狀態資料，此為接續的使用者委派所直接存取。</span><span class="sxs-lookup"><span data-stu-id="81fc8-144">The following example resembles the previous example, but instead of examining the `Result` property of the antecedent, the continuation examines the custom state data that is directly accessible to the user delegate of the continuation.</span></span>  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a><span data-ttu-id="81fc8-145">同步處理多個 FromAsync 工作</span><span class="sxs-lookup"><span data-stu-id="81fc8-145">Synchronizing Multiple FromAsync Tasks</span></span>  
 <span data-ttu-id="81fc8-146">當搭配 `FromAsync` 方法使用時，靜態 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> 和 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> 方法會提供額外的彈性。</span><span class="sxs-lookup"><span data-stu-id="81fc8-146">The static <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> and <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> methods provide added flexibility when used in conjunction with the `FromAsync` methods.</span></span> <span data-ttu-id="81fc8-147">下列範例示範如何初始化多個非同步 I/O 作業，然後等候它們全部完成，才執行接續。</span><span class="sxs-lookup"><span data-stu-id="81fc8-147">The following example shows how to initiate multiple asynchronous I/O operations, and then wait for all of them to complete before you execute the continuation.</span></span>  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a><span data-ttu-id="81fc8-148">僅適用 End 方法的 FromAsync 工作</span><span class="sxs-lookup"><span data-stu-id="81fc8-148">FromAsync Tasks For Only the End Method</span></span>  
 <span data-ttu-id="81fc8-149">在 `Begin` 方法需要三個以上輸入參數，或是具有 `ref` 或 `out` 參數的少數情況下，您可以使用 `FromAsync` 多載，例如 <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>，這只會代表 `End` 方法。</span><span class="sxs-lookup"><span data-stu-id="81fc8-149">For those few cases in which the `Begin` method requires more than three input parameters, or has `ref` or `out` parameters, you can use the `FromAsync` overloads, for example, <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, that represent only the `End` method.</span></span> <span data-ttu-id="81fc8-150">這些方法也可用在當您傳遞 <xref:System.IAsyncResult> 且想要將它封裝在工作中的任何情況下。</span><span class="sxs-lookup"><span data-stu-id="81fc8-150">These methods can also be used in any scenario in which you are passed an <xref:System.IAsyncResult> and want to encapsulate it in a Task.</span></span>  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a><span data-ttu-id="81fc8-151">啟動及取消 FromAsync 工作</span><span class="sxs-lookup"><span data-stu-id="81fc8-151">Starting and Canceling FromAsync Tasks</span></span>  
 <span data-ttu-id="81fc8-152">`FromAsync` 方法所傳回的工作具有 WaitingForActivation 狀態，並且會在工作建立之後由系統在某個時間點啟動。</span><span class="sxs-lookup"><span data-stu-id="81fc8-152">The task returned by a `FromAsync` method has a status of WaitingForActivation and will be started by the system at some point after the task is created.</span></span> <span data-ttu-id="81fc8-153">如果您嘗試呼叫這類工作上的 Start，就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="81fc8-153">If you attempt to call Start on such a task, an exception will be raised.</span></span>  
  
 <span data-ttu-id="81fc8-154">您不能取消 `FromAsync` 工作，因為基礎 .NET Framework API 目前不支援檔案或網路 I/O 的進行中取消。</span><span class="sxs-lookup"><span data-stu-id="81fc8-154">You cannot cancel a `FromAsync` task, because the underlying .NET Framework APIs currently do not support in-progress cancellation of file or network I/O.</span></span> <span data-ttu-id="81fc8-155">您可以加入取消功能到封裝 `FromAsync` 呼叫的方法，但是您只可以在 `FromAsync` 呼叫之前或完成之後回應取消 (例如在接續工作中)。</span><span class="sxs-lookup"><span data-stu-id="81fc8-155">You can add cancellation functionality to a method that encapsulates a `FromAsync` call, but you can only respond to the cancellation before `FromAsync` is called or after it completed (for example, in a continuation task).</span></span>  
  
 <span data-ttu-id="81fc8-156">有些類別支援 EAP，例如 <xref:System.Net.WebClient> 支援取消，您可以使用取消語彙基元整合該原生的取消功能。</span><span class="sxs-lookup"><span data-stu-id="81fc8-156">Some classes that support EAP, for example, <xref:System.Net.WebClient>, do support cancellation, and you can integrate that native cancellation functionality by using cancellation tokens.</span></span>  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a><span data-ttu-id="81fc8-157">將複雜的 EAP 作業公開為工作</span><span class="sxs-lookup"><span data-stu-id="81fc8-157">Exposing Complex EAP Operations As Tasks</span></span>  
 <span data-ttu-id="81fc8-158">TPL 不提供任何專門用來封裝事件架構非同步作業的方法，和 `FromAsync` 系列方法包裝 <xref:System.IAsyncResult> 模式的方式相同。</span><span class="sxs-lookup"><span data-stu-id="81fc8-158">The TPL does not provide any methods that are specifically designed to encapsulate an event-based asynchronous operation in the same way that the `FromAsync` family of methods wrap the <xref:System.IAsyncResult> pattern.</span></span> <span data-ttu-id="81fc8-159">但是，TPL 並不提供 <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> 類別，這可用來代表任意一組作業為 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="81fc8-159">However, the TPL does provide the <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> class, which can be used to represent any arbitrary set of operations as a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="81fc8-160">此作業可能為同步或非同步，而且可能為 I/O 繫結或計算繫結，或兩者兼具。</span><span class="sxs-lookup"><span data-stu-id="81fc8-160">The operations may be synchronous or asynchronous, and may be I/O bound or compute-bound, or both.</span></span>  
  
 <span data-ttu-id="81fc8-161">下列範例示範如何使用 <xref:System.Threading.Tasks.TaskCompletionSource%601>來公開一組非同步 <xref:System.Net.WebClient> 作業給用戶端程式碼做為基本的 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="81fc8-161">The following example shows how to use a <xref:System.Threading.Tasks.TaskCompletionSource%601> to expose a set of asynchronous <xref:System.Net.WebClient> operations to client code as a basic <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="81fc8-162">此方法可讓您輸入 Web URL 和要搜尋的詞彙或名稱之陣列，然後傳回在每個網站出現搜尋詞彙的次數。</span><span class="sxs-lookup"><span data-stu-id="81fc8-162">The method lets you enter an array of Web URLs, and a term or name to search for, and then returns the number of times the search term occurs on each site.</span></span>  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 <span data-ttu-id="81fc8-163">如需更完整的範例，其中包含其他例外狀況處理，並示範如何從用戶端程式碼呼叫方法，請參閱[如何：將 EAP 模式包裝在工作中](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md)。</span><span class="sxs-lookup"><span data-stu-id="81fc8-163">For a more complete example, which includes additional exception handling and shows how to call the method from client code, see [How to: Wrap EAP Patterns in a Task](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).</span></span>  
  
 <span data-ttu-id="81fc8-164">請記住任何由 <xref:System.Threading.Tasks.TaskCompletionSource%601> 所建立的工作，都將由 TaskCompletionSource 啟動，因此使用者程式碼不應該在該工作上呼叫 Start 方法。</span><span class="sxs-lookup"><span data-stu-id="81fc8-164">Remember that any task that is created by a <xref:System.Threading.Tasks.TaskCompletionSource%601> will be started by that TaskCompletionSource and, therefore, user code should not call the Start method on that task.</span></span>  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a><span data-ttu-id="81fc8-165">使用工作來實作 APM 模式</span><span class="sxs-lookup"><span data-stu-id="81fc8-165">Implementing the APM Pattern By Using Tasks</span></span>  
 <span data-ttu-id="81fc8-166">在某些案例，可能會希望使用 API 中的 Begin/End 方法組來直接公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="81fc8-166">In some scenarios, it may be desirable to directly expose the <xref:System.IAsyncResult> pattern by using Begin/End method pairs in an API.</span></span> <span data-ttu-id="81fc8-167">例如，您可能想要維護現有 API 的一致性，或者您想要有需要此模式的自動化工具。</span><span class="sxs-lookup"><span data-stu-id="81fc8-167">For example, you may want to maintain consistency with existing APIs, or you may have automated tools that require this pattern.</span></span> <span data-ttu-id="81fc8-168">在這種情況下，您可以使用工作來簡化內部實作 APM 模式的方式。</span><span class="sxs-lookup"><span data-stu-id="81fc8-168">In such cases, you can use Tasks to simplify how the APM pattern is implemented internally.</span></span>  
  
 <span data-ttu-id="81fc8-169">對於長時間執行的計算繫結方法，下列範例示範如何使用工作來實作 APM Begin/End 方法組。</span><span class="sxs-lookup"><span data-stu-id="81fc8-169">The following example shows how to use tasks to implement an APM Begin/End method pair for a long-running compute-bound method.</span></span>  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a><span data-ttu-id="81fc8-170">使用 StreamExtensions 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="81fc8-170">Using the StreamExtensions Sample Code</span></span>  
 <span data-ttu-id="81fc8-171">[使用 .NET Framework 4 進行平行程式設計的範例](https://code.msdn.microsoft.com/ParExtSamples)中的 Streamextensions.cs 檔案包含數個參考實作，這些參考實作會使用 Task 物件來執行非同步檔案和網路 I/O。</span><span class="sxs-lookup"><span data-stu-id="81fc8-171">The Streamextensions.cs file, in [Samples for Parallel Programming with the .NET Framework 4](https://code.msdn.microsoft.com/ParExtSamples), contains several reference implementations that use Task objects for asynchronous file and network I/O.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fc8-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="81fc8-172">See Also</span></span>  
 [<span data-ttu-id="81fc8-173">工作平行程式庫 (TPL)</span><span class="sxs-lookup"><span data-stu-id="81fc8-173">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
