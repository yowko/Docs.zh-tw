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
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="f3ea4-102">在 .NET 中使用緩衝區</span><span class="sxs-lookup"><span data-stu-id="f3ea4-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="f3ea4-103">本文概述可協助讀取跨多個緩衝區執行之資料的類型。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="f3ea4-104">它們主要是用來支援 <xref:System.IO.Pipelines.PipeReader> 物件。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="f3ea4-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="f3ea4-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="f3ea4-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> 這是同步緩衝寫入的合約。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="f3ea4-107">在最低層級，介面：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="f3ea4-108">是基本的，而且不難使用。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="f3ea4-109">允許存取 <xref:System.Memory%601> 或 <xref:System.Span%601> 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="f3ea4-110">`Memory<T>`或 `Span<T>` 可寫入至，而且您可以決定 `T` 寫入的專案數目。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="f3ea4-111">上述方法：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-111">The preceding method:</span></span>

- <span data-ttu-id="f3ea4-112">使用從要求至少5個位元組的緩衝區 `IBufferWriter<byte>` `GetSpan(5)` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="f3ea4-113">將 ASCII 字串 "Hello" 的位元組寫入傳回的 `Span<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="f3ea4-114">呼叫  <xref:System.Buffers.IBufferWriter%601> 以指出寫入緩衝區的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="f3ea4-115">這種撰寫方法會使用 `Memory<T>` / `Span<T>` 提供的緩衝區 `IBufferWriter<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="f3ea4-116">或者， <xref:System.Buffers.BuffersExtensions.Write%2A> 擴充方法可以用來將現有的緩衝區複製到 `IBufferWriter<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="f3ea4-117">`Write`會執行適當的呼叫工作 `GetSpan` / `Advance` ，因此不需要 `Advance` 在寫入之後呼叫：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="f3ea4-118"><xref:System.Buffers.ArrayBufferWriter%601> 是 `IBufferWriter<T>` 其備份存放區是單一連續陣列的實作為。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="f3ea4-119">IBufferWriter 常見問題</span><span class="sxs-lookup"><span data-stu-id="f3ea4-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="f3ea4-120">`GetSpan` 並傳回 `GetMemory` 至少具有所要求記憶體數量的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="f3ea4-121">請勿採用確切的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="f3ea4-122">不保證後續的呼叫會傳回相同的緩衝區或相同大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="f3ea4-123">呼叫之後必須要求新的緩衝區 `Advance` ，才能繼續寫入更多資料。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="f3ea4-124">在呼叫之後，無法寫入先前取得的緩衝區 `Advance` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="f3ea4-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="f3ea4-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence 顯示在管線中的記憶體，以及在該唯讀記憶體的順序位置底下](media/buffers/ro-sequence.png)

<span data-ttu-id="f3ea4-127"><xref:System.Buffers.ReadOnlySequence%601> 這是一個結構，可以表示連續或非連續的序列 `T` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="f3ea4-128">您可以從下列結構建立：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-128">It can be constructed from:</span></span>

1. <span data-ttu-id="f3ea4-129">`T[]`</span><span class="sxs-lookup"><span data-stu-id="f3ea4-129">A `T[]`</span></span>
1. <span data-ttu-id="f3ea4-130">`ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="f3ea4-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="f3ea4-131">一組連結的清單節點 <xref:System.Buffers.ReadOnlySequenceSegment%601> 和索引，表示序列的開始和結束位置。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="f3ea4-132">第三個表示是最有趣的，因為它會對上的各種作業產生效能影響 `ReadOnlySequence<T>` ：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="f3ea4-133">表示法</span><span class="sxs-lookup"><span data-stu-id="f3ea4-133">Representation</span></span>|<span data-ttu-id="f3ea4-134">作業</span><span class="sxs-lookup"><span data-stu-id="f3ea4-134">Operation</span></span>|<span data-ttu-id="f3ea4-135">複雜度</span><span class="sxs-lookup"><span data-stu-id="f3ea4-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="f3ea4-136">由於這種混合標記法，因此會 `ReadOnlySequence<T>` 公開索引， `SequencePosition` 而不是整數。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="f3ea4-137">答 `SequencePosition` ：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="f3ea4-138">這是一個不透明的值，表示 `ReadOnlySequence<T>` 其來源所在的索引。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="f3ea4-139">由兩個部分組成：整數和物件。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="f3ea4-140">這兩個值所代表的內容會系結至的實值 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="f3ea4-141">存取資料</span><span class="sxs-lookup"><span data-stu-id="f3ea4-141">Access data</span></span>

