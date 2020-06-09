---
title: 在 Debian 上安裝 .NET Core-.NET Core
description: 示範在 Debian 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c66d8e1daad4e59a766781b7117600352879b724
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603052"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="6f751-103">在 Debian 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="6f751-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="6f751-104">本文說明如何在 Debian 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="6f751-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="6f751-105">當 Debian 版本不支援時，該版本就不再支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="6f751-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="6f751-106">不過，這些指示可以協助您取得在這些版本上執行的 .NET Core，即使它不受支援也一樣。</span><span class="sxs-lookup"><span data-stu-id="6f751-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="6f751-107">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="6f751-107">Supported distributions</span></span>

<span data-ttu-id="6f751-108">下表列出目前支援的 .NET Core 版本，以及支援的 Debian 版本。</span><span class="sxs-lookup"><span data-stu-id="6f751-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="6f751-109">在[.Net Core 版本達到支援終止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，或[Debian 版本達到生命週期結束](https://wiki.debian.org/DebianReleases)之前，這些版本仍受到支援。</span><span class="sxs-lookup"><span data-stu-id="6f751-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="6f751-110">✔️表示仍然支援 Debian 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="6f751-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="6f751-111">A ❌ 表示該 Debian 版本不支援 Debian 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="6f751-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="6f751-112">當 Debian 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="6f751-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="6f751-113">Debian</span><span class="sxs-lookup"><span data-stu-id="6f751-113">Debian</span></span>                   | <span data-ttu-id="6f751-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6f751-114">.NET Core 2.1</span></span> | <span data-ttu-id="6f751-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6f751-115">.NET Core 3.1</span></span> | <span data-ttu-id="6f751-116">.NET 5 Preview （僅限手動安裝）</span><span class="sxs-lookup"><span data-stu-id="6f751-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="6f751-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="6f751-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="6f751-118">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="6f751-118">✔️ 2.1</span></span>        | <span data-ttu-id="6f751-119">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="6f751-119">✔️ 3.1</span></span>        | <span data-ttu-id="6f751-120">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="6f751-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="6f751-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="6f751-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="6f751-122">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="6f751-122">✔️ 2.1</span></span>        | <span data-ttu-id="6f751-123">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="6f751-123">✔️ 3.1</span></span>        | <span data-ttu-id="6f751-124">✔️ 5.0 Preview</span><span class="sxs-lookup"><span data-stu-id="6f751-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="6f751-125">❌[8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="6f751-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="6f751-126">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="6f751-126">✔️ 2.1</span></span>        | <span data-ttu-id="6f751-127">❌3.1</span><span class="sxs-lookup"><span data-stu-id="6f751-127">❌ 3.1</span></span>        | <span data-ttu-id="6f751-128">❌5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="6f751-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="6f751-129">已不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="6f751-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="6f751-130">這些下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="6f751-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="6f751-131">3.0</span><span class="sxs-lookup"><span data-stu-id="6f751-131">3.0</span></span>
- <span data-ttu-id="6f751-132">2.2</span><span class="sxs-lookup"><span data-stu-id="6f751-132">2.2</span></span>
- <span data-ttu-id="6f751-133">2.0</span><span class="sxs-lookup"><span data-stu-id="6f751-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="6f751-134">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="6f751-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="6f751-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="6f751-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="6f751-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="6f751-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="6f751-137">Debian 8❌</span><span class="sxs-lookup"><span data-stu-id="6f751-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="6f751-138">APT 更新 SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="6f751-138">APT update SDK or runtime</span></span>

<span data-ttu-id="6f751-139">當 .NET Core 有新的修補程式版本可供使用時，您只要使用下列命令，即可透過 APT 進行升級：</span><span class="sxs-lookup"><span data-stu-id="6f751-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="6f751-140">APT 疑難排解</span><span class="sxs-lookup"><span data-stu-id="6f751-140">APT troubleshooting</span></span>

<span data-ttu-id="6f751-141">本節提供您在使用 APT 安裝 .NET Core 時可能會遇到的常見錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="6f751-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="6f751-142">找不到</span><span class="sxs-lookup"><span data-stu-id="6f751-142">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="6f751-143">無法提取</span><span class="sxs-lookup"><span data-stu-id="6f751-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="6f751-144">抓取</span><span class="sxs-lookup"><span data-stu-id="6f751-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="6f751-145">相依性</span><span class="sxs-lookup"><span data-stu-id="6f751-145">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="6f751-146">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="6f751-146">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="6f751-147">手動安裝</span><span class="sxs-lookup"><span data-stu-id="6f751-147">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="6f751-148">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6f751-148">Next steps</span></span>

- [<span data-ttu-id="6f751-149">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="6f751-149">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
