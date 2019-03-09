---
title: 記憶體與延伸
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
  - Memory<T>
  - Span<T>
  - buffers"
  - pipeline processing
author: rpetrusha
ms.author: ronpet
---

# <a name="memory--and-span-related-types"></a><span data-ttu-id="91d8a-102">記憶體與延伸相關類型</span><span class="sxs-lookup"><span data-stu-id="91d8a-102">Memory- and span-related types</span></span>

<span data-ttu-id="91d8a-103">從 .NET Core 2.1 開始，.NET 就包括一些相關類型，這些類型代表連續的強型別任意記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="91d8a-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="91d8a-104">它們包括：</span><span class="sxs-lookup"><span data-stu-id="91d8a-104">These include:</span></span>

- <span data-ttu-id="91d8a-105"><xref:System.Span%601?displayProperty=nameWithType>，此類型是用來存取連續記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="91d8a-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="91d8a-106"><xref:System.Span%601> 執行個體可由類型 `T` 的陣列、<xref:System.String>、使用[stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) 配置的緩衝區或非受控記憶體的指標來支持。</span><span class="sxs-lookup"><span data-stu-id="91d8a-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="91d8a-107">因為它必須在堆疊上配置，它有一些限制。</span><span class="sxs-lookup"><span data-stu-id="91d8a-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="91d8a-108">例如，類別中欄位的類型不能是 <xref:System.Span%601>，而且延伸也不能用於非同步作業中。</span><span class="sxs-lookup"><span data-stu-id="91d8a-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="91d8a-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>，這是 <xref:System.Span%601> 結構的不可變版本。</span><span class="sxs-lookup"><span data-stu-id="91d8a-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="91d8a-110"><xref:System.Memory%601?displayProperty=nameWithType>，這是在受空堆積而非堆疊上配置的連續記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="91d8a-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="91d8a-111"><xref:System.Memory%601> 執行個體可由類型為 `T` 的陣列或 <xref:System.String> 支持。</span><span class="sxs-lookup"><span data-stu-id="91d8a-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="91d8a-112">因為它可以存放在受控堆積上，<xref:System.Memory%601> 有沒有 <xref:System.Span%601> 的任何限制。</span><span class="sxs-lookup"><span data-stu-id="91d8a-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="91d8a-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>，這是 <xref:System.Memory%601> 結構的不可變版本。</span><span class="sxs-lookup"><span data-stu-id="91d8a-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="91d8a-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>，它會從記憶體集區配置強型別記憶體區塊到擁有者。</span><span class="sxs-lookup"><span data-stu-id="91d8a-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="91d8a-115"><xref:System.Buffers.IMemoryOwner%601> 執行個體可從集區租借，方式是呼叫 <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> 並透過呼叫 <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> 釋放回集區。</span><span class="sxs-lookup"><span data-stu-id="91d8a-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="91d8a-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>，這代表記憶體區塊擁有者並控制其生命週期管理。</span><span class="sxs-lookup"><span data-stu-id="91d8a-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="91d8a-117"><xref:System.Buffers.MemoryManager%601>，它是抽象基底類別，可用於取代 <xref:System.Memory%601> 的實作，以便 <xref:System.Memory%601> 可由額外類型 (例如安全控制代碼) 支持。</span><span class="sxs-lookup"><span data-stu-id="91d8a-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="91d8a-118"><xref:System.Buffers.MemoryManager%601> 是用於進階案例。</span><span class="sxs-lookup"><span data-stu-id="91d8a-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="91d8a-119"><xref:System.ArraySegment%601>，它是特定陣列元素 (從特定索引開始) 數目的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="91d8a-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="91d8a-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>，它是擴充方法集合，這些擴充方法可用來將字串、陣列與陣列區段轉換為 <xref:System.Memory%601> 區塊。</span><span class="sxs-lookup"><span data-stu-id="91d8a-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="91d8a-121">針對較早的架構，<xref:System.Span%601> 與 <xref:System.Memory%601> 可在 [System.Memory NuGet 套件](https://www.nuget.org/packages/System.Memory/)中找到。</span><span class="sxs-lookup"><span data-stu-id="91d8a-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="91d8a-122">如需詳細資訊，請參閱 <xref:System.Buffers?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="91d8a-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="91d8a-123">處理記憶體與延伸</span><span class="sxs-lookup"><span data-stu-id="91d8a-123">Working with memory and span</span></span>

<span data-ttu-id="91d8a-124">因為記憶體與延伸相關類型通常用於將資料存放在處理管線中，開發人員在使用<xref:System.Span%601>、<xref:System.Memory%601> 與相關類型時務必依照一組最佳作法執行。</span><span class="sxs-lookup"><span data-stu-id="91d8a-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="91d8a-125">這些最佳做法記錄在[記憶體\<T>與延伸\<T> 使用指導方針](memory-t-usage-guidelines.md)中。</span><span class="sxs-lookup"><span data-stu-id="91d8a-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91d8a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d8a-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>