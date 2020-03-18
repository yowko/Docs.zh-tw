---
title: I/O 管道 - .NET
description: 瞭解如何在 .NET 中有效地使用 I/O 管道，並避免代碼中的問題。
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: b18b2bf31787fa58e614cd4f057fba9037fe8ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627548"
---
# <a name="systemiopipelines-in-net"></a>系統.IO.管道在 .NET 中

<xref:System.IO.Pipelines>是一個新的庫，旨在使在 .NET 中更輕鬆地執行高性能 I/O。 它是面向 .NET 標準的庫，適用于所有 .NET 實現。

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>系統.IO.管道解決了什麼問題

<!-- corner case doesn't MT (machine translate)   -->
分析流資料的應用由具有許多專用和異常代碼流的樣板代碼組成。 樣板和特殊情況碼複雜且難以維護。

`System.IO.Pipelines`被設計為：

* 具有高性能分析流資料。
* 降低代碼複雜性。

以下代碼對於從用戶端接收行分隔消息（由`'\n'`） 分隔的 TCP 伺服器而言是典型的：

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

前面的代碼有幾個問題：

* 在單個調用`ReadAsync`中可能不會接收整個消息（行尾）。
* 它忽略了 的結果`stream.ReadAsync`。 `stream.ReadAsync`返回讀取的資料量。
* 它不處理在單個`ReadAsync`調用中讀取多行的情況。
* 它分配一個`byte`包含每個讀取的陣列。

要修復上述問題，需要進行以下更改：

* 緩衝傳入資料，直到找到新行。
* 分析緩衝區中返回的所有行。
* 該行可能大於 1 KB（1024 位元組）。 代碼需要調整輸入緩衝區的大小，直到找到分隔符號，以便適合緩衝區內的完整行。

  * 如果調整緩衝區大小，則隨著輸入中顯示的長行，將會有更多的緩衝區副本。
  * 為了減少浪費的空間，請壓縮用於讀取線的緩衝區。

* 請考慮使用緩衝集區以避免重複分配記憶體。
* 以下代碼解決了其中一些問題：

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

前面的代碼很複雜，不能解決所有已識別的問題。 高性能網路通常意味著編寫非常複雜的代碼以最大限度地提高性能。 `System.IO.Pipelines`旨在使編寫此類代碼更容易。

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a>Pipe

類<xref:System.IO.Pipelines.Pipe>可用於創建對`PipeWriter/PipeReader`。 寫入 的`PipeWriter`所有資料均位於 ： `PipeReader`

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>管道基本用法

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

有兩個迴圈：

* `FillPipeAsync`從 讀取`Socket`並寫入`PipeWriter`。
* `ReadPipeAsync`從`PipeReader`讀取 和 解析傳入行。

沒有分配顯式緩衝區。 所有緩衝區管理都委派給`PipeReader`和`PipeWriter`實現。 委派緩衝區管理使使用代碼更容易只關注業務邏輯。

在第一個迴圈中：

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>調用 以從基礎寫入器獲取記憶體。
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>調用 以告訴寫入`PipeWriter`緩衝區的資料量。
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>調用 以使資料可供 。 `PipeReader`

在第二個迴圈中，`PipeReader`使用 由 編寫的`PipeWriter`緩衝區。 緩衝區來自通訊端。 調用`PipeReader.ReadAsync`：

* 返回包含<xref:System.IO.Pipelines.ReadResult>兩條重要資訊的 返回 ：

  * 以 的 讀取形式的資料`ReadOnlySequence<byte>`。
  * 一個布林`IsCompleted`，指示是否已達到資料結束 （EOF）。

找到行的末尾 （EOL） 分隔符號並分析行後：

* 邏輯處理緩衝區以跳過已處理的內容。
* `PipeReader.AdvanceTo`調用 以告訴已`PipeReader`消耗和檢查的資料量。

讀取器和編寫器通過調用`Complete`結束。 `Complete`允許基礎管道釋放它分配的記憶體。

