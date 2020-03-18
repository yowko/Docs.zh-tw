---
title: 移除 .NET Core 執行階段和 SDK
description: 本文說明如何判斷目前所安裝的 .NET Core 執行階段和 SDK 版本，然後如何在 Windows、Mac 及 Linux 上移除它們。
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398836"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="74635-103">如何移除 .NET Core 執行階段和 SDK</span><span class="sxs-lookup"><span data-stu-id="74635-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="74635-104">隨時間下來，當您安裝 .NET Core 執行階段和 SDK 的更新版本時，您可能想要從電腦移除過期的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="74635-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="74635-105">移除舊版執行階段可能會變更選為執行共用架構應用程式的執行階段，如 [.NET Core 版本選取](selection.md)一文所述。</span><span class="sxs-lookup"><span data-stu-id="74635-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="74635-106">我是否應該移除某個版本？</span><span class="sxs-lookup"><span data-stu-id="74635-106">Should I remove a version?</span></span>

<span data-ttu-id="74635-107">[.NET Core 版本選取](selection.md)行為及不同更新之間的 .NET Core 執行階段相容性，可讓您安全地移除舊版。</span><span class="sxs-lookup"><span data-stu-id="74635-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="74635-108">.NET Core 執行階段更新在主要版本「範圍」內 (例如 1.x 和 2.x) 是相容的。</span><span class="sxs-lookup"><span data-stu-id="74635-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="74635-109">此外，較新版本的 .NET Core SDK 通常能夠繼續以相容的方式，來建置以舊版執行階段為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="74635-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="74635-110">一般而言，您只需要最新的 SDK，以及您應用程式所需之執行階段的最新修補版本。</span><span class="sxs-lookup"><span data-stu-id="74635-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="74635-111">保留較舊的 SDK 或執行階段版本的實例包括維護基於**project.json**的應用程式。</span><span class="sxs-lookup"><span data-stu-id="74635-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="74635-112">除非您的應用程式有特定理由需要舊版 SDK 或執行階段，否則您可以安全地移除舊版。</span><span class="sxs-lookup"><span data-stu-id="74635-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="74635-113">判斷已安裝的項目</span><span class="sxs-lookup"><span data-stu-id="74635-113">Determine what is installed</span></span>

