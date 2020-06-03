---
title: System.object-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739618"
---
# <a name="work-with-buffers-in-net"></a>在 .NET 中使用緩衝區

本文概述可協助讀取跨多個緩衝區執行之資料的類型。 它們主要是用來支援 <xref:System.IO.Pipelines.PipeReader> 物件。

## <a name="ibufferwritert"></a>IBufferWriter \< T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>這是同步緩衝寫入的合約。 在最低層級，介面：

- 是基本且不容易使用。
- 允許存取 <xref:System.Memory%601> 或 <xref:System.Span%601> 。 `Memory<T>`或 `Span<T>` 可寫入，而且您可以判斷寫入的專案數 `T` 。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

上述方法：

- 使用從要求至少有5個位元組的緩衝區 `IBufferWriter<byte>` `GetSpan(5)` 。
- 將 ASCII 字串 "Hello" 的位元組寫入傳回的 `Span<byte>` 。
- 呼叫 <xref:System.Buffers.IBufferWriter%601> 以指出寫入緩衝區的位元組數目。

這種寫入方法會使用所 `Memory<T>` / `Span<T>` 提供的緩衝區 `IBufferWriter<T>` 。 或者，您也 <xref:System.Buffers.BuffersExtensions.Write%2A> 可以使用擴充方法，將現有的緩衝區複製到 `IBufferWriter<T>` 。 `Write`會執行適當呼叫的工作 `GetSpan` / `Advance` ，因此不需要 `Advance` 在撰寫後呼叫：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>是的實作為 `IBufferWriter<T>` 其備份存放區是單一連續陣列。

### <a name="ibufferwriter-common-problems"></a>IBufferWriter 常見的問題

- `GetSpan`和會傳回 `GetMemory` 至少具有所需記憶體數量的緩衝區。 請不要採用確切的緩衝區大小。
- 不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。
- 呼叫之後，必須要求新的緩衝區 `Advance` ，才能繼續寫入更多資料。 呼叫之後，無法將先前取得的緩衝區寫入 `Advance` 。

## <a name="readonlysequencet"></a>ReadOnlySequence \< T\>

