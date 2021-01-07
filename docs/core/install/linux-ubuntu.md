---
title: 在 Ubuntu 上安裝 .NET-.NET
description: 示範在 Ubuntu 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 14e5e9548d4aa09a586e2038f3e35a489ee65cd2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970758"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="ee2a4-103">在 Ubuntu 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="ee2a4-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="ee2a4-104">Ubuntu 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="ee2a4-105">本文說明如何在 Ubuntu 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="ee2a4-106">當 Ubuntu 版本不受支援時，就不再支援該版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="ee2a4-107">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="ee2a4-107">Supported distributions</span></span>

<span data-ttu-id="ee2a4-108">下表列出目前支援的 .NET 版本，以及支援的 Ubuntu 版本。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-108">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="ee2a4-109">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Ubuntu 的版本 [達到生命週期結束](https://wiki.ubuntu.com/Releases)，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="ee2a4-110">✔️表示仍支援 Ubuntu 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-110">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="ee2a4-111">❌表示該 ubuntu 版本不支援 ubuntu 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-111">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="ee2a4-112">當 Ubuntu 版本和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-112">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="ee2a4-113">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ee2a4-113">Ubuntu</span></span>                   | <span data-ttu-id="ee2a4-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-114">.NET Core 2.1</span></span> | <span data-ttu-id="ee2a4-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-115">.NET Core 3.1</span></span> | <span data-ttu-id="ee2a4-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="ee2a4-117">✔️ [20.10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-117">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="ee2a4-118">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-118">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-119">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-119">✔️ 3.1</span></span>        | <span data-ttu-id="ee2a4-120">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-120">✔️ 5.0</span></span> |
| <span data-ttu-id="ee2a4-121">✔️ [20.04 (LTS) ](#2004-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-121">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="ee2a4-122">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-122">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-123">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-123">✔️ 3.1</span></span>        | <span data-ttu-id="ee2a4-124">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-124">✔️ 5.0</span></span> |
| <span data-ttu-id="ee2a4-125">❌[19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-125">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="ee2a4-126">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-126">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-127">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-127">✔️ 3.1</span></span>        | <span data-ttu-id="ee2a4-128">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-128">✔️ 5.0</span></span> |
| <span data-ttu-id="ee2a4-129">❌[19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-129">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="ee2a4-130">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-130">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-131">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-131">✔️ 3.1</span></span>        | <span data-ttu-id="ee2a4-132">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-132">❌ 5.0</span></span> |
| <span data-ttu-id="ee2a4-133">❌[18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-133">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="ee2a4-134">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-134">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-135">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-135">❌ 3.1</span></span>        | <span data-ttu-id="ee2a4-136">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-136">❌ 5.0</span></span> |
| <span data-ttu-id="ee2a4-137">✔️ [18.04 (LTS) ](#1804-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-137">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="ee2a4-138">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-138">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-139">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-139">✔️ 3.1</span></span>        | <span data-ttu-id="ee2a4-140">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-140">✔️ 5.0</span></span> |
| <span data-ttu-id="ee2a4-141">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-141">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="ee2a4-142">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-142">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-143">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-143">❌ 3.1</span></span>        | <span data-ttu-id="ee2a4-144">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-144">❌ 5.0</span></span> |
| <span data-ttu-id="ee2a4-145">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-145">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="ee2a4-146">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-146">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-147">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-147">❌ 3.1</span></span>        | <span data-ttu-id="ee2a4-148">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-148">❌ 5.0</span></span> |
| <span data-ttu-id="ee2a4-149">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-149">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="ee2a4-150">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-150">❌ 2.1</span></span>        | <span data-ttu-id="ee2a4-151">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-151">❌ 3.1</span></span>        | <span data-ttu-id="ee2a4-152">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-152">❌ 5.0</span></span> |
| <span data-ttu-id="ee2a4-153">✔️ [16.04 (LTS) ](#1604-)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-153">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="ee2a4-154">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-154">✔️ 2.1</span></span>        | <span data-ttu-id="ee2a4-155">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-155">✔️ 3.1</span></span>        | <span data-ttu-id="ee2a4-156">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-156">✔️ 5.0</span></span> |

<span data-ttu-id="ee2a4-157">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-157">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="ee2a4-158">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="ee2a4-158">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ee2a4-159">3.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-159">3.0</span></span>
- <span data-ttu-id="ee2a4-160">2.2</span><span class="sxs-lookup"><span data-stu-id="ee2a4-160">2.2</span></span>
- <span data-ttu-id="ee2a4-161">2.0</span><span class="sxs-lookup"><span data-stu-id="ee2a4-161">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="ee2a4-162">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="ee2a4-162">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="2010-"></a><span data-ttu-id="ee2a4-163">20.10 ✔️</span><span class="sxs-lookup"><span data-stu-id="ee2a4-163">20.10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="ee2a4-164">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="ee2a4-164">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="ee2a4-165">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ee2a4-165">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="ee2a4-166">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="ee2a4-166">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="ee2a4-167">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ee2a4-167">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="ee2a4-168">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="ee2a4-168">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="ee2a4-169">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ee2a4-169">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="ee2a4-170">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="ee2a4-170">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="ee2a4-171">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ee2a4-171">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="ee2a4-172">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="ee2a4-172">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ee2a4-173">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="ee2a4-173">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="ee2a4-174">使用 APT 更新 .NET</span><span class="sxs-lookup"><span data-stu-id="ee2a4-174">Use APT to update .NET</span></span>

<span data-ttu-id="ee2a4-175">當 .NET 有新的修補程式版本時，您可以使用下列命令透過 APT 升級：</span><span class="sxs-lookup"><span data-stu-id="ee2a4-175">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="ee2a4-176">APT 疑難排解</span><span class="sxs-lookup"><span data-stu-id="ee2a4-176">APT troubleshooting</span></span>

<span data-ttu-id="ee2a4-177">本節提供使用 APT 來安裝 .NET 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-177">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="ee2a4-178">找不到套件</span><span class="sxs-lookup"><span data-stu-id="ee2a4-178">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="ee2a4-179">找不到 \\ 某些套件無法安裝</span><span class="sxs-lookup"><span data-stu-id="ee2a4-179">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="ee2a4-180">無法提取</span><span class="sxs-lookup"><span data-stu-id="ee2a4-180">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="ee2a4-181">相依性</span><span class="sxs-lookup"><span data-stu-id="ee2a4-181">Dependencies</span></span>

<span data-ttu-id="ee2a4-182">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-182">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="ee2a4-183">但是，如果您手動安裝 .NET 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="ee2a4-183">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="ee2a4-184">libc6</span><span class="sxs-lookup"><span data-stu-id="ee2a4-184">libc6</span></span>
- <span data-ttu-id="ee2a4-185">libgcc1</span><span class="sxs-lookup"><span data-stu-id="ee2a4-185">libgcc1</span></span>
- <span data-ttu-id="ee2a4-186">libgssapi-krb5.keytab-2</span><span class="sxs-lookup"><span data-stu-id="ee2a4-186">libgssapi-krb5-2</span></span>
- <span data-ttu-id="ee2a4-187">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-187">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="ee2a4-188">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-188">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="ee2a4-189">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="ee2a4-189">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="ee2a4-190">libicu66 (for 20. x) </span><span class="sxs-lookup"><span data-stu-id="ee2a4-190">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="ee2a4-191">libssl1.0.0 1.0.0 (，適用于 14. x、16. x) </span><span class="sxs-lookup"><span data-stu-id="ee2a4-191">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="ee2a4-192">libssl1.0.0 1.1 (，適用于6.x、20. x) </span><span class="sxs-lookup"><span data-stu-id="ee2a4-192">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="ee2a4-193">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="ee2a4-193">libstdc++6</span></span>
- <span data-ttu-id="ee2a4-194">zlib1g</span><span class="sxs-lookup"><span data-stu-id="ee2a4-194">zlib1g</span></span>

<span data-ttu-id="ee2a4-195">若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="ee2a4-195">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="ee2a4-196">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="ee2a4-196">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="ee2a4-197">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-197">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="ee2a4-198">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="ee2a4-198">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ee2a4-199">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ee2a4-199">Next steps</span></span>

- [<span data-ttu-id="ee2a4-200">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="ee2a4-200">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="ee2a4-201">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ee2a4-201">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
