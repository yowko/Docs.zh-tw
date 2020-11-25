---
title: 在 SLES 上安裝 .NET-.NET
description: 示範在 SLES 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f351a9b11ab16910963a1db88d88b6949b56ae11
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031796"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a><span data-ttu-id="1fe60-103">在 SLES 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="1fe60-103">Install the .NET SDK or the .NET Runtime on SLES</span></span>

<span data-ttu-id="1fe60-104">SLES 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="1fe60-104">.NET is supported on SLES.</span></span> <span data-ttu-id="1fe60-105">本文說明如何在 SLES 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="1fe60-105">This article describes how to install .NET on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="1fe60-106">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="1fe60-106">Supported distributions</span></span>

<span data-ttu-id="1fe60-107">下表是 SLES 12 SP2 和 SLES 15 目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="1fe60-107">The following table is a list of currently supported .NET releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="1fe60-108">在 [.net 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或不再支援 SLES 版本之前，會持續支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="1fe60-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="1fe60-109">✔️表示仍支援 SLES 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="1fe60-109">A ✔️ indicates that the version of SLES or .NET is still supported.</span></span>
- <span data-ttu-id="1fe60-110">❌表示該 sles 版本不支援 sles 或 .net 的版本。</span><span class="sxs-lookup"><span data-stu-id="1fe60-110">A ❌ indicates that the version of SLES or .NET isn't supported on that SLES release.</span></span>
- <span data-ttu-id="1fe60-111">當 SLES 和某個版本的 .NET 都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="1fe60-111">When both a version of SLES and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="1fe60-112">SLES</span><span class="sxs-lookup"><span data-stu-id="1fe60-112">SLES</span></span>                   | <span data-ttu-id="1fe60-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1fe60-113">.NET Core 2.1</span></span> | <span data-ttu-id="1fe60-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1fe60-114">.NET Core 3.1</span></span> | <span data-ttu-id="1fe60-115">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="1fe60-115">.NET 5.0</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="1fe60-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="1fe60-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="1fe60-117">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="1fe60-117">✔️ 2.1</span></span>        | <span data-ttu-id="1fe60-118">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="1fe60-118">✔️ 3.1</span></span>        | <span data-ttu-id="1fe60-119">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="1fe60-119">✔️ 5.0</span></span> |
| <span data-ttu-id="1fe60-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="1fe60-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="1fe60-121">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="1fe60-121">✔️ 2.1</span></span>        | <span data-ttu-id="1fe60-122">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="1fe60-122">✔️ 3.1</span></span>        | <span data-ttu-id="1fe60-123">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="1fe60-123">✔️ 5.0</span></span> |

<span data-ttu-id="1fe60-124">不再支援下列 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="1fe60-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="1fe60-125">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="1fe60-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1fe60-126">3.0</span><span class="sxs-lookup"><span data-stu-id="1fe60-126">3.0</span></span>
- <span data-ttu-id="1fe60-127">2.2</span><span class="sxs-lookup"><span data-stu-id="1fe60-127">2.2</span></span>
- <span data-ttu-id="1fe60-128">2.0</span><span class="sxs-lookup"><span data-stu-id="1fe60-128">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="1fe60-129">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="1fe60-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1fe60-130">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="1fe60-130">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="1fe60-131">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="1fe60-131">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="1fe60-132">目前，SLES 15 Microsoft 存放庫安裝套件會將 *Microsoft 生產* 的存放庫檔案安裝到錯誤的目錄，防止 zypper 找到 .net 套件。</span><span class="sxs-lookup"><span data-stu-id="1fe60-132">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET packages.</span></span> <span data-ttu-id="1fe60-133">若要修正此問題，請在正確的目錄中建立符號。</span><span class="sxs-lookup"><span data-stu-id="1fe60-133">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="1fe60-134">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="1fe60-134">SLES 12 ✔️</span></span>

<span data-ttu-id="1fe60-135">.NET 需要 SP2 作為 SLES 12 系列的最小值。</span><span class="sxs-lookup"><span data-stu-id="1fe60-135">.NET requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="1fe60-136">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1fe60-136">Troubleshoot the package manager</span></span>

<span data-ttu-id="1fe60-137">本節提供使用套件管理員安裝 .NET 時可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1fe60-137">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="1fe60-138">無法提取</span><span class="sxs-lookup"><span data-stu-id="1fe60-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="1fe60-139">相依性</span><span class="sxs-lookup"><span data-stu-id="1fe60-139">Dependencies</span></span>

<span data-ttu-id="1fe60-140">當您使用套件管理員進行安裝時，系統會為您安裝這些程式庫。</span><span class="sxs-lookup"><span data-stu-id="1fe60-140">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="1fe60-141">但是，如果您手動安裝 .NET 或發行獨立應用程式，則必須確定已安裝這些程式庫：</span><span class="sxs-lookup"><span data-stu-id="1fe60-141">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="1fe60-142">krb5</span><span class="sxs-lookup"><span data-stu-id="1fe60-142">krb5</span></span>
- <span data-ttu-id="1fe60-143">libicu</span><span class="sxs-lookup"><span data-stu-id="1fe60-143">libicu</span></span>
- <span data-ttu-id="1fe60-144">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="1fe60-144">libopenssl1_1</span></span>

<span data-ttu-id="1fe60-145">如果目標執行時間環境的 OpenSSL 版本是1.1 或更新版本，您必須安裝 **相容性 compat-openssl10**。</span><span class="sxs-lookup"><span data-stu-id="1fe60-145">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="1fe60-146">如需相依性的詳細資訊，請參閱 [獨立的 Linux 應用程式](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="1fe60-146">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="1fe60-147">若為使用 *system.string 元件的 .net 應用程式，* 您也需要下列相依性：</span><span class="sxs-lookup"><span data-stu-id="1fe60-147">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="1fe60-148">libgdiplus (6.0.1 版或更新版本) </span><span class="sxs-lookup"><span data-stu-id="1fe60-148">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="1fe60-149">您可以藉由將 Mono 存放庫新增至您的系統，來安裝最新版本的 *libgdiplus* 。</span><span class="sxs-lookup"><span data-stu-id="1fe60-149">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="1fe60-150">如需詳細資訊，請參閱<https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="1fe60-150">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="1fe60-151">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="1fe60-151">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="1fe60-152">手動安裝</span><span class="sxs-lookup"><span data-stu-id="1fe60-152">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="1fe60-153">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1fe60-153">Next steps</span></span>

- [<span data-ttu-id="1fe60-154">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1fe60-154">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
