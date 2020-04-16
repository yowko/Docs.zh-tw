---
title: I/O 管道 - .NET
description: 瞭解如何在 .NET 中有效地使用 I/O 管道,並避免代碼中的問題。
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 8822e731ae805e83d4072c5bd78dff3fcf9a31a1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81462514"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="9f014-103">系統.IO.導管在 .NET 中</span><span class="sxs-lookup"><span data-stu-id="9f014-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="9f014-104"><xref:System.IO.Pipelines>是一個新的庫,旨在使在 .NET 中更輕鬆地執行高性能 I/O。</span><span class="sxs-lookup"><span data-stu-id="9f014-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="9f014-105">它是面向 .NET 標準的庫,適用於所有 .NET 實現。</span><span class="sxs-lookup"><span data-stu-id="9f014-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="9f014-106">系統.IO.管道解決了什麼問題</span><span class="sxs-lookup"><span data-stu-id="9f014-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="9f014-107">分析流數據的應用由具有許多專用和異常代碼流的樣板代碼組成。</span><span class="sxs-lookup"><span data-stu-id="9f014-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="9f014-108">樣板和特殊情況碼複雜且難以維護。</span><span class="sxs-lookup"><span data-stu-id="9f014-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="9f014-109">`System.IO.Pipelines`被設計為:</span><span class="sxs-lookup"><span data-stu-id="9f014-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="9f014-110">具有高性能分析流數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="9f014-111">降低代碼複雜性。</span><span class="sxs-lookup"><span data-stu-id="9f014-111">Reduce code complexity.</span></span>

<span data-ttu-id="9f014-112">以下代碼對於從用戶端接收行分隔訊息(由`'\n'`) 分隔的 TCP 伺服器而言是典型的:</span><span class="sxs-lookup"><span data-stu-id="9f014-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="9f014-113">前面的代碼有幾個問題:</span><span class="sxs-lookup"><span data-stu-id="9f014-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="9f014-114">在單個調用`ReadAsync`中可能不會接收整個消息(行尾)。</span><span class="sxs-lookup"><span data-stu-id="9f014-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="9f014-115">忽略了的結果`stream.ReadAsync`。</span><span class="sxs-lookup"><span data-stu-id="9f014-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="9f014-116">`stream.ReadAsync`返回讀取的數據量。</span><span class="sxs-lookup"><span data-stu-id="9f014-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="9f014-117">它不處理在單個`ReadAsync`調用中讀取多行的情況。</span><span class="sxs-lookup"><span data-stu-id="9f014-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="9f014-118">它分配一個`byte`包含每個讀取的陣列。</span><span class="sxs-lookup"><span data-stu-id="9f014-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="9f014-119">要修復上述問題,需要進行以下更改:</span><span class="sxs-lookup"><span data-stu-id="9f014-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="9f014-120">緩衝傳入數據,直到找到新行。</span><span class="sxs-lookup"><span data-stu-id="9f014-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="9f014-121">分析緩衝區中返回的所有行。</span><span class="sxs-lookup"><span data-stu-id="9f014-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="9f014-122">該行可能大於 1 KB(1024 位元組)。</span><span class="sxs-lookup"><span data-stu-id="9f014-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="9f014-123">代碼需要調整輸入緩衝區的大小,直到找到分隔符,以便適合緩衝區內的完整行。</span><span class="sxs-lookup"><span data-stu-id="9f014-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="9f014-124">如果調整緩衝區大小,則隨著輸入中顯示的長行,將會有更多的緩衝區副本。</span><span class="sxs-lookup"><span data-stu-id="9f014-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="9f014-125">為了減少浪費的空間,請壓縮用於讀取線的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="9f014-126">請考慮使用緩衝池以避免重複分配內存。</span><span class="sxs-lookup"><span data-stu-id="9f014-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="9f014-127">以下代碼解決了其中一些問題:</span><span class="sxs-lookup"><span data-stu-id="9f014-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="9f014-128">前面的代碼很複雜,不能解決所有已識別的問題。</span><span class="sxs-lookup"><span data-stu-id="9f014-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="9f014-129">高性能網路通常意味著編寫非常複雜的代碼以最大限度地提高性能。</span><span class="sxs-lookup"><span data-stu-id="9f014-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="9f014-130">`System.IO.Pipelines`旨在使編寫此類代碼更容易。</span><span class="sxs-lookup"><span data-stu-id="9f014-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="9f014-131">Pipe</span><span class="sxs-lookup"><span data-stu-id="9f014-131">Pipe</span></span>