### <a name="backpressure-and-flow-control"></a>背壓力和流量控制

理想情況下，閱讀和分析協同工作：

* 編寫執行緒使用來自網路的資料並將其放入緩衝區中。
* 分析執行緒負責構造適當的資料結構。

通常，分析需要比從網路複製資料塊更多的時間：

* 讀取執行緒先于解析執行緒。
* 讀取執行緒必須減慢速度或分配更多記憶體以存儲分析執行緒的資料。

為了獲得最佳性能，在頻繁暫停和分配更多記憶體之間具有平衡。

要解決上述問題，有`Pipe`兩個設置來控制資料流程：

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>：確定在調用暫停<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>之前應緩衝多少資料。
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>：確定讀取器在調用恢復`PipeWriter.FlushAsync`之前必須觀察的資料量。

![具有恢復寫入器閾值和暫停寫入器閾值的圖表](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* 當`ValueTask<FlushResult>``Pipe`中的資料量交叉`PauseWriterThreshold`時返回不完整。
* `ValueTask<FlushResult>`當它低於`ResumeWriterThreshold`時完成。

兩個值用於防止快速迴圈，如果使用一個值，則可能發生此迴圈。

### <a name="examples"></a>範例

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>管道調度器

通常，當`async``await`使用 和 時，非同步代碼在<xref:System.Threading.Tasks.TaskScheduler>上 或<xref:System.Threading.SynchronizationContext>上繼續在當前 上。

執行 I/O 時，對執行 I/O 的位置進行細細微性控制非常重要。 此控制項允許有效地利用 CPU 緩存。 對於 Web 服務器等高性能應用，高效緩存至關重要。 <xref:System.IO.Pipelines.PipeScheduler>提供對非同步回檔運行位置的控制。 依照預設：

* 使用電流<xref:System.Threading.SynchronizationContext>。
* 如果沒有`SynchronizationContext`，則使用執行緒池運行回檔。

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[Pipe計畫.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool)是佇列<xref:System.IO.Pipelines.PipeScheduler>回檔到執行緒池的實現。 `PipeScheduler.ThreadPool`是預設值，通常是最佳選擇。 [Pipe計畫.內聯](xref:System.IO.Pipelines.PipeScheduler.Inline)可能會導致意外的後果，如鎖死。

### <a name="pipe-reset"></a>管道重定

重用`Pipe`物件通常很高效。 要重置管道，請當<xref:System.IO.Pipelines.PipeReader><xref:System.IO.Pipelines.Pipe.Reset%2A>`PipeReader`和`PipeWriter`都已完成時調用。

## <a name="pipereader"></a>管道閱讀器

<xref:System.IO.Pipelines.PipeReader>代表調用方管理記憶體。 **通話**後<xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType>始終呼叫<xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>。 這樣可以`PipeReader`知道調用方何時使用記憶體完成，以便可以跟蹤它。 返回`ReadOnlySequence<byte>``PipeReader.ReadAsync`的僅在調用 之前`PipeReader.AdvanceTo`有效。 調用`ReadOnlySequence<byte>``PipeReader.AdvanceTo`後使用是違法的。

`PipeReader.AdvanceTo`採用兩<xref:System.SequencePosition>個參數：

* 第一個參數確定消耗了多少記憶體。
* 第二個參數確定觀察到的緩衝區量。

將資料標記為已使用意味著管道可以將記憶體返回到基礎緩衝集區。 將資料標記為觀察控制下一次調用`PipeReader.ReadAsync`執行。 將所有內容標記為已觀察到，這意味著在下一`PipeReader.ReadAsync`個調用之前不會返回，直到有更多的資料寫入管道。 任何其他值都將發出下一個調用，`PipeReader.ReadAsync`以便立即返回觀測*和*未觀測的資料，但資料已使用。

### <a name="read-streaming-data-scenarios"></a>讀取流資料方案

嘗試讀取流資料時會出現幾個典型模式：

* 給定資料流程，解析單個消息。
* 給定資料流程，解析所有可用消息。

以下示例使用`TryParseMessage`方法分析 來自`ReadOnlySequence<byte>`的消息。 `TryParseMessage`分析單個消息並更新輸入緩衝區以修剪緩衝區中分析的消息。 `TryParseMessage`不是 .NET 的一部分，它是以下部分中使用的使用者書面方法。

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>閱讀一條消息

以下代碼從 讀取單個消息`PipeReader`並將其返回給調用方。

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

上述程式碼：

* 分析單個消息。
* 更新已使用`SequencePosition`並檢查`SequencePosition`的已用值，以指向修剪的輸入緩衝區的開始。

這兩`SequencePosition`個參數將更新，`TryParseMessage`因為從輸入緩衝區中刪除解析的消息。 通常，當分析來自緩衝區的單個消息時，檢查的位置應為以下位置之一：

* 消息的結尾。
* 如果未找到消息，則接收緩衝區的末尾。

單個消息大小寫最有可能出錯。 傳遞錯誤的值*以檢查*可能會導致記憶體不足異常或無限迴圈。 有關詳細資訊，請參閱本文中的[PipeReader 常見問題](#gotchas)部分。

### <a name="reading-multiple-messages"></a>讀取多條消息

以下代碼從 讀取`PipeReader`所有消息，並`ProcessMessageAsync`調用每個消息。

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>取消

`PipeReader.ReadAsync`:

* 支援傳遞<xref:System.Threading.CancellationToken>。
* 在讀取<xref:System.OperationCanceledException>掛起時`CancellationToken`引發 如果 已取消 。
* 支援通過 取消當前讀取操作的方法<xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>，以避免引發異常。 調用`PipeReader.CancelPendingRead`會導致當前或下一個調用`PipeReader.ReadAsync`返回 與<xref:System.IO.Pipelines.ReadResult>`IsCanceled`設置為`true`的 調用 。 這對於以非破壞性和非特殊方式停止現有讀取迴圈非常有用。

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>管道閱讀器常見問題

* 將錯誤值傳遞給`consumed`或`examined`可能導致讀取已讀取的資料。
* 通過`buffer.End`檢查可能導致：

  * 停滯的資料
  * 如果未消耗資料，則可能是最終記憶體不足 （OOM） 異常。 例如，`PipeReader.AdvanceTo(position, buffer.End)`當一次從緩衝區處理一條消息時。

* 將錯誤值傳遞給`consumed`或`examined`可能會導致無限迴圈。 例如，`PipeReader.AdvanceTo(buffer.Start)`如果`buffer.Start`尚未更改，將導致下一個調用`PipeReader.ReadAsync`在新資料到達之前立即返回。
* 將錯誤值傳遞給`consumed`或`examined`可能導致無限緩衝（最終 OOM）。
* 使用`ReadOnlySequence<byte>`後調用`PipeReader.AdvanceTo`可能會導致記憶體損壞（空閒後使用）。
* 無法調用`PipeReader.Complete/CompleteAsync`可能會導致記憶體洩漏。
* 在處理<xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType>緩衝區之前檢查和退出讀取邏輯會導致資料丟失。 環路允出準則應基於`ReadResult.Buffer.IsEmpty`和`ReadResult.IsCompleted`。 這樣做不正確可能會導致無限迴圈。

#### <a name="problematic-code"></a>有問題的代碼

❌**資料丟失**

當`ReadResult`設置為 時`IsCompleted`，可以返回資料的最後一段`true`。 在退出讀取迴圈之前不讀取該資料將導致資料丟失。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**無限迴圈**

如果 是`true`，則以下邏輯可能會導致無限迴圈，`Result.IsCompleted`但緩衝區中從未包含完整的消息。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

下面是另一個具有相同問題的代碼。 在檢查`ReadResult.IsCompleted`之前，它正在檢查非空緩衝區。 因為它在`else if`中，如果緩衝區中永遠不會有完整的消息，它將永遠迴圈。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**意外掛起**

在分析`PipeReader.AdvanceTo`單個`buffer.End`消息時`examined`，無條件調用 該位置可能會導致掛起。 下一個調用`PipeReader.AdvanceTo`不會返回，直到：

* 寫入管道的資料更多。
* 並且以前沒有檢查過新資料。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**記憶體不足 （OOM）**

在以下情況下，以下代碼會一直緩衝，直到發生<xref:System.OutOfMemoryException>：

* 沒有最大消息大小。
* 從 返回`PipeReader`的資料不會發出完整的消息。 例如，它不發出完整的消息，因為另一方正在編寫大型消息（例如，4 GB 消息）。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌**記憶體損壞**

編寫讀取緩衝區的説明器時，應在調用`Advance`之前複製任何返回的有效負載。 下面的示例將返回`Pipe`已丟棄的記憶體，並可能將其重新用於下一個操作（讀取/寫入）。

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>管道作家

<xref:System.IO.Pipelines.PipeWriter>管理緩衝區，用於代表調用方進行寫入。 `PipeWriter`實現[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)器 。 `IBufferWriter<byte>`無需其他緩衝區副本即可訪問緩衝區以執行寫入。

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

前面的代碼：

* 從 using<xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>請求至少 5 個位元組`PipeWriter`的緩衝區。
* 將 ASCII 字串`"Hello"`的位元組寫入返回`Memory<byte>`的 。
* 調用<xref:System.IO.Pipelines.PipeWriter.Advance%2A>以指示寫入緩衝區的位元組數。
* 刷新 將`PipeWriter`位元組發送到基礎設備的 刷新 。

前面的寫入方法使用 提供的緩衝區`PipeWriter`。 或者， <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>：

* 將現有緩衝區複製到 。 `PipeWriter`
* 調用`GetSpan`，`Advance`並根據需要調用<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>。

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>取消

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>支援傳遞<xref:System.Threading.CancellationToken>. 如果在刷新`CancellationToken`掛起時取消權杖，則在 中傳遞結果。 `OperationCanceledException` `PipeWriter.FlushAsync`支援通過<xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType>不引發異常來取消當前刷新操作的方法。 調用`PipeWriter.CancelPendingFlush`會導致當前或下一個調用`PipeWriter.FlushAsync`到`PipeWriter.WriteAsync`或<xref:System.IO.Pipelines.FlushResult>將`IsCanceled`設置為`true`返回 。 這對於以非破壞性和非特殊方式停止屈服沖洗非常有用。

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>管道編寫器常見問題

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>並<xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>返回至少具有請求記憶體量的緩衝區。 **不要**假定確切的緩衝區大小。
* 不能保證連續調用將返回相同的緩衝區或相同大小的緩衝區。
* 調用<xref:System.IO.Pipelines.PipeWriter.Advance%2A>後必須請求新的緩衝區以繼續寫入更多資料。 無法寫入以前獲取的緩衝區。
* 呼叫`GetMemory`或`GetSpan`呼叫不完整`FlushAsync`時不安全。
* 調用`Complete`或`CompleteAsync`未刷新資料時可能會導致記憶體損壞。

## <a name="iduplexpipe"></a>I雙工管

<xref:System.IO.Pipelines.IDuplexPipe>是支援讀取和寫入的類型的協定。 例如，網路連接將由 表示`IDuplexPipe`。

 與`Pipe`包含 和`PipeReader`a `PipeWriter` `IDuplexPipe`不同，表示全雙工連接的單一側。 這意味著寫入`PipeWriter`的內容不會從 讀取`PipeReader`。

## <a name="streams"></a>資料流

讀取或寫入流資料時，通常使用去序列化器讀取資料並使用序列化器寫入資料。 這些讀取和寫入流 API 大多具有參數`Stream`。 為了更輕鬆地與這些現有 API 集成，`PipeReader`並`PipeWriter`公開 。 <xref:System.IO.Pipelines.PipeReader.AsStream%2A>  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A>返回`Stream`圍繞`PipeReader`的`PipeWriter`實現。
