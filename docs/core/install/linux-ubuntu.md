---
title: 在 Ubuntu 上安裝 .NET Core-.NET Core
description: 示範在 Ubuntu 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c590bd89b718a5cd31dae9f83049eac910cb4049
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863887"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="cf513-103">在 Ubuntu 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="cf513-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="cf513-104">Ubuntu 支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cf513-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="cf513-105">本文說明如何在 Ubuntu 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cf513-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="cf513-106">當 Ubuntu 版本不支援時，該版本就不再支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cf513-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="cf513-107">不過，這些指示可以協助您取得在這些版本上執行的 .NET Core，即使它不受支援也一樣。</span><span class="sxs-lookup"><span data-stu-id="cf513-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="cf513-108">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="cf513-108">Supported distributions</span></span>

<span data-ttu-id="cf513-109">下表列出目前支援的 .NET Core 版本，以及支援的 Ubuntu 版本。</span><span class="sxs-lookup"><span data-stu-id="cf513-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="cf513-110">這些版本持續支援，直到[.Net Core 版本達到支援的終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或 Ubuntu 的版本[達到生命週期的結束](https://wiki.ubuntu.com/Releases)為止。</span><span class="sxs-lookup"><span data-stu-id="cf513-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="cf513-111">✔️表示仍然支援 Ubuntu 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="cf513-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="cf513-112">A ❌ 表示該 ubuntu 版本不支援 ubuntu 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="cf513-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="cf513-113">當 Ubuntu 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="cf513-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="cf513-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cf513-114">Ubuntu</span></span>                   | <span data-ttu-id="cf513-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cf513-115">.NET Core 2.1</span></span> | <span data-ttu-id="cf513-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="cf513-116">.NET Core 3.1</span></span> | <span data-ttu-id="cf513-117">.NET 5 Preview （僅限手動安裝）</span><span class="sxs-lookup"><span data-stu-id="cf513-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="cf513-118">✔️ [20.04 （LTS）](#2004-)</span><span class="sxs-lookup"><span data-stu-id="cf513-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="cf513-119">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-119">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-120">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="cf513-120">✔️ 3.1</span></span>        | <span data-ttu-id="cf513-121">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="cf513-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-122">❌[19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="cf513-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="cf513-123">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-123">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-124">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="cf513-124">✔️ 3.1</span></span>        | <span data-ttu-id="cf513-125">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="cf513-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-126">❌[19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="cf513-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="cf513-127">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-127">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-128">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="cf513-128">✔️ 3.1</span></span>        | <span data-ttu-id="cf513-129">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="cf513-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-130">❌[18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="cf513-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="cf513-131">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-131">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-132">❌3.1</span><span class="sxs-lookup"><span data-stu-id="cf513-132">❌ 3.1</span></span>        | <span data-ttu-id="cf513-133">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="cf513-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-134">✔️ [18.04 （LTS）](#1804-)</span><span class="sxs-lookup"><span data-stu-id="cf513-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="cf513-135">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-135">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-136">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="cf513-136">✔️ 3.1</span></span>        | <span data-ttu-id="cf513-137">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="cf513-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-138">❌[17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="cf513-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="cf513-139">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-139">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-140">❌3.1</span><span class="sxs-lookup"><span data-stu-id="cf513-140">❌ 3.1</span></span>        | <span data-ttu-id="cf513-141">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="cf513-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-142">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="cf513-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="cf513-143">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-143">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-144">❌3.1</span><span class="sxs-lookup"><span data-stu-id="cf513-144">❌ 3.1</span></span>        | <span data-ttu-id="cf513-145">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="cf513-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-146">❌[16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="cf513-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="cf513-147">❌2.1</span><span class="sxs-lookup"><span data-stu-id="cf513-147">❌ 2.1</span></span>        | <span data-ttu-id="cf513-148">❌3.1</span><span class="sxs-lookup"><span data-stu-id="cf513-148">❌ 3.1</span></span>        | <span data-ttu-id="cf513-149">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="cf513-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="cf513-150">✔️ [16.04 （LTS）](#1604-)</span><span class="sxs-lookup"><span data-stu-id="cf513-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="cf513-151">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="cf513-151">✔️ 2.1</span></span>        | <span data-ttu-id="cf513-152">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="cf513-152">✔️ 3.1</span></span>        | <span data-ttu-id="cf513-153">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="cf513-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="cf513-154">已不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="cf513-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="cf513-155">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="cf513-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="cf513-156">3.0</span><span class="sxs-lookup"><span data-stu-id="cf513-156">3.0</span></span>
- <span data-ttu-id="cf513-157">2.2</span><span class="sxs-lookup"><span data-stu-id="cf513-157">2.2</span></span>
- <span data-ttu-id="cf513-158">2.0</span><span class="sxs-lookup"><span data-stu-id="cf513-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cf513-159">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="cf513-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="cf513-160">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cf513-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="cf513-161">19.10❌</span><span class="sxs-lookup"><span data-stu-id="cf513-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="cf513-162">19.04❌</span><span class="sxs-lookup"><span data-stu-id="cf513-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="cf513-163">18.10❌</span><span class="sxs-lookup"><span data-stu-id="cf513-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="cf513-164">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cf513-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="cf513-165">17.10❌</span><span class="sxs-lookup"><span data-stu-id="cf513-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="cf513-166">17.04❌</span><span class="sxs-lookup"><span data-stu-id="cf513-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="cf513-167">16.10❌</span><span class="sxs-lookup"><span data-stu-id="cf513-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="cf513-168">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cf513-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="cf513-169">APT 更新 SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="cf513-169">APT update SDK or runtime</span></span>

<span data-ttu-id="cf513-170">當 .NET Core 有新的修補程式版本可供使用時，您只要使用下列命令，即可透過 APT 進行升級：</span><span class="sxs-lookup"><span data-stu-id="cf513-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="cf513-171">APT 疑難排解</span><span class="sxs-lookup"><span data-stu-id="cf513-171">APT troubleshooting</span></span>

<span data-ttu-id="cf513-172">本節提供您在使用 APT 安裝 .NET Core 時可能會遇到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="cf513-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="cf513-173">找不到</span><span class="sxs-lookup"><span data-stu-id="cf513-173">Unable to locate</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="cf513-174">無法提取</span><span class="sxs-lookup"><span data-stu-id="cf513-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="cf513-175">抓取</span><span class="sxs-lookup"><span data-stu-id="cf513-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="cf513-176">相依性</span><span class="sxs-lookup"><span data-stu-id="cf513-176">Dependencies</span></span>

<span data-ttu-id="cf513-177">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="cf513-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="cf513-178">但是，如果您手動安裝 .NET Core 或發行獨立的應用程式，您必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="cf513-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="cf513-179">libc6</span><span class="sxs-lookup"><span data-stu-id="cf513-179">libc6</span></span>
- <span data-ttu-id="cf513-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="cf513-180">libgcc1</span></span>
- <span data-ttu-id="cf513-181">libgssapi-krb5-krb5-2</span><span class="sxs-lookup"><span data-stu-id="cf513-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="cf513-182">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="cf513-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="cf513-183">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="cf513-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="cf513-184">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="cf513-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="cf513-185">libicu66 （適用于 20. x）</span><span class="sxs-lookup"><span data-stu-id="cf513-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="cf513-186">libssl1.0.0 1.0.0 （適用于 14. x、16. x）</span><span class="sxs-lookup"><span data-stu-id="cf513-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="cf513-187">libssl1.0.0 1.1 （適用于 18. x、20. x）</span><span class="sxs-lookup"><span data-stu-id="cf513-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="cf513-188">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="cf513-188">libstdc++6</span></span>
- <span data-ttu-id="cf513-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="cf513-189">zlib1g</span></span>

<span data-ttu-id="cf513-190">針對使用*system.web*元件的 .net Core 應用程式，您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="cf513-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="cf513-191">libgdiplus （6.0.1 版或更新版本）</span><span class="sxs-lookup"><span data-stu-id="cf513-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="cf513-192">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的*libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="cf513-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="cf513-193">如需詳細資訊，請參閱 <https://www.mono-project.com/download/stable/> 。</span><span class="sxs-lookup"><span data-stu-id="cf513-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="cf513-194">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="cf513-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="cf513-195">手動安裝</span><span class="sxs-lookup"><span data-stu-id="cf513-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="cf513-196">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="cf513-196">Next steps</span></span>

- [<span data-ttu-id="cf513-197">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="cf513-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