<span data-ttu-id="9f014-132">類別<xref:System.IO.Pipelines.Pipe>可建立`PipeWriter/PipeReader`。</span><span class="sxs-lookup"><span data-stu-id="9f014-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="9f014-133">寫入的`PipeWriter`資料均位於 : `PipeReader`</span><span class="sxs-lookup"><span data-stu-id="9f014-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="9f014-134">管線基本用法</span><span class="sxs-lookup"><span data-stu-id="9f014-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="9f014-135">有兩個迴圈:</span><span class="sxs-lookup"><span data-stu-id="9f014-135">There are two loops:</span></span>

* <span data-ttu-id="9f014-136">`FillPipeAsync`從 讀`Socket`取 並`PipeWriter`寫入 。</span><span class="sxs-lookup"><span data-stu-id="9f014-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="9f014-137">`ReadPipeAsync`從`PipeReader`讀取 和 解析傳入行。</span><span class="sxs-lookup"><span data-stu-id="9f014-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="9f014-138">沒有分配顯式緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="9f014-139">所有緩衝區管理都委派給`PipeReader``PipeWriter`和 實現。</span><span class="sxs-lookup"><span data-stu-id="9f014-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="9f014-140">委派緩衝區管理使使用代碼更容易只關注業務邏輯。</span><span class="sxs-lookup"><span data-stu-id="9f014-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="9f014-141">在第一個循環中:</span><span class="sxs-lookup"><span data-stu-id="9f014-141">In the first loop:</span></span>

