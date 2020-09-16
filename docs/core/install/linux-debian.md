---
title: 在 Debian 上安裝 .NET Core-.NET Core
description: 示範在 Debian 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: d0f7d4092ec420d031d0874a56b9e2148afdb865
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538536"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="2dfbf-103">在 Debian 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="2dfbf-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="2dfbf-104">本文說明如何在 Debian 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="2dfbf-105">當 Debian 版本不受支援時，就不再支援該版本的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="2dfbf-106">不過，這些指示可協助您讓 .NET Core 在這些版本上執行，即使它不受支援也是一樣。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="2dfbf-107">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="2dfbf-107">Supported distributions</span></span>

<span data-ttu-id="2dfbf-108">下表列出目前支援的 .NET Core 版本，以及其支援的 Debian 版本。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="2dfbf-109">在 [.Net Core 的版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Debian 的版本 [達到生命週期結束](https://wiki.debian.org/DebianReleases)之前，會持續支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="2dfbf-110">✔️表示仍支援 Debian 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="2dfbf-111">❌指出該 Debian 版本不支援 Debian 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="2dfbf-112">當版本的 Debian 和 .NET Core 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="2dfbf-113">Debian</span><span class="sxs-lookup"><span data-stu-id="2dfbf-113">Debian</span></span>                   | <span data-ttu-id="2dfbf-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-114">.NET Core 2.1</span></span> | <span data-ttu-id="2dfbf-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-115">.NET Core 3.1</span></span> | <span data-ttu-id="2dfbf-116">.NET 5 Preview (僅限手動安裝) </span><span class="sxs-lookup"><span data-stu-id="2dfbf-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="2dfbf-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="2dfbf-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="2dfbf-118">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-118">✔️ 2.1</span></span>        | <span data-ttu-id="2dfbf-119">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-119">✔️ 3.1</span></span>        | <span data-ttu-id="2dfbf-120">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="2dfbf-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="2dfbf-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="2dfbf-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="2dfbf-122">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-122">✔️ 2.1</span></span>        | <span data-ttu-id="2dfbf-123">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-123">✔️ 3.1</span></span>        | <span data-ttu-id="2dfbf-124">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="2dfbf-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="2dfbf-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="2dfbf-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="2dfbf-126">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-126">✔️ 2.1</span></span>        | <span data-ttu-id="2dfbf-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-127">❌ 3.1</span></span>        | <span data-ttu-id="2dfbf-128">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="2dfbf-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="2dfbf-129">不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="2dfbf-130">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="2dfbf-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="2dfbf-131">3.0</span><span class="sxs-lookup"><span data-stu-id="2dfbf-131">3.0</span></span>
- <span data-ttu-id="2dfbf-132">2.2</span><span class="sxs-lookup"><span data-stu-id="2dfbf-132">2.2</span></span>
- <span data-ttu-id="2dfbf-133">2.0</span><span class="sxs-lookup"><span data-stu-id="2dfbf-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2dfbf-134">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="2dfbf-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="2dfbf-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="2dfbf-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="2dfbf-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="2dfbf-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="2dfbf-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="2dfbf-137">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="2dfbf-138">APT 更新 SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="2dfbf-138">APT update SDK or runtime</span></span>

<span data-ttu-id="2dfbf-139">當 .NET Core 有新的修補程式版本可供使用時，您可以使用下列命令透過 APT 升級：</span><span class="sxs-lookup"><span data-stu-id="2dfbf-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="2dfbf-140">APT 疑難排解</span><span class="sxs-lookup"><span data-stu-id="2dfbf-140">APT troubleshooting</span></span>

<span data-ttu-id="2dfbf-141">本節提供使用 APT 來安裝 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="2dfbf-142">找不到套件</span><span class="sxs-lookup"><span data-stu-id="2dfbf-142">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="2dfbf-143">找不到 \\ 某些套件無法安裝</span><span class="sxs-lookup"><span data-stu-id="2dfbf-143">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="2dfbf-144">無法提取</span><span class="sxs-lookup"><span data-stu-id="2dfbf-144">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="2dfbf-145">單元</span><span class="sxs-lookup"><span data-stu-id="2dfbf-145">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="2dfbf-146">相依性</span><span class="sxs-lookup"><span data-stu-id="2dfbf-146">Dependencies</span></span>

<span data-ttu-id="2dfbf-147">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="2dfbf-148">但是，如果您手動安裝 .NET Core 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="2dfbf-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="2dfbf-149">libc6</span><span class="sxs-lookup"><span data-stu-id="2dfbf-149">libc6</span></span>
- <span data-ttu-id="2dfbf-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="2dfbf-150">libgcc1</span></span>
- <span data-ttu-id="2dfbf-151">libgssapi-krb5.keytab-2</span><span class="sxs-lookup"><span data-stu-id="2dfbf-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="2dfbf-152">適用于 8.x) 的 libicu52 (</span><span class="sxs-lookup"><span data-stu-id="2dfbf-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="2dfbf-153">libicu57 (for 2.x) </span><span class="sxs-lookup"><span data-stu-id="2dfbf-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="2dfbf-154">libicu63 (for 2.x) </span><span class="sxs-lookup"><span data-stu-id="2dfbf-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="2dfbf-155">適用于 11. x) 的 libicu67 (</span><span class="sxs-lookup"><span data-stu-id="2dfbf-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="2dfbf-156">適用于 8.x) 的 libssl1.0.0 1.0.0 (</span><span class="sxs-lookup"><span data-stu-id="2dfbf-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="2dfbf-157">libssl1.0.0 1.1 (for 2.x-11. x) </span><span class="sxs-lookup"><span data-stu-id="2dfbf-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="2dfbf-158">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="2dfbf-158">libstdc++6</span></span>
- <span data-ttu-id="2dfbf-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="2dfbf-159">zlib1g</span></span>

<span data-ttu-id="2dfbf-160">若為使用 system.string 元件的 .NET Core *應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="2dfbf-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="2dfbf-161">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="2dfbf-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="2dfbf-162">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="2dfbf-163">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="2dfbf-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="2dfbf-164">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="2dfbf-164">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="2dfbf-165">手動安裝</span><span class="sxs-lookup"><span data-stu-id="2dfbf-165">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="2dfbf-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2dfbf-166">Next steps</span></span>

- [<span data-ttu-id="2dfbf-167">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2dfbf-167">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
