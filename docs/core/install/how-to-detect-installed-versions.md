---
title: 在 Windows、Linux 和 macOS 上檢查已安裝的 .NET 版本-.NET
description: 瞭解如何列出電腦上安裝的 .NET 版本。 這包括 .NET 執行時間和 SDK。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 39020a32cdea9b82dc9d30e62e663ebc4ee39ebb
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687438"
---
# <a name="how-to-check-that-net-is-already-installed"></a>如何檢查是否已安裝 .NET

本文會教您如何檢查電腦上已安裝的 .NET 執行時間和 SDK 版本。 如果您有整合式開發環境，例如 Visual Studio 或 Visual Studio for Mac，可能已經安裝 .NET。

安裝 SDK 會安裝對應的執行時間。

如果本文中有任何命令失敗，您就不會安裝執行時間或 SDK。 如需詳細資訊，請參閱 [Windows](windows.md)、 [macOS](macos.md)或 [Linux](linux.md)的安裝文章。

## <a name="check-sdk-versions"></a>檢查 SDK 版本

您可以查看目前與終端機一起安裝的 .NET SDK 版本。 開啟終端機並執行下列命令。

```dotnetcli
dotnet --list-sdks
```

您會取得如下所示的輸出。

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
5.0.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
5.0.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a>檢查執行階段版本

您可以使用下列命令來查看目前已安裝的 .NET 執行階段版本。

```dotnetcli
dotnet --list-runtimes
```

您會取得如下所示的輸出。

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a>檢查安裝資料夾

您可以安裝 .NET，但無法將其新增至 `PATH` 您的作業系統或使用者設定檔的變數。 執行上述各節的命令可能無法運作。 或者，您可以檢查 .NET 安裝資料夾是否存在。

當您從安裝程式或腳本安裝 .NET 時，它會安裝到標準資料夾中。 您用來安裝 .NET 的安裝程式或腳本大部分的時候，都能讓您選擇安裝到不同的資料夾。 如果您選擇安裝到不同的資料夾，請調整資料夾路徑的開頭。

::: zone pivot="os-windows"

- **dotnet 可執行檔**\
_C： \\ program files \\ dotnet \\dotnet.exe_

- **.NET SDK**\
_C： \\ program files \\ dotnet \\ sdk \\ {version}\\_

- **.NET 執行時間**\
_C： \\ program files \\ dotnet \\ shared \\ {runtime-type} \\ {version}\\_

::: zone-end

::: zone pivot="os-linux"

- **dotnet 可執行檔**\
_/home/user/share/dotnet/dotnet_

- **.NET SDK**\
_/home/user/share/dotnet/sdk/{version}/_

- **.NET 執行時間**\
_/home/user/share/dotnet/shared/{runtime-type}/{version}/_

::: zone-end

::: zone pivot="os-macos"

- **dotnet 可執行檔**\
_/usr/local/share/dotnet/dotnet_

- **.NET SDK**\
_/usr/local/share/dotnet/sdk/{version}/_

- **.NET 執行時間**\
_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_

::: zone-end

## <a name="more-information"></a>詳細資訊

您可以使用命令來查看 SDK 版本和執行階段版本 `dotnet --info` 。 您也會取得其他環境相關資訊，例如作業系統版本和執行時間識別碼 (RID) 。

## <a name="next-steps"></a>後續步驟

- [安裝適用于 Windows 的 .Net 執行時間和 SDK](windows.md)。
- [安裝適用于 macOS 的 .Net 執行時間和 SDK](macos.md)。
- [安裝 .Net 執行時間和適用于 Linux 的 SDK](linux.md)。