* <span data-ttu-id="9f014-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>調用 以從基礎寫入器獲取記憶體。</span><span class="sxs-lookup"><span data-stu-id="9f014-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="9f014-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>調用 以告訴寫`PipeWriter`入 緩衝區的數據量。</span><span class="sxs-lookup"><span data-stu-id="9f014-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="9f014-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>呼叫 以使資料可供`PipeReader`。</span><span class="sxs-lookup"><span data-stu-id="9f014-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="9f014-145">在第二個循環中,`PipeReader`使用 由`PipeWriter`編寫的 緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="9f014-146">緩衝區來自套接字。</span><span class="sxs-lookup"><span data-stu-id="9f014-146">The buffers come from the socket.</span></span> <span data-ttu-id="9f014-147">呼叫`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="9f014-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="9f014-148">傳回<xref:System.IO.Pipelines.ReadResult>包含兩條重要資訊的傳回 :</span><span class="sxs-lookup"><span data-stu-id="9f014-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="9f014-149">以的讀取形式的`ReadOnlySequence<byte>`資料 。</span><span class="sxs-lookup"><span data-stu-id="9f014-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="9f014-150">一個布爾`IsCompleted`,指示是否已達到數據結束 (EOF)。</span><span class="sxs-lookup"><span data-stu-id="9f014-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="9f014-151">找到行的末尾 (EOL) 分隔符並分析行後:</span><span class="sxs-lookup"><span data-stu-id="9f014-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="9f014-152">邏輯處理緩衝區以跳過已處理的內容。</span><span class="sxs-lookup"><span data-stu-id="9f014-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="9f014-153">`PipeReader.AdvanceTo`調用 以告訴`PipeReader`已 消耗和檢查的數據量。</span><span class="sxs-lookup"><span data-stu-id="9f014-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="9f014-154">讀取器和編寫器通過調用`Complete`結束。</span><span class="sxs-lookup"><span data-stu-id="9f014-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="9f014-155">`Complete`允許基礎管道釋放它分配的記憶體。</span><span class="sxs-lookup"><span data-stu-id="9f014-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="9f014-156">背壓力和流量控制</span><span class="sxs-lookup"><span data-stu-id="9f014-156">Backpressure and flow control</span></span>

<span data-ttu-id="9f014-157">理想情況下,閱讀和分析協同工作:</span><span class="sxs-lookup"><span data-stu-id="9f014-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="9f014-158">編寫線程使用來自網路的數據並將其放入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="9f014-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="9f014-159">分析線程負責構造適當的數據結構。</span><span class="sxs-lookup"><span data-stu-id="9f014-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="9f014-160">通常,分析需要比從網路複製資料塊更多的時間:</span><span class="sxs-lookup"><span data-stu-id="9f014-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="9f014-161">讀取線程先於解析線程。</span><span class="sxs-lookup"><span data-stu-id="9f014-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="9f014-162">讀取線程必須減慢速度或分配更多記憶體以存儲分析線程的數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="9f014-163">為了獲得最佳性能,在頻繁暫停和分配更多記憶體之間具有平衡。</span><span class="sxs-lookup"><span data-stu-id="9f014-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="9f014-164">要解決上述問題,有`Pipe`兩個設置來控制數據流:</span><span class="sxs-lookup"><span data-stu-id="9f014-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="9f014-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>:確定在調用暫停<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>之前應緩衝多少數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="9f014-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>:確定讀取器在調用恢復`PipeWriter.FlushAsync`之前必須觀察的數據量。</span><span class="sxs-lookup"><span data-stu-id="9f014-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![具有復原寫入器閾值和暫停寫入器閾值的圖表](./media/pipelines/resume-pause.png)

<span data-ttu-id="9f014-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="9f014-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="9f014-169">當`ValueTask<FlushResult>``Pipe`中的數據量交叉`PauseWriterThreshold`時返回不完整。</span><span class="sxs-lookup"><span data-stu-id="9f014-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="9f014-170">`ValueTask<FlushResult>`當它低於`ResumeWriterThreshold`時完成。</span><span class="sxs-lookup"><span data-stu-id="9f014-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="9f014-171">兩個值用於防止快速迴圈,如果使用一個值,則可能發生此迴圈。</span><span class="sxs-lookup"><span data-stu-id="9f014-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="9f014-172">範例</span><span class="sxs-lookup"><span data-stu-id="9f014-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="9f014-173">導管排路</span><span class="sxs-lookup"><span data-stu-id="9f014-173">PipeScheduler</span></span>

<span data-ttu-id="9f014-174">通常,當`async``await`使用和時,非同步代碼在<xref:System.Threading.Tasks.TaskScheduler>上或<xref:System.Threading.SynchronizationContext>上繼續在當前上。</span><span class="sxs-lookup"><span data-stu-id="9f014-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="9f014-175">執行I/O時,對執行I/O的位置進行細粒度控制非常重要。</span><span class="sxs-lookup"><span data-stu-id="9f014-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="9f014-176">此控制項允許有效地利用 CPU 快取。</span><span class="sxs-lookup"><span data-stu-id="9f014-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="9f014-177">對於 Web 伺服器等高性能應用,高效緩存至關重要。</span><span class="sxs-lookup"><span data-stu-id="9f014-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="9f014-178"><xref:System.IO.Pipelines.PipeScheduler>提供對異步回調運行位置的控制。</span><span class="sxs-lookup"><span data-stu-id="9f014-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="9f014-179">依照預設：</span><span class="sxs-lookup"><span data-stu-id="9f014-179">By default:</span></span>

* <span data-ttu-id="9f014-180">使用電流<xref:System.Threading.SynchronizationContext>。</span><span class="sxs-lookup"><span data-stu-id="9f014-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="9f014-181">如果沒有`SynchronizationContext`,則使用線程池運行回調。</span><span class="sxs-lookup"><span data-stu-id="9f014-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="9f014-182">[Pipe計劃.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool)是佇<xref:System.IO.Pipelines.PipeScheduler>列 回調到線程池的實現。</span><span class="sxs-lookup"><span data-stu-id="9f014-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="9f014-183">`PipeScheduler.ThreadPool`是預設值,通常是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="9f014-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="9f014-184">[Pipe計劃.內聯](xref:System.IO.Pipelines.PipeScheduler.Inline)可能會導致意外的後果,如死鎖。</span><span class="sxs-lookup"><span data-stu-id="9f014-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="9f014-185">管線複位</span><span class="sxs-lookup"><span data-stu-id="9f014-185">Pipe reset</span></span>

<span data-ttu-id="9f014-186">重用`Pipe`物件通常很高效。</span><span class="sxs-lookup"><span data-stu-id="9f014-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="9f014-187">要重置管道,請當<xref:System.IO.Pipelines.PipeReader><xref:System.IO.Pipelines.Pipe.Reset%2A>`PipeReader``PipeWriter`和都已完成時調用。</span><span class="sxs-lookup"><span data-stu-id="9f014-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="9f014-188">管管閱讀器</span><span class="sxs-lookup"><span data-stu-id="9f014-188">PipeReader</span></span>

<span data-ttu-id="9f014-189"><xref:System.IO.Pipelines.PipeReader>代表調用方管理記憶體。</span><span class="sxs-lookup"><span data-stu-id="9f014-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="9f014-190">**通話**<xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType>後 始終<xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>呼叫 。</span><span class="sxs-lookup"><span data-stu-id="9f014-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9f014-191">這樣可以`PipeReader`知道調用方何時使用記憶體完成,以便可以跟蹤它。</span><span class="sxs-lookup"><span data-stu-id="9f014-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="9f014-192">返回`ReadOnlySequence<byte>``PipeReader.ReadAsync`的僅在調用`PipeReader.AdvanceTo`之前 有效。</span><span class="sxs-lookup"><span data-stu-id="9f014-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="9f014-193">調用`ReadOnlySequence<byte>``PipeReader.AdvanceTo`后使用是違法的。</span><span class="sxs-lookup"><span data-stu-id="9f014-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="9f014-194">`PipeReader.AdvanceTo`採用兩<xref:System.SequencePosition>個參數:</span><span class="sxs-lookup"><span data-stu-id="9f014-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="9f014-195">第一個參數確定消耗了多少記憶體。</span><span class="sxs-lookup"><span data-stu-id="9f014-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="9f014-196">第二個參數確定觀察到的緩衝區量。</span><span class="sxs-lookup"><span data-stu-id="9f014-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="9f014-197">將數據標記為已使用意味著管道可以將記憶體返回到基礎緩衝池。</span><span class="sxs-lookup"><span data-stu-id="9f014-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="9f014-198">將數據標記為觀察控制下一次調用`PipeReader.ReadAsync`執行。</span><span class="sxs-lookup"><span data-stu-id="9f014-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="9f014-199">將所有內容標記為已觀察到,這意味著在下一`PipeReader.ReadAsync`個調用之前不會返回,直到有更多的數據寫入管道。</span><span class="sxs-lookup"><span data-stu-id="9f014-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="9f014-200">任何其他值都將發出下一個調用,`PipeReader.ReadAsync`以便立即返回觀測*和*未觀測的數據,但不會返回已使用的數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="9f014-201">讀取串流資料專案</span><span class="sxs-lookup"><span data-stu-id="9f014-201">Read streaming data scenarios</span></span>

<span data-ttu-id="9f014-202">嘗試讀取串流資料時會出現幾個典型模式:</span><span class="sxs-lookup"><span data-stu-id="9f014-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="9f014-203">給定數據流,解析單個消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="9f014-204">給定數據流,解析所有可用消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="9f014-205">以下示例使用`TryParseMessage`方法分析`ReadOnlySequence<byte>`來自的消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="9f014-206">`TryParseMessage`分析單一消息並更新輸入緩衝區以修剪緩衝區中分析的消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="9f014-207">`TryParseMessage`不是 .NET 的一部分,它是以下部分中使用的使用者書面方法。</span><span class="sxs-lookup"><span data-stu-id="9f014-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="9f014-208">閱讀訊息</span><span class="sxs-lookup"><span data-stu-id="9f014-208">Read a single message</span></span>

<span data-ttu-id="9f014-209">以下代碼從 讀取單個`PipeReader`消息 並將其返回給調用方。</span><span class="sxs-lookup"><span data-stu-id="9f014-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="9f014-210">上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="9f014-210">The preceding code:</span></span>

* <span data-ttu-id="9f014-211">分析單個消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-211">Parses a single message.</span></span>
* <span data-ttu-id="9f014-212">更新已使用`SequencePosition`並`SequencePosition`檢查 的已用值,以指向修剪的輸入緩衝區的開始。</span><span class="sxs-lookup"><span data-stu-id="9f014-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="9f014-213">這兩`SequencePosition`個參數將更新,`TryParseMessage`因為從輸入緩衝區中刪除解析的消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="9f014-214">通常,當分析來自緩衝區的單一訊息時,檢查的位置應為以下位置之一:</span><span class="sxs-lookup"><span data-stu-id="9f014-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="9f014-215">消息的結尾。</span><span class="sxs-lookup"><span data-stu-id="9f014-215">The end of the message.</span></span>
* <span data-ttu-id="9f014-216">如果未找到消息,則接收緩衝區的末尾。</span><span class="sxs-lookup"><span data-stu-id="9f014-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="9f014-217">單個消息大小寫最有可能出錯。</span><span class="sxs-lookup"><span data-stu-id="9f014-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="9f014-218">傳遞錯誤的值*以檢查*可能會導致記憶體不足異常或無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="9f014-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="9f014-219">有關詳細資訊,請參閱本文中的[PipeReader 常見問題](#gotchas)部分。</span><span class="sxs-lookup"><span data-stu-id="9f014-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="9f014-220">讀取多條訊息</span><span class="sxs-lookup"><span data-stu-id="9f014-220">Reading multiple messages</span></span>

<span data-ttu-id="9f014-221">以下代碼從 讀`PipeReader`取 所有消息`ProcessMessageAsync`,並調用每個消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="9f014-222">取消</span><span class="sxs-lookup"><span data-stu-id="9f014-222">Cancellation</span></span>

<span data-ttu-id="9f014-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="9f014-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="9f014-224">支援傳遞<xref:System.Threading.CancellationToken>。</span><span class="sxs-lookup"><span data-stu-id="9f014-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="9f014-225">在讀取<xref:System.OperationCanceledException>掛起`CancellationToken`時 引發 如果 取消 。</span><span class="sxs-lookup"><span data-stu-id="9f014-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="9f014-226">支援通過 取消當前讀取操作<xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>的方法 ,以避免引發異常。</span><span class="sxs-lookup"><span data-stu-id="9f014-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="9f014-227">呼叫`PipeReader.CancelPendingRead`此或下一個呼叫`PipeReader.ReadAsync`傳<xref:System.IO.Pipelines.ReadResult>`IsCanceled`回`true`設定為的呼叫 。</span><span class="sxs-lookup"><span data-stu-id="9f014-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="9f014-228">這對於以非破壞性和非特殊方式停止現有讀取迴圈非常有用。</span><span class="sxs-lookup"><span data-stu-id="9f014-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="9f014-229">管機閱讀器常見問題</span><span class="sxs-lookup"><span data-stu-id="9f014-229">PipeReader common problems</span></span>

* <span data-ttu-id="9f014-230">將錯誤值傳遞給`consumed``examined`或可能導致讀取已讀取的數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="9f014-231">通過`buffer.End`檢查可能導致:</span><span class="sxs-lookup"><span data-stu-id="9f014-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="9f014-232">停滯的資料</span><span class="sxs-lookup"><span data-stu-id="9f014-232">Stalled data</span></span>
  * <span data-ttu-id="9f014-233">如果未消耗數據,則可能是最終記憶體不足 (OOM) 異常。</span><span class="sxs-lookup"><span data-stu-id="9f014-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="9f014-234">例如,`PipeReader.AdvanceTo(position, buffer.End)`當一次從緩衝區處理一條消息時。</span><span class="sxs-lookup"><span data-stu-id="9f014-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="9f014-235">將錯誤值傳遞給`consumed``examined`或 可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="9f014-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="9f014-236">例如,`PipeReader.AdvanceTo(buffer.Start)``buffer.Start`如果尚未更改,將導致下一個呼`PipeReader.ReadAsync`叫 在新資料到達之前立即返回。</span><span class="sxs-lookup"><span data-stu-id="9f014-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="9f014-237">將錯誤值傳遞給`consumed``examined`或可能導致無限緩衝(最終 OOM)。</span><span class="sxs-lookup"><span data-stu-id="9f014-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="9f014-238">使用`ReadOnlySequence<byte>`后調用`PipeReader.AdvanceTo`可能會導致記憶體損壞(空閒后使用)。</span><span class="sxs-lookup"><span data-stu-id="9f014-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="9f014-239">無法調用`PipeReader.Complete/CompleteAsync`可能會導致記憶體洩漏。</span><span class="sxs-lookup"><span data-stu-id="9f014-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="9f014-240">在處理<xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType>緩衝區之前檢查和退出讀取邏輯會導致數據丟失。</span><span class="sxs-lookup"><span data-stu-id="9f014-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="9f014-241">環路退出條件應基於`ReadResult.Buffer.IsEmpty``ReadResult.IsCompleted`與 。</span><span class="sxs-lookup"><span data-stu-id="9f014-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="9f014-242">這樣做不正確可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="9f014-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="9f014-243">有問題的代碼</span><span class="sxs-lookup"><span data-stu-id="9f014-243">Problematic code</span></span>

<span data-ttu-id="9f014-244">❌**資料遺失**</span><span class="sxs-lookup"><span data-stu-id="9f014-244">❌ **Data loss**</span></span>

<span data-ttu-id="9f014-245">設定`ReadResult`為時`IsCompleted`,可以傳回資料的最後一段`true`。</span><span class="sxs-lookup"><span data-stu-id="9f014-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="9f014-246">在退出讀取迴圈之前不讀取該數據將導致數據丟失。</span><span class="sxs-lookup"><span data-stu-id="9f014-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9f014-247">❌**無限迴圈**</span><span class="sxs-lookup"><span data-stu-id="9f014-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="9f014-248">如果`true`是 ,則以下邏輯可能會導致無限`Result.IsCompleted`迴圈, 但緩衝區中從未包含完整的消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9f014-249">下面是另一個具有相同問題的代碼。</span><span class="sxs-lookup"><span data-stu-id="9f014-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="9f014-250">在檢查`ReadResult.IsCompleted`之前,它正在檢查非空緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="9f014-251">因為它在`else if`中,如果緩衝區中永遠不會有完整的消息,它將永遠迴圈。</span><span class="sxs-lookup"><span data-stu-id="9f014-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9f014-252">❌**意外暫停**</span><span class="sxs-lookup"><span data-stu-id="9f014-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="9f014-253">在分析`PipeReader.AdvanceTo`單`buffer.End`個`examined`消息時 ,無條件調用 該位置可能會導致掛起。</span><span class="sxs-lookup"><span data-stu-id="9f014-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="9f014-254">下一個呼叫`PipeReader.AdvanceTo`不會返回,直到:</span><span class="sxs-lookup"><span data-stu-id="9f014-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="9f014-255">寫入管道的數據更多。</span><span class="sxs-lookup"><span data-stu-id="9f014-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="9f014-256">並且以前沒有檢查過新數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9f014-257">❌**記憶體不足 (OOM)**</span><span class="sxs-lookup"><span data-stu-id="9f014-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="9f014-258">在以下情況下,以下代碼會一直緩衝,直到發生<xref:System.OutOfMemoryException>:</span><span class="sxs-lookup"><span data-stu-id="9f014-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="9f014-259">沒有最大消息大小。</span><span class="sxs-lookup"><span data-stu-id="9f014-259">There's no maximum message size.</span></span>
* <span data-ttu-id="9f014-260">從返回`PipeReader`的數據不會發出完整的消息。</span><span class="sxs-lookup"><span data-stu-id="9f014-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="9f014-261">例如,它不發出完整的消息,因為另一方正在編寫大型消息(例如,4 GB 消息)。</span><span class="sxs-lookup"><span data-stu-id="9f014-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="9f014-262">❌**記憶體損壞**</span><span class="sxs-lookup"><span data-stu-id="9f014-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="9f014-263">編寫讀取緩衝區的幫助器時,應在調用`Advance`之前複製任何返回的有效負載。</span><span class="sxs-lookup"><span data-stu-id="9f014-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="9f014-264">下面的示例將返回`Pipe`已丟棄的記憶體,並可能將其重新用於下一個操作(讀取/寫入)。</span><span class="sxs-lookup"><span data-stu-id="9f014-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="9f014-265">管道作家</span><span class="sxs-lookup"><span data-stu-id="9f014-265">PipeWriter</span></span>

<span data-ttu-id="9f014-266"><xref:System.IO.Pipelines.PipeWriter>管理緩衝區,用於代表調用方進行寫入。</span><span class="sxs-lookup"><span data-stu-id="9f014-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="9f014-267">`PipeWriter`實現[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)器 。</span><span class="sxs-lookup"><span data-stu-id="9f014-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="9f014-268">`IBufferWriter<byte>`無需其他緩衝區副本即可訪問緩衝區以執行寫入。</span><span class="sxs-lookup"><span data-stu-id="9f014-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="9f014-269">前面的代碼:</span><span class="sxs-lookup"><span data-stu-id="9f014-269">The previous code:</span></span>

* <span data-ttu-id="9f014-270">從 using<xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>請求至少`PipeWriter`5 個字節 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="9f014-271">將 ASCII 字`"Hello"`串的位元組寫`Memory<byte>`入的 。</span><span class="sxs-lookup"><span data-stu-id="9f014-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="9f014-272">調用<xref:System.IO.Pipelines.PipeWriter.Advance%2A>以指示寫入緩衝區的位元組數。</span><span class="sxs-lookup"><span data-stu-id="9f014-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="9f014-273">重新載`PipeWriter`入位元組傳送到基礎裝置的刷新 。</span><span class="sxs-lookup"><span data-stu-id="9f014-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="9f014-274">前面的寫入方法使用 提供的緩衝`PipeWriter`區 。</span><span class="sxs-lookup"><span data-stu-id="9f014-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="9f014-275">或者, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="9f014-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="9f014-276">將現有緩衝區複製到`PipeWriter`。</span><span class="sxs-lookup"><span data-stu-id="9f014-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="9f014-277">呼叫`GetSpan`,`Advance`並根據需要呼<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>叫 。</span><span class="sxs-lookup"><span data-stu-id="9f014-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="9f014-278">取消</span><span class="sxs-lookup"><span data-stu-id="9f014-278">Cancellation</span></span>

<span data-ttu-id="9f014-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>支援傳遞<xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="9f014-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="9f014-280">如果在刷新`CancellationToken`掛起時取消權杖,則在中傳遞結果`OperationCanceledException`。</span><span class="sxs-lookup"><span data-stu-id="9f014-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="9f014-281">`PipeWriter.FlushAsync`支援通過<xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType>不引發異常來取消當前刷新操作的方法。</span><span class="sxs-lookup"><span data-stu-id="9f014-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="9f014-282">呼叫`PipeWriter.CancelPendingFlush`此或下一個呼叫`PipeWriter.FlushAsync``PipeWriter.WriteAsync`到<xref:System.IO.Pipelines.FlushResult>`IsCanceled`或`true`設定為傳回 。</span><span class="sxs-lookup"><span data-stu-id="9f014-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="9f014-283">這對於以非破壞性和非特殊方式停止屈服沖洗非常有用。</span><span class="sxs-lookup"><span data-stu-id="9f014-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="9f014-284">管管編寫器常見問題</span><span class="sxs-lookup"><span data-stu-id="9f014-284">PipeWriter common problems</span></span>

* <span data-ttu-id="9f014-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>並<xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>返回至少具有請求內存量的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="9f014-286">**不要**假定確切的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="9f014-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="9f014-287">不能保證連續調用將返回相同的緩衝區或相同大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="9f014-288">調用<xref:System.IO.Pipelines.PipeWriter.Advance%2A>後必須請求新的緩衝區以繼續寫入更多數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="9f014-289">無法寫入以前獲取的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9f014-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="9f014-290">呼叫`GetMemory``GetSpan`或呼叫不`FlushAsync`完整 時不安全。</span><span class="sxs-lookup"><span data-stu-id="9f014-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="9f014-291">調用`Complete``CompleteAsync`或 未刷新數據時可能會導致記憶體損壞。</span><span class="sxs-lookup"><span data-stu-id="9f014-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="9f014-292">I雙工管</span><span class="sxs-lookup"><span data-stu-id="9f014-292">IDuplexPipe</span></span>

<span data-ttu-id="9f014-293"><xref:System.IO.Pipelines.IDuplexPipe>是支援讀取和寫入的類型的協定。</span><span class="sxs-lookup"><span data-stu-id="9f014-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="9f014-294">例如, 網路連線將由`IDuplexPipe`表示 。</span><span class="sxs-lookup"><span data-stu-id="9f014-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="9f014-295">與`Pipe`包含和`PipeReader` `PipeWriter` `IDuplexPipe`a 不同,表示全雙工連接的單一側。</span><span class="sxs-lookup"><span data-stu-id="9f014-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="9f014-296">這表示寫`PipeWriter`入 的內容不會從`PipeReader`讀取 。</span><span class="sxs-lookup"><span data-stu-id="9f014-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="9f014-297">資料流</span><span class="sxs-lookup"><span data-stu-id="9f014-297">Streams</span></span>

<span data-ttu-id="9f014-298">讀取或寫入流數據時,通常使用去序列化器讀取數據並使用序列化器寫入數據。</span><span class="sxs-lookup"><span data-stu-id="9f014-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="9f014-299">這些讀取與寫入流 API 大多`Stream`有參數 。</span><span class="sxs-lookup"><span data-stu-id="9f014-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="9f014-300">為了更輕鬆地與這些現有 API`PipeReader`整合`PipeWriter`,<xref:System.IO.Pipelines.PipeReader.AsStream%2A>並公開 。</span><span class="sxs-lookup"><span data-stu-id="9f014-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="9f014-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>返回`Stream``PipeReader`圍繞`PipeWriter`的 實現。</span><span class="sxs-lookup"><span data-stu-id="9f014-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
