---
title: dotnet-計數器-.NET Core
description: 瞭解如何安裝和使用 dotnet-counter 命令列工具。
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: b2fab239713d9d19c580580496e73a91ceafcc52
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321586"
---
# <a name="dotnet-counters"></a><span data-ttu-id="1ce61-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="1ce61-103">dotnet-counters</span></span>

<span data-ttu-id="1ce61-104">**本文適用于：✓** .net CORE 3.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="1ce61-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="1ce61-105">安裝 dotnet-計數器</span><span class="sxs-lookup"><span data-stu-id="1ce61-105">Install dotnet-counters</span></span>

<span data-ttu-id="1ce61-106">若要安裝 `dotnet-counters` [NuGet 套件](https://www.nuget.org/packages/dotnet-counters)的最新發行版本，請使用[dotnet tool install](../tools/dotnet-tool-install.md)命令：</span><span class="sxs-lookup"><span data-stu-id="1ce61-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="1ce61-107">概要</span><span class="sxs-lookup"><span data-stu-id="1ce61-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="1ce61-108">描述</span><span class="sxs-lookup"><span data-stu-id="1ce61-108">Description</span></span>

<span data-ttu-id="1ce61-109">`dotnet-counters` 是一種效能監視工具，可用於臨機操作健全狀況監視和第一層效能調查。</span><span class="sxs-lookup"><span data-stu-id="1ce61-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="1ce61-110">它可以觀察透過 <xref:System.Diagnostics.Tracing.EventCounter> API 發佈的效能計數器值。</span><span class="sxs-lookup"><span data-stu-id="1ce61-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="1ce61-111">例如，您可以快速監視 CPU 使用量，或 .NET Core 應用程式中擲回之例外狀況的速率，以查看使用 `PerfView` 或 `dotnet-trace` 進行更嚴重的效能調查之前是否有任何可疑的問題。</span><span class="sxs-lookup"><span data-stu-id="1ce61-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="1ce61-112">選項</span><span class="sxs-lookup"><span data-stu-id="1ce61-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="1ce61-113">顯示 dotnet 計數器公用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="1ce61-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1ce61-114">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="1ce61-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="1ce61-115">命令</span><span class="sxs-lookup"><span data-stu-id="1ce61-115">Commands</span></span>

| <span data-ttu-id="1ce61-116">命令</span><span class="sxs-lookup"><span data-stu-id="1ce61-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="1ce61-117">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="1ce61-117">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="1ce61-118">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="1ce61-118">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a><span data-ttu-id="1ce61-119">dotnet-計數器清單</span><span class="sxs-lookup"><span data-stu-id="1ce61-119">dotnet-counters list</span></span>

<span data-ttu-id="1ce61-120">顯示計數器名稱和描述的清單，依提供者分組。</span><span class="sxs-lookup"><span data-stu-id="1ce61-120">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1ce61-121">概要</span><span class="sxs-lookup"><span data-stu-id="1ce61-121">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="1ce61-122">範例</span><span class="sxs-lookup"><span data-stu-id="1ce61-122">Example</span></span>

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="1ce61-123">dotnet-計數器監視</span><span class="sxs-lookup"><span data-stu-id="1ce61-123">dotnet-counters monitor</span></span>

<span data-ttu-id="1ce61-124">顯示已選取計數器的定期重新整理值。</span><span class="sxs-lookup"><span data-stu-id="1ce61-124">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1ce61-125">概要</span><span class="sxs-lookup"><span data-stu-id="1ce61-125">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="1ce61-126">選項</span><span class="sxs-lookup"><span data-stu-id="1ce61-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="1ce61-127">要監視之進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1ce61-127">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="1ce61-128">更新所顯示計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="1ce61-128">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="1ce61-129">以空格分隔的計數器清單。</span><span class="sxs-lookup"><span data-stu-id="1ce61-129">A space separated list of counters.</span></span> <span data-ttu-id="1ce61-130">@No__t_0 可以指定計數器。</span><span class="sxs-lookup"><span data-stu-id="1ce61-130">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="1ce61-131">如果在沒有符合資格的 `counter_name` 的情況下使用 `provider_name`，則會顯示所有計數器。</span><span class="sxs-lookup"><span data-stu-id="1ce61-131">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="1ce61-132">若要探索提供者和計數器名稱，請使用[dotnet-計數器 list](#dotnet-counters-list)命令。</span><span class="sxs-lookup"><span data-stu-id="1ce61-132">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="1ce61-133">範例</span><span class="sxs-lookup"><span data-stu-id="1ce61-133">Examples</span></span>

- <span data-ttu-id="1ce61-134">以3秒的重新整理間隔監視 `System.Runtime` 的所有計數器：</span><span class="sxs-lookup"><span data-stu-id="1ce61-134">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="1ce61-135">僅監視 `System.Runtime` 的 CPU 使用量和 GC 堆積大小：</span><span class="sxs-lookup"><span data-stu-id="1ce61-135">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="1ce61-136">從使用者定義的 `EventSource` 監視 `EventCounter` 值。</span><span class="sxs-lookup"><span data-stu-id="1ce61-136">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="1ce61-137">如需詳細資訊，請參閱[教學課程：如何使用 EventCounters 測量非常頻繁事件的效能](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="1ce61-137">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
