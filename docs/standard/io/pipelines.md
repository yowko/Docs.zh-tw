---
title: I/o 管線-.NET
description: 瞭解如何在 .NET 中有效率地使用 i/o 管線，並避免程式碼中發生問題。
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 9e26fb36b77e38c81273ccda370a203dd3388e5c
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291736"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="f2ca2-103">.NET 中的 system.object</span><span class="sxs-lookup"><span data-stu-id="f2ca2-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="f2ca2-104"><xref:System.IO.Pipelines> 是新的程式庫，其設計目的是為了讓您更輕鬆地在 .NET 中執行高效能的 i/o。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="f2ca2-105">它是以 .NET Standard 為目標的程式庫，其適用于所有的 .NET 部署。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="f2ca2-106">由 system.servicemodel 解決的問題</span><span class="sxs-lookup"><span data-stu-id="f2ca2-106">What problem does System.IO.Pipelines solve</span></span>
<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="f2ca2-107">剖析串流資料的應用程式是由具有許多特製化和異常程式碼流程的重複採用程式碼所組成。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="f2ca2-108">「未定案」和「特殊案例」程式碼很複雜且難以維護。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="f2ca2-109">`System.IO.Pipelines` 已架構為：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="f2ca2-110">具有高效能剖析串流資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="f2ca2-111">降低程式碼的複雜度。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-111">Reduce code complexity.</span></span>

<span data-ttu-id="f2ca2-112">下列程式碼通常用於從用戶端接收以行分隔的訊息（以 `'\n'` 分隔）的 TCP 伺服器：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);
    
    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="f2ca2-113">上述程式碼有幾個問題：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="f2ca2-114">在 `ReadAsync` 的單一呼叫中，可能不會收到整個訊息（結尾的那一行）。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="f2ca2-115">它會忽略 `stream.ReadAsync` 的結果。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="f2ca2-116">`stream.ReadAsync` 會傳回已讀取的資料量。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="f2ca2-117">它不會處理在單一 `ReadAsync` 呼叫中讀取多行的情況。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="f2ca2-118">它會在每次讀取時配置 @no__t 0 陣列。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="f2ca2-119">若要修正上述問題，需要進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="f2ca2-120">緩衝傳入的資料，直到找到新的一行為止。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="f2ca2-121">剖析緩衝區中傳回的所有行。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="f2ca2-122">這行程式碼可能大於 1 KB （1024個位元組）。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="f2ca2-123">程式碼必須調整輸入緩衝區的大小，才能找到整行。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-123">The code needs to resize the input buffer a complete line is found.</span></span>

  * <span data-ttu-id="f2ca2-124">如果調整緩衝區大小，則會在輸入中出現較長的行時，產生更多的緩衝區複本。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="f2ca2-125">若要減少浪費的空間，請壓縮用來讀取行的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="f2ca2-126">請考慮使用緩衝集區來避免重複配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="f2ca2-127">下列程式碼會解決其中一些問題：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-127">The following code address some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="f2ca2-128">先前的程式碼很複雜，而且無法解決所有已識別的問題。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="f2ca2-129">高效能的網路功能通常表示撰寫非常複雜的程式碼，以將效能最大化。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="f2ca2-130">`System.IO.Pipelines` 的設計可讓您更輕鬆地撰寫這種類型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

## <a name="pipe"></a><span data-ttu-id="f2ca2-131">管道</span><span class="sxs-lookup"><span data-stu-id="f2ca2-131">Pipe</span></span>

<span data-ttu-id="f2ca2-132">@No__t-0 類別可以用來建立 @no__t 1 的配對。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="f2ca2-133">寫入 `PipeWriter` 的所有資料都可在 `PipeReader` 中取得：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="f2ca2-134">管道基本使用方式</span><span class="sxs-lookup"><span data-stu-id="f2ca2-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="f2ca2-135">有兩個迴圈：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-135">There are two loops:</span></span>

