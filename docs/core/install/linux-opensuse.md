---
title: 在 openSUSE 上安裝 .NET Core-.NET Core
description: 示範在 openSUSE 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: ccdb23ca1838d2c15c9a95b45c8505efe7a6df0e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539226"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="7a2bf-103">在 openSUSE 上安裝 .NET Core SDK 或 .NET Core 執行時間</span><span class="sxs-lookup"><span data-stu-id="7a2bf-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="7a2bf-104">OpenSUSE 支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="7a2bf-105">本文說明如何在 openSUSE 上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="7a2bf-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="7a2bf-106">Supported distributions</span></span>

<span data-ttu-id="7a2bf-107">下表是 openSUSE 15 上目前支援的 .NET Core 版本清單。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="7a2bf-108">在 [.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 openSUSE 版本之前，會持續支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="7a2bf-109">✔️表示仍支援 openSUSE 或 .NET Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="7a2bf-110">❌指出該 openSUSE 版本不支援 openSUSE 或 .Net Core 的版本。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="7a2bf-111">當版本的 openSUSE 和 .NET Core 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="7a2bf-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7a2bf-112">openSUSE</span></span>                   | <span data-ttu-id="7a2bf-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7a2bf-113">.NET Core 2.1</span></span> | <span data-ttu-id="7a2bf-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7a2bf-114">.NET Core 3.1</span></span> | <span data-ttu-id="7a2bf-115">.NET 5 Preview (僅限手動安裝) </span><span class="sxs-lookup"><span data-stu-id="7a2bf-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="7a2bf-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="7a2bf-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="7a2bf-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="7a2bf-117">✔️ 2.1</span></span>        | <span data-ttu-id="7a2bf-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="7a2bf-118">✔️ 3.1</span></span>        | <span data-ttu-id="7a2bf-119">✔️5.0 預覽</span><span class="sxs-lookup"><span data-stu-id="7a2bf-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="7a2bf-120">不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="7a2bf-121">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="7a2bf-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="7a2bf-122">3.0</span><span class="sxs-lookup"><span data-stu-id="7a2bf-122">3.0</span></span>
- <span data-ttu-id="7a2bf-123">2.2</span><span class="sxs-lookup"><span data-stu-id="7a2bf-123">2.2</span></span>
- <span data-ttu-id="7a2bf-124">2.0</span><span class="sxs-lookup"><span data-stu-id="7a2bf-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7a2bf-125">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="7a2bf-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="7a2bf-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="7a2bf-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="7a2bf-127">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7a2bf-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="7a2bf-128">本節提供使用套件管理員安裝 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="7a2bf-129">找不到套件</span><span class="sxs-lookup"><span data-stu-id="7a2bf-129">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="7a2bf-130">無法提取</span><span class="sxs-lookup"><span data-stu-id="7a2bf-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="7a2bf-131">單元</span><span class="sxs-lookup"><span data-stu-id="7a2bf-131">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="7a2bf-132">相依性</span><span class="sxs-lookup"><span data-stu-id="7a2bf-132">Dependencies</span></span>

<span data-ttu-id="7a2bf-133">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="7a2bf-134">但是，如果您手動安裝 .NET Core 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="7a2bf-134">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="7a2bf-135">krb5</span><span class="sxs-lookup"><span data-stu-id="7a2bf-135">krb5</span></span>
- <span data-ttu-id="7a2bf-136">libicu</span><span class="sxs-lookup"><span data-stu-id="7a2bf-136">libicu</span></span>
- <span data-ttu-id="7a2bf-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="7a2bf-137">libopenssl1_0_0</span></span>

<span data-ttu-id="7a2bf-138">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您必須安裝 **相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="7a2bf-139">如需相依性的詳細資訊，請參閱 [獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="7a2bf-140">若為使用 system.string 元件的 .NET Core *應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="7a2bf-140">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="7a2bf-141">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="7a2bf-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="7a2bf-142">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="7a2bf-143">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="7a2bf-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="7a2bf-144">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="7a2bf-144">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="7a2bf-145">手動安裝</span><span class="sxs-lookup"><span data-stu-id="7a2bf-145">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="7a2bf-146">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7a2bf-146">Next steps</span></span>

- [<span data-ttu-id="7a2bf-147">教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="7a2bf-147">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
