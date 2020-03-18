---
title: 調試記憶體洩漏教程
description: 瞭解如何在 .NET Core 中調試記憶體洩漏。
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737739"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>教程：在 .NET 核心中調試記憶體洩漏

**本文適用于：✔️** .NET Core 3.0 SDK 和更高版本

本教程演示了分析 .NET 核心記憶體洩漏的工具。

本教程使用示例應用，該應用旨在有意洩漏記憶體。 示例作為練習提供。 您可以分析無意中洩漏記憶體的應用。

在本教學課程中，您將：

> [!div class="checklist"]
>
> - 使用[點網計數器](dotnet-counters.md)檢查託管記憶體使用方式。
> - 生成轉儲檔。
> - 使用轉儲檔分析記憶體使用方式。

## <a name="prerequisites"></a>必要條件

教學課程會使用：

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。
- [點網跟蹤](dotnet-trace.md)到清單進程。
- [點網計數器](dotnet-counters.md)，用於檢查託管記憶體使用方式。
- [點網轉儲](dotnet-dump.md)以收集和分析轉儲檔。
- 要診斷[的示例調試目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)應用。

本教程假定示例和工具已安裝並可供使用。

## <a name="examine-managed-memory-usage"></a>檢查託管記憶體使用方式

在開始收集診斷資料以説明我們根本原因此方案之前，您需要確保實際看到記憶體洩漏（記憶體增長）。 您可以使用[點網計數器](dotnet-counters.md)工具來確認這一點。

打開主控台視窗並導航到下載的目錄並解壓縮[示例調試目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)。 運行目標：

```dotnetcli
dotnet run
```

從單獨的主控台，使用[點網跟蹤](dotnet-trace.md)工具查找進程 ID：

```console
dotnet-trace ps
```

輸出應該會類似：

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

現在，使用[點網計數器](dotnet-counters.md)工具檢查託管記憶體使用方式。 指定`--refresh-interval`刷新之間的秒數：

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

即時輸出應類似于：

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

專注于這條線：

```console
    GC Heap Size (MB)                                  4
```

您可以看到託管堆記憶體在啟動後立即為 4 MB。

現在，點擊 URL `http://localhost:5000/api/diagscenario/memleak/20000`。

觀察記憶體使用量已增長到 30 MB。

```console
    GC Heap Size (MB)                                 30
```

通過觀察記憶體使用方式，您可以安全地說記憶體在增長或洩漏。 下一步是收集正確的記憶體分析資料。

### <a name="generate-memory-dump"></a>生成記憶體傾印

分析可能的記憶體洩漏時，您需要訪問應用的記憶體堆。 然後，您可以分析記憶體內容。 觀察物件之間的關係，您創建關於為什麼記憶沒有被釋放的理論。 常見的診斷資料來源是 Windows 上的記憶體傾印或 Linux 上的等效核心轉儲。 要生成 .NET Core 應用程式的轉儲，可以使用[dotnet 轉儲）](dotnet-dump.md)工具。

使用以前啟動[的示例調試目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，運行以下命令以生成 Linux 核心轉儲：

```dotnetcli
dotnet-dump collect -p 4807
```

結果是位於同一資料夾中的核心轉儲。

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>重新開機失敗的進程

收集轉儲後，您應該有足夠的資訊來診斷失敗的進程。 如果失敗的進程在生產伺服器上運行，現在正是通過重新開機流程進行短期補救的理想時間。

在本教程中，您現在已完成[示例調試目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，您可以關閉它。 導航到啟動伺服器的終端，然後按`Control-C`。

### <a name="analyze-the-core-dump"></a>分析核心轉儲

生成核心轉儲後，請使用[dotnet 轉儲）](dotnet-dump.md)工具分析轉儲：

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

要`core_20190430_185145`分析的核心轉儲的名稱在哪裡。

> [!NOTE]
> 如果您發現一個錯誤，抱怨找不到*libdl.so，* 您可能需要安裝*libc6-dev*包。 如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](../linux-prerequisites.md)。

您將看到一個提示，您可以在其中輸入 SOS 命令。 通常，您要查看的第一件事是託管堆的總體狀態：

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

在這裡，您可以看到大多數物件是 或`String``Customer`物件。

可以將 該`dumpheap`命令與方法表 （MT） 再次使用，以獲取所有`String`實例的清單：

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

現在，可以使用`System.String`實例上`gcroot`的命令來查看物件如何以及為什麼紮根。 耐心等待，因為此命令需要幾分鐘時間使用 30 MB 堆：

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

您可以看到，`String`由`Customer`物件直接持有，並間接由`CustomerCache`物件持有。

您可以繼續轉儲物件，以查看大多數`String`物件遵循類似的模式。 此時，調查提供了足夠的資訊來識別代碼中的根本原因。

此常規過程允許您識別主要記憶體洩漏的來源。

## <a name="clean-up-resources"></a>清除資源

在本教程中，您啟動了一個示例 Web 服務器。 如["重新開機失敗的進程](#restart-the-failed-process)"部分所述，此伺服器應該已關閉。

您還可以刪除創建的轉儲檔。

## <a name="next-steps"></a>後續步驟

祝賀您完成本教程。

我們仍在發佈更多診斷教程。 您可以在[dotnet/診斷](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)存儲庫上讀取草稿版本。

本教程介紹了關鍵 .NET 診斷工具的基礎知識。 有關高級用法，請參閱以下參考文檔：

* [點網跟蹤](dotnet-trace.md)到清單進程。
* [點網計數器](dotnet-counters.md)，用於檢查託管記憶體使用方式。
* [點網轉儲](dotnet-dump.md)以收集和分析轉儲檔。
