---
title: dotnet-sos-.NET Core
description: 瞭解如何安裝和使用 dotnet-sos 命令列工具。
ms.date: 08/26/2020
ms.openlocfilehash: ba83105718909038ca56129ed8a5063aeff12e89
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065080"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="a32ec-103">SOS 安裝程式 (dotnet-sos) </span><span class="sxs-lookup"><span data-stu-id="a32ec-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="a32ec-104">本文**適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a32ec-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-sos"></a><span data-ttu-id="a32ec-105">安裝 dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="a32ec-105">Install dotnet-sos</span></span>

<span data-ttu-id="a32ec-106">若要安裝 `dotnet-sos` [NuGet 套件](https://www.nuget.org/packages/dotnet-sos)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="a32ec-106">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a><span data-ttu-id="a32ec-107">概要</span><span class="sxs-lookup"><span data-stu-id="a32ec-107">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="a32ec-108">描述</span><span class="sxs-lookup"><span data-stu-id="a32ec-108">Description</span></span>

<span data-ttu-id="a32ec-109">`dotnet-sos`全域工具會安裝[SOS 偵錯工具擴充](../../framework/tools/sos-dll-sos-debugging-extension.md)功能，以允許從原生偵錯工具（例如 Windows 上的 WinDbg/cdb 和 Linux 和 macOS 上的 lldb）[檢查 managed .net Core 狀態](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="a32ec-109">The `dotnet-sos` global tool installs the [SOS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and macOS.</span></span> <span data-ttu-id="a32ec-110">Windows 偵錯工具的最新版本 ( # B0 = WinDbg 或 cdb 的版本 10.0.18317.1001) 會自動從 Microsoft 擴充功能庫載入 SOS，因此 `dotnet-sos` 只有在 Linux 和 macOS 上，或是在使用舊版偵錯工具時，才需要透過工具安裝 sos。</span><span class="sxs-lookup"><span data-stu-id="a32ec-110">Recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and macOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="a32ec-111">選項。</span><span class="sxs-lookup"><span data-stu-id="a32ec-111">Options</span></span>

- **`--version`**

  <span data-ttu-id="a32ec-112">顯示版本資訊。</span><span class="sxs-lookup"><span data-stu-id="a32ec-112">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a32ec-113">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="a32ec-113">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="a32ec-114">dotnet-sos 安裝</span><span class="sxs-lookup"><span data-stu-id="a32ec-114">dotnet-sos install</span></span>

<span data-ttu-id="a32ec-115">在本機安裝 [SOS 擴充](../../framework/tools/sos-dll-sos-debugging-extension.md) 功能，以進行 .net Core 進程的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a32ec-115">Installs the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="a32ec-116">在 macOS 和 Linux 上，lldbinit 檔案將會更新，讓擴充功能在 lldb 啟動時自動載入。</span><span class="sxs-lookup"><span data-stu-id="a32ec-116">On macOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="a32ec-117">如果使用舊版偵錯工具在 Windows 上安裝 SOS ( # A0 version 10.0.18317.1001) ，您必須在偵錯工具中執行，以手動方式將擴充功能載入 WinDbg 或 cdb 中 `.load %USERPROFILE%\.dotnet\sos\sos.dll` 。</span><span class="sxs-lookup"><span data-stu-id="a32ec-117">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a32ec-118">概要</span><span class="sxs-lookup"><span data-stu-id="a32ec-118">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="a32ec-119">dotnet-sos 卸載</span><span class="sxs-lookup"><span data-stu-id="a32ec-119">dotnet-sos uninstall</span></span>

<span data-ttu-id="a32ec-120">卸載 [SOS 擴充](../../framework/tools/sos-dll-sos-debugging-extension.md) 功能，如果是在 Linux 或 macOS 上，則會將它從 lldb 設定中移除。</span><span class="sxs-lookup"><span data-stu-id="a32ec-120">Uninstalls the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) and, if on Linux or macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a32ec-121">概要</span><span class="sxs-lookup"><span data-stu-id="a32ec-121">Synopsis</span></span>

```console
dotnet-sos uninstall
```
