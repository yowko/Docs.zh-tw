---
title: Windows 上 .NET Core 的必要條件
description: 了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。
ms.date: 12/05/2018
ms.openlocfilehash: 8f9a823ab3eea15d7e33da6ff00992057c8c4e38
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130871"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="56cd8-103">Windows 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="56cd8-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="56cd8-104">本文會說明支援的 OS 版本，以便在 Windows 上執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="56cd8-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="56cd8-105">支援的作業系統版本和跟隨的相依性，適用於在 Windows 開發 .NET Core 應用程式的三種方式：</span><span class="sxs-lookup"><span data-stu-id="56cd8-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="56cd8-106">命令列</span><span class="sxs-lookup"><span data-stu-id="56cd8-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="56cd8-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="56cd8-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [<span data-ttu-id="56cd8-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="56cd8-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="56cd8-109">此外，如果您正在使用 Visual Studio 2017 在 Windows 上進行開發，則[使用 Visual Studio 2017 的必要條件](#prerequisites-with-visual-studio-2017)一節將詳細介紹 .NET Core 開發支援的最低版本。</span><span class="sxs-lookup"><span data-stu-id="56cd8-109">Also, if you're developing on Windows using Visual Studio 2017, the [Prerequisites with Visual Studio 2017](#prerequisites-with-visual-studio-2017) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="56cd8-110">.NET Core 支援的 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="56cd8-110">.NET Core supported Windows versions</span></span>

<span data-ttu-id="56cd8-111">下列版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="56cd8-111">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="56cd8-112">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="56cd8-112">Windows 7 SP1</span></span>
* <span data-ttu-id="56cd8-113">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="56cd8-113">Windows 8.1</span></span>
* <span data-ttu-id="56cd8-114">Windows 10 年度更新 (1607 版) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="56cd8-114">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="56cd8-115">Windows Server 2008 R2 SP1 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="56cd8-115">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="56cd8-116">Windows Server 2012 SP1 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="56cd8-116">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="56cd8-117">Windows Server 2012 R2 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="56cd8-117">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="56cd8-118">Windows Server 2016 或更新版本 (完整伺服器、Server Core 或 Nano Server)</span><span class="sxs-lookup"><span data-stu-id="56cd8-118">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="56cd8-119">.NET core 支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="56cd8-119">.NET Core supported operating systems</span></span>

