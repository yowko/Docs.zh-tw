---
title: 在 Fedora 上安裝 .NET-.NET
description: 示範在 Fedora 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9dd8c6264831e2a9382960be505639f1eba95151
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970820"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="db12d-103">在 Fedora 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="db12d-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="db12d-104">Fedora 支援 .NET，本文說明如何在 Fedora 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="db12d-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="db12d-105">當 Fedora 版本不受支援時，就不再支援該版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="db12d-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="install-net-50"></a><span data-ttu-id="db12d-106">安裝 .NET 5。0</span><span class="sxs-lookup"><span data-stu-id="db12d-106">Install .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="db12d-107">**Fedora 32**</span><span class="sxs-lookup"><span data-stu-id="db12d-107">**Fedora 32**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

<span data-ttu-id="db12d-108">**Fedora 33**</span><span class="sxs-lookup"><span data-stu-id="db12d-108">**Fedora 33**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="db12d-109">安裝 .NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="db12d-109">Install .NET Core 3.1</span></span>

<span data-ttu-id="db12d-110">適用于 Fedora 的預設封裝存放庫中提供的最新 .NET 版本是 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="db12d-110">The latest version of .NET available in the default package repositories for Fedora is .NET Core 3.1.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="db12d-111">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="db12d-111">Supported distributions</span></span>

<span data-ttu-id="db12d-112">下表列出目前支援的 .NET 版本，以及其支援的 Fedora 版本。</span><span class="sxs-lookup"><span data-stu-id="db12d-112">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="db12d-113">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Fedora 的版本 [達到生命週期結束](https://fedoraproject.org/wiki/End_of_life)，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="db12d-113">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="db12d-114">✔️表示仍支援 Fedora 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="db12d-114">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="db12d-115">❌指出該 Fedora 版本不支援 Fedora 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="db12d-115">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="db12d-116">當版本的 Fedora 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="db12d-116">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="db12d-117">.NET 版本</span><span class="sxs-lookup"><span data-stu-id="db12d-117">.NET Version</span></span>  | <span data-ttu-id="db12d-118">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-118">Fedora 33 ✔️</span></span> | <span data-ttu-id="db12d-119">32✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-119">32 ✔️</span></span> | <span data-ttu-id="db12d-120">31 ❌</span><span class="sxs-lookup"><span data-stu-id="db12d-120">31 ❌</span></span> | <span data-ttu-id="db12d-121">30 ❌</span><span class="sxs-lookup"><span data-stu-id="db12d-121">30 ❌</span></span> | <span data-ttu-id="db12d-122">29 ❌</span><span class="sxs-lookup"><span data-stu-id="db12d-122">29 ❌</span></span> | <span data-ttu-id="db12d-123">日 ❌</span><span class="sxs-lookup"><span data-stu-id="db12d-123">28 ❌</span></span> | <span data-ttu-id="db12d-124">27 ❌</span><span class="sxs-lookup"><span data-stu-id="db12d-124">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="db12d-125">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="db12d-125">.NET 5.0</span></span>      | <span data-ttu-id="db12d-126">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-126">✔️</span></span>        | <span data-ttu-id="db12d-127">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-127">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="db12d-128">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="db12d-128">.NET Core 3.1</span></span> | <span data-ttu-id="db12d-129">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-129">✔️</span></span>        | <span data-ttu-id="db12d-130">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-130">✔️</span></span> | <span data-ttu-id="db12d-131">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-131">✔️</span></span>|<span data-ttu-id="db12d-132">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-132">✔️</span></span> |<span data-ttu-id="db12d-133">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-133">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="db12d-134">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="db12d-134">.NET Core 2.1</span></span> | <span data-ttu-id="db12d-135">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-135">✔️</span></span>        | <span data-ttu-id="db12d-136">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-136">✔️</span></span> | <span data-ttu-id="db12d-137">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-137">✔️</span></span>|<span data-ttu-id="db12d-138">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-138">✔️</span></span> |<span data-ttu-id="db12d-139">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-139">✔️</span></span> |<span data-ttu-id="db12d-140">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-140">✔️</span></span>  |<span data-ttu-id="db12d-141">✔️</span><span class="sxs-lookup"><span data-stu-id="db12d-141">✔️</span></span> |

<span data-ttu-id="db12d-142">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="db12d-142">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="db12d-143">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="db12d-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="db12d-144">3.0</span><span class="sxs-lookup"><span data-stu-id="db12d-144">3.0</span></span>
- <span data-ttu-id="db12d-145">2.2</span><span class="sxs-lookup"><span data-stu-id="db12d-145">2.2</span></span>
- <span data-ttu-id="db12d-146">2.0</span><span class="sxs-lookup"><span data-stu-id="db12d-146">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="db12d-147">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="db12d-147">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="db12d-148">相依性</span><span class="sxs-lookup"><span data-stu-id="db12d-148">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="db12d-149">在較舊的發行版本上安裝</span><span class="sxs-lookup"><span data-stu-id="db12d-149">Install on older distributions</span></span>

<span data-ttu-id="db12d-150">舊版的 Fedora 在預設封裝存放庫中不會包含 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="db12d-150">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="db12d-151">您可以使用 [[貼齊](linux-snap.md)]、 [ _DOTNET-INSTALL.SH_ 腳本](linux-scripted-manual.md#scripted-install)來安裝 .net，或使用 Microsoft 的存放庫來安裝 .net：</span><span class="sxs-lookup"><span data-stu-id="db12d-151">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="db12d-152">首先，將 Microsoft 簽署金鑰新增至您的受信賴起點清單。</span><span class="sxs-lookup"><span data-stu-id="db12d-152">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="db12d-153">接下來，新增 Microsoft 套件存放庫。</span><span class="sxs-lookup"><span data-stu-id="db12d-153">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="db12d-154">存放庫的來源是以您的 Fedora 版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="db12d-154">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="db12d-155">Fedora 版本</span><span class="sxs-lookup"><span data-stu-id="db12d-155">Fedora Version</span></span> | <span data-ttu-id="db12d-156">套件存放庫</span><span class="sxs-lookup"><span data-stu-id="db12d-156">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="db12d-157">31</span><span class="sxs-lookup"><span data-stu-id="db12d-157">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="db12d-158">30</span><span class="sxs-lookup"><span data-stu-id="db12d-158">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="db12d-159">29</span><span class="sxs-lookup"><span data-stu-id="db12d-159">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="db12d-160">28</span><span class="sxs-lookup"><span data-stu-id="db12d-160">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="db12d-161">27</span><span class="sxs-lookup"><span data-stu-id="db12d-161">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="db12d-162">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="db12d-162">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="db12d-163">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="db12d-163">Troubleshoot the package manager</span></span>

<span data-ttu-id="db12d-164">本節提供使用套件管理員來安裝 .NET 或 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="db12d-164">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="db12d-165">找不到套件</span><span class="sxs-lookup"><span data-stu-id="db12d-165">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="db12d-166">無法提取</span><span class="sxs-lookup"><span data-stu-id="db12d-166">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="db12d-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="db12d-167">Next steps</span></span>

- [<span data-ttu-id="db12d-168">如何啟用 .NET CLI 的 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="db12d-168">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="db12d-169">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="db12d-169">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
