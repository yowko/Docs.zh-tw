---
title: 系統.緩衝區 - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: f939164cd56b2fb2feeeb171236b0e1171327e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160114"
---
# <a name="work-with-buffers-in-net"></a>使用 .NET 中的緩衝區

本文概述了説明讀取跨多個緩衝區運行的資料的類型。 它們主要用於支援<xref:System.IO.Pipelines.PipeReader>物件。

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>是同步緩衝寫入的協定。 在最低級別，介面：

- 是基本的，使用起來並不難。
- 允許訪問 或<xref:System.Memory%601><xref:System.Span%601>。 或 可以寫入，您可以確定寫入的專案數`T` `Memory<T>` `Span<T>`

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

上述方法：

- 從 using`GetSpan(5)`請求至少 5 個位元組`IBufferWriter<byte>`的緩衝區。
- 將 ASCII 字串"Hello"的位元組寫入返回`Span<byte>`的 。
- 調用<xref:System.Buffers.IBufferWriter%601>以指示寫入緩衝區的位元組數。

這種書寫`Memory<T>`/`Span<T>`方法使用 提供的緩衝區`IBufferWriter<T>`。 或者，<xref:System.Buffers.BuffersExtensions.Write%2A>擴充方法可用於將現有緩衝區複製到 。 `IBufferWriter<T>` `Write`是否`GetSpan`/`Advance`根據需要調用工作，因此無需在編寫後調用`Advance`：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>是 其備份`IBufferWriter<T>`存儲是單個連續陣列的實現。

### <a name="ibufferwriter-common-problems"></a>IBufferWriter 常見問題

- `GetSpan`並`GetMemory`返回至少具有請求記憶體量的緩衝區。 不要假定確切的緩衝區大小。
- 不能保證連續調用將返回相同的緩衝區或相同大小的緩衝區。
- 調用`Advance`後必須請求新的緩衝區以繼續寫入更多資料。 調用後`Advance`無法將以前獲取的緩衝區寫入。

## <a name="readonlysequencet"></a>唯讀序列\<T\>

