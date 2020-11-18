---
title: I/o 管線-.NET
description: 瞭解如何在 .NET 中有效率地使用 i/o 管線，並避免在您的程式碼中發生問題。
ms.date: 08/27/2020
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 508ae0e2b854f81ee639a63063a8f6d73ae84863
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830632"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="35463-103">.NET 中的 system.object</span><span class="sxs-lookup"><span data-stu-id="35463-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="35463-104"><xref:System.IO.Pipelines> 是新的程式庫，其設計目的是要讓您更輕鬆地在 .NET 中執行高效能 i/o。</span><span class="sxs-lookup"><span data-stu-id="35463-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="35463-105">它是以適用于所有 .NET 執行的 .NET Standard 為目標的程式庫。</span><span class="sxs-lookup"><span data-stu-id="35463-105">It's a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="35463-106">System.servicemodel 解決的問題</span><span class="sxs-lookup"><span data-stu-id="35463-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="35463-107">剖析串流資料的應用程式是由具有許多特製化和不尋常程式碼流程的未定案程式碼所組成。</span><span class="sxs-lookup"><span data-stu-id="35463-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="35463-108">未定案和特殊案例的程式碼很複雜且難以維護。</span><span class="sxs-lookup"><span data-stu-id="35463-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="35463-109">`System.IO.Pipelines` 的架構為：</span><span class="sxs-lookup"><span data-stu-id="35463-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="35463-110">具有高效能剖析串流資料的效能。</span><span class="sxs-lookup"><span data-stu-id="35463-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="35463-111">降低程式碼的複雜度。</span><span class="sxs-lookup"><span data-stu-id="35463-111">Reduce code complexity.</span></span>

