---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core SDK-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索開發 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 54819b409422e8bda9efe25478aa3424683a380b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567472"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="94aed-104">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="94aed-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="94aed-105">在本文中，您將瞭解如何安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="94aed-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="94aed-106">.NET Core SDK 可用來建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="94aed-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="94aed-107">.NET Core 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="94aed-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="94aed-108">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-108">Install with an installer</span></span>

<span data-ttu-id="94aed-109">Windows 和 macOS 都有獨立的安裝程式，可以用來安裝 .NET Core 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="94aed-109">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="94aed-110">Windows [x64 （64位） cpu](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 （32位） cpu](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="94aed-110">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="94aed-111">macOS [x64 （64位） cpu](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="94aed-111">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="94aed-112">使用套件管理員進行安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-112">Install with a package manager</span></span>

<span data-ttu-id="94aed-113">您可以使用許多常見的 Linux 套件管理員來安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="94aed-113">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="94aed-114">如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="94aed-114">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="94aed-115">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-115">Download and manually install</span></span>

<span data-ttu-id="94aed-116">若要解壓縮 SDK，並在終端機上提供命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="94aed-116">To extract the SDK and make the commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="94aed-117">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="94aed-117">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.0.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="94aed-118">上述命令只會將 .NET SDK 命令提供給其執行所在的終端機會話。</span><span class="sxs-lookup"><span data-stu-id="94aed-118">The above commands will only make the .NET SDK commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="94aed-119">您可以編輯您的 shell 設定檔，以永久新增命令。</span><span class="sxs-lookup"><span data-stu-id="94aed-119">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="94aed-120">有許多不同的 shell 可供 Linux 使用，而且每個都有不同的設定檔。</span><span class="sxs-lookup"><span data-stu-id="94aed-120">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="94aed-121">例如：</span><span class="sxs-lookup"><span data-stu-id="94aed-121">For example:</span></span>
>
> - <span data-ttu-id="94aed-122">**Bash Shell**： *~/. bash_profile*， *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="94aed-122">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="94aed-123">**Korn Shell**： *~/.kshrc*或 *. profile*</span><span class="sxs-lookup"><span data-stu-id="94aed-123">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="94aed-124">**Z Shell**： *~/.zshrc*或 *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="94aed-124">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="94aed-125">為您的 shell 編輯適當的原始程式檔，並將 `:$HOME/dotnet` 新增至現有 `PATH` 語句的結尾。</span><span class="sxs-lookup"><span data-stu-id="94aed-125">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="94aed-126">如果未包含任何 `PATH` 語句，請加入具有 `export PATH=$PATH:$HOME/dotnet`的新行。</span><span class="sxs-lookup"><span data-stu-id="94aed-126">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="94aed-127">此外，將 `export DOTNET_ROOT=$HOME/dotnet` 新增至檔案結尾。</span><span class="sxs-lookup"><span data-stu-id="94aed-127">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="94aed-128">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-128">Install with Visual Studio</span></span>

<span data-ttu-id="94aed-129">如果您使用 Visual Studio 開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最低必要版本。</span><span class="sxs-lookup"><span data-stu-id="94aed-129">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="94aed-130">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="94aed-130">.NET Core SDK version</span></span> | <span data-ttu-id="94aed-131">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="94aed-131">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="94aed-132">3.1 預覽</span><span class="sxs-lookup"><span data-stu-id="94aed-132">3.1 Preview</span></span>           | <span data-ttu-id="94aed-133">Visual Studio 2019 16.4 preview 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="94aed-133">Visual Studio 2019 version 16.4 preview or higher.</span></span> |
| <span data-ttu-id="94aed-134">3.0</span><span class="sxs-lookup"><span data-stu-id="94aed-134">3.0</span></span>                   | <span data-ttu-id="94aed-135">Visual Studio 2019 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="94aed-135">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="94aed-136">2.2</span><span class="sxs-lookup"><span data-stu-id="94aed-136">2.2</span></span>                   | <span data-ttu-id="94aed-137">Visual Studio 2017 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="94aed-137">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="94aed-138">2.1</span><span class="sxs-lookup"><span data-stu-id="94aed-138">2.1</span></span>                   | <span data-ttu-id="94aed-139">Visual Studio 2017 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="94aed-139">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="94aed-140">如果您已安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="94aed-140">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="94aed-141">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="94aed-141">Open Visual Studio.</span></span>
01. <span data-ttu-id="94aed-142">選取 **[** 說明] > **關於 Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="94aed-142">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="94aed-143">閱讀 [**關於**] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="94aed-143">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="94aed-144">Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="94aed-144">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="94aed-145">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="94aed-145">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="94aed-146">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="94aed-146">Select a workload</span></span>

<span data-ttu-id="94aed-147">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列其中一個工作負載：</span><span class="sxs-lookup"><span data-stu-id="94aed-147">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="94aed-148">[**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。</span><span class="sxs-lookup"><span data-stu-id="94aed-148">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="94aed-149">**Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="94aed-149">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="94aed-150">**Web & 雲端**一節中的**Azure 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="94aed-150">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="94aed-151">**桌上型電腦 & Mobile**一節中的 **.net 桌面開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="94aed-151">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="94aed-152">[使用 .NET Core 工作負載 ![Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="94aed-152">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="94aed-153">使用 Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-153">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="94aed-154">Visual Studio for Mac 在選取 [ **.Net Core** ] 工作負載時安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="94aed-154">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="94aed-155">若要開始在 macOS 上使用 .NET Core 開發，請參閱[安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="94aed-155">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="94aed-156">[使用 .NET Core 工作負載功能 ![macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="94aed-156">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="94aed-157">與 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-157">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="94aed-158">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="94aed-158">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="94aed-159">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="94aed-159">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="94aed-160">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援十分簡單。</span><span class="sxs-lookup"><span data-stu-id="94aed-160">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="94aed-161">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="94aed-161">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="94aed-162">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="94aed-162">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="94aed-163">[從 Visual Studio Code C# marketplace 安裝延伸](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)模組。</span><span class="sxs-lookup"><span data-stu-id="94aed-163">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="94aed-164">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-164">Install with PowerShell automation</span></span>

<span data-ttu-id="94aed-165">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="94aed-165">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="94aed-166">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="94aed-166">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="94aed-167">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="94aed-167">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="94aed-168">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="94aed-168">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="94aed-169">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="94aed-169">Install with bash automation</span></span>

<span data-ttu-id="94aed-170">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="94aed-170">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="94aed-171">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="94aed-171">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="94aed-172">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="94aed-172">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="94aed-173">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="94aed-173">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="94aed-174">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="94aed-174">All .NET Core downloads</span></span>

<span data-ttu-id="94aed-175">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="94aed-175">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="94aed-176">.NET Core 3.1 Preview 下載</span><span class="sxs-lookup"><span data-stu-id="94aed-176">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="94aed-177">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="94aed-177">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="94aed-178">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="94aed-178">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="94aed-179">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="94aed-179">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="94aed-180">Docker</span><span class="sxs-lookup"><span data-stu-id="94aed-180">Docker</span></span>

<span data-ttu-id="94aed-181">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="94aed-181">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="94aed-182">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="94aed-182">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="94aed-183">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="94aed-183">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="94aed-184">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="94aed-184">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="94aed-185">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="94aed-185">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="94aed-186">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="94aed-186">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="94aed-187">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="94aed-187">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="94aed-188">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="94aed-188">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="94aed-189">後續步驟</span><span class="sxs-lookup"><span data-stu-id="94aed-189">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="94aed-190">[教學課程C# ： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="94aed-190">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="94aed-191">[教學課程： Visual Basic Hello World 教學](../tutorials/vb-with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="94aed-191">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="94aed-192">[教學課程：使用 Visual Studio Code 建立新的應用程式](https://code.visualstudio.com/docs/languages/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="94aed-192">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="94aed-193">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="94aed-193">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="94aed-194">[教學課程：開始使用 macOS](../tutorials/using-on-mac-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="94aed-194">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="94aed-195">[教學課程：使用 Visual Studio Code 建立新的應用程式](https://code.visualstudio.com/docs/languages/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="94aed-195">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="94aed-196">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="94aed-196">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
