---
title: 記憶體回收的基本概念
description: 了解記憶體回收行程如何運作，以及如何為它設定最佳效能。
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330422"
---
# <a name="fundamentals-of-garbage-collection"></a>記憶體回收的基本概念

In the common language runtime (CLR), the garbage collector (GC) serves as an automatic memory manager. 它提供了下列優點：

- Enables you to develop your application without having to manually free memory.

- 有效率地在 Managed 堆積上配置物件。

- 回收不再使用的物件、清除其記憶體，並且讓記憶體可供未來的配置使用。 Managed 物件在開始時會自動取得乾淨的內容，因此其建構函式不需要初始化每個資料欄位。

- 確保某個物件無法使用另一個物件的內容，藉以提供記憶體安全性。

This article describes the core concepts of garbage collection.

## <a name="fundamentals-of-memory"></a>記憶體的基本概念

下列清單摘要說明重要的 CLR 記憶體概念。

- 每個處理序都有各自獨立的虛擬位址空間。 All processes on the same computer share the same physical memory and the page file, if there is one.

- 根據預設，在 32 位元電腦上，每個處理序都有 2 GB 使用者模式虛擬位址空間。

- 身為應用程式開發人員，您只會處理虛擬位址空間，絕不會直接操作實體記憶體。 記憶體回收行程會在 Managed 堆積上自動配置和釋出虛擬記憶體。

  If you are writing native code, you use Windows functions to work with the virtual address space. 這些函式會在原生堆積上自動配置和釋出虛擬記憶體。

- 虛擬記憶體可以有三種狀態：

  - 可用。 記憶體區塊沒有任何參考，可進行配置。

  - 保留的。 記憶體區塊可供您使用，但是無法用於任何其他配置要求。 不過，在此記憶體區塊認可之前，您無法將資料儲存到其中。

  - 已認可。 記憶體區塊會指派給實體儲存區。

- 虛擬位址空間可能會分成片段。 這表示，位址空間中有可用的區塊，也稱為可用的洞 (Hole)。 要求虛擬記憶體配置時，虛擬記憶體管理程式必須找到大小可滿足配置要求的單一可用區塊。 即使您擁有 2GB 可用空間，要求 2GB 的配置仍然不會成功，除非該可用空間全都在單一位址區塊中。

- You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit.

  The page file is used even if physical memory pressure (that is, demand for physical memory) is low. The first time physical memory pressure is high, the operating system must make room in physical memory to store data, and it backs up some of the data that is in physical memory to the page file. That data is not paged until it's needed, so it's possible to encounter paging in situations where the physical memory pressure is low.

## <a name="conditions-for-a-garbage-collection"></a>記憶體回收的條件

當下列其中一個條件成立時，就會進行記憶體回收：

- 系統的實體記憶體不足。 This is detected by either the low memory notification from the OS or low memory as indicated by the host.

- 由 Managed 堆積上之已配置物件所使用的記憶體超過可接受的臨界值。 這個臨界值會在處理序執行時持續調整。

- 已呼叫 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 方法。 在大多數的情況下，您不需要呼叫這個方法，因為記憶體回收行程會持續執行。 這個方法主要用於獨特的情況和測試。

## <a name="the-managed-heap"></a>Managed 堆積

CLR 初始化記憶體回收行程之後，記憶體回收行程就會配置用來儲存和管理物件的記憶體區段。 這個記憶體稱為 Managed 堆積，與作業系統中的原生堆積相反。

每個 Managed 處理序都有一個 Managed 堆積。 處理序中的所有執行緒都會對相同堆積上的物件配置記憶體。

To reserve memory, the garbage collector calls the Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) function and reserves one segment of memory at a time for managed applications. The garbage collector also reserves segments, as needed, and releases segments back to the operating system (after clearing them of any objects) by calling the Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) function.

> [!IMPORTANT]
> 記憶體回收行程所配置的區段大小是依實作而定，有可能在任何時間，包括在定期更新時做變更。 您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。

配置在堆積上的物件越少，記憶體回收行程必須進行的工作就越少。 當您配置物件時，請勿使用超出需求的進位值，例如，當您只需要 15 個位元組時，卻配置 32 個位元組的陣列。