<span data-ttu-id="35463-112">下列程式碼一般適用于接收以行分隔訊息 (`'\n'` 從用戶端) 分隔的 TCP 伺服器：</span><span class="sxs-lookup"><span data-stu-id="35463-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="35463-113">上述程式碼有幾個問題：</span><span class="sxs-lookup"><span data-stu-id="35463-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="35463-114">在的單一呼叫中，可能不會收到整個訊息 (行結尾) `ReadAsync` 。</span><span class="sxs-lookup"><span data-stu-id="35463-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="35463-115">它會忽略的結果 `stream.ReadAsync` 。</span><span class="sxs-lookup"><span data-stu-id="35463-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="35463-116">`stream.ReadAsync` 傳回讀取的資料量。</span><span class="sxs-lookup"><span data-stu-id="35463-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="35463-117">它不會處理在單一呼叫中讀取多行的情況 `ReadAsync` 。</span><span class="sxs-lookup"><span data-stu-id="35463-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="35463-118">它會在 `byte` 每次讀取時配置陣列。</span><span class="sxs-lookup"><span data-stu-id="35463-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="35463-119">若要修正上述問題，需要進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="35463-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="35463-120">緩衝傳入的資料，直到找到新的一行為止。</span><span class="sxs-lookup"><span data-stu-id="35463-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="35463-121">剖析緩衝區中傳回的所有行。</span><span class="sxs-lookup"><span data-stu-id="35463-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="35463-122">該行可能會)  (1024 個位元組的倍數。</span><span class="sxs-lookup"><span data-stu-id="35463-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="35463-123">程式碼需要調整輸入緩衝區的大小，直到找到分隔符號，才能符合緩衝區內的完整行。</span><span class="sxs-lookup"><span data-stu-id="35463-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="35463-124">如果重新調整緩衝區大小，則會在輸入中出現較長的行，以產生更多的緩衝區複本。</span><span class="sxs-lookup"><span data-stu-id="35463-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="35463-125">若要減少浪費的空間，請壓縮用來讀取行的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="35463-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="35463-126">請考慮使用緩衝集區，以避免重複配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="35463-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="35463-127">下列程式碼會解決其中一些問題：</span><span class="sxs-lookup"><span data-stu-id="35463-127">The following code addresses some of these problems:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

<span data-ttu-id="35463-128">先前的程式碼很複雜，而且無法解決所有識別出的問題。</span><span class="sxs-lookup"><span data-stu-id="35463-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="35463-129">高效能網路通常表示撰寫非常複雜的程式碼，以將效能最大化。</span><span class="sxs-lookup"><span data-stu-id="35463-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="35463-130">`System.IO.Pipelines` 的設計目的是要讓撰寫此類型的程式碼變得更容易。</span><span class="sxs-lookup"><span data-stu-id="35463-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="35463-131">Pipe</span><span class="sxs-lookup"><span data-stu-id="35463-131">Pipe</span></span>

<span data-ttu-id="35463-132"><xref:System.IO.Pipelines.Pipe>類別可以用來建立 `PipeWriter/PipeReader` 配對。</span><span class="sxs-lookup"><span data-stu-id="35463-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="35463-133">所有寫入的資料 `PipeWriter` 都可以在中取得 `PipeReader` ：</span><span class="sxs-lookup"><span data-stu-id="35463-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="35463-134">管道基本使用方式</span><span class="sxs-lookup"><span data-stu-id="35463-134">Pipe basic usage</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

<span data-ttu-id="35463-135">有兩個迴圈：</span><span class="sxs-lookup"><span data-stu-id="35463-135">There are two loops:</span></span>

* <span data-ttu-id="35463-136">`FillPipeAsync` 從讀取 `Socket` ，並寫入 `PipeWriter` 。</span><span class="sxs-lookup"><span data-stu-id="35463-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="35463-137">`ReadPipeAsync` 從讀取 `PipeReader` 並剖析傳入的行。</span><span class="sxs-lookup"><span data-stu-id="35463-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="35463-138">未配置明確的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="35463-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="35463-139">所有緩衝區管理都會委派給 `PipeReader` 和執行 `PipeWriter` 。</span><span class="sxs-lookup"><span data-stu-id="35463-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="35463-140">委派緩衝區管理可讓您更輕鬆地使用程式碼，僅專注于商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="35463-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="35463-141">在第一個迴圈中：</span><span class="sxs-lookup"><span data-stu-id="35463-141">In the first loop:</span></span>

* <span data-ttu-id="35463-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> 呼叫以從基礎寫入器取得記憶體。</span><span class="sxs-lookup"><span data-stu-id="35463-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="35463-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> 呼叫以指出 `PipeWriter` 寫入緩衝區的資料量。</span><span class="sxs-lookup"><span data-stu-id="35463-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="35463-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> 呼叫，以將資料提供給 `PipeReader` 。</span><span class="sxs-lookup"><span data-stu-id="35463-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="35463-145">在第二個迴圈中，會 `PipeReader` 使用寫入的緩衝區 `PipeWriter` 。</span><span class="sxs-lookup"><span data-stu-id="35463-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="35463-146">緩衝區來自通訊端。</span><span class="sxs-lookup"><span data-stu-id="35463-146">The buffers come from the socket.</span></span> <span data-ttu-id="35463-147">呼叫 `PipeReader.ReadAsync` ：</span><span class="sxs-lookup"><span data-stu-id="35463-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="35463-148">傳回 <xref:System.IO.Pipelines.ReadResult> ，其中包含兩個重要的資訊片段：</span><span class="sxs-lookup"><span data-stu-id="35463-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="35463-149">以形式讀取的資料 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="35463-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="35463-150">布林值 `IsCompleted` ，指出是否已達到 (EOF) 的資料結尾。</span><span class="sxs-lookup"><span data-stu-id="35463-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="35463-151">找出行尾 (EOL) 分隔符號和剖析該行：</span><span class="sxs-lookup"><span data-stu-id="35463-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="35463-152">邏輯會處理緩衝區以略過已處理的內容。</span><span class="sxs-lookup"><span data-stu-id="35463-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="35463-153">`PipeReader.AdvanceTo` 呼叫以告知已取用 `PipeReader` 和檢查的資料量。</span><span class="sxs-lookup"><span data-stu-id="35463-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="35463-154">讀取器和寫入器迴圈會藉由呼叫來結束 `Complete` 。</span><span class="sxs-lookup"><span data-stu-id="35463-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="35463-155">`Complete` 讓基礎管道釋出它所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="35463-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="35463-156">背壓和流程式控制制</span><span class="sxs-lookup"><span data-stu-id="35463-156">Backpressure and flow control</span></span>

<span data-ttu-id="35463-157">在理想的情況下，讀取和剖析工作：</span><span class="sxs-lookup"><span data-stu-id="35463-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="35463-158">寫入執行緒會取用網路的資料，並將它放入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="35463-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="35463-159">剖析執行緒負責建立適當的資料結構。</span><span class="sxs-lookup"><span data-stu-id="35463-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="35463-160">一般而言，剖析所需的時間比只從網路複製資料區塊更多：</span><span class="sxs-lookup"><span data-stu-id="35463-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="35463-161">讀取執行緒會在剖析執行緒之前取得。</span><span class="sxs-lookup"><span data-stu-id="35463-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="35463-162">讀取執行緒必須減緩或配置更多記憶體來儲存剖析執行緒的資料。</span><span class="sxs-lookup"><span data-stu-id="35463-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="35463-163">為了達到最佳效能，經常暫停和配置更多記憶體之間有平衡。</span><span class="sxs-lookup"><span data-stu-id="35463-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="35463-164">為了解決上述問題， `Pipe` 有兩個設定可控制資料的流程：</span><span class="sxs-lookup"><span data-stu-id="35463-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="35463-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>：決定在呼叫暫停之前應該緩衝的資料量 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 。</span><span class="sxs-lookup"><span data-stu-id="35463-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="35463-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>：決定讀取器必須觀察多少資料，才能繼續進行呼叫 `PipeWriter.FlushAsync` 。</span><span class="sxs-lookup"><span data-stu-id="35463-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![具有 ResumeWriterThreshold 和 PauseWriterThreshold 的圖表](media/pipelines/resume-pause.png)

<span data-ttu-id="35463-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="35463-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="35463-169">`ValueTask<FlushResult>`當超出時，傳回不完整的資料量 `Pipe` `PauseWriterThreshold` 。</span><span class="sxs-lookup"><span data-stu-id="35463-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="35463-170">`ValueTask<FlushResult>`當它變成低於時即完成 `ResumeWriterThreshold` 。</span><span class="sxs-lookup"><span data-stu-id="35463-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="35463-171">有兩個值可用來防止快速迴圈，如果使用一個值，就可能發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="35463-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="35463-172">範例</span><span class="sxs-lookup"><span data-stu-id="35463-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="35463-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="35463-173">PipeScheduler</span></span>

<span data-ttu-id="35463-174">通常在使用 `async` 和時 `await` ，非同步程式碼會在上 <xref:System.Threading.Tasks.TaskScheduler> 或目前的上繼續 <xref:System.Threading.SynchronizationContext> 。</span><span class="sxs-lookup"><span data-stu-id="35463-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="35463-175">執行 i/o 時，請務必對執行 i/o 的位置有細微的控制。</span><span class="sxs-lookup"><span data-stu-id="35463-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="35463-176">此控制項可讓您有效率地利用 CPU 快取。</span><span class="sxs-lookup"><span data-stu-id="35463-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="35463-177">有效率的快取對於高效能的應用程式（例如 web 伺服器）非常重要。</span><span class="sxs-lookup"><span data-stu-id="35463-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="35463-178"><xref:System.IO.Pipelines.PipeScheduler> 提供非同步回呼執行位置的控制權。</span><span class="sxs-lookup"><span data-stu-id="35463-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="35463-179">依照預設：</span><span class="sxs-lookup"><span data-stu-id="35463-179">By default:</span></span>

* <span data-ttu-id="35463-180">使用目前的 <xref:System.Threading.SynchronizationContext> 。</span><span class="sxs-lookup"><span data-stu-id="35463-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="35463-181">如果沒有 `SynchronizationContext` ，則會使用執行緒集區來執行回呼。</span><span class="sxs-lookup"><span data-stu-id="35463-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

<span data-ttu-id="35463-182">[PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) 是將回呼排入 <xref:System.IO.Pipelines.PipeScheduler> 執行緒集區的實作為佇列。</span><span class="sxs-lookup"><span data-stu-id="35463-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="35463-183">`PipeScheduler.ThreadPool` 是預設值，通常是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="35463-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="35463-184">[PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.Inline) 可能會造成非預期的結果，例如鎖死。</span><span class="sxs-lookup"><span data-stu-id="35463-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="35463-185">管道重設</span><span class="sxs-lookup"><span data-stu-id="35463-185">Pipe reset</span></span>

<span data-ttu-id="35463-186">重複使用物件通常會更有效率 `Pipe` 。</span><span class="sxs-lookup"><span data-stu-id="35463-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="35463-187">若要重設管道，請 <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> 在 `PipeReader` 和 `PipeWriter` 都完成時呼叫。</span><span class="sxs-lookup"><span data-stu-id="35463-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="35463-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="35463-188">PipeReader</span></span>

<span data-ttu-id="35463-189"><xref:System.IO.Pipelines.PipeReader> 代表呼叫端管理記憶體。</span><span class="sxs-lookup"><span data-stu-id="35463-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="35463-190">**一律** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> 在呼叫之後呼叫 <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="35463-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35463-191">這樣可讓您 `PipeReader` 知道呼叫端何時完成記憶體，以便進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="35463-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="35463-192">在 `ReadOnlySequence<byte>` 呼叫之前，從傳回的 `PipeReader.ReadAsync` 只有有效的 `PipeReader.AdvanceTo` 。</span><span class="sxs-lookup"><span data-stu-id="35463-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="35463-193">`ReadOnlySequence<byte>`在呼叫之後，請不合法 `PipeReader.AdvanceTo` 。</span><span class="sxs-lookup"><span data-stu-id="35463-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="35463-194">`PipeReader.AdvanceTo` 採用兩個 <xref:System.SequencePosition> 引數：</span><span class="sxs-lookup"><span data-stu-id="35463-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="35463-195">第一個引數會決定所耗用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="35463-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="35463-196">第二個引數會決定所觀察到的緩衝區數量。</span><span class="sxs-lookup"><span data-stu-id="35463-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="35463-197">將資料標示為已使用，表示管道可以將記憶體傳回至基礎緩衝集區。</span><span class="sxs-lookup"><span data-stu-id="35463-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="35463-198">將資料標示為觀察到的控制項下一次呼叫的方式 `PipeReader.ReadAsync` 。</span><span class="sxs-lookup"><span data-stu-id="35463-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="35463-199">將所有內容標示為已觀察，表示下一次的呼叫將 `PipeReader.ReadAsync` 不會傳回，直到有更多資料寫入管道為止。</span><span class="sxs-lookup"><span data-stu-id="35463-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="35463-200">任何其他值都會讓下一次呼叫 `PipeReader.ReadAsync` 立即傳回所觀察到 *and* 的未觀察到資料，但不是已取用的資料。</span><span class="sxs-lookup"><span data-stu-id="35463-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="35463-201">讀取串流資料案例</span><span class="sxs-lookup"><span data-stu-id="35463-201">Read streaming data scenarios</span></span>

<span data-ttu-id="35463-202">在嘗試讀取串流資料時，有幾個常見的模式會出現：</span><span class="sxs-lookup"><span data-stu-id="35463-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="35463-203">在給定資料流程的情況下，剖析單一訊息。</span><span class="sxs-lookup"><span data-stu-id="35463-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="35463-204">在給定資料流程的情況下，剖析所有可用的訊息。</span><span class="sxs-lookup"><span data-stu-id="35463-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="35463-205">下列範例會使用 `TryParseMessage` 方法來剖析來自的訊息 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="35463-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="35463-206">`TryParseMessage` 剖析單一訊息並更新輸入緩衝區，以修剪緩衝區中剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="35463-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="35463-207">`TryParseMessage` 不是 .NET 的一部分，而是在下列各節中使用的使用者撰寫方法。</span><span class="sxs-lookup"><span data-stu-id="35463-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="35463-208">讀取單一訊息</span><span class="sxs-lookup"><span data-stu-id="35463-208">Read a single message</span></span>

<span data-ttu-id="35463-209">下列程式碼會從讀取單一訊息 `PipeReader` ，並將它傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="35463-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

<span data-ttu-id="35463-210">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="35463-210">The preceding code:</span></span>

* <span data-ttu-id="35463-211">剖析單一訊息。</span><span class="sxs-lookup"><span data-stu-id="35463-211">Parses a single message.</span></span>
* <span data-ttu-id="35463-212">更新已使用 `SequencePosition` 和已檢查的， `SequencePosition` 以指向修剪的輸入緩衝區的開頭。</span><span class="sxs-lookup"><span data-stu-id="35463-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="35463-213">`SequencePosition`因為 `TryParseMessage` 從輸入緩衝區移除剖析的訊息，所以會更新這兩個引數。</span><span class="sxs-lookup"><span data-stu-id="35463-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="35463-214">一般來說，從緩衝區剖析單一訊息時，檢查的位置應該是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="35463-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="35463-215">訊息的結尾。</span><span class="sxs-lookup"><span data-stu-id="35463-215">The end of the message.</span></span>
* <span data-ttu-id="35463-216">如果找不到訊息，則為收到的緩衝區結尾。</span><span class="sxs-lookup"><span data-stu-id="35463-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="35463-217">單一訊息案例最有可能發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="35463-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="35463-218">傳遞錯誤的值給 *檢查* 可能會導致記憶體不足的例外狀況或無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="35463-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="35463-219">如需詳細資訊，請參閱本文中的 [PipeReader 常見問題](#gotchas) 一節。</span><span class="sxs-lookup"><span data-stu-id="35463-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="35463-220">讀取多個訊息</span><span class="sxs-lookup"><span data-stu-id="35463-220">Reading multiple messages</span></span>

<span data-ttu-id="35463-221">下列程式碼會讀取中的所有訊息 `PipeReader` ，並呼叫 `ProcessMessageAsync` 每個訊息。</span><span class="sxs-lookup"><span data-stu-id="35463-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a><span data-ttu-id="35463-222">取消</span><span class="sxs-lookup"><span data-stu-id="35463-222">Cancellation</span></span>

<span data-ttu-id="35463-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="35463-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="35463-224">支援傳遞 <xref:System.Threading.CancellationToken> 。</span><span class="sxs-lookup"><span data-stu-id="35463-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="35463-225"><xref:System.OperationCanceledException>如果在 `CancellationToken` 讀取暫止時取消，則會擲回。</span><span class="sxs-lookup"><span data-stu-id="35463-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="35463-226">支援透過的方式取消目前的讀取作業 <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> ，以避免引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35463-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="35463-227">呼叫 `PipeReader.CancelPendingRead` 會導致的目前或下一個呼叫傳回， `PipeReader.ReadAsync` <xref:System.IO.Pipelines.ReadResult> 並 `IsCanceled` 將設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="35463-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="35463-228">這有助於以非破壞性和非例外的方式來停止現有的讀取迴圈。</span><span class="sxs-lookup"><span data-stu-id="35463-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="35463-229">PipeReader 常見問題</span><span class="sxs-lookup"><span data-stu-id="35463-229">PipeReader common problems</span></span>

* <span data-ttu-id="35463-230">將錯誤的值傳遞至 `consumed` 或 `examined` 可能會導致讀取已讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="35463-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="35463-231">通過 `buffer.End` 檢查可能會導致：</span><span class="sxs-lookup"><span data-stu-id="35463-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="35463-232">停止資料</span><span class="sxs-lookup"><span data-stu-id="35463-232">Stalled data</span></span>
  * <span data-ttu-id="35463-233">如果未使用資料，可能會導致記憶體 (OOM) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35463-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="35463-234">例如， `PipeReader.AdvanceTo(position, buffer.End)` 從緩衝區一次處理單一訊息時。</span><span class="sxs-lookup"><span data-stu-id="35463-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="35463-235">將錯誤的值傳遞至 `consumed` 或 `examined` 可能會產生無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="35463-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="35463-236">例如， `PipeReader.AdvanceTo(buffer.Start)` 如果未 `buffer.Start` 變更，將會導致下一個呼叫在 `PipeReader.ReadAsync` 新的資料抵達前立即傳回。</span><span class="sxs-lookup"><span data-stu-id="35463-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="35463-237">將錯誤的值傳遞至 `consumed` 或 `examined` 可能會導致 (最終 OOM) 的無限緩衝。</span><span class="sxs-lookup"><span data-stu-id="35463-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="35463-238">在 `ReadOnlySequence<byte>` 呼叫之後， `PipeReader.AdvanceTo` 可能會導致記憶體損毀 (在免費) 之後使用。</span><span class="sxs-lookup"><span data-stu-id="35463-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="35463-239">呼叫失敗 `PipeReader.Complete/CompleteAsync` 可能會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="35463-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="35463-240">在 <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> 處理緩衝區之前檢查和結束讀取邏輯會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="35463-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="35463-241">迴圈結束條件應該以和為基礎 `ReadResult.Buffer.IsEmpty` `ReadResult.IsCompleted` 。</span><span class="sxs-lookup"><span data-stu-id="35463-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="35463-242">這樣做不正確，可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="35463-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="35463-243">有問題的程式碼</span><span class="sxs-lookup"><span data-stu-id="35463-243">Problematic code</span></span>

<span data-ttu-id="35463-244">❌ **資料遺失**</span><span class="sxs-lookup"><span data-stu-id="35463-244">❌ **Data loss**</span></span>

<span data-ttu-id="35463-245">`ReadResult`當設定為時，可以傳回最後一個資料區段 `IsCompleted` `true` 。</span><span class="sxs-lookup"><span data-stu-id="35463-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="35463-246">若未在結束讀取迴圈之前讀取該資料，將會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="35463-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="35463-247">❌**無限迴圈**</span><span class="sxs-lookup"><span data-stu-id="35463-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="35463-248">如果 `Result.IsCompleted` 是， `true` 但緩衝區中永遠不會有完整的訊息，則下列邏輯可能會產生無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="35463-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="35463-249">以下是具有相同問題的另一段程式碼。</span><span class="sxs-lookup"><span data-stu-id="35463-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="35463-250">它會先檢查是否有非空白的緩衝區，再進行檢查 `ReadResult.IsCompleted` 。</span><span class="sxs-lookup"><span data-stu-id="35463-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="35463-251">因為它是在中 `else if` ，所以如果緩衝區中沒有完整的訊息，它就會永遠不會迴圈。</span><span class="sxs-lookup"><span data-stu-id="35463-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="35463-252">❌未預期的停止 **回應**</span><span class="sxs-lookup"><span data-stu-id="35463-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="35463-253">`PipeReader.AdvanceTo`在位置中無條件地呼叫， `buffer.End` `examined` 可能會在剖析單一訊息時導致停止回應。</span><span class="sxs-lookup"><span data-stu-id="35463-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="35463-254">下一次呼叫將 `PipeReader.AdvanceTo` 不會傳回：</span><span class="sxs-lookup"><span data-stu-id="35463-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="35463-255">有更多資料寫入管道。</span><span class="sxs-lookup"><span data-stu-id="35463-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="35463-256">而且先前未檢查過新的資料。</span><span class="sxs-lookup"><span data-stu-id="35463-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="35463-257">❌**記憶體不足 (OOM)**</span><span class="sxs-lookup"><span data-stu-id="35463-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="35463-258">在下列情況下，下列程式碼會保留緩衝處理，直到 <xref:System.OutOfMemoryException> 發生為止：</span><span class="sxs-lookup"><span data-stu-id="35463-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="35463-259">沒有訊息大小上限。</span><span class="sxs-lookup"><span data-stu-id="35463-259">There's no maximum message size.</span></span>
* <span data-ttu-id="35463-260">從傳回的資料 `PipeReader` 並不會產生完整訊息。</span><span class="sxs-lookup"><span data-stu-id="35463-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="35463-261">例如，它不會建立完整的訊息，因為另一端正在撰寫大型訊息 (例如，4 GB 訊息) 。</span><span class="sxs-lookup"><span data-stu-id="35463-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="35463-262">❌**記憶體損毀**</span><span class="sxs-lookup"><span data-stu-id="35463-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="35463-263">撰寫讀取緩衝區的協助程式時，應在呼叫之前複製任何傳回的裝載 `Advance` 。</span><span class="sxs-lookup"><span data-stu-id="35463-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="35463-264">下列範例會傳回已捨棄的記憶體 `Pipe` ，而且可能會針對下一項作業重複使用它 (讀取/寫入) 。</span><span class="sxs-lookup"><span data-stu-id="35463-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="35463-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="35463-265">PipeWriter</span></span>

<span data-ttu-id="35463-266"><xref:System.IO.Pipelines.PipeWriter>管理緩衝區以代表呼叫者來撰寫。</span><span class="sxs-lookup"><span data-stu-id="35463-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="35463-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) 。</span><span class="sxs-lookup"><span data-stu-id="35463-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="35463-268">`IBufferWriter<byte>` 可以取得緩衝區的存取權，以執行寫入，而不需要額外的緩衝區複本。</span><span class="sxs-lookup"><span data-stu-id="35463-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

