---
title: 在 RHEL 上安裝 .NET-.NET
description: 示範在 RHEL 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: cb03f84cf84557d467f0a067b8d5629a843ec7e3
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594566"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="a39b9-103">在 RHEL 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="a39b9-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="a39b9-104">RHEL 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="a39b9-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="a39b9-105">本文說明如何在 RHEL 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="a39b9-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="a39b9-106">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="a39b9-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="a39b9-107">若要在 RHEL 上從 Red Hat 安裝 .NET，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="a39b9-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="a39b9-108">如果未在您的系統上完成此操作，或如果您不確定，請參閱 [.net 的 Red Hat 產品檔](https://access.redhat.com/documentation/net/5.0/)。</span><span class="sxs-lookup"><span data-stu-id="a39b9-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="a39b9-109">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="a39b9-109">Supported distributions</span></span>

<span data-ttu-id="a39b9-110">下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="a39b9-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="a39b9-111">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或已不再支援 RHEL 版本，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="a39b9-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="a39b9-112">✔️表示仍支援 RHEL 或 .NET 的版本。</span><span class="sxs-lookup"><span data-stu-id="a39b9-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="a39b9-113">❌表示該 rhel 版本不支援 rhel 或 .net 的版本。</span><span class="sxs-lookup"><span data-stu-id="a39b9-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="a39b9-114">當版本的 RHEL 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="a39b9-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="a39b9-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="a39b9-115">RHEL</span></span>                     | <span data-ttu-id="a39b9-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a39b9-116">.NET Core 2.1</span></span> | <span data-ttu-id="a39b9-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a39b9-117">.NET Core 3.1</span></span> | <span data-ttu-id="a39b9-118">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="a39b9-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="a39b9-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="a39b9-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="a39b9-120">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="a39b9-120">✔️ 2.1</span></span>        | <span data-ttu-id="a39b9-121">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="a39b9-121">✔️ 3.1</span></span>        | <span data-ttu-id="a39b9-122">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="a39b9-122">✔️ 5.0</span></span> |
| <span data-ttu-id="a39b9-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="a39b9-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="a39b9-124">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="a39b9-124">✔️ 2.1</span></span>        | <span data-ttu-id="a39b9-125">✔️ [3.1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="a39b9-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="a39b9-126">✔️ [5.0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="a39b9-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="a39b9-127">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="a39b9-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="a39b9-128">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="a39b9-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="a39b9-129">3.0</span><span class="sxs-lookup"><span data-stu-id="a39b9-129">3.0</span></span>
- <span data-ttu-id="a39b9-130">2.2</span><span class="sxs-lookup"><span data-stu-id="a39b9-130">2.2</span></span>
- <span data-ttu-id="a39b9-131">2.0</span><span class="sxs-lookup"><span data-stu-id="a39b9-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a39b9-132">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="a39b9-132">How to install other versions</span></span>

<span data-ttu-id="a39b9-133">請參閱 [.net 的 Red Hat 檔](https://access.redhat.com/documentation/net/5.0/) ，以瞭解安裝其他 .net 版本所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="a39b9-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="a39b9-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="a39b9-134">RHEL 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="a39b9-135">.NET 5.0 尚未在應用程式資料流程存放庫中提供，但 .NET Core 3.1 為。</span><span class="sxs-lookup"><span data-stu-id="a39b9-135">.NET 5.0 isn't yet available in the AppStream repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="a39b9-136">若要安裝 .NET Core 3.1，請使用 `dnf install` 命令搭配適當的封裝，例如 `aspnetcore-runtime-3.1` 或 `dotnet-sdk-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="a39b9-136">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="a39b9-137">下列指示適用于 .NET 5.0。</span><span class="sxs-lookup"><span data-stu-id="a39b9-137">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/8/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="a39b9-138">RHEL 7 ✔️ .NET 5。0</span><span class="sxs-lookup"><span data-stu-id="a39b9-138">RHEL 7 ✔️ .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-yum.md)]

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="a39b9-139">RHEL 7 ✔️ .NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="a39b9-139">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="a39b9-140">下列命令會安裝 `scl-utils` 套件：</span><span class="sxs-lookup"><span data-stu-id="a39b9-140">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="a39b9-141">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="a39b9-141">Install the SDK</span></span>

<span data-ttu-id="a39b9-142">.NET Core SDK 可讓您使用 .NET Core 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="a39b9-142">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="a39b9-143">如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="a39b9-143">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="a39b9-144">若要安裝 .NET Core SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a39b9-144">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="a39b9-145">Red Hat 不建議永久啟用 `rh-dotnet31` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="a39b9-145">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="a39b9-146">例如， `rh-dotnet31` 包含 `libcurl` 與基底 RHEL 版本不同的版本。</span><span class="sxs-lookup"><span data-stu-id="a39b9-146">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="a39b9-147">這可能會導致不預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="a39b9-147">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="a39b9-148">如果您想要 `rh-dotnet` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="a39b9-148">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="a39b9-149">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="a39b9-149">Install the runtime</span></span>

<span data-ttu-id="a39b9-150">.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a39b9-150">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="a39b9-151">下列命令會安裝 ASP.NET Core 執行時間，這是 .NET Core 最相容的執行時間。</span><span class="sxs-lookup"><span data-stu-id="a39b9-151">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="a39b9-152">在您的終端機中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a39b9-152">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="a39b9-153">Red Hat 不建議永久啟用 `rh-dotnet31-aspnetcore-runtime-3.1` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="a39b9-153">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="a39b9-154">例如， `rh-dotnet31-aspnetcore-runtime-3.1` 包含 `libcurl` 與基底 RHEL 版本不同的版本。</span><span class="sxs-lookup"><span data-stu-id="a39b9-154">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="a39b9-155">這可能會導致不預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="a39b9-155">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="a39b9-156">如果您想要 `rh-dotnet31-aspnetcore-runtime-3.1` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="a39b9-156">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="a39b9-157">除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `rh-dotnet31-aspnetcore-runtime-3.1` 在上述命令中將取代為 `rh-dotnet31-dotnet-runtime-3.1` 。</span><span class="sxs-lookup"><span data-stu-id="a39b9-157">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="a39b9-158">單元</span><span class="sxs-lookup"><span data-stu-id="a39b9-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="a39b9-159">相依性</span><span class="sxs-lookup"><span data-stu-id="a39b9-159">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="a39b9-160">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="a39b9-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="a39b9-161">手動安裝</span><span class="sxs-lookup"><span data-stu-id="a39b9-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="a39b9-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a39b9-162">Next steps</span></span>

- [<span data-ttu-id="a39b9-163">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a39b9-163">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
