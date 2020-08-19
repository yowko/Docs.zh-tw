---
title: dotnet-gcdump-.NET Core
description: 安裝和使用 dotnet-gcdump 命令列工具。
ms.date: 07/26/2020
ms.openlocfilehash: 10e4c7e9e3a1df5d0eb58e68d38c0af091aeedc1
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88575678"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a>堆積分析工具 (dotnet-gcdump) 

本文**適用于：** ✔️ .net CORE 3.1 SDK 和更新版本

## <a name="install-dotnet-gcdump"></a>安裝 dotnet-gcdump

若要安裝 `dotnet-gcdump` [NuGet 套件](https://www.nuget.org/packages/dotnet-gcdump)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a>概要

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-gcdump`全域工具是一種方式，可收集 GC (垃圾收集行程，) 即時 .net 進程的傾印。 它會使用 EventPipe 技術，這是 Windows 上的 ETW 的跨平臺替代方案。 GC 傾印的建立方式，是在目標進程中觸發 GC、開啟特殊事件，以及從事件資料流程重新產生物件根目錄的圖形。 這可讓您在進程執行時收集 GC 傾印，並提供最少量的額外負荷。 這些傾印適用于數種案例：

- 比較堆積上數個時間點的物件數目。
- 分析物件的根目錄 (回答問題，例如「仍有此類型的參考？」。) 。
- 收集堆積上物件計數的一般統計資料。

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a>查看從 dotnet 所捕獲的 GC 傾印-gcdump

在 Windows 上，您 `.gcdump` 可以在 [PerfView](https://github.com/microsoft/perfview) 中查看檔案以進行分析或 Visual Studio。 目前沒有任何方法可以 `.gcdump` 在非 Windows 平臺上開啟。

您可以收集多個 `.gcdump` ，並同時在 Visual Studio 中開啟，以取得比較體驗。

## <a name="options"></a>選項。

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

### <a name="options"></a>選項。

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

### <a name="options"></a>選項。

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
