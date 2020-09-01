---
title: I/o 管線-.NET
description: 瞭解如何在 .NET 中有效率地使用 i/o 管線，並避免在您的程式碼中發生問題。
ms.date: 08/27/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: a24d7f5c22c936cd3fd3fdc51f0f3ace56386574
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271980"
---
# <a name="systemiopipelines-in-net"></a>.NET 中的 system.object

<xref:System.IO.Pipelines> 是新的程式庫，其設計目的是要讓您更輕鬆地在 .NET 中執行高效能 i/o。 它是以適用于所有 .NET 執行的 .NET Standard 為目標的程式庫。

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>System.servicemodel 解決的問題

<!-- corner case doesn't MT (machine translate)   -->
剖析串流資料的應用程式是由具有許多特製化和不尋常程式碼流程的未定案程式碼所組成。 未定案和特殊案例的程式碼很複雜且難以維護。

`System.IO.Pipelines` 的架構為：

* 具有高效能剖析串流資料的效能。
* 降低程式碼的複雜度。

下列程式碼一般適用于接收以行分隔訊息 (`'\n'` 從用戶端) 分隔的 TCP 伺服器：

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

* 在的單一呼叫中，可能不會收到整個訊息 (行結尾) `ReadAsync` 。
* 它會忽略的結果 `stream.ReadAsync` 。 `stream.ReadAsync` 傳回讀取的資料量。
* 它不會處理在單一呼叫中讀取多行的情況 `ReadAsync` 。
* 它會在 `byte` 每次讀取時配置陣列。

若要修正上述問題，需要進行下列變更：

