---
title: 如何移除 .NET 執行階段和 SDK
description: 在 Windows、Mac 和 Linux 上移除 .NET Core 執行階段和 SDK 元件的指示
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.openlocfilehash: 1806d1af3b10e44ccc2eff788d8958ca976fe85b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989809"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="0ff07-103">如何移除 .NET Core 執行階段和 SDK</span><span class="sxs-lookup"><span data-stu-id="0ff07-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="0ff07-104">隨時間下來，當您安裝 .NET Core 執行階段和 SDK 的更新版本時，您可能想要從電腦移除過期的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="0ff07-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="0ff07-105">移除舊版執行階段可能會變更選為執行共用架構應用程式的執行階段，如 [.NET Core 版本選取](selection.md)一文所述。</span><span class="sxs-lookup"><span data-stu-id="0ff07-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

<span data-ttu-id="0ff07-106">從 .NET Core 2.1 開始，.NET CLI 可讓您選擇使用電腦上安裝的 SDK 和執行階段版本清單。</span><span class="sxs-lookup"><span data-stu-id="0ff07-106">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="0ff07-107">使用 [`dotnet --list-sdks`](../tools/dotnet.md#options) 可查看您電腦上安裝的 SDK 清單。</span><span class="sxs-lookup"><span data-stu-id="0ff07-107">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="0ff07-108">使用 [`dotnet --list-runtimes`](../tools/dotnet.md#options) 可查看您電腦上安裝的執行階段清單。</span><span class="sxs-lookup"><span data-stu-id="0ff07-108">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="0ff07-109">下列文字顯示 Windows、macOS 或 Linux 的一般輸出：</span><span class="sxs-lookup"><span data-stu-id="0ff07-109">The following text shows typical output for Windows, macOS, or Linux:</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="0ff07-110">Windows</span><span class="sxs-lookup"><span data-stu-id="0ff07-110">Windows</span></span>](#tab/Windows)

```console
C:\> dotnet --list-sdks
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

C:\> dotnet --list-runtimes
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

# <a name="linuxtablinux"></a>[<span data-ttu-id="0ff07-111">Linux</span><span class="sxs-lookup"><span data-stu-id="0ff07-111">Linux</span></span>](#tab/Linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
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

# <a name="macostabmacos"></a>[<span data-ttu-id="0ff07-112">macOS</span><span class="sxs-lookup"><span data-stu-id="0ff07-112">macOS</span></span>](#tab/macOS)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
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

***

## <a name="uninstalling-net-core"></a><span data-ttu-id="0ff07-113">解除安裝 .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ff07-113">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="0ff07-114">Windows</span><span class="sxs-lookup"><span data-stu-id="0ff07-114">Windows</span></span>](#tab/Windows)

<span data-ttu-id="0ff07-115">.NET Core 使用 Windows [新增/移除程式] 對話方塊來移除 .NET Core 執行階段和 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="0ff07-115">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="0ff07-116">下圖顯示 [新增/移除程式] 對話方塊，其中已安裝數個 .NET 執行階段和 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="0ff07-116">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![用以移除 .NET Core 的 [新增/移除程式]](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="0ff07-118">選取您想要從電腦移除的任意版本，然後按一下 [解除安裝]。</span><span class="sxs-lookup"><span data-stu-id="0ff07-118">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="0ff07-119">Linux</span><span class="sxs-lookup"><span data-stu-id="0ff07-119">Linux</span></span>](#tab/Linux)

<span data-ttu-id="0ff07-120">在 Linux 上解除安裝 .NET Core (SDK 或執行階段) 有更多選項。</span><span class="sxs-lookup"><span data-stu-id="0ff07-120">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="0ff07-121">解除安裝 .NET Core 的最佳方式是對照您用來安裝 .NET Core 的動作。</span><span class="sxs-lookup"><span data-stu-id="0ff07-121">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="0ff07-122">細節會依您選擇的版本和安裝方法而異。</span><span class="sxs-lookup"><span data-stu-id="0ff07-122">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ff07-123">針對 Red Hat 安裝，請參閱 [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) (Red Hat 入門指南)，取得安裝和解除安裝 .NET Core 的資訊。</span><span class="sxs-lookup"><span data-stu-id="0ff07-123">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="0ff07-124">從 .NET Core 2.1 開始，不需要解除安裝 .NET Core SDK，使用套件管理員即可升級。</span><span class="sxs-lookup"><span data-stu-id="0ff07-124">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="0ff07-125">套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。</span><span class="sxs-lookup"><span data-stu-id="0ff07-125">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="0ff07-126">如果您使用套件管理員來安裝 .NET Core，您可以使用該相同的套件管理員來解除安裝 .NET SDK 或執行階段。</span><span class="sxs-lookup"><span data-stu-id="0ff07-126">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="0ff07-127">.NET Core 安裝支援最熱門的套件管理員。</span><span class="sxs-lookup"><span data-stu-id="0ff07-127">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="0ff07-128">請參閱版本的套件管理員文件，了解環境的精確語法：</span><span class="sxs-lookup"><span data-stu-id="0ff07-128">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="0ff07-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) 適用於 Debian 型系統，包括 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="0ff07-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="0ff07-130">[yum(8)](https://linux.die.net/man/8/yum) 適用於 Fedora、CentOS 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="0ff07-130">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="0ff07-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 適用於 openSUSE 和 SUSE Linux Enterprise System (SLES)。</span><span class="sxs-lookup"><span data-stu-id="0ff07-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="0ff07-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) 適用於 Fedora。</span><span class="sxs-lookup"><span data-stu-id="0ff07-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="0ff07-133">在絕大多數的情況下，移除套件的命令是 `remove`。</span><span class="sxs-lookup"><span data-stu-id="0ff07-133">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="0ff07-134">對於大多數套件管理員，.NET Core SDK 安裝的套件名稱是 `dotnet-sdk`，後面接著版本號碼。</span><span class="sxs-lookup"><span data-stu-id="0ff07-134">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="0ff07-135">從 .NET Core SDK 2.1.300 版和執行階段 `2.1` 版開始，只需要主要和次要版本號碼：例如，.NET Core SDK 2.1.300 版可用套件 `dotnet-sdk-2.1` 參考。</span><span class="sxs-lookup"><span data-stu-id="0ff07-135">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="0ff07-136">舊版需要整個版本字串：例如，.NET Core SDK 2.1.200 版需要 `dotnet-sdk-2.1.200`。</span><span class="sxs-lookup"><span data-stu-id="0ff07-136">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="0ff07-137">針對只安裝執行階段但未安裝 SDK 的電腦，套件名稱是 `dotnet-runtime-<version>` (適用於 .NET Core 執行階段) 和 `aspnetcore-runtime-<version>` (適用於整個執行階段堆疊)。</span><span class="sxs-lookup"><span data-stu-id="0ff07-137">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="0ff07-138">使用套件管理員解除安裝 SDK 時，2.0 以前的 .NET Core 安裝不會解除安裝主應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ff07-138">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="0ff07-139">請使用 `apt-get`，命令如下：</span><span class="sxs-lookup"><span data-stu-id="0ff07-139">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="0ff07-140">請注意，`dotnet-host` 未附加任何版本。</span><span class="sxs-lookup"><span data-stu-id="0ff07-140">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="0ff07-141">如果您使用 tarball 安裝，則必須使用手動方法移除 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="0ff07-141">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="0ff07-142">您可以透過移除含有該版本的目錄，來個別移除 SDK 和執行階段。</span><span class="sxs-lookup"><span data-stu-id="0ff07-142">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="0ff07-143">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="0ff07-143">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="0ff07-144">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="0ff07-144">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="0ff07-145">macOS</span><span class="sxs-lookup"><span data-stu-id="0ff07-145">macOS</span></span>](#tab/macOS)

<span data-ttu-id="0ff07-146">在 Mac 上，您必須透過移除含有該版本的目錄，來個別移除 SDK 和執行階段。</span><span class="sxs-lookup"><span data-stu-id="0ff07-146">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="0ff07-147">例如，若要移除 1.0.1 SDK 和執行階段，您可以使用下列 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="0ff07-147">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="0ff07-148">SDK 和執行階段的父目錄會列於 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令輸出，如前述表格所示。</span><span class="sxs-lookup"><span data-stu-id="0ff07-148">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

<span data-ttu-id="0ff07-149">從 .NET Core 2.1 開始，不需要解除安裝 .NET Core SDK，使用套件管理員即可升級。</span><span class="sxs-lookup"><span data-stu-id="0ff07-149">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="0ff07-150">套件管理員 `update` 或 `refresh` 命令會在成功安裝新版本之後，自動移除舊版本。</span><span class="sxs-lookup"><span data-stu-id="0ff07-150">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

---