![ReadOnlySequence 會以管道顯示記憶體，並在該順序位置的唯讀記憶體](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>是可以代表連續或非連續序列的結構 `T` 。 它可以從下列結構來進行：

1. `T[]`。
1. `ReadOnlyMemory<T>`。
1. 一對連結清單節點 <xref:System.Buffers.ReadOnlySequenceSegment%601> 和索引，代表序列的開始和結束位置。

第三個表示是最有趣的一種，因為它對上的各種作業有效能上的影響 `ReadOnlySequence<T>` ：

|表示法|操作|複雜度|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

由於這種混合標記法，會將 `ReadOnlySequence<T>` 索引公開為， `SequencePosition` 而不是整數。 答 `SequencePosition` ：

- 是不透明的值，表示 `ReadOnlySequence<T>` 其來源位置的索引。
- 由兩個部分組成：整數和物件。 這兩個值所代表的內容會系結至的執行 `ReadOnlySequence<T>` 。

### <a name="access-data"></a>存取資料

會將 `ReadOnlySequence<T>` 資料公開為的可列舉 `ReadOnlyMemory<T>` 。 您可以使用基本的 foreach 來列舉每個區段：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

上述方法會在每個區段中搜尋特定的位元組。 如果您需要追蹤每個區段的 `SequencePosition` ， <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> 更適合。 下一個範例會變更上述程式碼，以傳回 `SequencePosition` 而不是整數。 傳回的 `SequencePosition` 優點是允許呼叫者避免第二次掃描，以取得特定索引的資料。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

和的組合 `SequencePosition` `TryGet` 運作方式就像列舉值一樣。 [位置] 欄位會在每個反復專案開始時修改，以便在中的每個區段開始 `ReadOnlySequence<T>` 。

先前的方法在上是以擴充方法的形式存在 `ReadOnlySequence<T>` 。 <xref:System.Buffers.BuffersExtensions.PositionOf%2A>可以用來簡化上述程式碼：

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>處理 ReadOnlySequence \< T\>

處理可能 `ReadOnlySequence<T>` 會很困難，因為資料可能會分割成序列內的多個區段。 為了達到最佳效能，請將程式碼分成兩個路徑：

- 處理單一區段案例的快速路徑。
- 處理跨區段分割之資料的緩慢路徑。

有幾種方法可以用來處理多分割序列中的資料：

- 使用 [`SequenceReader<T>`](#sequencereadert) 。
- 依區段剖析資料區段，並追蹤已剖析 `SequencePosition` 區段內的和索引。 這可避免不必要的配置，但可能沒有效率，特別是針對小型緩衝區。
- 將複製 `ReadOnlySequence<T>` 到連續的陣列，並將它視為單一緩衝區：
  - 如果的大小 `ReadOnlySequence<T>` 很小，使用[stackalloc](../../csharp/language-reference/operators/stackalloc.md)運算子將資料複製到堆疊配置的緩衝區可能會是合理的。
  - 使用將複製到集區 `ReadOnlySequence<T>` 陣列 <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> 。
  - 使用 [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A)。 在最忙碌的路徑中不建議這樣做，因為它會在堆積上配置新的 `T[]` 。

下列範例示範一些常見的處理案例 `ReadOnlySequence<byte>` ：

##### <a name="process-binary-data"></a>處理二進位資料

下列範例會從的開頭剖析4個位元組的大序整數長度 `ReadOnlySequence<byte>` 。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>處理文字資料

下列範例將：

- 尋找中的第一個分行符號（ `\r\n` ） `ReadOnlySequence<byte>` ，並透過 out ' line ' 參數傳回它。
- 修剪該行， `\r\n` 從輸入緩衝區排除。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>空白區段

將空的區段儲存在中是有效的 `ReadOnlySequence<T>` 。 明確列舉區段時，可能會發生空的區段：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

上述程式碼會建立 `ReadOnlySequence<byte>` 具有空白區段的，並顯示這些空白區段如何影響各種 api：

- `ReadOnlySequence<T>.Slice`當 `SequencePosition` 指向空的區段時，會保留該區段。
- `ReadOnlySequence<T>.Slice`使用 int 略過空的區段。
- 列舉會 `ReadOnlySequence<T>` 列舉空的區段。

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>ReadOnlySequence \< T> 和 SequencePosition 的潛在問題

處理和一般時，會有幾個不尋常的結果 `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` ：

- `SequencePosition`是特定的位置標記 `ReadOnlySequence<T>` ，而不是絕對位置。 由於它是相對於特定的 `ReadOnlySequence<T>` ，因此如果在其來源的外部使用，則不會有意義 `ReadOnlySequence<T>` 。
- 無法在 `SequencePosition` 沒有的情況下執行算術 `ReadOnlySequence<T>` 。 這表示會撰寫類似的基本事項 `position++` `ReadOnlySequence<T>.GetPosition(position, 1)` 。
- `GetPosition(long)`不**支援負**索引。 這表示無法取得第二個到最後一個字元，而不需要流覽所有區段。
- `SequencePosition`無法比較兩個，使其難以：
  - 知道某個位置是否大於或小於另一個位置。
  - 撰寫一些剖析演算法。
- `ReadOnlySequence<T>`大於物件參考，而且應該在可能的情況下，[以](../../csharp/language-reference/keywords/in-parameter-modifier.md)或[ref](../../csharp/language-reference/keywords/ref.md)傳遞。 傳遞 `ReadOnlySequence<T>` `in` 或 `ref` 減少[結構](../../csharp/language-reference/builtin-types/struct.md)的複本。
- 空白區段：
  - 在中是有效的 `ReadOnlySequence<T>` 。
  - 使用方法逐一查看時，可能會出現 `ReadOnlySequence<T>.TryGet` 。
  - 可以使用 `ReadOnlySequence<T>.Slice()` 方法與物件來切割序列 `SequencePosition` 。

## <a name="sequencereadert"></a>SequenceReader \< T\>

<xref:System.Buffers.SequenceReader%601>:

- 是 .NET Core 3.0 中引進的新類型，可簡化的處理 `ReadOnlySequence<T>` 。
- 將單一區段與多區段之間的差異統一 `ReadOnlySequence<T>` `ReadOnlySequence<T>` 。
- 提供協助程式來讀取不 `byte` `char` 一定會在區段之間分割的二進位和文字資料（和）。

有內建方法可處理二進位和分隔的資料。 下一節將示範那些與相同的方法，如下所示 `SequenceReader<T>` ：

### <a name="access-data"></a>存取資料

`SequenceReader<T>`有方法可直接列舉內部的資料 `ReadOnlySequence<T>` 。 下列程式碼是一 `ReadOnlySequence<byte>` 次處理 a 的範例 `byte` ：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

`CurrentSpan`會公開目前的區段 `Span` ，這類似于在方法中手動執行的作業。

### <a name="use-position"></a>使用位置

下列程式碼是使用的範例執行 `FindIndexOf` `SequenceReader<T>` ：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>處理二進位資料

下列範例會從的開頭剖析4個位元組的大序整數長度 `ReadOnlySequence<byte>` 。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>處理文字資料

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader \< T \> 常見問題

- 因為 `SequenceReader<T>` 是可變動的結構，所以一定要以傳[址](../../csharp/language-reference/keywords/ref.md)方式傳遞。
- `SequenceReader<T>`是[ref 結構](../../csharp/language-reference/builtin-types/struct.md#ref-struct)，因此只能用於同步方法中，而且不能儲存在欄位中。 如需詳細資訊，請參閱[撰寫安全且有效率的 c # 程式碼](../../csharp/write-safe-efficient-code.md)。
- `SequenceReader<T>`已優化，可做為順向讀取器使用。 `Rewind`適用于無法使用其他 `Read` 、和 api 解決的小型備份 `Peek` `IsNext` 。
