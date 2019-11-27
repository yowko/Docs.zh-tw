---
title: 在 Windows、Linux 和 macOS 上安裝 .NET Core SDK-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core。 探索開發 .NET Core 應用程式所需的相依性。
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2f65e9dc39a4cd1076af1a70dfedfa671f20b42d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450874"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="04320-104">安裝 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="04320-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="04320-105">在本文中，您將瞭解如何安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="04320-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="04320-106">.NET Core SDK 可用來建立 .NET Core 應用程式和程式庫。</span><span class="sxs-lookup"><span data-stu-id="04320-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="04320-107">.NET Core 執行時間一律會與 SDK 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="04320-107">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="04320-108">您可以使用下列其中一個連結直接下載並安裝 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="04320-108">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="04320-109">.NET Core 3.1 Preview 3 下載</span><span class="sxs-lookup"><span data-stu-id="04320-109">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="04320-110">.NET Core 3.0 下載</span><span class="sxs-lookup"><span data-stu-id="04320-110">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="04320-111">.NET Core 2.2 下載</span><span class="sxs-lookup"><span data-stu-id="04320-111">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="04320-112">.NET Core 2.1 下載</span><span class="sxs-lookup"><span data-stu-id="04320-112">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

<span data-ttu-id="04320-113">您也可以將 .NET Core 安裝為整合式開發環境（IDE）的一部分，如下節所述。</span><span class="sxs-lookup"><span data-stu-id="04320-113">You can also install .NET Core as part of an integrated development environment (IDE), detailed in the sections below.</span></span>

## <a name="install-with-an-installer"></a><span data-ttu-id="04320-114">使用安裝程式安裝</span><span class="sxs-lookup"><span data-stu-id="04320-114">Install with an installer</span></span>

