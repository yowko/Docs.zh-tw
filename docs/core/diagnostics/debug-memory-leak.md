---
title: 調試記憶體流失教學課程
description: 瞭解如何在 .NET Core 中偵測記憶體流失。
author: sdmaclea
ms.author: stmaclea
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: def848b5fe6f08cf32067b833bbf6a97a56edda1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443509"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>教學課程：在 .NET Core 中偵測記憶體流失

**本文適用于：✓** .net CORE 3.0 SDK 和更新版本

本教學課程示範用來分析 .NET Core 記憶體流失的工具。

本教學課程使用範例應用程式，其設計目的是刻意流失記憶體。 範例是以練習的形式提供。 您也可以分析意外流失記憶體的應用程式。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
>
> - 使用[dotnet-計數器](dotnet-counters.md)檢查 managed 記憶體使用量。
> - 產生傾印檔案。
> - 使用傾印檔案來分析記憶體使用量。

## <a name="prerequisites"></a>必要條件：

教學課程會使用：

- [.Net Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core)或更新版本。
- [dotnet-](dotnet-trace.md)用來列出進程的追蹤。
- [dotnet-](dotnet-counters.md)用來檢查 managed 記憶體使用量的計數器。
- [dotnet-](dotnet-dump.md)傾印以收集和分析傾印檔案。
- 要診斷的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)應用程式。

本教學課程假設已安裝範例和工具，並可供使用。

## <a name="examine-managed-memory-usage"></a>檢查 managed 記憶體使用量

在您開始收集診斷資料以協助我們根本造成這種情況時，您必須確定您確實看到記憶體流失（記憶體成長）。 您可以使用[dotnet 計數器](dotnet-counters.md)工具來確認。

開啟主控台視窗，並流覽至您下載並解壓縮[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)的目錄。 執行目標：

```dotnetcli
dotnet run
```

從個別的主控台，使用[dotnet 追蹤](dotnet-trace.md)工具來尋找處理序識別碼：

```console
dotnet-trace ps
```

輸出應該會類似：

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

現在，使用[dotnet 計數器](dotnet-counters.md)工具來檢查 managed 記憶體使用量。 `--refresh-interval` 指定重新整理之間的秒數：

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

即時輸出應該類似：

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

重點放在這一行：

```console
    GC Heap Size (MB)                                  4
```

在啟動之後，您可以看到受控堆積記憶體是 4 MB。

現在，請按 `http://localhost:5000/api/diagscenario/memleak/20000`的 URL。

請注意，記憶體使用量已增加至 30 MB。

```console
    GC Heap Size (MB)                                 30
```

藉由監看記憶體使用量，您可以放心地指出記憶體正在增加或流失。 下一個步驟是收集正確的記憶體分析資料。

### <a name="generate-memory-dump"></a>產生記憶體傾印

分析可能的記憶體流失時，您需要存取應用程式的記憶體堆積。 然後您就可以分析記憶體內容。 查看物件之間的關聯性時，您會建立理論，說明為何無法釋放記憶體。 常見的診斷資料來源是 Windows 上的記憶體傾印或 Linux 上的對等核心傾印。 若要產生 .NET Core 應用程式的傾印，您可以使用[dotnet-dump）](dotnet-dump.md)工具。

使用先前啟動的[範例 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，執行下列命令以產生 Linux 核心傾印：

```dotnetcli
dotnet-dump collect -p 4807
```

結果是位於相同資料夾中的核心傾印。

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>重新開機失敗的進程

收集到傾印之後，您應該會有足夠的資訊來診斷失敗的進程。 如果失敗的進程是在實際執行伺服器上執行，現在是重新開機程式，這是短期補救的理想時機。

在本教學課程中，您現在已完成[範例的 debug 目標](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)，而且您可以將它關閉。 流覽至啟動伺服器的終端機，然後按 `Control-C`。

### <a name="analyze-the-core-dump"></a>分析核心傾印

現在您已產生核心傾印，請使用[dotnet-](dotnet-dump.md)傾印）工具來分析傾印：

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

其中 `core_20190430_185145` 是您想要分析的核心傾印名稱。

> [!NOTE]
> 如果您看到錯誤，指出找不到*libdl.so* ，您可能必須安裝*libc6 開發人員*套件。 如需詳細資訊，請參閱 [Linux 上 .NET Core 的必要條件](../linux-prerequisites.md)。

您會看到提示，您可以在其中輸入 SOS 命令。 通常，您想要查看的第一件事是受控堆積的整體狀態：

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

在這裡，您可以看到大部分的物件都是 `String` 或 `Customer` 物件。

您可以使用 [`dumpheap`] 命令，搭配方法表（MT）來取得所有 `String` 實例的清單：

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

您現在可以在 `System.String` 實例上使用 `gcroot` 命令，以查看物件的根目錄和原因。 請耐心等候，因為此命令需要幾分鐘的時間，其中包含 30 MB 的堆積：

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

您可以看到 `String` 直接由 `Customer` 物件持有，並由 `CustomerCache` 物件間接持有。

您可以繼續傾印物件，以查看大部分的 `String` 物件遵循類似的模式。 此時，調查已提供足夠的資訊來識別程式碼中的根本原因。

這個一般程式可讓您識別主要記憶體流失的來源。

## <a name="clean-up-resources"></a>清除資源

在本教學課程中，您已啟動範例 web 伺服器。 此伺服器應已關閉，如[重新開機失敗的進程](#restart-the-failed-process)一節中所述。

您也可以刪除已建立的傾印檔案。

## <a name="next-steps"></a>後續步驟

恭喜您完成本教學課程。

我們仍在發行更多診斷教學課程。 您可以閱讀[dotnet/診斷](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)存放庫中的草稿版本。

本教學課程涵蓋重要 .NET 診斷工具的基本概念。 如需先進的使用方式，請參閱下列參考檔：

* [dotnet-](dotnet-trace.md)用來列出進程的追蹤。
* [dotnet-](dotnet-counters.md)用來檢查 managed 記憶體使用量的計數器。
* [dotnet-](dotnet-dump.md)傾印以收集和分析傾印檔案。
