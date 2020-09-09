---
title: dotnet-符號-.NET Core
description: 安裝和使用 dotnet 符號命令列工具。
ms.date: 08/26/2020
ms.openlocfilehash: feaa64ad756878f85b829ab0cecf6ea2736014ba
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598331"
---
# <a name="symbol-downloader-dotnet-symbol"></a>符號下載程式 (dotnet-符號) 

本文**適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

## <a name="install-dotnet-symbol"></a>安裝 dotnet-符號

若要安裝 `dotnet-symbol` [NuGet 套件](https://www.nuget.org/packages/dotnet-symbol)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

```dotnetcli
dotnet tool install -g dotnet-symbol
```

## <a name="synopsis"></a>概要

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a>描述

全域工具會將檔案 `dotnet-symbol` 下載 (符號、DAC、模組等，) 調試核心傾印和小型傾印所需的檔案。 當您在另一部電腦上捕獲到的傾印時，這會很有用。 `dotnet-symbol` 可以下載分析傾印所需的模組和符號。

## <a name="options"></a>選項。

- **`--microsoft-symbol-server`**

  將 ' http://msdl.microsoft.com/download/symbols ' 符號伺服器路徑 (預設) 。

- **`--server-path <symbol server path>`**

  將符號伺服器新增至伺服器路徑。

- **`authenticated-server-path <pat> <server path>`**

  使用個人存取權杖 (PAT) ，將已驗證的符號伺服器新增至伺服器路徑。

- **`--cache-directory <file cache directory>`**

  新增快取目錄。

- **`--recurse-subdirectories`**

  處理所有子目錄中的輸入檔。

- **`--host-only`**

  只下載主機程式 (例如，lldb 需要載入核心傾印的 dotnet) 。

- **`--symbols`**

  下載符號檔 ( .pdb、dbg、. 阻礙) 。

- **`--modules`**

  下載模組檔案 ( .dll、. dylib) 。

- **`--debugging`**

  下載 (DAC、DBI、SOS) 的特殊偵錯工具模組。

- **`--windows-pdbs`**

  當可移植的 Pdb 也可供使用時，強制下載 Windows Pdb。

- **`-o, --output <output directory>`**

  設定輸出目錄。 否則，請在輸入檔旁邊寫入 (預設) 。

- **`-d, --diagnostics`**

  啟用診斷輸出。

- **`-h|--help`**

  顯示命令列說明。

## <a name="download-symbols"></a>載入符號

`dotnet-symbol`根據預設，針對傾印檔案執行時，將會下載所有需要的模組、符號和 DAC/DBI 檔案，以偵測包含 managed 元件的傾印。 由於 SOS 現在可以視需要下載符號，因此大部分的 Linux 核心傾印都可以使用 lldb 來分析，而只有主機 (dotnet) 和偵錯工具模組。 若要取得使用 lldb run 診斷核心傾印所需的這些檔案：

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a>疑難排解

- 下載符號時，找不到404。

   只有透過官方通道取得的官方 .NET Core 執行階段版本才支援符號下載，例如 [官方網站](https://dotnet.microsoft.com/download/dotnet-core) 和 [dotnet 安裝腳本中的預設來源](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-scripts)。 下載偵錯工具檔時發生404錯誤，可能表示已從另一個來源以 .NET Core 執行時間建立傾印，例如在本機或針對特定的 Linux 發行版本，或從 archlinux 之類的社區網站建立的轉儲。 在這種情況下，必須從這些來源或從建立傾印檔案的環境複製 (dotnet、libcoreclr.so 和 libmscordaccore.so) 所需的檔案。
