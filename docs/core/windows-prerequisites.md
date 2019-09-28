---
title: Windows 上 .NET Core 的必要條件
description: 了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: b1557e6910cb6d0b6d7e2b3ce2aec97d3715fec7
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591676"
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="ea8bb-103">Windows 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="ea8bb-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="ea8bb-104">本文會說明支援的 OS 版本，以便在 Windows 上執行 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-104">This article shows the supported OS versions in order to run .NET Core applications on Windows.</span></span> <span data-ttu-id="ea8bb-105">支援的作業系統版本和跟隨的相依性，適用於在 Windows 開發 .NET Core 應用程式的三種方式：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="ea8bb-106">命令列</span><span class="sxs-lookup"><span data-stu-id="ea8bb-106">Command line</span></span>](./tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="ea8bb-107">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ea8bb-107">Visual Studio</span></span>](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [<span data-ttu-id="ea8bb-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ea8bb-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

<span data-ttu-id="ea8bb-109">此外，如果您是使用 Visual Studio 在 Windows 上進行開發，[使用 Visual Studio 一節開發 .Net core 應用程式的必要條件](#prerequisites-to-develop-net-core-apps-with-visual-studio)會更詳細地說明 .net core 開發支援的最低版本。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-109">Also, if you're developing on Windows using Visual Studio, the [Prerequisites to develop .NET Core apps with Visual Studio](#prerequisites-to-develop-net-core-apps-with-visual-studio) section goes in more detail about minimum versions supported for .NET Core development.</span></span>

## <a name="net-core-supported-operating-systems"></a><span data-ttu-id="ea8bb-110">.NET core 支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="ea8bb-110">.NET Core supported operating systems</span></span>

<span data-ttu-id="ea8bb-111">以下文件有 .NET Core 所支援每個版本作業系統的完整清單：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-111">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="ea8bb-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ea8bb-112">.NET Core 3.0</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [<span data-ttu-id="ea8bb-113">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ea8bb-113">.NET Core 2.2</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [<span data-ttu-id="ea8bb-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ea8bb-114">.NET Core 2.1</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

<span data-ttu-id="ea8bb-115">如需下載連結和詳細資訊，請參閱 [NET 下載](https://dotnet.microsoft.com/download)以下載最新版本或 [.NET 下載封存](https://dotnet.microsoft.com/download/archives#dotnet-core) (針對舊版本)。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-115">For download links and more information, see [.NET downloads](https://dotnet.microsoft.com/download) to download the latest version or [.NET downloads archive](https://dotnet.microsoft.com/download/archives#dotnet-core) for older versions.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="ea8bb-116">.NET Core 的相依性</span><span class="sxs-lookup"><span data-stu-id="ea8bb-116">.NET Core dependencies</span></span>

<span data-ttu-id="ea8bb-117">必須手動安裝 [Microsoft Visual C++ 2015 可轉散發套件 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) 的時機：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-117">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="ea8bb-118">使用[安裝程式指令碼](./tools/dotnet-install-script.md)安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-118">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="ea8bb-119">部署獨立的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-119">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="ea8bb-120">從來源建置產品。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-120">Building the product from source.</span></span>
* <span data-ttu-id="ea8bb-121">透過 *.zip* 檔案安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-121">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="ea8bb-122">這可以包含組建/CI/CD 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-122">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="ea8bb-123">**適用於 Windows 8.1 和更早版本，或 Windows Server 2012 R2 和更早版本：**</span><span class="sxs-lookup"><span data-stu-id="ea8bb-123">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="ea8bb-124">請確定您的 Windows 安裝處於最新狀態，且包含 [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows) \(機器翻譯\) (可透過 Windows Update 安裝)。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-124">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="ea8bb-125">如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="ea8bb-125">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="ea8bb-126">**適用於 Windows 7 或 Windows Server 2008 R2：**</span><span class="sxs-lookup"><span data-stu-id="ea8bb-126">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="ea8bb-127">除了 KB2999226，請確定您也已經安裝 [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-127">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="ea8bb-128">如果沒有安裝此更新，當您啟動 .NET Core 應用程式時，將會看到如下的錯誤：`The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-128">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a><span data-ttu-id="ea8bb-129">使用 Visual Studio 開發 .NET Core 應用程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="ea8bb-129">Prerequisites to develop .NET Core apps with Visual Studio</span></span>
    
<span data-ttu-id="ea8bb-130">雖然您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式，但 Visual Studio 2017 和更新版本為 Windows 上的 .NET Core 應用程式提供整合式開發環境。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-130">Even though you can use any editor to develop .NET Core applications using the .NET Core SDK, Visual Studio 2017 and later versions provide an integrated development environment for .NET Core apps on Windows.</span></span>

<a name="vs-mapping"></a>

<span data-ttu-id="ea8bb-131">每個 .NET Core 版本都具有所需 Visual Studio 的最低版本。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-131">Each .NET Core version has a minimum version of Visual Studio required.</span></span> <span data-ttu-id="ea8bb-132">確認 Visual Studio 版本：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-132">To verify your Visual Studio version:</span></span>

* <span data-ttu-id="ea8bb-133">在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]** 。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-133">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
* <span data-ttu-id="ea8bb-134">在 [關於 Microsoft Visual Studio] 對話方塊中，確認版本號碼。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-134">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>

<span data-ttu-id="ea8bb-135">下表列出每個 SDK 的最低版本：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-135">The following table lists the minimum version for each SDK:</span></span>

| <span data-ttu-id="ea8bb-136">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="ea8bb-136">.NET Core SDK version</span></span> | <span data-ttu-id="ea8bb-137">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="ea8bb-137">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="ea8bb-138">3.0</span><span class="sxs-lookup"><span data-stu-id="ea8bb-138">3.0</span></span>                   | <span data-ttu-id="ea8bb-139">Visual Studio 2019 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-139">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="ea8bb-140">2.2</span><span class="sxs-lookup"><span data-stu-id="ea8bb-140">2.2</span></span>                   | <span data-ttu-id="ea8bb-141">Visual Studio 2017 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-141">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="ea8bb-142">2.1</span><span class="sxs-lookup"><span data-stu-id="ea8bb-142">2.1</span></span>                   | <span data-ttu-id="ea8bb-143">Visual Studio 2017 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-143">Visual Studio 2017 version 15.7 or higher.</span></span> |
| <span data-ttu-id="ea8bb-144">1.x</span><span class="sxs-lookup"><span data-stu-id="ea8bb-144">1.x</span></span>                   | <span data-ttu-id="ea8bb-145">Visual Studio 2017 15.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-145">Visual Studio 2017 version 15.0 or higher.</span></span> |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="ea8bb-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ea8bb-146">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="ea8bb-147">若要使用 .NET Core 3.0 SDK 在 Visual Studio 2019 中開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-147">To develop .NET Core apps in Visual Studio 2019 using the .NET Core 3.0 SDK:</span></span>

* <span data-ttu-id="ea8bb-148">[下載並安裝 Visual Studio 2019 16.3 版或更新版本](/visualstudio/install/install-visual-studio)，並根據您所建立的應用程式類型，選取包含 .NET Core SDK 的下列其中一個工作負載：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-148">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) and select one of the following workloads that includes the .NET Core SDK, depending on the kind of application you're building:</span></span>

  * <span data-ttu-id="ea8bb-149">[**其他工具**組] 區段中的 [ **.net Core 跨平臺開發**] 工作負載。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-149">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
  * <span data-ttu-id="ea8bb-150">**Web & 雲端**一節中的**ASP.NET 和 網頁程式開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-150">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
  * <span data-ttu-id="ea8bb-151">**Windows**區段中的**NET desktop 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-151">The **NET desktop development** workload in the **Windows** section.</span></span>

<span data-ttu-id="ea8bb-152">下圖顯示在 [Visual Studio] UI 中選取的 [ **.Net Core 跨平臺開發**] 工作負載：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-152">The following image shows the **.NET Core cross-platform development** workload selected in the Visual Studio UI:</span></span>

![已選取 [.NET Core 跨平臺開發] 工作負載的 Visual Studio 2019 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-2019-workloads.jpg)

<span data-ttu-id="ea8bb-154">Visual Studio 2019 16.3 在安裝任何這些工作負載之後，預設會使用 .NET Core 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-154">Visual Studio 2019 16.3 uses .NET Core 3.0 SDK by default after any of these workloads are installed.</span></span>

<span data-ttu-id="ea8bb-155">如果您想要讓現有的專案使用最新的 .NET Core 執行時間，請使用下列指示，將每個現有的 .NET Core 專案的目標重定為 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-155">If you want your existing projects to use the latest .NET Core runtime, retarget each existing .NET Core project to .NET Core 3.0 using the following instructions:</span></span>

* <span data-ttu-id="ea8bb-156">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-156">On the **Project** menu, choose **Properties**.</span></span>
* <span data-ttu-id="ea8bb-157">在 [**目標 framework** ] 選取功能表中，將值設定為 [ **.net Core 3.0**]。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-157">In the **Target framework** selection menu, set the value to **.NET Core 3.0**.</span></span>

![已選取 ".NET Core 3.0" 目標 framework 功能表項目的 Visual Studio 2019 應用程式專案屬性的螢幕擷取畫面](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

<span data-ttu-id="ea8bb-159">當您使用 .NET Core 3.0 SDK 設定 Visual Studio 之後，就可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-159">Once you have Visual Studio configured with .NET Core 3.0 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="ea8bb-160">開啟、建置及執行現有的 .NET Core 1.x 和 2.x 專案。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-160">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="ea8bb-161">將 .NET Core 1.x 和2.x 專案的目標重定為 .NET Core 3.0、組建和執行。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-161">Retarget .NET Core 1.x and 2.x projects to .NET Core 3.0, build, and run.</span></span>
* <span data-ttu-id="ea8bb-162">建立新的 .NET Core 3.0 專案。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-162">Create new .NET Core 3.0 projects.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ea8bb-163">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ea8bb-163">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="ea8bb-164">若要在 Visual Studio 2017 中開發使用 .NET Core 2.2 SDK 的 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-164">To develop .NET Core apps in Visual Studio 2017 using the .NET Core 2.2 SDK:</span></span>

* <span data-ttu-id="ea8bb-165">使用已選取的 **.Net Core 跨平臺開發**工作負載（在 [**其他工具**組] 區段），[下載並安裝 Visual Studio 2019 16.3 版或更新版本](/visualstudio/install/install-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-165">[Download and install Visual Studio 2019 version 16.3 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
* <span data-ttu-id="ea8bb-166">[下載並安裝 Visual Studio 2017 15.9.0 版本或更新版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-166">[Download and install Visual Studio 2017 version 15.9.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-2017-workloads.jpg)

<span data-ttu-id="ea8bb-168">安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 通常會安裝舊版的 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-168">After the **.NET Core cross-platform development** toolset is installed, Visual Studio usually installs a previous version of the .NET Core SDK.</span></span>
<span data-ttu-id="ea8bb-169">例如，安裝工作負載之後，Visual Studio 2017 15.9 預設會使用 .NET Core 2.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-169">For example, Visual Studio 2017 15.9 uses .NET Core 2.1 SDK by default after the workload is installed.</span></span>

<span data-ttu-id="ea8bb-170">若要更新 Visual Studio 以使用 .NET Core 2.2 SDK：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-170">To update Visual Studio to use .NET Core 2.2 SDK:</span></span>

 1. <span data-ttu-id="ea8bb-171">安裝 [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-171">Install the [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download).</span></span>

 1. <span data-ttu-id="ea8bb-172">如果您想要讓專案使用最新的 .NET Core 執行時間，請使用下列指示，將每個現有或新的 .NET Core 專案的目標重定為 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-172">If you want your project to use the latest .NET Core runtime, retarget each existing or new .NET Core project to .NET Core 2.2 using the following instructions:</span></span>

    * <span data-ttu-id="ea8bb-173">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-173">On the **Project** menu, choose **Properties**.</span></span>
    * <span data-ttu-id="ea8bb-174">在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.2**。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-174">In the **Target framework** selection menu, set the value to **.NET Core 2.2**.</span></span>

![螢幕擷取畫面：選取 ".NET Core 2.2" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/targeting-dotnet-core.jpg)

<span data-ttu-id="ea8bb-176">一旦使用 .NET Core 2.2 SDK 設定 Visual Studio，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ea8bb-176">Once you have Visual Studio configured with .NET Core 2.2 SDK, you can do the following actions:</span></span>

* <span data-ttu-id="ea8bb-177">開啟、建置及執行現有的 .NET Core 1.x 和 2.x 專案。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-177">Open, build, and run existing .NET Core 1.x and 2.x projects.</span></span>
* <span data-ttu-id="ea8bb-178">將 .NET Core 1.x 和 2.x 專案目標重新設定為 .NET Core 2.2、建置和執行。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-178">Retarget .NET Core 1.x and 2.x projects to .NET Core 2.2, build, and run.</span></span>
* <span data-ttu-id="ea8bb-179">建立新的 .NET Core 2.2 專案。</span><span class="sxs-lookup"><span data-stu-id="ea8bb-179">Create new .NET Core 2.2 projects.</span></span>

---
