---
title: 對 Linux 傾印進行偵錯
description: 在本文中，您將瞭解如何收集和分析來自 Linux 環境的傾印。
ms.date: 08/27/2020
ms.openlocfilehash: 692d6228fae31de015412c23c4ec5317024faaab
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982258"
---
# <a name="debug-linux-dumps"></a>對 Linux 傾印進行偵錯

本文 **適用于：✔️** .net CORE 3.0 SDK 和更新版本

## <a name="collect-dumps-on-linux"></a>在 Linux 上收集傾印

在 Linux 上收集傾印的兩個建議方法是 [`dotnet-dump`](dotnet-dump.md) 或 [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) 工具。

### <a name="managed-dumps-with-dotnet-dump"></a>受控傾印 `dotnet-dump`

此 [`dotnet-dump`](dotnet-dump.md) 工具很容易使用，而且沒有任何原生偵錯工具的相依性。 `dotnet-dump` 適用于各種不同的 Linux 平臺 (例如 Alpine 或 ARM32/ARM64) 可能無法使用傳統的偵錯工具。 不過， `dotnet-dump` 只會取得受管理的狀態，使其無法用於偵測機器碼中的問題。 收集的傾印 `dotnet-dump` 會在具有建立傾印之相同作業系統和架構的環境中進行分析。 此 [`dotnet-gcdump`](dotnet-gcdump.md) 工具可用來做為替代方案，只會捕捉 GC 堆積資訊，但會產生可在 Windows 上分析的傾印。

### <a name="core-dumps-with-createdump"></a>核心傾印 `createdump`

建立僅限受控傾印的替代方案 `dotnet-dump` [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) 是在 Linux 上建立核心傾印的建議工具，其中包含原生和受管理的資訊。 其他工具（例如 gdb 或 gcore）也可以用來建立核心傾印，但可能會遺失 managed 偵錯工具所需的狀態，在分析期間導致「未知」類型或函式名稱。

這些 `createdump` 工具會與 .Net Core 執行時間一起安裝，並可在 libcoreclr.so 的旁邊找到， (通常位於 "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]" ) 。 此工具會採用處理序識別碼來收集傾印作為其主要引數，也可以使用選擇性參數來指定要收集的傾印類型 (使用堆積的小型傾印是預設) 。 這些選項包括：

- **`<input-filename>`**

  要轉換的輸入追蹤檔案。 預設值為 *nettrace*。

### <a name="options"></a>選項

- **`-f|--name <output-filename>`**

  要寫入傾印的檔案。 預設值為 '/tmp/coredump.%p '，其中% p 是目標進程的處理序識別碼。

- **`-n|--normal`**

  建立小型傾印。

- **`-h|--withheap`**

  使用堆積 (預設) 建立小型傾印。

- **`-t|--triage`**

  建立分級小型傾印。

- **`-u|--full`**

  建立完整的核心轉儲。

- **`-d|--diag`**

  啟用診斷訊息。

請注意，收集核心傾印需要 `SYS_PTRACE` 功能或 `createdump` 使用 sudo 或 su 來執行。

## <a name="analyze-dumps-on-linux"></a>分析 Linux 上的傾印

使用收集的管理傾印和收集的核心傾印，都 `dotnet-dump` `createdump` 可以 `dotnet-dump` 使用命令，利用工具進行分析 `dotnet-dump analyze` 。 需要分析傾印的 `dotnet dump` 環境與用來捕捉傾印的環境具有相同的作業系統和架構。

或者，您也可以使用 [LLDB](https://lldb.llvm.org/) 來分析 Linux 上的核心傾印，以允許分析 managed 和原生框架。 LLDB 使用 SOS 擴充功能來進行 managed 程式碼的偵錯工具。 您 [`dotnet-sos`](dotnet-sos.md) 可以使用 CLI 工具來安裝包含 [許多實用命令](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) 的 SOS，以進行 managed 程式碼的偵錯工具。 為了分析 .NET Core 傾印，LLDB 和 SOS 需要下列 .NET Core 二進位檔，其來自于建立傾印的環境：

1. libmscordaccore.so
2. libcoreclr.so
3. dotnet (用來啟動應用程式的主機) 

在大部分的情況下，可以使用工具來下載這些二進位檔 [`dotnet-symbol`](dotnet-symbol.md) 。 如果無法下載所需的二進位檔， `dotnet-symbol` (例如，如果從來源建立的 .Net Core 私用版本是使用中的) ，則可能需要從建立傾印的環境複製上方列出的檔案。 如果檔案不在傾印檔案的旁邊，您可以使用 LLDB/SOS 命令設定要 `setclrpath <path>` 從中載入的路徑，以及 `setsymbolserver -directory <path>` 設定要在符號檔中尋找的路徑。

一旦有必要的檔案可供使用，就可以藉由將 dotnet 主機指定為要進行偵錯工具的可執行檔，在 LLDB 中載入傾印：

```console
lldb --core <dump-file> <host-program>
```

在上述命令列中， `<dump-file>` 是要分析的傾印路徑，而 `<host-program>` 是啟動 .net Core 應用程式的原生程式。 `dotnet`除非應用程式是獨立的，否則這通常是二進位檔，在此情況下，它是沒有 dll 副檔名的應用程式名稱。

開始 LLDB 之後，您可能必須使用 `setsymbolserver` 命令來指向正確的符號位置， (`setsymbolserver -ms` 使用 Microsoft 的符號伺服器或 `setsymbolserver -directory <path>` 指定本機路徑) 。 您可以藉由執行來載入原生符號 `loadsymbols` 。 此時，可以使用 [SOS 命令](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) 來分析傾印。

## <a name="see-also"></a>另請參閱

- [dotnet-sos](dotnet-sos.md) ，以取得安裝 sos 擴充功能的詳細資料。
- [dotnet-符號](dotnet-symbol.md) ，以取得安裝和使用符號下載工具的詳細資料。
- [.Net Core 診斷](https://github.com/dotnet/diagnostics/blob/master/documentation/) 存放庫，以取得更多有關偵錯工具的詳細資料，包括有用的常見問題。
- [安裝 LLDB](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) 以取得在 Linux 或 Mac 上安裝 LLDB 的指示。