<span data-ttu-id="35463-269">先前的程式碼：</span><span class="sxs-lookup"><span data-stu-id="35463-269">The previous code:</span></span>

* <span data-ttu-id="35463-270">使用從要求至少5個位元組的緩衝區 `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 。</span><span class="sxs-lookup"><span data-stu-id="35463-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="35463-271">將 ASCII 字串的位元組寫入 `"Hello"` 傳回的 `Memory<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="35463-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="35463-272">呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> 以指出寫入緩衝區的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="35463-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="35463-273">清除 `PipeWriter` ，將位元組傳送到基礎裝置。</span><span class="sxs-lookup"><span data-stu-id="35463-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="35463-274">先前撰寫的方法會使用提供的緩衝區 `PipeWriter` 。</span><span class="sxs-lookup"><span data-stu-id="35463-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="35463-275">或者， <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="35463-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="35463-276">將現有的緩衝區複製到 `PipeWriter` 。</span><span class="sxs-lookup"><span data-stu-id="35463-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="35463-277">`GetSpan` `Advance` 視需要呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 。</span><span class="sxs-lookup"><span data-stu-id="35463-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a><span data-ttu-id="35463-278">取消</span><span class="sxs-lookup"><span data-stu-id="35463-278">Cancellation</span></span>

<span data-ttu-id="35463-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 支援傳遞 <xref:System.Threading.CancellationToken> 。</span><span class="sxs-lookup"><span data-stu-id="35463-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="35463-280">`CancellationToken` `OperationCanceledException` 如果在清除暫止時取消權杖，則在中傳遞結果。</span><span class="sxs-lookup"><span data-stu-id="35463-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="35463-281">`PipeWriter.FlushAsync` 支援透過未引發例外狀況來取消目前清除作業的方法 <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="35463-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="35463-282">呼叫 `PipeWriter.CancelPendingFlush` 會導致或的目前或下一個呼叫傳回 `PipeWriter.FlushAsync` `PipeWriter.WriteAsync` <xref:System.IO.Pipelines.FlushResult> ，並 `IsCanceled` 將設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="35463-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="35463-283">這有助於以非破壞性和非例外的方式來停止產生的清除。</span><span class="sxs-lookup"><span data-stu-id="35463-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="35463-284">PipeWriter 常見問題</span><span class="sxs-lookup"><span data-stu-id="35463-284">PipeWriter common problems</span></span>

