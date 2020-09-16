---
title: 在 Ubuntu 上安裝 .NET Core-.NET Core
description: 示範在 Ubuntu 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 5c07de20110a1aecf2ec5cb9de88f204625e548d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538446"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="eb5ee-103">在 Ubuntu 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="eb5ee-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="eb5ee-104">Ubuntu 支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="eb5ee-105">本文說明如何在 Ubuntu 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="eb5ee-106">當 Ubuntu 版本不受支援時，就不再支援該版本的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="eb5ee-107">不過，這些指示可協助您讓 .NET Core 在這些版本上執行，即使它不受支援也是一樣。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="eb5ee-108">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="eb5ee-108">Supported distributions</span></span>

<span data-ttu-id="eb5ee-109">下表列出目前支援的 .NET Core 版本，以及支援的 Ubuntu 版本。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="eb5ee-110">在 [.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Ubuntu 的版本 [達到生命週期結束](https://wiki.ubuntu.com/Releases)之前，這些版本仍會受到支援。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="eb5ee-111">✔️表示仍支援 Ubuntu 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="eb5ee-112">❌表示該 ubuntu 版本不支援 ubuntu 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="eb5ee-113">當 Ubuntu 版本與 .NET Core 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="eb5ee-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="eb5ee-114">Ubuntu</span></span>                   | <span data-ttu-id="eb5ee-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-115">.NET Core 2.1</span></span> | <span data-ttu-id="eb5ee-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-116">.NET Core 3.1</span></span> | <span data-ttu-id="eb5ee-117">.NET 5 Preview (僅限手動安裝) </span><span class="sxs-lookup"><span data-stu-id="eb5ee-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="eb5ee-118">✔️ [20.04 (LTS) ](#2004-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="eb5ee-119">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-119">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-120">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-120">✔️ 3.1</span></span>        | <span data-ttu-id="eb5ee-121">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-122">❌[19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="eb5ee-123">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-123">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-124">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-124">✔️ 3.1</span></span>        | <span data-ttu-id="eb5ee-125">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-126">❌[19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="eb5ee-127">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-127">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-128">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-128">✔️ 3.1</span></span>        | <span data-ttu-id="eb5ee-129">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-130">❌[18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="eb5ee-131">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-131">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-132">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-132">❌ 3.1</span></span>        | <span data-ttu-id="eb5ee-133">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-134">✔️ [18.04 (LTS) ](#1804-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="eb5ee-135">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-135">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-136">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-136">✔️ 3.1</span></span>        | <span data-ttu-id="eb5ee-137">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-138">❌[17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="eb5ee-139">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-139">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-140">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-140">❌ 3.1</span></span>        | <span data-ttu-id="eb5ee-141">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-142">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="eb5ee-143">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-143">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-144">❌ 3.1</span></span>        | <span data-ttu-id="eb5ee-145">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-146">❌[16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="eb5ee-147">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-147">❌ 2.1</span></span>        | <span data-ttu-id="eb5ee-148">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-148">❌ 3.1</span></span>        | <span data-ttu-id="eb5ee-149">❌ 5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="eb5ee-150">✔️ [16.04 (LTS) ](#1604-)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="eb5ee-151">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-151">✔️ 2.1</span></span>        | <span data-ttu-id="eb5ee-152">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-152">✔️ 3.1</span></span>        | <span data-ttu-id="eb5ee-153">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="eb5ee-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="eb5ee-154">不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="eb5ee-155">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="eb5ee-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="eb5ee-156">3.0</span><span class="sxs-lookup"><span data-stu-id="eb5ee-156">3.0</span></span>
- <span data-ttu-id="eb5ee-157">2.2</span><span class="sxs-lookup"><span data-stu-id="eb5ee-157">2.2</span></span>
- <span data-ttu-id="eb5ee-158">2.0</span><span class="sxs-lookup"><span data-stu-id="eb5ee-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="eb5ee-159">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="eb5ee-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="eb5ee-160">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="eb5ee-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="eb5ee-161">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="eb5ee-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="eb5ee-162">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="eb5ee-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="eb5ee-163">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="eb5ee-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="eb5ee-164">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="eb5ee-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="eb5ee-165">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="eb5ee-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="eb5ee-166">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="eb5ee-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="eb5ee-167">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="eb5ee-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="eb5ee-168">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="eb5ee-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="eb5ee-169">APT 更新 SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="eb5ee-169">APT update SDK or runtime</span></span>

<span data-ttu-id="eb5ee-170">當 .NET Core 有新的修補程式版本可供使用時，您可以使用下列命令透過 APT 升級：</span><span class="sxs-lookup"><span data-stu-id="eb5ee-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="eb5ee-171">APT 疑難排解</span><span class="sxs-lookup"><span data-stu-id="eb5ee-171">APT troubleshooting</span></span>

<span data-ttu-id="eb5ee-172">本節提供使用 APT 來安裝 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="eb5ee-173">找不到套件</span><span class="sxs-lookup"><span data-stu-id="eb5ee-173">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="eb5ee-174">找不到 \\ 某些套件無法安裝</span><span class="sxs-lookup"><span data-stu-id="eb5ee-174">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="eb5ee-175">無法提取</span><span class="sxs-lookup"><span data-stu-id="eb5ee-175">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="eb5ee-176">單元</span><span class="sxs-lookup"><span data-stu-id="eb5ee-176">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="eb5ee-177">相依性</span><span class="sxs-lookup"><span data-stu-id="eb5ee-177">Dependencies</span></span>

<span data-ttu-id="eb5ee-178">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-178">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="eb5ee-179">但是，如果您手動安裝 .NET Core 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="eb5ee-179">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="eb5ee-180">libc6</span><span class="sxs-lookup"><span data-stu-id="eb5ee-180">libc6</span></span>
- <span data-ttu-id="eb5ee-181">libgcc1</span><span class="sxs-lookup"><span data-stu-id="eb5ee-181">libgcc1</span></span>
- <span data-ttu-id="eb5ee-182">libgssapi-krb5.keytab-2</span><span class="sxs-lookup"><span data-stu-id="eb5ee-182">libgssapi-krb5-2</span></span>
- <span data-ttu-id="eb5ee-183">libicu52 (適用於 14.x)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-183">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="eb5ee-184">libicu55 (適用於 16.x)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-184">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="eb5ee-185">libicu60 (適用於 18.x)</span><span class="sxs-lookup"><span data-stu-id="eb5ee-185">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="eb5ee-186">libicu66 (for 20. x) </span><span class="sxs-lookup"><span data-stu-id="eb5ee-186">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="eb5ee-187">libssl1.0.0 1.0.0 (，適用于 14. x、16. x) </span><span class="sxs-lookup"><span data-stu-id="eb5ee-187">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="eb5ee-188">libssl1.0.0 1.1 (，適用于6.x、20. x) </span><span class="sxs-lookup"><span data-stu-id="eb5ee-188">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="eb5ee-189">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="eb5ee-189">libstdc++6</span></span>
- <span data-ttu-id="eb5ee-190">zlib1g</span><span class="sxs-lookup"><span data-stu-id="eb5ee-190">zlib1g</span></span>

<span data-ttu-id="eb5ee-191">若為使用 system.string 元件的 .NET Core *應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="eb5ee-191">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="eb5ee-192">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="eb5ee-192">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="eb5ee-193">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-193">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="eb5ee-194">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="eb5ee-194">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="eb5ee-195">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="eb5ee-195">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="eb5ee-196">手動安裝</span><span class="sxs-lookup"><span data-stu-id="eb5ee-196">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="eb5ee-197">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eb5ee-197">Next steps</span></span>

- [<span data-ttu-id="eb5ee-198">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="eb5ee-198">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
