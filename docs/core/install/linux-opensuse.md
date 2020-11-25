---
title: 在 openSUSE 上安裝 .NET-.NET
description: 示範在 openSUSE 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: eb31e3109ccd40999c22a27607d48544bf117dc2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031861"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="e79e0-103">在 openSUSE 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="e79e0-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="e79e0-104">OpenSUSE 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="e79e0-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="e79e0-105">本文說明如何在 openSUSE 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="e79e0-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="e79e0-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="e79e0-106">Supported distributions</span></span>

<span data-ttu-id="e79e0-107">下表是 openSUSE 15 上目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="e79e0-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="e79e0-108">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 openSUSE 版本，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="e79e0-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="e79e0-109">✔️表示仍支援 openSUSE 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="e79e0-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="e79e0-110">❌指出該 openSUSE 版本不支援 openSUSE 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="e79e0-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="e79e0-111">當版本的 openSUSE 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="e79e0-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="e79e0-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e79e0-112">openSUSE</span></span>                   | <span data-ttu-id="e79e0-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e79e0-113">.NET Core 2.1</span></span> | <span data-ttu-id="e79e0-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="e79e0-114">.NET Core 3.1</span></span> | <span data-ttu-id="e79e0-115">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="e79e0-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="e79e0-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="e79e0-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="e79e0-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e79e0-117">✔️ 2.1</span></span>        | <span data-ttu-id="e79e0-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="e79e0-118">✔️ 3.1</span></span>        | <span data-ttu-id="e79e0-119">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="e79e0-119">✔️ 5.0</span></span> |

<span data-ttu-id="e79e0-120">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="e79e0-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="e79e0-121">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="e79e0-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="e79e0-122">3.0</span><span class="sxs-lookup"><span data-stu-id="e79e0-122">3.0</span></span>
- <span data-ttu-id="e79e0-123">2.2</span><span class="sxs-lookup"><span data-stu-id="e79e0-123">2.2</span></span>
- <span data-ttu-id="e79e0-124">2.0</span><span class="sxs-lookup"><span data-stu-id="e79e0-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="e79e0-125">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="e79e0-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e79e0-126">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="e79e0-126">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="e79e0-127">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="e79e0-127">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="e79e0-128">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e79e0-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="e79e0-129">本節提供使用套件管理員安裝 .NET 時可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e79e0-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="e79e0-130">找不到套件</span><span class="sxs-lookup"><span data-stu-id="e79e0-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="e79e0-131">無法提取</span><span class="sxs-lookup"><span data-stu-id="e79e0-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="e79e0-132">單元</span><span class="sxs-lookup"><span data-stu-id="e79e0-132">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="e79e0-133">相依性</span><span class="sxs-lookup"><span data-stu-id="e79e0-133">Dependencies</span></span>

<span data-ttu-id="e79e0-134">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="e79e0-134">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="e79e0-135">但是，如果您手動安裝 .NET 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="e79e0-135">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="e79e0-136">krb5</span><span class="sxs-lookup"><span data-stu-id="e79e0-136">krb5</span></span>
- <span data-ttu-id="e79e0-137">libicu</span><span class="sxs-lookup"><span data-stu-id="e79e0-137">libicu</span></span>
- <span data-ttu-id="e79e0-138">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="e79e0-138">libopenssl1_0_0</span></span>

<span data-ttu-id="e79e0-139">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您必須安裝 **相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="e79e0-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="e79e0-140">如需相依性的詳細資訊，請參閱 [獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="e79e0-140">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="e79e0-141">若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="e79e0-141">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="e79e0-142">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="e79e0-142">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="e79e0-143">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="e79e0-143">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="e79e0-144">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="e79e0-144">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="e79e0-145">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="e79e0-145">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="e79e0-146">手動安裝</span><span class="sxs-lookup"><span data-stu-id="e79e0-146">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="e79e0-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e79e0-147">Next steps</span></span>

- [<span data-ttu-id="e79e0-148">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e79e0-148">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
