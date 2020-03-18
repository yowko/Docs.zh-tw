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
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="5628b-102">使用 .NET 中的緩衝區</span><span class="sxs-lookup"><span data-stu-id="5628b-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="5628b-103">本文概述了説明讀取跨多個緩衝區運行的資料的類型。</span><span class="sxs-lookup"><span data-stu-id="5628b-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="5628b-104">它們主要用於支援<xref:System.IO.Pipelines.PipeReader>物件。</span><span class="sxs-lookup"><span data-stu-id="5628b-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="5628b-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="5628b-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="5628b-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>是同步緩衝寫入的協定。</span><span class="sxs-lookup"><span data-stu-id="5628b-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="5628b-107">在最低級別，介面：</span><span class="sxs-lookup"><span data-stu-id="5628b-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="5628b-108">是基本的，使用起來並不難。</span><span class="sxs-lookup"><span data-stu-id="5628b-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="5628b-109">允許訪問 或<xref:System.Memory%601><xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="5628b-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="5628b-110">或 可以寫入，您可以確定寫入的專案數`T` `Memory<T>` `Span<T>`</span><span class="sxs-lookup"><span data-stu-id="5628b-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="5628b-111">上述方法：</span><span class="sxs-lookup"><span data-stu-id="5628b-111">The preceding method:</span></span>

- <span data-ttu-id="5628b-112">從 using`GetSpan(5)`請求至少 5 個位元組`IBufferWriter<byte>`的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5628b-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="5628b-113">將 ASCII 字串"Hello"的位元組寫入返回`Span<byte>`的 。</span><span class="sxs-lookup"><span data-stu-id="5628b-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="5628b-114">調用<xref:System.Buffers.IBufferWriter%601>以指示寫入緩衝區的位元組數。</span><span class="sxs-lookup"><span data-stu-id="5628b-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="5628b-115">這種書寫`Memory<T>`/`Span<T>`方法使用 提供的緩衝區`IBufferWriter<T>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="5628b-116">或者，<xref:System.Buffers.BuffersExtensions.Write%2A>擴充方法可用於將現有緩衝區複製到 。 `IBufferWriter<T>`</span><span class="sxs-lookup"><span data-stu-id="5628b-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="5628b-117">`Write`是否`GetSpan`/`Advance`根據需要調用工作，因此無需在編寫後調用`Advance`：</span><span class="sxs-lookup"><span data-stu-id="5628b-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="5628b-118"><xref:System.Buffers.ArrayBufferWriter%601>是 其備份`IBufferWriter<T>`存儲是單個連續陣列的實現。</span><span class="sxs-lookup"><span data-stu-id="5628b-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="5628b-119">IBufferWriter 常見問題</span><span class="sxs-lookup"><span data-stu-id="5628b-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="5628b-120">`GetSpan`並`GetMemory`返回至少具有請求記憶體量的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5628b-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="5628b-121">不要假定確切的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="5628b-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="5628b-122">不能保證連續調用將返回相同的緩衝區或相同大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5628b-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="5628b-123">調用`Advance`後必須請求新的緩衝區以繼續寫入更多資料。</span><span class="sxs-lookup"><span data-stu-id="5628b-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="5628b-124">調用後`Advance`無法將以前獲取的緩衝區寫入。</span><span class="sxs-lookup"><span data-stu-id="5628b-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="5628b-125">唯讀序列\<T\></span><span class="sxs-lookup"><span data-stu-id="5628b-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence 在管道中顯示記憶體，低於唯讀記憶體的序列位置](media/buffers/ro-sequence.png)

<span data-ttu-id="5628b-127"><xref:System.Buffers.ReadOnlySequence%601>是一個結構，可以表示 的連續序列或不連續序列`T`。</span><span class="sxs-lookup"><span data-stu-id="5628b-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="5628b-128">它可以從：</span><span class="sxs-lookup"><span data-stu-id="5628b-128">It can be constructed from:</span></span>

1. <span data-ttu-id="5628b-129">`T[]`。</span><span class="sxs-lookup"><span data-stu-id="5628b-129">A `T[]`</span></span>
1. <span data-ttu-id="5628b-130">`ReadOnlyMemory<T>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="5628b-131">一對連結清單節點<xref:System.Buffers.ReadOnlySequenceSegment%601>和索引，用於表示序列的開始和結束位置。</span><span class="sxs-lookup"><span data-stu-id="5628b-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="5628b-132">第三個表示形式是最有趣的，因為它對 ： `ReadOnlySequence<T>`</span><span class="sxs-lookup"><span data-stu-id="5628b-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="5628b-133">表示法</span><span class="sxs-lookup"><span data-stu-id="5628b-133">Representation</span></span>|<span data-ttu-id="5628b-134">作業</span><span class="sxs-lookup"><span data-stu-id="5628b-134">Operation</span></span>|<span data-ttu-id="5628b-135">複雜度</span><span class="sxs-lookup"><span data-stu-id="5628b-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="5628b-136">由於這種混合表示形式，`ReadOnlySequence<T>`公開索引不是`SequencePosition`整數。</span><span class="sxs-lookup"><span data-stu-id="5628b-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="5628b-137">A `SequencePosition`：</span><span class="sxs-lookup"><span data-stu-id="5628b-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="5628b-138">是表示索引到其發源地的`ReadOnlySequence<T>`不透明值。</span><span class="sxs-lookup"><span data-stu-id="5628b-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="5628b-139">由兩個部分組成，一個整數和一個物件。</span><span class="sxs-lookup"><span data-stu-id="5628b-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="5628b-140">這兩個值表示的內容與 的`ReadOnlySequence<T>`實現相關聯。</span><span class="sxs-lookup"><span data-stu-id="5628b-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="5628b-141">存取資料</span><span class="sxs-lookup"><span data-stu-id="5628b-141">Access data</span></span>

