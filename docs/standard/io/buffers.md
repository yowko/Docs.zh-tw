---
title: System.object-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: e42f165bfedec3b1fa54615ee7e2a2028f40aadb
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960492"
---
# <a name="work-with-buffers-in-net"></a>在 .NET 中使用緩衝區

本文概述可協助讀取跨多個緩衝區執行之資料的類型。 它們主要是用來支援 <xref:System.IO.Pipelines.PipeReader> 物件。

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> 是同步緩衝寫入的合約。 在最低層級，介面：

- 是基本且不容易使用。
- 允許存取 <xref:System.Memory%601> 或 <xref:System.Span%601>。 `Memory<T>` 或 `Span<T>` 可以寫入，而且您可以判斷寫入多少 `T` 專案。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

上述方法：

- 使用 `GetSpan(5)`從 `IBufferWriter<byte>` 要求至少有5個位元組的緩衝區。
- 將 ASCII 字串 "Hello" 的位元組寫入傳回的 `Span<byte>`。
- 呼叫 <xref:System.Buffers.IBufferWriter%601> 以指出寫入緩衝區的位元組數目。

這種寫入方法會使用 `IBufferWriter<T>`所提供的 `Memory<T>`/`Span<T>` 緩衝區。 或者，也可以使用 <xref:System.Buffers.BuffersExtensions.Write%2A> 擴充方法，將現有的緩衝區複製到 `IBufferWriter<T>`。 `Write` 會適當地呼叫 `GetSpan`/`Advance` 的工作，因此在撰寫之後，不需要呼叫 `Advance`：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601> 是執行的 `IBufferWriter<T>`，其備份存放區是單一連續陣列。

### <a name="ibufferwriter-common-problems"></a>IBufferWriter 常見的問題