* 緩衝傳入的資料，直到找到新的一行為止。
* 剖析緩衝區中傳回的所有行。
* 該行可能會)  (1024 個位元組的倍數。 程式碼需要調整輸入緩衝區的大小，直到找到分隔符號，才能符合緩衝區內的完整行。

  * 如果重新調整緩衝區大小，則會在輸入中出現較長的行，以產生更多的緩衝區複本。
  * 若要減少浪費的空間，請壓縮用來讀取行的緩衝區。

* 請考慮使用緩衝集區，以避免重複配置記憶體。
* 下列程式碼會解決其中一些問題：

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

先前的程式碼很複雜，而且無法解決所有識別出的問題。 高效能網路通常表示撰寫非常複雜的程式碼，以將效能最大化。 `System.IO.Pipelines` 的設計目的是要讓撰寫此類型的程式碼變得更容易。

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Pipe

<xref:System.IO.Pipelines.Pipe>類別可以用來建立 `PipeWriter/PipeReader` 配對。 所有寫入的資料 `PipeWriter` 都可以在中取得 `PipeReader` ：

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>管道基本使用方式

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

有兩個迴圈：

* `FillPipeAsync` 從讀取 `Socket` ，並寫入 `PipeWriter` 。
* `ReadPipeAsync` 從讀取 `PipeReader` 並剖析傳入的行。

未配置明確的緩衝區。 所有緩衝區管理都會委派給 `PipeReader` 和執行 `PipeWriter` 。 委派緩衝區管理可讓您更輕鬆地使用程式碼，僅專注于商務邏輯。

在第一個迴圈中：

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> 呼叫以從基礎寫入器取得記憶體。
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> 呼叫以指出 `PipeWriter` 寫入緩衝區的資料量。
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> 呼叫，以將資料提供給 `PipeReader` 。

在第二個迴圈中，會 `PipeReader` 使用寫入的緩衝區 `PipeWriter` 。 緩衝區來自通訊端。 呼叫 `PipeReader.ReadAsync` ：

* 傳回 <xref:System.IO.Pipelines.ReadResult> ，其中包含兩個重要的資訊片段：

  * 以形式讀取的資料 `ReadOnlySequence<byte>` 。
  * 布林值 `IsCompleted` ，指出是否已達到 (EOF) 的資料結尾。

找出行尾 (EOL) 分隔符號和剖析該行：

* 邏輯會處理緩衝區以略過已處理的內容。
* `PipeReader.AdvanceTo` 呼叫以告知已取用 `PipeReader` 和檢查的資料量。

讀取器和寫入器迴圈會藉由呼叫來結束 `Complete` 。 `Complete` 讓基礎管道釋出它所配置的記憶體。

### <a name="backpressure-and-flow-control"></a>背壓和流程式控制制

在理想的情況下，讀取和剖析工作：

* 寫入執行緒會取用網路的資料，並將它放入緩衝區中。
* 剖析執行緒負責建立適當的資料結構。

一般而言，剖析所需的時間比只從網路複製資料區塊更多：

* 讀取執行緒會在剖析執行緒之前取得。
* 讀取執行緒必須減緩或配置更多記憶體來儲存剖析執行緒的資料。

為了達到最佳效能，經常暫停和配置更多記憶體之間有平衡。

為了解決上述問題， `Pipe` 有兩個設定可控制資料的流程：

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>：決定在呼叫暫停之前應該緩衝的資料量 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 。
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>：決定讀取器必須觀察多少資料，才能繼續進行呼叫 `PipeWriter.FlushAsync` 。

![具有 ResumeWriterThreshold 和 PauseWriterThreshold 的圖表](media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* `ValueTask<FlushResult>`當超出時，傳回不完整的資料量 `Pipe` `PauseWriterThreshold` 。
* `ValueTask<FlushResult>`當它變成低於時即完成 `ResumeWriterThreshold` 。

有兩個值可用來防止快速迴圈，如果使用一個值，就可能發生這種情況。

### <a name="examples"></a>範例

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

通常在使用 `async` 和時 `await` ，非同步程式碼會在上 <xref:System.Threading.Tasks.TaskScheduler> 或目前的上繼續 <xref:System.Threading.SynchronizationContext> 。

執行 i/o 時，請務必對執行 i/o 的位置有細微的控制。 此控制項可讓您有效率地利用 CPU 快取。 有效率的快取對於高效能的應用程式（例如 web 伺服器）非常重要。 <xref:System.IO.Pipelines.PipeScheduler> 提供非同步回呼執行位置的控制權。 依照預設：

* 使用目前的 <xref:System.Threading.SynchronizationContext> 。
* 如果沒有 `SynchronizationContext` ，則會使用執行緒集區來執行回呼。

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

[PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) 是將回呼排入 <xref:System.IO.Pipelines.PipeScheduler> 執行緒集區的實作為佇列。 `PipeScheduler.ThreadPool` 是預設值，通常是最佳選擇。 [PipeScheduler](xref:System.IO.Pipelines.PipeScheduler.Inline) 可能會造成非預期的結果，例如鎖死。

### <a name="pipe-reset"></a>管道重設

重複使用物件通常會更有效率 `Pipe` 。 若要重設管道，請 <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> 在 `PipeReader` 和 `PipeWriter` 都完成時呼叫。

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> 代表呼叫端管理記憶體。 **一律** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> 在呼叫之後呼叫 <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> 。 這樣可讓您 `PipeReader` 知道呼叫端何時完成記憶體，以便進行追蹤。 在 `ReadOnlySequence<byte>` 呼叫之前，從傳回的 `PipeReader.ReadAsync` 只有有效的 `PipeReader.AdvanceTo` 。 `ReadOnlySequence<byte>`在呼叫之後，請不合法 `PipeReader.AdvanceTo` 。

`PipeReader.AdvanceTo` 採用兩個 <xref:System.SequencePosition> 引數：

* 第一個引數會決定所耗用的記憶體數量。
* 第二個引數會決定所觀察到的緩衝區數量。

將資料標示為已使用，表示管道可以將記憶體傳回至基礎緩衝集區。 將資料標示為觀察到的控制項下一次呼叫的方式 `PipeReader.ReadAsync` 。 將所有內容標示為已觀察，表示下一次的呼叫將 `PipeReader.ReadAsync` 不會傳回，直到有更多資料寫入管道為止。 任何其他值都會讓下一次呼叫 `PipeReader.ReadAsync` 立即傳回所觀察到*and*的未觀察到資料，但不是已取用的資料。

### <a name="read-streaming-data-scenarios"></a>讀取串流資料案例

在嘗試讀取串流資料時，有幾個常見的模式會出現：

* 在給定資料流程的情況下，剖析單一訊息。
* 在給定資料流程的情況下，剖析所有可用的訊息。

下列範例會使用 `TryParseMessage` 方法來剖析來自的訊息 `ReadOnlySequence<byte>` 。 `TryParseMessage` 剖析單一訊息並更新輸入緩衝區，以修剪緩衝區中剖析的訊息。 `TryParseMessage` 不是 .NET 的一部分，而是在下列各節中使用的使用者撰寫方法。

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>讀取單一訊息

下列程式碼會從讀取單一訊息 `PipeReader` ，並將它傳回給呼叫端。

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

上述程式碼：

* 剖析單一訊息。
* 更新已使用 `SequencePosition` 和已檢查的， `SequencePosition` 以指向修剪的輸入緩衝區的開頭。

`SequencePosition`因為 `TryParseMessage` 從輸入緩衝區移除剖析的訊息，所以會更新這兩個引數。 一般來說，從緩衝區剖析單一訊息時，檢查的位置應該是下列其中一項：

* 訊息的結尾。
* 如果找不到訊息，則為收到的緩衝區結尾。

單一訊息案例最有可能發生錯誤。 傳遞錯誤的值給 *檢查* 可能會導致記憶體不足的例外狀況或無限迴圈。 如需詳細資訊，請參閱本文中的 [PipeReader 常見問題](#gotchas) 一節。

### <a name="reading-multiple-messages"></a>讀取多個訊息

下列程式碼會讀取中的所有訊息 `PipeReader` ，並呼叫 `ProcessMessageAsync` 每個訊息。

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a>取消

`PipeReader.ReadAsync`:

* 支援傳遞 <xref:System.Threading.CancellationToken> 。
* <xref:System.OperationCanceledException>如果在 `CancellationToken` 讀取暫止時取消，則會擲回。
* 支援透過的方式取消目前的讀取作業 <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> ，以避免引發例外狀況。 呼叫 `PipeReader.CancelPendingRead` 會導致的目前或下一個呼叫傳回， `PipeReader.ReadAsync` <xref:System.IO.Pipelines.ReadResult> 並 `IsCanceled` 將設定為 `true` 。 這有助於以非破壞性和非例外的方式來停止現有的讀取迴圈。

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>PipeReader 常見問題

* 將錯誤的值傳遞至 `consumed` 或 `examined` 可能會導致讀取已讀取的資料。
* 通過 `buffer.End` 檢查可能會導致：

  * 停止資料
  * 如果未使用資料，可能會導致記憶體 (OOM) 例外狀況。 例如， `PipeReader.AdvanceTo(position, buffer.End)` 從緩衝區一次處理單一訊息時。

* 將錯誤的值傳遞至 `consumed` 或 `examined` 可能會產生無限迴圈。 例如， `PipeReader.AdvanceTo(buffer.Start)` 如果未 `buffer.Start` 變更，將會導致下一個呼叫在 `PipeReader.ReadAsync` 新的資料抵達前立即傳回。
* 將錯誤的值傳遞至 `consumed` 或 `examined` 可能會導致 (最終 OOM) 的無限緩衝。
* 在 `ReadOnlySequence<byte>` 呼叫之後， `PipeReader.AdvanceTo` 可能會導致記憶體損毀 (在免費) 之後使用。
* 呼叫失敗 `PipeReader.Complete/CompleteAsync` 可能會導致記憶體流失。
* 在 <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> 處理緩衝區之前檢查和結束讀取邏輯會導致資料遺失。 迴圈結束條件應該以和為基礎 `ReadResult.Buffer.IsEmpty` `ReadResult.IsCompleted` 。 這樣做不正確，可能會導致無限迴圈。

#### <a name="problematic-code"></a>有問題的程式碼

❌**資料遺失**

`ReadResult`當設定為時，可以傳回最後一個資料區段 `IsCompleted` `true` 。 若未在結束讀取迴圈之前讀取該資料，將會導致資料遺失。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**無限迴圈**

如果 `Result.IsCompleted` 是， `true` 但緩衝區中永遠不會有完整的訊息，則下列邏輯可能會產生無限迴圈。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

以下是具有相同問題的另一段程式碼。 它會先檢查是否有非空白的緩衝區，再進行檢查 `ReadResult.IsCompleted` 。 因為它是在中 `else if` ，所以如果緩衝區中沒有完整的訊息，它就會永遠不會迴圈。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌未預期的停止 **回應**

`PipeReader.AdvanceTo`在位置中無條件地呼叫， `buffer.End` `examined` 可能會在剖析單一訊息時導致停止回應。 下一次呼叫將 `PipeReader.AdvanceTo` 不會傳回：

* 有更多資料寫入管道。
* 而且先前未檢查過新的資料。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**記憶體不足 (OOM) **

在下列情況下，下列程式碼會保留緩衝處理，直到 <xref:System.OutOfMemoryException> 發生為止：

* 沒有訊息大小上限。
* 從傳回的資料 `PipeReader` 並不會產生完整訊息。 例如，它不會建立完整的訊息，因為另一端正在撰寫大型訊息 (例如，4 GB 訊息) 。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**記憶體損毀**

撰寫讀取緩衝區的協助程式時，應在呼叫之前複製任何傳回的裝載 `Advance` 。 下列範例會傳回已捨棄的記憶體 `Pipe` ，而且可能會針對下一項作業重複使用它 (讀取/寫入) 。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

<xref:System.IO.Pipelines.PipeWriter>管理緩衝區以代表呼叫者來撰寫。 `PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) 。 `IBufferWriter<byte>` 可以取得緩衝區的存取權，以執行寫入，而不需要額外的緩衝區複本。

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

先前的程式碼：

* 使用從要求至少5個位元組的緩衝區 `PipeWriter` <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 。
* 將 ASCII 字串的位元組寫入 `"Hello"` 傳回的 `Memory<byte>` 。
* 呼叫 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> 以指出寫入緩衝區的位元組數目。
* 清除 `PipeWriter` ，將位元組傳送到基礎裝置。

先前撰寫的方法會使用提供的緩衝區 `PipeWriter` 。 或者， <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> ：

* 將現有的緩衝區複製到 `PipeWriter` 。
* `GetSpan` `Advance` 視需要呼叫 <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 。

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a>取消

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> 支援傳遞 <xref:System.Threading.CancellationToken> 。 `CancellationToken` `OperationCanceledException` 如果在清除暫止時取消權杖，則在中傳遞結果。 `PipeWriter.FlushAsync` 支援透過未引發例外狀況來取消目前清除作業的方法 <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> 。 呼叫 `PipeWriter.CancelPendingFlush` 會導致或的目前或下一個呼叫傳回 `PipeWriter.FlushAsync` `PipeWriter.WriteAsync` <xref:System.IO.Pipelines.FlushResult> ，並 `IsCanceled` 將設定為 `true` 。 這有助於以非破壞性和非例外的方式來停止產生的清除。

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>PipeWriter 常見問題

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> 並傳回 <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> 至少具有所要求記憶體數量的緩衝區。 **請勿** 採用確切的緩衝區大小。
* 不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。
* 呼叫之後必須要求新的緩衝區 <xref:System.IO.Pipelines.PipeWriter.Advance%2A> ，才能繼續寫入更多資料。 無法寫入先前取得的緩衝區。
* 呼叫 `GetMemory` 或 `GetSpan` ，但 `FlushAsync` 不安全的呼叫不安全。
* 呼叫 `Complete` 或 `CompleteAsync` 未清除資料時，可能會導致記憶體損毀。

## <a name="iduplexpipe"></a>IDuplexPipe

<xref:System.IO.Pipelines.IDuplexPipe>是支援讀取和寫入的類型合約。 例如，網路連接會以表示 `IDuplexPipe` 。

 不同 `Pipe` 于（包含 `PipeReader` 和 `PipeWriter` ）， `IDuplexPipe` 代表全雙工連接的單一端。 這表示 `PipeWriter` 將不會從讀取寫入的內容 `PipeReader` 。

## <a name="streams"></a>串流

讀取或寫入資料流程資料時，您通常會使用還原序列化程式讀取資料，並使用序列化程式寫入資料。 大部分的讀取和寫入串流 Api 都有 `Stream` 參數。 讓您更輕鬆地整合這些現有的 Api， `PipeReader` 並 `PipeWriter` 公開 <xref:System.IO.Pipelines.PipeReader.AsStream%2A> 方法。 <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> 傳回 `Stream` 或周圍的執行 `PipeReader` `PipeWriter` 。

### <a name="stream-example"></a>資料流程範例

`PipeReader` 您 `PipeWriter` 可以使用靜態方法來建立和實例，並 `Create` 指定 <xref:System.IO.Stream> 物件和選擇性的對應建立選項。

可 <xref:System.IO.Pipelines.StreamPipeReaderOptions> 讓您控制如何 `PipeReader` 使用下列參數來建立實例：

- <xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> 這是從集區租用記憶體時所使用的最小緩衝區大小（以位元組為單位），預設為 `4096` 。
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> 旗標會決定基礎資料流程是否在完成之後保持開啟 `PipeReader` ，而且預設為 `false` 。
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> 表示在配置新的緩衝區之前，緩衝區中剩餘位元組的臨界值，預設為 `1024` 。
- <xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> 是在配置 `MemoryPool<byte>` 記憶體時使用，而且預設為 `null` 。

可 <xref:System.IO.Pipelines.StreamPipeWriterOptions> 讓您控制如何 `PipeWriter` 使用下列參數來建立實例：

- <xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> 旗標會決定基礎資料流程是否在完成之後保持開啟 `PipeWriter` ，而且預設為 `false` 。
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> 表示從租借記憶體時要使用的最小緩衝區大小 <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> ，並且預設為 `4096` 。
- <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> 是在配置 `MemoryPool<byte>` 記憶體時使用，而且預設為 `null` 。

> [!IMPORTANT]
> `PipeReader` `PipeWriter` 使用方法建立和實例時 `Create` ，您必須考慮 `Stream` 物件存留期。 如果您需要在讀取器或寫入器完成後才能存取資料流程，您必須 `LeaveOpen` `true` 在建立選項上將旗標設為。 否則，資料流程將會關閉。

下列程式碼示範如何 `PipeReader` `PipeWriter` 使用來自資料流程的方法來建立和實例 `Create` 。

:::code language="csharp" source="snippets/pipelines/Program.cs":::

應用程式會使用將 <xref:System.IO.StreamReader> *lorem-ipsum.txt* 檔案讀取為數據流。 <xref:System.IO.FileStream>會傳遞至，以具現 <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> 化 `PipeReader` 物件。 然後，主控台應用程式會將其標準輸出資料流程傳遞至 <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> 使用 <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> 。 此範例支援 [取消](#cancellation)。