* <span data-ttu-id="f2ca2-136">`FillPipeAsync` 會從 `Socket` 讀取，並寫入至 `PipeWriter`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="f2ca2-137">`ReadPipeAsync` 會從 `PipeReader` 讀取並剖析傳入的行。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="f2ca2-138">未配置明確的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="f2ca2-139">系統會將所有緩衝區管理委派給 `PipeReader` 和 @no__t 1 的執行。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="f2ca2-140">委派緩衝區管理可讓您更輕鬆地使用程式碼，只著重于商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="f2ca2-141">在第一個迴圈中：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-141">In the first loop:</span></span>

* <span data-ttu-id="f2ca2-142">呼叫 <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>，以從基礎寫入器取得記憶體。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="f2ca2-143">呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>，告訴 `PipeWriter` 已寫入緩衝區的資料量。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="f2ca2-144">呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>，讓資料可供 `PipeReader` 使用。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="f2ca2-145">在第二個迴圈中，`PipeReader` 會耗用 `PipeWriter` 所寫入的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="f2ca2-146">緩衝區來自通訊端。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-146">The buffers come from the socket.</span></span> <span data-ttu-id="f2ca2-147">對 `PipeReader.ReadAsync` 的呼叫：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="f2ca2-148">傳回 <xref:System.IO.Pipelines.ReadResult>，其中包含兩個重要的資訊片段：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="f2ca2-149">以 `ReadOnlySequence<byte>` 格式讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="f2ca2-150">布林值 `IsCompleted`，指出是否已達到資料結尾（EOF）。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span> 

<span data-ttu-id="f2ca2-151">尋找行尾（結束）分隔符號並剖析程式程式碼之後：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="f2ca2-152">邏輯會處理緩衝區，以略過已處理的內容。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="f2ca2-153">呼叫 `PipeReader.AdvanceTo`，告訴 `PipeReader` 已耗用並檢查多少資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="f2ca2-154">「讀取器」和「寫入器」迴圈會藉由呼叫 `Complete` 來結束。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="f2ca2-155">`Complete` 可讓基礎管道釋放它所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="f2ca2-156">背壓和流量控制</span><span class="sxs-lookup"><span data-stu-id="f2ca2-156">Backpressure and flow control</span></span>

<span data-ttu-id="f2ca2-157">理想的情況是，同時讀取和剖析工作：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="f2ca2-158">撰寫執行緒會取用來自網路的資料，並將它放在緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="f2ca2-159">剖析執行緒負責建立適當的資料結構。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="f2ca2-160">一般來說，剖析所花費的時間比只複製網路中的資料區塊還多：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="f2ca2-161">讀取執行緒會在剖析執行緒的前面取得。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="f2ca2-162">讀取執行緒必須減緩速度，或配置更多記憶體來儲存剖析執行緒的資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="f2ca2-163">為了達到最佳效能，經常暫停和配置更多記憶體之間會有平衡。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="f2ca2-164">若要解決上述問題，`Pipe` 有兩個設定可控制資料的流程：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="f2ca2-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>:決定在呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 暫停之前，應該緩衝多少資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="f2ca2-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>:判斷讀取器在 `PipeWriter.FlushAsync` 繼續的呼叫之前必須觀察多少資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![具有 ResumeWriterThreshold 和 PauseWriterThreshold 的圖表](./media/pipelines/resume-pause.png)

<span data-ttu-id="f2ca2-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="f2ca2-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="f2ca2-169">當 `Pipe` 中的資料量跨越 `PauseWriterThreshold` 時，傳回未完成的 `ValueTask<FlushResult>`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="f2ca2-170">當 `ValueTask<FlushResult>` 低於 `ResumeWriterThreshold` 時，即完成。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="f2ca2-171">有兩個值可用來防止快速迴圈，如果使用了某個值，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="f2ca2-172">範例</span><span class="sxs-lookup"><span data-stu-id="f2ca2-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="f2ca2-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="f2ca2-173">PipeScheduler</span></span>