觸發記憶體回收時，記憶體回收行程就會回收無作用物件所佔據的記憶體。 回收處理序會壓縮使用中物件，讓它們集合在一起，並且移除無作用物件，因而讓堆積更小。 這樣可確保一起配置的物件會在 Managed 堆積上集中，以便保持其區域性。

記憶體回收的干擾程度 (頻率和持續期間) 是 Managed 堆積上之配置量和未被回收記憶體數量的結果。

您可以將此堆積視為兩個堆積的累積：[大型物件堆積](large-object-heap.md)和小型物件堆積。

[大型物件堆積](large-object-heap.md)包含 85,000 個位元組以上的超大型物件。 大型物件堆積上的物件通常是陣列。 超大型的執行個體物件非常罕見。

> [!TIP]
> You can [configure the threshold size](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) for objects to go on the large object heap.

## <a name="generations"></a>層代

堆積會組織成層代，因此它可以處理存留較久和存留較短的物件。 記憶體回收主要與存留較短物件的回收一起進行，而這些物件通常只佔據堆積的一小部分。 堆積上的物件有三個層代：

- **層代 0**。 這是最新的層代而且包含存留較短的物件。 存留較短的物件範例是暫存變數。 記憶體回收最常在這個層代中進行。

  Newly allocated objects form a new generation of objects and are implicitly generation 0 collections. However, if they are large objects, they go on the large object heap in a generation 2 collection.

  大部分物件都會在層代 0 的記憶體回收中回收，而且不會存留至下一個層代。

- **層代 1**。 這個層代包含存留較短的物件，而且當做存留較短物件與存留較長物件之間的緩衝區。

- **層代 2**。 這個層代包含存留較長的物件。 An example of a long-lived object is an object in a server application that contains static data that's live for the duration of the process.

當條件許可時，記憶體回收會針對特定層代進行。 回收層代是指回收該層代中的物件及其所有較新的層代。 層代 2 記憶體回收也稱為完整記憶體回收，因為它會回收所有層代中的所有物件 (亦即，Managed 堆積中的所有物件)。

### <a name="survival-and-promotions"></a>未回收和提升

Objects that are not reclaimed in a garbage collection are known as survivors and are promoted to the next generation. 在層代 0 記憶體回收中未被回收的物件會提升至層代 1、在層代 1 記憶體回收中未被回收的物件會提升至層代 2，而在層代 2 記憶體回收中未被回收的物件則保留在層代 2 中。

When the garbage collector detects that the survival rate is high in a generation, it increases the threshold of allocations for that generation. The next collection gets a substantial size of reclaimed memory. The CLR continually balances two priorities: not letting an application's working set get too large by delaying garbage collection and not letting the garbage collection run too frequently.

### <a name="ephemeral-generations-and-segments"></a>暫時層代和區段

因為層代 0 和 1 中的物件存留較短，所以這些層代稱為暫時層代。

暫時層代必須配置於稱為暫時區段的記憶體區段中。 記憶體回收行程所取得的每個新區段都會成為新的暫時區段，而且包含在層代 0 記憶體回收中未被回收的物件。 舊的暫時區段會成為新的層代 2 區段。

The size of the ephemeral segment varies depending on whether a system is 32-bit or 64-bit, and on the type of garbage collector it is running. 下表顯示預設值。

||32 位元|64 位元|
|-|-------------|-------------|
|工作站 GC|16 MB|256 MB|
|伺服器 GC|64 MB|4 GB|
|具有多於 4 個邏輯 CPU 的伺服器 GC|32 MB|2 GB|
|具有 > 8 個邏輯 CPU 的伺服器 GC|16 MB|1 GB|

暫時區段可能會包括層代 2 物件。 層代 2 物件可以使用多個區段 (取決於處理序所需而且記憶體允許的數目)。

暫時記憶體回收中釋放記憶體的數量會限制為暫時區段的大小。 所釋放的記憶體數量會與無作用物件所佔據的空間成正比。

## <a name="what-happens-during-a-garbage-collection"></a>記憶體回收期間進行的作業

記憶體回收具有下列階段：

- 標記階段：尋找和建立所有使用中物件的清單。

