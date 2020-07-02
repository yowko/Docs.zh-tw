---
title: 在 openSUSE 上安裝 .NET Core-.NET Core
description: 示範在 openSUSE 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619464"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="bc48d-103">在 openSUSE 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="bc48d-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="bc48d-104">OpenSUSE 上支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="bc48d-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="bc48d-105">本文說明如何在 openSUSE 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="bc48d-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="bc48d-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="bc48d-106">Supported distributions</span></span>

<span data-ttu-id="bc48d-107">下表是 openSUSE 15 上目前支援的 .NET Core 版本清單。</span><span class="sxs-lookup"><span data-stu-id="bc48d-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="bc48d-108">在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或不再支援 openSUSE 版本之前，這些版本都會持續受到支援。</span><span class="sxs-lookup"><span data-stu-id="bc48d-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="bc48d-109">✔️表示仍然支援 openSUSE 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="bc48d-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="bc48d-110">A ❌ 表示該 openSUSE 版本不支援 openSUSE 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="bc48d-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="bc48d-111">當 openSUSE 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="bc48d-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="bc48d-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="bc48d-112">openSUSE</span></span>                   | <span data-ttu-id="bc48d-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bc48d-113">.NET Core 2.1</span></span> | <span data-ttu-id="bc48d-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="bc48d-114">.NET Core 3.1</span></span> | <span data-ttu-id="bc48d-115">.NET 5 Preview （僅限手動安裝）</span><span class="sxs-lookup"><span data-stu-id="bc48d-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="bc48d-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="bc48d-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="bc48d-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="bc48d-117">✔️ 2.1</span></span>        | <span data-ttu-id="bc48d-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="bc48d-118">✔️ 3.1</span></span>        | <span data-ttu-id="bc48d-119">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="bc48d-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="bc48d-120">已不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="bc48d-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="bc48d-121">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="bc48d-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="bc48d-122">3.0</span><span class="sxs-lookup"><span data-stu-id="bc48d-122">3.0</span></span>
- <span data-ttu-id="bc48d-123">2.2</span><span class="sxs-lookup"><span data-stu-id="bc48d-123">2.2</span></span>
- <span data-ttu-id="bc48d-124">2.0</span><span class="sxs-lookup"><span data-stu-id="bc48d-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="bc48d-125">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="bc48d-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="bc48d-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="bc48d-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="bc48d-127">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="bc48d-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="bc48d-128">本節提供使用封裝管理員安裝 .NET Core 時，可能會收到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="bc48d-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="bc48d-129">無法提取</span><span class="sxs-lookup"><span data-stu-id="bc48d-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="bc48d-130">抓取</span><span class="sxs-lookup"><span data-stu-id="bc48d-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="bc48d-131">相依性</span><span class="sxs-lookup"><span data-stu-id="bc48d-131">Dependencies</span></span>

<span data-ttu-id="bc48d-132">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="bc48d-132">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="bc48d-133">但是，如果您手動安裝 .NET Core 或發行獨立的應用程式，您必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="bc48d-133">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="bc48d-134">krb5</span><span class="sxs-lookup"><span data-stu-id="bc48d-134">krb5</span></span>
- <span data-ttu-id="bc48d-135">libicu</span><span class="sxs-lookup"><span data-stu-id="bc48d-135">libicu</span></span>
- <span data-ttu-id="bc48d-136">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="bc48d-136">libopenssl1_0_0</span></span>

<span data-ttu-id="bc48d-137">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您將需要安裝**相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="bc48d-137">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="bc48d-138">如需相依性的詳細資訊，請參閱[獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="bc48d-138">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="bc48d-139">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="bc48d-139">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="bc48d-140">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="bc48d-140">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="bc48d-141">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的*libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="bc48d-141">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="bc48d-142">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/> 。</span><span class="sxs-lookup"><span data-stu-id="bc48d-142">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="bc48d-143">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="bc48d-143">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="bc48d-144">手動安裝</span><span class="sxs-lookup"><span data-stu-id="bc48d-144">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="bc48d-145">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bc48d-145">Next steps</span></span>

- [<span data-ttu-id="bc48d-146">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="bc48d-146">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
