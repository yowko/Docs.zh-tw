---
title: 移除 .NET 執行時間和 SDK
description: 本文說明如何判斷目前已安裝的 .NET 執行時間和 SDK 版本，以及如何在 Windows、Mac 和 Linux 上移除它們。
author: adegeo
ms.author: adegeo
ms.date: 11/20/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: f07a9acdc5be310d38da18602dde2ebf678e9a1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031718"
---
# <a name="how-to-remove-the-net-runtime-and-sdk"></a><span data-ttu-id="be41c-103">如何移除 .NET 執行時間和 SDK</span><span class="sxs-lookup"><span data-stu-id="be41c-103">How to remove the .NET Runtime and SDK</span></span>

<span data-ttu-id="be41c-104">經過一段時間後，當您安裝 .NET 執行時間和 SDK 的更新版本時，您可能會想要從您的電腦移除過時的 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-104">Over time, as you install updated versions of the .NET runtime and SDK, you may want to remove outdated versions of .NET from your machine.</span></span> <span data-ttu-id="be41c-105">移除舊版執行時間可能會變更選擇執行共用 framework 應用程式的執行時間，如 [.net 版本選取](../versions/selection.md)專案中所述。</span><span class="sxs-lookup"><span data-stu-id="be41c-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET version selection](../versions/selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="be41c-106">我是否應該移除某個版本？</span><span class="sxs-lookup"><span data-stu-id="be41c-106">Should I remove a version?</span></span>

<span data-ttu-id="be41c-107">[.Net 版本的選取](../versions/selection.md)行為和 .net 之間的 .net 執行時間相容性，可讓您安全地移除先前的版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-107">The [.NET version selection](../versions/selection.md) behaviors and the runtime compatibility of .NET across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="be41c-108">.NET 執行時間更新在主要版本 **波段** （例如1.x 和2.x）中相容。</span><span class="sxs-lookup"><span data-stu-id="be41c-108">.NET runtime updates are compatible within a major version **band** such as 1.x and 2.x.</span></span> <span data-ttu-id="be41c-109">此外，較新版本的 .NET SDK 通常會維持能夠以相容的方式來建立以舊版執行時間為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="be41c-109">Additionally, newer releases of the .NET SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="be41c-110">一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="be41c-111">您可能想要保留舊版 SDK 或執行階段版本的實例，包括維護 *project.js的* 應用程式。</span><span class="sxs-lookup"><span data-stu-id="be41c-111">Instances where you might want to keep older SDK or runtime versions include maintaining *project.json*-based applications.</span></span> <span data-ttu-id="be41c-112">除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。</span><span class="sxs-lookup"><span data-stu-id="be41c-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="be41c-113">判斷已安裝的項目</span><span class="sxs-lookup"><span data-stu-id="be41c-113">Determine what is installed</span></span>

<span data-ttu-id="be41c-114">.NET CLI 有一些選項，可讓您用來列出電腦上安裝的 SDK 和執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-114">The .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="be41c-115">使用 [`dotnet --list-sdks`](../tools/dotnet.md#options) 以查看電腦上安裝的 sdk 清單。</span><span class="sxs-lookup"><span data-stu-id="be41c-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="be41c-116">使用 [`dotnet --list-runtimes`](../tools/dotnet.md#options) 以查看電腦上安裝的執行時間清單。</span><span class="sxs-lookup"><span data-stu-id="be41c-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="be41c-117">如需詳細資訊，請參閱 [如何檢查是否已安裝 .net](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="be41c-117">For more information, see [How to check that .NET is already installed](how-to-detect-installed-versions.md).</span></span>

## <a name="uninstall-net"></a><span data-ttu-id="be41c-118">卸載 .NET</span><span class="sxs-lookup"><span data-stu-id="be41c-118">Uninstall .NET</span></span>

::: zone pivot="os-windows"

<span data-ttu-id="be41c-119">.NET 會使用 Windows **應用程式 & 功能** ] 對話方塊來移除 .net 執行時間和 SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-119">.NET uses the Windows **Apps & features** dialog to remove versions of the .NET runtime and SDK.</span></span> <span data-ttu-id="be41c-120">下圖顯示 [ **應用程式 & 功能** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="be41c-120">The following figure shows the **Apps & features** dialog.</span></span> <span data-ttu-id="be41c-121">您可以搜尋 **核心 sdk** 或 **.net sdk** ，以篩選和顯示已安裝的 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-121">You can search for **core sdk** or **.net sdk** to filter and show installed versions of .NET.</span></span>

![新增/移除程式以移除 .NET](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="be41c-123">選取您想要從電腦移除的任意版本，然後按一下 [解除安裝]。</span><span class="sxs-lookup"><span data-stu-id="be41c-123">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

::: zone-end

::: zone pivot="os-linux"

<span data-ttu-id="be41c-124">有更多選項可將 .NET (SDK 或 Linux 上的執行時間) 卸載。</span><span class="sxs-lookup"><span data-stu-id="be41c-124">There are more options to uninstall .NET (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="be41c-125">卸載 .NET 的最佳方式是鏡像您用來安裝 .NET 的動作。</span><span class="sxs-lookup"><span data-stu-id="be41c-125">The best way for you to uninstall .NET is to mirror the action you used to install .NET.</span></span> <span data-ttu-id="be41c-126">細節會依您選擇的版本和安裝方法而異。</span><span class="sxs-lookup"><span data-stu-id="be41c-126">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="be41c-127">針對 Red Hat 安裝，請參閱 [.net 的 Red Hat 產品檔](https://access.redhat.com/documentation/en-us/net/5.0/)。</span><span class="sxs-lookup"><span data-stu-id="be41c-127">For Red Hat installations, consult the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/en-us/net/5.0/).</span></span>

<span data-ttu-id="be41c-128">除非您要從預覽版本升級，否則不需要在使用套件管理員升級 .NET SDK 時卸載 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="be41c-128">There's no need to uninstall the .NET SDK when upgrading it using a package manager, unless you're upgrading from a preview version.</span></span> <span data-ttu-id="be41c-129">套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-129">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span> <span data-ttu-id="be41c-130">如果您已安裝預覽版本，請將它卸載。</span><span class="sxs-lookup"><span data-stu-id="be41c-130">If you have a preview version installed, uninstall it.</span></span>

<span data-ttu-id="be41c-131">如果您使用套件管理員安裝 .NET，請使用相同的套件管理員來卸載 .NET SDK 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="be41c-131">If you installed .NET using a package manager, use that same package manager to uninstall the .NET SDK or runtime.</span></span> <span data-ttu-id="be41c-132">.NET 安裝支援最熱門的封裝管理員。</span><span class="sxs-lookup"><span data-stu-id="be41c-132">.NET installations support most popular package managers.</span></span> <span data-ttu-id="be41c-133">請參閱散發套件管理員的檔，以瞭解您環境中的精確語法：</span><span class="sxs-lookup"><span data-stu-id="be41c-133">Consult the documentation for your distribution's package manager for the precise syntax in your environment:</span></span>

- <span data-ttu-id="be41c-134">[apt-get(8)](https://linux.die.net/man/8/apt-get) 適用於 Debian 型系統，包括 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="be41c-134">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="be41c-135">[yum(8)](https://linux.die.net/man/8/yum) 適用於 Fedora、CentOS 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="be41c-135">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="be41c-136">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 適用於 openSUSE 和 SUSE Linux Enterprise System (SLES)。</span><span class="sxs-lookup"><span data-stu-id="be41c-136">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="be41c-137">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) 適用於 Fedora。</span><span class="sxs-lookup"><span data-stu-id="be41c-137">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="be41c-138">在絕大多數的情況下，移除套件的命令是 `remove`。</span><span class="sxs-lookup"><span data-stu-id="be41c-138">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="be41c-139">大部分套件管理員的 .NET SDK 安裝封裝名稱是 `dotnet-sdk` ，後面接著版本號碼。</span><span class="sxs-lookup"><span data-stu-id="be41c-139">The package name for the .NET SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="be41c-140">從 .NET SDK 的版本2.1.300 和執行時間的版本開始 `2.1` ，只需要主要和次要版本號碼：例如，您可以將 .NET SDK 版本2.1.300 參考為套件 `dotnet-sdk-2.1` 。</span><span class="sxs-lookup"><span data-stu-id="be41c-140">Starting with the version 2.1.300 of the .NET SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="be41c-141">先前的版本需要整個版本字串：例如， `dotnet-sdk-2.1.200` .NET SDK 的版本2.1.200 需要此版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-141">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET SDK.</span></span>

<span data-ttu-id="be41c-142">對於僅安裝執行時間（而不是 SDK）的電腦，套件名稱適用 `dotnet-runtime-<version>` 于 .net 執行時間和 `aspnetcore-runtime-<version>` 整個執行時間堆疊。</span><span class="sxs-lookup"><span data-stu-id="be41c-142">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

> [!TIP]
> <span data-ttu-id="be41c-143">使用套件管理員卸載 SDK 時，早于2.0 的 .NET Core 安裝不會卸載主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="be41c-143">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="be41c-144">請使用 `apt-get`，命令如下：</span><span class="sxs-lookup"><span data-stu-id="be41c-144">Using `apt-get`, the command is:</span></span>
>
> ```bash
> apt-get remove dotnet-host
> ```
>
> <span data-ttu-id="be41c-145">沒有任何版本附加至 `dotnet-host` 。</span><span class="sxs-lookup"><span data-stu-id="be41c-145">There's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="be41c-146">如果您使用 tarball 安裝，則必須使用手動方法來移除 .NET。</span><span class="sxs-lookup"><span data-stu-id="be41c-146">If you installed using a tarball, you must remove .NET using the manual method.</span></span>

<span data-ttu-id="be41c-147">在 Linux 上，您必須移除已建立版本的目錄，來個別移除 Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="be41c-147">On Linux, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="be41c-148">移除它們會從磁片刪除 SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="be41c-148">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="be41c-149">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="be41c-149">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="be41c-150">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="be41c-150">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="be41c-151">在 Mac 上，您必須移除已建立版本的目錄，來個別移除 Sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="be41c-151">On Mac, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="be41c-152">移除它們會從磁片刪除 SDK 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="be41c-152">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="be41c-153">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="be41c-153">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="be41c-154">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="be41c-154">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

## <a name="net-uninstall-tool"></a><span data-ttu-id="be41c-155">.NET 卸載工具</span><span class="sxs-lookup"><span data-stu-id="be41c-155">.NET Uninstall Tool</span></span>

<span data-ttu-id="be41c-156">[.Net 卸載工具](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) 可讓您從系統移除 .net sdk 和執行時間。</span><span class="sxs-lookup"><span data-stu-id="be41c-156">The [.NET Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET SDKs and runtimes from a system.</span></span> <span data-ttu-id="be41c-157">選項的集合可以用來指定應該卸載的版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-157">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="be41c-158">.NET Core SDK 版本的 Visual Studio 相依性</span><span class="sxs-lookup"><span data-stu-id="be41c-158">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="be41c-159">在 Visual Studio 2019 16.3 版之前，Visual Studio 安裝程式，稱為獨立 .NET Core SDK 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="be41c-159">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="be41c-160">因此，SDK 版本會出現在 [Windows **應用程式 & 功能** ] 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="be41c-160">As a result, the SDK versions appear in the Windows **Apps & features** dialog.</span></span> <span data-ttu-id="be41c-161">使用獨立安裝程式移除 Visual Studio 所安裝的 .NET Core Sdk 可能會中斷 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="be41c-161">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="be41c-162">如果 Visual Studio 在卸載 Sdk 之後遇到問題，請在該特定版本的 Visual Studio 上執行 Repair。</span><span class="sxs-lookup"><span data-stu-id="be41c-162">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="be41c-163">下表顯示 .NET Core SDK 版本的部分 Visual Studio 相依性：</span><span class="sxs-lookup"><span data-stu-id="be41c-163">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="be41c-164">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="be41c-164">Visual Studio version</span></span>           | <span data-ttu-id="be41c-165">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="be41c-165">.NET Core SDK version</span></span>          |
|---------------------------------|--------------------------------|
| <span data-ttu-id="be41c-166">Visual Studio 2019 16.2 版</span><span class="sxs-lookup"><span data-stu-id="be41c-166">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="be41c-167">.NET Core SDK 2.2.4 xx，2.1.8 xx</span><span class="sxs-lookup"><span data-stu-id="be41c-167">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="be41c-168">Visual Studio 2019 16.1 版</span><span class="sxs-lookup"><span data-stu-id="be41c-168">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="be41c-169">.NET Core SDK 2.2.3 xx，2.1.7 xx</span><span class="sxs-lookup"><span data-stu-id="be41c-169">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="be41c-170">Visual Studio 2019 16.0 版</span><span class="sxs-lookup"><span data-stu-id="be41c-170">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="be41c-171">.NET Core SDK 2.2.2 xx、2.1.6 xx</span><span class="sxs-lookup"><span data-stu-id="be41c-171">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="be41c-172">Visual Studio 2017 15.9 版</span><span class="sxs-lookup"><span data-stu-id="be41c-172">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="be41c-173">.NET Core SDK 2.2.1 xx，2.1.5 xx</span><span class="sxs-lookup"><span data-stu-id="be41c-173">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="be41c-174">Visual Studio 2017 15.8 版</span><span class="sxs-lookup"><span data-stu-id="be41c-174">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="be41c-175">.NET Core SDK 2.1.4 xx</span><span class="sxs-lookup"><span data-stu-id="be41c-175">.NET Core SDK 2.1.4xx</span></span>          |

<span data-ttu-id="be41c-176">從 Visual Studio 2019 16.3 版開始，Visual Studio 負責自己的 .NET SDK 複本。</span><span class="sxs-lookup"><span data-stu-id="be41c-176">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET SDK.</span></span> <span data-ttu-id="be41c-177">基於這個理由，您不會再于 [ **應用程式 & 功能** ] 對話方塊中看到這些 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-177">For that reason, you no longer see those SDK versions in the **Apps & features** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="be41c-178">移除 NuGet fallback 資料夾</span><span class="sxs-lookup"><span data-stu-id="be41c-178">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="be41c-179">在 .NET Core 3.0 SDK 之前，.NET Core SDK 安裝程式會使用名為 *NuGetFallbackFolder* 的資料夾來儲存 NuGet 套件的快取。</span><span class="sxs-lookup"><span data-stu-id="be41c-179">Before .NET Core 3.0 SDK, the .NET Core SDK installers used a folder named *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="be41c-180">此快取是在作業期間使用，例如 `dotnet restore` 或 `dotnet build /t:Restore` 。</span><span class="sxs-lookup"><span data-stu-id="be41c-180">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="be41c-181">*NuGetFallbackFolder* 位於 Windows 上的 *C:\Program Files\dotnet\sdk* 和 macOS 上的 */usr/local/share/dotnet/sdk* 。</span><span class="sxs-lookup"><span data-stu-id="be41c-181">The *NuGetFallbackFolder* is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="be41c-182">如果有下列情況，您可能會想要移除此資料夾：</span><span class="sxs-lookup"><span data-stu-id="be41c-182">You may want to remove this folder, if:</span></span>

- <span data-ttu-id="be41c-183">您只是使用 .NET Core 3.0 SDK 或 .NET 5.0 或更新版本進行開發。</span><span class="sxs-lookup"><span data-stu-id="be41c-183">You're only developing using .NET Core 3.0 SDK or .NET 5.0 or later versions.</span></span>
- <span data-ttu-id="be41c-184">您是使用早于3.0 的 .NET Core SDK 版本進行開發，但您可以在線上工作。</span><span class="sxs-lookup"><span data-stu-id="be41c-184">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online.</span></span>

<span data-ttu-id="be41c-185">如果您想要移除 NuGet 回溯資料夾，您可以將其刪除，但需要系統管理員許可權才能完成此動作。</span><span class="sxs-lookup"><span data-stu-id="be41c-185">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="be41c-186">不建議刪除 *dotnet* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="be41c-186">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="be41c-187">這麼做會移除先前安裝的所有通用工具。</span><span class="sxs-lookup"><span data-stu-id="be41c-187">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="be41c-188">此外，在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="be41c-188">Also, on Windows:</span></span>

- <span data-ttu-id="be41c-189">您將會中斷 Visual Studio 2019 16.3 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="be41c-189">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="be41c-190">您可以執行 **Repair** 來復原。</span><span class="sxs-lookup"><span data-stu-id="be41c-190">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="be41c-191">如果 [ **應用程式 & 功能** ] 對話方塊中有 .NET Core SDK 專案，它們會是孤立的。</span><span class="sxs-lookup"><span data-stu-id="be41c-191">If there are .NET Core SDK entries in the **Apps & features** dialog, they'll be orphaned.</span></span>
