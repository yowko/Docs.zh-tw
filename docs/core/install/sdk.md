---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core SDK-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索開發 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 0aa323533dd9136372c2bbc330c9c3056fdf428c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157567"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="7128a-104">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="7128a-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="7128a-105">在本文中，您將瞭解如何安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7128a-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="7128a-106">.NET Core SDK 可用來建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="7128a-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="7128a-107">.NET Core 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="7128a-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="7128a-108">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-108">Install with an installer</span></span>

<span data-ttu-id="7128a-109">Windows 有獨立的安裝程式，可用於安裝 .NET Core 3.1 SDK：</span><span class="sxs-lookup"><span data-stu-id="7128a-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="7128a-110">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="7128a-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="7128a-111">x86 （32位） Cpu</span><span class="sxs-lookup"><span data-stu-id="7128a-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="7128a-112">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-112">Install with an installer</span></span>

<span data-ttu-id="7128a-113">macOS 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="7128a-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="7128a-114">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="7128a-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="7128a-115">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-115">Download and manually install</span></span>

<span data-ttu-id="7128a-116">除了適用于 .NET Core 的 macOS 安裝程式之外，您還可以下載並手動安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="7128a-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="7128a-117">若要解壓縮 SDK，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="7128a-118">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="7128a-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="7128a-119">假設執行時間已下載至 `~/Downloads/dotnet-sdk.pkg` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7128a-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="7128a-120">使用套件管理員進行安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-120">Install with a package manager</span></span>

