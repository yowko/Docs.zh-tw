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
# <a name="dotnet-counters"></a>dotnet-counters

**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本

## <a name="install-dotnet-counters"></a>安裝點網計數器

要安裝最新版本的`dotnet-counters` [NuGet 包](https://www.nuget.org/packages/dotnet-counters)，請使用[dotnet 工具安裝](../tools/dotnet-tool-install.md)命令：

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>概要

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-counters`是用於臨時運行狀況監控和一級績效調查的性能監控工具。 它可以觀察通過<xref:System.Diagnostics.Tracing.EventCounter>API 發佈的效能計數器值。 例如，您可以快速監視 CPU 使用率或引發到 .NET Core 應用程式中的異常率等內容，以查看在使用`PerfView`或`dotnet-trace`進行更嚴肅的性能調查之前，是否有可疑之處。

## <a name="options"></a>選項。

- **`--version`**

  顯示點網計數器實用程式的版本。

- **`-h|--help`**

  顯示命令列説明。

## <a name="commands"></a>命令

| Command                                             |
| --------------------------------------------------- |
| [點網計數器收集](#dotnet-counters-collect) |
| [點網計數器清單](#dotnet-counters-list)       |
| [點網計數器監視器](#dotnet-counters-monitor) |
| [點網計數器 ps](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>點網計數器收集

定期收集選定的計數器值並將其匯出到指定的檔案格式以進行後處理。

### <a name="synopsis"></a>概要

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>選項。

- **`-p|--process-id <PID>`**

  要監視的進程的 ID。

- **`--refresh-interval <SECONDS>`**

  更新顯示的計數器之間的延遲秒數

- **`counter_list <COUNTERS>`**

  計數器的空間分隔清單。 可以指定`provider_name[:counter_name]`計數器。 `provider_name`如果使用時沒有限定`counter_name`，則顯示所有計數器。 要發現提供程式和計數器名稱，請使用[dotnet 計數器清單](#dotnet-counters-list)命令。

- **`--format <csv|json>`**

  T 要匯出的格式。 當前可用： csv， json.

- **`-o|--output <output>`**

  輸出檔案的名稱。

### <a name="examples"></a>範例

- 以 3 秒的刷新間隔收集所有計數器，並將 csv 生成為輸出：

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>點網計數器清單

顯示按提供程式分組的計數器名稱和說明的清單。

### <a name="synopsis"></a>概要

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>範例

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

## <a name="dotnet-counters-monitor"></a>點網計數器監視器

顯示所選計數器的定期刷新值。

### <a name="synopsis"></a>概要

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>選項。

- **`-p|--process-id <PID>`**

  要監視的進程的 ID。

- **`--refresh-interval <SECONDS>`**

  更新顯示的計數器之間的延遲秒數

- **`counter_list <COUNTERS>`**

  計數器的空間分隔清單。 可以指定`provider_name[:counter_name]`計數器。 `provider_name`如果使用時沒有限定`counter_name`，則顯示所有計數器。 要發現提供程式和計數器名稱，請使用[dotnet 計數器清單](#dotnet-counters-list)命令。

### <a name="examples"></a>範例

- `System.Runtime`以 3 秒的刷新間隔監控所有計數器：

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

- 僅從 監控 CPU 使用率`System.Runtime`和 GC 堆大小：

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- 監視`EventCounter`使用者定義的`EventSource`值。 有關詳細資訊，請參閱[教程：如何使用事件計數器測量非常頻繁事件的性能](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)。

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>點網計數器 ps

顯示可監視的 dotnet 進程的清單。

### <a name="synopsis"></a>概要

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>範例

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
