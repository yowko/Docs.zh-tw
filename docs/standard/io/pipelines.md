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
# <a name="systemiopipelines-in-net"></a>.NET 中的 system.object

<xref:System.IO.Pipelines> 是新的程式庫，其設計目的是為了讓您更輕鬆地在 .NET 中執行高效能的 i/o。 它是以 .NET Standard 為目標的程式庫，其適用于所有的 .NET 部署。

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>由 system.servicemodel 解決的問題
<!-- corner case doesn't MT (machine translate)   -->
剖析串流資料的應用程式是由具有許多特製化和異常程式碼流程的重複採用程式碼所組成。 「未定案」和「特殊案例」程式碼很複雜且難以維護。

`System.IO.Pipelines` 已架構為：

* 具有高效能剖析串流資料。
* 降低程式碼的複雜度。

下列程式碼通常用於從用戶端接收以行分隔的訊息（以 `'\n'` 分隔）的 TCP 伺服器：

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);
    
    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

上述程式碼有幾個問題：

* 在 `ReadAsync` 的單一呼叫中，可能不會收到整個訊息（結尾的那一行）。
* 它會忽略 `stream.ReadAsync` 的結果。 `stream.ReadAsync` 會傳回已讀取的資料量。
* 它不會處理在單一 `ReadAsync` 呼叫中讀取多行的情況。
* 它會在每次讀取時配置 @no__t 0 陣列。

若要修正上述問題，需要進行下列變更：

* 緩衝傳入的資料，直到找到新的一行為止。
* 剖析緩衝區中傳回的所有行。
* 這行程式碼可能大於 1 KB （1024個位元組）。 程式碼必須調整輸入緩衝區的大小，才能找到整行。

  * 如果調整緩衝區大小，則會在輸入中出現較長的行時，產生更多的緩衝區複本。
  * 若要減少浪費的空間，請壓縮用來讀取行的緩衝區。

* 請考慮使用緩衝集區來避免重複配置記憶體。
* 下列程式碼會解決其中一些問題：

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

先前的程式碼很複雜，而且無法解決所有已識別的問題。 高效能的網路功能通常表示撰寫非常複雜的程式碼，以將效能最大化。 `System.IO.Pipelines` 的設計可讓您更輕鬆地撰寫這種類型的程式碼。

## <a name="pipe"></a>管道

@No__t-0 類別可以用來建立 @no__t 1 的配對。 寫入 `PipeWriter` 的所有資料都可在 `PipeReader` 中取得：

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>管道基本使用方式

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

有兩個迴圈：

* `FillPipeAsync` 會從 `Socket` 讀取，並寫入至 `PipeWriter`。
* `ReadPipeAsync` 會從 `PipeReader` 讀取並剖析傳入的行。

未配置明確的緩衝區。 系統會將所有緩衝區管理委派給 `PipeReader` 和 @no__t 1 的執行。 委派緩衝區管理可讓您更輕鬆地使用程式碼，只著重于商務邏輯。

在第一個迴圈中：

* 呼叫 <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>，以從基礎寫入器取得記憶體。
* 呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>，告訴 `PipeWriter` 已寫入緩衝區的資料量。
* 呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>，讓資料可供 `PipeReader` 使用。

在第二個迴圈中，`PipeReader` 會耗用 `PipeWriter` 所寫入的緩衝區。 緩衝區來自通訊端。 對 `PipeReader.ReadAsync` 的呼叫：

* 傳回 <xref:System.IO.Pipelines.ReadResult>，其中包含兩個重要的資訊片段：

  * 以 `ReadOnlySequence<byte>` 格式讀取的資料。
  * 布林值 `IsCompleted`，指出是否已達到資料結尾（EOF）。 

尋找行尾（結束）分隔符號並剖析程式程式碼之後：

* 邏輯會處理緩衝區，以略過已處理的內容。
* 呼叫 `PipeReader.AdvanceTo`，告訴 `PipeReader` 已耗用並檢查多少資料。

「讀取器」和「寫入器」迴圈會藉由呼叫 `Complete` 來結束。 `Complete` 可讓基礎管道釋放它所配置的記憶體。