<span data-ttu-id="7128a-121">您可以使用許多常見的 Linux 套件管理員來安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7128a-121">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="7128a-122">如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-122">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="7128a-123">只有在 x64 架構上才支援使用套件管理員進行安裝。</span><span class="sxs-lookup"><span data-stu-id="7128a-123">Installing with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="7128a-124">如果您要使用不同的架構（例如 ARM）安裝 .NET Core SDK，請遵循下列[下載並手動安裝](#download-and-manually-install)指示。</span><span class="sxs-lookup"><span data-stu-id="7128a-124">If you're installing the .NET Core SDK with a different architecture, such as ARM, follow the [Download and manually install](#download-and-manually-install) instructions below.</span></span> <span data-ttu-id="7128a-125">如需有關支援哪些架構的詳細資訊，請參閱[.Net Core 相依性和需求](dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-125">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="7128a-126">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-126">Download and manually install</span></span>

<span data-ttu-id="7128a-127">若要解壓縮 SDK，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-127">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="7128a-128">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="7128a-128">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="7128a-129">上述 `export` 命令只會將 .NET Core CLI 命令提供給執行它的終端機會話。</span><span class="sxs-lookup"><span data-stu-id="7128a-129">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="7128a-130">您可以編輯您的 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="7128a-130">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="7128a-131">有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="7128a-131">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="7128a-132">例如：</span><span class="sxs-lookup"><span data-stu-id="7128a-132">For example:</span></span>
>
> - <span data-ttu-id="7128a-133">**Bash Shell**： *~/. bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="7128a-133">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="7128a-134">**Korn Shell**： *~/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="7128a-134">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="7128a-135">**Z Shell**： *~/.zshrc*或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="7128a-135">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="7128a-136">為您的 shell 編輯適當的原始程式檔，並將 `:$HOME/dotnet` 新增至現有 `PATH` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="7128a-136">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="7128a-137">如果未包含任何 `PATH` 語句，請加入具有 `export PATH=$PATH:$HOME/dotnet`的新行。</span><span class="sxs-lookup"><span data-stu-id="7128a-137">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="7128a-138">此外，將 `export DOTNET_ROOT=$HOME/dotnet` 新增至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="7128a-138">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="7128a-139">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-139">Install with Visual Studio</span></span>

<span data-ttu-id="7128a-140">如果您使用 Visual Studio 開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最低必要版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-140">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="7128a-141">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="7128a-141">.NET Core SDK version</span></span> | <span data-ttu-id="7128a-142">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="7128a-142">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="7128a-143">3.1</span><span class="sxs-lookup"><span data-stu-id="7128a-143">3.1</span></span>                   | <span data-ttu-id="7128a-144">Visual Studio 2019 16.4 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-144">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="7128a-145">3.0</span><span class="sxs-lookup"><span data-stu-id="7128a-145">3.0</span></span>                   | <span data-ttu-id="7128a-146">Visual Studio 2019 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-146">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="7128a-147">2.2</span><span class="sxs-lookup"><span data-stu-id="7128a-147">2.2</span></span>                   | <span data-ttu-id="7128a-148">Visual Studio 2017 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-148">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="7128a-149">2.1</span><span class="sxs-lookup"><span data-stu-id="7128a-149">2.1</span></span>                   | <span data-ttu-id="7128a-150">Visual Studio 2017 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-150">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="7128a-151">如果您已安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-151">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="7128a-152">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7128a-152">Open Visual Studio.</span></span>
01. <span data-ttu-id="7128a-153">選取 **[** 說明] > **關於 Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="7128a-153">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="7128a-154">閱讀 [**關於**] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7128a-154">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="7128a-155">Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="7128a-155">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="7128a-156">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="7128a-156">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="7128a-157">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="7128a-157">Select a workload</span></span>

<span data-ttu-id="7128a-158">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列其中一個或多個工作負載：</span><span class="sxs-lookup"><span data-stu-id="7128a-158">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="7128a-159">[**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。</span><span class="sxs-lookup"><span data-stu-id="7128a-159">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="7128a-160">**Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="7128a-160">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7128a-161">**Web & 雲端**一節中的**Azure 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="7128a-161">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7128a-162">**桌上型電腦 & Mobile**一節中的 **.net 桌面開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="7128a-162">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="7128a-163">[使用 .NET Core 工作負載 ![Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="7128a-163">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="7128a-164">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-164">Download and manually install</span></span>

<span data-ttu-id="7128a-165">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="7128a-165">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="7128a-166">然後，建立要安裝的目錄，例如 `%USERPROFILE%\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="7128a-166">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="7128a-167">最後，將下載的 zip 檔案解壓縮至該目錄。</span><span class="sxs-lookup"><span data-stu-id="7128a-167">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="7128a-168">根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7128a-168">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="7128a-169">您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="7128a-169">You have to explicitly choose to use it.</span></span> <span data-ttu-id="7128a-170">若要這麼做，請變更應用程式啟動時所使用的環境變數：</span><span class="sxs-lookup"><span data-stu-id="7128a-170">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="7128a-171">這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7128a-171">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="7128a-172">即使已設定這些環境變數，在選取最佳架構來執行應用程式時，.NET Core 仍然會考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="7128a-172">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="7128a-173">預設值通常是 `C:\Program Files\dotnet`，這是安裝程式所使用的。</span><span class="sxs-lookup"><span data-stu-id="7128a-173">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="7128a-174">您也可以藉由設定此環境變數，指示執行時間只使用自訂安裝位置：</span><span class="sxs-lookup"><span data-stu-id="7128a-174">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="7128a-175">使用 Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-175">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="7128a-176">Visual Studio for Mac 在選取 [ **.Net Core** ] 工作負載時安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="7128a-176">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="7128a-177">若要開始在 macOS 上使用 .NET Core 開發，請參閱[安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="7128a-177">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="7128a-178">針對最新版本 .NET Core 3.1，您必須使用 Visual Studio for Mac 8.4 Preview。</span><span class="sxs-lookup"><span data-stu-id="7128a-178">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="7128a-179">[使用 .NET Core 工作負載功能 ![macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="7128a-179">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="7128a-180">與 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-180">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="7128a-181">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="7128a-181">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="7128a-182">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="7128a-182">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="7128a-183">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援十分簡單。</span><span class="sxs-lookup"><span data-stu-id="7128a-183">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="7128a-184">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="7128a-184">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="7128a-185">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7128a-185">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="7128a-186">[從 Visual Studio Code C# marketplace 安裝延伸](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)模組。</span><span class="sxs-lookup"><span data-stu-id="7128a-186">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="7128a-187">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-187">Install with PowerShell automation</span></span>

<span data-ttu-id="7128a-188">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="7128a-188">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="7128a-189">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="7128a-189">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="7128a-190">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="7128a-190">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7128a-191">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="7128a-191">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="7128a-192">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="7128a-192">Install with bash automation</span></span>

<span data-ttu-id="7128a-193">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="7128a-193">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="7128a-194">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="7128a-194">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="7128a-195">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="7128a-195">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7128a-196">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="7128a-196">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="7128a-197">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="7128a-197">All .NET Core downloads</span></span>

<span data-ttu-id="7128a-198">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="7128a-198">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="7128a-199">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="7128a-199">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="7128a-200">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="7128a-200">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="7128a-201">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="7128a-201">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="7128a-202">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="7128a-202">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="7128a-203">Docker</span><span class="sxs-lookup"><span data-stu-id="7128a-203">Docker</span></span>

<span data-ttu-id="7128a-204">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="7128a-204">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="7128a-205">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="7128a-205">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="7128a-206">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="7128a-206">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="7128a-207">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="7128a-207">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="7128a-208">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="7128a-208">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="7128a-209">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="7128a-209">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="7128a-210">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="7128a-210">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="7128a-211">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-211">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7128a-212">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7128a-212">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="7128a-213">[教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="7128a-213">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="7128a-214">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-214">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="7128a-215">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-215">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="7128a-216">使用[MacOS Catalina notarization](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-216">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="7128a-217">[教學課程：開始使用 macOS](../tutorials/using-on-mac-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-217">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="7128a-218">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-218">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="7128a-219">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-219">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="7128a-220">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-220">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="7128a-221">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7128a-221">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