* <span data-ttu-id="35463-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> 並傳回 <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 至少具有所要求記憶體數量的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="35463-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="35463-286">**請勿** 採用確切的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="35463-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="35463-287">不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="35463-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="35463-288">呼叫之後必須要求新的緩衝區 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> ，才能繼續寫入更多資料。</span><span class="sxs-lookup"><span data-stu-id="35463-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="35463-289">無法寫入先前取得的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="35463-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="35463-290">呼叫 `GetMemory` 或 `GetSpan` ，但 `FlushAsync` 不安全的呼叫不安全。</span><span class="sxs-lookup"><span data-stu-id="35463-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="35463-291">呼叫 `Complete` 或 `CompleteAsync` 未清除資料時，可能會導致記憶體損毀。</span><span class="sxs-lookup"><span data-stu-id="35463-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="35463-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="35463-292">IDuplexPipe</span></span>

<span data-ttu-id="35463-293"><xref:System.IO.Pipelines.IDuplexPipe>是支援讀取和寫入的類型合約。</span><span class="sxs-lookup"><span data-stu-id="35463-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="35463-294">例如，網路連接會以表示 `IDuplexPipe` 。</span><span class="sxs-lookup"><span data-stu-id="35463-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="35463-295">不同 `Pipe` 于（包含 `PipeReader` 和 `PipeWriter` ）， `IDuplexPipe` 代表全雙工連接的單一端。</span><span class="sxs-lookup"><span data-stu-id="35463-295">Unlike `Pipe`, which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="35463-296">這表示 `PipeWriter` 將不會從讀取寫入的內容 `PipeReader` 。</span><span class="sxs-lookup"><span data-stu-id="35463-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="35463-297">串流</span><span class="sxs-lookup"><span data-stu-id="35463-297">Streams</span></span>