<span data-ttu-id="f3ea4-142">會將 `ReadOnlySequence<T>` 資料公開為的可列舉 `ReadOnlyMemory<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="f3ea4-143">您可以使用基本 foreach 來列舉每個區段：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="f3ea4-144">上述方法會在每個區段中搜尋特定的位元組。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="f3ea4-145">如果您需要追蹤每個區段 `SequencePosition` ， <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> 則更適合。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="f3ea4-146">下一個範例會變更上述程式碼，以傳回 `SequencePosition` 而不是整數。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="f3ea4-147">傳回的 `SequencePosition` 好處是允許呼叫者避免第二次掃描取得特定索引的資料。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="f3ea4-148">和的組合 `SequencePosition` 會 `TryGet` 像列舉值一樣運作。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="f3ea4-149">在每個反復專案開始時修改位置欄位，以便在中的每個區段開始 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="f3ea4-150">上述方法會以的擴充方法形式存在 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="f3ea4-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> 可以用來簡化上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="f3ea4-152">處理 ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="f3ea4-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="f3ea4-153">`ReadOnlySequence<T>`因為資料可能會分割成序列內的多個區段，所以處理很有挑戰性。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="f3ea4-154">為了達到最佳效能，請將程式碼分成兩個路徑：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="f3ea4-155">處理單一區段案例的快速路徑。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="f3ea4-156">處理跨區段分割資料的慢速路徑。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="f3ea4-157">有幾種方法可以用來處理多分段序列中的資料：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="f3ea4-158">使用 [`SequenceReader<T>`](#sequencereadert) 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="f3ea4-159">依區段剖析資料區段，並追蹤所剖析 `SequencePosition` 區段內的和索引。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="f3ea4-160">這可避免不必要的配置，但效率不佳，尤其是針對小型緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="f3ea4-161">將複製 `ReadOnlySequence<T>` 到連續的陣列，並將它視為單一緩衝區：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="f3ea4-162">如果的大小 `ReadOnlySequence<T>` 很小，則使用 [stackalloc](../../csharp/language-reference/operators/stackalloc.md) 運算子將資料複製到堆疊配置的緩衝區可能是合理的。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="f3ea4-163">使用將複製到集區 `ReadOnlySequence<T>` 陣列中 <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="f3ea4-164">使用 [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A)。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="f3ea4-165">不建議在最忙碌路徑中，因為它會在堆積上配置新的 `T[]` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="f3ea4-166">下列範例示範處理的一些常見案例 `ReadOnlySequence<byte>` ：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="f3ea4-167">處理二進位資料</span><span class="sxs-lookup"><span data-stu-id="f3ea4-167">Process binary data</span></span>

<span data-ttu-id="f3ea4-168">下列範例會從的開頭剖析4位元組的位元組由大到小整數長度 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="f3ea4-169">處理文字資料</span><span class="sxs-lookup"><span data-stu-id="f3ea4-169">Process text data</span></span>

<span data-ttu-id="f3ea4-170">下列範例將：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-170">The following example:</span></span>

- <span data-ttu-id="f3ea4-171">在中找出第一個新行 (`\r\n`) `ReadOnlySequence<byte>` ，並透過 out ' line ' 參數傳回。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="f3ea4-172">修剪該行， `\r\n` 從輸入緩衝區中排除。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="f3ea4-173">空白區段</span><span class="sxs-lookup"><span data-stu-id="f3ea4-173">Empty segments</span></span>

<span data-ttu-id="f3ea4-174">將空白區段儲存在中是有效的 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="f3ea4-175">明確地列舉區段時可能會發生空白區段：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="f3ea4-176">上述程式碼會建立 `ReadOnlySequence<byte>` 具有空白區段的，並顯示這些空的區段如何影響各種 api：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="f3ea4-177">`ReadOnlySequence<T>.Slice``SequencePosition`指向空白區段的會保留該區段。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="f3ea4-178">`ReadOnlySequence<T>.Slice` 使用 int 略過空白區段。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="f3ea4-179">列舉會 `ReadOnlySequence<T>` 列舉空白區段。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="f3ea4-180">ReadOnlySequence 和 SequencePosition 的潛在問題 \<T></span><span class="sxs-lookup"><span data-stu-id="f3ea4-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="f3ea4-181">處理 vs 時，有幾個不尋常的結果 `ReadOnlySequence<T>` / `SequencePosition` `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int` ：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="f3ea4-182">`SequencePosition` 這是特定的位置標記 `ReadOnlySequence<T>` ，不是絕對位置。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="f3ea4-183">因為它是相對於特定的 `ReadOnlySequence<T>` ，所以如果使用的位置超出其產生的位置，則沒有任何意義 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="f3ea4-184">無法在 `SequencePosition` 沒有的情況下執行算術 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="f3ea4-185">這表示會撰寫像這樣的基本事項 `position++` `ReadOnlySequence<T>.GetPosition(position, 1)` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="f3ea4-186">`GetPosition(long)` 不 **支援負** 索引。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="f3ea4-187">這表示不可能取得第二個字元到最後一個字元，而不需要結束所有區段。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="f3ea4-188">兩個 `SequencePosition` 無法比較，因此很難：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="f3ea4-189">知道一個位置是否大於或小於另一個位置。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="f3ea4-190">撰寫一些剖析演算法。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="f3ea4-191">`ReadOnlySequence<T>` 大於物件參考，且應盡可能 [以 in](../../csharp/language-reference/keywords/in-parameter-modifier.md) 或 [ref](../../csharp/language-reference/keywords/ref.md) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="f3ea4-192">傳遞 `ReadOnlySequence<T>` `in` 或 `ref` 減少 [結構](../../csharp/language-reference/builtin-types/struct.md)的複本。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="f3ea4-193">空白區段：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-193">Empty segments:</span></span>
  - <span data-ttu-id="f3ea4-194">在中是有效的 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="f3ea4-195">可以在使用方法進行反覆運算時出現 `ReadOnlySequence<T>.TryGet` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="f3ea4-196">可以使用 `ReadOnlySequence<T>.Slice()` 方法與物件來顯示切割序列 `SequencePosition` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="f3ea4-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="f3ea4-197">SequenceReader\<T\></span></span>

<span data-ttu-id="f3ea4-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="f3ea4-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="f3ea4-199">是 .NET Core 3.0 中引進的新類型，可簡化的處理 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="f3ea4-200">統一單一區段 `ReadOnlySequence<T>` 和多個區段之間的差異 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="f3ea4-201">提供讀取二進位和文字資料的協助程式， (`byte` 和不 `char` 一定會分割到區段的) 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="f3ea4-202">有內建方法可處理二進位和分隔資料的處理。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="f3ea4-203">下一節將示範這些相同的方法與下列各項的樣子 `SequenceReader<T>` ：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="f3ea4-204">存取資料</span><span class="sxs-lookup"><span data-stu-id="f3ea4-204">Access data</span></span>

<span data-ttu-id="f3ea4-205">`SequenceReader<T>` 具有可直接列舉內部資料的方法 `ReadOnlySequence<T>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="f3ea4-206">下列程式碼是一次處理 a 的 `ReadOnlySequence<byte>` 範例 `byte` ：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="f3ea4-207">`CurrentSpan`會公開目前的區段 `Span` ，這類似于在方法中手動完成的作業。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="f3ea4-208">使用位置</span><span class="sxs-lookup"><span data-stu-id="f3ea4-208">Use position</span></span>

