---
title: 在 openSUSE 上安裝 .NET-.NET
description: 示範在 openSUSE 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7a519f19f708e1f12af1e9715bad4f38a607f9c3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970807"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="96e41-103">在 openSUSE 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="96e41-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="96e41-104">OpenSUSE 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="96e41-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="96e41-105">本文說明如何在 openSUSE 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="96e41-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="96e41-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="96e41-106">Supported distributions</span></span>

<span data-ttu-id="96e41-107">下表是 openSUSE 15 上目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="96e41-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="96e41-108">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 openSUSE 版本，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="96e41-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="96e41-109">✔️表示仍支援 openSUSE 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="96e41-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="96e41-110">❌指出該 openSUSE 版本不支援 openSUSE 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="96e41-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="96e41-111">當版本的 openSUSE 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="96e41-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="96e41-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="96e41-112">openSUSE</span></span>                   | <span data-ttu-id="96e41-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="96e41-113">.NET Core 2.1</span></span> | <span data-ttu-id="96e41-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="96e41-114">.NET Core 3.1</span></span> | <span data-ttu-id="96e41-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="96e41-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="96e41-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="96e41-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="96e41-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="96e41-117">✔️ 2.1</span></span>        | <span data-ttu-id="96e41-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="96e41-118">✔️ 3.1</span></span>        | <span data-ttu-id="96e41-119">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="96e41-119">✔️ 5.0</span></span> |

<span data-ttu-id="96e41-120">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="96e41-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="96e41-121">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="96e41-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="96e41-122">3.0</span><span class="sxs-lookup"><span data-stu-id="96e41-122">3.0</span></span>
- <span data-ttu-id="96e41-123">2.2</span><span class="sxs-lookup"><span data-stu-id="96e41-123">2.2</span></span>
- <span data-ttu-id="96e41-124">2.0</span><span class="sxs-lookup"><span data-stu-id="96e41-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="96e41-125">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="96e41-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="96e41-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="96e41-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="96e41-127">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="96e41-127">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="96e41-128">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="96e41-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="96e41-129">本節提供使用套件管理員安裝 .NET 時可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="96e41-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="96e41-130">找不到套件</span><span class="sxs-lookup"><span data-stu-id="96e41-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="96e41-131">無法提取</span><span class="sxs-lookup"><span data-stu-id="96e41-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="96e41-132">相依性</span><span class="sxs-lookup"><span data-stu-id="96e41-132">Dependencies</span></span>

<span data-ttu-id="96e41-133">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="96e41-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="96e41-134">但是，如果您手動安裝 .NET 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="96e41-134">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="96e41-135">krb5</span><span class="sxs-lookup"><span data-stu-id="96e41-135">krb5</span></span>
- <span data-ttu-id="96e41-136">libicu</span><span class="sxs-lookup"><span data-stu-id="96e41-136">libicu</span></span>
- <span data-ttu-id="96e41-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="96e41-137">libopenssl1_0_0</span></span>

<span data-ttu-id="96e41-138">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您必須安裝 **相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="96e41-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="96e41-139">如需相依性的詳細資訊，請參閱 [獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="96e41-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="96e41-140">若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="96e41-140">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="96e41-141">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="96e41-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="96e41-142">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="96e41-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="96e41-143">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="96e41-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="96e41-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="96e41-144">Next steps</span></span>

- [<span data-ttu-id="96e41-145">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="96e41-145">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="96e41-146">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="96e41-146">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