<span data-ttu-id="04320-115">Windows 和 macOS 都有獨立的安裝程式，可以用來安裝 .NET Core 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="04320-115">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="04320-116">Windows [X64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="04320-116">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span></span>
- <span data-ttu-id="04320-117">macOS [X64 cpu](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="04320-117">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span></span>

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="04320-118">使用套件管理員進行安裝</span><span class="sxs-lookup"><span data-stu-id="04320-118">Install with a package manager</span></span>

<span data-ttu-id="04320-119">您可以使用許多常見的 Linux 套件管理員來安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="04320-119">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="04320-120">如需詳細資訊，請參閱[Linux 套件管理員-安裝 .Net Core](linux-package-manager-rhel7.md)。</span><span class="sxs-lookup"><span data-stu-id="04320-120">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="04320-121">使用 Visual Studio 安裝</span><span class="sxs-lookup"><span data-stu-id="04320-121">Install with Visual Studio</span></span>

<span data-ttu-id="04320-122">如果您使用 Visual Studio 開發 .NET Core 應用程式，下表將根據目標 .NET Core SDK 版本描述 Visual Studio 的最低必要版本。</span><span class="sxs-lookup"><span data-stu-id="04320-122">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="04320-123">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="04320-123">.NET Core SDK version</span></span> | <span data-ttu-id="04320-124">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="04320-124">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="04320-125">3.0</span><span class="sxs-lookup"><span data-stu-id="04320-125">3.0</span></span>                   | <span data-ttu-id="04320-126">Visual Studio 2019 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="04320-126">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="04320-127">2.2</span><span class="sxs-lookup"><span data-stu-id="04320-127">2.2</span></span>                   | <span data-ttu-id="04320-128">Visual Studio 2017 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="04320-128">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="04320-129">2.1</span><span class="sxs-lookup"><span data-stu-id="04320-129">2.1</span></span>                   | <span data-ttu-id="04320-130">Visual Studio 2017 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="04320-130">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="04320-131">如果您已安裝 Visual Studio，您可以使用下列步驟來檢查您的版本。</span><span class="sxs-lookup"><span data-stu-id="04320-131">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="04320-132">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="04320-132">Open Visual Studio.</span></span>
01. <span data-ttu-id="04320-133">選取 **[** 說明] > **關於 Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="04320-133">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="04320-134">閱讀 [**關於**] 對話方塊中的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="04320-134">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="04320-135">Visual Studio 可以安裝最新的 .NET Core SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="04320-135">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="04320-136">[下載 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="04320-136">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="04320-137">選取工作負載</span><span class="sxs-lookup"><span data-stu-id="04320-137">Select a workload</span></span>

<span data-ttu-id="04320-138">安裝或修改 Visual Studio 時，請根據您所建立的應用程式類型，選取下列其中一個工作負載：</span><span class="sxs-lookup"><span data-stu-id="04320-138">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="04320-139">[**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。</span><span class="sxs-lookup"><span data-stu-id="04320-139">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="04320-140">**Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="04320-140">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="04320-141">**Web & 雲端**一節中的**Azure 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="04320-141">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="04320-142">**桌上型電腦 & Mobile**一節中的 **.net 桌面開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="04320-142">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="04320-143">[使用 .NET Core 工作負載 ![Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="04320-143">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="04320-144">使用 Visual Studio for Mac 安裝</span><span class="sxs-lookup"><span data-stu-id="04320-144">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="04320-145">Visual Studio for Mac 在選取 [ **.Net Core** ] 工作負載時安裝 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="04320-145">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="04320-146">若要開始在 macOS 上使用 .NET Core 開發，請參閱[安裝適用于 Mac 的 Visual Studio 2019](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="04320-146">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="04320-147">[使用 .NET Core 工作負載功能 ![macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="04320-147">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-from-visual-studio-code"></a><span data-ttu-id="04320-148">從 Visual Studio Code 安裝</span><span class="sxs-lookup"><span data-stu-id="04320-148">Install from Visual Studio Code</span></span>

<span data-ttu-id="04320-149">Visual Studio Code 是一種功能強大且輕量的原始程式碼編輯器，可在您的桌面上執行。</span><span class="sxs-lookup"><span data-stu-id="04320-149">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="04320-150">Visual Studio Code 適用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="04320-150">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="04320-151">雖然 Visual Studio Code 不隨附 .NET Core 支援，但新增 .NET Core 支援很簡單。</span><span class="sxs-lookup"><span data-stu-id="04320-151">While Visual Studio Code doesn't come with .NET Core support, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="04320-152">[下載並安裝 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="04320-152">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="04320-153">[下載並安裝 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0)。</span><span class="sxs-lookup"><span data-stu-id="04320-153">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>
01. <span data-ttu-id="04320-154">[從 Visual Studio Code C# marketplace 安裝延伸](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)模組。</span><span class="sxs-lookup"><span data-stu-id="04320-154">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="04320-155">使用 PowerShell 自動化進行安裝</span><span class="sxs-lookup"><span data-stu-id="04320-155">Install with PowerShell automation</span></span>

<span data-ttu-id="04320-156">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="04320-156">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="04320-157">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="04320-157">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="04320-158">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="04320-158">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="04320-159">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="04320-159">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="04320-160">使用 bash automation 進行安裝</span><span class="sxs-lookup"><span data-stu-id="04320-160">Install with bash automation</span></span>

<span data-ttu-id="04320-161">[Dotnet-安裝腳本](../tools/dotnet-install-script.md)會用於 SDK 的自動化和非系統管理員安裝。</span><span class="sxs-lookup"><span data-stu-id="04320-161">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="04320-162">您可以從 [ [dotnet-安裝腳本參考] 頁面](../tools/dotnet-install-script.md)下載此腳本。</span><span class="sxs-lookup"><span data-stu-id="04320-162">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="04320-163">腳本預設為安裝最新的[長期支援（LTS）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本，也就是 .net Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="04320-163">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="04320-164">若要安裝目前版本的 .NET Core，請使用下列參數執行腳本。</span><span class="sxs-lookup"><span data-stu-id="04320-164">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="04320-165">Docker</span><span class="sxs-lookup"><span data-stu-id="04320-165">Docker</span></span>

<span data-ttu-id="04320-166">容器提供輕量的方式，將您的應用程式與主機系統的其餘部分隔離。</span><span class="sxs-lookup"><span data-stu-id="04320-166">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="04320-167">相同電腦上的容器只會共用核心，並使用提供給您應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="04320-167">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="04320-168">.NET Core 可以在 Docker 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="04320-168">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="04320-169">官方 .NET Core Docker 映像會發佈至 Microsoft 容器登錄 (MCR)，並且可在 [Microsoft.NET Core Docker Hub 存放庫](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\) 中找到。</span><span class="sxs-lookup"><span data-stu-id="04320-169">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="04320-170">每個存放庫都包含您可以使用的 .NET (SDK 或執行階段) 與作業系統不同組合的映像。</span><span class="sxs-lookup"><span data-stu-id="04320-170">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="04320-171">Microsoft 會提供針對特定案例量身訂做的映像。</span><span class="sxs-lookup"><span data-stu-id="04320-171">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="04320-172">例如，[ASP.NET Core 存放庫](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) \(英文\) 可提供為了在生產環境中執行 ASP.NET Core 應用程式而建置的映像。</span><span class="sxs-lookup"><span data-stu-id="04320-172">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="04320-173">如需在 Docker 容器中使用 .NET Core 的詳細資訊，請參閱[.net 和 Docker 簡介](../docker/introduction.md)和[範例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="04320-173">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="04320-174">後續步驟</span><span class="sxs-lookup"><span data-stu-id="04320-174">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="04320-175">[教學課程C# ： Hello World 教學](../tutorials/with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="04320-175">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="04320-176">[教學課程： Visual Basic Hello World 教學](../tutorials/vb-with-visual-studio.md)課程。</span><span class="sxs-lookup"><span data-stu-id="04320-176">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="04320-177">[教學課程：使用 Visual Studio Code 建立新的應用程式](https://code.visualstudio.com/docs/languages/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="04320-177">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="04320-178">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="04320-178">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="04320-179">[教學課程：開始使用 macOS](../tutorials/using-on-mac-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="04320-179">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="04320-180">[教學課程：使用 Visual Studio Code 建立新的應用程式](https://code.visualstudio.com/docs/languages/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="04320-180">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="04320-181">[教學課程：容器化 .Net Core 應用程式](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="04320-181">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
