---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core SDK-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索開發 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 9b170765740600641f96056adc08ff0b69a03338
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768310"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="f0af4-104">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="f0af4-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="f0af4-105">在本文中，您將瞭解如何安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f0af4-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="f0af4-106">.NET Core SDK 可用來建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="f0af4-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="f0af4-107">.NET Core 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="f0af4-107">The .NET Core runtime is always installed with the SDK.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="f0af4-108">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-108">Install with an installer</span></span>

<span data-ttu-id="f0af4-109">Windows 有獨立的安裝程式，可用於安裝 .NET Core 3.1 SDK：</span><span class="sxs-lookup"><span data-stu-id="f0af4-109">Windows has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="f0af4-110">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="f0af4-110">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f0af4-111">x86 （32位） Cpu</span><span class="sxs-lookup"><span data-stu-id="f0af4-111">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="f0af4-112">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-112">Install with an installer</span></span>

<span data-ttu-id="f0af4-113">macOS 具有可用於安裝 .NET Core 3.1 SDK 的獨立安裝程式：</span><span class="sxs-lookup"><span data-stu-id="f0af4-113">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="f0af4-114">x64 （64位） Cpu</span><span class="sxs-lookup"><span data-stu-id="f0af4-114">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="f0af4-115">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-115">Download and manually install</span></span>

<span data-ttu-id="f0af4-116">除了適用于 .NET Core 的 macOS 安裝程式之外，您還可以下載並手動安裝 SDK。</span><span class="sxs-lookup"><span data-stu-id="f0af4-116">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK.</span></span>

<span data-ttu-id="f0af4-117">若要解壓縮 SDK，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-117">To extract the SDK and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="f0af4-118">然後，開啟終端機並執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="f0af4-118">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="f0af4-119">假設執行時間已下載至檔案 `~/Downloads/dotnet-sdk.pkg` 。</span><span class="sxs-lookup"><span data-stu-id="f0af4-119">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-sdk.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="f0af4-120">在 Linux 上安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-120">Install on Linux</span></span>

<span data-ttu-id="f0af4-121">這篇文章很快就會移除。</span><span class="sxs-lookup"><span data-stu-id="f0af4-121">This article will be removed soon.</span></span> <span data-ttu-id="f0af4-122">目前已藉由[在 Linux 上安裝 .Net Core](linux.md)來取代。</span><span class="sxs-lookup"><span data-stu-id="f0af4-122">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="f0af4-123">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-123">Install with Visual Studio</span></span>

<span data-ttu-id="f0af4-124">如果您使用 Visual Studio 開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最低必要版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-124">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="f0af4-125">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="f0af4-125">.NET Core SDK version</span></span> | <span data-ttu-id="f0af4-126">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="f0af4-126">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="f0af4-127">3.1</span><span class="sxs-lookup"><span data-stu-id="f0af4-127">3.1</span></span>                   | <span data-ttu-id="f0af4-128">Visual Studio 2019 16.4 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-128">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="f0af4-129">3.0</span><span class="sxs-lookup"><span data-stu-id="f0af4-129">3.0</span></span>                   | <span data-ttu-id="f0af4-130">Visual Studio 2019 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-130">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="f0af4-131">2.2</span><span class="sxs-lookup"><span data-stu-id="f0af4-131">2.2</span></span>                   | <span data-ttu-id="f0af4-132">Visual Studio 2017 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-132">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="f0af4-133">2.1</span><span class="sxs-lookup"><span data-stu-id="f0af4-133">2.1</span></span>                   | <span data-ttu-id="f0af4-134">Visual Studio 2017 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-134">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="f0af4-135">如果您已安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-135">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="f0af4-136">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f0af4-136">Open Visual Studio.</span></span>
01. <span data-ttu-id="f0af4-137">選取 **[**  >  **關於 Microsoft Visual Studio**的說明]。</span><span class="sxs-lookup"><span data-stu-id="f0af4-137">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="f0af4-138">閱讀 [**關於**] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f0af4-138">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="f0af4-139">Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="f0af4-139">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="f0af4-140">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-140">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="f0af4-141">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="f0af4-141">Select a workload</span></span>

