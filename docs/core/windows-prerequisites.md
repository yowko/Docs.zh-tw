---
title: Windows 上 .NET Core 的必要條件
description: 了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。
author: JRAlexander
ms.author: johalex
ms.date: 05/18/2018
ms.openlocfilehash: 3d172c83f0a79744afbaeeff52d7fea62d9b98b6
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="377d4-103">Windows 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="377d4-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="377d4-104">本文會說明在 Windows 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="377d4-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="377d4-105">支援的作業系統版本和跟隨的相依性，適用於在 Windows 開發 .NET Core 應用程式的三種方式：</span><span class="sxs-lookup"><span data-stu-id="377d4-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="377d4-106">命令列</span><span class="sxs-lookup"><span data-stu-id="377d4-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="377d4-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="377d4-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="377d4-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="377d4-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="377d4-109">.NET Core 支援的 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="377d4-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="377d4-110">下列版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="377d4-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="377d4-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="377d4-111">Windows 7 SP1</span></span>
* <span data-ttu-id="377d4-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="377d4-112">Windows 8.1</span></span>
* <span data-ttu-id="377d4-113">Windows 10 年度更新 (1607 版) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="377d4-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="377d4-114">Windows Server 2008 R2 SP1 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="377d4-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="377d4-115">Windows Server 2012 SP1 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="377d4-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="377d4-116">Windows Server 2012 R2 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="377d4-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="377d4-117">Windows Server 2016 或更新版本 (完整伺服器、Server Core 或 Nano Server)</span><span class="sxs-lookup"><span data-stu-id="377d4-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="377d4-118">以下文件有 .NET Core 所支援每個版本作業系統的完整清單：</span><span class="sxs-lookup"><span data-stu-id="377d4-118">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* <span data-ttu-id="377d4-119">[.NET core 2.1 - 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="377d4-119">[.NET Core 2.1 - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)</span></span>
* <span data-ttu-id="377d4-120">[.NET core 2.0 - 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="377d4-120">[.NET Core 2.0 - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)</span></span>
* <span data-ttu-id="377d4-121">[.NET core 1.x - 支援的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="377d4-121">[.NET Core 1.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="377d4-122">.NET Core 的相依性</span><span class="sxs-lookup"><span data-stu-id="377d4-122">.NET Core dependencies</span></span>

<span data-ttu-id="377d4-123">在 Windows 10 和 Windows Server 2016 之前的 Windows 版本上執行時，.NET Core 1.1 和舊版本需要 Visual C++ 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="377d4-123">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="377d4-124">.NET Core 安裝程式會自動安裝此相依性。</span><span class="sxs-lookup"><span data-stu-id="377d4-124">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="377d4-125">必須手動安裝 [Microsoft Visual C++ 2015 可轉散發套件 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) 的時機：</span><span class="sxs-lookup"><span data-stu-id="377d4-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="377d4-126">使用[安裝程式指令碼](./tools/dotnet-install-script.md)安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="377d4-126">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="377d4-127">部署獨立的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="377d4-127">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="377d4-128">從來源建置產品。</span><span class="sxs-lookup"><span data-stu-id="377d4-128">Building the product from source.</span></span>
* <span data-ttu-id="377d4-129">透過 *.zip* 檔案安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="377d4-129">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="377d4-130">這可以包含組建/CI/CD 伺服器。</span><span class="sxs-lookup"><span data-stu-id="377d4-130">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="377d4-131">**適用於 Windows 8.1 和更早版本，或 Windows Server 2012 R2 和更早版本：**</span><span class="sxs-lookup"><span data-stu-id="377d4-131">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="377d4-132">請確定您的 Windows 安裝處於最新狀態，且包含 [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) \(機器翻譯\) (可透過 Windows Update 安裝)。</span><span class="sxs-lookup"><span data-stu-id="377d4-132">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="377d4-133">如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="377d4-133">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="377d4-134">**適用於 Windows 7 或 Windows Server 2008 R2：**</span><span class="sxs-lookup"><span data-stu-id="377d4-134">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="377d4-135">除了 KB2999226，請確定您也已經安裝 [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)。</span><span class="sxs-lookup"><span data-stu-id="377d4-135">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="377d4-136">如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`。</span><span class="sxs-lookup"><span data-stu-id="377d4-136">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="377d4-137">使用 Visual Studio 2017 的必要條件</span><span class="sxs-lookup"><span data-stu-id="377d4-137">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="377d4-138">您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="377d4-138">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="377d4-139">[Visual Studio 2017](#visual-studio-2017) 為 Windows 上的 .NET Core 應用程式提供整合式開發環境。</span><span class="sxs-lookup"><span data-stu-id="377d4-139">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="377d4-140">您可以在[版本資訊](/visualstudio/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。</span><span class="sxs-lookup"><span data-stu-id="377d4-140">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="377d4-141">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="377d4-141">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="377d4-142">若要在 Visual Studio 2017 中開發 .NET Core 2.x 應用程式：</span><span class="sxs-lookup"><span data-stu-id="377d4-142">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="377d4-143">[下載並安裝 Visual Studio 2017 15.3.0 版本或更高版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。</span><span class="sxs-lookup"><span data-stu-id="377d4-143">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="377d4-145">安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 2017 預設使用 .NET Core 1.x。</span><span class="sxs-lookup"><span data-stu-id="377d4-145">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="377d4-146">安裝 .NET Core 2.x SDK 以取得 Visual Studio 2017 中的 .NET Core 2.x 支援。</span><span class="sxs-lookup"><span data-stu-id="377d4-146">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="377d4-147">安裝 [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="377d4-147">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="377d4-148">使用下列指示將現有或新的 .NET Core 1.x 專案目標重定到 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="377d4-148">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="377d4-149">在 [專案] 功能表上，選擇 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="377d4-149">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="377d4-150">在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.0**。</span><span class="sxs-lookup"><span data-stu-id="377d4-150">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![螢幕擷取畫面：選取 ".NET Core 2.0" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="377d4-152">一旦安裝 .NET Core 2.x SDK，Visual Studio 2017 預設會使用 .NET Core SDK 2.x，而且支援下列動作：</span><span class="sxs-lookup"><span data-stu-id="377d4-152">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="377d4-153">開啟、建置及執行現有的 .NET Core 1.x 專案。</span><span class="sxs-lookup"><span data-stu-id="377d4-153">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="377d4-154">將 .NET Core 1.x 專案重定目標至 .NET Core 2.x、建置和執行。</span><span class="sxs-lookup"><span data-stu-id="377d4-154">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="377d4-155">建立新的 .NET Core 2.x 專案。</span><span class="sxs-lookup"><span data-stu-id="377d4-155">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="377d4-156">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="377d4-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="377d4-157">若要使用 Visual Studio 開發 .NET Core 1.x 應用程式，請[下載並安裝 Visual Studio 2017 RTM (版本 15.0.26228.4) 或更高版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。</span><span class="sxs-lookup"><span data-stu-id="377d4-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="377d4-159">有可能使用 Visual Studio 2015 開發 .NET Core 1.x，但不建議為下列原因而如此做：</span><span class="sxs-lookup"><span data-stu-id="377d4-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="377d4-160">.NET Core 工具是預覽版本，不受支援。</span><span class="sxs-lookup"><span data-stu-id="377d4-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="377d4-161">專案是以 project.json 為基礎，已被取代。</span><span class="sxs-lookup"><span data-stu-id="377d4-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="377d4-162">如需專案格式變更的詳細資訊，請參閱[變更的高階概觀](./tools/cli-msbuild-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="377d4-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="377d4-163">確認 Visual Studio 2017 版本：</span><span class="sxs-lookup"><span data-stu-id="377d4-163">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="377d4-164">在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]**。</span><span class="sxs-lookup"><span data-stu-id="377d4-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="377d4-165">在 [關於 Microsoft Visual Studio] 對話方塊中，確認版本號碼。</span><span class="sxs-lookup"><span data-stu-id="377d4-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="377d4-166">對於 .NET Core 2.1 RC 應用程式，需要 Visual Studio 2017 15.7 版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="377d4-166">For .NET Core 2.1 RC apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="377d4-167">若為 .NET Core 2.0 應用程式，需要 Visual Studio 2017 版本 15.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="377d4-167">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="377d4-168">若為 .NET Core 1.x 應用程式，需要 Visual Studio 2017 版本 15.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="377d4-168">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