<span data-ttu-id="35463-298">讀取或寫入資料流程資料時，您通常會使用還原序列化程式讀取資料，並使用序列化程式寫入資料。</span><span class="sxs-lookup"><span data-stu-id="35463-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="35463-299">大部分的讀取和寫入串流 Api 都有 `Stream` 參數。</span><span class="sxs-lookup"><span data-stu-id="35463-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="35463-300">讓您更輕鬆地整合這些現有的 Api， `PipeReader` 並 `PipeWriter` 公開 <xref:System.IO.Pipelines.PipeReader.AsStream%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="35463-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A> method.</span></span> <span data-ttu-id="35463-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> 傳回 `Stream` 或周圍的執行 `PipeReader` `PipeWriter` 。</span><span class="sxs-lookup"><span data-stu-id="35463-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>

### <a name="stream-example"></a><span data-ttu-id="35463-302">資料流程範例</span><span class="sxs-lookup"><span data-stu-id="35463-302">Stream example</span></span>

<span data-ttu-id="35463-303">`PipeReader` 您 `PipeWriter` 可以使用靜態方法來建立和實例，並 `Create` 指定 <xref:System.IO.Stream> 物件和選擇性的對應建立選項。</span><span class="sxs-lookup"><span data-stu-id="35463-303">`PipeReader` and `PipeWriter` instances can be created using the static `Create` methods given a <xref:System.IO.Stream> object and optional corresponding creation options.</span></span>