### <a name="backpressure-and-flow-control"></a>背壓和流量控制

理想的情況是，同時讀取和剖析工作：

* 撰寫執行緒會取用來自網路的資料，並將它放在緩衝區中。
* 剖析執行緒負責建立適當的資料結構。

一般來說，剖析所花費的時間比只複製網路中的資料區塊還多：

* 讀取執行緒會在剖析執行緒的前面取得。
* 讀取執行緒必須減緩速度，或配置更多記憶體來儲存剖析執行緒的資料。

為了達到最佳效能，經常暫停和配置更多記憶體之間會有平衡。

若要解決上述問題，`Pipe` 有兩個設定可控制資料的流程：

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>:決定在呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 暫停之前，應該緩衝多少資料。
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>:判斷讀取器在 `PipeWriter.FlushAsync` 繼續的呼叫之前必須觀察多少資料。

![具有 ResumeWriterThreshold 和 PauseWriterThreshold 的圖表](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* 當 `Pipe` 中的資料量跨越 `PauseWriterThreshold` 時，傳回未完成的 `ValueTask<FlushResult>`。
* 當 `ValueTask<FlushResult>` 低於 `ResumeWriterThreshold` 時，即完成。

有兩個值可用來防止快速迴圈，如果使用了某個值，就會發生這種情況。

### <a name="examples"></a>範例

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

通常在使用 `async` 和 `await` 時，非同步程式碼會在 <xref:System.Threading.Tasks.TaskScheduler> 或目前 <xref:System.Threading.SynchronizationContext> 上繼續。

執行 i/o 時，請務必對執行 i/o 的位置進行更精細的控制。 此控制項可讓您有效地利用 CPU 快取。 有效率的快取對於高效能應用程式（例如 web 伺服器）很重要。 <xref:System.IO.Pipelines.PipeScheduler> 可讓您控制非同步回呼的執行位置。 根據預設：

* 使用目前的 <xref:System.Threading.SynchronizationContext>。
* 如果沒有 `SynchronizationContext`，它會使用執行緒集區來執行回呼。

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.ThreadPool)是將回呼佇列排入執行緒集區的 @no__t 1 實。 `PipeScheduler.ThreadPool` 是預設值，通常是最佳選擇。 [PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.Inline)可能會導致非預期的結果，例如鎖死。

### <a name="pipe-reset"></a>管道重設

重複使用 `Pipe` 物件通常會很有效率。 若要重設管道，當 `PipeReader` 和 `PipeWriter` 完成時，請呼叫 <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A>。

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> 代表呼叫端管理記憶體。 呼叫 <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> 之後，**一律**呼叫 <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType>。 這可讓 `PipeReader` 知道呼叫端何時會使用記憶體來進行追蹤。 從 `PipeReader.ReadAsync` 傳回的 `ReadOnlySequence<byte>` 只有在呼叫 `PipeReader.AdvanceTo` 之前才有效。 呼叫 `PipeReader.AdvanceTo` 之後，使用 `ReadOnlySequence<byte>` 是不合法的。

`PipeReader.AdvanceTo` 會接受兩個 <xref:System.SequencePosition> 個引數：

* 第一個引數會決定耗用多少記憶體。
* 第二個引數會決定觀察到多少緩衝區。

將資料標示為已使用表示管道可以將記憶體傳回基礎緩衝集區。 將資料標示為已觀察控制下一次呼叫 `PipeReader.ReadAsync` 的方式。 將所有專案標示為「已觀察」，表示下一次呼叫 `PipeReader.ReadAsync` 將不會傳回，直到有更多資料寫入管道為止。 任何其他值都會讓下一次呼叫 `PipeReader.ReadAsync` 會立即傳回已觀察*和*未觀察到的資料，但已耗用資料。

### <a name="read-streaming-data-scenarios"></a>讀取串流資料案例

嘗試讀取串流資料時，有幾個常見的模式會出現：

* 假設有資料流程的資料，請剖析單一訊息。
* 在給定資料流程的情況下，剖析所有可用的訊息。