<span data-ttu-id="f2ca2-174">通常在使用 `async` 和 `await` 時，非同步程式碼會在 <xref:System.Threading.Tasks.TaskScheduler> 或目前 <xref:System.Threading.SynchronizationContext> 上繼續。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="f2ca2-175">執行 i/o 時，請務必對執行 i/o 的位置進行更精細的控制。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="f2ca2-176">此控制項可讓您有效地利用 CPU 快取。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="f2ca2-177">有效率的快取對於高效能應用程式（例如 web 伺服器）很重要。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="f2ca2-178"><xref:System.IO.Pipelines.PipeScheduler> 可讓您控制非同步回呼的執行位置。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="f2ca2-179">根據預設：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-179">By default:</span></span>

* <span data-ttu-id="f2ca2-180">使用目前的 <xref:System.Threading.SynchronizationContext>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="f2ca2-181">如果沒有 `SynchronizationContext`，它會使用執行緒集區來執行回呼。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="f2ca2-182">[PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.ThreadPool)是將回呼佇列排入執行緒集區的 @no__t 1 實。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="f2ca2-183">`PipeScheduler.ThreadPool` 是預設值，通常是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="f2ca2-184">[PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.Inline)可能會導致非預期的結果，例如鎖死。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="f2ca2-185">管道重設</span><span class="sxs-lookup"><span data-stu-id="f2ca2-185">Pipe reset</span></span>

<span data-ttu-id="f2ca2-186">重複使用 `Pipe` 物件通常會很有效率。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="f2ca2-187">若要重設管道，當 `PipeReader` 和 `PipeWriter` 完成時，請呼叫 <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="f2ca2-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="f2ca2-188">PipeReader</span></span>

<span data-ttu-id="f2ca2-189"><xref:System.IO.Pipelines.PipeReader> 代表呼叫端管理記憶體。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="f2ca2-190">呼叫 <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> 之後，**一律**呼叫 <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f2ca2-191">這可讓 `PipeReader` 知道呼叫端何時會使用記憶體來進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="f2ca2-192">從 `PipeReader.ReadAsync` 傳回的 `ReadOnlySequence<byte>` 只有在呼叫 `PipeReader.AdvanceTo` 之前才有效。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="f2ca2-193">呼叫 `PipeReader.AdvanceTo` 之後，使用 `ReadOnlySequence<byte>` 是不合法的。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="f2ca2-194">`PipeReader.AdvanceTo` 會接受兩個 <xref:System.SequencePosition> 個引數：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="f2ca2-195">第一個引數會決定耗用多少記憶體。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="f2ca2-196">第二個引數會決定觀察到多少緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="f2ca2-197">將資料標示為已使用表示管道可以將記憶體傳回基礎緩衝集區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="f2ca2-198">將資料標示為已觀察控制下一次呼叫 `PipeReader.ReadAsync` 的方式。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="f2ca2-199">將所有專案標示為「已觀察」，表示下一次呼叫 `PipeReader.ReadAsync` 將不會傳回，直到有更多資料寫入管道為止。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="f2ca2-200">任何其他值都會讓下一次呼叫 `PipeReader.ReadAsync` 會立即傳回已觀察*和*未觀察到的資料，但已耗用資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="f2ca2-201">讀取串流資料案例</span><span class="sxs-lookup"><span data-stu-id="f2ca2-201">Read streaming data scenarios</span></span>

<span data-ttu-id="f2ca2-202">嘗試讀取串流資料時，有幾個常見的模式會出現：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="f2ca2-203">假設有資料流程的資料，請剖析單一訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="f2ca2-204">在給定資料流程的情況下，剖析所有可用的訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="f2ca2-205">下列範例使用 `TryParseMessage` 方法來剖析來自 `ReadOnlySequence<byte>` 的訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="f2ca2-206">`TryParseMessage` 會剖析單一訊息，並更新輸入緩衝區，以從緩衝區修剪已剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="f2ca2-207">`TryParseMessage` 不是 .NET 的一部分，它是在下列各節中使用的使用者撰寫方法。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="f2ca2-208">讀取單一訊息</span><span class="sxs-lookup"><span data-stu-id="f2ca2-208">Read a single message</span></span>