- `GetSpan` 和 `GetMemory` 會傳回至少具有所需記憶體數量的緩衝區。 請不要採用確切的緩衝區大小。
- 不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。
- 呼叫 `Advance` 之後，必須要求新的緩衝區，才能繼續寫入更多資料。 呼叫 `Advance` 之後，無法將先前取得的緩衝區寫入。

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence 會以管道顯示記憶體，並在該順序位置的唯讀記憶體](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601> 是一種結構，可以代表連續或不連續的 `T`序列。 它可以從下列結構來進行：

1. `T[]`
1. `ReadOnlyMemory<T>`
1. 一對連結的清單節點 <xref:System.Buffers.ReadOnlySequenceSegment%601> 和索引，代表序列的開始和結束位置。

第三個表示是最有趣的一種，因為它對 `ReadOnlySequence<T>`上的各種作業有效能上的影響：

|Representation|運算|複雜性|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

由於這種混合標記法，`ReadOnlySequence<T>` 會將索引公開為 `SequencePosition` 而不是整數。 `SequencePosition`：

- 是不透明的值，代表其來源之 `ReadOnlySequence<T>` 的索引。
- 由兩個部分組成：整數和物件。 這兩個值所代表的內容會系結至 `ReadOnlySequence<T>`的執行。

### <a name="access-data"></a>存取資料

`ReadOnlySequence<T>` 會將資料公開為 `ReadOnlyMemory<T>`的可列舉。 您可以使用基本的 foreach 來列舉每個區段：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

上述方法會在每個區段中搜尋特定的位元組。 如果您需要追蹤每個區段的 `SequencePosition`，<xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> 較為適當。 下一個範例會變更上述程式碼，以傳回 `SequencePosition` 而不是整數。 傳回 `SequencePosition` 有一個優點，就是允許呼叫者避免第二次掃描取得特定索引的資料。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

`SequencePosition` 和 `TryGet` 的組合，其作用就像列舉值。 [位置] 欄位會在每個反復專案開始時修改，以開始 `ReadOnlySequence<T>`中的每個區段。

先前的方法會以 `ReadOnlySequence<T>`上的擴充方法形式存在。 <xref:System.Buffers.BuffersExtensions.PositionOf%2A> 可以用來簡化上述程式碼：

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>處理 ReadOnlySequence\<T\>

處理 `ReadOnlySequence<T>` 可能很具挑戰性，因為資料可能會分割成序列內的多個區段。 為了達到最佳效能，請將程式碼分成兩個路徑：

- 處理單一區段案例的快速路徑。
- 處理跨區段分割之資料的緩慢路徑。

有幾種方法可以用來處理多分割序列中的資料：

- 使用[`SequenceReader<T>`](#sequencereadert)。
- 依區段剖析資料區段，追蹤區段中的 `SequencePosition` 和索引。 這可避免不必要的配置，但可能沒有效率，特別是針對小型緩衝區。
- 將 `ReadOnlySequence<T>` 複製到連續的陣列，並將它視為單一緩衝區：
  - 如果 `ReadOnlySequence<T>` 的大小很小，使用[stackalloc](../../csharp/language-reference/operators/stackalloc.md)運算子將資料複製到堆疊配置的緩衝區可能會是合理的。
  - 使用 <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>將 `ReadOnlySequence<T>` 複製到集區陣列。
  - 使用 [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A)。 在最忙碌的路徑中，不建議使用這種方式，因為它會在堆積上配置新的 `T[]`。

下列範例示範處理 `ReadOnlySequence<byte>`的一些常見案例：

##### <a name="process-binary-data"></a>處理二進位資料

下列範例會從 `ReadOnlySequence<byte>`的開頭剖析4個位元組的大序整數長度。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

##### <a name="process-text-data"></a>處理文字資料

下列範例︰

- 尋找 `ReadOnlySequence<byte>` 中的第一個分行符號（`\r\n`），並透過 out ' line ' 參數傳回它。
- 修剪該行，排除輸入緩衝區中的 `\r\n`。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>空白區段

將空的區段儲存在 `ReadOnlySequence<T>`內是有效的。 明確列舉區段時，可能會發生空的區段：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

上述程式碼會建立具有空白區段的 `ReadOnlySequence<byte>`，並顯示這些空白區段如何影響各種 Api：

- `SequencePosition` 指向空白區段的 `ReadOnlySequence<T>.Slice` 會保留該區段。
- 具有 int 的 `ReadOnlySequence<T>.Slice` 會略過空的區段。
- 列舉 `ReadOnlySequence<T>` 列舉空的區段。

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>ReadOnlySequence\<T > 和 SequencePosition 的潛在問題

處理 `ReadOnlySequence<T>`/`SequencePosition` 和一般 `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/時，會出現幾個不尋常的結果：

- `SequencePosition` 是特定 `ReadOnlySequence<T>`的位置標記，而不是絕對位置。 由於它是相對於特定的 `ReadOnlySequence<T>`，因此如果在其來源的 `ReadOnlySequence<T>` 之外使用，則不會有意義。
- 無法在沒有 `ReadOnlySequence<T>`的 `SequencePosition` 上執行算術。 這表示 `position++` 撰寫 `ReadOnlySequence<T>.GetPosition(position, 1)`的基本事項。
- `GetPosition(long)` 不**支援負**索引。 這表示無法取得第二個到最後一個字元，而不需要流覽所有區段。
- 無法比較兩個 `SequencePosition`，因此很難以：
  - 知道某個位置是否大於或小於另一個位置。
  - 撰寫一些剖析演算法。
- `ReadOnlySequence<T>` 大於物件參考，而且應該在可能的情況下，[以](../../csharp/language-reference/keywords/in-parameter-modifier.md)或[ref](../../csharp/language-reference/keywords/ref.md)傳遞。 `in` 或 `ref` 傳遞 `ReadOnlySequence<T>`，會減少[結構](../../csharp/language-reference/keywords/struct.md)的複本。
- 空白區段：
  - 在 `ReadOnlySequence<T>`內有效。
  - 重複使用 `ReadOnlySequence<T>.TryGet` 方法時，可能會出現。
  - 可以使用具有 `SequencePosition` 物件的 `ReadOnlySequence<T>.Slice()` 方法，以配量順序。

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- 是 .NET Core 3.0 中引進的新類型，可簡化 `ReadOnlySequence<T>`的處理。
- 將單一區段 `ReadOnlySequence<T>` 和多區段 `ReadOnlySequence<T>`之間的差異統一。
- 提供協助程式來讀取不一定會在區段之間分割的二進位和文字資料（`byte` 和 `char`）。

有內建方法可處理二進位和分隔的資料。 下一節將示範這些相同的方法與 `SequenceReader<T>`的相似之處：

### <a name="access-data"></a>存取資料

`SequenceReader<T>` 有方法可以直接列舉 `ReadOnlySequence<T>` 內部的資料。 下列程式碼是一次處理 `byte` `ReadOnlySequence<byte>` 的範例：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

`CurrentSpan` 會公開目前區段的 `Span`，這類似于在方法中手動執行的作業。

### <a name="use-position"></a>使用位置

下列程式碼是使用 `SequenceReader<T>``FindIndexOf` 的範例執行：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>處理二進位資料

下列範例會從 `ReadOnlySequence<byte>`的開頭剖析4個位元組的大序整數長度。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>處理文字資料

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<T\> 常見的問題

- 因為 `SequenceReader<T>` 是可變動的結構，所以一定要以傳[址](../../csharp/language-reference/keywords/ref.md)方式傳遞。
- `SequenceReader<T>` 是[ref 結構](../../csharp/language-reference/keywords/ref.md#ref-struct-types)，因此它只能用於同步方法中，而且不能儲存在欄位中。 如需詳細資訊，請參閱[撰寫安全C#且有效率](../../csharp/write-safe-efficient-code.md)的程式碼。
- `SequenceReader<T>` 已優化，可做為順向讀取器使用。 `Rewind` 適用于無法使用其他 `Read`、`Peek`和 `IsNext` Api 來解決的小型備份。
