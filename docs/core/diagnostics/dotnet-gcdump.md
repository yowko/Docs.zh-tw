---
title: dotnet-gcdump 診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-gcdump CLI 工具，以使用 .NET EventPipe 收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。
ms.date: 11/17/2020
ms.openlocfilehash: 59de1845ada9e5bdd0b24bf4312517283324ce94
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826036"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a>堆積分析工具 (dotnet-gcdump) 

本文 **適用于：** ✔️ .net CORE 3.1 SDK 和更新版本

## <a name="install"></a>安裝

有兩種方式可以下載和安裝 `dotnet-gcdump` ：

- **dotnet global tool：**

  若要安裝 `dotnet-gcdump` [NuGet 套件](https://www.nuget.org/packages/dotnet-gcdump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- **直接下載：**

  下載符合您平臺的工具可執行檔：

  | OS  | 平台 |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-gcdump/win-x86) \|[x64](https://aka.ms/dotnet-gcdump/win-x64) \|[arm](https://aka.ms/dotnet-gcdump/win-arm) \|[arm-x64](https://aka.ms/dotnet-gcdump/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-gcdump/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-gcdump/linux-x64) \|[arm](https://aka.ms/dotnet-gcdump/linux-arm) \|[arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64) |

## <a name="synopsis"></a>概要

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a>說明

`dotnet-gcdump`全域工具會使用[EventPipe](./eventpipe.md)收集即時 .NET 進程的 GC (垃圾收集行程) 傾印。 GC 傾印的建立方式，是在目標進程中觸發 GC、開啟特殊事件，以及從事件資料流程重新產生物件根目錄的圖形。 此程式可讓您在進程執行時收集 GC 傾印，並以最少量的額外負荷進行收集。 這些傾印適用于數種案例：

- 比較堆積上數個時間點的物件數目。
- 分析物件的根目錄 (回答問題，例如「仍有此類型的參考？」。) 。
- 收集堆積上物件計數的一般統計資料。

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a>查看從 dotnet 所捕獲的 GC 傾印-gcdump

在 Windows 上，您 `.gcdump` 可以在 [PerfView](https://github.com/microsoft/perfview) 中查看檔案以進行分析或 Visual Studio。 目前沒有任何方法可以 `.gcdump` 在非 Windows 平臺上開啟。

您可以收集多個 `.gcdump` ，並同時在 Visual Studio 中開啟，以取得比較體驗。

## <a name="options"></a>選項

- **`--version`**

  顯示公用程式的版本 `dotnet-gcdump` 。

- **`-h|--help`**

  顯示命令列說明。

## `dotnet-gcdump collect`

從目前正在執行的進程收集 GC 傾印。

### <a name="synopsis"></a>概要

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a>選項

- **`-h|--help`**

  顯示命令列說明。

- **`-p|--process-id <pid>`**

  從中收集 GC 傾印的處理序識別碼。

- **`-o|--output <gcdump-file-path>`**

  應寫入所收集 GC 傾印的路徑。 預設為 *。 \\YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*。

- **`-v|--verbose`**

  在收集 GC 傾印時輸出記錄。

- **`-t|--timeout <timeout>`**

  如果 GC 傾印花費的時間超過這段時間，請放棄收集。 預設值是 30。

- **`-n|--name <name>`**

  要從中收集 GC 傾印的進程名稱。

## `dotnet-gcdump ps`

列出可收集 GC 傾印的 dotnet 進程。

### <a name="synopsis"></a>概要

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

從先前產生的 GC 傾印或執行中的進程產生報表，然後寫入至 `stdout` 。

### <a name="synopsis"></a>概要

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a>選項

- **`-h|--help`**

  顯示命令列說明。

- **`-p|--process-id <pid>`**

  從中收集 GC 傾印的處理序識別碼。

- **`-t|--report-type <HeapStat>`**

  要產生的報表類型。 可用的選項： heapstat (預設) 。

## <a name="troubleshoot"></a>疑難排解

- Gcdump 中沒有類型資訊。

   在 .NET Core 3.1 之前，有一個問題，就是使用 EventPipe 叫用 gcdumps 時，不會清除類型快取。 這會導致判斷第二個和後續 gcdumps 的類型資訊未傳送所需的事件。 這已在 .NET Core 3.1-preview2 中修正。

- COM 和靜態類型不在 GC 傾印中。

   在 .NET Core 3.1-preview2 之前，有一個問題：當透過 EventPipe 叫用 GC 傾印時，不會傳送靜態和 COM 類型。 這已在 .NET Core 3.1-preview2 中修正。