<span data-ttu-id="f2ca2-209">下列程式碼會從 `PipeReader` 讀取單一訊息，並將它傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="f2ca2-210">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-210">The preceding code:</span></span>

* <span data-ttu-id="f2ca2-211">剖析單一訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-211">Parses a single message.</span></span>
* <span data-ttu-id="f2ca2-212">更新已取用的 `SequencePosition`，並檢查 `SequencePosition` 以指向已修剪之輸入緩衝區的開頭。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="f2ca2-213">這兩個 @no__t 0 引數會更新，因為 `TryParseMessage` 會從輸入緩衝區移除剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="f2ca2-214">一般來說，從緩衝區剖析單一訊息時，檢查的位置應該是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="f2ca2-215">訊息的結尾。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-215">The end of the message.</span></span>
* <span data-ttu-id="f2ca2-216">如果找不到任何訊息，則為收到的緩衝區結尾。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="f2ca2-217">單一訊息案例最有可能發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="f2ca2-218">傳遞錯誤的值進行*檢查*可能會導致記憶體不足的例外狀況或無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="f2ca2-219">如需詳細資訊，請參閱本文的[PipeReader 常見問題](#gotchas)一節。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="f2ca2-220">讀取多個訊息</span><span class="sxs-lookup"><span data-stu-id="f2ca2-220">Reading multiple messages</span></span>

<span data-ttu-id="f2ca2-221">下列程式碼會讀取來自 `PipeReader` 的所有訊息，並在每個上呼叫 `ProcessMessageAsync`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="f2ca2-222">取消</span><span class="sxs-lookup"><span data-stu-id="f2ca2-222">Cancellation</span></span>

<span data-ttu-id="f2ca2-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="f2ca2-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="f2ca2-224">支援傳遞 <xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="f2ca2-225">如果在讀取暫止時取消 `CancellationToken`，則會擲回 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="f2ca2-226">支援透過 <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> 取消目前讀取作業的方法，這可避免引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="f2ca2-227">呼叫 `PipeReader.CancelPendingRead` 會導致 `PipeReader.ReadAsync` 的目前或下一次呼叫傳回 <xref:System.IO.Pipelines.ReadResult>，並將 `IsCanceled` 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="f2ca2-228">這有助於以非破壞性和非例外的方式來暫停現有的讀取迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="f2ca2-229">PipeReader 常見的問題</span><span class="sxs-lookup"><span data-stu-id="f2ca2-229">PipeReader common problems</span></span>

* <span data-ttu-id="f2ca2-230">將錯誤的值傳遞給 `consumed` 或 `examined` 可能會導致讀取已讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="f2ca2-231">如已檢查傳遞 `buffer.End`，可能會導致：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="f2ca2-232">停止的資料</span><span class="sxs-lookup"><span data-stu-id="f2ca2-232">Stalled data</span></span>
  * <span data-ttu-id="f2ca2-233">如果未耗用資料，可能是最終的記憶體不足（OOM）例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="f2ca2-234">例如，從緩衝區一次處理單一訊息時 `PipeReader.AdvanceTo(position, buffer.End)`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="f2ca2-235">將錯誤的值傳遞給 `consumed` 或 `examined` 可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="f2ca2-236">例如，如果 `buffer.Start` 未變更，則 `PipeReader.AdvanceTo(buffer.Start)` 會導致下一次呼叫 `PipeReader.ReadAsync` 在新資料抵達之前立即傳回。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="f2ca2-237">將錯誤的值傳遞給 `consumed` 或 `examined` 可能會導致無限緩衝（最終 OOM）。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="f2ca2-238">呼叫 `PipeReader.AdvanceTo` 之後，使用 `ReadOnlySequence<byte>` 可能會導致記憶體損毀（在免費後使用）。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="f2ca2-239">無法呼叫 `PipeReader.Complete/CompleteAsync` 可能會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="f2ca2-240">在處理緩衝區之前，檢查 <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> 並結束讀取邏輯會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="f2ca2-241">迴圈結束條件應以 `ReadResult.Buffer.IsEmpty` 和 `ReadResult.IsCompleted` 為基礎。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="f2ca2-242">這麼做不正確，可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="f2ca2-243">有問題的程式碼</span><span class="sxs-lookup"><span data-stu-id="f2ca2-243">Problematic code</span></span>

<span data-ttu-id="f2ca2-244">@no__t 0**資料遺失**</span><span class="sxs-lookup"><span data-stu-id="f2ca2-244">❌ **Data loss**</span></span>

<span data-ttu-id="f2ca2-245">當 `IsCompleted` 設定為 `true` 時，`ReadResult` 可以傳回最後的資料區段。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="f2ca2-246">在結束讀取迴圈之前不讀取該資料將會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="f2ca2-247">@no__t 0**無限迴圈**</span><span class="sxs-lookup"><span data-stu-id="f2ca2-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="f2ca2-248">如果 `Result.IsCompleted` `true`，但緩衝區中沒有完整的訊息，下列邏輯可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="f2ca2-249">以下是另一個具有相同問題的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="f2ca2-250">在檢查 `ReadResult.IsCompleted` 之前，它會檢查是否有非空白的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="f2ca2-251">因為它是在 `else if` 中，所以如果緩衝區中永遠不會有完整的訊息，它就會永久迴圈。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="f2ca2-252">❌ 非預期的停止**回應**</span><span class="sxs-lookup"><span data-stu-id="f2ca2-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="f2ca2-253">在 `examined` 位置中，以 `buffer.End` 無條件地呼叫 `PipeReader.AdvanceTo`，可能會在剖析單一訊息時造成停止回應。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="f2ca2-254">下一次呼叫 `PipeReader.AdvanceTo` 將不會傳回，直到：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="f2ca2-255">有更多資料寫入管道。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="f2ca2-256">而且先前並未檢查新的資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="f2ca2-257">❌**記憶體不足（OOM）**</span><span class="sxs-lookup"><span data-stu-id="f2ca2-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="f2ca2-258">在下列情況下，下列程式碼會持續進行緩衝處理，直到發生 <xref:System.OutOfMemoryException> 為止：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="f2ca2-259">訊息大小沒有上限。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-259">There's no maximum message size.</span></span>
* <span data-ttu-id="f2ca2-260">從 `PipeReader` 傳回的資料不會產生完整的訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="f2ca2-261">例如，它不會建立完整的訊息，因為另一端正在寫入大型訊息（例如，4 GB 的訊息）。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="f2ca2-262">❌**記憶體損毀**</span><span class="sxs-lookup"><span data-stu-id="f2ca2-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="f2ca2-263">撰寫讀取緩衝區的協助程式時，應該先複製任何傳回的承載，再呼叫 `Advance`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="f2ca2-264">下列範例會傳回 `Pipe` 已捨棄的記憶體，而且可能會在下一個作業中重複使用它（讀取/寫入）。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="f2ca2-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="f2ca2-265">PipeWriter</span></span>

<span data-ttu-id="f2ca2-266">@No__t-0 會管理要代表呼叫端寫入的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="f2ca2-267">`PipeWriter` 會執行[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1)。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1).</span></span> <span data-ttu-id="f2ca2-268">`IBufferWriter<byte>` 可讓您取得緩衝區的存取權，以執行寫入，而不需要額外的緩衝區複本。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="f2ca2-269">先前的程式碼：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-269">The previous code:</span></span>