<span data-ttu-id="74635-114">從 .NET Core 2.1 開始，.NET CLI 可讓您選擇使用電腦上安裝的 SDK 和執行階段版本清單。</span><span class="sxs-lookup"><span data-stu-id="74635-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="74635-115">用於[`dotnet --list-sdks`](../tools/dotnet.md#options)查看電腦上安裝的 SDK 清單。</span><span class="sxs-lookup"><span data-stu-id="74635-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="74635-116">用於[`dotnet --list-runtimes`](../tools/dotnet.md#options)查看電腦上安裝的運行時清單。</span><span class="sxs-lookup"><span data-stu-id="74635-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="74635-117">下列文字顯示 Windows、macOS 或 Linux 的一般輸出：</span><span class="sxs-lookup"><span data-stu-id="74635-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="74635-118">Windows</span><span class="sxs-lookup"><span data-stu-id="74635-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="74635-119">通過運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="74635-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="74635-120">您將獲得類似于以下內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="74635-120">You get output similar to the following:</span></span>

```console
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]
```

<span data-ttu-id="74635-121">通過運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="74635-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="74635-122">您將獲得類似于以下內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="74635-122">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linux"></a>[<span data-ttu-id="74635-123">Linux</span><span class="sxs-lookup"><span data-stu-id="74635-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="74635-124">通過運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="74635-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="74635-125">您將獲得類似于以下內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="74635-125">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

<span data-ttu-id="74635-126">通過運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="74635-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="74635-127">您將獲得類似于以下內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="74635-127">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macos"></a>[<span data-ttu-id="74635-128">macOS</span><span class="sxs-lookup"><span data-stu-id="74635-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="74635-129">通過運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="74635-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="74635-130">您將獲得類似于以下內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="74635-130">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

<span data-ttu-id="74635-131">通過運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="74635-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="74635-132">您將獲得類似于以下內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="74635-132">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstall-net-core"></a><span data-ttu-id="74635-133">卸載 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="74635-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="74635-134">Windows</span><span class="sxs-lookup"><span data-stu-id="74635-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="74635-135">.NET Core 使用 Windows [新增/移除程式]\*\*\*\* 對話方塊來移除 .NET Core 執行階段和 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="74635-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="74635-136">下圖顯示 [新增/移除程式]\*\*\*\* 對話方塊，其中已安裝數個 .NET 執行階段和 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="74635-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![用以移除 .NET Core 的 [新增/移除程式]](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="74635-138">選取您想要從電腦移除的任意版本，然後按一下 [解除安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="74635-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="74635-139">Linux</span><span class="sxs-lookup"><span data-stu-id="74635-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="74635-140">在 Linux 上解除安裝 .NET Core (SDK 或執行階段) 有更多選項。</span><span class="sxs-lookup"><span data-stu-id="74635-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="74635-141">解除安裝 .NET Core 的最佳方式是對照您用來安裝 .NET Core 的動作。</span><span class="sxs-lookup"><span data-stu-id="74635-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="74635-142">細節會依您選擇的版本和安裝方法而異。</span><span class="sxs-lookup"><span data-stu-id="74635-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74635-143">針對 Red Hat 安裝，請參閱 [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) (Red Hat 入門指南)，取得安裝和解除安裝 .NET Core 的資訊。</span><span class="sxs-lookup"><span data-stu-id="74635-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="74635-144">從 .NET Core 2.1 開始，使用包管理器升級 .NET Core SDK 時無需卸載它。</span><span class="sxs-lookup"><span data-stu-id="74635-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="74635-145">套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。</span><span class="sxs-lookup"><span data-stu-id="74635-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="74635-146">如果您使用套件管理員來安裝 .NET Core，您可以使用該相同的套件管理員來解除安裝 .NET SDK 或執行階段。</span><span class="sxs-lookup"><span data-stu-id="74635-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="74635-147">.NET Core 安裝支援最熱門的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="74635-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="74635-148">請參閱版本的套件管理員文件，了解環境的精確語法：</span><span class="sxs-lookup"><span data-stu-id="74635-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="74635-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) 適用於 Debian 型系統，包括 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="74635-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="74635-150">[yum(8)](https://linux.die.net/man/8/yum) 適用於 Fedora、CentOS 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="74635-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="74635-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 適用於 openSUSE 和 SUSE Linux Enterprise System (SLES)。</span><span class="sxs-lookup"><span data-stu-id="74635-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="74635-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) 適用於 Fedora。</span><span class="sxs-lookup"><span data-stu-id="74635-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="74635-153">在絕大多數的情況下，移除套件的命令是 `remove`。</span><span class="sxs-lookup"><span data-stu-id="74635-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="74635-154">對於大多數套件管理員，.NET Core SDK 安裝的套件名稱是 `dotnet-sdk`，後面接著版本號碼。</span><span class="sxs-lookup"><span data-stu-id="74635-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="74635-155">從 .NET Core SDK 2.1.300 版和執行階段 `2.1` 版開始，只需要主要和次要版本號碼：例如，.NET Core SDK 2.1.300 版可用套件 `dotnet-sdk-2.1` 參考。</span><span class="sxs-lookup"><span data-stu-id="74635-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="74635-156">舊版需要整個版本字串：例如，.NET Core SDK 2.1.200 版需要 `dotnet-sdk-2.1.200`。</span><span class="sxs-lookup"><span data-stu-id="74635-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="74635-157">針對只安裝執行階段但未安裝 SDK 的電腦，套件名稱是 `dotnet-runtime-<version>` (適用於 .NET Core 執行階段) 和 `aspnetcore-runtime-<version>` (適用於整個執行階段堆疊)。</span><span class="sxs-lookup"><span data-stu-id="74635-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="74635-158">.NET Core 安裝早于 2.0 時，使用包管理器卸載 SDK 時未卸載主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="74635-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="74635-159">請使用 `apt-get`，命令如下：</span><span class="sxs-lookup"><span data-stu-id="74635-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="74635-160">請注意，沒有附加到`dotnet-host`的版本。</span><span class="sxs-lookup"><span data-stu-id="74635-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="74635-161">如果您使用 tarball 安裝，則必須使用手動方法移除 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="74635-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="74635-162">您可以透過移除含有該版本的目錄，來個別移除 SDK 和執行階段。</span><span class="sxs-lookup"><span data-stu-id="74635-162">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="74635-163">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="74635-163">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="74635-164">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="74635-164">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="74635-165">macOS</span><span class="sxs-lookup"><span data-stu-id="74635-165">macOS</span></span>](#tab/macos)

<span data-ttu-id="74635-166">在 Mac 上，您必須透過移除含有該版本的目錄，來個別移除 SDK 和執行階段。</span><span class="sxs-lookup"><span data-stu-id="74635-166">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="74635-167">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="74635-167">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="74635-168">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="74635-168">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="74635-169">.NET Core 解除安裝工具</span><span class="sxs-lookup"><span data-stu-id="74635-169">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="74635-170">[.NET 核心卸載工具](../additional-tools/uninstall-tool.md)（`dotnet-core-uninstall`） 允許您從系統中刪除 .NET 核心 SDK 和運行時。</span><span class="sxs-lookup"><span data-stu-id="74635-170">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="74635-171">選項組合可用於指定應卸載哪些版本。</span><span class="sxs-lookup"><span data-stu-id="74635-171">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="74635-172">對 .NET 核心 SDK 版本的視覺化工作室依賴</span><span class="sxs-lookup"><span data-stu-id="74635-172">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="74635-173">在 Visual Studio 2019 版本 16.3 之前，Visual Studio 安裝程式稱為獨立的 .NET 酷睿 SDK 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="74635-173">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="74635-174">因此，SDK 版本將顯示在 Windows**添加/刪除程式**對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="74635-174">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="74635-175">刪除 Visual Studio 使用獨立安裝程式安裝的 .NET 核心 SDK 可能會中斷 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="74635-175">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="74635-176">如果卸載 SDK 後 Visual Studio 出現問題，請對該特定版本的 Visual Studio 運行修復。</span><span class="sxs-lookup"><span data-stu-id="74635-176">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="74635-177">下表顯示了 .NET Core SDK 版本的一些 Visual Studio 依賴項：</span><span class="sxs-lookup"><span data-stu-id="74635-177">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="74635-178">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="74635-178">Visual Studio version</span></span> | <span data-ttu-id="74635-179">.NET 核心 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="74635-179">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="74635-180">Visual Studio 2019 16.2 版</span><span class="sxs-lookup"><span data-stu-id="74635-180">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="74635-181">.NET 核心 SDK 2.2.4xx， 2.1.8xx</span><span class="sxs-lookup"><span data-stu-id="74635-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="74635-182">Visual Studio 2019 16.1 版</span><span class="sxs-lookup"><span data-stu-id="74635-182">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="74635-183">.NET 核心 SDK 2.2.3xx， 2.1.7xx</span><span class="sxs-lookup"><span data-stu-id="74635-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="74635-184">視覺工作室 2019 版本 16.0</span><span class="sxs-lookup"><span data-stu-id="74635-184">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="74635-185">.NET 核心 SDK 2.2.2xx， 2.1.6xx</span><span class="sxs-lookup"><span data-stu-id="74635-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="74635-186">視覺工作室 2017 版本 15.9</span><span class="sxs-lookup"><span data-stu-id="74635-186">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="74635-187">.NET 核心 SDK 2.2.1xx， 2.1.5xx</span><span class="sxs-lookup"><span data-stu-id="74635-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="74635-188">Visual Studio 2017 15.8 版</span><span class="sxs-lookup"><span data-stu-id="74635-188">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="74635-189">.NET 核心 SDK 2.1.4xx</span><span class="sxs-lookup"><span data-stu-id="74635-189">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="74635-190">從 Visual Studio 2019 版本 16.3 開始，Visual Studio 負責自己的 .NET 核心 SDK 副本。</span><span class="sxs-lookup"><span data-stu-id="74635-190">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="74635-191">因此，您不再在 **"添加/刪除程式"** 對話方塊中看到這些 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="74635-191">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="74635-192">刪除 NuGet 回退資料夾</span><span class="sxs-lookup"><span data-stu-id="74635-192">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="74635-193">在 .NET Core 3.0 SDK 之前，.NET Core SDK 安裝程式使用*NuGetFallbackFolder*存儲 NuGet 包的緩存。</span><span class="sxs-lookup"><span data-stu-id="74635-193">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="74635-194">此緩存在操作（如`dotnet restore`或`dotnet build /t:Restore`） 時使用。</span><span class="sxs-lookup"><span data-stu-id="74635-194">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="74635-195">位於`NuGetFallbackFolder`Windows 上的*C：*程式檔\dotnet_sdk，\* 位於 macOS 上的 */usr/local/share/點網/sdk。*</span><span class="sxs-lookup"><span data-stu-id="74635-195">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="74635-196">您可能希望刪除此資料夾，如果：</span><span class="sxs-lookup"><span data-stu-id="74635-196">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="74635-197">您只使用 .NET Core 3.0 SDK 或更高版本進行開發。</span><span class="sxs-lookup"><span data-stu-id="74635-197">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="74635-198">您正在使用早于 3.0 的 .NET Core SDK 版本進行開發，但您可以連線工作，並且速度可能會變慢一次。</span><span class="sxs-lookup"><span data-stu-id="74635-198">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="74635-199">如果要刪除 NuGet 回退資料夾，可以將其刪除，但需要管理員許可權才能刪除。</span><span class="sxs-lookup"><span data-stu-id="74635-199">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="74635-200">不建議刪除*dotnet*資料夾。</span><span class="sxs-lookup"><span data-stu-id="74635-200">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="74635-201">這樣做將刪除以前安裝的任何全域工具。</span><span class="sxs-lookup"><span data-stu-id="74635-201">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="74635-202">此外，在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="74635-202">Also, on Windows:</span></span>

- <span data-ttu-id="74635-203">您將打破 Visual Studio 2019 版本 16.3 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="74635-203">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="74635-204">您可以運行 **"修復"** 以恢復。</span><span class="sxs-lookup"><span data-stu-id="74635-204">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="74635-205">如果在 **"添加/刪除程式"** 對話方塊中有 .NET 核心 SDK 條目，則這些條目將孤立化。</span><span class="sxs-lookup"><span data-stu-id="74635-205">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
