---
title: 點網計數器 - .NET 核心
description: 瞭解如何安裝和使用點網計數器命令列工具。
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147174"
---
# <a name="dotnet-counters"></a><span data-ttu-id="9f4ed-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="9f4ed-103">dotnet-counters</span></span>

<span data-ttu-id="9f4ed-104">**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="9f4ed-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="9f4ed-105">安裝點網計數器</span><span class="sxs-lookup"><span data-stu-id="9f4ed-105">Install dotnet-counters</span></span>

<span data-ttu-id="9f4ed-106">要安裝最新版本的`dotnet-counters` [NuGet 包](https://www.nuget.org/packages/dotnet-counters)，請使用[dotnet 工具安裝](../tools/dotnet-tool-install.md)命令：</span><span class="sxs-lookup"><span data-stu-id="9f4ed-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="9f4ed-107">概要</span><span class="sxs-lookup"><span data-stu-id="9f4ed-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="9f4ed-108">描述</span><span class="sxs-lookup"><span data-stu-id="9f4ed-108">Description</span></span>

<span data-ttu-id="9f4ed-109">`dotnet-counters`是用於臨時運行狀況監控和一級績效調查的性能監控工具。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="9f4ed-110">它可以觀察通過<xref:System.Diagnostics.Tracing.EventCounter>API 發佈的效能計數器值。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="9f4ed-111">例如，您可以快速監視 CPU 使用率或引發到 .NET Core 應用程式中的異常率等內容，以查看在使用`PerfView`或`dotnet-trace`進行更嚴肅的性能調查之前，是否有可疑之處。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="9f4ed-112">選項。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="9f4ed-113">顯示點網計數器實用程式的版本。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9f4ed-114">顯示命令列説明。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="9f4ed-115">命令</span><span class="sxs-lookup"><span data-stu-id="9f4ed-115">Commands</span></span>

| <span data-ttu-id="9f4ed-116">Command</span><span class="sxs-lookup"><span data-stu-id="9f4ed-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="9f4ed-117">點網計數器收集</span><span class="sxs-lookup"><span data-stu-id="9f4ed-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="9f4ed-118">點網計數器清單</span><span class="sxs-lookup"><span data-stu-id="9f4ed-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="9f4ed-119">點網計數器監視器</span><span class="sxs-lookup"><span data-stu-id="9f4ed-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="9f4ed-120">點網計數器 ps</span><span class="sxs-lookup"><span data-stu-id="9f4ed-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="9f4ed-121">點網計數器收集</span><span class="sxs-lookup"><span data-stu-id="9f4ed-121">dotnet-counters collect</span></span>

<span data-ttu-id="9f4ed-122">定期收集選定的計數器值並將其匯出到指定的檔案格式以進行後處理。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9f4ed-123">概要</span><span class="sxs-lookup"><span data-stu-id="9f4ed-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="9f4ed-124">選項。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9f4ed-125">要監視的進程的 ID。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="9f4ed-126">更新顯示的計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="9f4ed-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="9f4ed-127">計數器的空間分隔清單。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-127">A space separated list of counters.</span></span> <span data-ttu-id="9f4ed-128">可以指定`provider_name[:counter_name]`計數器。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="9f4ed-129">`provider_name`如果使用時沒有限定`counter_name`，則顯示所有計數器。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="9f4ed-130">要發現提供程式和計數器名稱，請使用[dotnet 計數器清單](#dotnet-counters-list)命令。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="9f4ed-131">T 要匯出的格式。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-131">TThe format to be exported.</span></span> <span data-ttu-id="9f4ed-132">當前可用： csv， json.</span><span class="sxs-lookup"><span data-stu-id="9f4ed-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="9f4ed-133">輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="9f4ed-134">範例</span><span class="sxs-lookup"><span data-stu-id="9f4ed-134">Examples</span></span>

- <span data-ttu-id="9f4ed-135">以 3 秒的刷新間隔收集所有計數器，並將 csv 生成為輸出：</span><span class="sxs-lookup"><span data-stu-id="9f4ed-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="9f4ed-136">點網計數器清單</span><span class="sxs-lookup"><span data-stu-id="9f4ed-136">dotnet-counters list</span></span>

<span data-ttu-id="9f4ed-137">顯示按提供程式分組的計數器名稱和說明的清單。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9f4ed-138">概要</span><span class="sxs-lookup"><span data-stu-id="9f4ed-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="9f4ed-139">範例</span><span class="sxs-lookup"><span data-stu-id="9f4ed-139">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="9f4ed-140">點網計數器監視器</span><span class="sxs-lookup"><span data-stu-id="9f4ed-140">dotnet-counters monitor</span></span>

<span data-ttu-id="9f4ed-141">顯示所選計數器的定期刷新值。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9f4ed-142">概要</span><span class="sxs-lookup"><span data-stu-id="9f4ed-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="9f4ed-143">選項。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9f4ed-144">要監視的進程的 ID。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="9f4ed-145">更新顯示的計數器之間的延遲秒數</span><span class="sxs-lookup"><span data-stu-id="9f4ed-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="9f4ed-146">計數器的空間分隔清單。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-146">A space separated list of counters.</span></span> <span data-ttu-id="9f4ed-147">可以指定`provider_name[:counter_name]`計數器。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="9f4ed-148">`provider_name`如果使用時沒有限定`counter_name`，則顯示所有計數器。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="9f4ed-149">要發現提供程式和計數器名稱，請使用[dotnet 計數器清單](#dotnet-counters-list)命令。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="9f4ed-150">範例</span><span class="sxs-lookup"><span data-stu-id="9f4ed-150">Examples</span></span>

- <span data-ttu-id="9f4ed-151">`System.Runtime`以 3 秒的刷新間隔監控所有計數器：</span><span class="sxs-lookup"><span data-stu-id="9f4ed-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="9f4ed-152">僅從 監控 CPU 使用率`System.Runtime`和 GC 堆大小：</span><span class="sxs-lookup"><span data-stu-id="9f4ed-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="9f4ed-153">監視`EventCounter`使用者定義的`EventSource`值。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="9f4ed-154">有關詳細資訊，請參閱[教程：如何使用事件計數器測量非常頻繁事件的性能](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="9f4ed-155">點網計數器 ps</span><span class="sxs-lookup"><span data-stu-id="9f4ed-155">dotnet-counters ps</span></span>

<span data-ttu-id="9f4ed-156">顯示可監視的 dotnet 進程的清單。</span><span class="sxs-lookup"><span data-stu-id="9f4ed-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9f4ed-157">概要</span><span class="sxs-lookup"><span data-stu-id="9f4ed-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="9f4ed-158">範例</span><span class="sxs-lookup"><span data-stu-id="9f4ed-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