- 重新配置階段：更新即將壓縮之物件的參考。

- 壓縮階段：回收無作用物件所佔據的空間並壓縮未被回收的物件。 壓縮階段會將記憶體回收中未被回收的物件移至區段的較舊端。

  因為層代 2 回收可能會佔據多個區段，所以提升至層代 2 的物件可能會移至較舊區段。 層代 1 和層代 2 的未回收物件都可能會移至不同的區段，因為它們都會被提升至層代 2。

  Ordinarily, the large object heap (LOH) is not compacted, because copying large objects imposes a performance penalty. However, in .NET Core and in .NET Framework 4.5.1 and later, you can use the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property to compact the large object heap on demand. In addition, the LOH is automatically compacted when a hard limit is set by specifying either:

  - a memory limit on a container, or
  - the [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) or [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) run-time configuration options

記憶體回收行程會使用下列資訊來判斷物件是否使用中：

- **堆疊根目錄**。 Just-in-Time (JIT) 編譯器和堆疊查核器所提供的堆疊變數。 JIT optimizations can lengthen or shorten regions of code within which stack variables are reported to the garbage collector.

- **記憶體回收控制代碼**。 會指向 Managed 物件，而且可由使用者程式碼或 Common Language Runtime 配置的控制代碼。

- **靜態資料**。 應用程式定義域中可能參考其他物件的靜態物件。 每個應用程式定義域都會追蹤其靜態物件。

記憶體回收開始之前，所有 Managed 執行緒都會暫停，但觸發記憶體回收的執行緒除外。

下圖顯示觸發記憶體回收且造成其他執行緒暫停的執行緒。