<span data-ttu-id="35463-304">可 <xref:System.IO.Pipelines.StreamPipeReaderOptions> 讓您控制如何 `PipeReader` 使用下列參數來建立實例：</span><span class="sxs-lookup"><span data-stu-id="35463-304">The <xref:System.IO.Pipelines.StreamPipeReaderOptions> allow for control over the creation of the `PipeReader` instance with the following parameters:</span></span>

- <span data-ttu-id="35463-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> 這是從集區租用記憶體時所使用的最小緩衝區大小（以位元組為單位），預設為 `4096` 。</span><span class="sxs-lookup"><span data-stu-id="35463-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> is the minimum buffer size in bytes used when renting memory from the pool, and defaults to `4096`.</span></span>
- <span data-ttu-id="35463-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> 旗標會決定基礎資料流程是否在完成之後保持開啟 `PipeReader` ，而且預設為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="35463-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeReader` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="35463-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> 表示在配置新的緩衝區之前，緩衝區中剩餘位元組的臨界值，預設為 `1024` 。</span><span class="sxs-lookup"><span data-stu-id="35463-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> represents the threshold of remaining bytes in the buffer before a new buffer is allocated, and defaults to `1024`.</span></span>
- <span data-ttu-id="35463-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> 是在配置 `MemoryPool<byte>` 記憶體時使用，而且預設為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="35463-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

<span data-ttu-id="35463-309">可 <xref:System.IO.Pipelines.StreamPipeWriterOptions> 讓您控制如何 `PipeWriter` 使用下列參數來建立實例：</span><span class="sxs-lookup"><span data-stu-id="35463-309">The <xref:System.IO.Pipelines.StreamPipeWriterOptions> allow for control over the creation of the `PipeWriter` instance with the following parameters:</span></span>

- <span data-ttu-id="35463-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> 旗標會決定基礎資料流程是否在完成之後保持開啟 `PipeWriter` ，而且預設為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="35463-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeWriter` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="35463-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> 表示從租借記憶體時要使用的最小緩衝區大小 <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> ，並且預設為 `4096` 。</span><span class="sxs-lookup"><span data-stu-id="35463-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> represents the minimum buffer size to use when renting memory from the <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool>, and defaults to `4096`.</span></span>
- <span data-ttu-id="35463-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> 是在配置 `MemoryPool<byte>` 記憶體時使用，而且預設為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="35463-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35463-313">`PipeReader` `PipeWriter` 使用方法建立和實例時 `Create` ，您必須考慮 `Stream` 物件存留期。</span><span class="sxs-lookup"><span data-stu-id="35463-313">When creating `PipeReader` and `PipeWriter` instances using the `Create` methods, you need to consider the `Stream` object lifetime.</span></span> <span data-ttu-id="35463-314">如果您需要在讀取器或寫入器完成後才能存取資料流程，您必須 `LeaveOpen` `true` 在建立選項上將旗標設為。</span><span class="sxs-lookup"><span data-stu-id="35463-314">If you need access to the stream after the reader or writer is done with it, you'll need to set the `LeaveOpen` flag to `true` on the creation options.</span></span> <span data-ttu-id="35463-315">否則，資料流程將會關閉。</span><span class="sxs-lookup"><span data-stu-id="35463-315">Otherwise, the stream will be closed.</span></span>