<span data-ttu-id="f0af4-142">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列其中一個或多個工作負載：</span><span class="sxs-lookup"><span data-stu-id="f0af4-142">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="f0af4-143">[**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。</span><span class="sxs-lookup"><span data-stu-id="f0af4-143">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="f0af4-144">**Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="f0af4-144">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f0af4-145">**Web & 雲端**一節中的**Azure 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="f0af4-145">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="f0af4-146">**桌上型電腦 & Mobile**一節中的 **.net 桌面開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="f0af4-146">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="f0af4-147">[![Windows Visual Studio 2019 與 .NET Core 工作負載](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="f0af4-147">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="f0af4-148">下載並手動安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-148">Download and manually install</span></span>

<span data-ttu-id="f0af4-149">若要將執行時間解壓縮，並在終端機上提供 .NET Core CLI 命令，請先[下載](#all-net-core-downloads).net Core 二進位版本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="f0af4-150">然後，建立要安裝的目錄，例如 `%USERPROFILE%\dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="f0af4-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="f0af4-151">最後，將下載的 zip 檔案解壓縮至該目錄。</span><span class="sxs-lookup"><span data-stu-id="f0af4-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="f0af4-152">根據預設，.NET Core CLI 命令和應用程式不會使用以這種方式安裝的 .NET Core，因此您必須明確地選擇使用它。</span><span class="sxs-lookup"><span data-stu-id="f0af4-152">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="f0af4-153">若要這麼做，請變更應用程式啟動時所使用的環境變數：</span><span class="sxs-lookup"><span data-stu-id="f0af4-153">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="f0af4-154">這種方法可讓您將多個版本安裝到不同的位置，然後明確地選擇應用程式應該使用的安裝位置，方法是以指向該位置的環境變數執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0af4-154">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="f0af4-155">即使已設定這些環境變數，在選取最佳架構來執行應用程式時，.NET Core 仍然會考慮預設的全域安裝位置。</span><span class="sxs-lookup"><span data-stu-id="f0af4-155">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="f0af4-156">預設值通常是 `C:\Program Files\dotnet` 安裝程式所使用的。</span><span class="sxs-lookup"><span data-stu-id="f0af4-156">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="f0af4-157">您也可以藉由設定此環境變數，指示執行時間只使用自訂安裝位置：</span><span class="sxs-lookup"><span data-stu-id="f0af4-157">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="f0af4-158">使用 Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-158">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="f0af4-159">Visual Studio for Mac 在選取 [ **.Net Core** ] 工作負載時安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="f0af4-159">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="f0af4-160">若要開始在 macOS 上使用 .NET Core 開發，請參閱[安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-160">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="f0af4-161">針對最新版本 .NET Core 3.1，您必須使用 Visual Studio for Mac 8.4 Preview。</span><span class="sxs-lookup"><span data-stu-id="f0af4-161">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="f0af4-162">[![使用 .NET Core 工作負載功能的 macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="f0af4-162">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-windows,os-macos"

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="f0af4-163">與 Visual Studio Code 一起安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-163">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="f0af4-164">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="f0af4-164">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="f0af4-165">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="f0af4-165">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="f0af4-166">雖然 Visual Studio Code 不會隨附像 Visual Studio 這樣的自動化 .NET Core 安裝程式，但新增 .NET Core 支援十分簡單。</span><span class="sxs-lookup"><span data-stu-id="f0af4-166">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="f0af4-167">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-167">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="f0af4-168">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-168">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="f0af4-169">[從 Visual Studio Code Marketplace 安裝 c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能。</span><span class="sxs-lookup"><span data-stu-id="f0af4-169">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="f0af4-170">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-170">Install with PowerShell automation</span></span>

<span data-ttu-id="f0af4-171">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="f0af4-171">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="f0af4-172">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-172">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f0af4-173">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="f0af4-173">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="f0af4-174">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-174">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="f0af4-175">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="f0af4-175">Install with bash automation</span></span>

<span data-ttu-id="f0af4-176">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="f0af4-176">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="f0af4-177">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-177">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="f0af4-178">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="f0af4-178">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="f0af4-179">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="f0af4-179">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="f0af4-180">所有 .NET Core 下載</span><span class="sxs-lookup"><span data-stu-id="f0af4-180">All .NET Core downloads</span></span>

<span data-ttu-id="f0af4-181">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="f0af4-181">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="f0af4-182">.NET Core 3.1 下載</span><span class="sxs-lookup"><span data-stu-id="f0af4-182">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="f0af4-183">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="f0af4-183">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="f0af4-184">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="f0af4-184">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="f0af4-185">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="f0af4-185">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="f0af4-186">Docker</span><span class="sxs-lookup"><span data-stu-id="f0af4-186">Docker</span></span>

<span data-ttu-id="f0af4-187">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="f0af4-187">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="f0af4-188">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="f0af4-188">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="f0af4-189">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="f0af4-189">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="f0af4-190">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="f0af4-190">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="f0af4-191">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="f0af4-191">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="f0af4-192">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="f0af4-192">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="f0af4-193">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="f0af4-193">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="f0af4-194">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-194">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f0af4-195">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f0af4-195">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="f0af4-196">[教學課程： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="f0af4-196">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="f0af4-197">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-197">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="f0af4-198">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-198">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="f0af4-199">使用[MacOS Catalina notarization](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-199">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="f0af4-200">[教學課程：開始使用 macOS](../tutorials/using-on-mac-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-200">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="f0af4-201">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-201">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="f0af4-202">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-202">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="f0af4-203">[教學課程：使用 Visual Studio Code 建立新的應用程式](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-203">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="f0af4-204">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="f0af4-204">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
