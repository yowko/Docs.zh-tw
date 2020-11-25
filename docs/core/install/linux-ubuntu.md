---
title: 在 Ubuntu 上安裝 .NET-.NET
description: 示範在 Ubuntu 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 22ce3379e028f065528e1f507a2d8c1ae598f0e8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031838"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="3bc39-103">在 Ubuntu 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="3bc39-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="3bc39-104">Ubuntu 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="3bc39-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="3bc39-105">本文說明如何在 Ubuntu 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="3bc39-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="3bc39-106">當 Ubuntu 版本不受支援時，就不再支援該版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="3bc39-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="3bc39-107">不過，這些指示可協助您讓 .NET 在這些版本上執行，即使它不受支援也是一樣。</span><span class="sxs-lookup"><span data-stu-id="3bc39-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="3bc39-108">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="3bc39-108">Supported distributions</span></span>

<span data-ttu-id="3bc39-109">下表列出目前支援的 .NET 版本，以及支援的 Ubuntu 版本。</span><span class="sxs-lookup"><span data-stu-id="3bc39-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="3bc39-110">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Ubuntu 的版本 [達到生命週期結束](https://wiki.ubuntu.com/Releases)，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="3bc39-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="3bc39-111">✔️表示仍支援 Ubuntu 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="3bc39-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="3bc39-112">❌表示該 ubuntu 版本不支援 ubuntu 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="3bc39-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="3bc39-113">當 Ubuntu 版本和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="3bc39-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="3bc39-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3bc39-114">Ubuntu</span></span>                   | <span data-ttu-id="3bc39-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3bc39-115">.NET Core 2.1</span></span> | <span data-ttu-id="3bc39-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="3bc39-116">.NET Core 3.1</span></span> | <span data-ttu-id="3bc39-117">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="3bc39-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="3bc39-118">✔️ [20.10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="3bc39-119">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-119">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-120">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-120">✔️ 3.1</span></span>        | <span data-ttu-id="3bc39-121">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="3bc39-121">✔️ 5.0</span></span> |
| <span data-ttu-id="3bc39-122">✔️ [20.04 (LTS) ](#2004-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="3bc39-123">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-123">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-124">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-124">✔️ 3.1</span></span>        | <span data-ttu-id="3bc39-125">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="3bc39-125">✔️ 5.0</span></span> |
| <span data-ttu-id="3bc39-126">❌[19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="3bc39-127">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-127">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-128">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-128">✔️ 3.1</span></span>        | <span data-ttu-id="3bc39-129">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="3bc39-129">✔️ 5.0</span></span> |
| <span data-ttu-id="3bc39-130">❌[19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="3bc39-131">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-131">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-132">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-132">✔️ 3.1</span></span>        | <span data-ttu-id="3bc39-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3bc39-133">❌ 5.0</span></span> |
| <span data-ttu-id="3bc39-134">❌[18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="3bc39-135">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-135">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-136">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="3bc39-136">❌ 3.1</span></span>        | <span data-ttu-id="3bc39-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3bc39-137">❌ 5.0</span></span> |
| <span data-ttu-id="3bc39-138">✔️ [18.04 (LTS) ](#1804-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="3bc39-139">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-139">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-140">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-140">✔️ 3.1</span></span>        | <span data-ttu-id="3bc39-141">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="3bc39-141">✔️ 5.0</span></span> |
| <span data-ttu-id="3bc39-142">❌[17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="3bc39-143">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-143">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="3bc39-144">❌ 3.1</span></span>        | <span data-ttu-id="3bc39-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3bc39-145">❌ 5.0</span></span> |
| <span data-ttu-id="3bc39-146">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="3bc39-147">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-147">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-148">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="3bc39-148">❌ 3.1</span></span>        | <span data-ttu-id="3bc39-149">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3bc39-149">❌ 5.0</span></span> |
| <span data-ttu-id="3bc39-150">❌[16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="3bc39-151">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="3bc39-151">❌ 2.1</span></span>        | <span data-ttu-id="3bc39-152">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="3bc39-152">❌ 3.1</span></span>        | <span data-ttu-id="3bc39-153">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="3bc39-153">❌ 5.0</span></span> |
| <span data-ttu-id="3bc39-154">✔️ [16.04 (LTS) ](#1604-)</span><span class="sxs-lookup"><span data-stu-id="3bc39-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="3bc39-155">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-155">✔️ 2.1</span></span>        | <span data-ttu-id="3bc39-156">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="3bc39-156">✔️ 3.1</span></span>        | <span data-ttu-id="3bc39-157">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="3bc39-157">✔️ 5.0</span></span> |

<span data-ttu-id="3bc39-158">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="3bc39-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="3bc39-159">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="3bc39-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="3bc39-160">3.0</span><span class="sxs-lookup"><span data-stu-id="3bc39-160">3.0</span></span>
- <span data-ttu-id="3bc39-161">2.2</span><span class="sxs-lookup"><span data-stu-id="3bc39-161">2.2</span></span>
- <span data-ttu-id="3bc39-162">2.0</span><span class="sxs-lookup"><span data-stu-id="3bc39-162">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="3bc39-163">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="3bc39-163">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="3bc39-164">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="3bc39-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="3bc39-165">20.10 ✔️</span><span class="sxs-lookup"><span data-stu-id="3bc39-165">20.10 ✔️</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bc39-166">套件摘要中尚無法使用 .NET Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="3bc39-166">.NET Core 2.1 isn't yet available in the package feed.</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="3bc39-167">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="3bc39-167">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="3bc39-168">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="3bc39-168">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="3bc39-169">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="3bc39-169">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="3bc39-170">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="3bc39-170">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="3bc39-171">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="3bc39-171">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="3bc39-172">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="3bc39-172">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="3bc39-173">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="3bc39-173">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="3bc39-174">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="3bc39-174">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="3bc39-175">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="3bc39-175">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="3bc39-176">APT 更新 SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="3bc39-176">APT update SDK or runtime</span></span>

<span data-ttu-id="3bc39-177">當 .NET 有新的修補程式版本時，您可以使用下列命令透過 APT 升級：</span><span class="sxs-lookup"><span data-stu-id="3bc39-177">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="3bc39-178">APT 疑難排解</span><span class="sxs-lookup"><span data-stu-id="3bc39-178">APT troubleshooting</span></span>

<span data-ttu-id="3bc39-179">本節提供使用 APT 來安裝 .NET 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3bc39-179">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="3bc39-180">找不到套件</span><span class="sxs-lookup"><span data-stu-id="3bc39-180">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="3bc39-181">找不到 \\ 某些套件無法安裝</span><span class="sxs-lookup"><span data-stu-id="3bc39-181">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="3bc39-182">無法提取</span><span class="sxs-lookup"><span data-stu-id="3bc39-182">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="3bc39-183">單元</span><span class="sxs-lookup"><span data-stu-id="3bc39-183">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="3bc39-184">相依性</span><span class="sxs-lookup"><span data-stu-id="3bc39-184">Dependencies</span></span>

<span data-ttu-id="3bc39-185">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="3bc39-185">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="3bc39-186">但是，如果您手動安裝 .NET 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="3bc39-186">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="3bc39-187">libc6</span><span class="sxs-lookup"><span data-stu-id="3bc39-187">libc6</span></span>
- <span data-ttu-id="3bc39-188">libgcc1</span><span class="sxs-lookup"><span data-stu-id="3bc39-188">libgcc1</span></span>
- <span data-ttu-id="3bc39-189">libgssapi-krb5.keytab-2</span><span class="sxs-lookup"><span data-stu-id="3bc39-189">libgssapi-krb5-2</span></span>
- <span data-ttu-id="3bc39-190">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="3bc39-190">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="3bc39-191">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="3bc39-191">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="3bc39-192">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="3bc39-192">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="3bc39-193">libicu66 (for 20. x) </span><span class="sxs-lookup"><span data-stu-id="3bc39-193">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="3bc39-194">libssl1.0.0 1.0.0 (，適用于 14. x、16. x) </span><span class="sxs-lookup"><span data-stu-id="3bc39-194">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="3bc39-195">libssl1.0.0 1.1 (，適用于6.x、20. x) </span><span class="sxs-lookup"><span data-stu-id="3bc39-195">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="3bc39-196">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="3bc39-196">libstdc++6</span></span>
- <span data-ttu-id="3bc39-197">zlib1g</span><span class="sxs-lookup"><span data-stu-id="3bc39-197">zlib1g</span></span>

<span data-ttu-id="3bc39-198">若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="3bc39-198">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="3bc39-199">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="3bc39-199">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="3bc39-200">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="3bc39-200">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="3bc39-201">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="3bc39-201">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="3bc39-202">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="3bc39-202">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="3bc39-203">手動安裝</span><span class="sxs-lookup"><span data-stu-id="3bc39-203">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="3bc39-204">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3bc39-204">Next steps</span></span>

- [<span data-ttu-id="3bc39-205">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3bc39-205">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
