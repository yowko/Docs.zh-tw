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

# <a name="memory--and-span-related-types"></a>記憶體與延伸相關類型

從 .NET Core 2.1 開始，.NET 就包括一些相關類型，這些類型代表連續的強型別任意記憶體區域。 它們包括：

- <xref:System.Span%601?displayProperty=nameWithType>，此類型是用來存取連續記憶體區域。 <xref:System.Span%601> 執行個體可由類型 `T` 的陣列、<xref:System.String>、使用[stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) 配置的緩衝區或非受控記憶體的指標來支持。 因為它必須在堆疊上配置，它有一些限制。 例如，類別中欄位的類型不能是 <xref:System.Span%601>，而且延伸也不能用於非同步作業中。

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>，這是 <xref:System.Span%601> 結構的不可變版本。

- <xref:System.Memory%601?displayProperty=nameWithType>，這是在受空堆積而非堆疊上配置的連續記憶體區域。 <xref:System.Memory%601> 執行個體可由類型為 `T` 的陣列或 <xref:System.String> 支持。 因為它可以存放在受控堆積上，<xref:System.Memory%601> 有沒有 <xref:System.Span%601> 的任何限制。

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>，這是 <xref:System.Memory%601> 結構的不可變版本。

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>，它會從記憶體集區配置強型別記憶體區塊到擁有者。 <xref:System.Buffers.IMemoryOwner%601> 執行個體可從集區租借，方式是呼叫 <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> 並透過呼叫 <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> 釋放回集區。

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>，這代表記憶體區塊擁有者並控制其生命週期管理。

- <xref:System.Buffers.MemoryManager%601>，它是抽象基底類別，可用於取代 <xref:System.Memory%601> 的實作，以便 <xref:System.Memory%601> 可由額外類型 (例如安全控制代碼) 支持。 <xref:System.Buffers.MemoryManager%601> 是用於進階案例。

- <xref:System.ArraySegment%601>，它是特定陣列元素 (從特定索引開始) 數目的包裝函式。

- <xref:System.MemoryExtensions?displayProperty=nameWithType>，它是擴充方法集合，這些擴充方法可用來將字串、陣列與陣列區段轉換為 <xref:System.Memory%601> 區塊。

> [!NOTE]
> 針對較早的架構，<xref:System.Span%601> 與 <xref:System.Memory%601> 可在 [System.Memory NuGet 套件](https://www.nuget.org/packages/System.Memory/)中找到。

如需詳細資訊，請參閱 <xref:System.Buffers?displayProperty=nameWithType>。

## <a name="working-with-memory-and-span"></a>處理記憶體與延伸

因為記憶體與延伸相關類型通常用於將資料存放在處理管線中，開發人員在使用<xref:System.Span%601>、<xref:System.Memory%601> 與相關類型時務必依照一組最佳作法執行。 這些最佳做法記錄在[記憶體\<T>與延伸\<T> 使用指導方針](memory-t-usage-guidelines.md)中。

## <a name="see-also"></a>另請參閱

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>