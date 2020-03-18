---
title: 在 Windows、Linux 和 macOS 上安裝 .NET 核心 SDK - .NET 核心
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 瞭解開發 .NET Core 應用所需的依賴項。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399004"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="e70cb-104">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e70cb-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="e70cb-105">在本文中，您將學習如何安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="e70cb-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="e70cb-106">.NET 核心 SDK 用於創建 .NET 核心應用和庫。</span><span class="sxs-lookup"><span data-stu-id="e70cb-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="e70cb-107">.NET 核心運行時始終與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="e70cb-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="e70cb-108">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-108">Install with an installer</span></span>

<span data-ttu-id="e70cb-109">Windows 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="e70cb-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="e70cb-110">x64 （64 位） CPU</span><span class="sxs-lookup"><span data-stu-id="e70cb-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="e70cb-111">x86 （32 位） CPU</span><span class="sxs-lookup"><span data-stu-id="e70cb-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="e70cb-112">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-112">Install with an installer</span></span>

<span data-ttu-id="e70cb-113">macOS 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="e70cb-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="e70cb-114">x64 （64 位） CPU</span><span class="sxs-lookup"><span data-stu-id="e70cb-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="e70cb-115">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-115">Download and manually install</span></span>

<span data-ttu-id="e70cb-116">作為 .NET Core 的 macOS 安裝程式的替代方法，您可以下載並手動安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="e70cb-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="e70cb-117">要提取 SDK 並使 .NET 核心 CLI 命令在終端上可用，請先[下載](#all-net-core-downloads).NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="e70cb-118">然後，打開一個終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e70cb-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="e70cb-119">假定運行時將下載到`~/Downloads/dotnet-sdk.pkg`檔中。</span><span class="sxs-lookup"><span data-stu-id="e70cb-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="e70cb-120">使用包管理器安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-120">Install with a package manager</span></span>

