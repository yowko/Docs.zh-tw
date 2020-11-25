---
title: 在 Fedora 上安裝 .NET-.NET
description: 示範在 Fedora 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f7422941af7e39d69d286a0f79920b025c1bf9c0
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031900"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="e175e-103">在 Fedora 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="e175e-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="e175e-104">Fedora 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="e175e-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="e175e-105">本文說明如何在 Fedora 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="e175e-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="e175e-106">當 Fedora 版本不受支援時，就不再支援該版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="e175e-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="e175e-107">不過，這些指示可協助您讓 .NET 在這些版本上執行，即使它不受支援也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e175e-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="e175e-108">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="e175e-108">Supported distributions</span></span>

<span data-ttu-id="e175e-109">下表列出目前支援的 .NET 版本，以及其支援的 Fedora 版本。</span><span class="sxs-lookup"><span data-stu-id="e175e-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="e175e-110">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或 Fedora 的版本 [達到生命週期結束](https://fedoraproject.org/wiki/End_of_life)，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="e175e-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="e175e-111">✔️表示仍支援 Fedora 或 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="e175e-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="e175e-112">❌指出該 Fedora 版本不支援 Fedora 或 .net 版本。</span><span class="sxs-lookup"><span data-stu-id="e175e-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="e175e-113">當版本的 Fedora 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="e175e-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="e175e-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="e175e-114">Fedora</span></span>               | <span data-ttu-id="e175e-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e175e-115">.NET Core 2.1</span></span> | <span data-ttu-id="e175e-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="e175e-116">.NET Core 3.1</span></span> | <span data-ttu-id="e175e-117">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="e175e-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="e175e-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="e175e-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="e175e-119">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e175e-119">✔️ 2.1</span></span>        | <span data-ttu-id="e175e-120">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="e175e-120">✔️ 3.1</span></span>        | <span data-ttu-id="e175e-121">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="e175e-121">✔️ 5.0</span></span> |
| <span data-ttu-id="e175e-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="e175e-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="e175e-123">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e175e-123">✔️ 2.1</span></span>        | <span data-ttu-id="e175e-124">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="e175e-124">✔️ 3.1</span></span>        | <span data-ttu-id="e175e-125">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="e175e-125">✔️ 5.0</span></span> |
| <span data-ttu-id="e175e-126">❌[31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="e175e-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="e175e-127">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e175e-127">✔️ 2.1</span></span>        | <span data-ttu-id="e175e-128">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="e175e-128">✔️ 3.1</span></span>        | <span data-ttu-id="e175e-129">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="e175e-129">❌ 5.0</span></span> |
| <span data-ttu-id="e175e-130">❌ [30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="e175e-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="e175e-131">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e175e-131">✔️ 2.1</span></span>        | <span data-ttu-id="e175e-132">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="e175e-132">✔️ 3.1</span></span>        | <span data-ttu-id="e175e-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="e175e-133">❌ 5.0</span></span> |
| <span data-ttu-id="e175e-134">❌[29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="e175e-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="e175e-135">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e175e-135">✔️ 2.1</span></span>        | <span data-ttu-id="e175e-136">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="e175e-136">✔️ 3.1</span></span>        | <span data-ttu-id="e175e-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="e175e-137">❌ 5.0</span></span> |
| <span data-ttu-id="e175e-138">❌[28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="e175e-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="e175e-139">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e175e-139">✔️ 2.1</span></span>        | <span data-ttu-id="e175e-140">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="e175e-140">❌ 3.1</span></span>        | <span data-ttu-id="e175e-141">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="e175e-141">❌ 5.0</span></span> |
| <span data-ttu-id="e175e-142">❌[27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="e175e-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="e175e-143">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="e175e-143">✔️ 2.1</span></span>        | <span data-ttu-id="e175e-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="e175e-144">❌ 3.1</span></span>        | <span data-ttu-id="e175e-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="e175e-145">❌ 5.0</span></span> |

<span data-ttu-id="e175e-146">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="e175e-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="e175e-147">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="e175e-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="e175e-148">3.0</span><span class="sxs-lookup"><span data-stu-id="e175e-148">3.0</span></span>
- <span data-ttu-id="e175e-149">2.2</span><span class="sxs-lookup"><span data-stu-id="e175e-149">2.2</span></span>
- <span data-ttu-id="e175e-150">2.0</span><span class="sxs-lookup"><span data-stu-id="e175e-150">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="e175e-151">移除預覽版本</span><span class="sxs-lookup"><span data-stu-id="e175e-151">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e175e-152">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="e175e-152">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="e175e-153">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="e175e-153">Fedora 33 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="e175e-154">Fedora 33 的預設套件存放庫中有提供 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="e175e-154">.NET Core 3.1 is available in the default package repositories for Fedora 33.</span></span> <span data-ttu-id="e175e-155">若要安裝 .NET Core 3.1，請使用 `dnf install` 命令搭配適當的封裝，例如 `aspnetcore-runtime-3.1` 或 `dotnet-sdk-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="e175e-155">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="e175e-156">預設套件存放庫中尚無法使用 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="e175e-156">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="e175e-157">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="e175e-157">Fedora 32 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="e175e-158">Fedora 32 的預設套件存放庫中有提供 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="e175e-158">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span> <span data-ttu-id="e175e-159">若要安裝 .NET Core 3.1，請使用 `dnf install` 命令搭配適當的封裝，例如 `aspnetcore-runtime-3.1` 或 `dotnet-sdk-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="e175e-159">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="e175e-160">預設套件存放庫中尚無法使用 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="e175e-160">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="e175e-161">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="e175e-161">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="e175e-162">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="e175e-162">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="e175e-163">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="e175e-163">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="e175e-164">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="e175e-164">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="e175e-165">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="e175e-165">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="e175e-166">針對套件管理員進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e175e-166">Troubleshoot the package manager</span></span>

<span data-ttu-id="e175e-167">本節提供使用套件管理員安裝 .NET Core 時，您可能會遇到的常見錯誤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e175e-167">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="e175e-168">找不到套件</span><span class="sxs-lookup"><span data-stu-id="e175e-168">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="e175e-169">無法提取</span><span class="sxs-lookup"><span data-stu-id="e175e-169">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="e175e-170">單元</span><span class="sxs-lookup"><span data-stu-id="e175e-170">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="e175e-171">相依性</span><span class="sxs-lookup"><span data-stu-id="e175e-171">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="e175e-172">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="e175e-172">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="e175e-173">手動安裝</span><span class="sxs-lookup"><span data-stu-id="e175e-173">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="e175e-174">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e175e-174">Next steps</span></span>

- [<span data-ttu-id="e175e-175">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e175e-175">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