下列範例使用 `TryParseMessage` 方法來剖析來自 `ReadOnlySequence<byte>` 的訊息。 `TryParseMessage` 會剖析單一訊息，並更新輸入緩衝區，以從緩衝區修剪已剖析的訊息。 `TryParseMessage` 不是 .NET 的一部分，它是在下列各節中使用的使用者撰寫方法。

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>讀取單一訊息

下列程式碼會從 `PipeReader` 讀取單一訊息，並將它傳回給呼叫者。

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

上述程式碼：

* 剖析單一訊息。
* 更新已取用的 `SequencePosition`，並檢查 `SequencePosition` 以指向已修剪之輸入緩衝區的開頭。

這兩個 @no__t 0 引數會更新，因為 `TryParseMessage` 會從輸入緩衝區移除剖析的訊息。 一般來說，從緩衝區剖析單一訊息時，檢查的位置應該是下列其中一項：

* 訊息的結尾。
* 如果找不到任何訊息，則為收到的緩衝區結尾。

單一訊息案例最有可能發生錯誤。 傳遞錯誤的值進行*檢查*可能會導致記憶體不足的例外狀況或無限迴圈。 如需詳細資訊，請參閱本文的[PipeReader 常見問題](#gotchas)一節。

### <a name="reading-multiple-messages"></a>讀取多個訊息

下列程式碼會讀取來自 `PipeReader` 的所有訊息，並在每個上呼叫 `ProcessMessageAsync`。

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>取消

`PipeReader.ReadAsync`:

* 支援傳遞 <xref:System.Threading.CancellationToken>。
* 如果在讀取暫止時取消 `CancellationToken`，則會擲回 <xref:System.OperationCanceledException>。
* 支援透過 <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> 取消目前讀取作業的方法，這可避免引發例外狀況。 呼叫 `PipeReader.CancelPendingRead` 會導致 `PipeReader.ReadAsync` 的目前或下一次呼叫傳回 <xref:System.IO.Pipelines.ReadResult>，並將 `IsCanceled` 設定為 `true`。 這有助於以非破壞性和非例外的方式來暫停現有的讀取迴圈。

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>PipeReader 常見的問題

* 將錯誤的值傳遞給 `consumed` 或 `examined` 可能會導致讀取已讀取的資料。
* 如已檢查傳遞 `buffer.End`，可能會導致：

  * 停止的資料
  * 如果未耗用資料，可能是最終的記憶體不足（OOM）例外狀況。 例如，從緩衝區一次處理單一訊息時 `PipeReader.AdvanceTo(position, buffer.End)`。

* 將錯誤的值傳遞給 `consumed` 或 `examined` 可能會導致無限迴圈。 例如，如果 `buffer.Start` 未變更，則 `PipeReader.AdvanceTo(buffer.Start)` 會導致下一次呼叫 `PipeReader.ReadAsync` 在新資料抵達之前立即傳回。
* 將錯誤的值傳遞給 `consumed` 或 `examined` 可能會導致無限緩衝（最終 OOM）。
* 呼叫 `PipeReader.AdvanceTo` 之後，使用 `ReadOnlySequence<byte>` 可能會導致記憶體損毀（在免費後使用）。
* 無法呼叫 `PipeReader.Complete/CompleteAsync` 可能會導致記憶體流失。
* 在處理緩衝區之前，檢查 <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> 並結束讀取邏輯會導致資料遺失。 迴圈結束條件應以 `ReadResult.Buffer.IsEmpty` 和 `ReadResult.IsCompleted` 為基礎。 這麼做不正確，可能會導致無限迴圈。

#### <a name="problematic-code"></a>有問題的程式碼

@no__t 0**資料遺失**

當 `IsCompleted` 設定為 `true` 時，`ReadResult` 可以傳回最後的資料區段。 在結束讀取迴圈之前不讀取該資料將會導致資料遺失。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

@no__t 0**無限迴圈**

如果 `Result.IsCompleted` `true`，但緩衝區中沒有完整的訊息，下列邏輯可能會導致無限迴圈。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

以下是另一個具有相同問題的程式碼片段。 在檢查 `ReadResult.IsCompleted` 之前，它會檢查是否有非空白的緩衝區。 因為它是在 `else if` 中，所以如果緩衝區中永遠不會有完整的訊息，它就會永久迴圈。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ 非預期的停止**回應**

在 `examined` 位置中，以 `buffer.End` 無條件地呼叫 `PipeReader.AdvanceTo`，可能會在剖析單一訊息時造成停止回應。 下一次呼叫 `PipeReader.AdvanceTo` 將不會傳回，直到：

* 有更多資料寫入管道。
* 而且先前並未檢查新的資料。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**記憶體不足（OOM）**

在下列情況下，下列程式碼會持續進行緩衝處理，直到發生 <xref:System.OutOfMemoryException> 為止：

* 訊息大小沒有上限。
* 從 `PipeReader` 傳回的資料不會產生完整的訊息。 例如，它不會建立完整的訊息，因為另一端正在寫入大型訊息（例如，4 GB 的訊息）。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**記憶體損毀**

撰寫讀取緩衝區的協助程式時，應該先複製任何傳回的承載，再呼叫 `Advance`。 下列範例會傳回 `Pipe` 已捨棄的記憶體，而且可能會在下一個作業中重複使用它（讀取/寫入）。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

@No__t-0 會管理要代表呼叫端寫入的緩衝區。 `PipeWriter` 會執行[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1)。 `IBufferWriter<byte>` 可讓您取得緩衝區的存取權，以執行寫入，而不需要額外的緩衝區複本。

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

先前的程式碼：

* 使用 <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>，從 `PipeWriter` 要求至少5個位元組的緩衝區。
* 將 ASCII 字串 `"Hello"` 的位元組寫入傳回的 `Span<byte>`。
* 呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance%2A>，表示寫入緩衝區的位元組數目。
* 排清 `PipeWriter`，這會將位元組傳送至基礎裝置。

先前的寫入方法會使用 `PipeWriter` 所提供的緩衝區。 或者，<xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>：

* 將現有的緩衝區複製到 `PipeWriter`。
* 視情況呼叫 `GetSpan`，`Advance`，並呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>。

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>取消

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 支援傳遞 <xref:System.Threading.CancellationToken>。 如果在清除暫止時解除標記，則傳遞 `CancellationToken` 會導致 `OperationCanceledException`。 `PipeWriter.FlushAsync` 支援透過 <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> 取消目前的清除作業，而不引發例外狀況的方法。 呼叫 `PipeWriter.CancelPendingFlush` 會導致目前或下一次呼叫 `PipeWriter.FlushAsync` 或 `PipeWriter.WriteAsync` 傳回 `IsCanceled` 設定為 `true` 的 <xref:System.IO.Pipelines.FlushResult>。 這有助於以非破壞性和非例外的方式來暫停產生排清。

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter 常見的問題

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>，<xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 會傳回至少具有所要求記憶體數量的緩衝區。 請**不要**採用確切的緩衝區大小。
* 不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。
* 呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> 之後，必須要求新的緩衝區，才能繼續寫入更多資料。 無法寫入先前取得的緩衝區。
* 呼叫 `GetMemory` 或 `GetSpan`，但不完整的呼叫 `FlushAsync` 並不安全。
* 呼叫 `Complete` 或 `CompleteAsync`，而未清除的資料可能會導致記憶體損毀。

## <a name="iduplexpipe"></a>IDuplexPipe

@No__t-0 是支援讀取和寫入之類型的合約。 例如，網路連接會以 `IDuplexPipe` 來表示。

 與包含 `PipeReader` 和 `PipeWriter` 的 `Pipe` 不同，`IDuplexPipe` 代表全雙工連線的單一端。 這表示將不會從 `PipeReader` 讀取寫入 @no__t 0。

## <a name="streams"></a>資料流

讀取或寫入資料流程資料時，您通常會使用還原序列化程式來讀取資料，並使用序列化程式來寫入資料。 大部分的讀取和寫入串流 Api 都有 `Stream` 參數。 為了讓您更輕鬆地與這些現有的 Api 整合，`PipeReader`，而 `PipeWriter` 會公開 <xref:System.IO.Pipelines.PipeReader.AsStream%2A>。  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> 會傳回圍繞 `PipeReader` 或 `PipeWriter` 的 @no__t 1 執行。
