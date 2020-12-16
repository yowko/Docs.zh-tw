---
title: 使用 PerfCollect 追蹤 .NET 應用程式。
description: 本教學課程會逐步引導您使用 .NET 中的 perfcollect 收集追蹤。
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 53e4584953d2af4e766daadfa757cca752ae7329
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593216"
---
# <a name="trace-net-applications-with-perfcollect"></a>使用 PerfCollect 追蹤 .NET 應用程式

本文 **適用于：✔️** .net CORE 2.1 SDK 和更新版本

當 Linux 上發生效能問題時，使用收集追蹤 `perfcollect` 可用來收集有關效能問題時電腦上發生之狀況的詳細資訊。

`perfcollect` 是一種 bash 腳本，它會利用 [Linux 追蹤 Tookit-Next 產生 (LTTng) ](https://lttng.org) 收集從執行時間或任何 [EventSource](xref:System.Diagnostics.Tracing.EventListener)撰寫的事件， [以及使用](https://perf.wiki.kernel.org/) 效能收集目標進程的 CPU 範例。

## <a name="prepare-your-machine"></a>準備您的電腦

遵循下列步驟來準備您的機器，以收集效能追蹤 `perfcollect` 。

> [!NOTE]
> 如果您是在容器環境中，您的容器必須有 `SYS_ADMIN` 功能。 如需使用 PerfCollect 在容器內追蹤應用程式的詳細資訊，請參閱 [在容器中收集診斷](./diagnostics-in-containers.md)。

1. 下載 `perfcollect` 。

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. 讓腳本成為可執行檔。

    > ```bash
    > chmod +x perfcollect
    > ```

3. 安裝追蹤必要條件-這些是實際的追蹤程式庫。

    > ```bash
    > sudo ./perfcollect install
    > ```

    這會在您的電腦上安裝下列必要條件：

    1. `perf`： Linux 效能事件子系統和隨附的使用者模式集合/檢視器應用程式。 `perf` 是 Linux 核心來源的一部分，但通常不會預設安裝。

    2. `LTTng`：用來捕捉 CoreCLR 在執行時間發出的事件資料。 這項資料接著會用來分析各種執行時間元件的行為，例如 GC、JIT 和執行緒集區。

最新版本的 .NET Core 和 Linux 效能工具支援自動解析架構程式碼的方法名稱。 如果您使用的是 .NET Core 3.1 版或更低版本，則需要額外的步驟。 請參閱 [解析架構符號](#resolve-framework-symbols) 以取得詳細資料。

若要解析原生執行時間 Dll 的方法名稱 (例如 libcoreclr.so) ， `perfcollect` 將會在轉換資料時解析它們的符號，但只有在這些二進位檔的符號存在時才會解析這些符號。 如需詳細資料，請參閱 [取得原生運行](#get-symbols-for-the-native-runtime) 時間的符號一節。

## <a name="collect-a-trace"></a>收集追蹤

1. 有兩個可用的 shell-一個用來控制追蹤，稱為 **[Trace]**，另一個用來執行應用程式，稱為 **[App]**。

2. **[追蹤]** 開始收集。

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    預期的輸出：

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. **[應用程式]** 使用下列環境變數來設定應用程式 shell-這會啟用 CoreCLR 的追蹤設定。

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. **[應用程式]** 執行應用程式-讓它在您需要的時間內執行，以便捕捉效能問題。 確切的長度可以是您所需的最短時間，只要它足以捕捉您要調查的效能問題發生的時間範圍。

    > ```bash
    > dotnet run
    > ```

5. **[追蹤]** 停止收集-按 CTRL + C。

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    壓縮的追蹤檔案現在會儲存在目前的工作目錄中。

## <a name="view-a-trace"></a>查看追蹤

有許多選項可供您用來查看已收集的追蹤。 追蹤最適合使用 Windows 上的 [PerfView](https://aka.ms/perfview) ，但可以直接在 Linux 上使用 `PerfCollect` 本身或來查看 `TraceCompass` 。

### <a name="use-perfcollect-to-view-the-trace-file"></a>使用 PerfCollect 來查看追蹤檔案

您可以使用 perfcollect 本身來查看您所收集的追蹤。 若要這樣做，請使用下列命令：

```bash
./perfcollect view sampleTrace.trace.zip
```

根據預設，這會使用來顯示應用程式的 CPU 追蹤 `perf` 。

若要查看透過所收集的事件 `LTTng` ，您可以傳入旗標 `-viewer lttng` 以查看個別事件：

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

這會使用 `babeltrace` 檢視器來列印事件承載：

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a>使用 PerfView 開啟追蹤檔案

若要查看 CPU 範例和事件的匯總視圖，您可以 `PerfView` 在 Windows 電腦上使用。

1. 將 trace.zip 檔案從 Linux 複製到 Windows 電腦。

2. 從下載 PerfView <https://aka.ms/perfview> 。

3. 執行 PerfView.exe

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

PerfView 會根據追蹤檔中包含的資料，顯示支援的視圖清單。

- 針對 CPU 調查，請選擇 [ **cpu 堆疊**]。

- 如需詳細的 GC 資訊，請選擇 [ **GCStats**]。

- 針對每個進程/模組/方法的 JIT 資訊，請選擇 [ **JITStats**]。

- 如果沒有您需要的資訊，您可以嘗試在「原始事件」視圖中尋找事件。  選擇 [ **事件**]。

如需有關如何在 PerfView 中解讀視圖的詳細資訊，請參閱 view 本身的說明連結，或從 PerfView 的主視窗中，選擇 [說明 **->使用者指南**]。

### <a name="use-tracecompass-to-open-the-trace-file"></a>使用 TraceCompass 開啟追蹤檔案

[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) 是另一個可供您用來查看追蹤的選項。 `TraceCompass` 也可在 Linux 機器上運作，因此您不需要將追蹤移至 Windows 電腦。 若要使用 `TraceCompass` 開啟您的追蹤檔案，您將需要解壓縮檔案。

```bash
unzip myTrace.trace.zip
```

`perfcollect` 會將收集到的 LTTng 追蹤儲存到中子目錄的 CTF 檔案格式 `lttngTrace` 。 具體來說，CTF 檔會位於看起來像這樣的目錄中 `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` 。

您可以 `TraceCompass` 選取並選取檔案，以開啟中的 CTF 追蹤檔案 `File -> Open Trace` `metadata` 。

如需詳細資訊，請參閱[ `TraceCompass` 檔](https://www.eclipse.org/tracecompass/)。

## <a name="resolve-framework-symbols"></a>解析架構符號

在收集追蹤時，需要手動產生 Framework 符號。 它們與應用層級符號不同，因為架構是預先編譯的，而應用程式程式碼則是在編譯時進行。 針對已先行編譯成機器碼的架構程式碼，您必須呼叫 `crossgen` ，知道如何從機器碼產生對應到方法的名稱。

`perfcollect` 可以為您處理大部分的詳細資料，但它必須可以 `crossgen` 使用。 依預設，它不會隨 .NET 發行版本一起安裝。 如果 `crossgen` 不存在， `perfcollect` 則會警告您，並參考這些指示。 若要修正此問題，您必須針對所使用的執行時間，提取正確的 crossgen 版本。 如果您將 crossgen 工具放在與 .NET 執行時間 Dll 相同的目錄中 (例如 libcoreclr.so) ，則 `perfcollect` 可以找到它，並為您將架構符號新增至追蹤檔案。

一般來說，當您建立 .NET 應用程式時，它只會為您撰寫的程式碼產生 DLL，並使用其餘的執行時間共用複本。   不過，您也可以產生所謂的「獨立」版本的應用程式，其中包含所有執行時間 Dll。 `crossgen` 是 NuGet 套件的一部分，用來建立獨立式應用程式，因此取得正確版本的其中一種方式 `crossgen` 就是建立應用程式的獨立套件。

例如：

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

這會建立新的 Hello World 應用程式，並將其建立為獨立應用程式。

作為建立獨立式應用程式的副作用，dotnet 工具會下載名為 linux-x64 的 NuGet 套件，並將它放在目錄 ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION 中，其中 VERSION 是 .NET Core 執行時間的版本號碼 (例如 2.1.0) 。 這是一個工具目錄，裡面有您需要的 crossgen 工具。 從 .NET Core 3.0 開始，套件位置是 ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION。

此 `crossgen` 工具必須放在應用程式實際使用的執行時間旁。 一般來說，您的應用程式會使用安裝在/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION 的 .NET Core 共用版本，其中版本是 .NET 執行時間的版本號碼。 這是共用的位置，因此您必須是超級使用者才能修改它。 如果版本是2.1.0，則要更新的命令將 `crossgen` 會是：

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

完成此步驟之後， `perfcollect` 將會使用 crossgen 來包含架構符號。 `perfcollect`用來發出問題的警告應該會消失。 在您更新執行時間) 之前，每一部電腦只能有一次 (。

### <a name="alternative-turn-off-use-of-precompiled-code"></a>替代方法：關閉先行編譯器代碼的使用

如果您無法更新 .NET 執行時間 (以新增 `crossgen`) ，或上述程式因某些原因而無法運作，則可以使用另一種方法來取得架構符號。 您可以告訴執行時間單純不使用先行編譯的架構程式碼。 這段程式碼將會及時編譯，而且 `crossgen` 不需要。

> [!NOTE]
> 選擇此方法可能會增加應用程式的啟動時間。

若要這樣做，您可以新增下列環境變數：

```bash
export COMPlus_ZapDisable=1
```

透過這種變更，您應該會取得所有 .NET 程式碼的符號。

## <a name="get-symbols-for-the-native-runtime"></a>取得原生執行時間的符號

大部分情況下，您對自己的程式碼有興趣， `perfcollect` 預設會解決此情況。 有時候，查看 .NET Dll 內的內容會很有用 (這是最後一節) 的部分，但有時在原生執行時間 dll 中的情況下， (通常會 libcoreclr.so) ，這是很有趣的事。  `perfcollect` 會在轉換其資料時解析這些符號，但只有在這些原生 Dll 的符號存在 (，而且位於) 的程式庫旁時，才會解析這些符號。

有一個稱為 dotnet 的全域命令，它會執行這 [項](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) 工作。 若要使用 dotnet-符號來取得原生執行時間符號：

1. 安裝 `dotnet-symbol`：

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. 下載符號。 如果您已安裝 .NET Core 執行時間的版本2.1.0，則執行此動作的命令為：

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. 將符號複製到正確的位置。

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    如果因為您沒有適當目錄的寫入權限而無法完成，您可以使用 `perf buildid-cache` 新增符號。

之後，當您執行時，應該會取得原生 dll 的符號名稱 `perfcollect` 。

## <a name="collect-in-a-docker-container"></a>在 Docker 容器中收集

如需有關如何 `perfcollect` 在容器環境中使用的詳細資訊，請參閱在 [容器中收集診斷](./diagnostics-in-containers.md)。

## <a name="learn-more-about-collection-options"></a>深入瞭解收集選項

您可以指定下列選擇性旗標， `perfcollect` 使其更符合您的診斷需求。

### <a name="collect-for-a-specific-duration"></a>針對特定持續時間進行收集

當您想要收集特定期間的追蹤時，您可以使用 `-collectsec` 選項，後面接著一個數位，以指定收集追蹤的總秒數。

### <a name="collect-threadtime-traces"></a>收集 threadtime 追蹤

指定 `-threadtime` with 可 `perfcollect` 讓您收集每個執行緒的 CPU 使用量資料。 這可讓您分析每個執行緒花費其 CPU 時間的位置。

### <a name="collect-traces-for-managed-memory-and-garbage-collector-performance"></a>收集 managed 記憶體和垃圾收集行程效能的追蹤

下列選項可讓您明確地從執行時間收集 GC 事件。

* `perfcollect collect -gccollectonly`

只收集一組基本的 GC 收集事件。 這是最不詳細的 GC 事件集合設定檔，對目標應用程式效能的影響最低。 此命令類似于 `PerfView.exe /GCCollectOnly collect` PerfView 中的命令。

* `perfcollect collect -gconly`

使用 JIT、載入器和例外狀況事件收集更詳細的 GC 收集事件。 這會要求更詳細的事件 (例如配置資訊和 GC 聯結資訊) ，而且對目標應用程式效能的影響會比選項更多 `-gccollectonly` 。 此命令類似于 `PerfView.exe /GCOnly collect` PerfView 中的命令。

* `perfcollect collect -gcwithheap`

收集最詳細的 GC 收集事件，這些事件也會追蹤堆積的存活和移動。 這可提供 GC 行為的深入分析，但會產生高效能的成本，因為每個 GC 可能需要兩倍以上的時間。 建議您瞭解在生產環境中進行追蹤時，使用此追蹤選項的效能含意。
