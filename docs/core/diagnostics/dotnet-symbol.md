---
title: dotnet-符號診斷工具-.NET CLI
description: 瞭解如何安裝和使用 dotnet 符號 CLI 工具，以下載 .NET 傾印和小型傾印的偵錯工具所需的檔案。
ms.date: 11/17/2020
ms.openlocfilehash: 69c05544e886d9d41113c8a2383f760b85d01124
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764990"
---
# <a name="symbol-downloader-dotnet-symbol"></a><span data-ttu-id="892c5-103">符號下載程式 (dotnet-符號) </span><span class="sxs-lookup"><span data-stu-id="892c5-103">Symbol downloader (dotnet-symbol)</span></span>

<span data-ttu-id="892c5-104">本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="892c5-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="892c5-105">安裝</span><span class="sxs-lookup"><span data-stu-id="892c5-105">Install</span></span>

<span data-ttu-id="892c5-106">若要安裝 `dotnet-symbol` [NuGet 套件](https://www.nuget.org/packages/dotnet-symbol)的最新版本，請使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="892c5-106">To install the latest release version of the `dotnet-symbol` [NuGet package](https://www.nuget.org/packages/dotnet-symbol), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-symbol
```

## <a name="synopsis"></a><span data-ttu-id="892c5-107">概要</span><span class="sxs-lookup"><span data-stu-id="892c5-107">Synopsis</span></span>

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a><span data-ttu-id="892c5-108">描述</span><span class="sxs-lookup"><span data-stu-id="892c5-108">Description</span></span>

<span data-ttu-id="892c5-109">全域工具會將檔案 `dotnet-symbol` 下載 (符號、DAC、模組等，) 調試核心傾印和小型傾印所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="892c5-109">The `dotnet-symbol` global tool downloads files (symbols, DAC, modules, etc.) needed for debugging core dumps and minidumps.</span></span> <span data-ttu-id="892c5-110">當您在另一部電腦上捕獲到的傾印時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="892c5-110">This can be useful when debugging dumps captured on another machine.</span></span> <span data-ttu-id="892c5-111">`dotnet-symbol` 可以下載分析傾印所需的模組和符號。</span><span class="sxs-lookup"><span data-stu-id="892c5-111">`dotnet-symbol` can download modules and symbols needed to analyze the dump.</span></span>

## <a name="options"></a><span data-ttu-id="892c5-112">選項</span><span class="sxs-lookup"><span data-stu-id="892c5-112">Options</span></span>

- **`--microsoft-symbol-server`**

  <span data-ttu-id="892c5-113">將 ' http://msdl.microsoft.com/download/symbols ' 符號伺服器路徑 (預設) 。</span><span class="sxs-lookup"><span data-stu-id="892c5-113">Add 'http://msdl.microsoft.com/download/symbols' symbol server path (default).</span></span>

- **`--server-path <symbol server path>`**

  <span data-ttu-id="892c5-114">將符號伺服器新增至伺服器路徑。</span><span class="sxs-lookup"><span data-stu-id="892c5-114">Add a symbol server to the server path.</span></span>

- **`authenticated-server-path <pat> <server path>`**

  <span data-ttu-id="892c5-115">使用個人存取權杖 (PAT) ，將已驗證的符號伺服器新增至伺服器路徑。</span><span class="sxs-lookup"><span data-stu-id="892c5-115">Add an authenticated symbol server to the server path using a personal access token (PAT).</span></span>

- **`--cache-directory <file cache directory>`**

  <span data-ttu-id="892c5-116">新增快取目錄。</span><span class="sxs-lookup"><span data-stu-id="892c5-116">Adds a cache directory.</span></span>

- **`--recurse-subdirectories`**

  <span data-ttu-id="892c5-117">處理所有子目錄中的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="892c5-117">Process input files in all subdirectories.</span></span>

- **`--host-only`**

  <span data-ttu-id="892c5-118">只下載主機程式 (也就是 lldb 載入核心傾印所需的 dotnet) 。</span><span class="sxs-lookup"><span data-stu-id="892c5-118">Download only the host program (that is, dotnet) that lldb needs for loading core dumps.</span></span>

- **`--symbols`**

  <span data-ttu-id="892c5-119">下載符號檔 ( .pdb、dbg、. 阻礙) 。</span><span class="sxs-lookup"><span data-stu-id="892c5-119">Download symbol files (.pdb, .dbg, .dwarf).</span></span>

- **`--modules`**

  <span data-ttu-id="892c5-120">下載模組檔案 ( .dll、. dylib) 。</span><span class="sxs-lookup"><span data-stu-id="892c5-120">Download the module files (.dll, .so, .dylib).</span></span>

- **`--debugging`**

  <span data-ttu-id="892c5-121">下載 (DAC、DBI、SOS) 的特殊偵錯工具模組。</span><span class="sxs-lookup"><span data-stu-id="892c5-121">Download the special debugging modules (DAC, DBI, SOS).</span></span>

- **`--windows-pdbs`**

  <span data-ttu-id="892c5-122">當可移植的 Pdb 也可供使用時，強制下載 Windows Pdb。</span><span class="sxs-lookup"><span data-stu-id="892c5-122">Force the downloading of the Windows PDBs when Portable PDBs are also available.</span></span>

- **`-o, --output <output directory>`**

  <span data-ttu-id="892c5-123">設定輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="892c5-123">Set the output directory.</span></span> <span data-ttu-id="892c5-124">否則，請在輸入檔旁邊寫入 (預設) 。</span><span class="sxs-lookup"><span data-stu-id="892c5-124">Otherwise, write next to the input file (default).</span></span>

- **`-d, --diagnostics`**

  <span data-ttu-id="892c5-125">啟用診斷輸出。</span><span class="sxs-lookup"><span data-stu-id="892c5-125">Enable diagnostic output.</span></span>

- **`-h|--help`**

  <span data-ttu-id="892c5-126">顯示命令列說明。</span><span class="sxs-lookup"><span data-stu-id="892c5-126">Shows command-line help.</span></span>

## <a name="download-symbols"></a><span data-ttu-id="892c5-127">載入符號</span><span class="sxs-lookup"><span data-stu-id="892c5-127">Download symbols</span></span>

<span data-ttu-id="892c5-128">`dotnet-symbol`根據預設，針對傾印檔案執行時，將會下載所有需要的模組、符號和 DAC/DBI 檔案，以偵測包含 managed 元件的傾印。</span><span class="sxs-lookup"><span data-stu-id="892c5-128">Running `dotnet-symbol` against a dump file will, by default, download all the modules, symbols, and DAC/DBI files needed to debug the dump including the managed assemblies.</span></span> <span data-ttu-id="892c5-129">由於 SOS 現在可以視需要下載符號，因此大部分的 Linux 核心傾印都可以使用 lldb 來分析，而只有主機 (dotnet) 和偵錯工具模組。</span><span class="sxs-lookup"><span data-stu-id="892c5-129">Because SOS can now download symbols when needed, most Linux core dumps can be analyzed using lldb with only the host (dotnet) and debugging modules.</span></span> <span data-ttu-id="892c5-130">若要取得使用 lldb run 診斷核心傾印所需的這些檔案：</span><span class="sxs-lookup"><span data-stu-id="892c5-130">To get these files necessary for diagnosing a core dump with lldb run:</span></span>

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a><span data-ttu-id="892c5-131">疑難排解</span><span class="sxs-lookup"><span data-stu-id="892c5-131">Troubleshoot</span></span>

- <span data-ttu-id="892c5-132">下載符號時，找不到404。</span><span class="sxs-lookup"><span data-stu-id="892c5-132">404 Not Found while downloading symbols.</span></span>

   <span data-ttu-id="892c5-133">只有透過官方通道取得的官方 .NET Core 執行階段版本才支援符號下載，例如 [官方網站](https://dotnet.microsoft.com/download/dotnet-core) 和 [dotnet 安裝腳本中的預設來源](../tools/dotnet-install-script.md)。</span><span class="sxs-lookup"><span data-stu-id="892c5-133">Symbol download is only supported for official .NET Core runtime versions acquired through official channels such as [the official web site](https://dotnet.microsoft.com/download/dotnet-core) and the [default sources in the dotnet installation scripts](../tools/dotnet-install-script.md).</span></span> <span data-ttu-id="892c5-134">下載偵錯工具檔時發生404錯誤，可能表示已從另一個來源以 .NET Core 執行時間建立傾印，例如在本機或針對特定的 Linux 發行版本，或從 archlinux 之類的社區網站建立的轉儲。</span><span class="sxs-lookup"><span data-stu-id="892c5-134">A 404 error while downloading debugging files may indicate that the dump was created with a .NET Core runtime from another source, such as one built from source locally or for a particular Linux distro, or from community sites like archlinux.</span></span> <span data-ttu-id="892c5-135">在這種情況下，必須從這些來源或從建立傾印檔案的環境複製 (dotnet、libcoreclr.so 和 libmscordaccore.so) 所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="892c5-135">In such cases, file necessary for debugging (dotnet, libcoreclr.so, and libmscordaccore.so) should be copied from those sources or from the environment the dump file was created in.</span></span>

## <a name="see-also"></a><span data-ttu-id="892c5-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="892c5-136">See also</span></span>

* [<span data-ttu-id="892c5-137">使用符號進行調試</span><span class="sxs-lookup"><span data-stu-id="892c5-137">Debugging with symbols</span></span>](/windows/win32/dxtecharts/debugging-with-symbols)
* [<span data-ttu-id="892c5-138">便攜 Pdb</span><span class="sxs-lookup"><span data-stu-id="892c5-138">Portable PDBs</span></span>](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md)