* <span data-ttu-id="f2ca2-270">使用 <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>，從 `PipeWriter` 要求至少5個位元組的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>.</span></span>
* <span data-ttu-id="f2ca2-271">將 ASCII 字串 `"Hello"` 的位元組寫入傳回的 `Span<byte>`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-271">Writes bytes for the ASCII string `"Hello"` to the returned `Span<byte>`.</span></span>
* <span data-ttu-id="f2ca2-272">呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance%2A>，表示寫入緩衝區的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="f2ca2-273">排清 `PipeWriter`，這會將位元組傳送至基礎裝置。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="f2ca2-274">先前的寫入方法會使用 `PipeWriter` 所提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="f2ca2-275">或者，<xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="f2ca2-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="f2ca2-276">將現有的緩衝區複製到 `PipeWriter`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="f2ca2-277">視情況呼叫 `GetSpan`，`Advance`，並呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="f2ca2-278">取消</span><span class="sxs-lookup"><span data-stu-id="f2ca2-278">Cancellation</span></span>

<span data-ttu-id="f2ca2-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 支援傳遞 <xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="f2ca2-280">如果在清除暫止時解除標記，則傳遞 `CancellationToken` 會導致 `OperationCanceledException`。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="f2ca2-281">`PipeWriter.FlushAsync` 支援透過 <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> 取消目前的清除作業，而不引發例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="f2ca2-282">呼叫 `PipeWriter.CancelPendingFlush` 會導致目前或下一次呼叫 `PipeWriter.FlushAsync` 或 `PipeWriter.WriteAsync` 傳回 `IsCanceled` 設定為 `true` 的 <xref:System.IO.Pipelines.FlushResult>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="f2ca2-283">這有助於以非破壞性和非例外的方式來暫停產生排清。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="f2ca2-284">PipeWriter 常見的問題</span><span class="sxs-lookup"><span data-stu-id="f2ca2-284">PipeWriter common problems</span></span>

