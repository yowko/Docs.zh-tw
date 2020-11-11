---
title: 在 RHEL 上安裝 .NET-.NET
description: 示範在 RHEL 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: a742497bba3459a4d8772f5c9e3d915b5b18e62e
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506920"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="2f027-103">在 RHEL 上安裝 .NET SDK 或 .NET 執行時間</span><span class="sxs-lookup"><span data-stu-id="2f027-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="2f027-104">RHEL 支援 .NET。</span><span class="sxs-lookup"><span data-stu-id="2f027-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="2f027-105">本文說明如何在 RHEL 上安裝 .NET。</span><span class="sxs-lookup"><span data-stu-id="2f027-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="2f027-106">註冊您的 Red Hat 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="2f027-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="2f027-107">若要在 RHEL 上從 Red Hat 安裝 .NET，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。</span><span class="sxs-lookup"><span data-stu-id="2f027-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="2f027-108">如果未在您的系統上完成此操作，或如果您不確定，請參閱 [.net 的 Red Hat 產品檔](https://access.redhat.com/documentation/net/5.0/)。</span><span class="sxs-lookup"><span data-stu-id="2f027-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="2f027-109">支援的發行版本</span><span class="sxs-lookup"><span data-stu-id="2f027-109">Supported distributions</span></span>

<span data-ttu-id="2f027-110">下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET 版本清單。</span><span class="sxs-lookup"><span data-stu-id="2f027-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="2f027-111">除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或已不再支援 RHEL 版本，否則仍支援這些版本。</span><span class="sxs-lookup"><span data-stu-id="2f027-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="2f027-112">✔️表示仍支援 RHEL 或 .NET 的版本。</span><span class="sxs-lookup"><span data-stu-id="2f027-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="2f027-113">❌表示該 rhel 版本不支援 rhel 或 .net 的版本。</span><span class="sxs-lookup"><span data-stu-id="2f027-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="2f027-114">當版本的 RHEL 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。</span><span class="sxs-lookup"><span data-stu-id="2f027-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="2f027-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="2f027-115">RHEL</span></span>                   | <span data-ttu-id="2f027-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2f027-116">.NET Core 2.1</span></span> | <span data-ttu-id="2f027-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2f027-117">.NET Core 3.1</span></span> | <span data-ttu-id="2f027-118">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="2f027-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="2f027-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="2f027-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="2f027-120">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="2f027-120">✔️ 2.1</span></span>        | <span data-ttu-id="2f027-121">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="2f027-121">✔️ 3.1</span></span>        | <span data-ttu-id="2f027-122">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="2f027-122">✔️ 5.0</span></span> |
| <span data-ttu-id="2f027-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="2f027-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="2f027-124">✔️2。1</span><span class="sxs-lookup"><span data-stu-id="2f027-124">✔️ 2.1</span></span>        | <span data-ttu-id="2f027-125">✔️3。1</span><span class="sxs-lookup"><span data-stu-id="2f027-125">✔️ 3.1</span></span>        | <span data-ttu-id="2f027-126">✔️5。0</span><span class="sxs-lookup"><span data-stu-id="2f027-126">✔️ 5.0</span></span> |

<span data-ttu-id="2f027-127">不再支援下列 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="2f027-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="2f027-128">這些內容的下載仍會保持發佈：</span><span class="sxs-lookup"><span data-stu-id="2f027-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="2f027-129">3.0</span><span class="sxs-lookup"><span data-stu-id="2f027-129">3.0</span></span>
- <span data-ttu-id="2f027-130">2.2</span><span class="sxs-lookup"><span data-stu-id="2f027-130">2.2</span></span>
- <span data-ttu-id="2f027-131">2.0</span><span class="sxs-lookup"><span data-stu-id="2f027-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2f027-132">如何安裝其他版本</span><span class="sxs-lookup"><span data-stu-id="2f027-132">How to install other versions</span></span>

<span data-ttu-id="2f027-133">請參閱 [.net 的 Red Hat 檔](https://access.redhat.com/documentation/net/5.0/) ，以瞭解安裝其他 .net 版本所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="2f027-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="2f027-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="2f027-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="2f027-135">.NET 包含在 RHEL 8 的應用程式資料流程存放庫中。</span><span class="sxs-lookup"><span data-stu-id="2f027-135">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="2f027-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="2f027-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="2f027-137">下列命令會安裝 `scl-utils` 套件：</span><span class="sxs-lookup"><span data-stu-id="2f027-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="2f027-138">安裝 SDK</span><span class="sxs-lookup"><span data-stu-id="2f027-138">Install the SDK</span></span>

<span data-ttu-id="2f027-139">.NET SDK 可讓您使用 .NET 開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f027-139">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="2f027-140">如果您安裝 .NET SDK，就不需要安裝對應的執行時間。</span><span class="sxs-lookup"><span data-stu-id="2f027-140">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="2f027-141">若要安裝 .NET SDK，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f027-141">To install the .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="2f027-142">Red Hat 不建議永久啟用 `rh-dotnet50` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="2f027-142">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="2f027-143">例如， `rh-dotnet50` 包含 `libcurl` 與基底 RHEL 版本不同的版本。</span><span class="sxs-lookup"><span data-stu-id="2f027-143">For example, `rh-dotnet50` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="2f027-144">這可能會導致不預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="2f027-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="2f027-145">如果您想要 `rh-dotnet` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="2f027-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="2f027-146">安裝執行階段</span><span class="sxs-lookup"><span data-stu-id="2f027-146">Install the runtime</span></span>

<span data-ttu-id="2f027-147">ASP.NET Core 執行時間可讓您執行不提供執行時間的 .NET 所建立的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f027-147">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="2f027-148">下列命令會安裝 ASP.NET Core 執行時間，也就是最相容的 .NET 執行時間。</span><span class="sxs-lookup"><span data-stu-id="2f027-148">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="2f027-149">在您的終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="2f027-149">In your terminal, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50-aspnetcore-runtime-5.0 bash
```

<span data-ttu-id="2f027-150">Red Hat 不建議永久啟用 `rh-dotnet50-aspnetcore-runtime-5.0` ，因為它可能會影響其他程式。</span><span class="sxs-lookup"><span data-stu-id="2f027-150">Red Hat doesn't recommend permanently enabling `rh-dotnet50-aspnetcore-runtime-5.0` because it may affect other programs.</span></span> <span data-ttu-id="2f027-151">例如， `rh-dotnet50-aspnetcore-runtime-5.0` 包含 `libcurl` 與基底 RHEL 版本不同的版本。</span><span class="sxs-lookup"><span data-stu-id="2f027-151">For example, `rh-dotnet50-aspnetcore-runtime-5.0` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="2f027-152">這可能會導致不預期不同版本的程式發生問題 `libcurl` 。</span><span class="sxs-lookup"><span data-stu-id="2f027-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="2f027-153">如果您想要 `rh-dotnet50-aspnetcore-runtime-5.0` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。</span><span class="sxs-lookup"><span data-stu-id="2f027-153">If you want to enable `rh-dotnet50-aspnetcore-runtime-5.0` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50-aspnetcore-runtime-5.0
```

<span data-ttu-id="2f027-154">除了 ASP.NET Core 執行時間之外，您還可以安裝 .NET 執行時間，不包括 ASP.NET Core 支援： `rh-dotnet50-aspnetcore-runtime-5.0` 在先前的命令中將取代為 `rh-dotnet50-dotnet-runtime-5.0` 。</span><span class="sxs-lookup"><span data-stu-id="2f027-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the previous commands with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="snap"></a><span data-ttu-id="2f027-155">單元</span><span class="sxs-lookup"><span data-stu-id="2f027-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="2f027-156">相依性</span><span class="sxs-lookup"><span data-stu-id="2f027-156">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="2f027-157">腳本式安裝</span><span class="sxs-lookup"><span data-stu-id="2f027-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="2f027-158">手動安裝</span><span class="sxs-lookup"><span data-stu-id="2f027-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="2f027-159">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2f027-159">Next steps</span></span>

- [<span data-ttu-id="2f027-160">教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2f027-160">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