<span data-ttu-id="f3ea4-209">下列程式碼是使用的範例執行 `FindIndexOf` `SequenceReader<T>` ：</span><span class="sxs-lookup"><span data-stu-id="f3ea4-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="f3ea4-210">處理二進位資料</span><span class="sxs-lookup"><span data-stu-id="f3ea4-210">Process binary data</span></span>

<span data-ttu-id="f3ea4-211">下列範例會從的開頭剖析4位元組的位元組由大到小整數長度 `ReadOnlySequence<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="f3ea4-212">處理文字資料</span><span class="sxs-lookup"><span data-stu-id="f3ea4-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="f3ea4-213">SequenceReader \<T\> 常見問題</span><span class="sxs-lookup"><span data-stu-id="f3ea4-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="f3ea4-214">由於是可變動的 `SequenceReader<T>` 結構，因此應該一律以傳 [址](../../csharp/language-reference/keywords/ref.md)方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="f3ea4-215">`SequenceReader<T>` 是 [ref 結構](../../csharp/language-reference/builtin-types/struct.md#ref-struct) ，因此它只能用於同步方法，而且無法儲存在欄位中。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="f3ea4-216">如需詳細資訊，請參閱 [撰寫安全且有效率的 c # 程式碼](../../csharp/write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="f3ea4-217">`SequenceReader<T>` 已針對用作順向讀取器進行優化。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="f3ea4-218">`Rewind` 適用于無法利用其他 `Read` 、和 api 處理的小型備份 `Peek` `IsNext` 。</span><span class="sxs-lookup"><span data-stu-id="f3ea4-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
