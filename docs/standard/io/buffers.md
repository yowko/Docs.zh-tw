---
title: 系統緩衝區-.NET
ms.date: 12/05/2019
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: afcd6976e6220349fbec370c47b11596a35a81a2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823520"
---
# <a name="work-with-buffers-in-net"></a>在 .NET 中使用緩衝區

本文概述可協助讀取跨多個緩衝區執行之資料的類型。 它們主要是用來支援 <xref:System.IO.Pipelines.PipeReader> 物件。

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> 這是同步緩衝寫入的合約。 在最低層級，介面：

- 是基本的，而且不難使用。
- 允許存取 <xref:System.Memory%601> 或 <xref:System.Span%601> 。 `Memory<T>`或 `Span<T>` 可寫入至，而且您可以決定 `T` 寫入的專案數目。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

上述方法：

- 使用從要求至少5個位元組的緩衝區 `IBufferWriter<byte>` `GetSpan(5)` 。
- 將 ASCII 字串 "Hello" 的位元組寫入傳回的 `Span<byte>` 。
- 呼叫  <xref:System.Buffers.IBufferWriter%601> 以指出寫入緩衝區的位元組數目。

這種撰寫方法會使用 `Memory<T>` / `Span<T>` 提供的緩衝區 `IBufferWriter<T>` 。 或者， <xref:System.Buffers.BuffersExtensions.Write%2A> 擴充方法可以用來將現有的緩衝區複製到 `IBufferWriter<T>` 。 `Write`會執行適當的呼叫工作 `GetSpan` / `Advance` ，因此不需要 `Advance` 在寫入之後呼叫：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601> 是 `IBufferWriter<T>` 其備份存放區是單一連續陣列的實作為。

### <a name="ibufferwriter-common-problems"></a>IBufferWriter 常見問題