![當執行緒觸發記憶體回收時](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipulate unmanaged resources

If managed objects reference unmanaged objects by using their native file handles, you have to explicitly free the unmanaged objects, because the garbage collector only tracks memory on the managed heap.

Users of the managed object may not dispose the native resources used by the object. To perform the cleanup, you can make the managed object finalizable. Finalization consists of cleanup actions that execute when the object is no longer in use. When the managed object dies, it performs cleanup actions that are specified in its finalizer method.

當系統發現某個可最終處理物件無作用時，該物件的完成項就會放入佇列中，以便執行其清除動作，但是物件本身會提升至下一個層代。 因此，您必須等候直到在該層代上進行的下一次記憶體回收 (不一定是下一次記憶體回收)，以便判斷此物件是否已經回收。

For more information about finalization, see <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>工作站和伺服器記憶體回收

記憶體回收行程會自行調整而且可在各種案例中運作。 You can use a [configuration file setting](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) to set the type of garbage collection based on the characteristics of the workload. CLR 會提供下列記憶體回收類型：

- Workstation garbage collection (GC) is designed for client apps. It is the default GC flavor for standalone apps. For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.

  工作站記憶體回收可能是並行或非並行的。 並行記憶體回收可讓 Managed 執行緒在記憶體回收期間繼續運作。 [Background garbage collection](#background-workstation-garbage-collection) replaces [concurrent garbage collection](#concurrent-garbage-collection) in .NET Framework 4 and later versions.

- 伺服器記憶體回收，適用於需要高輸送量和延展性的伺服器應用程式。

  - In .NET Core, server garbage collection can be non-concurrent or background.

  - In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background (background garbage collection replaces concurrent garbage collection). In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.

The following illustration shows the dedicated threads that perform the garbage collection on a server:

![伺服器記憶體回收執行緒](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Compare workstation and server garbage collection

以下是工作站記憶體回收的執行緒和效能考量：

- 此回收會針對觸發記憶體回收的使用者執行緒進行，而且維持相同的優先權。 因為使用者執行緒通常會以一般優先權執行，所以記憶體回收行程 (在一般優先權執行緒上執行) 必須與其他執行緒爭用 CPU 時間。 (Threads that run native code are not suspended on either server or workstation garbage collection.)

- Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

以下是伺服器記憶體回收的執行緒和效能考量：

- 此回收會針對以 `THREAD_PRIORITY_HIGHEST` 優先權層級執行的多個專屬執行緒進行。

- 執行記憶體回收的堆積和專屬執行緒是針對每個 CPU 提供的，而且這些堆積會同時回收。 每個堆積都包含小型物件堆積和大型物件堆積，而且所有堆積都可由使用者程式碼存取。 不同堆積上的物件可以彼此參考。

- 因為多個記憶體回收執行緒會一起運作，所以就相同大小堆積而言，伺服器記憶體回收的速度比工作站記憶體回收的速度要快。

- 伺服器記憶體回收通常具有較大的區段。 However, this is only a generalization: segment size is implementation-specific and is subject to change. Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.

- 伺服器記憶體回收可能會耗用大量資源。 For example, imagine that there are 12 processes that use server GC running on a computer that has 4 processors. If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor. If the processes are active, it's not a good idea to have them all use server GC.

If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled. 這樣會產生較少的內容切換，因此可能會改善效能。

## <a name="background-workstation-garbage-collection"></a>背景工作站記憶體回收

In background workstation garbage collection, ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress. Background workstation garbage collection is performed on a dedicated thread and applies only to generation 2 collections.

Background garbage collection is enabled by default and can be enabled or disabled with the [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework apps or the [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) setting in .NET Core apps.

> [!NOTE]
> Background garbage collection replaces [concurrent garbage collection](#concurrent-garbage-collection) and is available in .NET Framework 4 and later versions. In .NET Framework 4, it's supported only for workstation garbage collection. Starting with .NET Framework 4.5, background garbage collection is available for both workstation and server garbage collection.

背景記憶體回收期間，暫時層代的回收稱為前景記憶體回收。 進行前景記憶體回收時，所有 Managed 執行緒都會暫停。

When background garbage collection is in progress and you've allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection. 專屬的背景記憶體回收執行緒會在經常安全點檢查，以便判斷是否存在前景記憶體回收的要求。 如果有，背景回收就會自行暫停，讓前景記憶體回收能夠進行。 在前景記憶體回收完成之後，專屬的背景記憶體回收執行緒和使用者執行緒就會繼續進行。

背景記憶體回收會移除並行記憶體回收所加諸的配置限制，因為暫時記憶體回收可能會在背景記憶體回收期間進行。 Background garbage collection can remove dead objects in ephemeral generations. It can also expand the heap if needed during a generation 1 garbage collection.

下圖顯示在工作站上另一個專用執行緒上執行的背景記憶體回收：

![背景工作站記憶體回收](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>背景伺服器記憶體回收

Starting with .NET Framework 4.5, background server garbage collection is the default mode for server garbage collection.

Background server garbage collection functions similarly to background workstation garbage collection, described in the previous section, but there are a few differences:

- Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads. Typically, there's a dedicated thread for each logical processor.

- 與工作站背景記憶體回收執行緒不同的是，這些執行緒不會逾時。

下圖顯示在伺服器上另一個專用執行緒上執行的背景記憶體回收：

![背景伺服器記憶體回收](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>並行的記憶體回收

> [!TIP]
> This section applies to:
>
> - .NET Framework 3.5 and earlier for workstation garbage collection
> - .NET Framework 4 and earlier for server garbage collection
>
> Concurrent garbage is replaced by [background garbage collection](#background-workstation-garbage-collection) in later versions.

In workstation or server garbage collection, you can [enable concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection. 這個選項只會影響層代 2 中的記憶體回收。層代 0 和 1 一律為非並行，因為它們的完成速度非常快。

並行記憶體回收會將回收期間的暫停降到最低，藉以加快互動式應用程式的回應速度。 當並行記憶體回收執行緒正在執行時，Managed 執行緒幾乎可以繼續執行。 這會在記憶體回收進行時縮短暫停時間。

並行記憶體回收會針對專屬執行緒執行。 根據預設，CLR 會執行工作站記憶體回收並啟用並行記憶體回收。 這種回收適用於單一處理器和多處理器電腦。

下列圖例顯示在分開的專屬執行緒上執行的並行記憶體回收。

![並行記憶體回收執行緒](./media/gc-concurrent.png)

## <a name="see-also"></a>請參閱

- [Configuration options for GC](../../core/run-time-config/garbage-collector.md)
- [記憶體回收](index.md)