* <span data-ttu-id="f2ca2-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>，<xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 會傳回至少具有所要求記憶體數量的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="f2ca2-286">請**不要**採用確切的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="f2ca2-287">不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="f2ca2-288">呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> 之後，必須要求新的緩衝區，才能繼續寫入更多資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="f2ca2-289">無法寫入先前取得的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="f2ca2-290">呼叫 `GetMemory` 或 `GetSpan`，但不完整的呼叫 `FlushAsync` 並不安全。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="f2ca2-291">呼叫 `Complete` 或 `CompleteAsync`，而未清除的資料可能會導致記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="f2ca2-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="f2ca2-292">IDuplexPipe</span></span>

<span data-ttu-id="f2ca2-293">@No__t-0 是支援讀取和寫入之類型的合約。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="f2ca2-294">例如，網路連接會以 `IDuplexPipe` 來表示。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="f2ca2-295">與包含 `PipeReader` 和 `PipeWriter` 的 `Pipe` 不同，`IDuplexPipe` 代表全雙工連線的單一端。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="f2ca2-296">這表示將不會從 `PipeReader` 讀取寫入 @no__t 0。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="f2ca2-297">資料流</span><span class="sxs-lookup"><span data-stu-id="f2ca2-297">Streams</span></span>

<span data-ttu-id="f2ca2-298">讀取或寫入資料流程資料時，您通常會使用還原序列化程式來讀取資料，並使用序列化程式來寫入資料。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="f2ca2-299">大部分的讀取和寫入串流 Api 都有 `Stream` 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="f2ca2-300">為了讓您更輕鬆地與這些現有的 Api 整合，`PipeReader`，而 `PipeWriter` 會公開 <xref:System.IO.Pipelines.PipeReader.AsStream%2A>。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="f2ca2-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> 會傳回圍繞 `PipeReader` 或 `PipeWriter` 的 @no__t 1 執行。</span><span class="sxs-lookup"><span data-stu-id="f2ca2-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