![ReadOnlySequence 在管道中顯示記憶體，低於唯讀記憶體的序列位置](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>是一個結構，可以表示 的連續序列或不連續序列`T`。 它可以從：

1. `T[]`。
1. `ReadOnlyMemory<T>`。
1. 一對連結清單節點<xref:System.Buffers.ReadOnlySequenceSegment%601>和索引，用於表示序列的開始和結束位置。

第三個表示形式是最有趣的，因為它對 ： `ReadOnlySequence<T>`

|表示法|作業|複雜度|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

由於這種混合表示形式，`ReadOnlySequence<T>`公開索引不是`SequencePosition`整數。 A `SequencePosition`：

- 是表示索引到其發源地的`ReadOnlySequence<T>`不透明值。
- 由兩個部分組成，一個整數和一個物件。 這兩個值表示的內容與 的`ReadOnlySequence<T>`實現相關聯。

### <a name="access-data"></a>存取資料

公開`ReadOnlySequence<T>`資料作為 的`ReadOnlyMemory<T>`枚舉。 可以使用基本功能枚舉每個段進行枚舉：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

前面的方法搜索每個段以尋找特定的位元組。 如果需要跟蹤每個段的`SequencePosition`，<xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType>則更合適。 下一個示例將前面的代碼更改為返回`SequencePosition`而不是整數。 返回`SequencePosition`a 的好處是允許調用方避免第二次掃描以獲取特定索引上的資料。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

和`TryGet`的組合`SequencePosition`類似于枚舉器。 位置欄位在每次反覆運算開始時被修改為 中每個段的開始`ReadOnlySequence<T>`。

前面的方法作為擴充方法存在於 上`ReadOnlySequence<T>`。 <xref:System.Buffers.BuffersExtensions.PositionOf%2A>可用於簡化前面的代碼：

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>處理唯讀序列\<T\>

處理`ReadOnlySequence<T>`可能具有挑戰性，因為資料可能會跨序列中的多個段拆分。 為了獲得最佳性能，請將代碼拆分為兩個路徑：

- 處理單個段案例的快速路徑。
- 處理跨段拆分的資料的慢速路徑。

有幾種方法可用於處理多分段序列中的資料：

- 使用[`SequenceReader<T>`](#sequencereadert)。
- 按段分析資料段，跟蹤所分析的段`SequencePosition`內的 和 索引。 這樣可以避免不必要的分配，但效率可能很低，尤其是對於小型緩衝區。
- 將`ReadOnlySequence<T>`複製到連續陣列並將其視為單個緩衝區：
  - 如果 的大小`ReadOnlySequence<T>`較小，則使用[stackalloc](../../csharp/language-reference/operators/stackalloc.md)運算子將資料複製到堆疊分配的緩衝區可能是合理的。
  - 使用`ReadOnlySequence<T>`將 複製到池陣列中<xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>。
  - 使用[`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A)。 在熱路徑中不建議這樣做，因為它在堆上分配了`T[]`一個新的。

以下示例演示了一些用於處理`ReadOnlySequence<byte>`的常見案例：

##### <a name="process-binary-data"></a>處理二進位資料

下面的示例從 開始分析 4 位元組的大位元組整數長度`ReadOnlySequence<byte>`。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>處理文本資料

下列範例將：

- 在 中找到 中的第`\r\n`一個折`ReadOnlySequence<byte>`線 （ ）， 並通過 out"行"參數返回它。
- 修剪該行，不包括輸入緩衝區`\r\n`中的 。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>空段

將空段存儲在 中是有效的`ReadOnlySequence<T>`。 顯式枚舉段時可能會出現空段：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

前面的代碼創建具有空`ReadOnlySequence<byte>`段的 ，並顯示這些空段如何影響各種 API：

- `ReadOnlySequence<T>.Slice`指向`SequencePosition`空段的點將保留該段。
- `ReadOnlySequence<T>.Slice`帶 int 跳過空段。
- 枚舉枚`ReadOnlySequence<T>`舉空段。

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>ReadOnly序列\<T>和序列位置的潛在問題

處理`ReadOnlySequence<T>`/`SequencePosition`正常`ReadOnlySpan<T>`/`ReadOnlyMemory<T>`與/，有幾個不尋常的`int`結果： `T[]` /

- `SequencePosition`是特定`ReadOnlySequence<T>`位置（而不是絕對位置）的位置標記。 因為它相對於特定`ReadOnlySequence<T>`，如果使用它的來源之外，`ReadOnlySequence<T>`它沒有意義。
- 沒有 無法對`SequencePosition`執行算術。 `ReadOnlySequence<T>` 這意味著做基本的事情，如`position++`寫`ReadOnlySequence<T>.GetPosition(position, 1)`。
- `GetPosition(long)`不支援**負**索引。 這意味著，如果不走遍所有段，就不可能獲得第二個到最後一個字元。
- 兩`SequencePosition`個無法比較，因此很難：
  - 瞭解一個位置是否大於或小於另一個位置。
  - 編寫一些分析演算法。
- `ReadOnlySequence<T>`大於物件引用，應盡可能通過[in](../../csharp/language-reference/keywords/in-parameter-modifier.md)或[ref](../../csharp/language-reference/keywords/ref.md)傳遞。 傳遞`ReadOnlySequence<T>``in`或`ref`減少[結構](../../csharp/language-reference/builtin-types/struct.md)的副本。
- 空段：
  - 在 中有效`ReadOnlySequence<T>`。
  - 可以使用`ReadOnlySequence<T>.TryGet`方法反覆運算時顯示。
  - 可以使用 方法`ReadOnlySequence<T>.Slice()`與物件一起`SequencePosition`切片序列。

## <a name="sequencereadert"></a>序列閱讀器\<T\>

<xref:System.Buffers.SequenceReader%601>:

- 是 .NET Core 3.0 中引入的一種新類型，用於`ReadOnlySequence<T>`簡化 的處理。
- 將單個段和多段`ReadOnlySequence<T>``ReadOnlySequence<T>`之間的差異一起。
- 提供用於讀取二進位和文本資料 （`byte` `char`和 ） 的説明器，這些資料和文本資料可能跨段拆分，也可能不拆分。

有處理二進位和分隔資料的內置方法。 以下部分演示了這些相同的方法與 ： `SequenceReader<T>`

### <a name="access-data"></a>存取資料

`SequenceReader<T>`具有直接枚舉資料`ReadOnlySequence<T>`的方法。 以下代碼是一次處理 a`ReadOnlySequence<byte>``byte`的示例：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

公開`CurrentSpan`當前段的`Span`，這與手動在方法中執行的內容類別似。

### <a name="use-position"></a>使用位置

以下代碼是使用 的示例`FindIndexOf`實現： `SequenceReader<T>`

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>處理二進位資料

下面的示例從 開始分析 4 位元組的大位元組整數長度`ReadOnlySequence<byte>`。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>處理文本資料

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>序列閱讀器\< \> T 常見問題

- 因為它是`SequenceReader<T>`可變結構，它應始終通過[引用](../../csharp/language-reference/keywords/ref.md)傳遞。
- `SequenceReader<T>`是一個[ref 結構](../../csharp/language-reference/keywords/ref.md#ref-struct-types)，因此它只能在同步方法中使用，並且不能存儲在欄位中。 有關詳細資訊，請參閱[編寫安全高效的 C# 代碼](../../csharp/write-safe-efficient-code.md)。
- `SequenceReader<T>`經過優化，可用作僅轉發讀取器。 `Rewind`用於使用其他`Read`無法使用 和`Peek` `IsNext` API 解決的小型備份。
