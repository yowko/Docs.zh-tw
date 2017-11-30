---
title: "Windows 上 .NET Core 的必要條件"
description: "了解在 Windows 電腦上開發及執行 .NET Core 應用程式時，您需要哪些相依性。"
author: JRAlexander
ms.author: johalex
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 16a72edde39e4857dbdfb400f195deb9975f993c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="16629-103">Windows 上 .NET Core 的必要條件</span><span class="sxs-lookup"><span data-stu-id="16629-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="16629-104">本文會說明在 Windows 開發 .NET Core 應用程式所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="16629-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="16629-105">支援的作業系統版本和跟隨的相依性，適用於在 Windows 開發 .NET Core 應用程式的三種方式：</span><span class="sxs-lookup"><span data-stu-id="16629-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="16629-106">命令列</span><span class="sxs-lookup"><span data-stu-id="16629-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="16629-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="16629-107">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* [<span data-ttu-id="16629-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16629-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="16629-109">.NET Core 支援的 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="16629-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="16629-110">下列版本支援 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="16629-110">.NET Core is supported on the following versions of :</span></span>

* <span data-ttu-id="16629-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="16629-111">Windows 7 SP1</span></span>
* <span data-ttu-id="16629-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="16629-112">Windows 8.1</span></span>
* <span data-ttu-id="16629-113">Windows 10、Windows 10 年度更新 (1607 版) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="16629-113">Windows 10, Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="16629-114">Windows Server 2008 R2 SP1 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="16629-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="16629-115">Windows Server 2012 SP1 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="16629-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="16629-116">Windows Server 2012 R2 (完整伺服器或 Server Core)</span><span class="sxs-lookup"><span data-stu-id="16629-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="16629-117">Windows Server 2016 (完整伺服器、Server Core 或 Nano Server)</span><span class="sxs-lookup"><span data-stu-id="16629-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="16629-118">如需 .NET Core 2.x 支援的作業系統完整清單，請參閱 [.NET Core 2.x - 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="16629-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="16629-119">如需 .NET Core 1.x 支援的作業系統完整清單，請參閱 [.NET Core 1.x 支援的作業系統版本](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="16629-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="16629-120">.NET Core 的相依性</span><span class="sxs-lookup"><span data-stu-id="16629-120">.NET Core dependencies</span></span>

<span data-ttu-id="16629-121">早於 Windows 10 和 Windows Server 2016 的 Windows 版本上執行時，.NET core 1.1 及更早版本需要 Visual c + + 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="16629-121">.NET Core 1.1 and earlier requires the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="16629-122">.NET Core 安裝程式會自動安裝此相依性。</span><span class="sxs-lookup"><span data-stu-id="16629-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="16629-123">必須手動安裝 [Microsoft Visual C++ 2015 可轉散發套件 Update 3](https://www.microsoft.com/download/details.aspx?id=52685) 的時機：</span><span class="sxs-lookup"><span data-stu-id="16629-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

   * <span data-ttu-id="16629-124">使用[安裝程式指令碼](./tools/dotnet-install-script.md)安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="16629-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
   * <span data-ttu-id="16629-125">部署獨立的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="16629-125">Deploying a self-contained .NET Core application.</span></span>

> [!NOTE]
> <span data-ttu-id="16629-126"><em>僅適用於 Windows 7 和 Windows Server 2008 電腦：</em></span><span class="sxs-lookup"><span data-stu-id="16629-126"><em>For Windows 7 and Windows Server 2008 machines only:</em></span></span><br>
> <span data-ttu-id="16629-127">確定您的 Windows 安裝為最新狀態，而且包含已透過 Windows Update 安裝的 Hotfix [KB2533623](https://support.microsoft.com/help/2533623)。</span><span class="sxs-lookup"><span data-stu-id="16629-127">Make sure that your Windows installation is up-to-date and includes hotfix [KB2533623](https://support.microsoft.com/help/2533623) installed through Windows Update.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="16629-128">使用 Visual Studio 2017 的必要條件</span><span class="sxs-lookup"><span data-stu-id="16629-128">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="16629-129">您可以使用任何編輯器來開發使用 .NET Core SDK 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="16629-129">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span>  <span data-ttu-id="16629-130">[Visual Studio 2017](#visual-studio-2017) 為 Windows 上的 .NET Core 應用程式提供整合式開發環境。</span><span class="sxs-lookup"><span data-stu-id="16629-130">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="16629-131">您可以在[版本資訊](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)中，進一步了解 Visual Studio 2017 的變更。</span><span class="sxs-lookup"><span data-stu-id="16629-131">You can read more about the changes in Visual Studio 2017 in the [release notes](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span></span>
# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="16629-132">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="16629-132">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="16629-133">若要在 Visual Studio 2017 中開發 .NET Core 2.x 應用程式：</span><span class="sxs-lookup"><span data-stu-id="16629-133">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="16629-134">[下載並安裝 Visual Studio 2017 15.3.0 版本或更高版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。</span><span class="sxs-lookup"><span data-stu-id="16629-134">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="16629-135">![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="16629-135">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span></span>

<span data-ttu-id="16629-136">安裝 **.NET Core 跨平台開發**工具集之後，Visual Studio 2017 預設使用 .NET Core 1.x。</span><span class="sxs-lookup"><span data-stu-id="16629-136">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="16629-137">安裝 .NET Core 2.x SDK 以取得 Visual Studio 2017 中的 .NET Core 2.x 支援。</span><span class="sxs-lookup"><span data-stu-id="16629-137">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="16629-138">安裝 [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core)。</span><span class="sxs-lookup"><span data-stu-id="16629-138">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="16629-139">使用下列指示將現有或新的 .NET Core 1.x 專案目標重定到 .NET Core 2.x：</span><span class="sxs-lookup"><span data-stu-id="16629-139">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="16629-140">在 [專案] 功能表上，選擇 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="16629-140">On the **Project** menu, Choose **Properties**.</span></span> 
    * <span data-ttu-id="16629-141">在 [目標 Framework] 選取功能表中，將值設為 **.NET Core 2.0**。</span><span class="sxs-lookup"><span data-stu-id="16629-141">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![螢幕擷取畫面：選取 ".NET Core 2.0" 目標 Framework 功能表項目的 Visual Studio 2017 應用程式專案屬性](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="16629-143">一旦安裝 .NET Core 2.x SDK，Visual Studio 2017 預設會使用 .NET Core SDK 2.x，而且支援下列動作：</span><span class="sxs-lookup"><span data-stu-id="16629-143">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

  * <span data-ttu-id="16629-144">開啟、建置及執行現有的 .NET Core 1.x 專案。</span><span class="sxs-lookup"><span data-stu-id="16629-144">Open, build, and run existing .NET Core 1.x projects.</span></span>
  * <span data-ttu-id="16629-145">將 .NET Core 1.x 專案重定目標至 .NET Core 2.x、建置和執行。</span><span class="sxs-lookup"><span data-stu-id="16629-145">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
  * <span data-ttu-id="16629-146">建立新的 .NET Core 2.x 專案。</span><span class="sxs-lookup"><span data-stu-id="16629-146">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="16629-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="16629-147">.NET Core 1.x</span></span>](#tab/netcore1x)
<span data-ttu-id="16629-148">若要使用 Visual Studio 開發 .NET Core 1.x 應用程式，請[下載並安裝 Visual Studio 2017 RTM (版本 15.0.26228.4) 或更高版本](/visualstudio/install/install-visual-studio)，選取 [.NET Core 跨平台開發] 工作負載 (在 [其他工具組] 區段)。</span><span class="sxs-lookup"><span data-stu-id="16629-148">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="16629-149">![已選取 [.NET Core 跨平台開發] 工作負載的 Visual Studio 2017 安裝螢幕擷取畫面](./media/windows-prerequisites/vs_workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="16629-149">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs_workloads.jpg)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="16629-150">有可能使用 Visual Studio 2015 開發 .NET Core 1.x，但不建議為下列原因而如此做：</span><span class="sxs-lookup"><span data-stu-id="16629-150">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="16629-151">.NET Core 工具是預覽版本，不受支援。</span><span class="sxs-lookup"><span data-stu-id="16629-151">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="16629-152">專案是以 project.json 為基礎，已被取代。</span><span class="sxs-lookup"><span data-stu-id="16629-152">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="16629-153">如需專案格式變更的詳細資訊，請參閱[變更的高階概觀](./tools/cli-msbuild-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="16629-153">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

>[!TIP]
  > <span data-ttu-id="16629-154">確認 Visual Studio 2017 版本：</span><span class="sxs-lookup"><span data-stu-id="16629-154">To verify your Visual Studio 2017 version:</span></span>
>
     > * <span data-ttu-id="16629-155">在 **[說明]** 功能表上，選擇 **[關於 Microsoft Visual Studio]**。</span><span class="sxs-lookup"><span data-stu-id="16629-155">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
     > * <span data-ttu-id="16629-156">在 [關於 Microsoft Visual Studio] 對話方塊中，確認版本號碼。</span><span class="sxs-lookup"><span data-stu-id="16629-156">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>     * <span data-ttu-id="16629-157">.NET Core 2.x 應用程式應為 Visual Studio 2017 版本 15.3 (26730.01) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="16629-157">For .NET Core 2.x apps, Visual Studio 2017 version 15.3 (26730.01) or higher.</span></span>
>     * <span data-ttu-id="16629-158">.NET Core 1.x 應用程式應為 Visual Studio 2017 版本 15.0 (26228.04) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="16629-158">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 (26228.04) or higher.</span></span>
