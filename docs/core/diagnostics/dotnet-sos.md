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
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="b2cfc-103">SOS 安裝程式 (dotnet-sos) </span><span class="sxs-lookup"><span data-stu-id="b2cfc-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="b2cfc-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="b2cfc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="b2cfc-105">安裝</span><span class="sxs-lookup"><span data-stu-id="b2cfc-105">Install</span></span>

<span data-ttu-id="b2cfc-106">有兩種方式可以下載和安裝 `dotnet-sos` ：</span><span class="sxs-lookup"><span data-stu-id="b2cfc-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="b2cfc-107">**dotnet global tool：**</span><span class="sxs-lookup"><span data-stu-id="b2cfc-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="b2cfc-108">若要安裝 `dotnet-sos` [NuGet 套件](https://www.nuget.org/packages/dotnet-sos)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="b2cfc-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="b2cfc-109">**直接下載：**</span><span class="sxs-lookup"><span data-stu-id="b2cfc-109">**Direct download:**</span></span>

  <span data-ttu-id="b2cfc-110">下載符合您平臺的工具可執行檔：</span><span class="sxs-lookup"><span data-stu-id="b2cfc-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="b2cfc-111">OS</span><span class="sxs-lookup"><span data-stu-id="b2cfc-111">OS</span></span>  | <span data-ttu-id="b2cfc-112">平台</span><span class="sxs-lookup"><span data-stu-id="b2cfc-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="b2cfc-113">Windows</span><span class="sxs-lookup"><span data-stu-id="b2cfc-113">Windows</span></span> | <span data-ttu-id="b2cfc-114">[x86](https://aka.ms/dotnet-sos/win-x86) \|[x64](https://aka.ms/dotnet-sos/win-x64) \|[arm](https://aka.ms/dotnet-sos/win-arm) \|[arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="b2cfc-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="b2cfc-115">macOS</span><span class="sxs-lookup"><span data-stu-id="b2cfc-115">macOS</span></span>   | [<span data-ttu-id="b2cfc-116">x64</span><span class="sxs-lookup"><span data-stu-id="b2cfc-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="b2cfc-117">Linux</span><span class="sxs-lookup"><span data-stu-id="b2cfc-117">Linux</span></span>   | <span data-ttu-id="b2cfc-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \|[arm](https://aka.ms/dotnet-sos/linux-arm) \|[arm64](https://aka.ms/dotnet-sos/linux-arm64) \|[musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \|[musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="b2cfc-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="b2cfc-119">概要</span><span class="sxs-lookup"><span data-stu-id="b2cfc-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="b2cfc-120">描述</span><span class="sxs-lookup"><span data-stu-id="b2cfc-120">Description</span></span>

<span data-ttu-id="b2cfc-121">`dotnet-sos`全域工具會安裝[SOS 偵錯工具擴充](sos-debugging-extension.md)功能。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-121">The `dotnet-sos` global tool installs the [SOS debugger extension](sos-debugging-extension.md).</span></span> <span data-ttu-id="b2cfc-122">此延伸模組可讓您從 lldb 和 windbg 等原生偵錯工具檢查 managed .NET Core 狀態。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-122">This extension lets you inspect managed .NET Core state from native debuggers like lldb and windbg.</span></span>

> [!NOTE]
> <span data-ttu-id="b2cfc-123">`dotnet-sos`只有 Linux 或 macOS 才需要透過工具安裝 SOS。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-123">Installing SOS via the `dotnet-sos` tool is only needed on Linux or macOS.</span></span>  <span data-ttu-id="b2cfc-124">如果您使用的是較舊的調試工具，可能也需要在 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-124">It may also be needed on Windows if you're using older debugging tools.</span></span> <span data-ttu-id="b2cfc-125">[Windows 偵錯工具](/windows-hardware/drivers/debugger/debugger-download-tools)的最新版本 ( # B0 = WinDbg 或 cdb 的版本 10.0.18317.1001) 從 Microsoft 擴充功能資源庫自動載入 SOS。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-125">Recent versions of the [Windows Debugger](/windows-hardware/drivers/debugger/debugger-download-tools) (>= version 10.0.18317.1001 of WinDbg or cdb) load SOS automatically from the Microsoft extension gallery.</span></span>  

## <a name="options"></a><span data-ttu-id="b2cfc-126">選項</span><span class="sxs-lookup"><span data-stu-id="b2cfc-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="b2cfc-127">顯示版本資訊。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-127">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b2cfc-128">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-128">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="b2cfc-129">dotnet-sos 安裝</span><span class="sxs-lookup"><span data-stu-id="b2cfc-129">dotnet-sos install</span></span>

<span data-ttu-id="b2cfc-130">在本機安裝 [SOS 擴充](sos-debugging-extension.md) 功能，以進行 .net Core 進程的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-130">Installs the [SOS extension](sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="b2cfc-131">在 macOS 和 Linux 上， *lldbinit* 檔案將會更新，讓擴充功能在 lldb 啟動時自動載入。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-131">On macOS and Linux, the *.lldbinit* file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="b2cfc-132">如果您要在具有舊版偵錯工具的 Windows 上安裝 SOS (在 10.0.18317.1001) 之前，您必須在偵錯工具中執行，以手動方式將擴充功能載入 WinDbg 或 cdb 中 `.load %USERPROFILE%\.dotnet\sos\sos.dll` 。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-132">If you're installing SOS on Windows with older debugging tools (prior to version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b2cfc-133">概要</span><span class="sxs-lookup"><span data-stu-id="b2cfc-133">Synopsis</span></span>

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a><span data-ttu-id="b2cfc-134">選項</span><span class="sxs-lookup"><span data-stu-id="b2cfc-134">Options</span></span>

- **`--architecture <arch>`**

  <span data-ttu-id="b2cfc-135">指定要安裝之 SOS 二進位檔的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-135">Specifies the processor architecture of the SOS binaries to install.</span></span> <span data-ttu-id="b2cfc-136">預設會 `dotnet-sos` 安裝主機電腦的架構。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-136">By default, `dotnet-sos` installs the architecture of the host machine.</span></span> <span data-ttu-id="b2cfc-137">當您想要為不同于 dotnet 主機架構的架構安裝 SOS 時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-137">Use this option when you want to install SOS for an architecture that's different from the dotnet host architecture.</span></span> <span data-ttu-id="b2cfc-138">例如，如果您是從 Arm64 主機執行 Arm32 二進位檔，則必須使用安裝 SOS `dotnet-sos install --architecture Arm` 。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-138">For example, if you're running Arm32 binaries from an Arm64 host, you will need to install SOS with `dotnet-sos install --architecture Arm`.</span></span>

  <span data-ttu-id="b2cfc-139">以下是可用的架構：</span><span class="sxs-lookup"><span data-stu-id="b2cfc-139">The following architectures are available:</span></span>

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="b2cfc-140">dotnet-sos 卸載</span><span class="sxs-lookup"><span data-stu-id="b2cfc-140">dotnet-sos uninstall</span></span>

<span data-ttu-id="b2cfc-141">卸載 [SOS 擴充](sos-debugging-extension.md) 功能，然後在 Linux 和 macOS 上將它從 lldb 設定中移除。</span><span class="sxs-lookup"><span data-stu-id="b2cfc-141">Uninstalls the [SOS extension](sos-debugging-extension.md) and, on Linux and macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b2cfc-142">概要</span><span class="sxs-lookup"><span data-stu-id="b2cfc-142">Synopsis</span></span>

```console
dotnet-sos uninstall
```
