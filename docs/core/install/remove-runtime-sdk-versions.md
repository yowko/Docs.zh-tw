---
title: 移除 .NET Core 執行階段和 SDK
description: 本文說明如何判斷目前所安裝的 .NET Core 執行階段和 SDK 版本，然後如何在 Windows、Mac 及 Linux 上移除它們。
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f1482c243ba22fa81c69ede847a0f6b36a9cb83c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595780"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="72cef-103">如何移除 .NET Core 執行階段和 SDK</span><span class="sxs-lookup"><span data-stu-id="72cef-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="72cef-104">隨時間下來，當您安裝 .NET Core 執行階段和 SDK 的更新版本時，您可能想要從電腦移除過期的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="72cef-105">移除舊版執行階段可能會變更選為執行共用架構應用程式的執行階段，如 [.NET Core 版本選取](../versions/selection.md)一文所述。</span><span class="sxs-lookup"><span data-stu-id="72cef-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](../versions/selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="72cef-106">我是否應該移除某個版本？</span><span class="sxs-lookup"><span data-stu-id="72cef-106">Should I remove a version?</span></span>

<span data-ttu-id="72cef-107">[.NET Core 版本選取](../versions/selection.md)行為及不同更新之間的 .NET Core 執行階段相容性，可讓您安全地移除舊版。</span><span class="sxs-lookup"><span data-stu-id="72cef-107">The [.NET Core version selection](../versions/selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="72cef-108">.NET Core 執行階段更新在主要版本「範圍」內 (例如 1.x 和 2.x) 是相容的。</span><span class="sxs-lookup"><span data-stu-id="72cef-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="72cef-109">此外，較新版本的 .NET Core SDK 通常能夠繼續以相容的方式，來建置以舊版執行階段為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="72cef-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="72cef-110">一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="72cef-111">您可能想要保留舊版 SDK 或執行階段版本的實例，包括維護以*json*為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="72cef-111">Instances where you might want to keep older SDK or runtime versions include maintaining *project.json*-based applications.</span></span> <span data-ttu-id="72cef-112">除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。</span><span class="sxs-lookup"><span data-stu-id="72cef-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="72cef-113">判斷已安裝的項目</span><span class="sxs-lookup"><span data-stu-id="72cef-113">Determine what is installed</span></span>

<span data-ttu-id="72cef-114">從 .NET Core 2.1 開始，.NET CLI 可讓您選擇使用電腦上安裝的 SDK 和執行階段版本清單。</span><span class="sxs-lookup"><span data-stu-id="72cef-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="72cef-115">使用[`dotnet --list-sdks`](../tools/dotnet.md#options)查看電腦上安裝的 sdk 清單。</span><span class="sxs-lookup"><span data-stu-id="72cef-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="72cef-116">使用[`dotnet --list-runtimes`](../tools/dotnet.md#options)查看電腦上安裝的執行時間清單。</span><span class="sxs-lookup"><span data-stu-id="72cef-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="72cef-117">如需詳細資訊，請參閱[如何檢查是否已安裝 .Net Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="72cef-117">For more information, see [How to check that .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>

## <a name="uninstall-net-core"></a><span data-ttu-id="72cef-118">卸載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="72cef-118">Uninstall .NET Core</span></span>

::: zone pivot="os-windows"

<span data-ttu-id="72cef-119">.NET Core 使用 Windows**應用程式 & 功能**] 對話方塊來移除 .net Core 執行時間和 SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-119">.NET Core uses the Windows **Apps & features** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="72cef-120">下圖顯示 [**應用程式 & 功能**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="72cef-120">The following figure shows the **Apps & features** dialog.</span></span> <span data-ttu-id="72cef-121">您可以搜尋**core sdk**來篩選並顯示已安裝的 .net core 版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-121">You can search for **core sdk** to filter and show installed versions of .NET Core.</span></span>

![用以移除 .NET Core 的 [新增/移除程式]](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="72cef-123">選取您想要從電腦移除的任意版本，然後按一下 [解除安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72cef-123">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

::: zone-end

::: zone pivot="os-linux"

<span data-ttu-id="72cef-124">在 Linux 上解除安裝 .NET Core (SDK 或執行階段) 有更多選項。</span><span class="sxs-lookup"><span data-stu-id="72cef-124">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="72cef-125">解除安裝 .NET Core 的最佳方式是對照您用來安裝 .NET Core 的動作。</span><span class="sxs-lookup"><span data-stu-id="72cef-125">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="72cef-126">細節會依您選擇的版本和安裝方法而異。</span><span class="sxs-lookup"><span data-stu-id="72cef-126">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72cef-127">針對 Red Hat 安裝，請參閱 [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) (Red Hat 入門指南)，取得安裝和解除安裝 .NET Core 的資訊。</span><span class="sxs-lookup"><span data-stu-id="72cef-127">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="72cef-128">從 .NET Core 2.1 開始，使用套件管理員進行升級時，不需要卸載 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="72cef-128">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="72cef-129">套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-129">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="72cef-130">如果您使用套件管理員來安裝 .NET Core，您可以使用該相同的套件管理員來解除安裝 .NET SDK 或執行階段。</span><span class="sxs-lookup"><span data-stu-id="72cef-130">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="72cef-131">.NET Core 安裝支援最熱門的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="72cef-131">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="72cef-132">如需您環境中的確切語法，請參閱散發套件管理員的檔：</span><span class="sxs-lookup"><span data-stu-id="72cef-132">Consult the documentation for your distribution's package manager for the precise syntax in your environment:</span></span>

- <span data-ttu-id="72cef-133">[apt-get(8)](https://linux.die.net/man/8/apt-get) 適用於 Debian 型系統，包括 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="72cef-133">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="72cef-134">[yum(8)](https://linux.die.net/man/8/yum) 適用於 Fedora、CentOS 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="72cef-134">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="72cef-135">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 適用於 openSUSE 和 SUSE Linux Enterprise System (SLES)。</span><span class="sxs-lookup"><span data-stu-id="72cef-135">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="72cef-136">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) 適用於 Fedora。</span><span class="sxs-lookup"><span data-stu-id="72cef-136">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="72cef-137">在絕大多數的情況下，移除套件的命令是 `remove`。</span><span class="sxs-lookup"><span data-stu-id="72cef-137">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="72cef-138">對於大多數套件管理員，.NET Core SDK 安裝的套件名稱是 `dotnet-sdk`，後面接著版本號碼。</span><span class="sxs-lookup"><span data-stu-id="72cef-138">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="72cef-139">從 .NET Core SDK 2.1.300 版和執行階段 `2.1` 版開始，只需要主要和次要版本號碼：例如，.NET Core SDK 2.1.300 版可用套件 `dotnet-sdk-2.1` 參考。</span><span class="sxs-lookup"><span data-stu-id="72cef-139">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="72cef-140">舊版需要整個版本字串：例如，.NET Core SDK 2.1.200 版需要 `dotnet-sdk-2.1.200`。</span><span class="sxs-lookup"><span data-stu-id="72cef-140">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="72cef-141">針對只安裝執行階段但未安裝 SDK 的電腦，套件名稱是 `dotnet-runtime-<version>` (適用於 .NET Core 執行階段) 和 `aspnetcore-runtime-<version>` (適用於整個執行階段堆疊)。</span><span class="sxs-lookup"><span data-stu-id="72cef-141">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="72cef-142">早于2.0 的 .NET Core 安裝在使用套件管理員卸載 SDK 時，並未卸載主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="72cef-142">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="72cef-143">請使用 `apt-get`，命令如下：</span><span class="sxs-lookup"><span data-stu-id="72cef-143">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="72cef-144">請注意，沒有附加至`dotnet-host`的版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-144">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="72cef-145">如果您使用 tarball 安裝，則必須使用手動方法移除 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="72cef-145">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="72cef-146">在 Linux 上，您必須移除已建立版本的目錄，分別移除 Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="72cef-146">On Linux, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="72cef-147">移除它們會從磁片中刪除 SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="72cef-147">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="72cef-148">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="72cef-148">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="72cef-149">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="72cef-149">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="72cef-150">在 Mac 上，您必須移除已建立版本的目錄，分別移除 Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="72cef-150">On Mac, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="72cef-151">移除它們會從磁片中刪除 SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="72cef-151">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="72cef-152">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="72cef-152">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="72cef-153">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="72cef-153">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="72cef-154">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="72cef-154">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="72cef-155">[.Net core 卸載工具](../additional-tools/uninstall-tool.md)（`dotnet-core-uninstall`）可讓您從系統中移除 .net Core sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="72cef-155">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="72cef-156">有一組選項可用來指定應該卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-156">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="72cef-157">Visual Studio .NET Core SDK 版本的相依性</span><span class="sxs-lookup"><span data-stu-id="72cef-157">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="72cef-158">在 Visual Studio 2019 16.3 版之前，Visual Studio 安裝程式，稱為獨立 .NET Core SDK 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="72cef-158">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="72cef-159">因此，SDK 版本會顯示在 [Windows**應用程式 & 功能**] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="72cef-159">As a result, the SDK versions appear in the Windows **Apps & features** dialog.</span></span> <span data-ttu-id="72cef-160">移除 Visual Studio 使用獨立安裝程式所安裝的 .NET Core Sdk 可能會中斷 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="72cef-160">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="72cef-161">如果 Visual Studio 在卸載 Sdk 之後發生問題，請在該特定版本的 Visual Studio 上執行 [修復]。</span><span class="sxs-lookup"><span data-stu-id="72cef-161">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="72cef-162">下表顯示 .NET Core SDK 版本的部分 Visual Studio 相依性：</span><span class="sxs-lookup"><span data-stu-id="72cef-162">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="72cef-163">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="72cef-163">Visual Studio version</span></span>           | <span data-ttu-id="72cef-164">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="72cef-164">.NET Core SDK version</span></span>          |
|---------------------------------|--------------------------------|
| <span data-ttu-id="72cef-165">Visual Studio 2019 16.2 版</span><span class="sxs-lookup"><span data-stu-id="72cef-165">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="72cef-166">.NET Core SDK 2.2.4 xx，2.1.8 xx</span><span class="sxs-lookup"><span data-stu-id="72cef-166">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="72cef-167">Visual Studio 2019 16.1 版</span><span class="sxs-lookup"><span data-stu-id="72cef-167">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="72cef-168">.NET Core SDK 2.2.3 xx，2.1.7 xx</span><span class="sxs-lookup"><span data-stu-id="72cef-168">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="72cef-169">Visual Studio 2019 16.0 版</span><span class="sxs-lookup"><span data-stu-id="72cef-169">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="72cef-170">.NET Core SDK 2.2.2 xx，2.1.6 xx</span><span class="sxs-lookup"><span data-stu-id="72cef-170">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="72cef-171">Visual Studio 2017 15.9 版</span><span class="sxs-lookup"><span data-stu-id="72cef-171">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="72cef-172">.NET Core SDK 2.2.1 xx，2.1.5 xx</span><span class="sxs-lookup"><span data-stu-id="72cef-172">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="72cef-173">Visual Studio 2017 15.8 版</span><span class="sxs-lookup"><span data-stu-id="72cef-173">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="72cef-174">.NET Core SDK 2.1.4 xx</span><span class="sxs-lookup"><span data-stu-id="72cef-174">.NET Core SDK 2.1.4xx</span></span>          |

<span data-ttu-id="72cef-175">從 Visual Studio 2019 16.3 版開始，Visual Studio 會負責自己的 .NET Core SDK 複本。</span><span class="sxs-lookup"><span data-stu-id="72cef-175">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="72cef-176">基於這個理由，您不會再于 [**應用程式 & 功能**] 對話方塊中看到這些 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-176">For that reason, you no longer see those SDK versions in the **Apps & features** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="72cef-177">移除 NuGet fallback 資料夾</span><span class="sxs-lookup"><span data-stu-id="72cef-177">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="72cef-178">在 .NET Core 3.0 SDK 之前，.NET Core SDK 安裝程式會使用名為*NuGetFallbackFolder*的資料夾來儲存 NuGet 套件的快取。</span><span class="sxs-lookup"><span data-stu-id="72cef-178">Before .NET Core 3.0 SDK, the .NET Core SDK installers used a folder named *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="72cef-179">此快取是在作業期間使用`dotnet restore` ， `dotnet build /t:Restore`例如或。</span><span class="sxs-lookup"><span data-stu-id="72cef-179">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="72cef-180">*NuGetFallbackFolder*位於 Windows 上的*C:\Program Files\dotnet\sdk*和 macOS 上的 */usr/local/share/dotnet/sdk* 。</span><span class="sxs-lookup"><span data-stu-id="72cef-180">The *NuGetFallbackFolder* is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="72cef-181">如果有下列情況，您可能會想要移除此資料夾：</span><span class="sxs-lookup"><span data-stu-id="72cef-181">You may want to remove this folder, if:</span></span>

- <span data-ttu-id="72cef-182">您只是使用 .NET Core 3.0 SDK 或更新版本進行開發。</span><span class="sxs-lookup"><span data-stu-id="72cef-182">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
- <span data-ttu-id="72cef-183">您正在使用3.0 之前的 .NET Core SDK 版本進行開發，但您可以在線上工作。</span><span class="sxs-lookup"><span data-stu-id="72cef-183">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online.</span></span>

<span data-ttu-id="72cef-184">如果您想要移除 NuGet fallback 資料夾，可以將它刪除，但是您需要系統管理員許可權才能執行此動作。</span><span class="sxs-lookup"><span data-stu-id="72cef-184">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="72cef-185">不建議刪除*dotnet*資料夾。</span><span class="sxs-lookup"><span data-stu-id="72cef-185">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="72cef-186">這麼做會移除您先前安裝的任何通用工具。</span><span class="sxs-lookup"><span data-stu-id="72cef-186">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="72cef-187">此外，在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="72cef-187">Also, on Windows:</span></span>

- <span data-ttu-id="72cef-188">您將會中斷 Visual Studio 2019 16.3 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="72cef-188">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="72cef-189">您可以執行**Repair**來復原。</span><span class="sxs-lookup"><span data-stu-id="72cef-189">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="72cef-190">如果 [**應用程式 & 功能**] 對話方塊中有 .NET Core SDK 專案，則它們會是孤立的。</span><span class="sxs-lookup"><span data-stu-id="72cef-190">If there are .NET Core SDK entries in the **Apps & features** dialog, they'll be orphaned.</span></span>