- `GetSpan` 並傳回 `GetMemory` 至少具有所要求記憶體數量的緩衝區。 請勿採用確切的緩衝區大小。
- 不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。
- 呼叫之後必須要求新的緩衝區 `Advance` ，才能繼續寫入更多資料。 在呼叫之後，無法寫入先前取得的緩衝區 `Advance` 。

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence 顯示在管線中的記憶體，以及在該唯讀記憶體的順序位置底下](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601> 這是一個結構，可以表示連續或非連續的序列 `T` 。 您可以從下列結構建立：

1. `T[]`
1. `ReadOnlyMemory<T>`
1. 一組連結的清單節點 <xref:System.Buffers.ReadOnlySequenceSegment%601> 和索引，表示序列的開始和結束位置。

第三個表示是最有趣的，因為它會對上的各種作業產生效能影響 `ReadOnlySequence<T>` ：

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

由於這種混合標記法，因此會 `ReadOnlySequence<T>` 公開索引， `SequencePosition` 而不是整數。 答 `SequencePosition` ：

- 這是一個不透明的值，表示 `ReadOnlySequence<T>` 其來源所在的索引。
- 由兩個部分組成：整數和物件。 這兩個值所代表的內容會系結至的實值 `ReadOnlySequence<T>` 。

### <a name="access-data"></a>存取資料

會將 `ReadOnlySequence<T>` 資料公開為的可列舉 `ReadOnlyMemory<T>` 。 您可以使用基本 foreach 來列舉每個區段：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

上述方法會在每個區段中搜尋特定的位元組。 如果您需要追蹤每個區段 `SequencePosition` ， <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> 則更適合。 下一個範例會變更上述程式碼，以傳回 `SequencePosition` 而不是整數。 傳回的 `SequencePosition` 好處是允許呼叫者避免第二次掃描取得特定索引的資料。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

和的組合 `SequencePosition` 會 `TryGet` 像列舉值一樣運作。 在每個反復專案開始時修改位置欄位，以便在中的每個區段開始 `ReadOnlySequence<T>` 。

上述方法會以的擴充方法形式存在 `ReadOnlySequence<T>` 。 <xref:System.Buffers.BuffersExtensions.PositionOf%2A> 可以用來簡化上述程式碼：

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>處理 ReadOnlySequence\<T\>

`ReadOnlySequence<T>`因為資料可能會分割成序列內的多個區段，所以處理很有挑戰性。 為了達到最佳效能，請將程式碼分成兩個路徑：

- 處理單一區段案例的快速路徑。
- 處理跨區段分割資料的慢速路徑。

有幾種方法可以用來處理多分段序列中的資料：

- 使用 [`SequenceReader<T>`](#sequencereadert) 。
- 依區段剖析資料區段，並追蹤所剖析 `SequencePosition` 區段內的和索引。 這可避免不必要的配置，但效率不佳，尤其是針對小型緩衝區。
- 將複製 `ReadOnlySequence<T>` 到連續的陣列，並將它視為單一緩衝區：
  - 如果的大小 `ReadOnlySequence<T>` 很小，則使用 [stackalloc](../../csharp/language-reference/operators/stackalloc.md) 運算子將資料複製到堆疊配置的緩衝區可能是合理的。
  - 使用將複製到集區 `ReadOnlySequence<T>` 陣列中 <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> 。
  - 使用 [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A)。 不建議在最忙碌路徑中，因為它會在堆積上配置新的 `T[]` 。

下列範例示範處理的一些常見案例 `ReadOnlySequence<byte>` ：

##### <a name="process-binary-data"></a>處理二進位資料

下列範例會從的開頭剖析4位元組的位元組由大到小整數長度 `ReadOnlySequence<byte>` 。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>處理文字資料

下列範例將：

- 在中找出第一個新行 (`\r\n`) `ReadOnlySequence<byte>` ，並透過 out ' line ' 參數傳回。
- 修剪該行， `\r\n` 從輸入緩衝區中排除。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>空白區段

將空白區段儲存在中是有效的 `ReadOnlySequence<T>` 。 明確地列舉區段時可能會發生空白區段：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

上述程式碼會建立 `ReadOnlySequence<byte>` 具有空白區段的，並顯示這些空的區段如何影響各種 api：

- `ReadOnlySequence<T>.Slice``SequencePosition`指向空白區段的會保留該區段。
- `ReadOnlySequence<T>.Slice` 使用 int 略過空白區段。
- 列舉會 `ReadOnlySequence<T>` 列舉空白區段。

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>ReadOnlySequence 和 SequencePosition 的潛在問題 \<T>

處理 vs 時，有幾個不尋常的結果 `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` ：

- `SequencePosition` 這是特定的位置標記 `ReadOnlySequence<T>` ，不是絕對位置。 因為它是相對於特定的 `ReadOnlySequence<T>` ，所以如果使用的位置超出其產生的位置，則沒有任何意義 `ReadOnlySequence<T>` 。
- 無法在 `SequencePosition` 沒有的情況下執行算術 `ReadOnlySequence<T>` 。 這表示會撰寫像這樣的基本事項 `position++` `ReadOnlySequence<T>.GetPosition(position, 1)` 。
- `GetPosition(long)` 不 **支援負** 索引。 這表示不可能取得第二個字元到最後一個字元，而不需要結束所有區段。
- 兩個 `SequencePosition` 無法比較，因此很難：
  - 知道一個位置是否大於或小於另一個位置。
  - 撰寫一些剖析演算法。
- `ReadOnlySequence<T>` 大於物件參考，且應盡可能 [以 in](../../csharp/language-reference/keywords/in-parameter-modifier.md) 或 [ref](../../csharp/language-reference/keywords/ref.md) 傳遞。 傳遞 `ReadOnlySequence<T>` `in` 或 `ref` 減少 [結構](../../csharp/language-reference/builtin-types/struct.md)的複本。
- 空白區段：
  - 在中是有效的 `ReadOnlySequence<T>` 。
  - 可以在使用方法進行反覆運算時出現 `ReadOnlySequence<T>.TryGet` 。
  - 可以使用 `ReadOnlySequence<T>.Slice()` 方法與物件來顯示切割序列 `SequencePosition` 。

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- 是 .NET Core 3.0 中引進的新類型，可簡化的處理 `ReadOnlySequence<T>` 。
- 統一單一區段 `ReadOnlySequence<T>` 和多個區段之間的差異 `ReadOnlySequence<T>` 。
- 提供讀取二進位和文字資料的協助程式， (`byte` 和不 `char` 一定會分割到區段的) 。

有內建方法可處理二進位和分隔資料的處理。 下一節將示範這些相同的方法與下列各項的樣子 `SequenceReader<T>` ：

### <a name="access-data"></a>存取資料

`SequenceReader<T>` 具有可直接列舉內部資料的方法 `ReadOnlySequence<T>` 。 下列程式碼是一次處理 a 的 `ReadOnlySequence<byte>` 範例 `byte` ：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

`CurrentSpan`會公開目前的區段 `Span` ，這類似于在方法中手動完成的作業。

### <a name="use-position"></a>使用位置

下列程式碼是使用的範例執行 `FindIndexOf` `SequenceReader<T>` ：

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>處理二進位資料

下列範例會從的開頭剖析4位元組的位元組由大到小整數長度 `ReadOnlySequence<byte>` 。

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>處理文字資料

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader \<T\> 常見問題

- 由於是可變動的 `SequenceReader<T>` 結構，因此應該一律以傳 [址](../../csharp/language-reference/keywords/ref.md)方式傳遞。
- `SequenceReader<T>` 是 [ref 結構](../../csharp/language-reference/builtin-types/struct.md#ref-struct) ，因此它只能用於同步方法，而且無法儲存在欄位中。 如需詳細資訊，請參閱 [撰寫安全且有效率的 c # 程式碼](../../csharp/write-safe-efficient-code.md)。
- `SequenceReader<T>` 已針對用作順向讀取器進行優化。 `Rewind` 適用于無法利用其他 `Read` 、和 api 處理的小型備份 `Peek` `IsNext` 。