<span data-ttu-id="35463-316">下列程式碼示範如何 `PipeReader` `PipeWriter` 使用來自資料流程的方法來建立和實例 `Create` 。</span><span class="sxs-lookup"><span data-stu-id="35463-316">The following code demonstrates the creation of `PipeReader` and `PipeWriter` instances using the `Create` methods from a stream.</span></span>

:::code language="csharp" source="snippets/pipelines/Program.cs":::

<span data-ttu-id="35463-317">應用程式會使用將 <xref:System.IO.StreamReader> *lorem-ipsum.txt* 檔案讀取為數據流。</span><span class="sxs-lookup"><span data-stu-id="35463-317">The application uses a <xref:System.IO.StreamReader> to read the *lorem-ipsum.txt* file as a stream.</span></span> <span data-ttu-id="35463-318"><xref:System.IO.FileStream>會傳遞至，以具現 <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> 化 `PipeReader` 物件。</span><span class="sxs-lookup"><span data-stu-id="35463-318">The <xref:System.IO.FileStream> is passed to <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType>, which instantiates a `PipeReader` object.</span></span> <span data-ttu-id="35463-319">然後，主控台應用程式會將其標準輸出資料流程傳遞至 <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> 使用 <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="35463-319">The console application then passes its standard output stream to <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> using <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35463-320">此範例支援 [取消](#cancellation)。</span><span class="sxs-lookup"><span data-stu-id="35463-320">The example supports [cancellation](#cancellation).</span></span>
