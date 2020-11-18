---
title: dotnet-sos 診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-sos CLI 工具來管理 SOS 偵錯工具擴充功能，此擴充功能可搭配 Windows 和 Linux 上的原生偵錯工具使用。
ms.date: 11/17/2020
ms.openlocfilehash: 59512c42a778f68bb3cd092dc854dcc727fd2881
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825438"
---
# <a name="sos-installer-dotnet-sos"></a>SOS 安裝程式 (dotnet-sos) 

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="install"></a>安裝

有兩種方式可以下載和安裝 `dotnet-sos` ：

- **dotnet global tool：**

  若要安裝 `dotnet-sos` [NuGet 套件](https://www.nuget.org/packages/dotnet-sos)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- **直接下載：**

  下載符合您平臺的工具可執行檔：

  | OS  | 平台 |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-sos/win-x86) \|[x64](https://aka.ms/dotnet-sos/win-x64) \|[arm](https://aka.ms/dotnet-sos/win-arm) \|[arm-x64](https://aka.ms/dotnet-sos/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-sos/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-sos/linux-x64) \|[arm](https://aka.ms/dotnet-sos/linux-arm) \|[arm64](https://aka.ms/dotnet-sos/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64) |

## <a name="synopsis"></a>概要

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a>說明

`dotnet-sos`全域工具會安裝[SOS 偵錯工具擴充](../../framework/tools/sos-dll-sos-debugging-extension.md)功能，以允許從原生偵錯工具（例如 Windows 上的 WinDbg/cdb 和 Linux 和 macOS 上的 lldb）[檢查 managed .net Core 狀態](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md)。 Windows 偵錯工具的最新版本 ( # B0 = WinDbg 或 cdb 的版本 10.0.18317.1001) 會自動從 Microsoft 擴充功能庫載入 SOS，因此 `dotnet-sos` 只有在 Linux 和 macOS 上，或是在使用舊版偵錯工具時，才需要透過工具安裝 sos。

## <a name="options"></a>選項

- **`--version`**

  顯示版本資訊。

- **`-h|--help`**

  顯示命令列說明。

## <a name="dotnet-sos-install"></a>dotnet-sos 安裝

在本機安裝 [SOS 擴充](../../framework/tools/sos-dll-sos-debugging-extension.md) 功能，以進行 .net Core 進程的偵錯工具。 在 macOS 和 Linux 上，lldbinit 檔案將會更新，讓擴充功能在 lldb 啟動時自動載入。 如果使用舊版偵錯工具在 Windows 上安裝 SOS ( # A0 version 10.0.18317.1001) ，您必須在偵錯工具中執行，以手動方式將擴充功能載入 WinDbg 或 cdb 中 `.load %USERPROFILE%\.dotnet\sos\sos.dll` 。

### <a name="synopsis"></a>概要

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a>dotnet-sos 卸載

卸載 [SOS 擴充](../../framework/tools/sos-dll-sos-debugging-extension.md) 功能，如果是在 Linux 或 macOS 上，則會將它從 lldb 設定中移除。

### <a name="synopsis"></a>概要

```console
dotnet-sos uninstall
```