<span data-ttu-id="56cd8-120">以下文件有 .NET Core 所支援每個版本作業系統的完整清單：</span><span class="sxs-lookup"><span data-stu-id="56cd8-120">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="56cd8-121">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="56cd8-121">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="56cd8-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="56cd8-122">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="56cd8-123">.NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="56cd8-123">.NET Core 1.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1-supported-os.md)
* [<span data-ttu-id="56cd8-124">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="56cd8-124">.NET Core 1.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

<span data-ttu-id="56cd8-125">如需下載連結和詳細資訊，請參閱 [NET 下載](https://www.microsoft.com/net/download)以下載最新版本或 [.NET 下載封存](https://dotnet.microsoft.com/download/archives#dotnet-core) (針對舊版本)。</span><span class="sxs-lookup"><span data-stu-id="56cd8-125">For download links and more information, see [.NET downloads](https://www.microsoft.com/net/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="56cd8-126">.NET Core 的相依性</span><span class="sxs-lookup"><span data-stu-id="56cd8-126">.NET Core dependencies</span></span>

<span data-ttu-id="56cd8-127">在 Windows 10 和 Windows Server 2016 之前的 Windows 版本上執行時，.NET Core 1.1 和舊版本需要 Visual C++ 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="56cd8-127">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="56cd8-128">.NET Core 安裝程式會自動安裝此相依性。</span><span class="sxs-lookup"><span data-stu-id="56cd8-128">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="56cd8-129">必須手動安裝 [Microsoft Visual C++ 2015 可轉散發套件 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) 的時機：</span><span class="sxs-lookup"><span data-stu-id="56cd8-129">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="56cd8-130">使用[安裝程式指令碼](./tools/dotnet-install-script.md)安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="56cd8-130">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="56cd8-131">部署獨立的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="56cd8-131">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="56cd8-132">從來源建置產品。</span><span class="sxs-lookup"><span data-stu-id="56cd8-132">Building the product from source.</span></span>
* <span data-ttu-id="56cd8-133">透過 *.zip* 檔案安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="56cd8-133">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="56cd8-134">這可以包含組建/CI/CD 伺服器。</span><span class="sxs-lookup"><span data-stu-id="56cd8-134">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="56cd8-135">**適用於 Windows 8.1 和更早版本，或 Windows Server 2012 R2 和更早版本：**</span><span class="sxs-lookup"><span data-stu-id="56cd8-135">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="56cd8-136">請確定您的 Windows 安裝處於最新狀態，且包含 [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) \(機器翻譯\) (可透過 Windows Update 安裝)。</span><span class="sxs-lookup"><span data-stu-id="56cd8-136">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="56cd8-137">如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="56cd8-137">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="56cd8-138">**適用於 Windows 7 或 Windows Server 2008 R2：**</span><span class="sxs-lookup"><span data-stu-id="56cd8-138">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="56cd8-139">除了 KB2999226，請確定您也已經安裝 [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)。</span><span class="sxs-lookup"><span data-stu-id="56cd8-139">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="56cd8-140">如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`。</span><span class="sxs-lookup"><span data-stu-id="56cd8-140">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="56cd8-141">使用 Visual Studio 2017 的必要條件</span><span class="sxs-lookup"><span data-stu-id="56cd8-141">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="56cd8-142">您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="56cd8-142">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="56cd8-143">Visual Studio 2017 可為 Windows 上的 .NET Core 應用程式提供整合式開發環境。</span><span class="sxs-lookup"><span data-stu-id="56cd8-143">Visual Studio 2017 provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="56cd8-144">您可以在[版本資訊](/visualstudio/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。</span><span class="sxs-lookup"><span data-stu-id="56cd8-144">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="56cd8-145">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="56cd8-145">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="56cd8-146">若要在 Visual Studio 2017 中開發使用 .NET Core 2.2 SDK 的 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="56cd8-146">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="56cd8-147">[下載並安裝 Visual Studio 2017 15.9.0 版本或更新版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。</span><span class="sxs-lookup"><span data-stu-id="56cd8-147">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="56cd8-149">安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 通常會安裝舊版的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="56cd8-149">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="56cd8-150">例如，安裝工作負載之後，Visual Studio 2017 15.9 預設會使用 .NET Core 2.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="56cd8-150">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="56cd8-151">若要更新 Visual Studio 以使用 .NET Core 2.2 SDK：</span><span class="sxs-lookup"><span data-stu-id="56cd8-151">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="56cd8-152">安裝 [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="56cd8-152">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="56cd8-153">如果您希望專案使用最新的 .NET Core 執行階段，請使用下列指示將現有或新的 .NET Core 專案目標重新設定為 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="56cd8-153">If you want your project to use the latest .NET Core runtime, retarget existing or new .NET Core projects to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="56cd8-154">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="56cd8-154">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="56cd8-155">在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.2**。</span><span class="sxs-lookup"><span data-stu-id="56cd8-155">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![螢幕擷取畫面：選取 ".NET Core 2.2" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="56cd8-157">一旦使用 .NET Core 2.2 SDK 設定 Visual Studio，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="56cd8-157">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="56cd8-158">開啟、建置及執行現有的 .NET Core 1.x 和 2.x 專案。</span><span class="sxs-lookup"><span data-stu-id="56cd8-158">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="56cd8-159">將 .NET Core 1.x 和 2.x 專案目標重新設定為 .NET Core 2.2、建置和執行。</span><span class="sxs-lookup"><span data-stu-id="56cd8-159">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="56cd8-160">建立新的 .NET Core 2.2 專案。</span><span class="sxs-lookup"><span data-stu-id="56cd8-160">Create new .NET Core 2.2 projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="56cd8-161">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="56cd8-161">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="56cd8-162">若要使用 Visual Studio 開發 .NET Core 1.x 應用程式，請[下載並安裝 Visual Studio 2017](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。</span><span class="sxs-lookup"><span data-stu-id="56cd8-162">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="56cd8-164">有可能使用 Visual Studio 2015 開發 .NET Core 1.x，但不建議為下列原因而如此做：</span><span class="sxs-lookup"><span data-stu-id="56cd8-164">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="56cd8-165">.NET Core 工具是預覽版本，不受支援。</span><span class="sxs-lookup"><span data-stu-id="56cd8-165">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="56cd8-166">專案是以 project.json 為基礎，已被取代。</span><span class="sxs-lookup"><span data-stu-id="56cd8-166">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="56cd8-167">如需專案格式變更的詳細資訊，請參閱[變更的高階概觀](./tools/cli-msbuild-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="56cd8-167">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

---

<a name="vs-mapping"></a>

> [!TIP]
> <span data-ttu-id="56cd8-168">確認 Visual Studio 版本：</span><span class="sxs-lookup"><span data-stu-id="56cd8-168">To verify your Visual Studio version:</span></span>
>
> * <span data-ttu-id="56cd8-169">在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]**。</span><span class="sxs-lookup"><span data-stu-id="56cd8-169">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="56cd8-170">在 [關於 Microsoft Visual Studio] 對話方塊中，確認版本號碼。</span><span class="sxs-lookup"><span data-stu-id="56cd8-170">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="56cd8-171">若為 .NET Core 3.0 預覽 1 應用程式，需要 Visual Studio 2019 預覽 1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="56cd8-171">For .NET Core 3.0 Preview 1 apps, Visual Studio 2019 Preview 1 or higher.</span></span>
>   * <span data-ttu-id="56cd8-172">若為 .NET Core 2.2 應用程式，需要 Visual Studio 2017 15.9 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="56cd8-172">For .NET Core 2.2 apps, Visual Studio 2017 version 15.9 or higher.</span></span>
>   * <span data-ttu-id="56cd8-173">若為 .NET Core 2.1 應用程式，需要 Visual Studio 2017 15.7 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="56cd8-173">For .NET Core 2.1 apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="56cd8-174">若為 .NET Core 1.x 應用程式，需要 Visual Studio 2017 版本 15.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="56cd8-174">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
