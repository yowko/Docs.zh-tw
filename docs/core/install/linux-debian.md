---
title: 在 Debian 上安裝 .NET-.NET
description: 示範在 Debian 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 913d8bffdd6c0b5e88a70dae0ec4c8d732e80cc0
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970833"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="180bd-103">在 Debian 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="180bd-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="180bd-104">本文說明如何在 Debian 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="180bd-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="180bd-105">當 Debian 版本不受支援時，就不再支援該版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="180bd-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="180bd-106">不過，這些指示可協助您讓 .NET 在這些版本上執行，即使它不受支援也是一樣。</span><span class="sxs-lookup"><span data-stu-id="180bd-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="180bd-107">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="180bd-107">Supported distributions</span></span>

<span data-ttu-id="180bd-108">下表列出目前支援的 .NET 版本，以及其支援的 Debian 版本。</span><span class="sxs-lookup"><span data-stu-id="180bd-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="180bd-109">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Debian 的版本 [達到生命週期結束](https://wiki.debian.org/DebianReleases)，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="180bd-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="180bd-110">✔️表示仍支援 Debian 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="180bd-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="180bd-111">❌指出該 Debian 版本不支援 Debian 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="180bd-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="180bd-112">當版本的 Debian 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="180bd-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="180bd-113">Debian</span><span class="sxs-lookup"><span data-stu-id="180bd-113">Debian</span></span>                   | <span data-ttu-id="180bd-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="180bd-114">.NET Core 2.1</span></span> | <span data-ttu-id="180bd-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="180bd-115">.NET Core 3.1</span></span> | <span data-ttu-id="180bd-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="180bd-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="180bd-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="180bd-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="180bd-118">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="180bd-118">✔️ 2.1</span></span>        | <span data-ttu-id="180bd-119">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="180bd-119">✔️ 3.1</span></span>        | <span data-ttu-id="180bd-120">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="180bd-120">✔️ 5.0</span></span> |
| <span data-ttu-id="180bd-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="180bd-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="180bd-122">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="180bd-122">✔️ 2.1</span></span>        | <span data-ttu-id="180bd-123">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="180bd-123">✔️ 3.1</span></span>        | <span data-ttu-id="180bd-124">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="180bd-124">✔️ 5.0</span></span> |
| <span data-ttu-id="180bd-125">❌[8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="180bd-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="180bd-126">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="180bd-126">✔️ 2.1</span></span>        | <span data-ttu-id="180bd-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="180bd-127">❌ 3.1</span></span>        | <span data-ttu-id="180bd-128">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="180bd-128">❌ 5.0</span></span> |

<span data-ttu-id="180bd-129">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="180bd-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="180bd-130">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="180bd-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="180bd-131">3.0</span><span class="sxs-lookup"><span data-stu-id="180bd-131">3.0</span></span>
- <span data-ttu-id="180bd-132">2.2</span><span class="sxs-lookup"><span data-stu-id="180bd-132">2.2</span></span>
- <span data-ttu-id="180bd-133">2.0</span><span class="sxs-lookup"><span data-stu-id="180bd-133">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="180bd-134">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="180bd-134">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="debian-10-"></a><span data-ttu-id="180bd-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="180bd-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="180bd-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="180bd-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="180bd-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="180bd-137">Debian 8 ❌</span></span>

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

## <a name="how-to-install-other-versions"></a><span data-ttu-id="180bd-138">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="180bd-138">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="180bd-139">使用 APT 更新 .NET</span><span class="sxs-lookup"><span data-stu-id="180bd-139">Use APT to update .NET</span></span>

<span data-ttu-id="180bd-140">當 .NET 有新的修補程式版本時，您可以使用下列命令透過 APT 升級：</span><span class="sxs-lookup"><span data-stu-id="180bd-140">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="180bd-141">APT 疑難排解</span><span class="sxs-lookup"><span data-stu-id="180bd-141">APT troubleshooting</span></span>

<span data-ttu-id="180bd-142">本節提供使用 APT 來安裝 .NET 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="180bd-142">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="180bd-143">找不到套件</span><span class="sxs-lookup"><span data-stu-id="180bd-143">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="180bd-144">找不到 \\ 某些套件無法安裝</span><span class="sxs-lookup"><span data-stu-id="180bd-144">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="180bd-145">無法提取</span><span class="sxs-lookup"><span data-stu-id="180bd-145">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="180bd-146">相依性</span><span class="sxs-lookup"><span data-stu-id="180bd-146">Dependencies</span></span>

<span data-ttu-id="180bd-147">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="180bd-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="180bd-148">但是，如果您手動安裝 .NET Core 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="180bd-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="180bd-149">libc6</span><span class="sxs-lookup"><span data-stu-id="180bd-149">libc6</span></span>
- <span data-ttu-id="180bd-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="180bd-150">libgcc1</span></span>
- <span data-ttu-id="180bd-151">libgssapi-krb5.keytab-2</span><span class="sxs-lookup"><span data-stu-id="180bd-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="180bd-152">適用于 8.x) 的 libicu52 (</span><span class="sxs-lookup"><span data-stu-id="180bd-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="180bd-153">libicu57 (for 2.x) </span><span class="sxs-lookup"><span data-stu-id="180bd-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="180bd-154">libicu63 (for 2.x) </span><span class="sxs-lookup"><span data-stu-id="180bd-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="180bd-155">適用于 11. x) 的 libicu67 (</span><span class="sxs-lookup"><span data-stu-id="180bd-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="180bd-156">適用于 8.x) 的 libssl1.0.0 1.0.0 (</span><span class="sxs-lookup"><span data-stu-id="180bd-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="180bd-157">libssl1.0.0 1.1 (for 2.x-11. x) </span><span class="sxs-lookup"><span data-stu-id="180bd-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="180bd-158">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="180bd-158">libstdc++6</span></span>
- <span data-ttu-id="180bd-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="180bd-159">zlib1g</span></span>

<span data-ttu-id="180bd-160">若為使用 system.string 元件的 .NET Core *應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="180bd-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="180bd-161">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="180bd-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="180bd-162">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="180bd-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="180bd-163">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="180bd-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="180bd-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="180bd-164">Next steps</span></span>

- [<span data-ttu-id="180bd-165">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="180bd-165">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="180bd-166">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="180bd-166">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
