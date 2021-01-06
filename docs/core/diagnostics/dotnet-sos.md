---
title: dotnet-sos 診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet-sos CLI 工具來管理 SOS 偵錯工具擴充功能，此擴充功能可搭配 Windows 和 Linux 上的原生偵錯工具使用。
ms.date: 11/17/2020
ms.openlocfilehash: 09e8228c47bdc632bccf3c9ad2296d55fe420060
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765003"
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

## <a name="description"></a>描述

`dotnet-sos`全域工具會安裝[SOS 偵錯工具擴充](sos-debugging-extension.md)功能。 此延伸模組可讓您從 lldb 和 windbg 等原生偵錯工具檢查 managed .NET Core 狀態。

> [!NOTE]
> `dotnet-sos`只有 Linux 或 macOS 才需要透過工具安裝 SOS。  如果您使用的是較舊的調試工具，可能也需要在 Windows 上使用。 [Windows 偵錯工具](/windows-hardware/drivers/debugger/debugger-download-tools)的最新版本 ( # B0 = WinDbg 或 cdb 的版本 10.0.18317.1001) 從 Microsoft 擴充功能資源庫自動載入 SOS。  

## <a name="options"></a>選項

- **`--version`**

  顯示版本資訊。

- **`-h|--help`**

  顯示命令列說明。

## <a name="dotnet-sos-install"></a>dotnet-sos 安裝

在本機安裝 [SOS 擴充](sos-debugging-extension.md) 功能，以進行 .net Core 進程的偵錯工具。 在 macOS 和 Linux 上， *lldbinit* 檔案將會更新，讓擴充功能在 lldb 啟動時自動載入。 如果您要在具有舊版偵錯工具的 Windows 上安裝 SOS (在 10.0.18317.1001) 之前，您必須在偵錯工具中執行，以手動方式將擴充功能載入 WinDbg 或 cdb 中 `.load %USERPROFILE%\.dotnet\sos\sos.dll` 。

### <a name="synopsis"></a>概要

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a>選項

- **`--architecture <arch>`**

  指定要安裝之 SOS 二進位檔的處理器架構。 預設會 `dotnet-sos` 安裝主機電腦的架構。 當您想要為不同于 dotnet 主機架構的架構安裝 SOS 時，請使用此選項。 例如，如果您是從 Arm64 主機執行 Arm32 二進位檔，則必須使用安裝 SOS `dotnet-sos install --architecture Arm` 。

  以下是可用的架構：

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a>dotnet-sos 卸載

卸載 [SOS 擴充](sos-debugging-extension.md) 功能，然後在 Linux 和 macOS 上將它從 lldb 設定中移除。

### <a name="synopsis"></a>概要

```console
dotnet-sos uninstall
```