<span data-ttu-id="e70cb-121">您可以使用許多常見的 Linux 套裝程式管理器安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="e70cb-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="e70cb-122">有關詳細資訊，請參閱[Linux 套裝軟體管理器 - 安裝 .NET 核心](linux-package-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="e70cb-123">僅支援使用包管理器進行安裝。</span><span class="sxs-lookup"><span data-stu-id="e70cb-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="e70cb-124">如果要安裝具有其他體系結構（如 ARM）的 .NET 核心 SDK，請按照下面的[下載並手動安裝](#download-and-manually-install)說明進行操作。</span><span class="sxs-lookup"><span data-stu-id="e70cb-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="e70cb-125">有關支援哪些體系結構的詳細資訊，請參閱[.NET Core 依賴項和要求](dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="e70cb-126">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-126">Download and manually install</span></span>

<span data-ttu-id="e70cb-127">要提取 SDK 並使 .NET 核心 CLI 命令在終端上可用，請先[下載](#all-net-core-downloads).NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="e70cb-128">然後，打開一個終端並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e70cb-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="e70cb-129">前面的`export`命令僅使 .NET Core CLI 命令可用於運行它的終端會話。</span><span class="sxs-lookup"><span data-stu-id="e70cb-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="e70cb-130">您可以編輯 shell 設定檔以永久添加命令。</span><span class="sxs-lookup"><span data-stu-id="e70cb-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="e70cb-131">Linux 有許多不同的外殼，每個外殼都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="e70cb-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="e70cb-132">例如：</span><span class="sxs-lookup"><span data-stu-id="e70cb-132">For example:</span></span>
>
> - <span data-ttu-id="e70cb-133">**巴什外殼**： **/.bash_profile* *，*/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="e70cb-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="e70cb-134">**科恩殼牌**： \**/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="e70cb-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="e70cb-135">**Z 外殼**： \**/.zshrc*或 *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="e70cb-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="e70cb-136">編輯 shell 的相應原始檔案，並`:$HOME/dotnet`添加到現有`PATH`語句的末尾。</span><span class="sxs-lookup"><span data-stu-id="e70cb-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="e70cb-137">如果未`PATH`包含語句，則使用`export PATH=$PATH:$HOME/dotnet`添加新行。</span><span class="sxs-lookup"><span data-stu-id="e70cb-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="e70cb-138">此外，添加到`export DOTNET_ROOT=$HOME/dotnet`檔的末尾。</span><span class="sxs-lookup"><span data-stu-id="e70cb-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="e70cb-139">使用視覺工作室安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-139">Install with Visual Studio</span></span>

<span data-ttu-id="e70cb-140">如果您使用 Visual Studio 開發 .NET Core 應用，下表將基於目標 .NET Core SDK 版本描述視覺化工作室的最低要求版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="e70cb-141">.NET 核心 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="e70cb-141">.NET Core SDK version</span></span> | <span data-ttu-id="e70cb-142">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="e70cb-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="e70cb-143">3.1</span><span class="sxs-lookup"><span data-stu-id="e70cb-143">3.1</span></span>                   | <span data-ttu-id="e70cb-144">Visual Studio 2019 版本 16.4 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="e70cb-145">3.0</span><span class="sxs-lookup"><span data-stu-id="e70cb-145">3.0</span></span>                   | <span data-ttu-id="e70cb-146">Visual Studio 2019 版本 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="e70cb-147">2.2</span><span class="sxs-lookup"><span data-stu-id="e70cb-147">2.2</span></span>                   | <span data-ttu-id="e70cb-148">Visual Studio 2017 版本 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="e70cb-149">2.1</span><span class="sxs-lookup"><span data-stu-id="e70cb-149">2.1</span></span>                   | <span data-ttu-id="e70cb-150">Visual Studio 2017 版本 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="e70cb-151">如果您已經安裝了 Visual Studio，您可以使用以下步驟檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="e70cb-152">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e70cb-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="e70cb-153">選擇**關於** > **微軟視覺工作室的説明**。</span><span class="sxs-lookup"><span data-stu-id="e70cb-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="e70cb-154">從 **"關於"** 對話方塊中讀取版本號。</span><span class="sxs-lookup"><span data-stu-id="e70cb-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="e70cb-155">Visual Studio 可以安裝最新的 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="e70cb-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="e70cb-156">[下載視覺工作室](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="e70cb-157">選擇工作負荷</span><span class="sxs-lookup"><span data-stu-id="e70cb-157">Select a workload</span></span>

<span data-ttu-id="e70cb-158">安裝或修改 Visual Studio 時，根據要構建的應用程式類型選擇以下一個或多個工作負載：</span><span class="sxs-lookup"><span data-stu-id="e70cb-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="e70cb-159">**"其他工具集**"部分中的 **.NET 核心跨平臺開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="e70cb-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="e70cb-160">**Web &雲**部分中的**ASP.NET和 Web 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="e70cb-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="e70cb-161">**Web &雲**部分中的**Azure 開發**工作負荷。</span><span class="sxs-lookup"><span data-stu-id="e70cb-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="e70cb-162">**桌面&移動**部分中的 **.NET 桌面開發**工作負荷。</span><span class="sxs-lookup"><span data-stu-id="e70cb-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="e70cb-163">[![Windows 視覺化工作室 2019 與 .NET 核心工作負載](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="e70cb-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="e70cb-164">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-164">Download and manually install</span></span>

<span data-ttu-id="e70cb-165">要提取運行時並使 .NET Core CLI 命令在終端上可用，請首先[下載](#all-net-core-downloads).NET Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="e70cb-166">然後，創建要安裝到的目錄，例如`%USERPROFILE%\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="e70cb-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="e70cb-167">最後，將下載的 ZIP 檔案提取到該目錄中。</span><span class="sxs-lookup"><span data-stu-id="e70cb-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="e70cb-168">預設情況下，.NET 核心 CLI 命令和應用不會以這種方式使用 .NET Core 安裝。</span><span class="sxs-lookup"><span data-stu-id="e70cb-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="e70cb-169">您必須明確選取使用它。</span><span class="sxs-lookup"><span data-stu-id="e70cb-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="e70cb-170">為此，請更改啟動應用程式的環境變數：</span><span class="sxs-lookup"><span data-stu-id="e70cb-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="e70cb-171">此方法允許您將多個版本安裝到單獨的位置，然後通過運行應用程式的環境變數指向該位置來明確選取應用程式應使用哪個安裝位置。</span><span class="sxs-lookup"><span data-stu-id="e70cb-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="e70cb-172">即使設置了這些環境變數，.NET Core 在選擇運行應用程式的最佳框架時仍會考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="e70cb-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="e70cb-173">預設值通常是`C:\Program Files\dotnet`安裝程式使用的 。</span><span class="sxs-lookup"><span data-stu-id="e70cb-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="e70cb-174">也可以通過設置此環境變數來指示運行時僅使用自訂安裝位置：</span><span class="sxs-lookup"><span data-stu-id="e70cb-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="e70cb-175">安裝與 Mac 視覺工作室</span><span class="sxs-lookup"><span data-stu-id="e70cb-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="e70cb-176">選擇 **.NET 核心**工作負載時，適用于 Mac 的視覺化工作室將安裝 .NET 核心 SDK。</span><span class="sxs-lookup"><span data-stu-id="e70cb-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="e70cb-177">要開始在 macOS 上使用 .NET 核心開發，請參閱[為 Mac 安裝視覺化工作室 2019](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="e70cb-178">對於最新版本 .NET Core 3.1，您必須使用 Visual Studio 進行 Mac 8.4 預覽。</span><span class="sxs-lookup"><span data-stu-id="e70cb-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="e70cb-179">[![macOS 視覺化工作室 2019 適用于具有 .NET 核心工作負載功能的 Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="e70cb-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="e70cb-180">與視覺工作室代碼一起安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="e70cb-181">Visual Studio Code 是一款功能強大且羽量級的原始程式碼編輯器，在桌面上運行。</span><span class="sxs-lookup"><span data-stu-id="e70cb-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="e70cb-182">視覺化工作室代碼可用於 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="e70cb-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="e70cb-183">雖然 Visual Studio 代碼沒有像 Visual Studio 那樣具有自動化的 .NET 核心安裝程式，但添加 .NET Core 支援非常簡單。</span><span class="sxs-lookup"><span data-stu-id="e70cb-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="e70cb-184">[下載並安裝視覺工作室代碼](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="e70cb-185">[下載並安裝 .NET 核心 SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="e70cb-186">[從視覺化工作室代碼市場安裝 C# 擴展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="e70cb-187">使用 PowerShell 自動化安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-187">Install with PowerShell automation</span></span>

<span data-ttu-id="e70cb-188">[點網安裝腳本](../tools/dotnet-install-script.md)用於 SDK 的自動化和非管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="e70cb-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="e70cb-189">可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="e70cb-190">該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="e70cb-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="e70cb-191">要安裝 .NET Core 的當前版本，請使用以下開關運行腳本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="e70cb-192">使用 bash 自動化安裝</span><span class="sxs-lookup"><span data-stu-id="e70cb-192">Install with bash automation</span></span>

<span data-ttu-id="e70cb-193">[點網安裝腳本](../tools/dotnet-install-script.md)用於 SDK 的自動化和非管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="e70cb-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="e70cb-194">可以從[dotnet 安裝腳本引用頁](../tools/dotnet-install-script.md)下載腳本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="e70cb-195">該腳本預設安裝最新的[長期支援 （LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="e70cb-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="e70cb-196">要安裝 .NET Core 的當前版本，請使用以下開關運行腳本。</span><span class="sxs-lookup"><span data-stu-id="e70cb-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="e70cb-197">所有 .NET 核心下載</span><span class="sxs-lookup"><span data-stu-id="e70cb-197">All .NET Core downloads</span></span>

<span data-ttu-id="e70cb-198">您可以使用以下連結之一直接下載和安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="e70cb-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="e70cb-199">.NET 核心 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="e70cb-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="e70cb-200">.NET 核心 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="e70cb-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="e70cb-201">.NET 核心 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="e70cb-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="e70cb-202">.NET 核心 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="e70cb-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="e70cb-203">Docker</span><span class="sxs-lookup"><span data-stu-id="e70cb-203">Docker</span></span>

<span data-ttu-id="e70cb-204">容器提供了將應用程式與主機系統的其餘部分隔離的羽量級方法。</span><span class="sxs-lookup"><span data-stu-id="e70cb-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="e70cb-205">同一台電腦上的容器僅共用內核並使用提供給應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="e70cb-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="e70cb-206">.NET Core 可以在 Docker 容器中運行。</span><span class="sxs-lookup"><span data-stu-id="e70cb-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="e70cb-207">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="e70cb-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="e70cb-208">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="e70cb-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="e70cb-209">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="e70cb-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="e70cb-210">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="e70cb-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="e70cb-211">有關在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.NET 和 Docker 和](../docker/introduction.md)[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)簡介。</span><span class="sxs-lookup"><span data-stu-id="e70cb-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e70cb-212">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e70cb-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="e70cb-213">[教程：你好世界教程](../tutorials/with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="e70cb-214">[教程：使用視覺化工作室代碼創建新應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="e70cb-215">[教程： 容器化 .NET 核心應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="e70cb-216">[與macOS卡塔琳娜公證](macos-notarization-issues.md)工作。</span><span class="sxs-lookup"><span data-stu-id="e70cb-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="e70cb-217">[教程： 開始在 macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e70cb-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="e70cb-218">[教程：使用視覺化工作室代碼創建新應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="e70cb-219">[教程： 容器化 .NET 核心應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="e70cb-220">[教程：使用視覺化工作室代碼創建新應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="e70cb-221">[教程： 容器化 .NET 核心應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="e70cb-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