<span data-ttu-id="5628b-142">公開`ReadOnlySequence<T>`資料作為 的`ReadOnlyMemory<T>`枚舉。</span><span class="sxs-lookup"><span data-stu-id="5628b-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="5628b-143">可以使用基本功能枚舉每個段進行枚舉：</span><span class="sxs-lookup"><span data-stu-id="5628b-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="5628b-144">前面的方法搜索每個段以尋找特定的位元組。</span><span class="sxs-lookup"><span data-stu-id="5628b-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="5628b-145">如果需要跟蹤每個段的`SequencePosition`，<xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType>則更合適。</span><span class="sxs-lookup"><span data-stu-id="5628b-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="5628b-146">下一個示例將前面的代碼更改為返回`SequencePosition`而不是整數。</span><span class="sxs-lookup"><span data-stu-id="5628b-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="5628b-147">返回`SequencePosition`a 的好處是允許調用方避免第二次掃描以獲取特定索引上的資料。</span><span class="sxs-lookup"><span data-stu-id="5628b-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="5628b-148">和`TryGet`的組合`SequencePosition`類似于枚舉器。</span><span class="sxs-lookup"><span data-stu-id="5628b-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="5628b-149">位置欄位在每次反覆運算開始時被修改為 中每個段的開始`ReadOnlySequence<T>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="5628b-150">前面的方法作為擴充方法存在於 上`ReadOnlySequence<T>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="5628b-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>可用於簡化前面的代碼：</span><span class="sxs-lookup"><span data-stu-id="5628b-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="5628b-152">處理唯讀序列\<T\></span><span class="sxs-lookup"><span data-stu-id="5628b-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="5628b-153">處理`ReadOnlySequence<T>`可能具有挑戰性，因為資料可能會跨序列中的多個段拆分。</span><span class="sxs-lookup"><span data-stu-id="5628b-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="5628b-154">為了獲得最佳性能，請將代碼拆分為兩個路徑：</span><span class="sxs-lookup"><span data-stu-id="5628b-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="5628b-155">處理單個段案例的快速路徑。</span><span class="sxs-lookup"><span data-stu-id="5628b-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="5628b-156">處理跨段拆分的資料的慢速路徑。</span><span class="sxs-lookup"><span data-stu-id="5628b-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="5628b-157">有幾種方法可用於處理多分段序列中的資料：</span><span class="sxs-lookup"><span data-stu-id="5628b-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="5628b-158">使用[`SequenceReader<T>`](#sequencereadert)。</span><span class="sxs-lookup"><span data-stu-id="5628b-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="5628b-159">按段分析資料段，跟蹤所分析的段`SequencePosition`內的 和 索引。</span><span class="sxs-lookup"><span data-stu-id="5628b-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="5628b-160">這樣可以避免不必要的分配，但效率可能很低，尤其是對於小型緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5628b-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="5628b-161">將`ReadOnlySequence<T>`複製到連續陣列並將其視為單個緩衝區：</span><span class="sxs-lookup"><span data-stu-id="5628b-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="5628b-162">如果 的大小`ReadOnlySequence<T>`較小，則使用[stackalloc](../../csharp/language-reference/operators/stackalloc.md)運算子將資料複製到堆疊分配的緩衝區可能是合理的。</span><span class="sxs-lookup"><span data-stu-id="5628b-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="5628b-163">使用`ReadOnlySequence<T>`將 複製到池陣列中<xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5628b-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="5628b-164">使用[`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A)。</span><span class="sxs-lookup"><span data-stu-id="5628b-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="5628b-165">在熱路徑中不建議這樣做，因為它在堆上分配了`T[]`一個新的。</span><span class="sxs-lookup"><span data-stu-id="5628b-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="5628b-166">以下示例演示了一些用於處理`ReadOnlySequence<byte>`的常見案例：</span><span class="sxs-lookup"><span data-stu-id="5628b-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="5628b-167">處理二進位資料</span><span class="sxs-lookup"><span data-stu-id="5628b-167">Process binary data</span></span>

<span data-ttu-id="5628b-168">下面的示例從 開始分析 4 位元組的大位元組整數長度`ReadOnlySequence<byte>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="5628b-169">處理文本資料</span><span class="sxs-lookup"><span data-stu-id="5628b-169">Process text data</span></span>

<span data-ttu-id="5628b-170">下列範例將：</span><span class="sxs-lookup"><span data-stu-id="5628b-170">The following example:</span></span>

- <span data-ttu-id="5628b-171">在 中找到 中的第`\r\n`一個折`ReadOnlySequence<byte>`線 （ ）， 並通過 out"行"參數返回它。</span><span class="sxs-lookup"><span data-stu-id="5628b-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="5628b-172">修剪該行，不包括輸入緩衝區`\r\n`中的 。</span><span class="sxs-lookup"><span data-stu-id="5628b-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="5628b-173">空段</span><span class="sxs-lookup"><span data-stu-id="5628b-173">Empty segments</span></span>

<span data-ttu-id="5628b-174">將空段存儲在 中是有效的`ReadOnlySequence<T>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="5628b-175">顯式枚舉段時可能會出現空段：</span><span class="sxs-lookup"><span data-stu-id="5628b-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="5628b-176">前面的代碼創建具有空`ReadOnlySequence<byte>`段的 ，並顯示這些空段如何影響各種 API：</span><span class="sxs-lookup"><span data-stu-id="5628b-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="5628b-177">`ReadOnlySequence<T>.Slice`指向`SequencePosition`空段的點將保留該段。</span><span class="sxs-lookup"><span data-stu-id="5628b-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="5628b-178">`ReadOnlySequence<T>.Slice`帶 int 跳過空段。</span><span class="sxs-lookup"><span data-stu-id="5628b-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="5628b-179">枚舉枚`ReadOnlySequence<T>`舉空段。</span><span class="sxs-lookup"><span data-stu-id="5628b-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="5628b-180">ReadOnly序列\<T>和序列位置的潛在問題</span><span class="sxs-lookup"><span data-stu-id="5628b-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="5628b-181">處理`ReadOnlySequence<T>`/`SequencePosition`正常`ReadOnlySpan<T>`/`ReadOnlyMemory<T>`與/，有幾個不尋常的`int`結果： `T[]` /</span><span class="sxs-lookup"><span data-stu-id="5628b-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="5628b-182">`SequencePosition`是特定`ReadOnlySequence<T>`位置（而不是絕對位置）的位置標記。</span><span class="sxs-lookup"><span data-stu-id="5628b-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="5628b-183">因為它相對於特定`ReadOnlySequence<T>`，如果使用它的來源之外，`ReadOnlySequence<T>`它沒有意義。</span><span class="sxs-lookup"><span data-stu-id="5628b-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="5628b-184">沒有 無法對`SequencePosition`執行算術。 `ReadOnlySequence<T>`</span><span class="sxs-lookup"><span data-stu-id="5628b-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="5628b-185">這意味著做基本的事情，如`position++`寫`ReadOnlySequence<T>.GetPosition(position, 1)`。</span><span class="sxs-lookup"><span data-stu-id="5628b-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="5628b-186">`GetPosition(long)`不支援**負**索引。</span><span class="sxs-lookup"><span data-stu-id="5628b-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="5628b-187">這意味著，如果不走遍所有段，就不可能獲得第二個到最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="5628b-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="5628b-188">兩`SequencePosition`個無法比較，因此很難：</span><span class="sxs-lookup"><span data-stu-id="5628b-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="5628b-189">瞭解一個位置是否大於或小於另一個位置。</span><span class="sxs-lookup"><span data-stu-id="5628b-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="5628b-190">編寫一些分析演算法。</span><span class="sxs-lookup"><span data-stu-id="5628b-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="5628b-191">`ReadOnlySequence<T>`大於物件引用，應盡可能通過[in](../../csharp/language-reference/keywords/in-parameter-modifier.md)或[ref](../../csharp/language-reference/keywords/ref.md)傳遞。</span><span class="sxs-lookup"><span data-stu-id="5628b-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="5628b-192">傳遞`ReadOnlySequence<T>``in`或`ref`減少[結構](../../csharp/language-reference/builtin-types/struct.md)的副本。</span><span class="sxs-lookup"><span data-stu-id="5628b-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="5628b-193">空段：</span><span class="sxs-lookup"><span data-stu-id="5628b-193">Empty segments:</span></span>
  - <span data-ttu-id="5628b-194">在 中有效`ReadOnlySequence<T>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="5628b-195">可以使用`ReadOnlySequence<T>.TryGet`方法反覆運算時顯示。</span><span class="sxs-lookup"><span data-stu-id="5628b-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="5628b-196">可以使用 方法`ReadOnlySequence<T>.Slice()`與物件一起`SequencePosition`切片序列。</span><span class="sxs-lookup"><span data-stu-id="5628b-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="5628b-197">序列閱讀器\<T\></span><span class="sxs-lookup"><span data-stu-id="5628b-197">SequenceReader\<T\></span></span>

<span data-ttu-id="5628b-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="5628b-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="5628b-199">是 .NET Core 3.0 中引入的一種新類型，用於`ReadOnlySequence<T>`簡化 的處理。</span><span class="sxs-lookup"><span data-stu-id="5628b-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="5628b-200">將單個段和多段`ReadOnlySequence<T>``ReadOnlySequence<T>`之間的差異一起。</span><span class="sxs-lookup"><span data-stu-id="5628b-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="5628b-201">提供用於讀取二進位和文本資料 （`byte` `char`和 ） 的説明器，這些資料和文本資料可能跨段拆分，也可能不拆分。</span><span class="sxs-lookup"><span data-stu-id="5628b-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="5628b-202">有處理二進位和分隔資料的內置方法。</span><span class="sxs-lookup"><span data-stu-id="5628b-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="5628b-203">以下部分演示了這些相同的方法與 ： `SequenceReader<T>`</span><span class="sxs-lookup"><span data-stu-id="5628b-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="5628b-204">存取資料</span><span class="sxs-lookup"><span data-stu-id="5628b-204">Access data</span></span>

<span data-ttu-id="5628b-205">`SequenceReader<T>`具有直接枚舉資料`ReadOnlySequence<T>`的方法。</span><span class="sxs-lookup"><span data-stu-id="5628b-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="5628b-206">以下代碼是一次處理 a`ReadOnlySequence<byte>``byte`的示例：</span><span class="sxs-lookup"><span data-stu-id="5628b-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="5628b-207">公開`CurrentSpan`當前段的`Span`，這與手動在方法中執行的內容類別似。</span><span class="sxs-lookup"><span data-stu-id="5628b-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="5628b-208">使用位置</span><span class="sxs-lookup"><span data-stu-id="5628b-208">Use position</span></span>

<span data-ttu-id="5628b-209">以下代碼是使用 的示例`FindIndexOf`實現： `SequenceReader<T>`</span><span class="sxs-lookup"><span data-stu-id="5628b-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="5628b-210">處理二進位資料</span><span class="sxs-lookup"><span data-stu-id="5628b-210">Process binary data</span></span>

<span data-ttu-id="5628b-211">下面的示例從 開始分析 4 位元組的大位元組整數長度`ReadOnlySequence<byte>`。</span><span class="sxs-lookup"><span data-stu-id="5628b-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="5628b-212">處理文本資料</span><span class="sxs-lookup"><span data-stu-id="5628b-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="5628b-213">序列閱讀器\< \> T 常見問題</span><span class="sxs-lookup"><span data-stu-id="5628b-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="5628b-214">因為它是`SequenceReader<T>`可變結構，它應始終通過[引用](../../csharp/language-reference/keywords/ref.md)傳遞。</span><span class="sxs-lookup"><span data-stu-id="5628b-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="5628b-215">`SequenceReader<T>`是一個[ref 結構](../../csharp/language-reference/keywords/ref.md#ref-struct-types)，因此它只能在同步方法中使用，並且不能存儲在欄位中。</span><span class="sxs-lookup"><span data-stu-id="5628b-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/keywords/ref.md#ref-struct-types) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="5628b-216">有關詳細資訊，請參閱[編寫安全高效的 C# 代碼](../../csharp/write-safe-efficient-code.md)。</span><span class="sxs-lookup"><span data-stu-id="5628b-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="5628b-217">`SequenceReader<T>`經過優化，可用作僅轉發讀取器。</span><span class="sxs-lookup"><span data-stu-id="5628b-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="5628b-218">`Rewind`用於使用其他`Read`無法使用 和`Peek` `IsNext` API 解決的小型備份。</span><span class="sxs-lookup"><span data-stu-id="5628b-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
